---
title: 链接检查程序
description: 链接检查器有助于验证内部链接和外部链接，并允许链接重写。
exl-id: 30718d02-3370-48aa-a5ba-242d5efaa14c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# 链接检查程序 {#the-link-checker}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

内容作者不必担心如何验证其内容页面中包含的每个链接。

链接检查器会自动运行以协助内容作者获取其链接，包括：

* 在链接添加到内容时验证这些链接
* 显示内容中所有外部链接的列表
* 执行链接转换

链接检查程序具有 [配置选项](#configuring) 例如定义内部验证、允许在验证中忽略某些链接或链接路径，以及重写链接重写规则。

链接检查程序将同时验证这两个 [内部链接](#internal) 和 [外部链接。](#external)

>[!NOTE]
>
>由于链接检查器检查每个内容页面的链接，因此链接检查器可能会影响大型存储库的性能。 在这种情况下，您可能需要 [配置Link Checker运行的频率](#configuring) 或 [禁用它。](#disabling)

## 内部链接检查 {#internal}

内部链接是指指向AEM存储库中其他内容的链接。 可以使用RTE的路径选取器或自定义组件添加内部链接。 例如：

* 您的页面 `/content/wknd/us/en/adventures/ski-touring.html`
* 包含指向的链接 `/content/wknd/us/en/adventures/extreme-ironing.html` 在 [文本组件。](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

内容作者向页面添加内部链接后，会立即验证内部链接。 如果链接变为无效：

* 它将从发布者中删除。 链接的文本将保留，但链接本身将被删除。
* 在创作界面中，该链接显示为断开的链接。

![创作页面时内部链接断开](assets/link-checker-invalid-link-internal.png)

## 外部链接检查 {#external}

外部链接是指向AEM存储库外部的内容的链接。 可以使用RTE或自定义组件添加外部链接。 例如：

* 您的页面 `/content/wknd/us/en/adventures/ski-touring.html`
* 包含指向的链接 `https://bunwarmerthermalunderwear.com` 在 [文本组件。](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

通过检查外部链接的可用性，验证其语法。 此检查在可配置的内部位置异步完成。 如果链接检查器发现外部链接无效：

* 它将从发布者中删除。 链接的文本将保留，但链接本身将被删除。
* 在创作界面中，该链接显示为断开的链接。

![创作页面时内部链接断开](assets/link-checker-invalid-link-external.png)

此外， [外部链接检查程序](#external-link-checker) 界面提供了内容页面上所有外部链接的概述。

### 使用外部链接检查器 {#external-link-checker}

要使用外部链接检查程序，请执行以下操作：

1. 使用 **导航**，选择 **工具**，则 **站点**.
1. 选择 **外部链接检查程序** 将显示所有外部链接的列表。

![外部链接检查器窗口](assets/external-link-checker.png)

将显示以下信息：

* **状态**  — 链接的验证状态，可以是以下任一状态：
   * **有效** - Link Checker可访问外部链接
   * **待定**  — 已将外部链接添加到网站内容，但尚未通过链接检查程序验证
   * **无效**  — 链接检查程序无法访问外部链接
* **URL**  — 外部链接
* **反向链接**  — 包含外部链接的内容页面
   * 仅填充 [如果已配置。](#configuring)
* **上次检查**  — 链接检查程序上次验证外部链接时
   * 检查链接的频率 [可配置。](#configuring)
* **上次状态**  — 上次检查链接时返回的上次HTML状态代码
* **上次可用**  — 自上次链接可供链接检查程序使用以来的时间
* **上次访问**  — 自上次在创作界面中访问具有外部链接的页面以来经过的时间

您可以使用链接列表顶部的两个按钮来操作窗口的内容：

* **刷新**  — 刷新列表的内容
* **检查**  — 检查列表中选择的单个外部链接

### 外部链接检查程序的工作原理 {#how-it-works}

外部链接检查器虽然易于使用，但它依赖于许多服务，并了解它们的工作方式有助于您了解如何 [配置链接检查器](#configuring) 以满足您的需求。

1. 每当内容作者保存指向页面的任何链接时，都会触发事件处理程序。
1. 事件处理程序遍历 `/content` 和会检查新链接或更新链接，并将它们添加到链接检查器的缓存中。
1. 的 **Day CQ Link Checker服务** 然后按常规计划执行，以检查缓存中的条目以获取有效语法。
1. 经过语法验证的链接随后会显示在 [外部链接检查程序](#external-link-checker) 窗口。 但是，它们将位于 **待定** 状态。
1. 的 **Day CQ Link Checker任务** 然后定期执行，以通过调用GET来验证链接。
1. 的 **Day CQ Link Checker任务** 然后，使用GET调用的结果更新“外部链接检查器”窗口中的条目。

## 配置链接检查程序 {#configuring}

在AEM中，“链接检查器”可自动开箱即用。 但是，有许多OSGi配置可通过修改来更改其行为：

* **Day CQ Link Checker信息存储服务**  — 此服务定义存储库中Link Checker缓存的大小。
* **Day CQ Link Checker服务**  — 此服务对外部链接的语法执行异步检查。 您可以定义检查期，以及检查器跳过哪些类型的链接（包括其他选项）。
* **Day CQ Link Checker任务**  — 此服务对外部链接执行GET验证。 它允许对间隔进行不同的定义，以检查其他选项之间的不良链接和良好链接。
* **Day CQ Link Checker Transformer**  — 允许根据用户定义的规则集转换链接。

查看文档 [OSGi配置设置](/help/sites-deploying/osgi-configuration-settings.md) 有关如何更改OSGi设置的更多详细信息。

## 禁用链接检查程序 {#disabling}

您可以选择完全禁用链接检查程序。 为此，请执行以下操作：

1. 打开OSGi控制台。
1. 编辑 **Day CQ Link Checker Transformer**
1. 选中要禁用的选项：
   * **禁用检查**  — 禁用链接验证
   * **禁用重写**  — 禁用链接转换

>[!NOTE]
>
>如果在开始创建内容后禁用链接检查，则仍可能会在 [外部链接检查器窗口](#external-link-checker)，但它们将不再更新。
