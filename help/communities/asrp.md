---
title: ASRP -Adobe存储资源提供程序
seo-title: ASRP - Adobe Storage Resource Provider
description: 设置AEM Communities以使用关系数据库作为其公共存储
seo-description: Set up AEM Communities to use a relational database as its common store
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
role: Admin
exl-id: 136c0913-c8b8-451d-bb28-3c3285c172a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 2%

---

# ASRP -Adobe存储资源提供程序 {#asrp-adobe-storage-resource-provider}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 关于ASRP {#about-asrp}

当AEM Communities配置为使用ASRP作为其公共存储时，可以从所有创作和发布实例访问用户生成的内容(UGC)，而无需同步或复制。

另请参阅 [SRP选项的特点](working-with-srp.md#characteristics-of-srp-options) 和 [推荐的拓扑](topologies.md).

## 要求 {#requirements}

使用ASRP需要额外的许可证。

要将AEM Communities网站配置为使用ASRP for UGC，请联系您的客户代表，以获取：

* 数据中心URL（ASRP端点的地址）
* 使用者密钥
* 密钥
* 报表包ID

消费者密钥和密钥将在公司的所有报表包中共享。 每个租户有一个报表包。

## 配置 {#configuration}

### 选择ASRP {#select-asrp}

的 [存储配置控制台](srp-config.md) 允许选择默认存储配置，该配置标识要使用的SRP实施。

**在作者时**:

* 从全局导航： **[!UICONTROL 工具>社区>存储配置]**

![chlimage_1-310](assets/chlimage_1-310.png)

* 选择 **[!UICONTROL Adobe存储资源提供程序(ASRP)]**
* 以下信息来自配置过程

   * **[!UICONTROL 数据中心 URL]**

      下拉列表，选择由您的客户代表标识的生产数据中心

   * **[!UICONTROL 默认报表包]**

      输入默认报表包的名称

   * **[!UICONTROL 使用者密钥]**

      输入用户键

   * **[!UICONTROL 密钥]**

      输入密钥

* 选择 **[!UICONTROL 提交]**

准备发布实例：

* [复制加密密钥](#replicate-the-crypto-key)
* [复制配置](#publishing-the-configuration)

提交配置后，测试连接：

* 选择 **[!UICONTROL 测试配置]**
对于每个创作和发布实例，请从“存储配置”控制台测试与数据中心的连接

* 最后，确保用户档案数据的网站URL可通过 [外部链接](#externalize-links).

### 复制加密密钥 {#replicate-the-crypto-key}

消费者密钥和密钥已加密。 为了正确加密/解密密钥，所有AEM实例上的主Granite Crypto密钥必须相同。

按照 [复制加密密钥](deploy-communities.md#replicate-the-crypto-key).

### 将链接外部化 {#externalize-links}

要获取正确的配置文件和配置文件图像链接，请务必正确 [配置链接外部器](../../help/sites-developing/externalizer.md).

请确保将域设置为可从数据中心URL（ASRP端点）路由的URL。

### 时间同步 {#time-synchronization}

要成功使用ASRP端点进行身份验证，运行托管AEM Communities的计算机必须进行时间同步，例如与 [网络时间协议(NTP)](https://www.ntp.org/).

### 发布配置 {#publishing-the-configuration}

ASRP必须被标识为所有创作实例和发布实例上的公共存储。

要使相同的配置在发布环境中可用，请执行以下操作：

* **在作者时**:

   * 从主菜单导航到 **[!UICONTROL 工具>操作>复制]**
   * 选择 **[!UICONTROL 激活树]**
   * **[!UICONTROL 开始路径]**:

      * 浏览到 `/etc/socialconfig/srpc/`
   * 取消选中 **[!UICONTROL 仅已修改]**
   * 选择 **[!UICONTROL 激活]**


## 从AEM 6.0升级 {#upgrading-from-aem}

>[!CAUTION]
>
>如果在已发布的社区网站上启用ASRP，则任何已存储在 [JCR](jsrp.md) 将不再可见，因为内部部署存储和云存储之间没有数据同步。

**`AEM Communities Extension`** 之前在AEM 6.0 social communities as a cloud service中引入。 自AEM 6.1 Communities起，无需云配置，只需从 [存储配置控制台](srp-config.md).

由于新的存储结构，因此必须遵循 [升级](upgrade.md#adobe-cloud-storage) 从社交社区升级到社区时的说明。

## 管理用户数据 {#managing-user-data}

有关 *用户*, *用户配置文件* 和 *用户组*，通常在发布环境中输入，访问

* [用户同步](sync.md)
* [管理用户和用户组](users.md)

## 疑难解答 {#troubleshooting}

### 升级后UGC消失 {#ugc-disappears-after-upgrade}

如果从现有AEM 6.0社交社区网站进行升级，请务必遵循 [升级说明](upgrade.md#adobe-cloud-storage)，否则UGC将 *显示* 失去了。

### 身份验证错误 {#authentication-errors}

如果收到针对数据中心URL的身份验证错误，且AEM error.log包含有关过时时间戳的消息，则请验证是否正在进行时间同步。

建议使用诸如 [网络时间协议(NTP)](https://www.ntp.org/) 来同步所有AEM创作和发布服务器。

### 搜索中不显示新内容 {#new-content-does-not-appear-in-searches}

Adobe云存储基础架构使用 *最终一致性* 帮助实现其扩展和性能目标。 因此，新内容不会立即可用，并且可能需要几秒钟才能在搜索结果中显示。

虽然会监控影响最终一致性的间隔，但如果搜索中需要超过几秒钟的时间才能显示新内容，请联系您的客户代表。

### UGC在ASRP中不可见 {#ugc-not-visible-in-asrp}

通过检查存储选项的配置，确保ASRP已配置为默认提供程序。 默认情况下，存储资源提供程序是JSRP，而不是ASRP。

在所有创作和发布AEM实例上，重新访问存储配置控制台或检查AEM存储库：

* 在JCR中，如果 [/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * 不包含 [srpc](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) 节点，表示存储提供程序是JSRP
   * 如果srpc节点存在并包含节点 [defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)，默认配置的属性应将ASRP定义为默认提供程序
