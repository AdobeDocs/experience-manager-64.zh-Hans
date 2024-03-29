---
title: 如何使用IntelliJ IDEA开发AEM项目
seo-title: How to Develop AEM Projects using IntelliJ IDEA
description: 使用IntelliJ IDEA开发AEM项目
seo-description: Using IntelliJ IDEA to develop AEM projects
uuid: 382b5008-2aed-4e08-95be-03c48f2b549e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: df6410a2-794e-4fa2-ae8d-37271274d537
exl-id: 274b3a33-3267-41ee-bdcd-351787152570
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 0%

---

# 如何使用IntelliJ IDEA开发AEM项目{#how-to-develop-aem-projects-using-intellij-idea}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

要开始在IntelliJ上开发AEM，需要执行以下步骤。

在本操作说明的其余部分中，将更详细地解释每个操作说明。

* 安装IntelliJ
* 基于Maven设置AEM项目
* 在Maven POM中准备对IntelliJ的JSP支持
* 将Maven项目导入IntelliJ

>[!NOTE]
>
>本指南基于IntelliJ IDEA Ultimate Edition 12.1.4和AEM 5.6.1。

### 安装IntelliJ IDEA {#install-intellij-idea}

从下载IntelliJ IDEA [JetBrains的下载页面](https://www.jetbrains.com/idea/download/index.html).

然后，按照该页面上的安装说明操作。

### 基于Maven设置AEM项目 {#set-up-your-aem-project-based-on-maven}

接下来，使用Maven设置项目，如 [如何使用Apache Maven构建AEM项目](/help/sites-developing/ht-projects-maven.md).

要开始在IntelliJ IDEA中使用AEM项目，请参阅 [5分钟后入门](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html) 就够了。

### 准备对IntelliJ IDEA的JSP支持 {#prepare-jsp-support-for-intellij-idea}

IntelliJ IDEA还可以在使用JSP(例如，

* 自动完成标记库
* 对由 `<cq:defineObjects />` 和 `<sling:defineObjects />`

要使其正常工作，请按照 [如何使用JSP](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) in [如何使用Apache Maven构建AEM项目](/help/sites-developing/ht-projects-maven.md).

### 导入Maven项目 {#import-the-maven-project}

1. 打开 **导入** 对话框（位于IntelliJ IDEA中）

   * 选择 **导入项目** （如果尚未打开项目）
   * 选择 **文件 — >导入项目** 从主菜单

1. 在导入对话框中，选择项目的POM文件。

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. 继续默认设置，如下面的对话框所示。

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. 通过单击 **下一个** 和 **完成**.
1. 您现在已设置为使用IntelliJ IDEA进行AEM开发

   ![chlimage_1-47](assets/chlimage_1-47.png)

### 使用IntelliJ IDEA调试JSP {#debugging-jsps-with-intellij-idea}

使用IntelliJ IDEA调试JSP时，需要执行以下步骤

* 在项目中设置Web Facet
* 安装JSR45支持插件
* 配置调试配置文件
* 为调试模式配置AEM

#### 在项目中设置Web Facet {#set-up-a-web-facet-in-the-project}

IntelliJ IDEA需要了解在何处查找JSP以进行调试。 由于IDEA无法解释 `content-package-maven-plugin` 设置，则需要手动配置。

1. 转到 **文件 — >项目结构**
1. 选择 **内容** 模块
1. 单击 **+** 并选择 **Web**
1. 作为Web资源目录，选择 `content/src/main/content/jcr_root subdirectory` 的项目，如下面的屏幕快照所示。

![chlimage_1-48](assets/chlimage_1-48.png)

#### 安装JSR45支持插件 {#install-the-jsr-support-plugin}

1. 转到 **插件** “IntelliJ IDEA”设置中的窗格
1. 导航到 **JSR45集成** 插件并选中该插件旁边的复选框
1. 单击 **应用**
1. 请求重新启动IntelliJ IDEA

![chlimage_1-49](assets/chlimage_1-49.png)

#### 配置调试配置文件 {#configure-a-debug-profile}

1. 转到 **运行 — >编辑配置**
1. 点击 **+** 选择 **JSR45远程**
1. 在配置对话框中，选择 **配置** 下一页 **应用程序服务器** 和配置通用服务器
1. 如果要在开始调试时打开浏览器，请将起始页设置为相应的URL
1. 全部删除 **启动前** 任务（如果您使用vlt autosync），或者配置适当的Maven任务（如果您不使用vlt autosync）
1. 在 **启动/连接** 窗格，根据需要调整端口
1. 复制IntelliJ IDEA提出的命令行参数

![chlimage_1-50](assets/chlimage_1-50.png) ![chlimage_1-51](assets/chlimage_1-51.png)

#### 为调试模式配置AEM {#configure-aem-for-debug-mode}

所需的最后一步是使用IntelliJ IDEA建议的JVM选项启动AEM。

为此，您可以直接启动AEM jar文件并添加这些选项，例如使用以下命令行：

`java -Xdebug -Xrunjdwp:transport=dt_socket,address=58242,suspend=n,server=y -Xmx1024m -XX:MaxPermSize=256M -jar cq-quickstart-5.6.1.jar`

您还可以将这些选项添加到 `crx-quickstart/bin/start` 如下所示。

```shell
# ...

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).

# default JVM options

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
if [ -z "$CQ_JVM_OPTS" ]; then
 CQ_JVM_OPTS='-server -Xmx1024m -XX:MaxPermSize=256M -Djava.awt.headless=true'
fi

CQ_JVM_OPTS="$CQ_JVM_OPTS -Xdebug -Xrunjdwp:transport=dt_socket,address=58242,suspend=n,server=y"

# ...

>[!CAUTION]
>
>AEM 6.4 has reached the end of extended support and this documentation is no longer updated. For further details, see our [technical support periods](https://helpx.adobe.com/support/programs/eol-matrix.html). Find the supported versions [here](https://experienceleague.adobe.com/docs/).
```

#### 开始调试 {#start-debugging}

现在，您都已设置为在AEM中调试JSP。

1. 选择 **运行 — >调试 — >您的调试配置文件**
1. 在组件代码中设置断点
1. 在浏览器中访问页面

![chlimage_1-52](assets/chlimage_1-52.png)

### 使用IntelliJ IDEA调试包 {#debugging-bundles-with-intellij-idea}

可以使用标准的通用远程调试连接来调试包中的代码。 您可以在 [关于远程调试的Jetbrain文档](https://www.jetbrains.com/idea/webhelp/run-debug-configuration-remote.html).
