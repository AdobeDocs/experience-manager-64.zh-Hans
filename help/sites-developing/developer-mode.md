---
title: 开发人员模式
seo-title: 开发人员模式
description: 开发人员模式打开一个侧面板，其中包含多个选项卡，向开发人员提供有关当前页面的信息
seo-description: 开发人员模式打开一个侧面板，其中包含多个选项卡，向开发人员提供有关当前页面的信息
uuid: 2ff0d85e-fe49-4506-b6d6-74cc060d7ea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: components
content-type: reference
discoiquuid: efbe46a3-c37f-4b67-8b3a-188cfc75118b
translation-type: tm+mt
source-git-commit: 185bdd83b8b67671a31aa3f341b80614ed819b6c
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# 开发者模式{#developer-mode}

在AEM中编辑页面时，可以使用多种[模式](/help/sites-authoring/author-environment-tools.md#page-modes)，包括开发人员模式。 这会打开一个侧面板，其中包含多个选项卡，向开发人员提供有关当前页面的信息。 三个选项卡为：

* **[用于](#components)** 查看结构和性能信息的组件。
* **[进](#tests)** 行测试并分析结果。
* **[错](#errors)** 误，无法看到出现的任何问题。

这些帮助开发人员：

* 发现：页面由哪些页面组成。
* 调试：发生在何处、何时，这反过来有助于解决问题。
* 测试：应用程序是否按预期运行。

>[!CAUTION]
>
>开发人员模式：
>
>* 仅在触屏优化UI中可用（编辑页面时）。
>* 在移动设备或桌面上的小窗口上不可用（由于空间限制）。
   >   * 当宽度小于1024px时，会发生这种情况。
>* 仅适用于属于`administrators`组的用户。


>[!CAUTION]
>
>开发者模式仅适用于未使用nosamplecontent运行模式的标准作者实例。
>
>如果需要，可以配置它以供使用：
>
>* 在使用nosamplecontent运行模式的创作实例上
>* 发布实例

>
>
使用后应再次禁用它。

>[!NOTE]
>
>请参阅：
>
>* 知识库文章[AEM TouchUI问题疑难解答](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html)，以获取更多提示和工具。
>* AEM Gems会话关于[AEM 6.0开发者模式](https://docs.adobe.com/content/ddc/en/gems/aem-6-0-developer-mode.html)。


## 打开开发者模式{#opening-developer-mode}

开发人员模式作为页面编辑器的侧面板实现。 要打开面板，请从页面编辑器工具栏的模式选择器中选择&#x200B;**开发人员**:

![chlimage_1-229](assets/chlimage_1-229.png)

该面板分为两个选项卡：

* **[组件](/help/sites-developing/developer-mode.md#components)** -显示一个组件树，类似于作 [者的](/help/sites-authoring/author-environment-tools.md#content-tree) 内容树

* **[错误](/help/sites-developing/developer-mode.md#errors)** -出现问题时，将显示每个组件的详细信息。

### 组件 {#components}

![chlimage_1-230](assets/chlimage_1-230.png)

此组件树显示：

* 概述页面上呈现的组件和模板链（SLY、JSP等）。 树可以展开以在层次中显示上下文。
* 显示渲染组件所需的服务器端计算时间。
* 允许您展开树并在树中选择特定组件。 通过选择，可访问组件详细信息；例如：

   * 存储库路径
   * 脚本链接(以CRXDE Lite访问)

* 所选组件（在内容流中，用蓝色边框表示）将在内容树中高亮显示（反之亦然）。

这有助于：

* 确定并比较每个组件的渲染时间。
* 查看并了解层次结构。
* 通过查找慢速组件，了解并改进页面加载时间。

每个组件条目都可以显示（例如）:

![chlimage_1-231](assets/chlimage_1-231.png)

* **视图详细信息**:指向列表的链接，其中显示：

   * 用于呈现该组件的所有组件脚本。
   * 此特定组件的存储库内容路径。

   ![chlimage_1-232](assets/chlimage_1-232.png)

* **编辑脚本**:链接：

   * 以CRXDE Lite打开组件脚本。

* 展开组件条目（箭头）还可以显示：

   * 所选组件中的层次结构。
   * 单独呈现选定组件、嵌套在其中的任何单个组件以及合并的总时间。

   ![chlimage_1-233](assets/chlimage_1-233.png)

>[!CAUTION]
>
>某些链接指向`/libs`下的脚本。 但是，这些只供参考，您&#x200B;**不得**&#x200B;编辑`/libs`下的任何内容，因为您所做的任何更改都可能丢失。 这是因为，无论您何时升级或应用修补程序／功能包，此分支都可能发生更改。 您所需的任何更改都应在`/apps`下进行，请参阅[叠加和覆盖](/help/sites-developing/overlays.md)。

### 错误 {#errors}

![chlimage_1-234](assets/chlimage_1-234.png)

希望&#x200B;**Errors**&#x200B;选项卡始终为空（如上所示），但出现问题时，会为每个组件显示以下详细信息：

* 如果组件将一个条目写入错误日志以及错误的详细信息并直接链接到CRXDE Lite中的相应代码，则显示警告。
* 组件打开管理会话时显示警告。

例如，在调用未定义方法的情况下，将在&#x200B;**Errors**&#x200B;选项卡中显示结果错误：

![chlimage_1-235](assets/chlimage_1-235.png)

出现错误时，“组件”选项卡树中的组件条目也将用指示符进行标记。

### 测试 {#tests}

>[!CAUTION]
>
>在AEM 6.2中，开发者模式的测试功能作为独立工具应用程序重新实施。
>
>有关详细信息，请参阅[测试UI](/help/sites-developing/hobbes.md)。
