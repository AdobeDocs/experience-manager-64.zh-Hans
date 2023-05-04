---
title: SocialUtils重构
seo-title: SocialUtils Refactoring
description: com.adobe.cq.social.ugcbase.SocialUtils包已在AEM 6.1中弃用
seo-description: The package com.adobe.cq.social.ugcbase.SocialUtils was deprecated in AEM 6.1
uuid: 54a0d98e-5ead-4c12-850f-8252ea9b3263
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4ade0d6b-041e-4a2f-98f8-3b8fcae0fb29
exl-id: ba23188b-a72a-4349-b3e5-0fb50fd6312f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# SocialUtils重构 {#socialutils-refactoring}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 已弃用SocialUtils包 {#socialutils-package-deprecated}

包 **com.adobe.cq.social.ugcbase.SocialUtils** 已在AEM 6.1中弃用。

下表列出了用于代替SocialUtils方法的方法。

## SocialResourceUtilities包  {#socialresourceutilities-package}

| com.adobe.cq.social.srp.utilities.api.SocialResourceUtilities中的方法 |
|---|
| 布尔型checkPermission(ResourceResolver， String path， String action) |  |
| SocialResourceProvider getSocialResourceProvider（资源） |  |
| SocialResourceConfiguration getStorageConfig（资源） |  |
| 资源getUGCResource(Resource userResource) |  |
| 资源getUGCResource(Resource userResource， ResourceResolverFactory rrf) | 新建 |
| 资源getUGCResource(Resource userResource， ResourceResolverFactory rrf， String resourceTypeHint) | 新建 |
| 资源getUGCResource(Resource userResource， String resourceTypeHint) |  |
| 布尔值hasMediatePermissions（资源） |  |
| 字符串resourceToACLPath（资源资源） |  |
| 字符串resourceToUGCStoragePath（资源资源） | 替换字符串resourceToUGCPath(Resource resource) |
| 字符串UGCToResourcePath（资源资源） |  |
| 字符串UGCToResourcePath（字符串ugcPath） | 更改了签名 |
| 字符串UGCToResourcePath（字符串ugcPath， ResourceResolver） | 新建 |

| 中的方法 `com.adobe.cq.social.`utilities.resource.api.SocialResourceUtilities |
|---|
| SocialResourceProvider getSocialResourceProvider（资源） | 替换SocialResourceProvider getConfiguredProvider(Resource resource) |

## SCFUtilities包 {#scfutilities-package}

| 中的方法 `com.adobe.cq.social.`实用程序.scf.api.SCFUtilites |
|---|
| 字符串getAvatar(UserProperties userProperties) |
| 字符串getAvatar(UserProperties userProperties， int size) |
| 字符串getAvatar(UserProperties userProperties， String absoluteDefaultAvatar) |
| 字符串getAvatar(UserProperties userProperties， String absoluteDefaultAvatar， SocialUtils.AVATAR_SIZE size) |
| 页面getContainingPage（资源） |
| 字符串getSocialProfileURL（字符串用户名， ResourceResolver， Page页） |
| UserProperties getUserProperties(ResourceResolver， String userId) |

## 仅供内部使用 {#for-internal-use-only}

| 布尔canAddNode（会话会话，字符串路径） |
|---|
| 字符串createUniqueNameHint（字符串消息） |
| 字符串createUniqueNameHint(String message， int numRandomChars) |
| 字符串generateRandomString(int length) |
| SocialResourceConfiguration getDefaultStorageConfig() |
| 页面getPage（字符串路径， ResourceResolver） |
| 字符串getPagePath（资源） |
| 字符串getPagePath（字符串路径） |
| 字符串getResourceTypeForIncludedResource（资源组件，字符串defaultResourceType，字符串designPropertyName） |
| 字符串getResourceTypeFromDesign（资源，字符串样式属性，字符串默认值） |
| 布尔值isResourceOwner（资源） |
| 字符串mapUGCPath（资源） |
| 字符串mapUGCPath（字符串ugcPath， ResourceResolver） |
| 布尔型mayPost(ResourceResolver， Resource) |
| 字符串prepareUserGeneratedContent(ResourceResolver， String path) |

## 方法不再可用 {#methods-no-longer-available}

| Node createNode(ResourceResolver， String path， String nodeType) |
|---|
| Resource getResourceAtPath(ResourceResolver， String path) |
| Resource getResourceAtPath(ResourceResolver， String path， String resourceType) |
| 配置getStorageCloudServiceConfig（资源） |
| TranslationManager getTranslationManager() |
| TranslationSaveQueue getTranslationSaveQueue() |
| 布尔型mayAccessUGC(ResourceResolver) |
