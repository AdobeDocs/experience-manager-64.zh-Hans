---
title: 升级到AEM 6.4
seo-title: 升级到AEM 6.4
description: 了解将旧版AEM安装升级到AEM 6.4的基础知识。
seo-description: 了解将旧版AEM安装升级到AEM 6.4的基础知识。
uuid: aa878528-5161-4df3-9fed-cc779fb6bdbe
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 81ceb91d-039e-45f0-9b0c-b8233901dea8
targetaudience: target-audience upgrader
feature: Upgrading
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 3%

---


# 升级到AEM 6.4{#upgrading-to-aem}

在本节中，我们将介绍将AEM安装升级到AEM 6.4的过程：

* [计划升级](/help/sites-deploying/upgrade-planning.md)
* [利用模式检测器评估升级复杂度](/help/sites-deploying/pattern-detector.md)
* [AEM 6.4中的向后兼容性](/help/sites-deploying/backward-compatibility.md)
* [升级过程](/help/sites-deploying/upgrade-procedure.md)
* [升级代码和自定义](/help/sites-deploying/upgrading-code-and-customizations.md)
* [升级前维护任务](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [执行就地升级](/help/sites-deploying/in-place-upgrade.md)
* [升级后检查和疑难解答](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [可持续升级](/help/sites-deploying/sustainable-upgrades.md)
* [延迟内容迁移](/help/sites-deploying/lazy-content-migration.md)
* [AEM 6.4中的存储库重组](/help/sites-deploying/repository-restructuring.md)

为了更轻松地引用这些过程中涉及的AEM实例，在这些文章中使用了以下术语：

* *source*&#x200B;实例是您要从升级的AEM实例。
* *目标*&#x200B;实例是要升级到的实例。

>[!NOTE]
>
>作为提高升级可靠性的努力的一部分，AEM 6.4进行了全面的存储库重组。 有关如何与新结构对齐的详细信息，请参阅AEM 6.4中的[存储库重组](/help/sites-deploying/repository-restructuring.md)

## 有什么变化？{#what-has-changed}

以下是在过去几个AEM版本中对注释的主要更改：

AEM 6.0引入了新的Jackrabbit Oak存储库。 持久性管理器由[微内核](/help/sites-deploying/recommended-deploys.md)替换。 从6.1版开始，不再支持CRX2。 需要运行名为crx2oak的迁移工具，才能从5.6.1实例迁移CRX2存储库。 有关详细信息，请参阅[使用CRX2OAK迁移工具](/help/sites-deploying/using-crx2oak.md)。

如果要使用资产分析，并且您是从AEM 6.2以前的版本升级，则必须迁移资产，并通过JMX bean生成ID。 在我们的内部测试中，一个TarMK环境上的12.5万个资源在一小时内完成迁移，但结果可能有所不同。

AEM 6.3为`SegmentNodeStore`引入了一种新格式，这是TarMK实现的基础。 如果您从AEM 6.3以前的版本升级，则需要在升级过程中进行存储库迁移，这涉及系统停机。

Adobe工程公司估计，此时间约为20分钟。 请注意，不必重新编制索引。 此外，还发布了crx2oak工具的新版本以使用新的存储库格式。

**从AEM 6.3升级到AEM 6.4时，不需要进行此迁移。**

升级前维护任务已经过优化，可支持自动化。

crx2oak工具命令行使用选项已更改为适合自动化，并支持更多升级路径。

升级后的检查也变得对自动化友好。

修订的定期垃圾收集和数据存储垃圾收集现在是需要定期执行的例行维护任务。 随着AEM 6.3的推出，Adobe支持并建议联机修订清理。 有关如何配置这些任务的信息，请参见[修订清理](/help/sites-deploying/revision-cleanup.md)。

**AEM 6.4引入** 了Pattern  [Detector，](/help/sites-deploying/pattern-detector.md) 用于评估开始计划升级时的升级复杂性。6.4还着重于功能的[向后兼容性](/help/sites-deploying/backward-compatibility.md)。 最后，还添加了[可持续升级](/help/sites-deploying/sustainable-upgrades.md)的最佳做法。

有关最新AEM版本中其他内容更改的详细信息，请参阅完整发行说明：

* [https://helpx.adobe.com/cn/experience-manager/6-2/release-notes.html](https://helpx.adobe.com/cn/experience-manager/6-2/release-notes.html)
* [https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html)
* [https://helpx.adobe.com/cn/experience-manager/6-4/release-notes.html](https://helpx.adobe.com/cn/experience-manager/6-4/release-notes.html)

## 升级概述{#upgrade-overview}

升级AEM是一个多步骤、有时是多月的过程。 以下概述概述了升级项目中包含的内容以及本文档中包含的内容：

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## 升级流程，升级改进{#upgrade-overview-1}

下图显示了总体建议流程，重点介绍了升级方法。 请注意我们引入的新功能的参考。 升级应与模式检测器开始（请参阅[使用模式检测器评估升级复杂性](/help/sites-deploying/pattern-detector.md)），它允许您根据生成的报告中的模式决定要采用的路径，以与AEM 6.4兼容。

6.4中重点介绍了如何使所有新功能向后兼容，但是，在您仍看到某些向后兼容问题时，兼容性模式允许您暂时推迟开发以使自定义代码与6.4兼容。此方法可帮助您避免在升级后立即进行开发工作(请参阅AEM 6.4](/help/sites-deploying/backward-compatibility.md)中的[向后兼容性)。

最后，在6.4开发周期中，可持续升级（请参阅[可持续升级](/help/sites-deploying/sustainable-upgrades.md)）下引入的功能可帮助您遵循最佳实践，使未来升级更高效、更无缝。

![6_4_upgrade_overviewproftwork-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)

