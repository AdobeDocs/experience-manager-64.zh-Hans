---
title: 使用AEM管理资产的最佳实践
description: 根据AEM Assets部署以及用于采集和处理资产的功能，确定并遵循在负载下增强系统稳定性和性能的最佳实践。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0e0e2aa693c30c8e1ef1033b936b82d83e5b348e
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Best practices for AEM Assets {#best-practices-for-assets}

Adobe Experience Manager(AEM)资产是提供高质量数字营销体验的关键部分，通过提高内容速度，为实现业务目标做出贡献。 如果您在AEM Assets内处理大量资产或定期／定期上传大量资产（包括视频和动态媒体），则优化数字资产管理体验对于系统效率至关重要。

根据您为组织定位AEM Assets的方式以及围绕资产摄取、再现生成和元数据提取使用的功能，识别并遵循不同领域的最佳实践会在负载下极大地增强系统稳定性和性能。

查看以下指南后，您将拥有构建和管理满足您需求的企业资产管理系统的知识和工具。

* [资产性能调整](performance-tuning-guidelines.md)指南包括一套最佳实践，可在实施中的任何时间（即使您上线后）遵循这些实践，以确保您充分利用系统。
* [资产规模](assets-sizing-guide.md)调整指南在编制资产实施的估计时，务必确保在资产存储、CPU、内存、IO和网络吞吐量方面有足够的可用资源。 调整其中许多项目的大小需要了解要加载到系统中的资源数量。 本指南包括最佳实践，有助于确定评估部署AEM Assets所需的基础架构和资源的有效指标以及规模调整工具。
* [资产迁移指](assets-migration-guide.md)南如果您要将资产从旧式系统迁移到AEM Assets，可以考虑几个步骤来简化迁移过程。 迁移指南包含您执行的任务的最佳实践，以分阶段方式将资产引入AEM。 这包括应用元数据、生成演绎版以及激活资产以进行发布部署。
* [资产网络注意](assets-network-considerations.md)事项在处理AEM部署时，了解网络拓扑对于了解网络性能、识别选择点和描述预期的用户体验至关重要。 资产网络考虑事项文档在设计AEM资产部署时讨论网络考虑事项。
* [资产监控指](assets-monitoring-best-practices.md)南部署AEM后，您应当监控特定任务和系统的总体情况，以确保系统完整性和操作效率。 《监视指南》包括监控系统各个方面的最佳实践。
* （已弃用）资 [源卸载指](assets-offloading-best-practices.md)南在AEM Assets处理大文件和运行工作流会占用大量CPU、内存和I/O资源。 卸载这些任务可以降低CPU、内存和IO开销。 资产分载指南包括资产分载的推荐使用案例和最佳实践。
* [AEM桌面应用程序最佳实践](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)AEM桌面应用程序将您的数字资产管理(DAM)解决方案与您的桌面相链接，因此您可以直接在桌面上打开AEM web UI中提供的文件。 AEM桌面应用程序易于使用的工作流通过桌面操作系统提供的网络共享技术实现。 本指南介绍AEM桌面应用程序的主要功能和建议使用。
* [AEM和Creative Cloud集成最佳实践](aem-cc-integration-best-practices.md)您可以通过多种方式将AEM部部署与Creative Cloud集成。 遵循一些最佳实践来简化集成和资产转让工作流，有助于实现最高效率。 本指南包含有关将AEM Assets与Adobe Creative Cloud整合的最佳实践。
* （已弃用） [AEM到Creative Cloud文](aem-cc-folder-sharing-best-practices.md)件夹共享最佳实践您可以配置AEM以允许DAM中的用户与Creative Cloud(CC)用户共享文件夹，以便在Creative Cloud资产服务中将它们作为共享文件夹。 该功能可用于在创意团队和DAM用户之间交换文件。 本指南介绍了将AEM用于Creative Cloud文件夹共享功能的最佳实践。
