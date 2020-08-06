---
title: 将创建对应UI与自定义门户集成
seo-title: 将创建对应UI与自定义门户集成
description: 了解如何将创建通信UI与自定义门户集成
seo-description: 了解如何将创建通信UI与自定义门户集成
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 3%

---


# 将创建对应UI与自定义门户集成 {#integrating-create-correspondence-ui-with-your-custom-portal}

## 概述 {#overview}

本文详细介绍了如何将“创建通信解决方案”与环境集成。

## 基于URL的调用 {#url-based-invocation}

从自定义门户调用“创建对应”应用程序的一种方法是使用以下请求参数准备URL:

* 字母模板的标识符（使用cmLetterId参数）或字母模板的名称（使用cmLetterName参数）

* 从所需数据源获取的XML数据的URL（使用cmDataUrl参数）。

例如，自定义门户会将URL准备为\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`，这可以是门户上链接的href。\
如果门户手头有“信函”模板名称，则URL可以\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`。

>[!NOTE]
>
>以这种方式进行调用是不安全的，因为通过在URL中显示相同（清晰可见）的参数，将必需的参数作为GET请求传递。

>[!NOTE]
>
>在调用创建对应应用程序之前，请保存并上传数据，以在给定的dataURL调用创建对应UI。 这可以从自定义门户本身或通过另一个后端进程完成。

## 内联基于数据的调用 {#inline-data-based-invocation}

调用“创建通信”应用程序的另一种（也是更安全的）方法是，只需点击URL，同时发送参数和POST以调用“创建通信”应用程序作为请求（将它们隐藏在最终用户面前）。 `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`这也意味着您现在可以内嵌（作为同一请求的一部分，使用cmData参数）传递Create Commendence应用程序的XML数据，这在以前的方法中是不可能的／理想的。

### 用于指定字母的参数 {#parameters-for-specifying-letter}

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
   <td>字母实例的标识符。</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>字符串</td> 
   <td><p>字母模板的标识符。 </p> <p>如果服务器上存在多个同名的CM字母，则在URL中使用cmLetterName参数会引发错误“存在多个带名称的字母”。 在这种情况下，请在URL中使用cmLetterId参数，而不要使用cmLetterName。</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>字符串</td> 
   <td>字母模板的名称。</td> 
  </tr>
 </tbody>
</table>

表中的参数顺序指定用于加载字母的参数的首选项。

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
   <td>使用字母实例中可用的xml数据。</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>布尔型</td> 
   <td>重用数据字典中附加的测试数据。</td> 
  </tr>
 </tbody>
</table>

表中的参数顺序指定用于加载XML数据的参数的首选项。

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
   <td>布尔型</td> 
   <td>如果在预览模式下打开字母，则为True<br /> </td> 
  </tr>
  <tr>
   <td>随机</td> 
   <td>时间戳</td> 
   <td>解决浏览器缓存问题。</td> 
  </tr>
 </tbody>
</table>

如果对cmDataURL使用http或cq协议，则http/cq的URL应匿名访问。
