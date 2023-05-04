---
title: 使用AEM管理资产的最佳实践
description: 确定并遵循可增强系统在负载下的稳定性和性能的最佳实践，具体取决于 [!DNL Experience Manager] 资产部署以及用于摄取和处理资产的功能。
contentOwner: AG
feature: Asset Management
role: Architect,Admin
exl-id: e2ab924b-53cb-4011-8c0a-9e8e59dd2f16
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# 的最佳实践 [!DNL Experience Manager] 资产 {#best-practices-for-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets是提供高质量数字营销体验的关键部分，通过提高内容周转率，为实现业务目标做出贡献。 如果您在 [!DNL Assets] 或定期/定期上传大量资产（包括视频和动态媒体），优化数字资产管理体验对于提高系统效率至关重要。

根据您的定位方式 [!DNL Assets] 对于您的组织以及您在资产摄取、演绎版生成和元数据提取方面使用的功能，识别并遵循不同区域的最佳实践会极大地增强系统在加载时的稳定性和性能。

在查看以下指南后，您将拥有构建和管理符合您需求的企业资产管理系统所需的知识和工具。

* [资产性能调整指南](performance-tuning-guidelines.md)
包括一组最佳实践，您可以在实施的任何时间点（即使在上线后）遵循这些最佳实践，以确保您能够充分利用系统。
* [资产大小调整指南](assets-sizing-guide.md)
在编制资产实施的估计值时，务必确保在资产存储、CPU、内存、IO和网络吞吐量方面有足够的可用资源。 调整其中许多项目的大小需要了解系统中加载的资产数量。 本指南包含一些最佳实践，可帮助确定用于估算部署所需基础架构和资源的有效量度 [!DNL Experience Manager] 资产以及大小调整工具。
* [Assets迁移指南](assets-migration-guide.md)
如果您希望将资产从旧系统迁移到 [!DNL Experience Manager] 资产，需要考虑以下几个步骤来简化迁移过程。 迁移指南包含有关将资产引入的所执行任务的最佳实践 [!DNL Experience Manager] 分阶段进行。 这包括应用元数据、生成演绎版，以及激活资产以发布部署。
* [资产网络注意事项](assets-network-considerations.md)
处理时 [!DNL Experience Manager] 部署、了解网络拓扑对于了解网络性能、识别选择点和描述预期用户体验非常重要。 资产网络注意事项文档讨论了设计 [!DNL Experience Manager] 资产部署。
* [资产监控指南](assets-monitoring-best-practices.md)
在 [!DNL Experience Manager] 部署后，您应该监控某些任务和系统的总体情况，以确保系统完整性和操作效率。 监控指南包含监控系统各个方面的最佳实践。
* （已弃用） [Assets卸载指南](assets-offloading-best-practices.md)
在中处理大文件和运行工作流 [!DNL Experience Manager] 资产可能会消耗大量CPU、内存和I/O资源。 卸载这些任务可以减少CPU、内存和IO开销。 资产卸载指南包含资产卸载的推荐用例和最佳实践。
* [[!DNL Experience Manager] 桌面应用程序最佳实践](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app-best-practices.html)
   [!DNL Experience Manager] 桌面应用程序可将您的数字资产管理(DAM)解决方案与桌面链接，以便您能够打开 [!DNL Experience Manager] web UI直接在桌面上。 [!DNL Experience Manager] 桌面应用程序的易于使用的工作流程通过使用桌面操作系统提供的网络共享技术来实现。 本指南介绍的主要功能和建议使用 [!DNL Experience Manager] 桌面应用程序。
* [[!DNL Experience Manager] 和Creative Cloud集成最佳实践](aem-cc-integration-best-practices.md)
您可以集成 [!DNL Experience Manager] 通过Creative Cloud进行部署。 遵循一些最佳实践来简化集成和资产传输工作流，有助于实现最高效率。 本指南包含有关集成的最佳实践 [!DNL Experience Manager] 资产与Adobe Creative Cloud。
* （已弃用） [[!DNL Experience Manager] Creative Cloud文件夹共享最佳实践](aem-cc-folder-sharing-best-practices.md)
您可以配置 [!DNL Experience Manager] 允许DAM中的用户与Creative Cloud用户共享文件夹，以便他们在Creative Cloud资产服务中可以作为共享文件夹。 该功能可用于在创意团队和DAM用户之间交换文件。 本指南介绍了利用 [!DNL Experience Manager] Creative Cloud文件夹共享功能。
