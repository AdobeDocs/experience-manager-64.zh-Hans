---
title: AEM Brackets扩展
seo-title: AEM Brackets扩展
description: 'null'
seo-description: 'null'
uuid: 2f0dfa42-eb34-44ae-90eb-b5f321c03b79
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 8231a30a-dcb7-4156-bb45-c5a23e5b56ef
translation-type: tm+mt
source-git-commit: 8e2bd579e4c5edaaf86be36bd9d81dfffa13a573
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 0%

---


# AEM Brackets扩展{#aem-brackets-extension}

## 概述 {#overview}

AEM Brackets Extension提供了一个编辑AEM组件和客户端库的流畅工作流程，并利用Brackets代码编辑器的强大功能 [](https://brackets.io/) ，它允许从代码编辑器中访问Photoshop文件和图层。 扩展提供的轻松同步（无需Maven或File Vault）提高了开发人员效率，还帮助具有有限知识的前端开发人员参与项目。 此扩展还提供对HTML模 [板语言(HTL)的一些支持](https://helpx.adobe.com/experience-manager/htl/user-guide.html)，它消除了JSP的复杂性，使组件开发更简单、安全。

![chlimage_1-53](assets/chlimage_1-53.png)

### 功能 {#features}

AEM Brackets扩展的主要功能有：

* 将更改的文件自动同步到AEM开发实例。
* 文件和文件夹的手动双向同步。
* 项目的完整内容包同步。
* 表达式和块语句的HTL `data-sly-*` 代码完成。

此外，Brackets还为AEM字体端开发人员提供了许多有用的功能：

* Photoshop文件支持从PSD文件提取信息，如图层、度量、颜色、字体、文本等。
* PSD中的代码提示，以便在代码中轻松重复使用此提取的信息。
* CSS预处理器支持，如LESS和SCSS。
* 还有数百个附加扩展，可满足更具体的需求。

## 安装 {#installation}

### 括号 {#brackets}

AEM Brackets扩展支持Brackets 1.0或更高版本。

从brackets.io下载最 [新的Brackets版本](https://brackets.io/)。

### 扩展 {#the-extension}

要安装此扩展，请按照以下步骤继续：

1. 打开括号。 在菜单 **文件**&#x200B;中，选 **择Extension Manager...**
1. 在搜 **索** 栏中输入AEM并查找 **AEM Brackets扩展**。

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. 单击&#x200B;**安装**。
1. 安装完成后关闭对话框和Extension Manager。

## 入门 {#getting-started}

### 内容包项目 {#the-content-package-project}

安装扩展后，您可以通过使用Brackets从文件系统打开一个内容包文件夹来开始AEM组件的开发。

项目必须至少包含：

1. 文 `jcr_root` 件夹(例如 `myproject/jcr_root`)

1. 文 `filter.xml` 件(例如， `myproject/META-INF/vault/filter.xml`); 有关文件结构的更多详 `filter.xml` 细信息，请参阅工 [作区过滤器定义](https://jackrabbit.apache.org/filevault/filter.html)。

在Brackets的“ **文件** ”菜单中，选 **择“打开文件夹……** ”，然后选 `jcr_root` 择文件夹或父项目文件夹。

>[!NOTE]
>
>如果您没有包含内容包的项目，可以试用 [HTL TodoMVC示例](https://github.com/Adobe-Marketing-Cloud/aem-sightly-sample-todomvc)。 在GitHub上，单击“ **下载ZIP**”，在本地解压文件，然后按照上面的说明，在Brackets `jcr_root` 中打开文件夹。 然后按照以下步骤设置项 **目设置**，最后按照完全内容包同步部分的进一步说明，通过执行导 **出内容包** ，将整个包上传到AEM开发实例。
>
>完成这些步骤后，您应能够访问AEM开发实例的 `/content/todo.html` URL，并且您可以开始对Brackets中的代码进行修改，并了解在Web浏览器中进行刷新后，更改如何立即同步到AEM服务器。

### 项目设置 {#project-settings}

要同步与AEM开发实例之间的内容，您需要定义项目设置。 这可以通过转到AEM菜单并 **选择** “项目 **设置……”来完成。**

![chlimage_1-55](assets/chlimage_1-55.png)

项目设置允许定义：

1. 服务器URL(例如， `http://localhost:4502`)
1. 是否允许没有有效HTTPS证书的服务器（不选中，除非需要）
1. 用于同步内容的用户名(例如， `admin`)
1. 用户的口令(例如， `admin`)

## 同步内容 {#synchronizing-content}

AEM Brackets Extension为文件和文件夹提供以下类型的内容同步，这些内容同步由中定义的筛选规则所允许 `filter.xml`:

### 自动同步更改的文件 {#automated-synchronization-of-changed-files}

这将仅同步从Brackets到AEM实例的更改，但绝不会相反。

### 手动双向同步 {#manual-bidirectional-synchronization}

在项目资源管理器中，通过右键单击任何文件或文件夹打开上下文菜单，并可 **以访问“导出到服****务器”或“从服务器导入** ”选项。

![chlimage_1-56](assets/chlimage_1-56.png)

>[!NOTE]
>
>如果所选条目在文件夹之外， `jcr_root` 则禁用“ **导出到服务器** ”和“ **从服务器导入** ”上下文菜单条目。

### 完全内容包同步 {#full-content-package-synchronization}

在AEM菜 **单** 中，“导 **出内容包** ”或“导 **入内容包** ”选项允许将整个项目与服务器同步。

![chlimage_1-57](assets/chlimage_1-57.png)

### 同步状态 {#synchronization-status}

AEM Brackets Extension在Brackets窗口右侧的工具栏中显示一个通知图标，它指示上次同步的状态：

* 绿色——已成功同步所有文件
* blue —— 同步操作正在进行
* 黄色——某些文件未同步
* 红色——未同步任何文件

单击通知图标将打开“同步状态”报告对话框，其中列表了每个同步文件的所有状态。

![chlimage_1-58](assets/chlimage_1-58.png)

>[!NOTE]
>
>将只同步标记为筛选规则所包含的内 `filter.xml` 容，而不管使用的同步方法。
>
>此外， `.vltignore` 支持将内容排除在与存储库同步和与存储库同步之外的文件。

## 编辑HTL代码 {#editing-htl-code}

AEM Brackets Extension还具有一些自动完成功能，可简化HTL属性和表达式的编写。

### 属性自动完成 {#attribute-auto-completion}

1. 在HTML属性中，键入 `sly`。 属性自动完成 `data-sly-`。
1. 在下拉列表中选择HTL属性。

### 表达式自动完成 {#expression-auto-completion}

在表达式中， `${}`常用变量名称会自动完成。

## 更多信息 {#more-information}

AEM Brackets Extension是一个开放源码项目，由 [Adobe Marketing Cloud](https://github.com/Adobe-Marketing-Cloud) 组织在GitHub上根据Apache License 2.0版托管：

* 代码存储库： [https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension](https://github.com/Adobe-Marketing-Cloud/aem-sightly-brackets-extension)
* Apache License，版本2.0: [https://www.apache.org/licenses/LICENSE-2.0.html](https://www.apache.org/licenses/LICENSE-2.0.html)

Brackets代码编辑器也是一个开放源码项目，由Adobe Systems Incorporated组织在GitHub上 [托管](https://github.com/adobe) :

* 代码存储库： [https://github.com/adobe/brackets](https://github.com/adobe/brackets)

尽情贡献吧！
