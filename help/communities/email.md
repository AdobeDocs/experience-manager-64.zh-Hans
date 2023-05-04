---
title: 配置电子邮件
seo-title: Configuring Email
description: 社区的电子邮件配置
seo-description: Email configuration for Communities
uuid: e8422cc2-1594-43b0-b587-82825636cec1
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b4d38e45-eaa0-4ace-a885-a2e84fdfd5a1
pagetitle: Configuring Email
role: Admin
exl-id: 0a0222e7-ca30-4603-94ad-582005b2de11
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 2%

---

# 配置电子邮件 {#configuring-email}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM Communities使用电子邮件

* [社区通知](notifications.md)
* [Communities 订阅](subscriptions.md)

默认情况下，电子邮件功能无法正常使用，因为它需要指定SMTP服务器和SMTP用户。

>[!CAUTION]
>
>通知和订阅的电子邮件必须仅在 [主发布者](deploy-communities.md#primary-publisher).

## 默认邮件服务配置 {#default-mail-service-configuration}

通知和订阅均需要默认邮件服务。

* 在主发布者上
* 使用管理员权限登录
* 访问 [Web控制台](../../help/sites-deploying/configuring-osgi.md)

   * 例如， [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* 找到 `Day CQ Mail Service`
* 选择编辑图标

这基于 [配置电子邮件通知](../../help/sites-administering/notification.md)但是，这个领域 `"From" address` is *not* 必需，且应留空。

例如（仅用于说明目的的值填充）：

![chlimage_1-98](assets/chlimage_1-98.png)

* **[!UICONTROL SMTP服务器主机名]**: *（必需）* 要使用的SMTP服务器。

* **[!UICONTROL SMTP服务器端口]** *（必需）* SMTP服务器端口必须为25或更高。

* **[!UICONTROL SMTP用户]**: *（必需）* SMTP用户。

* **[!UICONTROL SMTP密码]**: *（必需）* SMTP用户的密码。

* **[!UICONTROL “发件人”地址]**:留空
* **[!UICONTROL SMTP使用SSL]**:如果选中，将发送安全电子邮件。 确保将端口设置为465或SMTP服务器所需的端口。
* **[!UICONTROL 调试电子邮件]**:如果选中此项，则启用SMTP服务器交互的日志记录。

## AEM Communities电子邮件配置 {#aem-communities-email-configuration}

一旦 [默认邮件服务](#default-mail-service-configuration) ，则 `AEM Communities Email Reply Configuration` 此版本中包含的OSGi配置可正常使用。

在允许通过电子邮件回复时，只需进一步配置订阅的实例。

1. ` [email](#configuration-for-notifications)` 实例

   不支持回复电子邮件且不应更改的通知

1. ` [subscriptions-email](#configuration-for-subscriptions)` 实例

   需要配置以完全启用通过回复电子邮件创建帖子的功能

要访问社区电子邮件配置实例，请执行以下操作：

* 在主发布者上
* 使用管理员权限登录
* 访问 [Web控制台](../../help/sites-deploying/configuring-osgi.md)

   * 例如， [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* 定位 `AEM Communities Email Reply Configuration`

![chlimage_1-99](assets/chlimage_1-99.png)

### 通知配置 {#configuration-for-notifications}

的实例 `AEM Communities Email Reply Configuration` 带有“名称”电子邮件的OSGi配置适用于通知功能。 此功能不包括电子邮件回复。

不应更改此配置。

* 找到 `AEM Communities Email Reply Configuration`
* 选择编辑图标
* 验证 **名称** is `email`

* 验证 **通过回复电子邮件创建帖子** is `unchecked`

![chlimage_1-100](assets/chlimage_1-100.png)

### 订阅配置 {#configuration-for-subscriptions}

对于社区订阅，可以启用或禁用成员通过回复电子邮件来发布内容的功能。

* 找到 `AEM Communities Email Reply Configuration`
* 选择编辑图标
* 验证 **名称** is `subscriptions-email`

![chlimage_1-101](assets/chlimage_1-101.png)

* **[!UICONTROL 名称]** : *（必需）* `subscriptions-email`. 请勿编辑。

* **[!UICONTROL 通过回复电子邮件创建帖子]**:如果选中，订阅电子邮件的收件人可以通过发送回复来发布内容。 默认选中。
* **[!UICONTROL 将跟踪的ID添加到标题]**:默认为 `Reply-To`.

* **[!UICONTROL 主题的最大长度]**:如果将跟踪器ID添加到主题行，则这是主题的最大长度（不包括跟踪的ID），在此之后将会对其进行裁剪。 请注意，这应尽可能小，以避免跟踪的ID信息丢失。 默认值为200。
* **[!UICONTROL 电子邮件“发件人”地址]**: *（必需）* 通知电子邮件将从中发送的地址。 可能是相同的 **SMTP用户** 为 [默认邮件服务](#configuredefaultmailservice). 默认为 `no-reply@example.com`.

* **[!UICONTROL 回复分隔符]**:如果将跟踪器ID添加到回复标头，则将使用此分隔符。 默认为 `+` （加号）。

* **[!UICONTROL 主题中的跟踪器ID前缀]**:如果将跟踪器ID添加到主题行，则将使用此前缀。 默认为 `post#`.

* **[!UICONTROL 消息正文中的跟踪器ID前缀]**:如果将跟踪器ID添加到消息正文，则将使用此前缀。 默认为 `Please do not remove this:`.

* **[!UICONTROL 电子邮件作为HTML]**:如果选中此项，则电子邮件的“内容类型”将设置为 `"text/html;charset=utf-8"`. 默认选中。

* **[!UICONTROL 默认用户名]**:此名称将不用于任何姓名用户。 默认为 `no-reply@example.com`.

* **[!UICONTROL 模板根路径]**:电子邮件是使用存储在此根路径中的模板生成的。 默认为 `/etc/community/templates/subscriptions-email`.

## 配置轮询导入程序 {#configure-polling-importer}

要将电子邮件引入存储库，必须配置轮询导入器并在存储库中手动配置其属性。

### 添加新轮询导入程序 {#add-new-polling-importer}

* 在主发布者上
* 使用管理员权限登录
* 浏览到轮询导入器控制台例如， [http://localhost:4503/etc/importers/polling.html](http://localhost:4503/etc/importers/polling.html)
* 选择 **[!UICONTROL 添加]**

![chlimage_1-102](assets/chlimage_1-102.png)

* **[!UICONTROL 类型]**: *（必需）* 下拉以选择 `POP3 (over SSL).`

* **[!UICONTROL URL]**: *（必需）* 出站邮件服务器。 例如，`pop.gmail.com:995/INBOX?username=community-emailgmail.com&password=****`

* **[!UICONTROL 导入路径]**&amp;ast; *（必需）* 设置为 `/content/usergenerated/mailFolder/postEmails`
浏览到 
`postEmails`文件夹，选择 **确定**

* **[!UICONTROL 更新间隔（以秒为单位）]**: *（可选）* 为默认邮件服务配置的邮件服务器可能对更新间隔值有要求。 例如，Gmail可能需要间隔 `300`.

* **[!UICONTROL 登录]**: *（可选）*

* **[!UICONTROL 密码]**: *（可选）*

* 选择 **[!UICONTROL 确定]**

### 调整新轮询导入程序的协议 {#adjust-protocol-for-new-polling-importer}

保存新轮询配置后，需要进一步修改订阅电子邮件导入器的属性，以便从 `POP3` to `emailreply`

使用 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* 在主发布者上
* 使用管理员权限登录
* 浏览到 [https://&lt;server>:&lt;port>/crx/de/index.jsp#/etc/importers/polling](http://localhost:4503/crx/de/index.jsp#/etc/importers/polling)
* 选择新创建的配置
* 修改以下属性

   * **feedType**:替换 `pop3s` with **`emailreply`**
   * **来源**:替换源协议 `pop3s://` with **`emailreply://`**

![chlimage_1-103](assets/chlimage_1-103.png)

红色三角形表示已修改的属性。 确保保存更改：

* 选择 **[!UICONTROL 全部保存]**
