---
title: 与Adobe Sign集成 |处理用户数据
seo-title: 与Adobe Sign集成 |处理用户数据
description: 'null'
seo-description: 'null'
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# 与Adobe Sign集成 |处理用户数据 {#integration-with-adobe-sign-handling-user-data}

AEM Forms公司与Adobe Sign公司整合，使电子签名工作流能以自适应形式处理法律，销售，工资，人力资源管理工作流的表单或协议。 它允许单个和多用户签名、顺序和同时签名工作流、以匿名或登录用户身份对表单进行签名，以及通过多种方式验证用户身份。

当签署方或多个签署方签署并提交自适应表单时，将生成包含有关签署方信息的Adobe Sign协议。

有关AEM Forms与Adobe Sign集成的更多信息，请参 [阅以自适应形式使用Adobe Sign](/help/forms/using/working-with-adobe-sign.md)。

## 用户数据和数据存储 {#data}

Adobe Sign启用的自适应表单包括关于签署者的信息，并且可以包括由自适应表单收集的其他用户数据。 Adobe Sign服务在协议中保存签名的用户数据。 协议将保存在AEM Forms云服务中配置的Adobe Sign服务器上。 此外，如果自适应表单配置为使用Forms门户提交操作，则协议数据将与表单数据一起保存在表单门户数据存储中。

## 访问和删除用户数据 {#access-and-delete-user-data}

用户数据在协议中收集，但不保存在任何服务表中。 Adobe Sign使管理员能够自行选择管理他们在服务中控制的数据。 Adobe Sign服务的隐私管理员可以根据申请人的电子邮件地址列表或删除协议。

Adobe Sign优惠一个web应用程序，允许参与者搜索协议，如果需要，还可以删除协议。 有关详细信息，请参阅 [Adobe Sign-功能： 删除用户信息](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html)。

配置为使用Forms门户提交操作的自适应表单的协议数据也保存在表单门户数据存储中。 要访问和删除表单门户数据存储中的数据，请参阅 [Forms门户 |处理用户数据](/help/forms/using/forms-portal-handling-user-data.md)。
