---
title: Experience Manager和Creative Cloud集成最佳实践
description: 将 [!DNL Experience Manager] 部署与Adobe Creative Cloud集成以简化资产传输工作流并实现最高效率的最佳实践
contentOwner: AG
feature: Collaboration,Adobe Asset Link,Desktop App
role: User,Admin
exl-id: cb9bea05-3359-4fb4-b935-59e522a5f387
source-git-commit: 1679bbab6390808a1988cb6fe9b7692c3db31ae4
workflow-type: tm+mt
source-wordcount: '3488'
ht-degree: 16%

---

# [!DNL Experience Manager] 和集 [!DNL Creative Cloud] 成最佳实践 {#aem-and-creative-cloud-integration-best-practices}

<!-- TBD: Reconcile with 6.5 article that's ahead of this article now in terms of content streamlining and structuring.
-->

Adobe Experience Manager Assets是一款数字资产管理(DAM)解决方案，它可以与Adobe Creative Cloud集成，以帮助DAM用户与创意团队合作，从而简化内容创建过程中的协作。

Adobe Creative Cloud为创意团队提供解决方案和服务生态系统，以帮助他们创建数字资产。 它包括桌面和移动应用程序、云服务（如具有桌面同步或Web体验的存储）以及市场(如Adobe Stock)。

请阅读相关内容，以了解根据您的用例在桌面与企业级DAM之间选择哪些集成，以及连接工作流的相关最佳实践。

