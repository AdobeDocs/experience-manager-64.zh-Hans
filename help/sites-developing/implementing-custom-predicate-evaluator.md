---
title: 为查询生成器实施自定义谓词计算器
seo-title: 为查询生成器实施自定义谓词计算器
description: 查询生成器优惠一种轻松的内容存储库查询方式
seo-description: 查询生成器优惠一种轻松的内容存储库查询方式
uuid: 5b599b60-a149-4425-b7ac-7fbe7e048bca
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 08bdade7-fdad-445d-80fe-8fc06596dace
translation-type: tm+mt
source-git-commit: 15bea340f3ba7d5a315d71932e521ad1f1a40073
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---


# 为查询生成器实施自定义谓词计算器{#implementing-a-custom-predicate-evaluator-for-the-query-builder}

本节介绍如何通过实现自 [定义谓词](/help/sites-developing/querybuilder-api.md) ，扩展查询生成器。

## 概述 {#overview}

查询 [生成器](/help/sites-developing/querybuilder-api.md) 优惠一种查询内容存储库的简单方法。 AEM附带一组谓词计算器，可帮助您处理数据。

但是，您可能希望通过实现隐藏某些复杂性并确保更好的语义的自定义谓词计算器来简化查询。

自定义谓词还可以执行XPath不能直接执行的其他操作，例如：

* 从一些服务中查找一些数据
* 基于计算的自定义过滤

>[!NOTE]
>
>实施自定义谓词时必须考虑性能问题。

>[!NOTE]
>
>您可以在查询生成器部分 [找到查询](/help/sites-developing/querybuilder-api.md) 。

GITHUB上的代码

您可以在GitHub上找到此页面的代码

* [在GitHub上打开aem-search-custom-predicate-evaluator项目](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)
* 以ZIP文件的 [形式下载项目](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/archive/master.zip)

## 详细谓词计算器 {#predicate-evaluator-in-detail}

谓词计算器处理特定谓词的计算，这些谓词是查询的定义约束。

它将更高级别的搜索约束（如“宽度> 200”）映射到符合实际内容模型的特定JCR查询（例如，元数据/@width > 200）。 或者，也可以手动过滤节点并检查其约束。

>[!NOTE]
>
>有关和包的更 `PredicateEvaluator` 多信 `com.day.cq.search` 息，请参阅 [Java文档](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/search/package-summary.html)。

## 为复制元数据实施自定义谓词计算器 {#implementing-a-custom-predicate-evaluator-for-replication-metadata}

作为示例，本节介绍如何创建自定义谓词计算器，以帮助基于复制元数据的数据：

* `cq:lastReplicated` 存储上次复制操作的日期

* `cq:lastReplicatedBy` 存储触发上次复制操作的用户的id

* `cq:lastReplicationAction` 存储上次复制操作(例如激活、取消激活)

### 使用默认谓词计算器查询复制元数据 {#querying-replication-metadata-with-default-predicate-evaluators}

以下查询获取自年初起 `/content` 已激活的分支 `admin` 中节点的列表。

```xml
path=/content

1_property=cq:lastReplicatedBy
1_property.value=admin

2_property=cq:lastReplicationAction
2_property.value=Activate

daterange.property=cq:lastReplicated
daterange.lowerBound=2013-01-01T00:00:00.000+01:00
daterange.lowerOperation=>=
```

此查询有效，但难以读取，并且不会突出显示三个复制属性之间的关系。 实施自定义谓词计算器将降低该查询的复杂性并改进语义。

### 目标 {#objectives}

其目标是使 `ReplicationPredicateEvaluator` 用以下语法支持上述查询。

```xml
path=/content

replic.by=admin
replic.since=2013-01-01T00:00:00.000+01:00
replic.action=Activate
```

使用自定义谓词计算器将复制元数据谓词分组有助于创建有意义的查询。

### 更新Maven依赖项 {#updating-maven-dependencies}

>[!NOTE]
>
>如何使用Apache Maven构建AEM项目，介绍使 [用maven建立新的AEM项目的方法](/help/sites-developing/ht-projects-maven.md)。

首先，您需要更新项目的Maven依赖关系。 该 `PredicateEvaluator` 项是项目的一 `cq-search` 部分，因此需要将其添加到您的Maven pom文件。

>[!NOTE]
>
>依赖项的范围 `cq-search` 设置为 `provided` , `cq-search` 因为容器将提供 `OSGi` 。

pom.xml

