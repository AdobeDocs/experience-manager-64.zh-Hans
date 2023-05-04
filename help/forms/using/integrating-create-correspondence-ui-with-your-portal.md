---
title: 将创建通信UI与自定义门户集成
seo-title: Integrating Create Correspondence UI with your custom portal
description: 了解如何将创建通信UI与自定义门户相集成
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 4%

---

# 将创建通信UI与自定义门户集成 {#integrating-create-correspondence-ui-with-your-custom-portal}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

本文详细介绍如何将“创建通信解决方案”与您的环境相集成。

## 基于URL的调用 {#url-based-invocation}

从自定义门户调用“创建通信”应用程序的一种方法是使用以下请求参数准备URL:

* 信件模板的标识符（使用cmLetterId参数）或信件模板的名称（使用cmLetterName参数）

* 从所需数据源获取的XML数据的URL（使用cmDataUrl参数）。

例如，自定义门户会将URL准备为\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`，可以是门户链接中的href。\
如果门户手头有信件模板名称，则URL可能为\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`。

>[!NOTE]
>
>以这种方式调用是不安全的，因为通过在URL中公布相同（显示得很清楚）的参数，将必需的参数作为GET请求传递。

>[!NOTE]
>
>在调用创建通信应用程序之前，请保存并上传数据，以在给定的dataURL中调用创建通信UI。 这可以通过自定义门户本身或通过其他后端流程来完成。

## 内联基于数据的调用 {#inline-data-based-invocation}

调用创建通信应用程序的另一种（也是更安全的）方法是，只需点击 `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`时，将参数和数据作为POST请求发送以调用创建通信应用程序（向最终用户隐藏它们）。 这还意味着您现在可以在内联传递Create Correspondence应用程序的XML数据（作为同一请求的一部分，使用cmData参数），在以前的方法中，这是不可能的/理想的。

### 用于指定信件的参数 {#parameters-for-specifying-letter}

<table> 
 <tbody>
  <tr>
   <td><strong>名称</strong></td> 
   <td><strong>类型</strong></td> 
   <td><strong>描述</strong></td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>字符串</td> 
   <td>信件实例的标识符。</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>字符串</td> 
   <td><p>信件模板的标识符。 </p> <p>如果服务器上存在多个同名的CM字母，则在URL中使用cmLetterName参数会引发错误“存在多个带有名称的字母”。 在这种情况下，请在URL中使用cmLetterId参数，而不是cmLetterName。</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>字符串</td> 
   <td>信件模板的名称。</td> 
  </tr>
 </tbody>
</table>

表中的参数顺序指定用于加载信件的参数的首选项。

### 用于指定XML数据源的参数 {#parameters-for-specifying-the-xml-data-source}

<table> 
 <tbody>
  <tr>
   <td><strong>名称</strong></td> 
   <td><strong>类型</strong></td> 
   <td><strong>描述</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>使用基本协议（如cq、ftp、http或文件）从源文件获取XML数据。<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>字符串</td> 
   <td>使用信件实例中可用的xml数据。</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>布尔值</td> 
   <td>重复使用数据字典中附加的测试数据。</td> 
  </tr>
 </tbody>
</table>

表中参数的顺序指定用于加载XML数据的参数的首选项。

### 其他参数 {#other-parameters}

<table> 
 <tbody>
  <tr>
   <td><strong>名称</strong></td> 
   <td><strong>类型</strong></td> 
   <td><strong>描述</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>布尔值</td> 
   <td>如果在预览模式下打开信件，则为true<br /> </td> 
  </tr>
  <tr>
   <td>随机</td> 
   <td>时间戳</td> 
   <td>用于解决浏览器缓存问题。</td> 
  </tr>
 </tbody>
</table>

如果您对cmDataURL使用http或cq协议，则http/cq的URL应当可以匿名访问。
