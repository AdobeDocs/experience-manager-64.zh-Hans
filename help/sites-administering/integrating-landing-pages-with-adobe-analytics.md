---
title: 将登陆页与Adobe Analytics集成
seo-title: 将登陆页与Adobe Analytics集成
description: 了解如何将登陆页与Adobe Analytics集成。
seo-description: 了解如何将登陆页与Adobe Analytics集成。
uuid: 8f6672d1-497f-4ccb-b3cc-f6120fc467ba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8ae7ccec-489b-4d20-ac56-6101402fb18a
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 24%

---


# 将登陆页与Adobe Analytics集成{#integrating-landing-pages-with-adobe-analytics}

AEM通过使用以下行动 [动员](https://www.omniture.com/en/products/analytics/sitecatalyst) (CTA)组件将登陆页解决方案与Adobe Analytics集成：

1. 点进率组件
1. 图形链接组件

这些组件提供可通过Adobe Analytics变量（流量、转换变量）映射的特定属性，以及成功事件将信息发送到Adobe Analytics。

## 前提条件 {#prerequisites}

Adobe建议您通过现有的AEM [-Adobe Analytics集成](/help/sites-administering/adobeanalytics.md) ，了解此集成的工作方式。

## 可用于映射的组件 {#components-available-for-mapping}

在AEM中，Sidekick中 **此处显示** 的 **行动动员组件** - ClickThroughLink **** 和GraphicalLink，可映射到Adobe Analytics变量。

![chlimage_1-21](assets/chlimage_1-21.jpeg)

### 将登陆页组件映射到Adobe Analytics {#mapping-landing-page-components-to-adobe-analytics}

要将登陆页组件映射到Adobe Analytics:

1. 创建Adobe Analytics配置并创建新框架后，从下拉菜单中选择相应的报告套件。 这会导致获取Adobe Analytics变量并在内容查找器中显示它们。
1. 按需要将 Sidekick 中的行动动员 (CTA) 组件拖放至页面中部的映射区。

<table> 
 <tbody>
  <tr>
   <td><strong>组件名称</strong></td> 
   <td><strong>显示的属性</strong></td> 
   <td><strong>属性含义</strong></td> 
  </tr>
  <tr>
   <td><strong>CTA 点进率链接</strong></td> 
   <td><i>eventdata.clickthroughLinkLabel</i> <br /> </td> 
   <td>链接上的标签或链接的文本 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clickthroughLinkTarget</i> <br /> </td> 
   <td>单击链接时被带到的目标位置 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.事件.clickthroughLinkClick</i> <br /> </td> 
   <td>单击事件 </td> 
  </tr>
  <tr>
   <td><strong>CTA 图形链接</strong></td> 
   <td><i>eventdata.clicktroughImageLabel</i> <br /> </td> 
   <td>CTA图像的标题 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clicktroughImageTarget</i> <br /> </td> 
   <td>您在单击包含链接的图像后被引向的目标地。</td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.clicktroughImageAsset</i> <br /> </td> 
   <td>存储库中图像资产的路径 </td> 
  </tr>
  <tr>
   <td><br type="_moz" /> </td> 
   <td><i>eventdata.事件.clicktroughImageClick</i> <br /> </td> 
   <td>单击事件</td> 
  </tr>
 </tbody>
</table>

1. 使用内容查找器中的任何Adobe Analytics变量映射这些暴露的属性。 框架现已准备就绪。
1. 您现在可以使用现有CTA组件创建新登陆页或打开现有登陆页，然后从Sidekick中单击页面属 **性** (在触屏优化UI中，选择“打开属性 **”并单**********&#x200B;击Cloud Services)中的“Cloud Services”选项卡，并配置框架以使用登陆页。 在下拉列表中选择框架。

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. 使用登陆页配置框架后，您现在可以使用已插入的组件，并且CTA的任何点击都会记录在Adobe Analytics。

