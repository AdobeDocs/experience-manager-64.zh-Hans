---
title: 使用AEM管理资产的最佳实践
description: 根据 [!DNL Experience Manager] Assets部署以及用于摄取和处理资产的功能，确定并遵循可在负载下增强系统稳定性和性能的最佳实践。
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# [!DNL Experience Manager]资产的最佳实践 {#best-practices-for-assets}

Adobe Experience Manager Assets是提供高质量数字营销体验的关键部分，通过提高内容周转率，为实现业务目标做出贡献。 如果您在[!DNL Assets]内处理大量资产，或定期/定期上传大量资产（包括视频和Dynamic Media），那么优化数字资产管理体验对于提高系统效率至关重要。

根据您为组织定位[!DNL Assets]的方式以及您在资产摄取、呈现版本生成和元数据提取方面使用的功能，识别并遵循不同区域的最佳实践会极大地增强负载下的系统稳定性和性能。

在查看以下指南后，您将拥有构建和管理符合您需求的企业资产管理系统所需的知识和工具。

* [资产性能](performance-tuning-guidelines.md)
调整指南包括一套最佳实践，您可以在实施的任何时间点（即使在上线后）遵循这些最佳实践，以确保您能够充分利用系统。
* [资产大](assets-sizing-guide.md)
小调整指南在编制资产实施的估计值时，必须确保在资产存储、CPU、内存、IO和网络吞吐量方面有足够的可用资源。调整其中许多项目的大小需要了解系统中加载的资产数量。 本指南包含一些最佳实践，可帮助确定用于评估[!DNL Experience Manager]资产部署所需的基础架构和资源的有效量度，以及大小调整工具。
* [资产迁](assets-migration-guide.md)
移指南如果您要将资产从旧版系统迁移 [!DNL Experience Manager] 到资产，可考虑以下几个步骤来简化迁移过程。迁移指南包含有关您执行的任务的最佳实践，以逐步将资产引入[!DNL Experience Manager]中。 这包括应用元数据、生成演绎版，以及激活资产以发布部署。
* [资产网络](assets-network-considerations.md)
注意事 [!DNL Experience Manager] 项在处理部署时，了解网络拓扑对于了解网络性能、识别选择点和描述预期用户体验至关重要。资产网络注意事项文档讨论了设计[!DNL Experience Manager]资产部署时的网络注意事项。
* [资产监](assets-monitoring-best-practices.md)
控指南 [!DNL Experience Manager] 部署后，您应当监控某些任务和系统的总体情况，以确保系统完整性和操作效率。监控指南包含监控系统各个方面的最佳实践。
* （已弃用）[资产卸载指南](assets-offloading-best-practices.md)
在[!DNL Experience Manager]资产中处理大型文件和运行工作流可能会占用大量CPU、内存和I/O资源。 卸载这些任务可以减少CPU、内存和IO开销。 资产卸载指南包含资产卸载的推荐用例和最佳实践。
* [[!DNL Experience Manager] 桌面应用程序最佳实践](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] 桌面应用程序将您的数字资产管理(DAM)解决方案与桌面链接在一起，这样您就可以直接在桌面上打开Web UI [!DNL Experience Manager] 中可用的文件。[!DNL Experience Manager] 桌面应用程序的易于使用的工作流程通过使用桌面操作系统提供的网络共享技术来实现。本指南介绍了[!DNL Experience Manager]桌面应用程序的关键功能和建议使用。
* [[!DNL Experience Manager] 和Creative Cloud集成最](aem-cc-integration-best-practices.md)
佳实践您可以通过多 [!DNL Experience Manager] 种方式将部署与Creative Cloud集成。遵循一些最佳实践来简化集成和资产传输工作流，有助于实现最高效率。 本指南包含有关将[!DNL Experience Manager]资产与Adobe Creative Cloud集成的最佳实践。
* （已弃用）[[!DNL Experience Manager] 用于Creative Cloud共享最佳实践的文件夹](aem-cc-folder-sharing-best-practices.md)
您可以配置[!DNL Experience Manager] ，以允许DAM中的用户与Creative Cloud(CC)用户共享文件夹，以便他们在Creative Cloud资产服务中可以作为共享文件夹使用。 该功能可用于在创意团队和DAM用户之间交换文件。 本指南介绍了利用[!DNL Experience Manager]Creative Cloud文件夹共享功能的最佳实践。
