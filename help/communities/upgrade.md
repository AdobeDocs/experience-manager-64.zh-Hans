---
title: 升级到AEM 6.4 Communities
seo-title: Upgrading to AEM 6.4 Communities
description: 如何从早期版本升级到AEM 6.4 Communities
seo-description: How to upgrade from an earlier version to AEM 6.4 Communities
uuid: c6c2846e-38d4-4e99-9038-bfb486afd8b9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 7aa28e36-6b31-4447-b800-cab2dc78c93c
exl-id: ef622ac3-d96d-48bf-bfb2-61516d9deb5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 1%

---

# 升级到AEM 6.4 Communities {#upgrading-to-aem-communities}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

根据每个站点的拓扑和功能，在升级到AEM Communities 6.4或安装最新功能包时，可能需要执行以下操作。

本节专门针对社区，并补充了 [升级到AEM 6.4](../../help/sites-deploying/upgrade.md) （平台）。

## 从AEM 6.1或更高版本升级 {#upgrading-from-aem-or-later}

### 重新索引Solr {#reindex-solr}

在配置了MSRP的部署上安装新的Communities功能包时，需要：

1. 安装 [最新功能包](deploy-communities.md#latestfeaturepack)
2. 安装 [最新Solr配置文件](msrp.md#upgrading)
3. 重新索引MSRP

   请参阅部分 [MSRP重新索引工具](msrp.md#msrp-reindex-tool)

### 启用2.0 {#enablement}

自AEM 6.3起，启用功能不再将报表信息存储在MySQL中。 MySQL依赖关系仅用于跟踪SCORM内容。

请联系 [客户关怀](https://helpx.adobe.com/cn/marketing-cloud/contact-support.html) 以获取有关从启用1.0迁移内容的帮助。

## 从AEM 6.0升级 {#upgrading-from-aem}

如果需要保留预先存在的UGC，则执行此操作的方法取决于部署是否存储了UGC [内部部署](#on-premise-storage) 或 [Adobe云](#adobe-cloud-storage).

### Adobe云存储 {#adobe-cloud-storage}

如果已升级的站点配置为使用Adobe云存储，则它可能会（错误地）显示，好像所有UGC都丢失了一样，因为SRP方法将无法在旧位置中找到预先存在的UGC。

因此，有能力指示ASRP使用 `AEM 6.0 compatability-mode` 访问UGC。

对于所有AEM 6.3创作和发布实例：

1. 使用管理员权限登录并配置 [ASRP](asrp.md).
1. 请按照以下步骤使现有UGC可见：

   i.浏览到Web控制台。 默认URL为
   `https://localhost:4502/system/console/configMgr`。

   ii. 定位 **[!UICONTROL AEM Communities实用程序]** 配置，然后选择以展开配置面板。

   三。 取消选中 **[!UICONTROL 云存储]** 单击 **[!UICONTROL 保存]**.

![chlimage_1-126](assets/chlimage_1-126.png)

### 内部部署存储 {#on-premise-storage}

如果已升级的站点不使用云存储，则必须转换任何预先存在的UGC，以符合AEM 6.1 Communities中引入的新结构，从而支持常用存储。

为此，在GitHub上提供了一个开源迁移工具：\
[AEM Communities UGC迁移工具](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration)

### Java API {#java-apis}

从AEM 6.0社交社区升级到AEM 6.3社区时，请注意，许多API已重新组织为不同的包。 在使用IDE自定义社区功能时，大多数问题都应该易于解决。

有关已弃用的SocialUtils包的详细信息，请访问 [SocialUtils重构](socialutils.md).

另请参阅 [将Maven用于社区](maven.md).

### 无JSP组件模板 {#no-jsp-component-templates}

的 [社交组件框架](scf.md) (SCF)使用 [HandlebarsJS](https://handlebarsjs.com/) (HBS)模板语言代替AEM 6.0之前使用的Java Server Pages(JSP)。

在AEM 6.0中，JSP组件与新的HBS框架组件一起保留在同一位置，HBS组件通常位于名为“hbs”的子文件夹中。

自AEM 6.1起，JSP组件已完全删除。 对于Communities，建议将JSP组件的所有使用替换为SCF组件。

## AEM Communities UGC迁移工具 {#aem-communities-ugc-migration-tool}

的 [AEM Communities UGC迁移工具](https://github.com/Adobe-Marketing-Cloud/communities-ugc-migration) 是一款开源迁移工具，在GitHub上提供，可通过自定义，将UGC从AEM社交社区的早期版本导出并导入AEM Communities 6.1或更高版本。

除了从早期版本移动UGC之外，还可以使用该工具将UGC从一个版本移动 [SRP](working-with-srp.md) 到另一个，如从管理系统更新项目到DSRP。

## 从AEM 5.6.1或更早版本升级 {#upgrading-from-aem-or-earlier}

从概念上讲，社区有三代组成部分：

**第1代**:大约CQ 5.4 - AEM 5.6.0 — 这些是 **collab** 将UGC存储在本地存储库中的组件使用复制作为跨平台同步UGC的手段。 其他差异包括使用Java Server Pages(JSP)实现，以及仅在创作环境中创作的博客功能。

**第2代**:从AEM 5.6.1到AEM 6.1 — 这是 **collab** 和 **社交** 组件。 AEM 6.0引入了 [社交组件框架](scf.md) (SCF)和AEM 6.2引入了 [通用UGC商店](working-with-srp.md) 其中，使用 [存储资源提供程序](srp.md) (SRP)。

**第3代**:从AEM 6.2转到 **社交** 组件，在SCF中作为Handlebars(HBS)组件实现，需要为UGC选择SRP。
