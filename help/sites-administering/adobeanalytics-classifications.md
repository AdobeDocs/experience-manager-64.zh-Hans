---
title: Adobe 分类
seo-title: Adobe Classifications
description: 了解Adobe分类。
seo-description: Learn about Adobe Classifications.
uuid: 57fb59f4-da90-4fe7-a5b1-c3bd51159a16
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6787511a-2ce0-421a-bcfb-90d5f32ad35e
exl-id: 25e58c68-5c67-4894-9a54-1717d90d7831
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 7%

---

# Adobe 分类{#adobe-classifications}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe分类将分类数据导出到 [Adobe Analytics](/help/sites-administering/adobeanalytics.md) 按计划进行。 导出程序是 **com.adobe.cq.scheduled.exporter.Exporter**.

要配置此项，请执行以下操作：

1. 导航方式 **工具， Cloudservices** 到 **Adobe Analytics** 中。
1. 添加新配置。 您将看到 **Adobe Analytics分类** 配置模板显示在 **Adobe Analytics框架** 配置。 提供 **标题** 和 **名称** 根据需要：

   ![aa-25](assets/aa-25.png)

1. 单击 **创建** 以配置设置。

   ![chlimage_1](assets/chlimage_1.png)

   属性包括：

   | **字段** | **描述** |
   |---|---|
   | 启用 | 选择 **是** ，以启用“Adobe分类”设置。 |
   | 发生冲突时覆盖 | 选择 **是** 覆盖任何数据冲突。 默认情况下，此参数设置为 **否**. |
   | 删除已处理的项目 | 如果设置为 **是**，删除已处理的节点。 默认值为 **False**. |
   | 导出作业描述 | 输入Adobe分类作业的说明。 |
   | 通知电子邮件 | 输入Adobe分类通知的电子邮件地址。 |
   | 报表包 | 输入要为其运行导入作业的报表包。 |
   | 数据集 | 输入要为其运行导入作业的数据集关系ID。 |
   | 转换程序 | 从下拉菜单中，选择变压器实施。 |
   | 数据源 | 导航到数据容器的路径。 |
   | 导出时间表 | 选择导出的计划。 默认每30分钟一次。 |

1. 单击 **确定** 来保存设置。

## 修改页面大小 {#modifying-page-size}

记录在页面中进行处理。 默认情况下，Adobe分类会创建页面大小为1000的页面。

根据Adobe分类中的每个定义，页面最大大小可为25000，并且可以从Felix控制台中修改。 在导出过程中，“Adobe分类”会锁定源节点以防止并发修改。 导出后、出错时或会话关闭时，将解锁节点。

要更改页面大小，请执行以下操作：

1. 导航到OSGI控制台(位于 **https://&lt;host>:&lt;port>/system/console/configMgr** 选择 **AdobeAEM分类导出器**.

   ![aa-26](assets/aa-26.png)

1. 更新 **导出页面大小** 根据需要，单击 **保存**.

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe分类以前称为SAINT导出器。

导出程序可以使用转换器将导出数据转换为特定格式。 对于Adobe分类，为子界面 `SAINTTransformer<String[]>` 提供了实现变压器接口。 此界面用于将数据类型限制为 `String[]` SAINTAPI使用的标记接口，用于查找此类服务以供选择。

在默认实施SAINTDefaultTransformer中，导出源的子资源将被视为属性名称作为键的记录，属性值作为值。 的 **键** 列将自动添加为第一列 — 其值将为节点名称。 忽略名称进度属性（包含：）。

*节点结构：*

* id-classification `nt:unstructured`

   * 1 `nt:unstructured`

      * Product = My Product Name(String)
      * 价格= 120.90（字符串）
      * 大小= M（字符串）
      * 颜色=黑色（字符串）
      * Color^Code = 101（字符串）

**SAINT标题和记录：**

| **键** | **产品** | **价格** | **大小** | **颜色** | **颜色^代码** |
|---|---|---|---|---|---|
| 1 | 我的产品名称 | 120.90 | M | black | 101 |

属性包括：

<table> 
 <tbody> 
  <tr> 
   <td><strong>属性路径</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>变压器</td> 
   <td>SAINTransferm实施的类名称</td> 
  </tr> 
  <tr> 
   <td>电子邮件</td> 
   <td>通知电子邮件地址。</td> 
  </tr> 
  <tr> 
   <td>reportsuites</td> 
   <td>报表包ID，用于为其运行导入作业。 </td> 
  </tr> 
  <tr> 
   <td>数据集</td> 
   <td>要为其运行导入作业的数据集关系ID。 </td> 
  </tr> 
  <tr> 
   <td>说明</td> 
   <td>作业描述。 <br /> </td> 
  </tr> 
  <tr> 
   <td>覆盖</td> 
   <td>覆盖数据冲突的标记。 默认为 <strong>false</strong>.</td> 
  </tr> 
  <tr> 
   <td>检查分支</td> 
   <td>用于检查报表包是否兼容的标记。 默认为 <strong>true</strong>.</td> 
  </tr> 
  <tr> 
   <td>deleteprocessed</td> 
   <td>导出后删除已处理节点的标记。 默认为 <strong>false</strong>.</td> 
  </tr> 
 </tbody> 
</table>

## 自动Adobe分类导出 {#automating-adobe-classifications-export}

您可以创建自己的工作流，以便任何新导入都会启动工作流，以在中创建适当且结构正确的数据 **/var/export/** 以便可将其导出到Adobe分类。
