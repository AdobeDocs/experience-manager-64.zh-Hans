---
title: AEM Sites 发行说明
seo-title: AEM Sites
description: 以下发行说明特定于 Adobe Experience Manager 6.4 Sites。
seo-description: 以下发行说明特定于 Adobe Experience Manager 6.4 Sites。
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
translation-type: tm+mt
source-git-commit: 901a923b6ab2b6bee1738d2b8f1928571c8019cb

---


# AEM Sites 发行说明 {#aem-sites-release-notes}

## 站点 {#sites}

有关 AEM Sites 6.4 增强功能的详细信息，请参阅以下内容：

### 站点管理 {#site-administration}

* 新内容树边栏可快速导航站点层次结构。 与列表视图相结合，这会恢复经典UI交互模型以浏览站点。
* 改进了在大文件夹的卡片视图和列表视图中的滚动。
* 改进了与搜索结果的交互——返回按钮可恢复先前的搜索结果。
* 其他键盘快捷键用于大多数常见操作，例如打开特定边栏、编辑、移动和删除页面或打开属性。
* 能够禁用键盘快捷键（在首选项中启用／禁用）。
* 在7天后停止显示所有UI中相对的时间戳（在“首选项”中设置为默认设置）。

### 页面编辑器 {#page-editor}

* 更新了设备列表以进行响应式站点预览，现在包括Apple iPhone 8、8 plus和X以及Samsung S7
* 将模板设计信息的默认位置从/etc/design移开到/conf中支持站点特定设置。 从先前AEM版本升级的客户可以继续使用/etc/design。

### 组件和模板开发 {#component-amp-template-development}

* Project Archetype 13+，请参阅 [Github以获取发行说明](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases)。
* HTL 版本 1.3.1，请参阅 [Github 以查看发行说明](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1)。
* Core Components 2.0.4+，请参阅 [Github 以查看发行说明](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases)。
* 样式系统

   * 添加了一个全新概念，用于将CSS类分配给组件并允许页面编辑器中的用户通过UI从样式子集中进行选择
   * 添加了定义组件周围呈现的HTML元素名称的功能，例如&lt;main>, &lt;aside>

* 布局容器的网格系统，请参阅 [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid)。
* 模板编辑器和策略

   * 策略现在支持每个组件、每个容器、每个模板的样式系统配置。
   * 改进了在可编辑组件上的模板中定义布局的支持

* 引用站点 We.Retail 3.0，请参阅 [Github 以查看发行说明](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases)。

>[!CAUTION]
>
>AEM包括jQuery库的版本1.12.4，以提供与现有自定义代码的最大兼容性。 Adobe 已对其进行了修改以解决已知的安全问题。

### 内容片段和编辑器 {#content-fragments-amp-editor}

* 引入了结构化内容模型作为内容片段的基础

   * 模型编辑器UI
   * 为内容片段模型（单行文本、多行文本、数字、布尔值、日期和时间、枚举、内容引用、标记）预配置的数据元素

* 改进了AEM内容片段编辑器的可用性

   * View-all-elements概述
   * 针对单个元素的全屏编辑
   * 增强的富文本编辑功能（项目符号列表、编号列表、缩进、超链接、表、查找和替换、拼写检查）

* 为AEM内容片段添加了增强的输出选项

   * 新内容片段组件，作为核心组件的一部分。 [查看GitHub上的代码。](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * 通过Sling Model Exporter支持JSON输出内容服务

### 体验片段 {#experience-fragments}

* 引入了体验片段构建块，以便通过分组组件和允许在变量内轻松引用来在体验片段变量之间重复使用内容。
* 添加了通过参考边栏将体验片段添加到翻译项目的功能
* 添加通过时间轴边栏使用Experience Fragments启动工作流的功能
* 引用边栏现在显示体验片段在AEM中的使用位置
* 模板位置的配置现在允许作者在全局级别或文件夹级别定义允许使用的体验片段模板
* 多面搜索现在支持高级筛选，如已发布／未发布，可导出到社交媒体和Adobe Target
* 在将体验片段导出到Pinterest或Facebook时添加了单个社交媒体登录
* 将AEM Experience Fragments与Adobe Target集成。 将体验片段同步到Target后，将在Adobe Target中创建选件，并与Target的Visual Experience Composer一起使用，以将其嵌入到任何支持Target的体验中。

### 翻译 {#translation}

* 增强了AEM Translation项目的可用性：

   * 在一个项目中支持多种目标语言
   * 用于自动提升和删除翻译启动项的选项
   * 可选择安排翻译项目（每日、每周、每月、每年）的重复执行
   * 增强的翻译项目拼贴，包含更详细的状态信息

* 引入了“反向翻译内存更新”，用于在AEM中编辑本地内容后更新第三方翻译管理系统中的翻译内存
* 翻译工作流程现在支持分组语言根
* 增加了将任意名称分配给语言根以及使用JCR属性映射到ISO代码的功能
* 智能翻译更新现在可识别已添加到语言主分支的新页面
* 在站点管理员列表视图中引入了翻译状态报告

### 多站点管理 (MSM) {#multi-site-management-msm}

* 通过使用基于Oak的索引与内存中的索引(LiveCopyIndex)改进了MSM可伸缩性

### 启动项 {#launches}

* 改进了包含大站点树的启动项的性能，并且如果有许多启动项处于活动状态
* 改进了具有多个根页面的启动项的自动提升和发布。
* 修复了导致响应式设备预览无法处理在启动项上下文中编辑的页面的问题。

### 内容定位和模拟 {#content-targeting-simulation}

* 支持文件夹以根据站点／上下文组织区段(CQ-94620)
* 将区段的默认位置移到/conf中，以包含特定于站点／上下文的区段列表。

### AEM 与 Adobe Target  {#aem-amp-adobe-target-nbsp}

* 将AEM Experience Fragments与Adobe Target集成。 将体验片段同步到Target后，将在Adobe Target中创建选件，并与Target的Visual Experience Composer一起使用，以将其嵌入到任何支持Target的体验中。
* Adobe Target mbox.js版本63现已包含在内。 Adobe建议将实施切换为at.js。
* 现在包含 at.js 版本 1.2.2。Adobe建议使用动态标签管理(DTM)或 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) ，将at.js配置到站点中。

### AEM 与 Adobe Analytics {#aem-amp-adobe-analytics}

* s_code.js H.27.5现已包含在内。 Adobe建议将实施切换到AppMeasurement.js
* AppMeasurement.js 1.8.0现已包括在内。 Adobe建议使用动态标签管理(DTM)或 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) ，将AppMeasurement.js配置到站点中。

## Communities 加载项 {#communities-add-on}

请参阅 [Communities 发行说明页面](/help/release-notes/communities-release-notes.md)

## Screens 加载项 {#screens-add-on}

* 增加了对Screens播放器的支持，可连接到AEM发布服务器以进行命令和控制以及渠道下载（而不是直接连接到AEM作者）。
* 增加了在计划中对渠道分配进行分组的功能
* 渠道分配现在具有开始和结束日期
* 设备控制板现在显示播放器外壳和固件版本
* 设备功能板列表显示播放器的连接状态
* 添加了对AEM Screens播放器的Google Chrome OS支持
* 添加了适用于AEM Screens播放器的Microsoft Windows 10

