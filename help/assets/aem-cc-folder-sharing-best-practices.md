---
title: 将Experience Manager Assets文件夹与Creative Cloud共享
description: 允许Adobe Experience Manager Assets用户与Adobe Creative Cloud用户交换资产文件夹的配置和最佳实践。
contentOwner: AG
feature: Collaboration
role: User,Admin
exl-id: 7e2adfcc-410d-4574-8f7e-39aceecfdd4b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# [!DNL Experience Manager] to [!DNL Creative Cloud] 文件夹共享最佳实践 {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>“Experience Manager到Creative Cloud文件夹共享”功能已弃用。 Adobe强烈建议使用较新的功能，例如 [Adobe资产链接](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) 或 [Experience Manager桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). 在 [Experience Manager和Creative Cloud集成最佳实践](/help/assets/aem-cc-integration-best-practices.md).

可以将Adobe Experience Manager配置为允许Experience Manager Assets中的用户与Creative Cloud用户共享文件夹，以便他们可以在Creative Cloud资产服务中作为共享文件夹使用。 该功能可用于在创意团队和Experience Manager Assets用户之间交换文件，尤其是当创意用户无权访问Experience Manager Assets实例（他们不在企业网络上）时。

此类集成可在两种用例中使用，尤其是在与没有直接访问Experience Manager Assets的用户合作时：

* 与“Creative Cloud文件”用户共享Experience Manager Assets中的一组特定资产（例如，创作摘要和一组已批准的资产，用于新营销活动的设计工作）
* 从Creative Cloud用户接收新文件。

>[!NOTE]
>
>在阅读本文档之前，您可以查看 [Experience Manager和Creative Cloud集成最佳实践](aem-cc-integration-best-practices.md) ，以获取主题的更高级概述。

## 概述 {#overview}

Experience Manager到Creative Cloud文件夹的共享依赖于Experience Manager Assets和Creative Cloud帐户之间在服务器端共享文件夹和文件。 在台式机上使用Creative Cloud桌面应用程序的创意专业人士，还可以使用Adobe CreativeSync技术在其磁盘上直接提供共享文件夹。

下图提供了集成的概述。

![chlimage_1-406](assets/chlimage_1-406.png)

该集成包含以下元素：

* **[!DNL Assets]服务器** 部署在企业网络（托管服务或内部部署）中：在此处启动文件夹共享。
* **Adobe Marketing Cloud Assets核心服务**:充当Experience Manager和Creative Cloud存储服务之间的中介。 使用集成的公司管理员需要在Marketing Cloud组织与Experience Manager Assets实例之间建立信任关系。 此外， [定义已批准的Creative Cloud协作者列表](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html#assets)，资产用户也可以共享文件夹以提高安全性。
* **Creative Cloud资产Web服务** (存储和Creative Cloud文件Web UI):在这里，与其共享了Creative Cloud文件夹的特定Creative Cloud用户将能够接受邀请，并在其资产帐户存储中查看文件夹。
* **Creative Cloud桌面应用程序**:（可选）允许通过与Creative Cloud资产存储同步，从创意用户的桌面直接访问共享文件夹/文件。

## 特征和限制 {#characteristics-and-limitations}

* **更改的单向传播：** 文件更改仅会沿一个方向传播 — 从最初创建（上传）Experience Manager的系统(Creative Cloud或资产)传播。 该集成不会在两个系统之间提供完全自动的双向同步。

* **版本控制:**

   * Experience Manager仅在更新时创建Experience Manager版本（如果文件源于资产，并且在该资产中进行了更新）。
   * Creative Cloud资产提供自己的 [版本控制功能](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html) 定位在进行中的更新（基本上，可将更新存储长达10天）

* **空间限制：** 交换的文件的大小和数量受特定 [Creative Cloud资产配额](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) 对于创意用户（取决于订阅级别），最大文件大小限制为5GB。 此外，组织在Adobe Marketing Cloud Assets核心服务中的资产配额也会限制空间。

* **空间要求：** 共享文件夹中的文件还需要物理存储在Experience Manager中，然后存储在Creative Cloud帐户中，并在Marketing Cloud资产核心服务中缓存副本。
* **网络和带宽：** 共享文件夹中的文件和所有更新需要通过网络在系统之间传输。 您应确保仅共享相关文件和更新。
* **文件夹类型**:共享类型的Assets文件夹 `sling:OrderedFolder`，不受支持。 如果要共享文件夹，则在Experience Manager Assets中创建文件夹时，请勿选择“已排序”选项。

## 最佳实践 {#best-practices}

利用Experience Manager进行Creative Cloud文件夹共享的最佳实践包括：

* **卷注意事项：** Experience Manager时，应使用“Creative Cloud文件夹共享”来共享较少数量的文件，例如，与特定营销活动或活动相关的文件。 要共享较大的资产集（与组织中所有已批准的资产一样），请使用其他分发方法(例如，Experience Manager Assets Brand Portal)或Experience Manager桌面应用程序。
* **避免共享深层次：** 按照递归方式进行共享，不允许选择性取消共享。 通常，只应考虑共享没有子文件夹或层次结构非常浅（如1个子文件夹级别）的文件夹。
* **单向共享的单独文件夹：** 应使用单独的文件夹将最终资产从Experience Manager Assets共享到Creative Cloud文件，以及将创意就绪资产从Creative Cloud文件共享回 [!DNL Assets]. 除了为这些文件夹制定了良好的命名规范外，它还为Experience Manager Assets和Creative Cloud用户创建了一个更易于理解的工作环境。
* **避免在共享文件夹中出现WIP:** 不应将共享文件夹用于进行中的工作 — 在Creative Cloud文件中使用单独的文件夹来执行需要频繁更改文件的工作。
* **在共享文件夹之外开始新工作：** 新设计（创作文件）应在Creative Cloud文件的单独WIP文件夹中启动，当它们准备好与Experience Manager Assets用户共享时，应将它们移动或保存到共享文件夹。
* **简化共享结构：** 要建立更易于管理的操作集，请考虑简化共享结构。 Experience Manager Assets文件夹不应与所有创意用户共享，而应仅与团队代表共享，如创意总监或团队经理。 创意方面的经理将接收最终资产，决定工作分配，然后让设计人员在自己的Creative Cloud帐户中处理WIP资产。 他们可以使用Creative Cloud协作功能来协调工作，最后选择已准备好共享回Experience Manager Assets的资产并将其放入其可供创意使用的共享文件夹。

下图展示了一个示例配置，用于根据Experience Manager Assets中的现有最终资产创建新设计。

![chlimage_1-407](assets/chlimage_1-407.png)
