---
title: 已弃用和已删除的功能
description: 以下发行说明特定于 Adobe Experience Manager 6.4 中已弃用和已删除功能。
exl-id: 2fe0dad7-fc78-4aac-afa3-79a278008453
source-git-commit: dcc36e499517f3f35d5f1d849802c4a5c35121bd
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 26%

---

# 已弃用和已删除的功能 {#deprecated-and-removed-features}

Adobe 不断评估产品功能，以便随着时间的推移，使用更现代的替代方案重塑或替换旧功能，从而提高整体客户价值，此过程中将始终谨慎考虑功能的向后兼容性。

为了传达即将删除/替换 AEM 功能，以下规则适用：

1. 首先宣布弃用。虽然已弃用，但功能仍然可用，但不会进一步增强。
1. 最早将在以下主要发行版中删除已弃用的功能。将宣布实际删除目标的日期。

在实际删除之前，此过程将为客户提供至少一个发行周期时间，使其实施适应已弃用功能的新版本或后续版本。

## 已弃用功能 {#deprecated-features}

下表列出了AEM 6.4中标记为已弃用的特性和功能。通常，计划在未来版本中删除的特性首先设置为已弃用，并提供替代功能。

建议客户检查其当前部署中是否使用了此类特性/功能，然后制定相应的计划以将其实施更改为使用提供的备选方案。

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| 区域 | 功能 | 替换 |
|---|---|---|
| UI | Adobe 不打算进一步增强经典 UI。AEM 6.4 包含经典 UI，从早期发行版升级的客户可以继续按原样使用它。请注意，经典 UI 在弃用期间仍完全受支持。 <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (页面编辑器) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | 建议客户切换以使用新的AEM UI。 |
| 组件 | Adobe不打算进一步增强下面列出的基础组件。 AEM 6.4中包含Foundation组件，从早期版本升级的客户可以按原样继续使用它们。 请注意，基础组件在弃用期间仍完全受支持。 <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordreset </li> <li> foundation/components/account/requestconfirmation </li> <li> 基础/组件/自适应图像 </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/痕迹导航 </li> <li> 基金会/组件/表单/信用卡 </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> 基础/组件/表 </li> <li> foundation/components/工具栏 </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | 建议客户在未来的项目中使用核心组件。无需更改现有网站。 |
| 组件 | Adobe不打算进一步增强下面列出的基础组件。 AEM 6.4中包含Foundation组件，从早期版本升级的客户可以按原样继续使用它们。 请注意，基础组件在弃用期间仍完全受支持。 <ul><li>基础/组件/时间</li></ul> | Adobe不打算提供替换。 |
| 门户Director | Portal Director是一组功能，它允许通过Portlet在第三方服务器中托管AEM内容。 Adobe不打算进一步增强下面所列位置下的Portal Director功能。 AEM 6.4包含Portal Director，从早期版本升级的客户可以继续按原样使用它。 请注意，弃用Portal Direct时仍完全支持。 <ul><li>/libs/portal/director</li></ul> | Adobe不打算提供替换。 |
| Portlet组件 | /foundation/components/portlet下的Portlet组件允许将AEM中的JSR Portlet作为组件进行托管。 Adobe不打算进一步增强Portlet组件功能。 AEM 6.4包含Portlet组件，从早期版本升级的客户可以按原样继续使用它。 请注意，Portlet组件在弃用时仍完全受支持。 | Adobe不打算提供替换。 |
| 表单 | 已弃用对Adobe中心迁移桥服务的支持，因为不再支持Adobe中心产品。 | 无替换项 |
| 表单 | 已在查询和操作选项中弃用JSONObject 。 已弃用以下API: <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | 使用`IValueMap` API |
| 表单 | 已弃用的Central Migration Bridge服务。 | 不提供任何替换。 |
| 资产 | 从AEM 6.4开始，已弃用Assets卸载。 |  |
| 开发人员 | Lodash/下划线客户端库。 Adobe不打算进一步维护和更新作为分发版（快速入门）一部分提供的Lodash/下划线客户端库 | Adobe建议仍要求代码使用长划线/下划线的客户将其添加到项目代码库中。 |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## 已删除功能 {#removed-features}

下表列出了从AEM 6.4中删除的特性和功能。以前版本的这些功能标记为
已弃用。

