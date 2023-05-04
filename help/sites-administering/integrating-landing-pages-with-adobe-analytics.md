---
title: 将登陆页面与Adobe Analytics集成
seo-title: Integrating Landing Pages with Adobe Analytics
description: 了解如何将登陆页面与Adobe Analytics集成。
seo-description: Learn how to integrate landing pages with Adobe Analytics.
uuid: 8f6672d1-497f-4ccb-b3cc-f6120fc467ba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8ae7ccec-489b-4d20-ac56-6101402fb18a
exl-id: 2923ae94-375a-4c44-a08f-f992eb08000a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---

# 将登陆页面与Adobe Analytics集成{#integrating-landing-pages-with-adobe-analytics}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM已将登陆页面解决方案与 [Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) 使用以下行动动员(CTA)组件：

1. 点进组件
1. 图形链接组件

这些组件显示可通过Adobe Analytics变量（流量、转化变量）映射的特定属性，以及成功事件，以将信息发送到Adobe Analytics。

## 前提条件 {#prerequisites}

Adobe建议您浏览 [现有AEM-Adobe Analytics集成](/help/sites-administering/adobeanalytics.md) 以了解此集成的工作原理。

## 可用于映射的组件 {#components-available-for-mapping}

在AEM中， **行动动员** 组件 —  **ClickThroughLink** 和 **图形链接**  — 显示在Sidekick中，可以映射到Adobe Analytics变量。

![chlimage_1-21](assets/chlimage_1-21.jpeg)

### 将登陆页面组件映射到Adobe Analytics {#mapping-landing-page-components-to-adobe-analytics}

要将登陆页面组件映射到Adobe Analytics，请执行以下操作：

1. 创建Adobe Analytics配置并创建新框架后，从下拉菜单中选择相应的报表包。 这会导致获取Adobe Analytics变量并在内容查找器中显示它们。
1. 将行动动员(CTA)组件酌情从Sidekick拖放到页面中间的映射区域。

<table> 
 <tbody>
  <tr>
   <td><strong>组件名称</strong></td> 
   <td><strong>显示的属性</strong></td> 
   <td><strong>属性含义</strong></td> 
  </tr>
  <tr>
   <td><strong>CTA点进链接</strong></td> 
   <td><i>eventdata.clickthroughLinkLabel</i> <br /> </td> 
   <td>链接上的标签或链接的文本 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clickthroughLinkTarget</i> <br /> </td> 
   <td>您在单击链接时到达的目标 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.events.clickthroughLinkClick</i> <br /> </td> 
   <td>点击事件 </td> 
  </tr>
  <tr>
   <td><strong>CTA图形链接</strong></td> 
   <td><i>eventdata.clicktroughImageLabel</i> <br /> </td> 
   <td>CTA图像的标题 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clicktroughImageTarget</i> <br /> </td> 
   <td>单击包含链接的图像时您被带到的目标位置</td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clicktroughImageAsset</i> <br /> </td> 
   <td>存储库中图像资产的路径 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.events.clicktroughImageClick</i> <br /> </td> 
   <td>点击事件</td> 
  </tr>
 </tbody>
</table>

1. 使用内容查找器中的任何Adobe Analytics变量映射这些公开的属性。 框架现已准备就绪，可供使用。
1. 您现在可以创建新登陆页面，或打开包含现有CTA组件的现有登陆页面，然后单击 **Cloud Services** 选项卡 **页面属性** 从sidekick(在触屏优化UI中，选择 **打开属性** 单击 **Cloud Services**)并配置框架以与登陆页面一起使用。 从下拉列表中选择框架。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 在使用登陆页面配置框架后，您现在可以使用感知组件，任何对CTA的点击都会记录在Adobe Analytics中。
