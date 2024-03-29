---
title: 面向客户的用户界面Recommendations
seo-title: User Interface Recommendations for Customers
description: 与经典用户界面和触屏优化用户界面相关的推荐列表。
seo-description: A list of recommendations related to the classic and touch-optimized user interfaces.
uuid: c661fb10-4dbc-4f8b-93be-3e77af1ad095
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 42bf42cb-0c6c-4390-8170-2c540c4d3ed3
exl-id: 1e5172d9-47a3-4d73-b749-166e201f4eef
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 1%

---

# 面向客户的用户界面Recommendations{#user-interface-recommendations-for-customers}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager 6.4附带两个UI — 统一的Experience CloudUI和经典UI。

本文档旨在指导客户根据自己的情况选择要使用的UI。

利息条款：

* **UI（或标准UI）**
5.6.0中引入的现代用户界面是作为技术预览并在后续版本中扩展的。 它基于Adobe Experience Cloud的统一用户体验，以前称为触屏UI或触屏UI。

* **经典UI**
2008年CQ 5.1引入的基于ExtJS技术的用户界面。

* **站点管理**
用于管理站点层次结构（移动、激活、托管引用）和创建新页面的功能。

* **页面创作**
添加/编辑页面内容的功能。

* **DAM/资产管理**
管理数字资产（包括图像、视频、文档、下载）的功能。

* **ContextHub**
用于汇总访客信息并将其用于各种目的的功能。 提供用户界面以模拟访问网站的人员。 从AEM 6.2开始，ContextHub取代了以前的技术Client Context。

## 常规 {#general}

过去几年，Adobe使用统一的用户界面更新了所有Adobe Experience Cloud解决方案。 Experience Cloud解决方案中的用户在如何使用和操作应用程序方面拥有一致的常见模式体验。 在每个版本中，Adobe都根据跨不同解决方案工作的客户的反馈来优化其用户界面。

AEM 6.4中提供了Adobe Experience Manager（以前称为CQ5）的原始用户界面（2008年推出，由运行版本5.0-5.6.1的客户使用）。这样，客户就可以更新到6.4，并从更新后的平台中获益，同时可以继续使用相同的用户界面。

Adobe建议客户计划在2018/19中切换到新UI。 这可以在6.4的更新期间完成，或在更新后的单独项目中完成，这些项目将包括对自定义和组件对话框进行必要的调整。

Adobe不打算从AEM 6.4开始进一步增强经典UI。请注意，经典UI在弃用时仍完全受支持。

## 规则和Recommendations {#rules-and-recommendations}

以下是Adobe Experience Manager 6.4产品管理团队的建议列表：

<table> 
 <tbody> 
  <tr> 
   <th>我的项目……</th> 
   <th>推荐</th> 
  </tr> 
  <tr> 
   <td>刚开始使用Adobe Experience Manager。</td> 
   <td>使用默认UI。</td> 
  </tr> 
  <tr> 
   <td><p>已使用AEM一段时间。</p> <p>已使用现成的产品UI并为网站开发了自定义组件。<br /> </p> </td> 
   <td> 
    <ol> 
     <li>更新至6.4</li> 
     <li>使用默认UI进行站点管理、资产、 。 以此类推。<br /> </li> 
     <li>配置“编辑页面”操作以打开经典UI页面编辑器。 请参阅 <a href="#selecting-your-ui">选择您的UI</a>.</li> 
    </ol> <p>然后，在第二个阶段：</p> 
    <ol> 
     <li>更新组件对话框以使用Coral 3对话框格式。 Adobe建议使用 <a href="/help/sites-developing/modernization-tools.md">AEM现代化工具</a> 以更新组件。</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>已构建一个使用集成ClientContext的网站。<br /> </td> 
   <td> 
    <ol> 
     <li>更新至6.4</li> 
     <li>使用默认UI进行站点管理、资产、 。 以此类推。</li> 
     <li>配置“编辑页面”操作以打开经典UI页面编辑器。 请参阅 <a href="#selecting-your-ui">选择您的UI</a>.</li> 
    </ol> <p>然后，在第二个阶段：</p> 
    <ol> 
     <li>更新组件对话框以使用Coral 3对话框格式。 Adobe建议使用 <a href="/help/sites-developing/modernization-tools.md">AEM现代化工具</a> 以更新组件。</li> 
     <li>配置ContextHub(ClientContext的替换项)并更新页面模板以使用ContextHub。 请注意， ContextHub具有兼容模式，允许加载自定义ClientContext存储。</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><p>已使用CQ/AEM多年。</p> <p>扩展了产品UI（例如，站点管理员）并构建了包含大量编辑对话框的组件。</p> </td> 
   <td><p>更新至6.4，并将经典UI配置为所有用户创作页面的默认UI。 请参阅 <a href="#selecting-your-ui">选择您的UI</a>.</p> <p>然后，启动一个项目以应用自定义并优化Coral 3格式的组件对话框。 请参阅 <a href="#resources-to-help">要帮助的资源</a>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

## 常见问题 {#faq}

请参阅知识库文章， [触屏UI创作常见问题解答](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html)，以了解详细信息。包括有关经典UI弃用计划的任何信息。

## 选择您的UI {#selecting-your-ui}

请参阅 [选择您的UI](/help/sites-authoring/select-ui.md) 有关根据需要配置系统的信息。

## 触屏优化UI状态 {#touch-optimized-ui-status}

有关AEM 6.3中触屏优化UI增强功能的详细信息，请参阅 [新增功能](/help/release-notes/release-notes.md#what-s-new) 中。

完整概述请参阅 [触屏UI功能状态](/help/release-notes/touch-ui-features-status.md) 页面

## 要帮助的资源 {#resources-to-help}

有关基本操作的背景信息：

* [使用创作环境](/help/sites-authoring/home.md).
* [创作页面](/help/sites-authoring/author-environment-tools.md).

有关详细的开发信息：

* [触屏优化UI架构](/help/sites-developing/touch-ui-concepts.md).
* 使用 [AEM现代化工具](/help/sites-developing/modernization-tools.md) 将组件编辑对话框从经典UI转换为触屏优化UI。

* [触屏优化UI的结构](/help/sites-developing/touch-ui-structure.md).

* [在触屏优化UI中自定义控制台](/help/sites-developing/customizing-consoles-touch.md) （包括示例代码）。

* [在触屏优化UI中自定义页面创作](/help/sites-developing/customizing-page-authoring-touch.md) （包括示例代码）。

* [Granite用户界面文档](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).
