---
title: 元数据架构参考
description: 了解描述资产元数据的标准惯例，包括都柏林核心、IPTC和其他元数据架构。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 883bebc6-8bbc-43b1-91e5-9e2bf2470b6e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 3%

---

# 元数据架构参考 {#metadata-schemata-reference}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

以下参考包括有关特定元数据架构（按字母顺序）的信息，以及属性列表及其定义。

## 都柏林核心 {#dublin-core}

都柏林核心元数据提供了一组用于描述资产的标准化惯例，以便更便于查找。 在 [!DNL Experience Manager] 都柏林核心资源介绍的数字资产，包括视频、声音、图像和文档。

都柏林核心元数据元素集(DCMES)很简单，共包含15个元数据元素，如下表所示。 每个都柏林核心元素都是可选元素，并且可以重复。 您可以像添加或删除特定于媒体类型的元数据一样，添加或删除都柏林核心元数据信息。

除了DCMES之外，都柏林核心计划还创建了其他元数据元素。 请参阅 [都柏林核心计划](https://dublincore.org/) 以了解更多信息。

| 属性 | 描述 |
|---|---|
| 参与者 | 负责对内容做出贡献的人或公司。 |
| 覆盖 | 资产涵盖的地理位置或时间段。 |
| creator | 负责创建内容的人员或公司。 |
| 日期 | 与资产关联的日期或时间段。 |
| 说明 | 有关资产的更多信息。 |
| 格式 | 资产的文件格式、物理介质或尺寸。 [!DNL Experience Manager] 使用dc:format表示资产的mime类型。 |
| 标识符 | 对资产的唯一引用。 |
| 语言 | 资产的语言（例如，en表示英语）。 |
| 发布者 | 负责使资产可用的人员或公司。 |
| 关系 | 相关资产。 |
| 权利 | 有关谁有权访问此资产的信息。 |
| source | 从中获取资产的相关资产。 |
| 主题 | 资产的主题。 |
| 标题 | 资产的名称。 |
| 类型 | 资产的性质或类型。 |

## IPTC {#iptc}

国际新闻电信理事会(IPTC)是全球新闻机构的联盟，其目标之一是制定和维护技术标准。 IPTC为图像定义了一套照片元数据标准，几乎在摄影师中得到普遍接受。 这些元数据标准是20世纪90年代创建的IPTC信息交换模型(IIM)这一更广泛标准的一部分。

尽管IPTC标头信息基本上已被XMP取代，但IPTC核心架构和扩展架构适用于XMP。 在图像程序中，XMP和IPTC属性都会同步。
