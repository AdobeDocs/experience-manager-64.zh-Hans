---
title: 使用Creative Cloud共享AEM Assets文件夹
description: 允许Adobe Experience Manager Assets用户与Adobe Creative Cloud用户交换资产文件夹的配置和最佳实践。
contentOwner: AG
translation-type: tm+mt
source-git-commit: e64f5b0e1333d511eaf450072756a95399e838d0
workflow-type: tm+mt
source-wordcount: '1061'
ht-degree: 0%

---


# AEM到Creative Cloud文件夹，共享最佳实践{#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>已弃用AEM到Creative Cloud文件夹共享功能。 Adobe强烈建议使用较新的功能，如[Adobe资产链接](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html)或[AEM桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)。 了解有关[AEM和Creative Cloud集成最佳实践的更多信息](/help/assets/aem-cc-integration-best-practices.md)。

Adobe Experience Manager(AEM)可以配置为允许AEM Assets中的用户与Creative Cloud用户共享文件夹，这样，在Creative Cloud资产服务中，这些用户就可以作为共享文件夹。 该功能可用于在创意团队和AEM Assets用户之间交换文件，尤其是当创意用户无权访问AEM Assets实例（他们不在企业网络上）时。

这类集成可用于两种用例，特别是与没有直接访问AEM Assets的用户合作时：

* 与Creative Cloud文件用户共享AEM Assets中的一组特定资产(例如，用于为新营销活动设计工作的创意简介和一组获准资产)
* 从Creative Cloud用户接收新文件。

>[!NOTE]
>
>在阅读此文档之前，您可以查阅整体[AEM和Creative Cloud集成最佳实践](aem-cc-integration-best-practices.md)，以获得主题的更高级别概述。

## 概述 {#overview}

AEM到Creative Cloud的文件夹共享依赖于AEM Assets和Creative Cloud帐户之间的文件夹和文件的服务器端共享。 在桌面上使用Creative Cloud桌面应用程序的创意专业人士还可以使用Adobe CreativeSync技术将共享文件夹直接放在其磁盘上。

下图提供了集成的概述。

![chlimage_1-406](assets/chlimage_1-406.png)

该集成包含以下元素：

* **AEM Assets** server部署在企业网络（托管服务或内部部署）中：在此处启动文件夹共享。
* **Adobe Marketing Cloud Assets核心服务**:充当AEM和Creative Cloud存储服务之间的中介。使用集成的公司的管理员需要在Marketing Cloud组织与AEM Assets实例之间建立信任关系。 它们还[定义了已批准的Creative Cloud协作者](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html?lang=en#assets)的列表,AEM Assets用户也可以共享文件夹，以增强安全性。
* **Creative Cloud资产Web服务** (存储和Creative Cloud文件Web UI):在这里，与其共享了AEM Assets文件夹的特定Creative Cloud用户可以接受邀请并在其Creative Cloud帐户存储中查看该文件夹。
* **Creative Cloud桌面应用程序**:（可选）允许通过与Creative Cloud Assets存储同步，从创意用户的桌面直接访问共享文件夹/文件。

## 特性和限制{#characteristics-and-limitations}

* **更改的单向传播：文** 件更改仅单向传播 — 从最初创建（上传）资产的系统(AEM或Creative Cloud资产)。该集成不提供两个系统之间完全自动的双向同步。

* **版本控制:**

   * AEM仅在文件源自AEM且在中进行更新时，才会在更新时创建资产的版本。
   * Creative Cloud Assets提供其自己的[版本控制功能](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html)，该功能针对Work in Progress更新（基本上，将更新存储10天）

* **空间限制：** 交换的文件大小和数量受特定Creative Cloud资 [产配额](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) (取决于订阅级别)的限制，最大文件大小限制为5GB。此外，组织在Adobe Marketing Cloud Assets核心服务中拥有的资产配额也限制了空间。

* **空间要求：** 共享文件夹中的文件还需要物理存储在AEM中，然后存储在Creative Cloud帐户中，并在Marketing Cloud Assets核心服务中缓存一个副本。
* **网络和带宽：** 共享文件夹中的文件和所有更新需要通过网络在系统之间传输。您应确保仅共享相关文件和更新。
* **文件夹类型**:不支持共享类型 `sling:OrderedFolder`的“资产”文件夹。如果要共享文件夹，则在AEM Assets中创建文件夹时，请勿选择“已排序”选项。

## 最佳实践{#best-practices}

将AEM用于Creative Cloud文件夹共享的最佳实践包括：

* **卷注意事** 项：应使用AEM/Creative Cloud文件夹共享来共享较少数量的文件，例如，与特定活动或活动相关的文件。要共享较大的资产集（与组织中所有已批准的资产一样），请使用其他分发方法(例如AEM Assets Brand Portal)或AEM桌面应用程序。
* **避免共享深层次结构：** 共享以递归方式工作，不允许选择性取消共享。通常，只有没有子文件夹或层次结构非常浅的文件夹（如1个子文件夹级别）才应考虑进行共享。
* **单向共享的单独文件夹：应** 使用单独的文件夹将最终资产从AEM Assets共享到Creative Cloud文件，将创意就绪型资产从Creative Cloud文件共享回AEM Assets。除了为这些文件夹制定了良好的命名规范外，它还为AEM Assets和Creative Cloud用户创建了一个更易于理解的工作环境。
* **在共享文件夹中避免** WIP：不应将共享文件夹用于进行中工作 — 在Creative Cloud文件中使用单独的文件夹来执行需要频繁更改文件的工作。
* **开始共享文件夹之外的新** 工作：新设计（创作文件）应在Creative Cloud文件中的单独WIP文件夹中启动，当它们准备好与AEM Assets用户共享时，应将它们移动或保存到共享文件夹。
* **简化共享结构：** 要实现更易于管理的操作设置，请考虑简化共享结构。AEM Assets文件夹应仅与团队代表共享，而不是与所有创意用户共享，就像创意总监或团队经理一样。 创意部门的经理将接收最终资产，决定工作分配，然后让设计人员在自己的Creative Cloud帐户中处理WIP资产。 他们可以使用Creative Cloud协作功能来协调工作，最后选择并放置准备好共享回AEM Assets的资源到他们的创意就绪共享文件夹。

下图说明了一个根据AEM Assets现有最终资产创建新设计的示例配置。

![chlimage_1-407](assets/chlimage_1-407.png)
