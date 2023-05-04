---
title: 管理 [!DNL Adobe Stock] 资产 [!DNL Adobe Experience Manager Assets].
description: 搜索、获取、许可和管理 [!DNL Adobe Stock] 资产 [!DNL Adobe Experience Manager]. 将授权资产用作任何其他数字资产。
contentOwner: AG
feature: Search,Adobe Stock
role: User,Admin
exl-id: f360abaf-a812-46ed-a160-ff569b6bec1c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 11%

---

# 使用 [!DNL Adobe Stock] 资产 [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

组织可以集成其 [!DNL Adobe Stock] 企业计划 [!DNL Experience Manager Assets] 以确保获得许可的资产可广泛用于其创意和营销项目，并具有 [!DNL Experience Manager].

[!DNL Adobe Stock] 该服务为设计人员和企业提供了数百万个高品质、精选且免版税的照片、矢量、插图、视频、模板和3D资产，供其所有创意项目使用。 [!DNL Experience Manager] 用户能够快速查找、预览和许可 [!DNL Adobe Stock] 保存在 [!DNL Experience Manager]，而不离开 [!DNL Experience Manager] 界面。

## 前提条件 {#prerequisites}

该集成需要 [企业Adobe Stock计划](https://stockenterprise.adobe.com/) 和 [!DNL Experience Manager] 6.4并至少部署了Service Pack 2。 对于 [!DNL Experience Manager] 6.4 service pack详细信息，请参阅这些 [发行说明](/help/release-notes/sp-release-notes.md).

## 集成 [!DNL Experience Manager] 和 [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

允许在 [!DNL Experience Manager] 和 [!DNL Adobe Stock]，创建IMS配置和 [!DNL Adobe Stock] 配置 [!DNL Experience Manager].

>[!NOTE]
>
>仅 [!DNL Experience Manager] 管理员和 [!DNL Admin Console] 组织的管理员可以执行需要管理员权限的集成。

### 创建IMS配置 {#create-an-ims-configuration}

1. 在 [!DNL Experience Manager] 用户界面，导航至 **[!UICONTROL 工具]** > **[!UICONTROL 安全性]** > **[!UICONTROL Adobe IMS配置]**. 单击&#x200B;**[!UICONTROL 创建]**，然后选择&#x200B;**[!UICONTROL 云解决方案]** > **[!UICONTROL Adobe Stock]**。
1. 重复使用现有证书或选择 **[!UICONTROL 创建新证书]**.
1. 单击&#x200B;**[!UICONTROL 创建证书]**。创建后，下载公钥。 单击&#x200B;**[!UICONTROL 下一步]**。离开 [!UICONTROL Adobe IMS技术帐户配置] 屏幕打开，以便很快提供所需的值。
1. 访问 [Adobe Developer控制台](https://console.adobe.io). 确保您的帐户拥有需要集成的组织的管理员权限。
1. 单击 **[!UICONTROL 创建新项目]** 单击 **[!UICONTROL 添加API]**. 选择 **[!UICONTROL Adobe Stock]** 从您可用的API列表中。 选择 [!UICONTROL OAUTH 2.0 Web].
1. 提供 **[!UICONTROL 默认重定向URI]** 和 **[!UICONTROL 重定向URI模式]** 值。 单击&#x200B;**[!UICONTROL 保存配置的 API]**。复制生成的ID和密钥。
1. 在 [!UICONTROL Adobe IMS技术帐户配置] ，在标题为 **[!UICONTROL 标题]**, **[!UICONTROL 授权服务器]**, **[!UICONTROL API密钥]**, **[!UICONTROL 客户端密钥]**&#x200B;和 **[!UICONTROL 负载]**. 有关这些值的详细信息，请参阅 [JWT身份验证快速入门](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

<!-- TBD: Update the URL when the new URL is available. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### 创建 [!DNL Adobe Stock] 配置 [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. 在 [!DNL Experience Manager] 用户界面，导航至 **[!UICONTROL 工具]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. 单击 **[!UICONTROL 创建]** 创建配置并将其与您现有的IMS配置关联。 选择 `PROD` 作为环境参数。
1. 在 **[!UICONTROL 授权资产路径]** 字段中，保留原样的位置。 请勿更改要存储 [!DNL Adobe Stock] 资产。
1. 通过添加所有必需属性完成创建。 单击“**[!UICONTROL 保存并关闭]**”。
1. 添加 [!DNL Experience Manager] 用户或组，他们可以授权资产。

>[!NOTE]
>
>如果存在多个 [!DNL Adobe Stock] 配置中，在用户首选项面板(**[!UICONTROL AEM]** > **[!UICONTROL 用户图标]** > **[!UICONTROL 用户首选项]** > **[!UICONTROL 库存配置]**)。

## 使用和管理 [!DNL Adobe Stock] 资产 [!DNL Experience Manager] {#usemanage}

使用此功能，组织可以允许其用户使用 [!DNL Adobe Stock] 资产 [!DNL Experience Manager Assets]. 从 [!DNL Experience Manager] 用户界面，用户可搜索 [!DNL Adobe Stock] 资产，并授予所需资产的许可。

一次 [!DNL Adobe Stock] 资产在 [!DNL Experience Manager]，则可以像常规资产一样使用和管理该资产。 在 [!DNL Experience Manager]，用户可以搜索和预览资产；复制和发布资产；共享资产 [!DNL Brand Portal];通过 [!DNL Experience Manager] 桌面应用程序；等等。

![搜索Adobe Stock资产并从Adobe Experience Manager工作区中筛选结果](assets/adobe-stock-search-results-workspace.png)

*图：搜索 [!DNL Adobe Stock] 从 [!DNL Experience Manager] 界面。*

**A.**[!DNL Adobe Stock] 搜索与提供 ID 的资产类似的资产。**B.** 搜索与您选择的形状或方向匹配的资产。**C.** 搜索一种或多种受支持的资产类型 **D.** 打开或折叠过滤器窗格 **E.** 在 中授权并保存选定的资产 [!DNL Experience Manager]**F.**[!DNL Experience Manager] 在 中保存带水印的资产 **G.**[!DNL Adobe Stock] 在 网站上浏览与选定资产类似的资产 **H.**[!DNL Adobe Stock] 在 网站上查看选定资产 **I.** 搜索结果中的选定资产数 **J.** 在卡片视图和列表视图之间切换

### 查找资产 {#find-assets}

您的 [!DNL Experience Manager] 用户，可以搜索这两个位置的资产， [!DNL Experience Manager] 和 [!DNL Adobe Stock]. 当搜索位置不限于 [!DNL Adobe Stock]，搜索结果来自 [!DNL Experience Manager] 和 [!DNL Adobe Stock] 中。

* 搜索 [!DNL Adobe Stock] 资产，单击 **[!UICONTROL 导航]** > **[!UICONTROL 资产]** > **[!UICONTROL 搜索Adobe Stock]**.

* 在 [!DNL Adobe Stock] 和 [!DNL Experience Manager Assets]单击搜索 ![search_icon](assets/search_icon.png).

或者，开始键入 `Location: Adobe Stock` ，以选择 [!DNL Adobe Stock] 资产。 [!DNL Experience Manager] 对搜索的资产提供了高级过滤功能，允许用户使用过滤器快速将所需资产插入其中，例如受支持的资产类型、图像方向和许可状态。

>[!NOTE]
>
>搜索的资产来源 [!DNL Adobe Stock] 才显示在 [!DNL Experience Manager]. [!DNL Adobe Stock] 获取资产并将其存储在 [!DNL Experience Manager] 仅在用户 [保存资产](/help/assets/aem-assets-adobe-stock.md#saveassets) 或 [许可证和保存资产](/help/assets/aem-assets-adobe-stock.md#licenseassets). 已存储在 [!DNL Experience Manager] 显示并高亮显示，以便于引用和访问。 此外， [!DNL Stock] 资产会与一些其他元数据一起保存，以将源指示为 [!DNL Stock].

![Experience Manager中的搜索过滤器，并在搜索结果中突出显示Adobe Stock资产](assets/aem-search-filters2.jpg)

*图：在 [!DNL Experience Manager] 突出显示 [!DNL Adobe Stock] 资产。*

### 保存并查看所需的资产 {#saveassets}

选择要保存的资产 [!DNL Experience Manager]. 单击 [!UICONTROL 保存] ，并提供资产的名称和位置。 未授权的资产将在本地保存，并带有水印。

下次搜索资产时，保存的资产会通过徽章突出显示，以指示此类资产在 [!DNL Experience Manager Assets].

>[!NOTE]
>
>最近添加的资产会显示一个“新建”徽章，而不是“授权”徽章。

### 许可资产 {#licenseassets}

用户可以 [!DNL Adobe Stock] 资产(使用 [!DNL Adobe Stock] 企业计划。 在您授权资产时，该资产将不带水印进行保存，并可在中搜索和使用 [!DNL Experience Manager Assets].

![在Experience Manager Assets中授权和保存Adobe Stock资产的对话框](assets/aem-stock_licenseandsave.jpg)

*图：用于授权和保存的对话框 [!DNL Adobe Stock] 资产 [!DNL Experience Manager Assets].*

### 访问元数据和资产属性 {#access-metadata-and-asset-properties}

用户可以访问和预览元数据，包括 [!DNL Adobe Stock] 中保存的资产的元数据属性 [!DNL Experience Manager]，然后添加 **[!UICONTROL 许可证参考]** ，例如 但是，对许可证引用的更新不会在 [!DNL Experience Manager] 和 [!DNL Adobe Stock] 网站。

用户可以查看授权和未授权资产的属性。

![查看和访问已保存资产的元数据和许可证引用](assets/metadata_properties.jpg)

*图：查看和访问已保存资产的元数据和许可证引用。*

## 已知限制 {#known-limitations}

* **未显示编辑图像警告**:授权图像时，用户无法检查图像是否为“仅编辑用途”。 为防止可能的误用，管理员可以从Admin Console中关闭对编辑资产的访问。

* **显示错误的许可证类型**:中可能显示不正确的许可证类型 [!DNL Experience Manager] ，例如 用户可以登录 [!DNL Adobe Stock] 网站查看许可证类型。

* **引用字段和元数据未同步**:当用户更新许可证参考字段时，许可证参考信息在 [!DNL Experience Manager] 但不在 [!DNL Adobe Stock] 网站。 同样，如果用户更新 [!DNL Adobe Stock] 网站，则更新未在 [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [有关使用的视频教程 [!DNL Adobe Stock] 资产 [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html)
>* [[!DNL Adobe Stock] 企业计划帮助](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-stock-enterprise.ug.html)
>* [[!DNL Adobe Stock] 常见问题](https://helpx.adobe.com/stock/faq.html)

