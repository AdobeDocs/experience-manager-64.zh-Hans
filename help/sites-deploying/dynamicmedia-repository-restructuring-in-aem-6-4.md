---
title: Dynamic Media 6.4中的存储库重组
seo-title: Dynamic Media repository restructuring in AEM 6.4
description: 了解如何进行必要的更改，以便迁移到AEM 6.4 for Dynamic Media中的新存储库结构。
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Dynamic Media.
uuid: e26d61a4-47b6-493a-9ba2-4c58b200ddd9
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 61cd5751-0dc8-48e0-873e-3a64899489bb
feature: Upgrading
exl-id: 1323ee60-c80c-4eed-b3e5-aa0f0c07e6ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 5%

---

# Dynamic Media 6.4中的存储库重组{#dynamic-media-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如父项中所述 [AEM 6.4中的存储库重组](/help/sites-deploying/repository-restructuring.md) 页面，升级到AEM 6.4的客户应使用此页面来评估与影响Dynamic Media解决方案的存储库更改相关的工作量。 某些更改在AEM 6.4升级过程中需要工作，而其他更改可能会推迟到6.5升级。

**6.5升级之前**

* [自定义自适应视频编码配置](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#custom-adaptive-video-encoding-configurations)
* [Dynamic Media(DMS7)云配置](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#dynamic-media-dms-cloud-configuration)
* [Dynamic Media（DM混合）Cloud Service配置](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#cloudserviceconfiguration)
* [Dynamic Media - YouTubeCloud Service配置](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#youtubecloudserviceconfiguration)
* [杂项](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md#misc)

## 6.5升级之前 {#prior-to-upgrade}

### 自定义自适应视频编码配置  {#custom-adaptive-video-encoding-configurations}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/dam/video/dynamicmedia</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td> 
  </tr>
  <tr>
   <td><strong>重组指导</strong></td> 
   <td><p>您可以运行以下迁移脚本以迁移到新位置：</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>或者，您也可以在AEM UI中编辑配置，并且更改将保存到新位置。</p> </td> 
  </tr>
  <tr>
   <td><strong>注释</strong></td> 
   <td>不适用<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media(DMS7)云配置 {#dynamic-media-dms-cloud-configuration}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td> 
  </tr>
  <tr>
   <td><strong>重组指导</strong></td> 
   <td><p>客户可以在此位置运行迁移脚本：<br /> </p> 
    <ul> 
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li> 
     <li>重新启动Dynamic Media OSGi包。</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>注释</strong></td> 
   <td>不适用</td> 
  </tr>
 </tbody>
</table>

### Dynamic Media（DM混合）Cloud Service配置 {#cloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td> 
  </tr>
  <tr>
   <td><strong>重组指导</strong></td> 
   <td><p>您可以运行以下迁移脚本，以便与最新模型保持一致：</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td> 
  </tr>
  <tr>
   <td><strong>注释</strong></td> 
   <td>不适用<br /> </td> 
  </tr>
 </tbody>
</table>

### Dynamic Media -YouTubeCloud Service配置  {#youtubecloudserviceconfiguration}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/cloudservices/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/libs/settings/dam/dm/youtube</code></td> 
  </tr>
  <tr>
   <td><strong>重组指导</strong></td> 
   <td><p>1.从YouTube取消发布所有视频<br /> 2. 使用新的触屏UI创建YouTube配置(从 <code>/conf</code>)，包括从旧位置复制所有渠道<br /> 3. 将所有视频发布回YouTube。</p> <p>此工作流会生成新的YouTube URL。 如果在创建新的触屏UI YouTube配置之前未取消发布，则“属性”下将列出多个YouTube URL，因为如果有机会，重新创建的渠道将再次发布。 这表示您的“属性”下将列出无用的URL。</p> </td> 
  </tr>
  <tr>
   <td><strong>注释</strong></td> 
   <td>不适用<br /> </td> 
  </tr>
 </tbody>
</table>

### 杂项 {#misc}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/dam/imageserver/macros</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td> 
  </tr>
  <tr>
   <td><strong>重组指导</strong></td> 
   <td><p>客户可以运行以下迁移脚本。</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>或者，您也可以在AEM UI中编辑配置，并且更改将保存到新位置。</p> </td> 
  </tr>
  <tr>
   <td><strong>注释</strong></td> 
   <td>不适用</td> 
  </tr>
 </tbody>
</table>

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><code>/etc/dam/presets/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><code>/libs/settings/dam/dm/analytics</code></td> 
  </tr>
  <tr>
   <td><strong>重组指导</strong></td> 
   <td><p>客户可以运行以下迁移脚本。</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td> 
  </tr>
  <tr>
   <td><strong>注释</strong></td> 
   <td>不适用</td> 
  </tr>
 </tbody>
</table>
