---
title: 配置远程处理端点
seo-title: Configuring Remoting endpoints
description: 了解如何配置远程端点。
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# 配置远程处理端点 {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

远程处理端点允许使用Flex构建的应用程序使用(AEM forms已弃用)AEM forms远程处理来调用服务。 将自动为每个已激活的服务创建远程处理端点。 创建与端点同名的Flex目标，Flex客户端可以创建指向此目标的远程对象以调用相关服务上的操作。

## 远程处理端点设置 {#remoting-endpoint-settings}

**Flex客户端身份验证方法：** 确定在启用了安全性、调用的操作不支持匿名调用且客户端传递了无或无效凭据时，服务器向客户端发送的响应类型。
