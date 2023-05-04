---
title: 交互式通信配置属性
seo-title: Interactive Communication configuration properties
description: 编辑交互式通信的默认配置属性
seo-description: Edit default configuration properties for Interactive Communications
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 8%

---

# 交互式通信配置属性 {#interactive-communications-configuration-properties}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

编辑交互式通信的默认配置属性

交互式通信包括在安装 [AEM Forms附加组件](/help/forms/using/installing-configuring-aem-forms-osgi.md) 包。 交互式通信作者可以使用 **Adobe Experience Manager Web控制台配置** 页面。

打开 **Adobe Experience Manager Web控制台配置** 页面：

https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr

配置属性包括：

* [文档片段配置](#document-fragments-configuration)
* [创建通信配置](#create-correspondence-configuration)
* [自适应表单与交互式通信Web信道配置](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [自适应表单与交互式通信Web渠道主题配置](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## 文档片段配置 {#document-fragments-configuration}

点按 **文档片段配置** 在 **Adobe Experience Manager Web控制台配置** 页面以查看文档片段的配置属性。

<table> 
 <tbody> 
  <tr> 
   <td>属性</td> 
   <td>描述</td> 
   <td>默认</td> 
   <td>可接受的值</td> 
  </tr> 
  <tr> 
   <td>数据显示格式</td> 
   <td>创建用于打印和Web渠道的交互式通信时，可用的字段、变量和表单数据模型元素的区域设置特定显示格式。</td> 
   <td> 
    <ul> 
     <li>locale = en_US、de_DE、fr_FR和ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = 。</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>缩进</td> 
   <td>应用于列表文档片段中文本的单个缩进单位的宽度。</td> 
   <td>12.7mm</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>罗马数字最小宽度</td> 
   <td>在列表文档片段中使用罗马数字时，应用于项目符号或数字字段的最小宽度。 </td> 
   <td>12.7mm</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>最小宽度数</td> 
   <td>在列表文档片段中使用编号列表和罗马数字之外的编号列表时，应用于项目符号或数字字段的最小宽度。</td> 
   <td>8.0mm</td> 
   <td>数字</td> 
  </tr> 
 </tbody> 
</table>

## 创建通信配置 {#create-correspondence-configuration}

点按 **创建通信配置** 在 **Adobe Experience Manager Web控制台配置** 页面查看代理UI的配置属性。

| 属性 | 描述 | 默认 | 可接受的值 |
|---|---|---|---|
| 显示要编辑的已解析内容 | 选中此复选框可在代理UI中编辑文本模块时显示已解析的内容（实际值而不是占位符）。 | 未选择 | 不适用 |
| 在预览期间应用水印 | 选中此复选框可在预览模式下将水印应用于交互式通信的打印渠道。 | 未选择 | 不适用 |

## 自适应表单与交互式通信Web信道配置 {#adaptive-form-and-interactive-communication-web-channel-configuration}

点按 **自适应表单与交互式通信Web信道配置** 在 **Adobe Experience Manager Web控制台配置** 页面查看自适应Forms和交互式通信Web渠道的配置属性。 下表描述了与交互式通信相关的属性：

| 属性 | 描述 | 默认 | 可接受的值 |
|---|---|---|---|
| 显示占位符 | 选中此复选框可为自适应表单和交互式通信中包含的字段启用占位符显示。 | 已选定 | 不适用 |
| 最大缓存条目数 | 设置可以使用缓存内存检索的自适应表单和交互式通信的最大数量。 | 100 | 数字 |
| 使文件名唯一 | 选中此复选框可在自适应Forms和交互式通信中以附件形式包含文件的唯一名称。 | 未选择 | 不适用 |

## 自适应表单与交互式通信Web渠道主题配置 {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

点按 **自适应表单与交互式通信Web渠道主题配置** 在 **Adobe Experience Manager Web控制台配置** 页面以查看自适应Forms和交互式通信Web渠道主题的配置属性。

<table> 
 <tbody> 
  <tr> 
   <td>属性</td> 
   <td>描述</td> 
   <td>默认</td> 
   <td>可接受的值</td> 
  </tr> 
  <tr> 
   <td>字体列表名称</td> 
   <td>可在创建自适应Forms和交互式通信时使用的字体列表。</td> 
   <td><p>格鲁吉亚</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>影响</p> <p>Palatino Linotype</p> </td> 
   <td>所有有效的Adobe服务器字体</td> 
  </tr> 
 </tbody> 
</table>
