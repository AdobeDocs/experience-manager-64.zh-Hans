---
title: 在AEM站点页面中嵌入自适应表单或交互式通信
seo-title: Embed an adaptive form or interactive communication in AEM sites page
description: 您可以在AEM站点页面中嵌入自适应表单。 用户无需离开网站页面即可填写和提交表单。
seo-description: You can embed adaptive forms in AEM sites pages. Users can fill and submit forms without leaving the site pages.
uuid: 59b49e2f-6d95-42e5-b31e-fc40936c42d2
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications, author
discoiquuid: 43362643-69cd-4006-a613-f998c79eeddc
feature: Adaptive Forms
exl-id: ba5d21a4-231c-4e1e-b172-4d700cb9696e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 0%

---

# 在AEM站点页面中嵌入自适应表单或交互式通信 {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

AEM Forms允许表单开发人员将自适应表单和交互式通信无缝嵌入到AEM Sites页面或托管在AEM外的网页中。 嵌入式自适应表单与交互式通信功能完全，用户无需离开页面即可填写和提交表单。 它有助于用户停留在网页上其他元素的上下文中，并同时与表单或交互式通信进行交互。

有关在外部网页中嵌入自适应表单的信息，请参阅 [在外部网页中嵌入自适应表单](/help/forms/using/embed-adaptive-form-external-web-page.md).

在AEM Sites页面中，您可以使用以下方式添加自适应表单或交互式通信：

* **[AEM Forms容器组件](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms提供了可添加到网站页面的组件。 利用AEM Forms容器组件，可嵌入自适应表单和交互式通信。

* **[资产浏览器](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
您创建的所有表单和交互式通信均可在资产下找到。 您可以将表单作为资产拖放到页面上。

## 前提条件 {#prerequisites}

要在使用可编辑模板的AEM站点页面中嵌入自适应表单或交互式通信，请确保将AEM表单组件配置为关联模板中允许使用的组件。 有关更多信息，请参阅 **策略和属性（布局容器）** 部分 [创建页面模板](/help/sites-authoring/templates.md).

如果站点页面使用静态模板，则需要在站点页面的段落系统中对其进行配置。 请参阅 [在设计模式下配置组件](/help/sites-authoring/default-components-designmode.md) 以了解更多信息。

## 嵌入自适应表单或交互式通信 {#af-component}

要使用AEM Forms容器组件嵌入自适应表单或交互式通信，请执行以下操作：

1. 在编辑模式下打开AEM站点页面，您要在其中嵌入自适应表单或交互式通信。
1. 从组件浏览器面板中，将AEM Forms容器组件拖放到页面上。

   或者，您也可以在资产浏览器中搜索自适应表单或交互式通信，并将其拖放到站点页面。 它将表单嵌入到AEM Forms容器中。

   >[!NOTE]
   >
   >页面上不支持多个AEM Forms容器组件。

1. 点按站点页面中嵌入的AEM Forms容器组件，然后点按 ![settings_icon](assets/settings_icon.png) 中。 的 **[!UICONTROL 编辑AEM Forms容器]** 对话框。
1. 在编辑AEM Forms容器对话框中，指定以下内容。

   * **资产类型：** 选择要嵌入的资产类型。 选项包括自适应表单和交互式通信
   * **资产路径**:浏览并选择要嵌入的自适应表单或交互式通信。 如果您从资产浏览器中将其删除，则会自动填充该内容。
   * （仅限自适应表单） **帖子提交**:选择要在表单提交时触发的操作。 您可以选择显示感谢信或感谢页。

      * **感谢信**:使用富文本编辑器编写消息以在表单提交时显示。 仅当您选择显示感谢信时，此选项才可用。
      * **感谢页面**:浏览并选择要在表单提交时显示的页面。 仅当您选择显示感谢页面时，此选项才可用。
      * **提交时刷新页面**:启用以刷新包含嵌入式自适应表单的页面，以显示感谢页面。 否则，感谢页面将替换AEM Forms容器中的自适应表单，而无需刷新页面。 仅当您选择显示感谢页面时，此选项才可用。
   * **主题**:选择一个主题，该主题定义自适应表单或交互式通信组件的样式。 样式包括外观属性，如字体样式、背景颜色、尺寸和对齐方式。
   * **高度**:指定容器的高度。 将其留空以自动调整容器大小。
   * **CSS客户端库**:指定CSS客户端库的路径。


1. 保存设置。 自适应表单或交互式通信现在嵌入到页面中。

## 发布嵌入式自适应表单和交互式通信 {#publishing-embedded-adaptive-form-and-interactive-communication}

让我们考虑以下方案，以在AEM站点页面中发布嵌入的资产（自适应表单或交互式通信）：

* 如果您是首次发布AEM站点页面，并且该页面包含嵌入的自适应表单或交互式通信，则发布站点页面和嵌入的资产。
* 如果您只修改了已发布站点页面中嵌入的自适应表单或交互式通信，则应发布原始资产，并且所做的更改会反映在已发布的站点页面中。 发布的网站页面包含对资产的引用，无需重新发布页面。
* 如果您修改了站点页面和嵌入的自适应表单或交互式通信，请重新发布站点页面和嵌入的资产。

## 修改嵌入式自适应表单和交互式通信 {#modifying-embedded-adaptive-form-and-interactive-communication}

AEM站点页面在AEM Forms容器中维护对自适应表单和交互式通信的引用。 因此，在原始自适应表单中配置的所有配置和属性（如主题、样式和提交操作）以及交互式通信都保留在嵌入的自适应表单和交互式通信中。

要修改嵌入式自适应表单和交互式通信的任何配置或属性，请执行以下操作之一。

* 在自适应表单中打开原始表单，或在相应编辑器中进行交互式通信，并对其进行修改。
* 在编辑模式下，从网站页面中点按自适应表单或交互式通信，然后点按 **[!UICONTROL 在新窗口中编辑]**. 原始表单会在编辑模式下打开，您可以对其进行修改。

>[!NOTE]
>
>在原始自适应表单或交互式通信中所做的更改会自动反映在嵌入表单中。 但是，请重新发布自适应表单、交互式通信或网站页面，以反映已发布页面中的更改。

## 注意事项和最佳实践 {#considerations-and-best-practices}

在AEM站点页面中嵌入自适应表单时，请牢记以下几点：

* 原始表单中的页眉和页脚未包含在嵌入的表单中。
* 支持用户草稿和提交嵌入的表单，这些草稿和提交内容显示在表单门户的“草稿”和“已提交”Forms选项卡中。
* 在原始表单上配置的提交操作将保留在嵌入表单中。
* 在原始表单上配置的体验定位和A/B测试在嵌入的表单中不起作用。 但是，您可以在站点页面上使用体验定位来根据用户配置文件显示不同的表单。
* 如果您为原始表单配置了Adobe Analytics，则会在Adobe Analytics中捕获嵌入表单的分析数据。 但是，它在表单分析报表中不可用。
