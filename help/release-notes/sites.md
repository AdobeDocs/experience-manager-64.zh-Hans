---
title: AEM Sites发行说明
seo-title: AEM Sites
description: 特定于Adobe Experience Manager 6.4站点的发行说明。
seo-description: Release notes specific to Adobe Experience Manager 6.4 Sites.
uuid: 593928ec-5d1a-4a88-bd73-897421c5984a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 40225441-7cfe-4395-ac71-60504b42e764
exl-id: 19ec5c00-eae5-4e7f-9dc5-c7a88b06fd2a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1046'
ht-degree: 1%

---

# AEM Sites发行说明 {#aem-sites-release-notes}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## Sites {#sites}

有关AEM Sites 6.4增强功能的详细信息，请参阅以下内容：

### 站点管理 {#site-administration}

* 新增了内容树边栏，可快速导航站点层次结构。 与列表视图结合使用，这会恢复经典UI交互模型以浏览站点。
* 改进了大型文件夹的卡片视图和列表视图中的滚动。
* 改进了与搜索结果的交互 — 返回按钮可恢复之前的搜索结果。
* 其他键盘快捷键，用于大多数常用操作，例如打开特定边栏、编辑、移动和删除页面，或打开属性。
* 能够禁用键盘快捷键（在“首选项”中启用/禁用）。
* 在7天后，停止在所有UI中显示相对时间戳（在“首选项”中设置默认设置）。

### 页面编辑器 {#page-editor}

* 更新了响应式网站预览的设备列表，现在包括Apple iPhone 8、8 Plus和X以及Samsung S7
* 将模板设计信息的默认位置从/etc/design移开，以支持/conf中的站点特定设置。 从以前的AEM版本升级的客户可以继续使用/etc/design。

### 组件和模板开发 {#component-amp-template-development}

