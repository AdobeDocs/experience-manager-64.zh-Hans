---
title: 消息传送功能
seo-title: Messaging Feature
description: 配置消息传送组件
seo-description: Configuring Messaging components
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 1%

---

# 消息传送功能 {#messaging-feature}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

除了在论坛和评论中发生的公开可见的交互之外，AEM Communities的报文传送功能还使社区成员能够更加私密地彼此交互。

当 [社区网站](overview.md#communitiessites) 创建时。

消息传送功能提供以下功能：

* 向一个或多个社区成员发送消息
* 向社区成员组发送消息
* 发送带有附件的邮件
* 转发消息
* 回复消息
* 删除消息
* 恢复已删除的消息

要启用和修改消息传送功能，请访问

* [配置消息传送](messaging.md) 对于管理员
* [消息传送要点](essentials-messaging.md) 适用于开发人员

>[!NOTE]
>
>不支持添加 `Compose Message, Message, or Message List` 组件(可在 `Communities`组件组)到“创作编辑”模式下的页面。

## 配置消息传送组件 {#configuring-messaging-components}

为社区站点启用消息传送后，该站点将完全设置，无需进一步配置。 如果需要更改默认配置，则会提供此信息。

### 配置消息列表（消息框） {#configuring-message-list-messagebox}

为了修改 **收件箱**, **已发送项目**&#x200B;和 **垃圾** 消息传送功能的页面，在 [创作编辑模式](sites-console.md#authoring-site-content).

在 `Preview` 模式，选择 **[!UICONTROL 消息]** 链接以打开主消息传送页面。 然后，选择 **[!UICONTROL 收件箱、已发送项目或垃圾桶]** 以配置该消息列表的组件。

在 `Edit` 模式下，在页面上选择组件。

要访问配置对话框，需要通过选择 `link`图标。

配置完成后，需要通过选择 `broken link` 图标。

![chlimage_1-396](assets/chlimage_1-396.png)

取消继承后，可以选择 `configure` 图标以打开配置对话框。

![chlimage_1-397](assets/chlimage_1-397.png)

#### “基本”选项卡 {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL 服务选择器]**
(*必需*)将其设置为属性的值 `serviceSelector.name` 从 [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service).

* **[!UICONTROL 撰写页面]**
(*必需*)成员单击 `Reply` 按钮。 目标页面应包含 **[!UICONTROL 撰写消息]** 表单。

* **[!UICONTROL 回复/查看为资源]**
如果选中此项，则回复URL和查看URL将引用资源，否则数据将作为查询参数在URL中传递。

* **[!UICONTROL 配置文件显示表单]**
用于显示发件人配置文件的配置文件表单。

* **[!UICONTROL 垃圾桶文件夹]**
如果选中，此消息列表组件仅显示标记为已删除（垃圾桶）的消息。

* **[!UICONTROL 文件夹路径]**
(*必需*)引用为 `inbox.path.name` 和 `sentitems.path.name` 在 [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service). 为 `Inbox`，使用的值添加一个条目 `inbox.path.name`. 为 `Outbox`，使用的值添加一个条目 `sentitems.path.name`. 配置 `Trash`，则添加两个具有这两个值的条目。

#### “显示”选项卡 {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL “标记读取”按钮]**
如果选中，则显示 
`Read`按钮，将消息标记为已读。

* **[!UICONTROL “标记未读”按钮]**
如果选中，则显示 
`Mark Unread` 按钮，将消息标记为已读。

* **[!UICONTROL “删除”按钮]**
如果选中，则显示 
`Delete`按钮，将消息标记为已读。 将在 **`Message Options`** 中。

* **[!UICONTROL 消息选项]**
如果选中，则显示 
**`Reply`**, **`Reply All`**, **`Forward`** 和 **`Delete`** 允许重新发送或删除消息的按钮。 将在 **`Delete Button`** 中。

* **[!UICONTROL 每页消息数]**
指定的编号是分页方案中每页显示的消息的最大数量。 如果未指定数字（留空），则会显示所有消息，并且不进行分页。

* **[!UICONTROL 时间戳模式]**
为一种或多种语言提供时间戳模式。 默认值为en、de、fr、it、es、ja、zh_CN、ko_KR。

* **[!UICONTROL 显示用户]**
选择 
**`Sender`** 或 **`Recipients`** 以确定是显示发件人还是收件人。

### 配置撰写消息 {#configuring-compose-message}

要修改撰写消息页面的配置，请在 [创作编辑模式](sites-console.md#authoring-site-content).

在 `Preview`模式，选择 **[!UICONTROL 消息]** 链接以打开主消息传送页面。 然后，选择New Message按钮以打开 `Compose Message` 页面……

在 `Edit` 模式下，在包含消息正文的页面上选择主组件。

要访问配置对话框，需要通过选择 `link`图标。

配置完成后，需要通过选择 `broken link` 图标。

![chlimage_1-400](assets/chlimage_1-400.png)

取消继承后，可以选择 `configure` 图标以打开配置对话框。

![chlimage_1-401](assets/chlimage_1-401.png)

#### “基本”选项卡 {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL 重定向URL]**
输入发送消息后显示的页面URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 取消URL]**
输入发件人取消消息时显示的页面URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 消息主体的最大长度]**
“主题”字段中允许的最大字符数。 例如，500。 默认为无限制。

* **[!UICONTROL 消息正文的最大长度]**
“内容”字段中允许的最大字符数。 例如，10000。 默认为无限制。

* **[!UICONTROL 服务选择器]**
(*必需*)将其设置为属性的值 **`serviceSelector.name`** 从 [AEM Communities Messaging Operations Service](messaging.md#messaging-operations-service).

#### “显示”选项卡 {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL 显示主题字段]**
如果选中，则显示 
`Subject` 字段，并启用向消息添加主题。 未选中默认值。

* **[!UICONTROL 主题标签]**
输入要在 
`Subject` 字段. 默认为 `Subject`.

* **[!UICONTROL 显示附加文件字段]**
如果选中，则显示 
`Attachment` 字段，并启用向消息添加文件附件的功能。 未选中默认值。

* **[!UICONTROL 附加文件标签]**
输入要在 
`Attachment` 字段. 默认为 **`Attach File`**.

* **[!UICONTROL 显示内容字段]**
如果选中，则显示 
`Content` 字段，并启用添加消息正文。 未选中默认值。

* **[!UICONTROL 内容标签]**
输入要在 
`Content` 字段. 默认为 **`Body`**.

* **[!UICONTROL 使用富文本编辑器]**
如果选中，则表示使用具有其自身富文本编辑器的自定义内容文本框。 未选中默认值。

* **[!UICONTROL 时间戳模式]**
为一种或多种语言提供时间戳模式。 默认值为en、de、fr、it、es、ja、zh_CN、ko_KR。
