---
title: 为卸载创建和使用作业
seo-title: Creating and Consuming Jobs for Offloading
description: Apache Sling Discovery功能提供了一个Java API，允许您创建使用JobManager作业和JobConsumer服务
seo-description: The Apache Sling Discovery feature provides a Java API that enables you to create JobManager jobs and JobConsumer services that consume them
uuid: d6a5beb0-0618-4b61-9b52-570862eac920
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: e7b6b9ee-d807-4eb0-8e96-75ca1e66a4e4
exl-id: ec5253cd-7f1e-4408-9765-8aaa9a81095c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 1%

---

# 为卸载创建和使用作业{#creating-and-consuming-jobs-for-offloading}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Apache Sling Discovery功能提供了一个Java API，允许您创建使用JobManager作业和JobConsumer服务的Java API。

有关创建卸载拓扑和配置主题使用情况的信息，请参阅 [卸载作业](/help/sites-deploying/offloading.md).

## 处理作业负载 {#handling-job-payloads}

卸载框架定义了两个用于标识作业负载的作业属性。 卸载的复制代理使用这些属性来标识要复制到拓扑中实例的资源：

* `offloading.job.input.payload`:以逗号分隔的内容路径列表。 内容会复制到执行该作业的实例。
* `offloading.job.output.payload`:以逗号分隔的内容路径列表。 作业执行完成后，作业有效负载将复制到创建作业的实例上的这些路径。

使用 `OffloadingJobProperties` 引用属性名称的枚举：

* `OffloadingJobProperties.INPUT_PAYLOAD.propertyName()`
* `OffloadingJobProperties.OUTPUT_PAYLOAD.propetyName()`

作业不需要负载。 但是，如果作业需要处理资源并且作业卸载到未创建作业的计算机，则有效负载是必需的。

## 为卸载创建作业 {#creating-jobs-for-offloading}

创建调用JobManager.addJob方法的客户端，以创建由自动选择的JobConsumer执行的作业。 提供以下信息以创建作业：

* 主题：作业主题。
* 名称：（可选）
* 属性映射：A `Map<String, Object>` 包含任意数量属性的对象，例如输入有效负载路径和输出有效负载路径。 此映射对象可用于执行该作业的JobConsumer对象。

以下示例服务为给定主题和输入有效负载路径创建作业。

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import java.util.HashMap;

import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;

import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.ResourceResolver;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class JobGeneratorImpl implements JobGenerator  {

 @Reference
 private JobManager jobManager;
 @Reference ResourceResolverFactory resolverFactory;

 public String createJob(String topic, String payload) throws Exception {
  Job offloadingJob;

  ResourceResolver resolver = resolverFactory.getResourceResolver(null);
  if(resolver.getResource(payload)!=null){

   HashMap<String, Object> jobprops = new HashMap<String, Object>();
   jobprops.put(OffloadingJobProperties.INPUT_PAYLOAD.propertyName(), payload);

   offloadingJob = jobManager.addJob(topic, null, jobprops);
  } else {
   throw new Exception("Payload for job cannot be found");
  }
  if (offloadingJob == null){
   throw new Exception ("Offloading job could not be created");
  }
  return offloadingJob.getId();
 }
}
```

在为 `com/adobe/example/offloading` 主题和 `/content/geometrixx/de/services` 有效负载：

```shell
10.06.2013 15:43:33.868 *INFO* [JobHandler: /etc/workflow/instances/2013-06-10/model_1554418768647484:/content/geometrixx/en/company] com.adobe.example.offloading.JobGeneratorImpl Received request to make job for topic com/adobe/example/offloading and payload /content/geometrixx/de/services
```

## 发展就业消费者 {#developing-a-job-consumer}

要使用作业，请开发一个实施 `org.apache.sling.event.jobs.consumer.JobConsumer` 界面。 使用识别要使用的主题 `JobConsumer.PROPERTY_TOPICS` 属性。

以下示例JobConsumer实施在 `com/adobe/example/offloading` 主题。 用户只需将有效负载内容节点的Unsed属性设置为true即可。

```java
package com.adobe.example.offloading;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.event.jobs.Job;
import org.apache.sling.event.jobs.JobManager;
import org.apache.sling.event.jobs.consumer.JobConsumer;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import javax.jcr.Session;
import javax.jcr.Node;

import com.adobe.granite.offloading.api.OffloadingJobProperties;

@Component
@Service
public class MyJobConsumer implements JobConsumer {

 public static final String TOPIC = "com/adobe/example/offloading";

 @Property(value = TOPIC)
 static final String myTopic = JobConsumer.PROPERTY_TOPICS; 

 @Reference
 private ResourceResolverFactory resolverFactory;

 @Reference
 private JobManager jobManager;

 private final Logger log = LoggerFactory.getLogger(getClass());

 public JobResult process(Job job) {
  JobResult result = JobResult.FAILED;
  String topic = job.getTopic();
  log.info("Consuming job of topic: {}", topic);
  String payloadIn =  (String) job.getProperty(OffloadingJobProperties.INPUT_PAYLOAD.propertyName());
  String payloadOut =  (String) job.getProperty(OffloadingJobProperties.OUTPUT_PAYLOAD.propertyName());

  log.info("Job has Input Payload {} and Output Payload {}",payloadIn, payloadOut);

  ResourceResolver resolver = null;
  try {
   resolver = resolverFactory.getAdministrativeResourceResolver(null);
   Session session = resolver.adaptTo(Session.class);
   Node inNode = session.getNode(payloadIn);
   inNode.getNode(Node.JCR_CONTENT).setProperty("consumed",true);
   result = JobResult.OK;
  }catch (Exception e){
   log.info("ERROR -- JOB RESULT IS FAILURE " + e.getMessage());
   result = JobResult.FAILED;
  }
  log.info("Job OK for payload {}",payloadIn);
  return result;
 }
}
```

MyJobConsumer类为/content/geometrixx/de/services的输入负载生成以下日志消息：

```shell
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Consuming job of topic: com/adobe/example/offloading
10.06.2013 16:02:40.803 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job has Input Payload /content/geometrixx/de/services and Output Payload /content/geometrixx/de/services
10.06.2013 16:02:40.884 *INFO* [pool-7-thread-17-<main queue>(com/adobe/example/offloading)] com.adobe.example.offloading.MyJobConsumer Job OK for payload /content/geometrixx/de/services
```

使用CRXDE Lite可以观察使用的属性：

![chlimage_1-25](assets/chlimage_1-25.png)

## Maven依赖项 {#maven-dependencies}

将以下依赖关系维护添加到pom.xml文件，以便Maven能够解析与卸载相关的类。

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.event</artifactId>
   <version>3.1.5-R1485539</version>
   <scope>provided</scope> 
</dependency>
<dependency>
   <groupId>com.adobe.granite</groupId>
   <artifactId>com.adobe.granite.offloading.core</artifactId>
   <version>1.0.4</version>
   <scope>provided</scope>
</dependency>
```

以前的示例还需要以下依赖关系定义：

```xml
<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.api</artifactId>
   <version>2.4.3-R1488084</version>
   <scope>provided</scope>
</dependency>

<dependency>
   <groupId>org.apache.sling</groupId>
   <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
   <version>2.0.0</version>
   <scope>provided</scope>
</dependency>
```