| 区域 | 功能 | 替换 |
|---|---|---|
| 与[!DNL Experience Cloud]集成 | 您可以通过[!DNL Adobe I/O]配置，将资产与[!DNL Experience Cloud]同步。 [!DNL Adobe Experience Cloud] 以前称为 [!DNL Adobe Marketing Cloud]。 | 如果您有任何查询，请联系[Adobe客户支持](https://experienceleague.adobe.com/?support-solution=General#support)。 |
| Analytics Activity Map | AEM 中包含的 Activity Map 的版本。 | 由于 Adobe Analytics API 中的安全性更改，无法再使用 AEM 中包含的 Activity Map 版本。现在，应使用Adobe Analytics](https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html)提供的[ActivityMap插件。 |
| 组件 — Forms | 表单验证码（基础/组件/表单/验证码） | 请改用ReCaptcha by Google组件 |
| 组件 | 幻灯片放映（基础/组件/幻灯片放映） | 无替换项 |
| 组件 | Flash(foundation/components/flash) | 无替换项 |
| 组件 | 删除了对视频组件（基础/组件/视频）中播放SWF文件的支持 | 使用基于无闪存的视频格式。 |
| 组件 | 产品表(commerce/components/product_table) | 无替换项 |
| 任务管理 | 经典UI任务管理(/libs/cq/taskmanagement/content/taskmanager.html) | 自6.0起已弃用。请使用与工作流UI结合的新任务管理。 |
| 工作流 | 5.6 - 6.2 之间使用的通知 UI  (/libs/cq/workflow/content/notifications.html) | 工作流收件箱 /aem/inbox |
| 表单 | Export PDF到PDF/E-1格式(使用PDF生成器)已被删除。 | PDF生成器继续支持将PDF导出为PDF/A-1a/b、PDF/A-2a/b和PDF/A-3a/b格式。 |
| 表单 | 删除了对文档片段中图像的支持。 | 交互式通信提供了直接在打印和Web渠道中使用图像的功能。 |
| 表单 | 无法就地升级 | 不提供异地升级支持 |
| 表单 | TarMK到DocumentMK迁移的边级 | 您可以从旧系统中导出数据，然后在全新安装的系统中导入。 有关详细说明，请参阅JEE上的AEM Forms升级文档 |
| 表单 | AEM Forms on JEE 32位安装程序不可用。 | Adobe已停止在JEE 32位安装程序上发送AEM Forms。 您可以继续使用64位安装程序在JEE上安装AEM Forms。 |
| 表单 | 删除了对在文档片段组件中使用DAM图像的支持。 | 您可以在交互式通信的打印渠道中使用图像和图表组件。 如果您在自适应表单中使用自适应文档的文档片段组件，则它在升级到AEM 6.4 Forms后停止工作。 |
| 表单 | 删除了自适应文档功能 | 您可以使用交互式通信功能创建打印和基于Web的通信。 如果您使用自适应文档，请安装兼容包以继续使用现有的自适应文档 |
| 表单 | 在特定于JEE的登陆页面上删除了AEM Forms。 | AEM Forms on JEE登录页面已替换为AEM登录页面(/aem/start.html) |
| 表单 | 删除了对默认验证码的支持 | 使用由Google提供的reCAPTCHA服务。 |
| 表单 | 删除了对AEM Designer中Flash字段的支持。 AEM Designer不允许编辑表单中使用的Flash字段。 | 您可以使用为以前版本发布的AEM Designer来编辑此类表单。 |
| 社区 | 已删除对验证码的支持。 | 使用自定义验证码集成(例如Google的reCAPTCHA)进行验证。 |

## 针对下一个发行版的预先宣布 {#pre-announcement-for-next-release}

下表列出了未弃用但可能影响客户的未来版本更改列表。 以下内容为规划目的而提供。

| 区域 | 功能 | 公告 |
|---|---|---|
| 浏览器支持 | Microsoft Internet Explorer | AEM 6.4是支持Microsoft Internet Explorer 11的最新版本。 |
| Foundation | UI 框架 | Adobe将在2019年弃用Coral UI 2组件。 AEM 6.4完全基于Coral UI 3(在AEM 6.2中引入)。 Adobe建议已使用Coral 2构建自定义UI的客户和合作伙伴将这些UI重构到Coral 3。 Adobe提供了将Coral 2对话框转换为Coral 3的工具 — [阅读更多。](/help/sites-developing/modernization-tools.md) |
