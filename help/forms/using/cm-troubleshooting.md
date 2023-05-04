---
title: “通信管理：故障排除”
seo-title: Correspondence Management Troubleshooting
description: 通信管理疑难解答
seo-description: Correspondence Management Troubleshooting
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: Correspondence Management
exl-id: 82a35d81-13d0-435f-875e-6fd0a6d574d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 7%

---

# 通信管理：疑难解答 {#correspondence-management-troubleshooting}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 保存信件时出错 {#errors-when-saving-a-letter}

### 问题 {#issue}

保存信件时显示以下错误之一：

* 文本模块不存在数据绑定
* 请提供以下内容所需的属性信息

### 原因 {#reason}

由于以下原因之一，可能会发生这些错误：

* 数据字典绑定到信件，但服务器上不存在。
* 数据字典绑定到该字母，但名称中带有下划线(_)。

### 解决方法 {#workaround}

确保您在信件中使用的数据字典在服务器上存在，且其名称中不带下划线(_)。

## 预览信件时出错 {#error-when-previewing-a-letter}

### 问题 {#issue-1}

预览信件时，出现错误“加载信件时出错：无法从XML输入导入资产”，即使在信件中发布了之前未发布的文本资产时也是如此。

### 解决方法 {#workaround-1}

使用以下步骤重置发布实例上的信件缓存，然后重试查看信件：

1. 转到 **`https://[server]:[port]/[contextPath]/system/console/configMgr`** 并以管理员身份登录。
1. 选择 **通信管理配置**.
1. 在 **通信管理配置**，禁用 **启用信件缓存**&#x200B;然后单击&#x200B;**保存。**
1. 启用 **启用信件缓存** 然后单击 **保存**.
1. 重试查看信件。
