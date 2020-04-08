---
title: 已弃用和已删除的功能
seo-title: 已弃用和已删除的功能
description: 以下发行说明特定于 Adobe Experience Manager 6.4 中已弃用和已删除功能。
seo-description: 以下发行说明特定于 Adobe Experience Manager 6.4 中已弃用和已删除功能。
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: 3316dbc8ef268be2b305d22da9003ae40414b4e1

---


# 已弃用和已删除的功能 {#deprecated-and-removed-features}

Adobe 不断评估产品功能，以便随着时间的推移，使用更现代的替代方案重塑或替换旧功能，从而提高整体客户价值，此过程中将始终谨慎考虑功能的向后兼容性。

为了传达即将删除/替换 AEM 功能，以下规则适用：

1. 首先宣布弃用。虽然已弃用，但功能仍可用，只是不会进一步增强。
1. 最早将在以下主要发行版中删除已弃用的功能。将宣布实际删除目标的日期。

在实际删除之前，此过程将为客户提供至少一个发行周期时间，使其实施适应已弃用功能的新版本或后续版本。

## 已弃用功能 {#deprecated-features}

本部分列出了 AEM 6.4 中已标记为弃用的特性和功能。通常，计划在未来发行版中删除的特性将首先设置为弃用，并提供备用方案。

建议客户检查其当前部署中是否使用了此类特性/功能，然后制定相应的计划以将其实施更改为使用提供的备选方案。

