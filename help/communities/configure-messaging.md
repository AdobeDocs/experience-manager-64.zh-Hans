---
title: 消息功能
seo-title: 消息功能
description: 配置消息传递组件
seo-description: 配置消息传递组件
uuid: 29ab63b6-67a1-4eb8-8cf8-c1ff52ff2bac
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 88ee8573-58c4-42cd-8e36-2ea4a0d654e4
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87
workflow-type: tm+mt
source-wordcount: '940'
ht-degree: 0%

---


# 消息功能 {#messaging-feature}

除了在论坛和评论中发生的公开可见的互动外，AEM Communities的消息传递功能使社区成员能够更加私下地彼此互动。

创建社区站点时可 [能会包](overview.md#communitiessites) 含此功能。

消息功能可以：

* 向一个或多个社区成员发送消息
* 向社区成员组发送消息
* 发送包含附件的邮件
* 转发消息
* 回复邮件
* 删除消息
* 恢复已删除的消息

要启用和修改消息功能，请访问

* [为管理员配置](messaging.md) “消息传递”
* [面向开发人员的](essentials-messaging.md) Messaging Essentials

>[!NOTE]
>
>在作者编辑模式 `Compose Message, Message, or Message List` 下，不支 `Communities`持将组件（在组件组中）添加到页面。

## 配置消息传递组件 {#configuring-messaging-components}

为社区站点启用消息传递后，将完全设置该站点，无需进一步配置。 如果需要更改默认配置，则会提供此信息。

### 配置消息列表（消息框） {#configuring-message-list-messagebox}

要修改消息传递功能的收件箱、已发送 **项目和废纸篓页面**&#x200B;的邮件列表 **，请打**&#x200B;开该站点，以创作编辑 ****[](sites-console.md#authoring-site-content)模式。

在模 `Preview` 式中，选择 **[!UICONTROL 消息链]** 接以打开主消息页面。 然后，选 **[!UICONTROL 择“收件箱”、“已发送项目”或]** “废纸篓”，为该邮件列表配置组件。

在模 `Edit` 式中，选择页面上的组件。

要访问配置对话框，必须通过选择图标来取消继 `link`承。

配置完成后，必须通过选择图标来恢复继 `broken link` 承。

![chlimage_1-396](assets/chlimage_1-396.png)

取消继承后，可以选择图标以 `configure` 打开配置对话框。

![chlimage_1-397](assets/chlimage_1-397.png)

#### Basic tab {#basic-tab}

![chlimage_1-398](assets/chlimage_1-398.png)

* **[!UICONTROL 服务选择器]**(*必需*)将其设置为“AEM Communities消息 `serviceSelector.name` 操作服 [务”属性的值](messaging.md#messaging-operations-service)。

* **[!UICONTROL 合成页]**(*必需*)成员单击按钮时要打开的 `Reply` 页面。 目标页面应包含合 **[!UICONTROL 成消息]** 。

* **[!UICONTROL 作为资源的回复/视图]**&#x200B;如果选中此选项，则回复URL和视图URL将引用某个资源，否则数据将作为查询参数在URL中传递。

* **[!UICONTROL 用户档案显示]**&#x200B;表单用于显示发件人用户档案的用户档案表单。

* **[!UICONTROL 废纸篓文]**&#x200B;件夹如果选中，则此邮件列表组件将仅显示标记为已删除（废纸篓）的邮件。

* **[!UICONTROL 文件夹路径]**(*必需*)引用为AEM Communities消息 `inbox.path.name` 操作服务 `sentitems.path.name` 中设置 [的值和值](messaging.md#messaging-operations-service)。 为配置时， `Inbox`请使用值添加一个条目( `inbox.path.name`)。 为配置时， `Outbox`请使用值添加一个条目( `sentitems.path.name`)。 配置时， `Trash`添加两个同时具有这两个值的条目。

#### 显示选项卡 {#display-tab}

![chlimage_1-399](assets/chlimage_1-399.png)

* **[!UICONTROL 标记读取按]**&#x200B;钮如果选中，则显示 
`Read`按钮。

* **[!UICONTROL 标记为未读按]**&#x200B;钮如果选中，则显示 
`Mark Unread` 按钮。

* **[!UICONTROL 删除按钮]**&#x200B;如果选中，则显示 
`Delete`按钮。 如果同时选中，将重复 **`Message Options`** 删除功能。

* **[!UICONTROL 消息选项]**&#x200B;如果选中，则显示 
**`Reply`**、 **`Reply All`**&#x200B;和 **`Forward`** 按钮 **`Delete`** ，允许重新发送或删除消息。 如果同时选中，将重复 **`Delete Button`** 删除功能。

* **[!UICONTROL 每页消息]**&#x200B;指定的数量是分页方案中每页显示的最大消息数。 如果未指定任何数字（留空），则显示所有消息，且不显示分页。

* **[!UICONTROL 时间戳模]**&#x200B;式为一种或多种语言提供时间戳模式。 默认值为en、de、fr、it、es、ja、zh_CN、ko_KR。

* **[!UICONTROL 显示用户]**&#x200B;选择 
**`Sender`** 或确 **`Recipients`** 定是否显示发送者或收件人。

### 配置合成消息 {#configuring-compose-message}

要修改合成消息页面的配置，请以作者编辑模式 [打开站点](sites-console.md#authoring-site-content)。

在模 `Preview`式中，选择“ **[!UICONTROL 消息]** ”链接以打开主消息页面。 然后选择“新建消息”按钮以打 `Compose Message` 开页面。

在模 `Edit` 式中，在包含消息正文的页面上选择主组件。

要访问配置对话框，必须通过选择图标来取消继 `link`承。

配置完成后，必须通过选择图标来恢复继 `broken link` 承。

![chlimage_1-400](assets/chlimage_1-400.png)

取消继承后，可以选择图标以 `configure` 打开配置对话框。

![chlimage_1-401](assets/chlimage_1-401.png)

#### Basic tab {#basic-tab-1}

![chlimage_1-402](assets/chlimage_1-402.png)

* **[!UICONTROL 重定向]** URL输入发送消息后显示的页面的URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 取消URL]**&#x200B;输入发送方取消消息时显示的页面URL。 例如， 
`../messaging.html`。

* **[!UICONTROL 邮件主题的最大长]**&#x200B;度“主题”字段中允许的最大字符数。 例如，500。 默认值为无限制。

* **[!UICONTROL 消息正文的最大长]**&#x200B;度“内容”字段中允许的最大字符数。 例如，10000。 默认值为无限制。

* **[!UICONTROL 服务选择器]**(*必需*)将其设置为“AEM Communities消息 **`serviceSelector.name`** 操作服 [务”属性的值](messaging.md#messaging-operations-service)。

#### 显示选项卡 {#display-tab-1}

![chlimage_1-403](assets/chlimage_1-403.png)

* **[!UICONTROL 显示主题字段]**&#x200B;如果选中，则显示 
`Subject` 字段，然后启用向邮件添加主题。 未选中默认值。

* **[!UICONTROL 主题标]**&#x200B;签输入要在 
`Subject` 字段. Default is `Subject`.

* **[!UICONTROL 显示附加文件字段]**&#x200B;如果选中，则显示 
`Attachment` 字段并启用向邮件中添加文件附件。 未选中默认值。

* **[!UICONTROL 附加文件]**&#x200B;标签输入要在 
`Attachment` 字段. Default is **`Attach File`**.

* **[!UICONTROL 显示内容字段]**&#x200B;如果选中，则显示 
`Content` 字段，并启用添加消息正文。 未选中默认值。

* **[!UICONTROL 内容标]**&#x200B;签输入要在 
`Content` 字段. Default is **`Body`**.

* **[!UICONTROL 使用富文本编]**&#x200B;辑器如果选中，则表示自定义内容文本框的使用情况与其自己的富文本编辑器。 未选中默认值。

* **[!UICONTROL 时间戳模]**&#x200B;式为一种或多种语言提供时间戳模式。 默认值为en、de、fr、it、es、ja、zh_CN、ko_KR。

