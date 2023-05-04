---
title: 使 CDN 缓存内容无效
seo-title: Invalidating your CDN cached content
description: 通过使CDN（内容交付网络）缓存内容失效，您可以快速更新由Dynamic Media交付的资产，而无需等待缓存过期。
seo-description: Invalidating your CDN (Content Delivery Network) cached content lets you quickly update assets that are delivered by Dynamic Media, instead of waiting for the cache to expire.
uuid: 0fd88e31-9745-4c98-a245-9f5d0766cad4
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: e6c9b50b-c27c-48bf-b3c0-9994e7bf6d7e
exl-id: 335c7a78-a00f-451b-8e53-225830d429c6
feature: Asset Management,CDN Cache
role: Admin,User,Developer
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 28%

---

# 使 CDN 缓存内容无效 {#invalidating-your-cdn-cached-content}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Dynamic Media资产由CDN缓存以便快速交付。 但是，当您对资产进行更新时，您可能希望这些更改立即生效。 通过使CDN（内容交付网络）缓存内容失效，您可以快速更新由Dynamic Media交付的资产，而无需等待缓存过期。

另请参阅 [Dynamic Media Classic中的缓存概述](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**要使CDN缓存内容失效，请执行以下操作：**

1. 登录到Dynamic Media Classic桌面应用程序。

   [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app)

   您的凭据和登录是在配置时由Adobe提供的。 如果您没有此信息，请联系技术支持。

1. 单击&#x200B;**[!UICONTROL 设置 > 应用程序设置 > 常规设置]**。
1. 在“应用程序常规设置”页面的“服务器”组标题下，找到 **[!UICONTROL CDN失效模板]** 框中。

1. 指定用于使CDN（内容交付网络）缓存失效的模板。

   例如，假定您输入了引用 `<ID>`，而不是像以下示例中那样使用特定的图像ID:

   `https://server.com/is/image/Company/<ID>?$product$`

   如果模板仅包含 `<ID>`，然后Dynamic Media填充 `https://<server>/is/image` where `<server>` 是在“常规设置”中定义的“发布服务器名称”， &lt;id> 是否选定要失效的资产。

1. 在页面的右下角，单击 **[!UICONTROL 关闭]**.
1. 在Dynamic Media Classic桌面应用程序的用户界面中，选择一个或多个资产，然后单击 **[!UICONTROL 文件>无效CDN]**. 您将看到一个列表，其中包含从您创建的模板以及您选择的资产中生成的一个或多个URL。 它使用“应用程序常规设置”下“已发布的服务器名称”下列出的服务器URL。

   例如，在上一步中设置CDN失效模板后，假定您选择了一个名为 `Backpack_B`. 单击 **[!UICONTROL 文件>无效CDN]** 这会导致在CDN失效用户界面中生成以下URL:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. 在URL列表框中，单击 **[!UICONTROL 继续]** 以清除每个特定URL的缓存。 请注意，您可以编辑URL，也可以通过键入或粘贴URL列表框来添加URL;您无需预先设置CDN无效模板。

   在单击 **[!UICONTROL 继续]**，将显示一个指示器，用于估算清除缓存需要多长时间。

   如果您选择了多个资产，请单击&#x200B;**[!UICONTROL 文件 > 无效 CDN]**，则每个资产都会在保存的&#x200B;**[!UICONTROL 模板 URL]** 中引用。因此，您可以定义 **[!UICONTROL CDN 无效模板]**，以引用网站上引用的每个 URL 图像预设（如产品详细信息、搜索结果等）。然后，当您从缓存中选择一个或多个要失效的图像时，URL 会自动填充该界面。

   >[!NOTE]
   >
   >当您选择资产，然后单击&#x200B;**[!UICONTROL 文件 > 无效 CDN]** 时，Dynamic Media 会使用无效 CDN 模板从内容交付网络 (CDN) 自动创建 URL。如果 **[!UICONTROL CDN 无效模板]**&#x200B;文本框中没有任何内容，则会显示空白 URL 列表。CDN 上的缓存不是基于资产，而是基于 URL。因此，必须了解您网站上的完整 URL。确定这些 URL 后，可以将其添加到步骤前面的&#x200B;**[!UICONTROL 无效 CDN 模板]**。然后，您可以选择这些资产，并在一个步骤中使 URL 失效。
   >
   >另一个选项是向 **[!UICONTROL 无效CDN]** 列表。 如果您遵循此方法，则无需在转到 **[!UICONTROL 文件>无效CDN]** 选项。
