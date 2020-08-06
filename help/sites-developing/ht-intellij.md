---
title: 如何使用IntelliJ IDEA开发AEM项目
seo-title: 如何使用IntelliJ IDEA开发AEM项目
description: 使用IntelliJ IDEA开发AEM项目
seo-description: 使用IntelliJ IDEA开发AEM项目
uuid: 382b5008-2aed-4e08-95be-03c48f2b549e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: df6410a2-794e-4fa2-ae8d-37271274d537
translation-type: tm+mt
source-git-commit: 5f84641d87b88532f0fa0d92fada4e8cca3d9684
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 0%

---


# 如何使用IntelliJ IDEA开发AEM项目{#how-to-develop-aem-projects-using-intellij-idea}

## 概述 {#overview}

要开始在IntelliJ上进行AEM开发，需要执行以下步骤。

每项操作在本“操作方法”的其余部分中都有更详细的说明。

* 安装IntelliJ
* 根据Maven设置AEM项目
* 在Maven POM中为IntelliJ准备JSP支持
* 将Maven项目导入IntelliJ

>[!NOTE]
>
>本指南基于IntelliJ IDEA Ultimate Edition 12.1.4和AEM 5.6.1。

### 安装IntelliJ IDEA {#install-intellij-idea}

从JetBrains的“下 [载”页下载IntelliJ IDEA](https://www.jetbrains.com/idea/download/index.html)。

然后，按照该页面上的安装说明操作。

### 根据Maven设置AEM项目 {#set-up-your-aem-project-based-on-maven}

接下来，如使用Apache Maven构建AEM项目 [中所述，使用Maven设置项目](/help/sites-developing/ht-projects-maven.md)。

要开始在IntelliJ IDEA中使用AEM项目，在5分钟内 [入门中的基本设置](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html) 已足够。

### 为IntelliJ IDEA准备JSP支持 {#prepare-jsp-support-for-intellij-idea}

IntelliJ IDEA还可以在使用JSP(例如，

* 标签库的自动完成
* 对定义和定义的对象 `<cq:defineObjects />` 的感知 `<sling:defineObjects />`

要使其正常工作，请按照使用 [Apache Maven构建AEM项目中](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps)[使用JSP的方法说明操作](/help/sites-developing/ht-projects-maven.md)。

### 导入Maven项目 {#import-the-maven-project}

1. 在IntelliJ IDEA **中** ，打开“导入”对话框

   * 如果 **尚未打开项** 目，请在欢迎屏幕上选择“导入项目”
   * 从主 **菜单中选择“文件** ”->“导入项目”

1. 在“导入”对话框中，选择项目的POM文件。

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. 继续使用默认设置，如下面的对话框所示。

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. 单击“下一步”和“完成” **，继续** 执行 **以下对话框**。
1. 您现在已使用IntelliJ IDEA为AEM Development设置

   ![chlimage_1-47](assets/chlimage_1-47.png)

### 使用IntelliJ IDEA调试JSP {#debugging-jsps-with-intellij-idea}

使用IntelliJ IDEA调试JSP时，必须执行以下步骤

* 在项目中设置Web彩块化
* 安装JSR45支持插件
* 配置调试用户档案
* 为调试模式配置AEM

#### 在项目中设置Web彩块化 {#set-up-a-web-facet-in-the-project}

IntelliJ IDEA需要了解在哪里可以找到用于调试的JSP。 由于IDEA无法解 `content-package-maven-plugin` 释设置，因此需要手动配置。

1. 转到“ **文件”->“项目结构”**
1. 选择内 **容模** 块
1. 单 **击** 模块列表上方的+并选择 **Web**
1. 作为Web资源目录，选择 `content/src/main/content/jcr_root subdirectory` 您的项目，如以下屏幕快照所示。

![chlimage_1-48](assets/chlimage_1-48.png)

#### 安装JSR45支持插件 {#install-the-jsr-support-plugin}

1. 转到IntelliJ **IDEA** 设置中的“插件”窗格
1. 导航到 **JSR45 Integration** Plugin并选中它旁边的复选框
1. 单击“应 **用”**
1. 请求重新启动IntelliJ IDEA

![chlimage_1-49](assets/chlimage_1-49.png)

#### 配置调试用户档案 {#configure-a-debug-profile}

1. 转到“运 **行”->“编辑配置”**
1. 点击 **+** 并选择 **JSR45 Remote**
1. 在配置对话框中，选择应 **用程序** 服务器旁 **边的配置** ，并配置通用服务器
1. 如果要在开始调试时打开浏览器，请将开始页设置为相应的URL
1. 如果您使 **用vlt自动同步** ，请在启动任务前删除所有任务，如果您不使用vlt自动同步，则请配置适当的Maven
1. 在“启 **动／连接** ”窗格中，根据需要调整端口
1. 复制IntelliJ IDEA建议的命令行参数

![chlimage_1-50](assets/chlimage_1-50.png) ![chlimage_1-51](assets/chlimage_1-51.png)

#### 为调试模式配置AEM {#configure-aem-for-debug-mode}

最后一步是开始AEM使用IntelliJ IDEA提出的JVM选项。

为此，可以直接启动AEM jar文件并添加这些选项，例如使用以下命令行：

`java -Xdebug -Xrunjdwp:transport=dt_socket,address=58242,suspend=n,server=y -Xmx1024m -XX:MaxPermSize=256M -jar cq-quickstart-5.6.1.jar`

您还可以按如下方式将这些选项添加 `crx-quickstart/bin/start` 到开始脚本。

```shell
# ...

# default JVM options
if [ -z "$CQ_JVM_OPTS" ]; then
 CQ_JVM_OPTS='-server -Xmx1024m -XX:MaxPermSize=256M -Djava.awt.headless=true'
fi

CQ_JVM_OPTS="$CQ_JVM_OPTS -Xdebug -Xrunjdwp:transport=dt_socket,address=58242,suspend=n,server=y"

# ...
```

#### 开始调试 {#start-debugging}

现在，您已全部设置为在AEM中调试JSP。

1. 选择 **运行->调试->调试用户档案**
1. 在组件代码中设置断点
1. 在浏览器中访问页面

![chlimage_1-52](assets/chlimage_1-52.png)

### 使用IntelliJ IDEA调试捆绑包 {#debugging-bundles-with-intellij-idea}

可以使用标准通用远程调试连接调试捆绑包中的代码。 您可以按照Jetbrain [文档进行远程调试](https://www.jetbrains.com/idea/webhelp/run-debug-configuration-remote.html)。
