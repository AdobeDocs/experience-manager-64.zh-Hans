---
title: 存储配置
seo-title: Storage Configuration
description: 如何访问存储配置控制台
seo-description: How to access the Storage Configuration Console
uuid: 6a5a71d5-6aaa-4635-8852-4dae33c497a9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 71fac7e9-814a-48b5-b816-9bdcb2a05190
role: Admin
exl-id: 905b6dc5-cf17-4f58-a687-27e2910a0729
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 3%

---

# 存储配置 {#storage-configuration}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

存储配置是标识为社区内容选择的存储的一种方法，也称为用户生成内容(UGC)。

此设置会通知AEM Communities代码在访问UGC时将使用存储资源提供程序(SRP)的实现，并且必须反映部署AEM时建立的拓扑。

有关存储选项和部署拓扑的讨论，请访问

* [社区内容存储](working-with-srp.md)
* [推荐的拓扑](topologies.md)

## 存储配置控制台 {#storage-configuration-console}

![chlimage_1-188](assets/chlimage_1-188.png)

在创作环境中，要访问存储配置控制台

* 从全局导航： **[!UICONTROL 工具>社区>存储配置]**

要选择默认JCR以外的存储选项，请执行以下操作：

* 选择选项
* 正确配置

   * 请参阅详细信息 [选择MSRP](msrp.md#select-msrp)
   * 请参阅详细信息 [选择DSRP](dsrp.md#select-dsrp)
   * 请参阅详细信息 [选择ASRP](asrp.md#select-asrp)

* 选择 **[!UICONTROL 提交]**

### 关于JCR存储 {#about-jcr-storage}

请注意，如果未进行任何选择，则默认为AEM存储库JCR。

JCR为 *not* 由创作和发布环境共享的公共存储。 社区内容将仅在创建社区内容的创作或发布环境中可见。

访问 [JCR商店](jsrp.md) 以了解其他信息。

>[!NOTE]
>
>节点的缺失 `srpc`在 `/etc/socialconfig` 表示默认 [JCR商店](jsrp.md).
