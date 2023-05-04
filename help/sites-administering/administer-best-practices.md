---
title: 最佳实践
description: 了解由Adobe工程和咨询团队编译的Adobe Experience Manager最佳实践，以帮助管理员快速入门并运行。
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
exl-id: 8c41dba4-bedc-4747-b67d-fd89d71c8b2c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 8%

---

# 最佳实践{#best-practices}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

最佳实践介绍如何以最有效、最有效的方式开发、管理或使用AEM。 这个不断增长的主题列表包括AEM中的多个区域。

以下区域提供了有关最佳实践的文档：

* [Assets](#assets)
* [Sites](#sites)

有关创作、部署和维护或开发的最佳实践，请参阅以下内容之一：

* [创作最佳实践](/help/sites-authoring/best-practices.md)
* [制定最佳实践](/help/sites-developing/best-practices.md)
* [部署最佳实践](/help/sites-deploying/best-practices.md)

下表中描述并链接了特定文档。

## Assets {#assets}

以下主题介绍了有关资产(包括Dynamic Media功能和Dynamic Media Classic集成)的最佳实践：

<table> 
 <tbody>
  <tr>
   <td>围绕Assets的不同领域的最佳实践，以增强负载下的系统稳定性和性能</td> 
   <td><a href="/help/assets/organize-assets.md">用于资产的最佳实践</a></td> 
   <td>包括指向资产不同区域最佳实践指南的链接。 在审核了这些信息后，您将拥有构建和管理企业资产管理系统的知识和工具。</td> 
  </tr>
  <tr>
   <td>如何组织内容（文件夹层次结构）</td> 
   <td><a href="/help/assets/organize-assets.md">文件管理最佳实践</a></td> 
   <td>大多数处理配置文件都基于文件夹，因为视频、元数据和图像处理始终应用于文件夹。 此最佳实践文档介绍了如何定义和设置文件夹层次结构，因为该层次结构对内容的处理方式有重大影响。 </td> 
  </tr>
  <tr>
   <td>集成Dynamic Media Classic和AEM</td> 
   <td><a href="/help/sites-administering/scene7.md#best-practices-for-integrating-scene-with-aem">将Dynamic Media Classic与AEM集成的最佳实践</a></td> 
   <td><p>介绍何时打开轮询导入器、如何测试集成，以及何时使用内容浏览器，何时直接上传到资产。</p> </td> 
  </tr>
  <tr>
   <td>图像预设选项</td> 
   <td>了解 <a href="/help/assets/managing-image-presets.md#understanding-image-presets">图像预设</a> 和 <a href="/help/assets/managing-image-presets.md#image-preset-options">图像预设最佳实践</a></td> 
   <td>作为 <a href="/help/assets/managing-image-presets.md">管理图像预设</a>，以下主题将介绍图像预设的含义以及有关选择图像预设选项的最佳实践。</td> 
  </tr>
  <tr>
   <td>Dynamic Media与Dynamic Media Classic的直接集成</td> 
   <td><a href="/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media">Dynamic Media Classic/AEM集成与Dynamic Media</a></td> 
   <td>描述何时最好使用Dynamic Media解决方案，何时将S7与AEM集成，或何时同时使用这两者。</td> 
  </tr>
 </tbody>
</table>

## Sites {#sites}

管理和创作网站内容有一些最佳实践，如下所述：

<table> 
 <tbody>
  <tr>
   <td>GDPR合规</td> 
   <td><a href="/help/sites-administering/gdpr-compliance-sites.md">AEM Sites GDPR合规</a></td> 
   <td>欧盟的《数据隐私权通用数据保护条例》已于2018年5月正式生效。 AEM Sites符合GDPR。 本页面将指导客户完成在AEM Sites中处理GDPR请求的过程。 它描述了私有数据的存储位置，以及如何手动或使用代码删除私有数据。</td> 
  </tr>
  <tr>
   <td>为实例定义默认UI。</td> 
   <td><p><a href="/help/sites-authoring/select-ui.md#configuring-the-default-ui-for-your-instance">为实例配置默认UI</a></p> </td> 
   <td>AEM有两个UI:触控优化和经典。 本节详细介绍如何为实例定义默认UI。</td> 
  </tr>
  <tr>
   <td>多站点管理</td> 
   <td><a href="/help/sites-administering/msm-best-practices.md">MSM 最佳实践</a></td> 
   <td>使用MSM自动部署内容的最佳实践。 </td> 
  </tr>
  <tr>
   <td>翻译内容</td> 
   <td><a href="/help/sites-administering/tc-bp.md">翻译最佳实践</a></td> 
   <td>规划和实施多语言站点的最佳实践。</td> 
  </tr>
  <tr>
   <td>用户管理</td> 
   <td><a href="/help/sites-administering/security.md#best-practices">权限和权限最佳实践</a></td> 
   <td>介绍使用权限和权限时的最佳实践 </td> 
  </tr>
  <tr>
   <td>工作流</td> 
   <td><a href="/help/sites-developing/workflows-best-practices.md#configuration">工作流最佳实践 — 配置</a></td> 
   <td>工作流使您能够自动执行Adobe Experience Manager(AEM)活动，并且可以代表AEM环境中发生的大量处理，因此强烈建议仔细规划和配置工作流实施。</td> 
  </tr>
 </tbody>
</table>
