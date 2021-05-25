---
title: 消息传送功能
seo-title: 消息传送功能
description: 配置消息传送组件
seo-description: 配置消息传送组件
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
exl-id: e03cf05c-2469-4883-ae7b-9d7e6660b71f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 0%

---

# 消息传送功能{#messaging-feature}

除了在论坛和评论中发生的公开可见的交互之外，AEM Communities的报文传送功能还使社区成员能够更加私密地彼此交互。

创建[社区站点](overview.md#communitiessites)时，可能会包含此功能。

消息传送功能提供以下功能：

* 向一个或多个社区成员发送消息
* 向社区成员组发送消息
* 发送带有附件的邮件
* 转发消息
* 回复消息
* 删除消息
* 恢复已删除的消息

要启用和修改消息传送功能，请访问

* [为管理](messaging.md) 员配置消息
* [对开发人](essentials-messaging.md) 员而言的消息传送要求

>[!NOTE]
>
>不支持在创作编辑模式下将`Compose Message, Message, or Message List`组件（位于`Communities`组件组中）添加到页面。

## 配置消息传送组件{#configuring-messaging-components}

为社区站点启用消息传送后，该站点将完全设置，无需进一步配置。 如果需要更改默认配置，则会提供此信息。

### 配置消息列表（消息框）{#configuring-message-list-messagebox}

为了修改&#x200B;**收件箱**、**已发送项目**&#x200B;和&#x200B;**垃圾桶**&#x200B;页面的邮件列表配置，请在[作者编辑模式](sites-console.md#authoring-site-content)中打开该站点。

在`Preview`模式下，选择&#x200B;**[!UICONTROL 消息]**&#x200B;链接以打开主消息传送页面。 然后，选择&#x200B;**[!UICONTROL 收件箱、已发送项目或垃圾桶]**&#x200B;以配置该消息列表的组件。

在`Edit`模式下，选择页面上的组件。

要访问配置对话框，必须通过选择`link`图标来取消继承。

配置完成后，需要通过选择`broken link`图标来恢复继承。

![chlimage_1-396](assets/chlimage_1-396.png)

取消继承后，将可以选择`configure`图标以打开配置对话框。

![chlimage_1-397](assets/chlimage_1-397.png)

#### 基本选项卡{#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL 服务选择器]**
(*必需*)将此参数设置为AEM Communities Messaging Operations `serviceSelector.name` 服务 [中属性的值](messaging.md#messaging-operations-service)。

* **[!UICONTROL 撰写页面]**
(*必需*)成员单击按钮时要打开的 `Reply` 页面。目标页面应包含&#x200B;**[!UICONTROL 撰写消息]**&#x200B;窗体。

* **[!UICONTROL 作为资源进行]**
回复/查看如果选中此选项，回复URL和查看URL将引用某个资源，否则数据将作为查询参数在URL中传递。

* **[!UICONTROL 配置文]**
件显示表单用于显示发件人配置文件的配置文件表单。

* **[!UICONTROL 垃圾桶]**
文件夹如果选中此选项，则此消息列表组件仅显示标记为已删除（垃圾桶）的消息。

* **[!UICONTROL 文件夹路径]**
(*必需*)引用AEM Communities Messaging Operations Service `inbox.path.name` 中 `sentitems.path.name` 和 [的值集](messaging.md#messaging-operations-service)。为`Inbox`配置时，请使用`inbox.path.name`值添加一个条目。 为`Outbox`配置时，请使用`sentitems.path.name`值添加一个条目。 为`Trash`配置时，请添加两个具有这两个值的条目。

#### 显示选项卡{#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL 标记读取]**
按钮如果选中，则显示 
`Read`按钮，将消息标记为已读。

* **[!UICONTROL 标记未读]**
按钮如果选中，则显示 
`Mark Unread` 按钮，将消息标记为已读。

* **[!UICONTROL 删除]**
按钮如果选中，则显示 
`Delete`按钮，将消息标记为已读。如果同时选中&#x200B;**`Message Options`**，则将复制删除功能。

* **[!UICONTROL 消息选]**
项如果选中，则显示 
**`Reply`**、和 **`Reply All`**&#x200B;按钮 **`Forward`** , **`Delete`** 允许重新发送或删除消息。如果同时选中&#x200B;**`Delete Button`**，则将复制删除功能。

* **[!UICONTROL 每页消]**
息指定的编号是分页方案中每页显示的最大消息数。如果未指定数字（留空），则会显示所有消息，并且不进行分页。

* **[!UICONTROL 时间戳]**
模式为一种或多种语言提供时间戳模式。默认值为en、de、fr、it、es、ja、zh_CN、ko_KR。

* **[!UICONTROL 显示用]**
户选择 
**`Sender`** 或 **`Recipients`** 确定是显示发件人还是收件人。

### 配置撰写消息{#configuring-compose-message}

要修改撰写消息页面的配置，请在[作者编辑模式](sites-console.md#authoring-site-content)中打开该站点。

在`Preview`模式下，选择&#x200B;**[!UICONTROL Messages]**&#x200B;链接以打开主消息传送页面。 然后，选择“新建消息”按钮以打开`Compose Message`页面。

在`Edit`模式下，在包含消息正文的页面上选择主组件。

要访问配置对话框，必须通过选择`link`图标来取消继承。

配置完成后，需要通过选择`broken link`图标来恢复继承。

![chlimage_1-400](assets/chlimage_1-400.png)

取消继承后，将可以选择`configure`图标以打开配置对话框。

![chlimage_1-401](assets/chlimage_1-401.png)

#### 基本选项卡{#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL 重定]**
向URL输入发送消息后显示的页面URL。例如， 
`../messaging.html`。

* **[!UICONTROL 取消]**
URL输入发件人取消消息时显示的页面URL。例如， 
`../messaging.html`。

* **[!UICONTROL 消息主题的最]**
大长度“主题”字段中允许的最大字符数。例如，500。 默认为无限制。

* **[!UICONTROL 消息正文的最]**
大长度“内容”字段中允许的最大字符数。例如，10000。 默认为无限制。

* **[!UICONTROL 服务选择器]**
(*必需*)将此参数设置为AEM Communities Messaging Operations **`serviceSelector.name`** 服务 [中属性的值](messaging.md#messaging-operations-service)。

#### 显示选项卡{#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL 显示主题]**
字段如果选中，则显示 
`Subject` 字段，并启用向消息添加主题。未选中默认值。

* **[!UICONTROL 主题]**
标签输入要在 
`Subject` 字段. 默认值为`Subject`。

* **[!UICONTROL 显示附加文]**
件字段如果选中，则显示 
`Attachment` 字段，并启用向消息添加文件附件的功能。未选中默认值。

* **[!UICONTROL 附加文]**
件标签输入要在 
`Attachment` 字段. 默认值为&#x200B;**`Attach File`**。

* **[!UICONTROL 显示内容字]**
段如果选中，则显示 
`Content` 字段，并启用添加消息正文。未选中默认值。

* **[!UICONTROL 内容]**
标签输入要在 
`Content` 字段. 默认值为&#x200B;**`Body`**。

* **[!UICONTROL 选中富文本编]**
辑器如果选中此选项，则表示使用自定义内容文本框及其自己的富文本编辑器。未选中默认值。

* **[!UICONTROL 时间戳]**
模式为一种或多种语言提供时间戳模式。默认值为en、de、fr、it、es、ja、zh_CN、ko_KR。