* 项目原型13+，请参阅 [Github（发行说明）](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype/releases).
* HTL版本1.3.1，请参阅 [Github（发行说明）](https://github.com/Adobe-Marketing-Cloud/htl-spec/releases/tag/1.3.1).
* 核心组件2.0.4及更高版本，请参阅 [Github（发行说明）](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/releases).
* 样式系统

   * 添加了一个全新概念，用于将CSS类分配给组件，并允许页面编辑器中的用户通过UI从样式子集中进行选择
   * 添加了定义呈现在组件周围的HTML元素名称的功能，例如 &lt;main>, &lt;aside>

* 布局容器的网格系统，请参阅 [Github](https://github.com/Adobe-Marketing-Cloud/aem-responsivegrid).
* 模板编辑器和策略

   * 策略现在支持每个组件、每个容器、每个模板的样式系统配置。
   * 改进了对在可编辑组件的模板中定义布局的支持

* 参考网站We.Retail 3.0，请参阅 [Github（发行说明）](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases).

>[!CAUTION]
>
>AEM包含jQuery库版本1.12.4，可最大程度地与现有自定义代码兼容。 已通过Adobe进行修改以解决已知安全问题。

### 内容片段和编辑器 {#content-fragments-amp-editor}

* 引入了结构化内容模型作为内容片段的基础

   * 模型编辑器UI
   * 为内容片段模型预配置的数据元素（单行文本、多行文本、数字、布尔值、日期和时间、枚举、内容引用、标记）

* 改进了AEM内容片段编辑器的可用性

   * 查看 — 所有元素概述
   * 单个元素的全屏编辑
   * 增强的富文本编辑功能（项目符号列表、编号列表、缩进、超链接、表、查找和替换、拼写检查）

* 为AEM内容片段添加了增强的输出选项

   * 作为核心组件的一部分，新增了内容片段组件。 [请参阅GitHub上的代码。](https://github.com/Adobe-Marketing-Cloud/aem-core-wcm-components/tree/master/extension/contentfragment/content/src/content/jcr_root/apps/core/wcm/extension/components/contentfragment/v1/contentfragment)
   * 通过Sling模型导出程序支持JSON输出的内容服务

### 体验片段 {#experience-fragments}

* 引入了体验片段构建基块，通过对组件进行分组并允许在变量中轻松引用，从而便于在体验片段变量之间重复使用内容。
* 添加了通过引用边栏将体验片段添加到翻译项目的功能
* 添加了通过时间轴边栏启动体验片段工作流的功能
* 引用边栏现在显示体验片段在AEM中的使用位置
* 模板位置的配置现在允许作者在全局或文件夹级别定义允许使用的体验片段模板
* 多面搜索现在支持高级过滤，例如已发布/未发布、导出到社交媒体和Adobe Target
* 在将体验片段导出到Pinterest或Facebook时，添加了单次社交媒体登录
* 将AEM体验片段与Adobe Target集成。 将体验片段同步到Target将在Adobe Target中创建选件，这些选件可以与Target的可视化体验编辑器一起使用，以将其嵌入到任何启用了Target的体验中。

### 翻译 {#translation}

* 增强了AEM翻译项目的可用性：

   * 在一个项目中支持多种目标语言
   * 用于自动提升和删除翻译启动项的选项
   * 用于计划翻译项目定期执行的选项（每日、每周、每月、每年）
   * 增强的翻译项目图块，其中包含更详细的状态信息

* 引入了反向翻译记忆库更新，以在AEM中对本地内容进行编辑后，更新第三方翻译管理系统中的翻译记忆库
* 翻译工作流现在支持分组语言根
* 添加了将任意名称分配给语言根以及使用JCR属性映射到ISO代码的功能
* 智能翻译更新现在可识别已添加到语言主控分支的新页面
* 在站点管理员列表视图中引入了翻译状态报表

### 多站点管理(MSM) {#multi-site-management-msm}

* 通过使用基于Oak的索引与内存(LiveCopyIndex)，改进了MSM可扩展性

### 启动项 {#launches}

* 改进了包含大型站点树且活动启动项数量较多时的启动项性能
* 改进了使用多个根页面自动提升和发布启动项的功能。
* 修复了导致响应式设备预览无法处理在启动项上下文中编辑的页面的问题。

### 内容定位和模拟 {#content-targeting-simulation}

* 支持文件夹根据站点/上下文组织区段(CQ-94620)
* 将区段的默认位置移到/conf中，以包含特定于站点/上下文的区段列表。

### AEM和Adobe Target  {#aem-amp-adobe-target-nbsp}

* 将AEM体验片段与Adobe Target集成。 将体验片段同步到Target将在Adobe Target中创建选件，这些选件可以与Target的可视化体验编辑器一起使用，以将其嵌入到任何启用了Target的体验中。
* Adobe Target mbox.js版本63现已包含在内。 Adobe建议将实施切换到at.js。
* 现已包含at.js版本1.2.2。 Adobe建议使用动态Tag Management(DTM)或 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) 将at.js配置到站点中。

### AEM和Adobe Analytics {#aem-amp-adobe-analytics}

* 现在包含s_code.js H.27.5。 Adobe建议将实施切换到AppMeasurement.js
* AppMeasurement.js 1.8.0现已包含在内。 Adobe建议使用动态Tag Management(DTM)或 [Adobe Experience Platform Launch](https://www.adobe.com/enterprise/cloud-platform/launch.html) 将AppMeasurement.js配置到网站中。

## Communities Add-On {#communities-add-on}

请参阅 [Communities发行说明页面](/help/release-notes/communities-release-notes.md)

## Screens附加组件 {#screens-add-on}

* 添加了对Screens播放器连接到AEM发布服务器以进行命令和控制以及渠道下载(而不是直接连接到AEM作者)的支持。
* 添加了在计划中对渠道分配进行分组的功能
* 渠道分配现在具有开始和结束日期
* 设备功能板现在显示播放器外壳和固件版本
* 设备功能板列表显示播放器的连接状态
* 添加了对Google Player的AEM Screens Chrome操作系统支持
* 添加了适用于Microsoft Player的AEM Screens Windows 10
