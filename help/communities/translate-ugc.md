---
title: 翻译用户生成的内容
seo-title: Translating User Generated Content
description: 翻译功能的工作原理
seo-description: How the translation feature works
uuid: 7ee3242c-2aca-4787-a60d-b807161401ad
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: bfaf80c5-448b-47fb-9f22-57ee0eb169b2
role: Admin
exl-id: b8cbc429-b0c3-4f6e-a15f-4aef54733c8e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---

# 翻译用户生成的内容 {#translating-user-generated-content}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM Communities的翻译功能扩展了 [翻译页面内容](../../help/sites-administering/translation.md) 发布到社区站点的用户生成内容(UGC) [社交组件框架(SCF)组件](scf.md).

UGC的翻译通过消除语言障碍，站点访客和成员可以体验到全球社区。

例如，假设，

* 一位来自法国的成员在一家跨国烹饪网站的社区论坛上发布了法文食谱
* 另一位来自日本的成员使用翻译功能触发从法语到日语的方法的翻译
* 从日本来的会员读完食谱后，用日语发表评论
* 来自法国的成员使用翻译功能将日语评论翻译成法语
* 全球交流！

## 概述 {#overview}

本文档的这一部分专门讨论了翻译服务如何在了解如何将AEM连接到 [翻译服务提供商](../../help/sites-administering/translation.md#connectingtoatranslationserviceprovider) 并通过配置 [翻译集成框架](../../help/sites-administering/tc-tic.md).

当翻译服务提供商与站点关联时，站点的每个语言副本将维护其自己通过SCF组件（如注释）发布的UGC线程。

当除了翻译服务提供者之外配置翻译集成框架时，站点的每个语言副本可以共享UGC的单个线程，从而提供跨语言副本的全局通信。 配置的 [全局共享存储](#global-translation-of-ugc) 无论从哪个语言副本查看整个线程，都可以看到该线程。 此外，可以配置多个翻译集成配置，以指定不同的全局共享存储，用于诸如按区域的全局参与者的逻辑分组。

## 默认翻译服务 {#the-default-translation-service}

AEM Communities包含 [试用许可](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license) a [默认翻译服务](../../help/sites-administering/tc-msconf.md) 启用了多种语言。

When [创建社区站点](sites-console.md)，默认翻译服务在 `Allow Machine Translation` 从 [翻译](sites-console.md#translation) 子面板。

>[!CAUTION]
>
>默认翻译服务仅用于演示。
>
>对于生产系统，需要获得许可的翻译服务。 如果未获得许可，则默认翻译服务应为 [关闭](../../help/sites-administering/tc-msconf.md#microsoft-translator-trial-license-geometrixx-outdoors).

## UGC的全球翻译 {#global-translation-of-ugc}

当网站具有多个 [语言副本](../../help/sites-administering/tc-prep.md)，则默认翻译服务不会识别在一个网站上输入的UGC可能与在另一个网站上输入的UGC相关，因为当UGC本质上是由同一组件（包含该组件的页面的语言副本）生成时。

这类似于讨论一个主题的一群人，他们不知道在他们自己之外的群体中发表评论，而在一个参与一个对话的大型群体中，每个人都是这样。

如果需要“一个组对话”，则可以在具有多个语言副本的网站上启用全局翻译，这样无论从哪种语言副本查看整个线程，都可以看到该线程。

例如，如果在基站上建立了论坛、创建了语言副本并启用了全局翻译，则以一个语言副本发布到论坛的主题将显示在所有语言副本中。 任何答复也是如此，无论答复是从哪种语文中输入的。 结果是，无论从哪种语言副本查看主题，都会显示该主题及其整个回复线程。

>[!CAUTION]
>
>全局翻译之前存在的任何UGC都不再可见。
>
>当UGC仍在 [公用商店](working-with-srp.md)，则会在语言特定的UGC位置下方找到，而配置全局翻译后添加的新内容将从全局共享存储位置检索。
>
>没有用于将语言特定内容移动或合并到全局共享存储的迁移工具。

### 翻译集成配置 {#translation-integration-configuration}

要创建新的翻译集成，该集成将翻译服务连接器与创作实例上的网站集成在一起：

* 以管理员身份登录
* 从 [主菜单](http://localhost:4502/)
* 选择 **[!UICONTROL 工具]**
* 选择 **[!UICONTROL 操作]**
* 选择 **[!UICONTROL 云]**
* 选择 **[!UICONTROL Cloud Services]**
* 向下滚动到 **[!UICONTROL 翻译集成]**

![chlimage_1-65](assets/chlimage_1-65.png)

* 选择 **[!UICONTROL 显示配置]**

![chlimage_1-66](assets/chlimage_1-66.png)

* 选择 `[+]` 图标 **[!UICONTROL 可用配置]** 创建新配置

#### 创建配置对话框 {#create-configuration-dialog}

![chlimage_1-67](assets/chlimage_1-67.png)

* **[!UICONTROL 父配置]**
（必需）通常保留为默认值。 默认为 
`/etc/cloudservices/translation`。

* **[!UICONTROL 标题]**
（必需）输入您选择的显示标题。 没有默认值。

* **[!UICONTROL 名称]**
（可选）输入配置的名称。 默认为基于标题的节点名称。

* 选择 **[!UICONTROL 创建]**

#### 翻译配置对话框 {#translation-config-dialog}

![chlimage_1-68](assets/chlimage_1-68.png)

有关详细说明，请访问 [创建翻译集成配置](../../help/sites-administering/tc-tic.md#creating-a-translation-integration-configuration)

* **[!UICONTROL 站点]** 选项卡：可以保留为默认值
* **[!UICONTROL 社区]** 选项卡：
   * **[!UICONTROL 翻译提供商]**
从下拉列表中选择翻译提供程序。 默认为 
`microsoft`，试用版服务。

   * **[!UICONTROL 内容类别]**
选择描述所翻译内容的类别。 默认为 
`General.`

   * **[!UICONTROL 选择区域设置……]**
（可选）通过选择存储UGC的区域设置，所有语言副本中的帖子将显示在一个全局对话中。 根据惯例，选择 [基本语言](sites-console.md#translation) 中。 选择 `No Common Store` 将禁用全局翻译。 默认情况下，全局翻译处于禁用状态。

* **[!UICONTROL 资产]** 选项卡：可以保留为默认值
* 选择 **[!UICONTROL 确定]**

#### 激活 {#activation}

需要将新的翻译集成云服务激活到发布环境。 与网站关联后，如果尚未激活，则在发布与其关联的页面时，激活工作流将提示发布此云服务配置。

## 管理翻译设置 {#managing-translation-settings}

>[!NOTE]
>
>**首选语言**
>
>为了检测帖子的语言是否与首选语言不同，必须建立网站访客的首选语言。
>
>首选语言是在网站访客登录并指定了语言首选项时，用户配置文件中设置的语言首选项。
>
>如果网站访客是匿名访客或在其配置文件中未指定语言首选项，则首选语言是页面模板的基本语言。

### 用户首选项 {#user-preference}

#### 用户配置文件 {#user-profile}

所有社区站点都提供一个用户配置文件，登录成员后，用户配置文件可以进行编辑，以便向社区标识自己并设置其首选项。

其中一种设置是是否始终以其首选语言显示社区内容。 默认情况下，设置未设置，且将默认为系统设置。 用户可以将设置更改为“开”或“关”，从而覆盖系统设置。

当页面自动翻译为用户首选语言时，仍可使用用于显示原始文本和改进翻译的UI。

![chlimage_1-69](assets/chlimage_1-69.png)

### 社区站点设置 {#community-site-setting}

创建社区站点后，可以启用和配置翻译选项。 翻译设置对匿名网站访客可能查看的内容有效，但会被用户的配置文件设置覆盖。
