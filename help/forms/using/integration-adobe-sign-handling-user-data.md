---
title: 与Acrobat Sign集成 |处理用户数据
seo-title: Integration with Acrobat Sign | Handling user data
description: AEM Forms与Acrobat Sign集成，以支持自适应表单中的电子签名工作流，以处理法律、销售、工资单、人力资源管理工作流的表单或协议。 深入了解用户数据、数据存储以及访问和删除用户数据。
seo-description: AEM Forms integrates with Acrobat Sign to enable e-signature workflows in adaptive forms to process forms or agreements for legal, sales, payroll, human resource management workflows. Dig deeper on user data, data stores, and access and delete user data.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Acrobat Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---

# 与Acrobat Sign集成 |处理用户数据 {#integration-with-adobe-sign-handling-user-data}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM Forms与Acrobat Sign集成，以支持自适应表单中的电子签名工作流，以处理法律、销售、工资单、人力资源管理工作流的表单或协议。 它允许单次和多用户签名、顺序和同时的签名工作流、以匿名或已登录用户身份对表单进行签名，以及通过多种方法来验证用户。

当签名者或多个签名者签名并提交自适应表单时，将生成一份Acrobat Sign协议，其中包含有关签名者的信息。

有关AEM Forms与Acrobat Sign集成的更多信息，请参阅 [在自适应表单中使用Acrobat Sign](/help/forms/using/working-with-adobe-sign.md).

## 用户数据和数据存储 {#data}

Acrobat Sign启用的自适应表单包括有关签名者的信息，并且可以包括由自适应表单收集的其他用户数据。 Acrobat Sign服务在协议内保存具有签名的用户数据。 协议保存在AEM Forms云服务中配置的Acrobat Sign服务器上。 此外，如果自适应表单配置为使用Forms Portal提交操作，则协议数据会与表单数据一起保存在表单门户数据存储中。

## 访问和删除用户数据 {#access-and-delete-user-data}

用户数据在协议中收集，但未保存在任何服务表中。 Acrobat Sign允许管理员在管理其在服务中控制的数据方面做出自己的选择。 Acrobat Sign服务的隐私管理员可以根据请求者的电子邮件地址列出或删除协议。

Acrobat Sign提供了一个web应用程序，允许参与者搜索协议，并在必要时删除协议。 有关更多信息，请参阅 [Acrobat Sign — 功能：删除用户信息](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

配置为使用Forms Portal提交操作的自适应表单的协议数据也会保存在Forms Portal数据存储中。 要从表单门户数据存储中访问和删除数据，请参阅 [Forms门户 |处理用户数据](/help/forms/using/forms-portal-handling-user-data.md).
