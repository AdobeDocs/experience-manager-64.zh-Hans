---
title: 配置通信管理解决方案
seo-title: 配置通信管理解决方案
description: 了解如何为创作实例版本还原定义创作实例URL，以及为公共实例激活管理器定义发布实例URL。
seo-description: 了解如何为创作实例版本还原定义创作实例URL，以及为公共实例激活管理器定义发布实例URL。
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: 通信管理
exl-id: a062957d-a526-4c4b-bbc5-0cda8ab007a3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 1%

---

# 配置通信管理解决方案{#configuring-a-correspondence-management-solution}

## 为VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}定义创作实例URL

使用以下步骤为创作实例版本还原定义创作实例URL:

1. 转到&#x200B;*https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*。 使用OSGi管理控制台用户凭据登录。 默认凭据为管理员/管理员。
1. 找到并单击&#x200B;****&#x200B;设置旁边的&#x200B;**[!UICONTROL 编辑图标。com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]**&#x200B;旁边的。
1. 在&#x200B;**[!UICONTROL VersionRestoreManager创作URL]**&#x200B;字段中，指定VersionRestoreManager创作实例的URL。

   **URL字符串**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >如果负载平衡器前面有多个创作实例（群集），请在&#x200B;**[!UICONTROL VersionRestoreManager创作URL]**&#x200B;字段中指定指向负载平衡器的URL。

1. 单击&#x200B;**[!UICONTROL 保存]**。

## 为ActivationManagerImpl（公共实例激活管理器）定义发布实例URL {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

按照以下步骤为公共实例激活管理器定义发布实例URL:

1. 转到&#x200B;*https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*。 使用OSGi管理控制台用户凭据登录。 默认凭据为管理员/管理员。
1. 找到并单击&#x200B;****&#x200B;设置旁边的&#x200B;**[!UICONTROL 编辑图标，即com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]**&#x200B;旁边的图标。
1. 在&#x200B;**[!UICONTROL ActivationManager Publish URL]**&#x200B;字段中，指定用于访问Publish实例ActivationManager的URL。 您可以提供以下URL。

   * **负载平衡器URL（推荐）**:提供负载平衡器URL。如果您在发布场（多个非群集发布实例）之前有一个Web服务器充当负载平衡器。
   * **发布实例URL**:提供任何发布实例URL。如果您有单个发布实例，或者发布场的Web服务器由于任何限制而无法从创作环境访问。如果指定的发布实例关闭，则在创作端有一个要处理的回退机制。
   * **URL字符串**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. 单击&#x200B;**[!UICONTROL 保存]**。

有关配置通信管理的更多信息，请参阅[通信管理配置属性](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html)。