以下代码片断以统一的差异 [格式显示差异](https://en.wikipedia.org/wiki/Diff#Unified_format)

```
@@ -120,6 +120,12 @@
             <scope>provided</scope>
         <dependency>
+            <groupid>com.day.cq</groupid>
+            <artifactid>cq-search</artifactid>
+            <version>5.6.4</version>
+            <scope>provided</scope>
+        </dependency>
+        <dependency>
             <groupid>junit</groupid>
             <artifactid>junit</artifactid>
             <version>3.8.1</version></dependency>
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)- [pom.xml](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/7aed6b35b4c8dd3655296e1b10cf40c0dd1eaa61/pom.xml)

### 编写ReplicationPredicateEvaluator {#writing-the-replicationpredicateevaluator}

项 `cq-search` 目包含 `AbstractPredicateEvaluator` 抽象类。 只需几步即可扩展该功能，以实现您自己的自定义谓词计算 `(PredicateEvaluator`器)。

>[!NOTE]
>
>以下过程说明了如何构建 `Xpath` 表达式来筛选数据。 另一个选项是实 `includes` 现按行选择数据的方法。 See the [Java documentation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/eval/PredicateEvaluator.html#includes28comdaycqsearchpredicatejavaxjcrqueryrowcomdaycqsearchevalevaluationcontext29) for more information.

1. 新建一个扩展 `com.day.cq.search.eval.AbstractPredicateEvaluator`
1. 使用类似于以下内容 `@Component` 对您的课堂进行注释

   src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

   以下代码片断以统一的差异 [格式显示差异](https://en.wikipedia.org/wiki/Diff#Unified_format)


```
@@ -19,8 +19,11 @@
  */
 package com.adobe.aem.docs.search;
+import org.apache.felix.scr.annotations.Component;
+import com.day.cq.search.eval.AbstractPredicateEvaluator;
+@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")
 public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

  }
```

[aem-search-custom-predicate-evaluator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator)- [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/raw/ec70fac35fbd0d132e00c6066a204804e9cbe70f/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)

>[!NOTE]
>
>该 `factory`字符串必须是以自定 `com.day.cq.search.eval.PredicateEvaluator/`义名称开头和结尾的唯一字符串 `PredicateEvaluator`。

>[!NOTE]
>
>谓词名称 `PredicateEvaluator` 是谓词名称，用于构建查询。

1. 覆盖：

   ```java
   public String getXPathExpression(Predicate predicate, EvaluationContext context)
   ```

   在覆盖方法中，您将根 `Xpath` 据参数中给 `Predicate` 定的表达式构建。

### 复制元数据的自定义谓词计算器示例 {#example-of-a-custom-predicate-evalutor-for-replication-metadata}

此类的完 `PredicateEvaluator` 整实现可能类似于以下类。

src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java

```
/*
 * #%L
 * aem-docs-custom-predicate-evaluator
 * %%
 * Copyright (C) 2013 Adobe Research
 * %%
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 * #L%
 */

package com.adobe.aem.docs.search;

import org.apache.felix.scr.annotations.Component;

import org.slf4j.Logger;

import org.slf4j.LoggerFactory;

 
import com.day.cq.search.Predicate;

import com.day.cq.search.eval.AbstractPredicateEvaluator;

import com.day.cq.search.eval.EvaluationContext;

 
@Component(metatype = false, factory = "com.day.cq.search.eval.PredicateEvaluator/repli")

public class ReplicationPredicateEvaluator extends AbstractPredicateEvaluator {

    static final String PE_NAME = "replic";

    static final String PN_LAST_REPLICATED_BY = "cq:lastReplicatedBy";

    static final String PN_LAST_REPLICATED = "cq:lastReplicated";

    static final String PN_LAST_REPLICATED_ACTION = "cq:lastReplicationAction";

    static final String PREDICATE_BY = "by";

    static final String PREDICATE_SINCE = "since";

    static final String PREDICATE_SINCE_OP = " >= ";

    static final String PREDICATE_ACTION = "action";
 

    Logger log = LoggerFactory.getLogger(getClass());

    /**
     * Returns a XPath expression filtering by replication metadata.
     *
     * @see com.day.cq.search.eval.AbstractPredicateEvaluator#getXPathExpression(com.day.cq.search.Predicate,
     *      com.day.cq.search.eval.EvaluationContext)
     */

    @Override

    public String getXPathExpression(Predicate predicate,

            EvaluationContext context) {

        log.debug("predicate {}", predicate);


        String date = predicate.get(PREDICATE_SINCE);

        String user = predicate.get(PREDICATE_BY);

        String action = predicate.get(PREDICATE_ACTION);


        StringBuilder sb = new StringBuilder();


        if (date != null) {

            sb.append(PN_LAST_REPLICATED).append(PREDICATE_SINCE_OP);

            sb.append("xs:dateTime('").append(date).append("')");

        }

        if (user != null) {

            addAndOperator(sb);

            sb.append(PN_LAST_REPLICATED_BY);

            sb.append("='").append(user).append("'");

        }

        if (action != null) {

            addAndOperator(sb);

            sb.append(PN_LAST_REPLICATED_ACTION);

            sb.append("='").append(action).append("'");

        }

        String xpath = sb.toString();

        log.debug("xpath **{}**", xpath);

        return xpath;

    }

    /**
     * Add an and operator if the builder is not empty.
     *
     * @param sb a {@link StringBuilder} containing the query under construction
     */

    private void addAndOperator(StringBuilder sb) {

        if (sb.length() != 0) {

            sb.append(" and ");

        }

    }

}
```

[aem-search-custom-predicate-evalator](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator) - [src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java](https://github.com/Adobe-Marketing-Cloud/aem-search-custom-predicate-evaluator/blob/master/src/main/java/com/adobe/aem/docs/search/ReplicationPredicateEvaluator.java)