<table> 
 <tbody>
  <tr>
   <td>区域</td> 
   <td>功能</td> 
   <td>替换</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe 不打算进一步增强经典 UI。AEM 6.4 包含经典 UI，从早期发行版升级的客户可以继续按原样使用它。请注意，经典 UI 在弃用期间仍完全受支持。 </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/标记</li> 
     <li>/cf#（页面编辑器）</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>建议客户切换使用新的AEM UI。</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>组件</td> 
   <td><p>Adobe不计划对下面列出的基础组件进行进一步的增强。 AEM 6.4包含基础组件，从早期版本升级的客户可以按原样继续使用它们。 请注意，在弃用时，基础组件仍完全受支持。 </p> 
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
   <td>建议客户在未来的项目中使用核心组件。无需更改现有站点。</td> 
  </tr>
  <tr>
   <td>组件</td> 
   <td><p>Adobe不计划对下面列出的基础组件进行进一步的增强。 AEM 6.4包含基础组件，从早期版本升级的客户可以按原样继续使用它们。 请注意，在弃用时，基础组件仍完全受支持。</p> 
    <ul> 
     <li>基础／组件／时间</li> 
    </ul> </td> 
   <td>在编写时，它并不打算提供替代。</td> 
  </tr>
  <tr>
   <td>门户控制器</td> 
   <td><p>门户控制器是一组功能，它允许通过第三方服务器中的Portlet托管AEM内容。</p> <p>Adobe不打算在以下列出的位置进一步增强门户控制器功能。 AEM 6.4包含Portal Director，从早期版本升级的客户可以按原样继续使用它。 请注意，弃用Portal Direct时仍完全受支持。</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>在编写时，它并不打算提供替代。</td> 
  </tr>
  <tr>
   <td>Portlet组件</td> 
   <td><p>/foundation/components/portlet下的Portlet组件支持将AEM中的JSR Portlet作为组件进行托管。</p> <p>Adobe不打算进一步增强Portlet组件功能。 AEM 6.4包含Portlet组件，从早期版本升级的客户可以按原样继续使用它。 请注意，Portlet组件在被弃用时仍完全受支持。</p> </td> 
   <td>在编写时，它并不打算提供替代。</td> 
  </tr>
  <tr>
   <td>表单</td> 
   <td><p>由于不再支持Adobe Central产品，因此已弃用对Adobe Central Migration Bridge服务的支持。</p> </td> 
   <td>无替换项 </td> 
  </tr>
    <tr>
   <td>表单</td> 
   <td><p>已弃用在查询和OperationOptions中使用JSONObject。 已弃用以下API:
   <ul><li>setArguments（JSONObject参数）</li><li>JSONObject getArguments()</li><li>OperationOptions（String operationId, JSONObject参数）</li><li>JSONObject getArguments()</li><li>void setArguments（JSONObject参数）</li></ul>
   </p> </td> 
   <td>使用IValueMap API </td> 
  </tr>
  <tr>
   <td>资产</td> 
   <td><p>从AEM 6.4开始，已弃用资产卸载功能</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 已删除功能 {#removed-features}

本节列表了已从AEM 6.4中删除的特性和功能。先前发行版具有标记为已弃用的这些功能。

<table> 
 <tbody>
  <tr>
   <td><strong>区域</strong></td> 
   <td><strong>功能</strong></td> 
   <td><strong>替换</strong></td> 
  </tr>
  <tr>
   <td>分析活动图</td> 
   <td>AEM中包含的活动图版本。</td> 
   <td>由于 Adobe Analytics API 中的安全性更改，因此无法再使用 AEM 中包含的 Activity Map 版本。<br><br>现 <a href="https://docs.adobe.com/content/help/zh-Hans/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">在应使用Adobe Analytics提供的</a> ActivityMap插件。</td> 
  </tr>
  <tr>
   <td>组件</td> 
   <td>表单Captcha<br /> (foundation/components/form/captcha)</td> 
   <td>请改用Google的ReCaptcha组件</td> 
  </tr>
  <tr>
   <td>组件</td> 
   <td>幻灯片放映<br /> （基础／组件／幻灯片放映）</td> 
   <td>无替换项</td> 
  </tr>
  <tr>
   <td>组件</td> 
   <td>Flash<br /> (foundation/components/flash)</td> 
   <td>无替换项</td> 
  </tr>
  <tr>
   <td>组件</td> 
   <td>删除了对在视频组件(foundation/components<br /> /video)中回放SWF文件的支持</td> 
   <td>使用无Flash视频格式。</td> 
  </tr>
  <tr>
   <td>组件</td> 
   <td>产品表<br /> (commerce/components/product_table)</td> 
   <td>无替换项</td> 
  </tr>
  <tr>
   <td>任务管理</td> 
   <td>经典UI任务管理<br /> (/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>自6.0起已弃用。使用与工作流UI结合的新任务管理。</td> 
  </tr>
  <tr>
   <td>工作流</td> 
   <td>在5.6-6.2之间使用的通知UI<br /> (/libs/cq/workflow/content/notifications.html)</td> 
   <td>工作流收件箱/aem/inbox</td> 
  </tr>
  <tr>
   <td>表单</td> 
   <td>已删除使用PDF生成器将PDF导出为PDF/E-1格式。</td> 
   <td>PDF Generator继续支持将PDF导出为PDF/A-1a/b、PDF/A-2a/b和PDF/A-3a/b格式。</td> 
  </tr>
  <tr>
   <td>表单</td> 
   <td>已删除自适应表单中对默认AEM Captcha服务的支持。 </td> 
   <td>请改用Google提供的ReCaptcha。</td> 
  </tr>
  <tr>
   <td>表单</td> 
   <td>已删除对文档片段内图像的支持。 </td> 
   <td>交互式通信提供了在印刷和Web渠道中直接使用图像的功能。<br /> </td> 
  </tr>
    <tr>
   <td>表单</td> 
   <td> 现场升级 </td> 
   <td>不提供异地升级支持 <br/> </td> 
  </tr>
  <tr>
   <td>表单</td> 
   <td> TarMK到DocumentMK迁移的侧传 </td> 
   <td> 您可以从旧系统中导出数据，然后导入到新安装的系统中。 有关详细说明，请参阅JEE上的AEM Forms升级文档 <br/> </td> 
  </tr>
    <tr>
   <td>表单</td> 
 <td>JEE 32位安装程序上的AEM Forms不可用。</td> 
   <td>Adobe已停止在JEE 32位安装程序上提供AEM Forms。 您可以继续使用64位安装程序在JEE上安装AEM Forms。 </td>  
  </tr>
    <tr>
    <td>表单</td> 
    <td>删除了在文档片段组件中使用DAM图像的支持。</td> 
    <td> 您可以在交互式通信的打印渠道中使用图像和图表组件。 如果您在自适应表单中使用自适应文档的文档片段组件，则在升级到AEM 6.4表单后，它将停止工作。 </td>  
  </tr>
  <tr>
   <td>表单</td> 
   <td> 删除了自适应文档功能</td> 
   <td> 您可以使用交互式通信功能创建基于Web的印刷通信。 如果您使用自适应文档，请安装兼容性包以继续使用现有的自适应文档<br/> </td> 
  </tr>
    <tr>
    <td>表单</td> 
    <td>删除了JEE特定登陆页上的AEM Forms。</td> 
    <td>JEE登陆页上的AEM Forms将替换为AEM登陆页(/aem/start.html) </td>  
  </tr>
   <tr>
   <td>表单</td> 
   <td>删除了对默认Captcha的支持</td> 
   <td>使用Google提供的reCAPTCHA服务。</td> 
  </tr>
   <tr>
   <td>表单</td> 
   <td>删除了对默认Captcha的支持</td> 
   <td>使用Google提供的reCAPTCHA服务。</td> 
  </tr>
  <tr>
   <td>社区</td> 
   <td>已取消对Captcha验证的支持。</td> 
   <td>使用自定义captcha集成（如Google的reCAPTCHA）进行验证。</td> 
  </tr>
 </tbody>
</table>

## 针对下一个发行版的预先宣布 {#pre-announcement-for-next-release}

此部分用于预先宣布未来发行版中的更改，这些更改未弃用，但会影响客户。以下内容为规划目的而提供。

<table> 
 <tbody>
  <tr>
   <td>区域<br /> </td> 
   <td>功能<br /> </td> 
   <td>宣布</td> 
  </tr>
  <tr>
   <td>浏览器支持</td> 
   <td>Microsoft Internet Explorer</td> 
   <td>AEM 6.4是支持Microsoft Internet Explorer 11的最后一个版本。</td> 
  </tr>
  <tr>
   <td>Foundation</td> 
   <td>UI 框架</td> 
   <td>Adobe在2019年弃用了Coral UI 2组件。 AEM 6.4完全基于Coral UI 3（随AEM 6.2一起引入）。 Adobe建议其已使用Coral 2构建自定义UI的客户和合作伙伴将这些UI重构到Coral 3。 Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - <a href="/help/sites-developing/dialog-conversion.md">Read more</a>.</td> 
  </tr>
 </tbody>
</table>
