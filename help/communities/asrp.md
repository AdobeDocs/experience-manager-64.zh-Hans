---
title: ASRP -Adobe存储资源提供程序
seo-title: ASRP -Adobe存储资源提供程序
description: 设置AEM Communities以将关系数据库用作其常用存储
seo-description: 设置AEM Communities以将关系数据库用作其常用存储
uuid: 29826b44-633d-4586-8553-cd87ebe269a2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 86349e4d-29ff-4baa-9fcd-c0ab1f0753e9
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 2%

---


# ASRP -Adobe存储资源提供程序 {#asrp-adobe-storage-resource-provider}

## 关于ASRP {#about-asrp}

将AEM Communities配置为使用ASRP作为其公用存储时，用户生成的内容(UGC)可从所有作者和发布实例访问，而无需同步或复制。

另请参 [阅SRP选项的特性](working-with-srp.md#characteristics-of-srp-options) 和建 [议的拓扑](topologies.md)。

## 要求 {#requirements}

使用ASRP需要额外的许可证。

要将您的AEM Communities站点配置为使用UGC的ASRP，请联系您的客户代表，了解：

* 数据中心URL（ASRP端点的地址）
* 使用者密钥
* 密钥
* 报表包ID

消费者密钥和密钥在所有报表包中共享，用于公司。 每个租户有一个报表包。

## 配置 {#configuration}

### 选择ASRP {#select-asrp}

存储 [配置控制台](srp-config.md) ，允许选择默认存储配置，该配置标识要使用的SRP实现。

**作者**:

* 从全局导航： **[!UICONTROL “工具”>“社区”>“存储配置”]**

![chlimage_1-310](assets/chlimage_1-310.png)

* Select **[!UICONTROL Adobe Storage Resource Provider (ASRP)]**
* 以下信息来自供应过程

   * **[!UICONTROL 数据中心 URL]**

      下拉列表选择由您的客户代表标识的生产数据中心

   * **[!UICONTROL 默认报表包]**

      输入默认报表包的名称

   * **[!UICONTROL 使用者密钥]**

      输入消费方密钥

   * **[!UICONTROL 密钥]**

      输入密钥

* Select **[!UICONTROL Submit]**

准备发布实例：

* [复制加密密钥](#replicate-the-crypto-key)
* [复制配置](#publishing-the-configuration)

提交配置后，测试连接：

* 为每 **[!UICONTROL 个作]**&#x200B;者和发布实例选择测试配置，从存储配置控制台测试与数据中心的连接

* 最后，通过将链接外部化，确保用户档案数据的站点URL可从数据 [中心路由](#externalize-links)。

### 复制加密密钥 {#replicate-the-crypto-key}

消费方密钥和密钥已加密。 要正确加密／解密密钥，主Granite加密密钥必须在所有AEM实例上相同。

请按照复制加 [密密钥中的说明](deploy-communities.md#replicate-the-crypto-key)。

### 将链接外部化 {#externalize-links}

要获得正确的用户档案和用户档案图像链接，请确保正确 [配置链接外部器](../../help/sites-developing/externalizer.md)。

请确保将域设置为可从数据中心URL（ASRP端点）路由的URL。

### 时间同步 {#time-synchronization}

要成功与ASRP端点进行身份验证，运行托管AEM Communities的计算机必须同步时间，如 [网络时间协议(NTP)](https://www.ntp.org/)。

### 发布配置 {#publishing-the-configuration}

ASRP必须被标识为所有作者实例和发布实例上的公用存储。

要在发布环境中提供相同的配置，请执行以下操作：

* **作者**:

   * 从主菜单导航到工 **[!UICONTROL 具>操作>复制]**
   * 选择 **[!UICONTROL 激活树]**
   * **[!UICONTROL 开始路径]**:

      * 浏览到 `/etc/socialconfig/srpc/`
   * 取消选 **[!UICONTROL 中仅已修改]**
   * 选择激 **[!UICONTROL 活]**


## 从AEM 6.0升级 {#upgrading-from-aem}

>[!CAUTION]
>
>如果在已发布的社区站点上启用ASRP，则任何已存储在 [JCR](jsrp.md) 中的UGC将不再可见，因为内部部署存储和云存储之间没有数据同步。

**`AEM Communities Extension`** 此前在AEM 6.0社交社区中作为云服务引入。 自AEM 6.1 Communities起，无需云配置，只需从存储配置控制台中 [选择ASRP](srp-config.md)。

由于新的存储结构，在从社交社区升级到社区 [时](upgrade.md#adobe-cloud-storage) ，必须按照升级说明操作。

## 管理用户数据 {#managing-user-data}

有关用户 *、用*&#x200B;户用户档案 ***、用户*&#x200B;和用户组的信息，通常在发布环境中输入，请访问

* [用户同步](sync.md)
* [管理用户和用户组](users.md)

## 疑难解答 {#troubleshooting}

### 升级后UGC消失 {#ugc-disappears-after-upgrade}

如果从现有的AEM 6.0社交社区站点升级，请务必按照 [升级说明](upgrade.md#adobe-cloud-storage)，否则UGC *将显* 示丢失。

### 身份验证错误 {#authentication-errors}

如果收到针对数据中心URL的身份验证错误，而AEM error.log包含有关过时时间戳的消息，则验证是否正在进行时间同步。

建议使用诸如网络时间协议(NTP) [之类的工具](https://www.ntp.org/) ，对所有AEM作者和发布服务器进行时间同步。

### 搜索中不显示新内容 {#new-content-does-not-appear-in-searches}

Adobe云存储基础架构使 *用最终的一致* 性来帮助实现其扩展和性能目标。 因此，新内容不会立即可用，并且可能需要几秒钟时间才能在搜索结果中显示。

在监视影响最终一致性的时间间隔时，如果搜索中显示新内容需要超过几秒钟的时间，请与您的帐户代表联系。

### UGC在ASRP中不可见 {#ugc-not-visible-in-asrp}

通过检查存储选项的配置，确保ASRP已配置为默认提供程序。 默认情况下，存储资源提供程序为JSRP，而非ASRP。

在所有作者实例和发布AEM实例上，重新访问存储配置控制台或检查AEM存储库：

* 在JCR中， [if/etc/socialconfig](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/)

   * 不包含srpc [节点](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc) ，它表示存储提供程序是JSRP
   * 如果srpc节点存在并包含 [节点defaultconfiguration](http://localhost:4502/crx/de/index.jsp#/etc/socialconfig/srpc/defaultconfiguration)，则默认配置的属性应将ASRP定义为默认提供程序

