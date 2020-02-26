---
title: 使用AEM管理资产的最佳实践
description: 根据AEM资产部署以及用于摄取和处理资产的功能，确定并遵循可提高系统在负载下的稳定性和性能的最佳实践。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e

---


# Best practices for AEM Assets {#best-practices-for-assets}

Adobe Experience Manager(AEM)资产是提供高质量数字营销体验的关键部分，通过提高内容速度，这些体验有助于实现业务目标。 如果您在AEM资产中处理大量资产，或定期／定期上传大量资产（包括视频和动态媒体），则优化数字资产管理体验对于提高系统效率至关重要。

根据您为组织定位AEM资产的方式以及您围绕资产摄取、演绎版生成和元数据提取使用的功能，识别并遵循不同区域的最佳实践可以极大地增强加载情况下的系统稳定性和性能。

查看以下指南后，您将拥有构建和管理满足您需求的企业资产管理系统的知识和工具。

* [资产性能调整指南](performance-tuning-guidelines.md)-包括一套最佳实践，可在实施过程中的任何时间点（即使在您上线后）遵循这些实践，以确保您充分利用系统。
* [资产大小调整指南](assets-sizing-guide.md)：在为资产实施制定估计时，务必确保在资产存储、CPU、内存、IO和网络吞吐量方面有足够的可用资源。 调整其中许多项目的大小需要了解要加载到系统中的资产数量。 本指南包含最佳实践，可帮助确定用于评估AEM资产部署所需的基础架构和资源的有效指标以及规模调整工具。
* [资产迁移指](assets-migration-guide.md)南如果您要将资产从旧版系统迁移到AEM资产，可以考虑几个步骤来简化迁移过程。 迁移指南包含有关您执行的任务的最佳实践，以逐步将资产引入AEM。 这包括应用元数据、生成演绎版以及激活资产以进行发布部署。
* [资产网络注意事](assets-network-considerations.md)项在处理AEM部署时，了解网络拓扑对于了解网络性能、识别选择点和描述预期的用户体验至关重要。 “资产网络注意事项”文档讨论了设计AEM资产部署时的网络注意事项。
* [资产监视指](assets-monitoring-best-practices.md)南部署AEM部署后，您应当监视某些任务和系统的总体情况，以确保系统完整性和操作效率。 “监视”指南包括监控系统各个方面的最佳实践。
* （已弃用）资 [产卸载指南](assets-offloading-best-practices.md)AEM资产中处理大文件和运行工作流可能会占用大量CPU、内存和I/O资源。 卸载这些任务可减少CPU、内存和IO开销。 资产分载指南包含资产分载的推荐使用案例和最佳实践。
* [AEM桌面应用程序最佳实践](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)AEM桌面应用程序将您的数字资产管理(DAM)解决方案与您的桌面关联，因此您可以直接在桌面上打开AEM Web UI中提供的文件。 AEM桌面应用程序的简单易用的工作流程是使用桌面操作系统提供的网络共享技术实现的。 本指南介绍AEM桌面应用程序的主要功能和建议使用。
* [AEM和Creative cloud集成最佳实践](aem-cc-integration-best-practices.md)-您可以通过多种方式将AEM部署与Creative cloud集成。 遵循一些最佳实践以简化集成和资产转让工作流程，有助于实现最高效率。 本指南包括有关将AEM资产与Adobe Creative cloud集成的最佳实践。
* （已弃用） [AEM到Creative cloud文件夹，共享最佳实践](aem-cc-folder-sharing-best-practices.md)您可以配置AEM，以允许DAM中的用户与Creative Cloud(CC)用户共享文件夹，以便在Creative Cloud资产服务中将它们作为共享文件夹使用。 该功能可用于在创意团队和DAM用户之间交换文件。 本指南介绍了将AEM用于Creative cloud文件夹共享功能的最佳实践。
