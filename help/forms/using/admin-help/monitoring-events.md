---
title: 监控事件
seo-title: Monitoring events
description: 启用审核功能后，文档安全功能允许您监视某些类型的事件。 您可以使用文档安全性轻松搜索事件列表并对其进行排序。
seo-description: When the auditing capability is enabled, document security enables you to monitor certain types of events. You can easily search and sort the events list using the document security.
uuid: 22add6ff-536d-4cb9-8eac-b72cad5c3ecf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 379957bf-0634-4182-b269-1b010da4c90f
feature: Document Security
exl-id: 0c4a846f-4e31-435b-a6f6-d0b7c4cd1259
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 0%

---

# 监控事件 {#monitoring-events}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

启用审核功能后，文档安全功能允许您监视某些类型的事件。 您能够看到的事件取决于您的角色：

**用户：** 可以查看其受策略保护的文档以及接收和使用的任何受保护文档的审核事件。

**策略集协调员：** 可以查看受策略保护的文档的已审核事件（包括文档和策略事件）及其策略集。

**管理员：** 可以查看与所有受策略保护的文档和用户相关的已审核事件。 管理员还可以跟踪其他类型的事件，包括用户、文档、策略和系统事件。

>[!NOTE]
>
>对受策略保护文档的副本执行的事件也作为原始受保护文档的事件进行跟踪。

(请参阅 [事件审核选项](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).)

如果未授权用户尝试查看文档或尝试使用不正确的用户名或密码登录，则记录失败事件。

>[!NOTE]
>
>如果编辑策略以删除匿名访问，则可能会记录文档的匿名访问失败事件。 当授权收件人尝试访问编辑的策略所保护的文档时，仍会尝试匿名访问，但会失败。

如果策略允许匿名用户访问，但管理员稍后会关闭对文档安全的匿名访问，则对使用该策略保护的文档的匿名访问将失败，并且该事件将不会被记录。

## 启用事件审核 {#enable-event-auditing}

要进行事件审核，必须满足以下设置要求：

* 系统或管理员必须为服务器启用审核功能。

   (请参阅 [配置事件审核和隐私设置](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings).)

* 用于保护文档的策略必须启用审核。 (请参阅 [创建和编辑策略](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## 搜索事件 {#search-for-an-event}

您可以搜索事件列表并查看有关事件的更多详细信息。 详细描述包括事件ID、描述、IP地址、组织、受影响的用户、事件发生的日期和时间、拒绝的活动和离线事件（用户在未连接到文档安全时尝试使用文档）等信息。

您可以使用事件搜索条件和事件发生日期的组合，在“事件”页面上搜索事件。 您可以搜索的事件取决于您的角色：

**用户：** 可以查看其受策略保护的文档以及接收和使用的任何受保护文档的审核事件。 以下搜索选项可用：

**与我相关的事件：** 用户可以找到他们创建或接收的任何受策略保护文档的事件。 例如，如果用户打开、查看或打印另一人保护的文档，则用户只会看到该文档的这些事件。

**与我的文档相关的事件：** 用户可以找到与自己受策略保护的文档相关的所有事件。 用户会看到每个处理其文档的人员生成的事件。

**策略集协调员：** 可以查看受策略保护的文档的已审核事件（包括文档和策略事件）及其策略集。 以下选项可用：

**记录我是策略集协调员的事件：** 具有查看事件权限的策略集协调员可以查找与其策略集中策略所保护的文档相关的事件。

**我是策略集协调员的策略事件：** 具有查看事件权限的策略集协调员可以从其策略集中查找与策略相关的事件。

**管理员：** 可以查看与所有受策略保护的文档和用户相关的已审核事件。 管理员还可以跟踪其他类型。 此外，管理员还可以根据用户类型进一步划分事件搜索：

**已知用户：** 用户位于源目录中或注册为外部用户。

**匿名用户：** 访问受允许匿名访问的策略保护的文档的未知用户。

**系统用户：** 服务器启动的事件，如目录同步。

1. 在文档安全页面上，单击事件。
1. 在查找列表中，选择要使用的搜索标准。 根据您在“查找”列表中的选择，将显示另一个列表，其中提供了其他搜索条件。 如果适用，在文本框中键入搜索条件。

   有关特定事件类型的更多详细信息，请参阅 [事件审核选项](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).

1. 在用户列表中，选择执行事件的用户类型：

   * 如果选择“已知用户”，则会显示第二个搜索框，您必须在其中键入用户的用户名或电子邮件地址。
   * 如果您不知道这些值，请单击通讯簿搜索图标以按用户名或电子邮件地址搜索用户。

1. 在日期列表中，选择日期范围选项。 如果选择“自定义日期”，则会显示相应框，其中您键入的日期格式为yyyy/mm/dd，或者您可以使用日期选取器指定日期范围：

   * 单击日历以打开日期选取器。
   * 使用箭头查找年和月。
   * 在日历上单击月的某一天。
   * 单击确定以关闭日期选取器。

1. 在显示列表中，选择每页要显示的搜索结果数。
1. 单击“查找”。

   任何失败事件都会在列表中以拒绝图标突出显示。

1. 要查看事件的详细信息，请单击列表中事件的描述。

## 对事件列表进行排序 {#sort-the-event-list}

您可以按列标题对事件列表进行排序，以便更轻松地查找事件。 列标题旁边的三角形图标指示当前用于排序的列。 向上指向三角形表示升序，而向下指向三角形表示降序。

1. 单击相应的列标题。
1. 要更改排序顺序，请再次单击列标题。
