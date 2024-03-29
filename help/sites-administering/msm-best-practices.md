---
title: MSM 最佳实践
seo-title: MSM Best Practices
description: 查找由Adobe工程和咨询团队编译的最佳实践，以帮助启动和运行AEM多站点管理器。
seo-description: Find best practices compiled by Adobe engineering and consulting teams to help get up and running with the AEM Multi Site Manager.
uuid: cbb598bb-ec8f-4985-97af-7c87f5891c66
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features, best-practices
content-type: reference
discoiquuid: 04344537-7485-40a9-ad14-804ba448f1e2
feature: Multi Site Manager
exl-id: f23a1c62-0191-4b5b-90be-d66d51e38f83
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 40%

---

# MSM 最佳实践{#msm-best-practices}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 常规 {#general}

MSM 是用于自动化内容部署的可配置框架。实施通常涉及网站的主要部分，并且跨多个组织和地理区域。因此，强烈建议您像规划网站一样仔细规划 MSM 实施：

* 在开始实施之前，仔细&#x200B;**规划结构和内容流**。
* **进行所需数量的自定义，越少越好。** 虽然MSM支持高度自定义（例如转出配置），但是对于网站的性能、可靠性和可升级性，通常的最佳实践是最大限度地减少自定义。
* 尽早建立&#x200B;**治理**&#x200B;模型，并相应地培训用户以确保成功。从治理角度来看，最佳做法是 **最大限度地减少本地内容制作者的权限** 将内容分配/连接到其他本地用户及其各自的Live Copy。 这是因为，不受控制的链式继承会大大增加 MSM 结构的复杂性并降低其性能和可靠性。

* 一旦您的结构存在计划，内容流、自动化和管理 —  **原型和全面测试系统**，然后再开始实时实施。
* 请记住，**Adobe 咨询和领先的系统集成商**&#x200B;在使用 MSM 规划和实施内容自动化方面拥有丰富的经验，他们可以帮助您启动 MSM 项目并完成整个实施。

