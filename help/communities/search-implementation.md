---
title: 搜索要点
seo-title: Search Essentials
description: 在社区中搜索
seo-description: Search in Communities
uuid: 5f35a033-2069-499e-9cdb-db25781312f0
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 300aa9f3-596f-42bc-8d46-e535f2bc4379
exl-id: 9092df98-f600-4ed8-93d8-f2e83cd8bb6a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 5%

---

# 搜索要点 {#search-essentials}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

搜索功能是AEM Communities的一项基本功能。 除 [AEM platform search](../../help/sites-deploying/queries-and-indexing.md) 功能，AEM Communities提供 [UGC搜索API](#ugc-search-api) 用于搜索用户生成的内容(UGC)。 UGC具有唯一的属性，因为它是与其他AEM内容和用户数据分开输入和存储的。

对于Communities，通常搜索的两项内容有：

* 社区成员发布的内容

   * 使用AEM Communities的UGC搜索API

* 用户和用户组（用户数据）

   * 使用AEM平台搜索功能

文档的此部分内容对于正在创建可创建或管理UGC的自定义组件的开发人员非常感兴趣。

## 安全和阴影节点 {#security-and-shadow-nodes}

对于自定义组件，必须使用 [SocialResourceUtilities](socialutils.md#socialresourceutilities-package) 方法。 创建和搜索UGC的实用程序方法将建立所需的 [阴影节点](srp.md#about-shadow-nodes-in-jcr) 并确保成员对请求拥有正确的权限。

未通过SRP实用程序管理的是与审核相关的属性。

请参阅 [SRP和UGC要点](srp-and-ugc.md) 有关用于访问UGC和ACL卷影节点的实用工具方法的信息。

## UGC搜索API {#ugc-search-api}

的 [UGC公用商店](working-with-srp.md) 由多种存储资源提供程序(SRP)之一提供，每个存储资源提供程序可能具有不同的本机查询语言。 因此，无论选择何种SRP，自定义代码都应使用 [UGC API包](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary.html) (*com.adobe.cq.social.ugc.api*)，将调用适合所选SRP的查询语言。

### ASRP搜索 {#asrp-searches}

对于 [ASRP](asrp.md)，则UGC会存储在Adobe云中。 虽然UGC在CRX中不可见， [审核](moderate-ugc.md) 可在创作和发布环境中使用。 使用 [UGC搜索API](#ugc-search-api) 对于ASRP的工作方式与其他SRP的工作方式相同。

当前不存在用于管理ASRP搜索的工具。

创建可搜索的自定义属性时，必须遵循 [命名要求](#naming-of-custom-properties).

### MSRP搜索 {#msrp-searches}

对于 [MSRP](msrp.md), UGC存储在MongoDB中，配置为使用Solr进行搜索。 UGC将不显示在CRX中，但 [审核](moderate-ugc.md) 可在创作和发布环境中使用。

关于MSRP和Solr:

* AEM平台的嵌入式解决程序不用于MSRP
* 如果为AEM平台使用远程解决程序，则可以与MSRP共享该解决方案，但它们应使用不同的集合
* Solr可配置为标准搜索或多语言搜索(MLS)
* 有关配置详细信息，请参阅 [Solr配置](msrp.md#solr-configuration) （针对MSRP）

自定义搜索功能应使用 [UGC搜索API](#ugc-search-api).

创建可搜索的自定义属性时，必须遵循 [命名要求](#naming-of-custom-properties).

### JSRP搜索 {#jsrp-searches}

对于 [JSRP](jsrp.md)，则UGC存储在 [Oak](../../help/sites-deploying/platform.md) 和仅在输入了它的AEM创作或发布实例的存储库中可见。

由于UGC通常在发布环境中输入，因此对于多发布者生产系统，需要配置 [发布群集](topologies.md)，而不是发布场，以便所有发布者都可以看到输入的内容。

对于JSRP，在发布环境中输入的UGC在创作环境中将不可见。 所以 [审核](moderate-ugc.md) 任务在发布环境中执行。

自定义搜索功能应使用 [UGC搜索API](#ugc-search-api).

#### Oak索引 {#oak-indexing}

虽然不会为AEM平台搜索自动创建Oak索引，但从AEM 6.2开始，已为AEM Communities添加了索引，以提高性能，并在显示UGC搜索结果时支持分页。

如果自定义属性正在使用且搜索速度缓慢，则需要为自定义属性创建其他索引，以提高其性能。 要保持便携性，请 [命名要求](#naming-of-custom-properties) 创建可搜索的自定义属性时。

要修改现有索引或创建自定义索引，请参阅 [Oak查询和索引](../../help/sites-deploying/queries-and-indexing.md).

的 [Oak索引管理器](https://adobe-consulting-services.github.io/acs-aem-commons/features/oak-index-manager.html) 可从ACS AEM Commons获取。 它提供：

* 现有索引的视图
* 启动重新索引的功能

查看 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)，位置为：

* `/oak:index/socialLucene`

![chlimage_1-235](assets/chlimage_1-235.png)

## 索引搜索属性 {#indexed-search-properties}

### 默认搜索属性 {#default-search-properties}

以下是用于各种社区功能的一些可搜索属性：

| **属性** | **数据类型** |
|---|---|
| isPratked | *布尔型* |
| isSpam | *布尔型* |
| 读取 | *布尔型* |
| 影响 | *布尔型* |
| 附件 | *布尔型* |
| 情绪 | *长整型* |
| 已标记 | *布尔型* |
| 已添加 | *日期* |
| modifiedDate | *日期* |
| 状态 | *字符串* |
| userIdentifier | *字符串* |
| 回复 | *长整型* |
| jcr:title | *字符串* |
| jcr:description | *字符串* |
| sling:resourceType | *字符串* |
| allowThreadedReply | *布尔型* |
| isDraft | *布尔型* |
| publishDate | *日期* |
| publishJobId | *字符串* |
| 已回复 | *布尔型* |
| 已应答的 | *布尔型* |
| 标记 | *字符串* |
| cq:Tag | *字符串* |
| author_display_name | *字符串* |
| location_t | *字符串* |
| parentPath | *字符串* |
| parentTitle | *字符串* |

### 自定义属性的命名 {#naming-of-custom-properties}

添加自定义属性时，为了对通过 [UGC搜索API](#ugc-search-api)，则*需要*才能在属性名称中添加后缀。

后缀适用于使用架构的查询语言：

* 它会将资产标识为可搜索
* 它标识数据类型

Solr是使用模式的查询语言的一个示例。

| **后缀** | **数据类型** |
|---|---|
| _b | *布尔型* |
| _dt | *日程表* |
| _d | *双精度型* |
| _tl | *长整型* |
| _s | *字符串* |
| _t | *文本* |

**注释:**

* *文本* 是一个以符号表示的字符串， *字符串* 不是。 使用 *文本* 模糊（更像这样）搜索。

* 对于多值类型，请在后缀中添加“s”，例如：

   * `viewDate_dt`:单日期属性
   * `viewDates_dts`:日期属性列表

## 过滤器 {#filters}

包含 [评论系统](essentials-comments.md) 支持在其端点中添加filter参数。

AND和OR逻辑的过滤器语法如下所示（在对URL进行编码之前显示）：

* 要指定OR，请使用一个带逗号分隔值的过滤器参数：

   * `filter=name eq 'Jennifer',name eq 'Jen'`

* 要指定AND，请使用多个筛选器参数：

   * `filter = name eq 'Jackson'&filter=message eq 'testing'`

的默认实施 [搜索组件](search.md) 使用此语法，如在 [社区组件指南](components-guide.md). 要进行实验，请浏览 [http://localhost:4503/content/community-components/en/search.html](http://localhost:4503/content/community-components/en/search.html).

过滤器运算符包括：

| EQ | 等于 |
|---|---|
| NE | 不等于 |
| LT | 小于 |
| LTE | 小于或等于 |
| GE | 大于 |
| GET | 大于或等于 |
| LIKE | 模糊匹配 |

URL应务必引用社区组件（资源），而不是放置组件的页面：

* 正确：论坛组件
   * `/content/community-components/en/forum/jcr:content/content/forum.social.json`
* 错误：论坛页面
   * `/content/community-components/en/forum.social.json`

## SRP工具 {#srp-tools}

有一个Adobe Marketing Cloud GitHub项目，其中包含：

[AEM Communities SRP工具](https://github.com/Adobe-Marketing-Cloud/aem-communities-srp-tools)

此存储库包含用于管理SRP中数据的工具。

当前，有一个Servlet提供从任何SRP中删除所有UGC的功能。

例如，要删除ASRP中的所有UGC，请执行以下操作：

```shell
curl -X POST http://localhost:4502/services/social/srp/cleanup?path=/content/usergenerated/asi/cloud -uadmin:admin
```

## 疑难解答 {#troubleshooting}

### 索尔查询 {#solr-query}

要帮助解决Solr查询问题，请为

`com.adobe.cq.social.srp.impl.SocialSolrConnector`。

实际的Solr查询将显示在调试日志中的URL编码：

要解决的查询是： `sort=timestamp+desc&bl=en&pl=en&start=0&rows=10 &q=%2Btitle_t:(hello)+%2Bprovider_id:\/content/usergenerated/asi/mongo/content/+%2Bresource_type_s:&df=provider_id&trf=verbatim&fq={!cost%3D100}report_suite:mongo`

的值 `q` 参数是查询。 解码URL编码后，查询可以传递到Solr Admin Query工具，以便进一步调试。

## 相关资源 {#related-resources}

* [社区内容存储](working-with-srp.md)  — 讨论UGC公用存储的可用SRP选项
* [存储资源提供程序概述](srp.md)  — 简介和存储库使用概述
* [使用SRP访问UGC](accessing-ugc-with-srp.md)  — 编码准则
* [SocialUtils重构](socialutils.md)  — 用于替换SocialUtils的SRP的实用程序方法
* [搜索和搜索结果组件](search.md)  — 向模板添加UGC搜索功能