>[!NOTE]
>
>将文件夹从[!DNL Experience Manager]共享到Creative Cloud已弃用，本指南不再涵盖该内容。 Adobe建议使用较新的功能(如[Adobe资产链接](https://helpx.adobe.com/cn/enterprise/using/adobe-asset-link.html)或[[!DNL Experience Manager] 桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html))，为创意用户提供对[!DNL Experience Manager]中管理的资产的访问权限。

## 创意人员、营销人员和DAM用户的协作需求 {#collaboration-needs-of-creatives-marketers-and-dam-users}

| 要求 | 用例 | 涉及的曲面 |
|---|---|---|
| 简化桌面版创意人员的体验 | 简化从DAM([!DNL Assets])访问资产的流程，供创意专业人士（更广泛地说，是使用本机资产创建应用程序的桌面用户）使用。 他们需要一种简单明了的方式来发现、使用（打开）、编辑和保存对[!DNL Experience Manager]所做的更改，以及上传新文件。 | Win或Mac台式机；Creative Cloud应用程序 |
| 从Adobe Stock提供高质量、可随时使用的资产 | 营销人员通过协助资产采购和发现来帮助加快内容创建流程。 创意专业人士可直接在其创意工具中使用已批准的资产。 | [!DNL Assets];Adobe Stock市场；元数据字段 |
| 按组织分发和共享资产 | 内部部门/地方分支机构和外部合作伙伴、分销商和代理使用由父组织共享的已批准资产。 该组织希望安全、无缝地共享所创建的资产，以便更广泛地重复使用。 | Brand Portal、资产共享共用 |

## Adobe服务以支持协作需求 {#adobe-offerings-to-support-the-collaboration-need}

| 参与角色的价值主张 | Adobe服务 | 涉及的曲面 |
|---|---|---|
| 创意用户从[!DNL Experience Manager]中发现资产，打开并使用资产，编辑资产并将其上传到[!DNL Experience Manager]，以及将新文件上传到[!DNL Experience Manager]，而无需离开Creative Cloud应用程序。 | [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop、Illustrator和InDesign |
| 业务用户可简化资产的打开和使用、编辑和上传对[!DNL Experience Manager]所做的更改，以及从桌面环境将新文件上传到[!DNL Experience Manager]的过程。 它们使用通用集成来打开本机桌面应用程序中的任何资产类型，包括非Adobe资产类型。 | [[!DNL Experience Manager] 桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | [!DNL Experience Manager] Win和Mac桌面版上的桌面应用程序 |
| 营销人员和业务用户从[!DNL Experience Manager]中发现、预览、许可和保存并管理Adobe Stock资产。 授权资产和已保存的资产可提供精选Adobe Stock元数据以更好地管理。 | [Experience Manager和Adobe Stock集成](aem-assets-adobe-stock.md) | [!DNL Experience Manager] web界面 |

本文主要介绍协作需求的前两个方面。作为一个用例，简要提及了资产的大规模分发和采购。对于此类需求解决方案，请考虑 Adobe Brand Portal 或 Asset Share Commons。诸如[Brand Portal](https://helpx.adobe.com/cn/experience-manager/brand-portal/user-guide.html)之类的替代解决方案、可基于[资产共享共用](https://adobe-marketing-cloud.github.io/asset-share-commons/)组件、使用[Experience Manager资产](/help/assets/managing-assets-touch-ui.md)的[链接共享](/help/assets/link-sharing.md)构建的解决方案，应根据特定要求进行审核。

![Creative Cloud连 [!DNL Experience Manager]接：确定要使用的功能](assets/creative-connections-aem.png)

<!-- 
## Terms and definitions {#terms-and-definitions}

The terms used in this document may have a different meaning in other contexts. In particular, the following terms pertaining to the digital asset lifecycle are used when referring to workflows between a creative professional's desktop and DAM:

* **Work-in-progress or creative work-in-progress (WIP):** A phase in asset lifecycle where an asset undergoes multiple changes and is typically not yet ready to be shared with broader teams.
* **Creative-ready assets:** Assets that are ready to be shared with a broader team, or have been  selected / approved  by the creative team for sharing with marketing or LOB teams.
* **Asset approvals:** The approval process that runs for assets already uploaded to DAM, which typically includes brand approvals, legal approvals, and so on.
* **Final asset:** An asset that has gone through all  approvals/metadata  tagging and is ready to be used by the broader team. Such an asset is stored in DAM and made available to all (or all interested) users. It can be used in marketing channels or by creative teams to create designs.
* **Minor asset  update/change:** A quick and small change to a digital asset. It is often made in response to a retouching or minor editing request, asset review, or approval (for example, reposition, change text size, adjust saturation/brightness, color, and so on).
* **Major asset  update/change:** A change to a digital asset that requires considerable work, and sometimes must be done over a longer period of time. It typically includes multiple changes. The asset must be saved multiple times while being updated. Major asset updates typically cause the asset to enter a WIP stage.
* **DAM:** Digital asset management. In this document, it is synonymous with Experience Manager Assets, unless specifically mentioned otherwise.
* **Creative user:** A creative professional, who creates digital assets using Creative Cloud apps and services. In some cases, a creative user may be a member of a creative team who may use Creative Cloud, but does not create digital assets (like a creative director or creative team manager).
* **DAM user:** A typical user of a DAM system. Depending on the organization, a DAM user can be a marketing or a non-marketing user, for example a Line-of-Business (LOB) user, librarian, sales person, and so on.
-->

### 用例映射

| 用例 | [!DNL Experience Manager] 桌面应用程序 | 文件夹共享 | 其他解决方案 |
|---|---|---|---|
| 与创意用户共享较小的(1)个DAM资产 | ✔✔ | ✔ |  |
| 与创意用户共享大量(2)的DAM资产 | ✔✔ | ✘ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [资产共享](assets-finder-editor.md) |
| 与有权访问DAM的用户共享DAM资产 | ✔✔ | ✔ | [链接共享](link-sharing.md) |
| 与无权访问DAM的用户共享DAM资产 | ✘ | ✔✔ | [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) <br> [资产共享](assets-finder-editor.md) |
| 将较小的资产数量/数量保存到DAM | ✔✔ | ✔ | [Web UI上传](managing-assets-touch-ui.md) |
| 将更多资产保存到DAM(3) | ✔✔ | ✘ | [Web UI上](managing-assets-touch-ui.md) <br> 载自定义脚本/工具 |
| 将大量资产迁移到DAM | ✘ | ✘ | [迁移指南](assets-migration-guide.md) |
| 在桌面上快速打开资产 | ✔✔ | ✘ |  |
| 在桌面上快速打开和更改资产 | ✔✔ | ✘ |  |

符号的图例：

* ✔✔:首选解决方案
* ✔:可接受的解决方案
* ✘:不应用于用例

其他注释：

* （一）资产数量较少：例如，与项目或营销策划相关的一小组资产
* （二）资产数量较大：例如，组织中所有已批准的资产
* (3)使用[!DNL Experience Manager]桌面应用程序上载文件夹功能

为了支持资产分发用例，应考虑使用其他解决方案：

* [Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) ，用于可配置的SaaS附加组件， [!DNL Experience Manager] 用于发布资产。
* 自定义解决方案基于[资产共享共用](https://adobe-marketing-cloud.github.io/asset-share-commons/)代码库创建。
* [!DNL Experience Manager] [链接](/help/assets/link-sharing.md) 共享，以使用链接共享临时资产。
* [[!DNL Experience Manager] 资产Web](/help/assets/managing-assets-touch-ui.md) 与外部方的区域交互，这些区域由访问控制 [!DNL Experience Manager] 设置进行保护，并进行必要的IT/网络配置调整，使这些外部用户可以访问 [!DNL Experience Manager]。

## 关键概念和用例 {#key-concepts-and-use-cases}

### 常用术语表 {#glossary-of-common-terms}

* **正在进行的工作或正在进行的创意工作 (WIP)：**&#x200B;资产生命周期中的一个阶段，在此阶段中，资产会经历多次更改，通常尚未准备好与更广的团队共享。
* **创意就绪资产：**&#x200B;已准备好与更广的团队共享的资产，或者已经由创意团队选择/批准与营销或 LOB 团队共享的资产。
* **资产批准：**&#x200B;为已上传到 DAM 的资产运行的批准流程，通常包括品牌批准、法律批准等。
* **最终资产：**&#x200B;已完成所有批准/元数据标记并可供更广的团队使用的资产。此类资产存储在 DAM 中，可供所有（或所有感兴趣的）用户使用。它可用于营销渠道或由创意团队用来创建设计。
* **次要资产更新/更改：**&#x200B;对数字资产进行快速、微小的更改。它通常是响应润饰或次要编辑请求、资产审阅或批准（例如，重新定位、更改文本大小、调整饱和度/亮度、颜色等）而生成的。
* **主要资产更新/更改：**&#x200B;需要大量工作，并且有时必须在较长的一段时间内完成的数字资产更改。它通常包括多项更改。更新资产时必须多次保存。主要资产更新通常会导致资产进入 WIP 阶段。
* **DAM：**&#x200B;数字资产管理。在本文档中，除非另有特别说明，否则与[!DNL Experience Manager Assets]同义。
* **创意用户：**&#x200B;使用 Creative Cloud 应用程序和服务创建数字资产的创意专业人士。在某些情况下，创意用户可能是使用 Creative Cloud 但不创建数字资产的创意团队成员（如创意总监或创意团队经理）。
* **DAM 用户：** DAM 系统的典型用户。根据组织的不同，DAM 用户可以是营销或非营销用户，例如业务线 (LOB) 用户、管理员、销售人员等。

### 使用[!DNL Experience Manager]和Creative Cloud集成时的注意事项 {#considerations-when-using-aem-and-creative-cloud-integration}

* 请参阅[桌面应用程序最佳实践](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/troubleshoot.html#best-practices-to-prevent-troubles)
* 请参阅[Adobe Stock集成](aem-assets-adobe-stock.md)
* 请参阅[Adobe资产链接](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html)

以下是Experience Manager和Creative Cloud集成最佳实践的简短摘要。 阅读本文档的其余部分，以详细了解这些内容。

* **对于使用 Photoshop、InDesign 或 Illustrator 的创意用户：** Adobe Asset Link 提供了最佳用户体验，包括清晰处理从 中签出的正在进行的资产[!DNL Experience Manager]
* **简化从桌面访问任何通用文件格式或应用程序资产的操作：**[!DNL Experience Manager]请使用 桌面应用程序
* **了解在 DAM 中存储资产的原因和时间：**&#x200B;将提供给组织中更广泛团队的更新
* **关注共享的资产数量：**&#x200B;如果您的用例是资产分发，则管理和安全可能是最重要的方面。考虑使用为大规模操作而构建的工具，如 Brand Portal。
* **了解资产生命周期：**&#x200B;了解组织中不同团队处理资产的方式
* **谨慎处理对资产的频繁保存：** Adobe Asset Link 通过 PS、AI、ID 为您提供相关服务。对于其他应用程序，除非您需要在 DAM 中完成所有更改，否则不要在映射/共享文件夹中执行正在进行的任务

### 从[!DNL Assets]访问Adobe Stock资产 {#access-to-adobe-stock-assets-from-aem-assets}

[[!DNL Experience Manager] 和Adobe Stock](/help/assets/aem-assets-adobe-stock.md) 集成 [!DNL Experience Manager] 使用户能够从Adobe Stock中搜索、预览、许可和保存资产，并将资产保存到 [!DNL Experience Manager]中。授权和保存的Adobe Stock资产已选择Stock元数据，该元数据可用于使用额外的过滤器搜索它们。

有关此集成的几个重要要点：

* 将Adobe库中的资产保存到[!DNL Experience Manager]后，这些资产将变成常规的[!DNL Experience Manager]资产，并将二进制文件保存到[!DNL Experience Manager]存储库。 在[!DNL Experience Manager]中为资产保存了一些与Adobe Stock相关的元数据，否则，摄取过程与任何其他文件的过程相同。 例如，如果智能标记处于活动状态，则会在保存时将标记添加到这些资产中。
* 保存到[!DNL Experience Manager]的资产是副本，而不是返回到Adobe Stock的链接。

**在Adobe Stock中处理从保存到 [!DNL Experience Manager] 的Creative Cloud**。此集成与Adobe资产链接无关，但Adobe资产链接可以这样识别从Stock中保存的这些资产，并在Photoshop、Illustrator或InDesign的Adobe资产链接扩展UI中，在这些资产上显示其他元数据和Stock图标。 这些文件可用于浏览、打开等 — 因为它们在保存到[!DNL Experience Manager]时是常规的[!DNL Experience Manager]资产。
使用具有Adobe资产链接扩展的Creative Cloud应用程序的创意用户除了能够从Adobe Stock访问[!DNL Experience Manager]中已授权的资产外，还可以使用Creative Cloud库面板来搜索、预览和许可Adobe Stock资产。
从Adobe Stock获得授权并保存到[!DNL Experience Manager]中的资产可供访问[!DNL Experience Manager]资产部署的更广泛的团队使用，而从Adobe Stock通过“Creative Cloud库”面板获得授权的创意人员只能在其Creative Cloud帐户中默认自行使用。

<!-- 
TBD: A condensed version of the below content is better placed in the Adobe DAM article.
-->

## 关于在DAM中存储资产 {#about-storing-assets-in-a-dam}

要在创意团队和营销/业务线(LOB)团队之间设计一个高效的工作流并选择最佳支持功能，请务必了解资产何时以及为何存储在DAM中。

### 资产为何存储在DAM中 {#why-assets-are-stored-in-dam}

将资产存储在DAM中，可轻松访问和查找资产。 它可确保组织或生态系统（包括合作伙伴、客户等）中的众多用户都能够利用资产。

大多数组织选择仅存储与下游营销/LOB流程相关的资产(通过[!DNL Experience Manager]站点或由Adobe Experience Cloud、Advertising Cloud提供并由Analytics Cloud测量的其他渠道（提供给用户/合作伙伴等）发布到Web渠道等渠道。 此外，组织会在DAM中存储可能需要审核/批准流程的资产。 这样，DAM存储的资产大多数是极有可能被利用的资产，并避免存储闲置资产。

存储资产还需要考虑技术和资源利用方面的考虑因素。 DAM提供了有关存储资产的其他服务，包括提取元数据、版本控制、生成预览/转码、管理引用和添加访问控制信息。 这些服务需要额外的时间和基础架构资源。

通常，存储所有资产和更新是不可取的。 例如，如果对特定资产的更新质量不佳，并且消耗了过多的资源，则资产可能不会存储在DAM中。

### 资产存储在DAM中时 {#when-assets-are-stored-in-dam}

创意团队（和组织）通常对在资产生命周期的每个阶段存储资产不感兴趣。 例如，在以下情况下，它们会避免存储资产：

* 尚未完成或有待试验的资产
* 未能通过创意/内部团队审阅周期的资产
* 与相关资产相比，团队有更好的候选人来向外部团队展示其工作

通常，以下类资产存储在DAM中：

* 已达到特定期限且被视为可共享的资产
* 创意团队预先选择的资产
* 根据特定合同或协议（例如，从RAW文件转换的JPG文件、PSD原始文件的TIFF/图像），由营销部门使用或请求的特定资产格式

### 资产更新存储在DAM中时 {#when-updates-to-assets-are-stored-in-dam}

作为规则，只应将与更广泛的DAM用户集相关的资产更新存储在DAM中。 它可确保用户（营销和类似功能）在DAM资产时间轴中仅看到相关版本。

通常与资产生命周期中的主要里程碑相关的更改。 例如，创意团队提供的初始创意就绪资产或基于请求/审阅的官方更新应存储在DAM中并进行版本控制。

创意团队在请求更改DAM中的现有资产后进行的更新（供营销团队审阅）便是相关更新的一个示例。 它应存储在DAM中并进行版本控制，以供进一步引用或还原到之前的版本。

以下是一些通常与之无关的更新示例：

* 在准备好进行营销审核之前，已上传资产的早期版本
* 在创作团队确定资产已准备就绪之前，在进行中的阶段中经常对资产进行创意更改

### 用户对DAM的访问权限 {#user-access-to-dam}

[!DNL Experience Manager] 资产根据用户对资产部署的访问权限，支持两种 [!DNL Experience Manager] 类型的用户。通常，企业网络（防火墙）内的用户可以直接访问DAM。 企业网络外的其他用户将无法直接访问。 用户类型从技术角度决定可以使用哪些集成。

#### 直接访问DAM的创意用户 {#creative-users-with-direct-access-to-dam}

通常，已载入内部网络的内部创意团队或代理/创意专业人士有权访问DAM实例，包括[!DNL Experience Manager]登录。

在这种情况下，[!DNL Experience Manager]桌面应用程序有助于您轻松访问最终/已批准的资产，并允许您将创意就绪资产保存到DAM。

#### 无权访问DAM的创意用户 {#creative-users-without-access-to-dam}

无法直接访问DAM实例的外部代理和自由职业者可能需要访问已批准的资产或希望将其新设计添加到DAM。

在这种情况下，您可以利用[!DNL Experience Manager]/Creative Cloud集成来改进工作流。 先决条件是创意用户拥有Adobe ID，并拥有具有存储服务的Creative Cloud帐户。

使用以下策略提供对最终/已批准资产的访问权限：

* 要提供对大量资产的访问，请执行以下操作：使用[[!DNL Experience Manager] Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html)，或客户在[!DNL Experience Manager]发布基础架构上实施[资产共享](assets-finder-editor.md)

* 要提供对一些资产的访问，请执行以下操作：与Adobe Creative Cloud共享的[!DNL Experience Manager]文件夹可以用于[!DNL Experience Manager] Assets Brand Portal或资产共享之外。 请注意，此集成存在某些限制，本文将详细介绍这些限制。

### 用例 {#use-cases}

以下用例描述了DAM与设计人员桌面之间的各种工作流类型。

#### 使用DAM中的资产创建新设计 {#creating-new-designs-using-assets-from-dam}

下图说明了数字资产生命周期。 它描述了创意用户和DAM用户（营销人员、LOB用户）如何利用现有资产，并使用这些资产创建更多资产，并发送这些资产以供审批。

![chlimage_1-301](assets/chlimage_1-301.png)

资产生命周期包括以下阶段：

1. 将批准的资产共享到Creative Desktop:创意用户（在桌面上）可以使用DAM中的最终资产
1. 创建新设计（创意数字资产）：新文件将存储在正在进行的工作(WIP)区域中。
1. 在新设计中使用（放置）已批准的资产：创意用户使用Creative Cloud应用程序中的现有已批准资产生成新资产
1. 频繁保存WIP更新：创意用户快速迭代并频繁保存文件。 在此阶段，创意用户可能会与他人协作，但经常保存的更新通常对DAM用户不感兴趣。
1. 资产会达到创作就绪状态，并保存到创作就绪文件夹
1. 资产更新：DAM中的用户可以使用资产更新或新文件
1. 资产投入生产：这是一个DAM流程，具体取决于组织，可能包括标记、批准和更改访问控制。 在此阶段，资产被视为最终资产，能否由利用DAM的更广的团队使用。 创意用户也可以使用它创建其他资产。

以下是关于如何通过此过程管理资产的一些一般建议：

* 对WIP文件使用专用存储区/系统(如Adobe Creative Cloud Assets同步文件夹):与DAM用户无关的频繁更新最好由专用系统处理，而不是从[!DNL Experience Manager]资产内处理。 可以使用Adobe Creative Cloud桌面应用程序将WIP资产同步到本地磁盘，并保存在本地存储上，等等。
* 对上传到DAM的最终资产和资产使用单独的文件夹/共享：为清楚起见，最终资产应具有自己的映射/共享文件夹（上面的“最终”示例），并且要上传回DAM的资产应具有自己的（“创意就绪”）

#### 更改DAM中管理的现有资产 {#changing-existing-assets-managed-in-dam}

在某些情况下，DAM中的资产可能需要进行更改。 示例包括：

* 在[!DNL Experience Manager]资产中完成审核和批准后，请求更改资产
* 对现有最终资产进行的重大更新
* 对现有文件进行快速编辑（尤其是在最终批准之前）

在这种情况下，[!DNL Experience Manager]桌面应用程序是执行这些操作的最简单方法。

![chlimage_1-302](assets/chlimage_1-302.png)

下图描述了事件的流程：

<!-- TBD for formatting. 
This article will get fixed automatically when 6.5 content is ported to it.
And 6.5 content will be ported after updating it for [!DNL Experience Manager] desktop app 2.0 best practices.
And it will be updated for DA2.0 best practices after 6.5 repo is available for writers to edit content in.
-->

* **1:** 将资产从DAM共享到桌面，或在选择的应用程序(例如，Adobe Photoshop等)中直接在桌面上打开资产。建议检出以锁定文件。
* **2:** 次要更新：编辑文件并保存更改。
* 步骤2的替代流程

   * **答：** 主要更新：如果文件需要精心设计的一组更改，则应间歇性地保存该文件，并将其复制到WIP文件夹/区域。
   * **B:** 继续处理WIP文件夹中的文件。保存的更改未同步到DAM中的版本
   * **C:** 更新完成后，文件将被复制回或保存到映射的文件夹

* **3:** 资产更新反映在DAM中。签入资产以解锁资产。
* **4:** 资产投入生产。

以下是关于如何在整个过程中管理资产的一些一般建议：

* 请避免直接保存您从由[!DNL Experience Manager]桌面应用程序映射的网络共享中打开的文件，除非您对该文件所做的更改很小。
* 如果要对文件进行其他更改、间歇性保存或与创意团队协作，请将文件复制到单独的WIP文件夹。

#### 批量上传到DAM {#bulk-upload-to-dam}

在某些情况下，您可能需要同时将大量文件上传到DAM，例如：

* 上传照片或大型项目的结果
* 上传由创意代理提供的资产
* 如果选择在DAM之外完成，则从较大的集上传选定资产

请注意，此描述是指在桌面用户工作流程中正常部分上传文件（例如，每周或每张照片，等等）。 此处未介绍大型资产迁移。

如果要批量上传资产，您可以利用以下功能：

* 要上传大型/分层文件夹，请使用[!DNL Experience Manager]桌面应用程序，该应用程序提供了[文件夹上传](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload)功能。 您还可以上传分层文件夹结构。 资产是在后台上传的，因此不会将其绑定到Web浏览器会话
* 如果要从单个文件夹上传几个文件，请直接将它们从桌面拖到Web UI，或使用[!DNL Experience Manager] Assets Web UI中的创建选项。

>[!NOTE]
>
>根据您的业务要求，您还可以使用自定义Uploader。

#### 直接从桌面管理数字资产 {#managing-digital-assets-directly-from-desktop}

如果您使用“网络文件共享”管理数字资产，则只需使用由[!DNL Experience Manager]桌面应用程序映射的网络共享即可被视为一种便捷的替代方法。 从网络文件共享进行转换时，请记住，[!DNL Experience Manager] Web UI提供了丰富的数字资产管理功能集，远远超出了网络共享上的可能功能（搜索、收藏集、元数据、协作、预览等），而[!DNL Experience Manager]桌面应用程序提供了一个方便的链接，用于将服务器端DAM存储库与桌面上的工作连接起来。

避免使用[!DNL Experience Manager]桌面应用程序直接在[!DNL Experience Manager]资产的网络共享中管理资产。 例如，请避免使用[!DNL Experience Manager]桌面应用程序移动/复制多个文件。 请改用[!DNL Experience Manager]资产Web UI将文件夹从Finder/Explorer拖到网络共享，或使用[!DNL Experience Manager]资产文件夹上传功能。

#### 资产迁移 {#asset-migration}

要规划和执行从现有系统到新系统的资产迁移，或迁移存储在服务器上的大量资产，请参阅[迁移指南](/help/assets/assets-migration-guide.md)。 [!DNL Experience Manager] 桌面应用程 [!DNL Experience Manager] 序和Creative Cloud集成不支持此类迁移。由于要摄取的资产量很大，并且对元数据映射、转换和摄取有其他要求，因此迁移应使用不同的工具和方法来处理。

>[!MORELIKETHIS]
>
>* [Adobe资产链接](https://helpx.adobe.com/in/enterprise/admin-guide.html/in/enterprise/using/adobe-asset-link.ug.html)
>* [[!DNL Experience Manager] 桌面应用程序最佳实践](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/archive/best-practices-for-v1.html)
>* [[!DNL Experience Manager] Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
>* [[!DNL Experience Manager] 和Adobe Stock集成](aem-assets-adobe-stock.md)