>[!NOTE]
>
>有关使用MSM的更多信息，请参阅知识库文章：
>
>* [MSM常见问题解答](https://helpx.adobe.com/experience-manager/kb/index/msm_faq.html)
>* [MSM问题疑难解答](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-msm-issues.html)
>


>[!NOTE]
>
>您还可以使用 [引用组件](/help/sites-authoring/default-components-foundation.md#reference) 重复使用单个页面或段落。 但请记住：
>
>* MSM更加灵活，允许对同步的内容和时间进行细粒度控制。
>* [核心组件](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=zh-Hans) 现在建议覆盖基础组件。
>


## Live Copy 源和 Blueprint 配置 {#live-copy-sources-and-blueprint-configurations}

请记住，Live Copy可以使用 [常规页面](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page) 或 [Blueprint配置](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). 二者都是有效的用例。

使用 Blueprint 配置的额外好处是：

* 允许作者使用 **转出** blueprint上的选项 — 将修改（显式）推送到从此blueprint继承的Live Copy。
* 允许作者使用 **创建网站**;这允许用户轻松选择语言并配置Live Copy的结构。
* 为与Blueprint有关的Live Copy定义默认转出配置。

如果未引用Blueprint配置，则只能从Live Copy本身启动转出，实质上是从源中提取内容。

使用Live Copy创建新站点时，最好创建Blueprint配置，以确保完整MSM功能集的可用性。

>[!NOTE]
>
>无法从Blueprint中将CUG组转出到Live Copy。 请在配置 Live Copy 时对此进行规划。

## 组件和容器同步 {#components-and-container-synchronization}

通常，MSM 中关于组件同步的转出规则是：

* 组件转出时将与 Blueprint 中包含的任何资源同步。
* 容器仅同步当前资源。

这意味着组件将被视为聚合，并且在转出时，组件本身及其所有子组件都将替换为 Blueprint 中的组件。这意味着，如果本地将资源添加到此类组件中，它将在转出时移至 Blueprint 的内容中。

为了支持组件的嵌套，以便在转出中维护本地添加的组件，必须将组件声明为容器。例如，默认的parsys声明为容器，以便它可以支持本地添加的内容。

>[!NOTE]
>
>将属性 `cq:isContainer` 添加到组件中以将它指定为容器。

## 创建站点 {#create-site}

请注意，AEM有两种主要方法可用于创建Live Copy:

* When [创建Live Copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-page)

   这可以视为更宽泛的方法，允许您从任何页面创建Live Copy。 Live Copy的内容结构与源完全匹配。

* When [创建网站](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration)

   这是一种更为专门的方法，主要用于创建具有多语言结构的网站。

在创建网站时，请注意以下事项：

* 要创建新站点，您需要 [Blueprint 配置](/help/sites-administering/msm-livecopy.md#managing-blueprint-configurations)。
* 要允许选择在新站点中创建的语言路径，相应的语言根必须存在于 Blueprint（源）中。
* 一次 [新站点已创建为live copy](/help/sites-administering/msm-livecopy.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (使用 **创建**，则 **网站**)，此Live Copy的前两个级别是 *浅浅*. 页面的子级不属于实时关系，但如果找到与触发器匹配的实时关系，则转出仍会下降。

   这有助于避免：

   * 在blueprint中手动添加语言（在第一级以下）
   * 手动在语言根目录的正下方添加内容，
   * 不会导致在转出时自动将新内容传递到Live Copy中。

## MSM 和多语言网站 {#msm-and-multilingual-websites}

MSM 可通过两种方式来帮助创建多语言网站：

* 创建语言母版时。

   * 虽然 MSM 本身&#x200B;**不提供内容翻译**，但它可以与第三方翻译连接器集成。请注意：

      * MSM允许您在页面和/或组件级别取消继承。 这有助于防止在下一个转出中覆盖已翻译的内容（来自Live Copy，包含来自Blueprint的尚未翻译的内容）。
      * 一些第三方翻译连接器会自动实施对 MSM 继承的管理。

         请与您的翻译服务提供商联系以获取更多信息。

      * 创建并翻译语言母版的另一种方法是将语言副本与 AEM 的现成的翻译集成框架结合使用。

* 从语言母版中推出内容时。

   * 例如，从主控法语到特定国家的地点，如法国/法语、加拿大/法语、瑞士/法语。

有关详细信息，请参阅 [翻译多语言站点的内容](/help/sites-administering/translation.md) 和 [翻译最佳实践](/help/sites-administering/tc-bp.md).

## 结构更改和转出 {#structure-changes-and-rollouts}

Blueprint/源树中内容结构的修改在Live Copy中的反映方式不同。 这取决于修改类型：

* **创建** 使用标准转出配置转出后，blueprint中的新页面将导致在Live Copy中创建相应的页面。

* **删除** 使用标准转出配置转出后，blueprint中的页面将导致从Live Copy中删除相应的页面。

* **移动** Blueprint中的页面将 **not** 使用标准转出配置转出后，将导致相应页面在Live Copy中移动：

   * 此行为的原因是页面移动隐式包含页面删除。这可能会在发布时导致意外行为，因为删除作者的页面会在发布时自动停用相应的内容。 这也可能会对相关项目（如链接、书签和其他项目）产生连锁影响。
   * 相应Live Copy页面中的内容继承会进行更新，以反映其源在Blueprint中的新位置。
   * 要完全实现页面从Blueprint移动到Live Copy，请考虑以下最佳实践：

>[!NOTE]
>
>此操作仅适用于 [转出触发器时](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/msm-sync.html#rollout-triggers).

* 创建自定义转出配置：

   * 此新配置必须包含操作：

      `PageMoveAction`

      不要向此配置添加其他操作。

* 定位新配置：

   * 要完全转出页面移动，同时在Live Copy中的旧位置删除相应的页面：

      * 将新创建的配置放置在标准转出配置的前面。

         标准转出配置将负责删除其旧位置中的页面。
   * 要在将相应页面保留在Live Copy中其旧位置（实质上是复制内容）的同时转出页面移动，请执行以下操作：

      * 将新创建的配置放置在标准转出配置的后面。

         这将确保Live Copy中未删除或从发布中停用任何内容。


## 自定义转出 {#customizing-rollouts}

MSM 转出配置是高度自定义的。您应意识到，自动化转出可能会产生深远的影响。作为最佳实践，您应该规划 *非常* 例如，在之前请仔细考虑：

* 自动推广；例如，使用 [onModify触发器](#onmodify),
* 自定义 [节点类型/属性](#node-types-properties),
* 启动后续工作流，
* 和/或在转出中激活内容。

### onModify {#onmodify}

在使用[转出触发器](/help/sites-administering/msm-sync.md#rollout-triggers) `onModify` 时，您应考虑：

* 使用 `onModify` 触发器自动化转出可能会对创作性能产生负面影响，因为它们会在每次修改页面后触发转出。**

* 转出结果可能与预期结果不同：

   * 您不能指定生成的修改事件的顺序。
   * 基于事件的架构不能保证传递给 Rollout Manager 的事件的顺序。

* 如果对同一资源进行并发更新，则使用此转出配置可能会导致发生提交冲突。

因此，建议您 *仅* use `onModify` 自动推出启动的好处超过任何潜在的性能问题时触发。

### 节点类型/属性 {#node-types-properties}

请记住：

* 除了自定义转出操作之外，MSM 还允许您自定义正在转出的节点属性。的 [MSM OSGi配置允许您排除节点类型](/help/sites-administering/msm-sync.md#excluding-properties-and-node-types-from-synchronization) 从源复制到Live Copy中。

## 更多信息 {#further-information}

本页和以下页介绍了相关问题：

* [创建并同步 Live Copy](/help/sites-administering/msm-livecopy.md)
* [Live Copy 概述控制台](/help/sites-administering/msm-livecopy-overview.md)
* [配置 Live Copy 同步](/help/sites-administering/msm-sync.md)
* [MSM 转出冲突](/help/sites-administering/msm-rollout-conflicts.md)
