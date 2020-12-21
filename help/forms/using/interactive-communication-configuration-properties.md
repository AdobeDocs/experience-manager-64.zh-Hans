---
title: 交互通信配置属性
seo-title: 交互通信配置属性
description: 编辑交互通信的默认配置属性
seo-description: 编辑交互通信的默认配置属性
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 7%

---


# 交互通信配置属性{#interactive-communications-configuration-properties}

编辑交互通信的默认配置属性

交互通信包括在安装[AEM Forms加载项](/help/forms/using/installing-configuring-aem-forms-osgi.md)软件包后自动配置的属性。 交互通信作者可以使用&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;页编辑这些默认配置属性。

使用以下URL打开&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;页：

https://&lt;server>:&lt;port>/&lt;contextPath>/system/console/configMgr

配置属性包括：

* [文档片段配置](#document-fragments-configuration)
* [创建对应配置](#create-correspondence-configuration)
* [自适应表单与交互式通信Web渠道配置](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [自适应表单与交互通信Web渠道主题配置](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## 文档片段配置{#document-fragments-configuration}

点按&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;页上的&#x200B;**文档片段配置**&#x200B;以视图文档片段的配置属性。

<table> 
 <tbody> 
  <tr> 
   <td>属性</td> 
   <td>描述</td> 
   <td>默认</td> 
   <td>可接受值</td> 
  </tr> 
  <tr> 
   <td>数据显示格式</td> 
   <td>创建用于打印和Web渠道的交互式通信时，可用的字段、变量和表单数据模型元素的区域设置特定显示格式。</td> 
   <td> 
    <ul> 
     <li>locale = en_US、de_DE、fr_FR和ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>缩进</td> 
   <td>应用于列表文档片段中文本的单个缩进单位的宽度。</td> 
   <td>12.7毫米</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>罗马数字最小宽度</td> 
   <td>在列表文档片段中使用罗马数字时，应用于项目符号或数字字段的最小宽度。 </td> 
   <td>12.7毫米</td> 
   <td>数字</td> 
  </tr> 
  <tr> 
   <td>最小宽度数</td> 
   <td>在列表文档片段中使用编号列表（除罗马数字之外）时，要应用于项目符号或编号字段的最小宽度。</td> 
   <td>8毫米</td> 
   <td>数字</td> 
  </tr> 
 </tbody> 
</table>

## 创建对应配置{#create-correspondence-configuration}

点按&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;页上的&#x200B;**创建对应配置**&#x200B;以视图代理UI的配置属性。

| 属性 | 描述 | 默认 | 可接受值 |
|---|---|---|---|
| 显示要编辑的已解析内容 | 选中此复选框可在代理UI上编辑文本模块时显示已解析的内容（实际值而非占位符）。 | 未选择 | 不适用 |
| 在预览期间应用水印 | 选中此复选框可将水印应用于“在预览模式下打印交互通信的渠道”。 | 未选择 | 不适用 |

## 自适应表单和交互式通信Web渠道配置{#adaptive-form-and-interactive-communication-web-channel-configuration}

点按&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;页上的&#x200B;**自适应表单和交互式通信Web渠道配置**，以视图自适应Forms和交互式通信Web渠道的配置属性。 下表描述了与交互通信相关的属性：

| 属性 | 描述 | 默认 | 可接受值 |
|---|---|---|---|
| 显示占位符 | 选中此复选框可显示自适应表单和交互式通信中包含的字段的占位符。 | 已选定 | 不适用 |
| 最大缓存条目数 | 设置可使用缓存检索的最大自适应表单和交互式通信数。 | 100 | 数字 |
| 使文件名唯一 | 选中此复选框可为自适应Forms和交互式通信中作为附件包含的文件提供唯一名称。 | 未选择 | 不适用 |

## 自适应表单和交互式通信Web渠道主题配置{#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

点按&#x200B;**Adobe Experience ManagerWeb控制台配置**&#x200B;页上的&#x200B;**自适应表单和交互式通信Web渠道主题配置**，以视图自适应Forms和交互式通信Web渠道主题的配置属性。

<table> 
 <tbody> 
  <tr> 
   <td>属性</td> 
   <td>描述</td> 
   <td>默认</td> 
   <td>可接受值</td> 
  </tr> 
  <tr> 
   <td>字体列表名</td> 
   <td>列表在创建自适应Forms和交互通信时可用的字体。</td> 
   <td><p>格鲁吉亚</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Black</p> <p>影响</p> <p>Palatino Linotype</p> </td> 
   <td>所有有效的Adobe服务器字体</td> 
  </tr> 
 </tbody> 
</table>

