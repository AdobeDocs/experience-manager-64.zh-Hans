---
title: 集成问题疑难解答
seo-title: 集成问题疑难解答
description: 了解如何解决集成问题。
seo-description: 了解如何解决集成问题。
uuid: fe080e58-a855-4308-a611-f72eb47ba82d
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 422ee332-23ae-46bd-8394-a4e0915beaa2
translation-type: tm+mt
source-git-commit: a210d3bf80b7e7ec62c76a21f1cc2e71e986a4dc
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 1%

---


# 集成问题疑难解答{#troubleshooting-integration-issues}

## 一般疑难解答提示 {#general-troubleshooting-tips}

### 确保没有JavaScript错误 {#ensure-there-are-no-javascript-errors}

检查浏览器的JavaScript控制台是否显示任何错误。 未处理的错误可能会阻止后续代码正确执行。 如果有错误，请检查导致错误的脚本以及在哪个区域。 脚本的路径可能会指示脚本属于哪些功能。

### 在组件级别登录 {#logging-on-component-level}

在某些情况下，在组件级别添加其他语句可能会很有帮助。 由于渲染了组件，因此您可以添加临时标记来显示可能有助于识别潜在问题的变量值。 例如：

```
<%
log.info("myVariable={}", myVariable);
%>
  
<!--
<%= myJspVariable %>
-->

<!--
${ myHtlVariable }
-->
```

有关日志记录的其他详细信息，请 [参阅](/help/sites-deploying/configure-logging.md) “ [日志记录和使用审核记录和日志文件](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) ”页。

## Analytics集成问题 {#analytics-integration-issues}

### 报表导入程序导致CPU/内存使用率高 {#the-report-importer-causes-high-cpu-memory-usage}

报表导入程序导致CPU/内存使用率高或导致异 `OutOfMemoryError` 常。

#### Solution {#solution}

要解决此问题，可尝试：

* 确保注册的PollingImporter数量不大（请参阅下面的“由于PollingImporter的原因而关闭需要很长时间”部分）。
* 在一天的某个时间，使用OSGi控制台中的配置的CRON表达式 `ManagedPollingImporter` 运行报 [表导入器](/help/sites-deploying/configuring-osgi.md)。

有关在AEM中创建自定义数据导入程序服务的其他详细信息，请阅读以下文 [章https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html)。

### 由于轮询导入程序，关闭需要很长时间 {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

设计分析时考虑了继承机制。 通常，您可以通过在页面属性Cloud Services卡中添加对Analytics配置的引用来为站点启 [用Analytics](/help/sites-developing/extending-cloud-config.md) 。 然后，该配置会自动继承到所有子页面，无需再次引用它，除非页面需要其他配置。 添加对站点的引用还会自动创建多个节点(AEM 6.3及更早版本的节点12或AEM 6.4的节点6)，这些节点将实例化用于将Analytics数据导入AEM `cq;PollConfig` 的PollingImporters。 因此：

* 如果有大量引用Analytics的页面，则会导致大量的PollingImporter。
* 此外，复制并粘贴引用Analytics配置的页面会导致复制其PollingImporters。

#### Solution {#solution-1}

首先，分析 [error.log](/help/sites-deploying/configure-logging.md) 可能会让您对活动或已注册的PollingImporter的数量有所了解。 例如：

```
# Count PollingImporter entries
$ sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\),interval.*/\1/p" error.log | wc -l
86415
# Count PollingImporter entries for last30days
$ sed -n "s/.*(aem-analytics-integration-last30Days).*target=\(.*\),interval.*/\1/p" error.log | wc -l
14531
# Count unique paths of PollingImporter registrations
sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\)\/jcr:content.*/\1/p" error.log | sort | uniq -c
28115
```

其次，确保只有顶级页面（在层次结构中较高）引用了Analytics配置。

有关在AEM中创建自定义数据导入程序服务的其他详细信息，请阅读以下文 [章https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html)。

## DTM（旧版）问题 {#dtm-legacy-issues}

### DTM脚本标记不呈现在页面源中 {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

DTM [脚本](/help/sites-administering/dtm.md) 标记未正确包含在页面中，即使配置已在页面属性Cloud Services选项卡中引 [用](/help/sites-developing/extending-cloud-config.md) 。

#### Solution {#solution-2}

要解决此问题，可尝试：

* 确保加密的属性可以解密(请注意，加密可能在每个AEM实例上使用不同的自动生成的密钥)。 有关其他详细信息，请阅 [读配置属性的加密支持](/help/sites-administering/encryption-support-for-configuration-properties.md)。
* 重新发布在 `/etc/cloudservices/dynamictagmanagement`
* 检查ACL `/etc/cloudservices`。 ACL应为：

   * 允许； jcr:read; webservice-support-servicelibfinder
   * 允许； jcr:read; 每个人； rep:glob:&amp;ast;/defaults/&amp;ast;
   * 允许； jcr:read; 每个人； rep:glob:&amp;ast;/defaults
   * 允许； jcr:read; 每个人； rep:&amp;ast;/public/&amp;ast;
   * 允许； jcr:read; 每个人； rep:glob:&amp;ast;/public

有关管理ACL的详细信息，请阅读“用 [户管理和安全](/help/sites-administering/security.md#permissions-in-aem) ”页。

## 目标集成问题 {#target-integration-issues}

### 使用自定义页面组件时，目标内容在预览模式下不可见 {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

出现此问题的原因是自定义页面组件不包含处理目标DTM集成的正确JSP或客户端库。

#### Solution {#solution-3}

您可以尝试以下解决方案：

* 确保自定义( `headlibs.jsp` 如果有 `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`)包括以下内容：

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* 确保自定义(如 `head.html` 果有) `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`不 **会选择性地包** 含特定的集成头像，如下面的示例所示：

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

将 `servicelibs.jsp` 添加所需的分析JavaScript对象并加载与网站相关的云服务库。 对于目标服务，库通过 `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

加载的库集取决于目标配置上使用的目标客户 `mbox.js` 端库 `at.js`的类型（或）。

使用DTM传送 `mbox.js` 或 `at.js` 确保在渲染内容之前加载库。 使用异步加载这些库的标签管理系统可能会导致执行目标特定JavaScript代码时出现问题。

有关其他信息，请阅 [读为目标内容开发](/help/sites-developing/target.md#understanding-the-target-component) 页。

### 浏览器控制台中显示错误“AppMeasurement初始化中缺少报表包ID” {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

当使用DTM在网站上实现Adobe Analytics并使用自定义代码时，可能会出现此问题。 原因是使用 `s = new AppMeasurement()` 实例化对 `s` 象。

#### Solution {#solution-4}

使用 `s_gi` 而不是实例 `new AppMeasurement` 化方法。 例如：

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### 默认优惠会随机显示，而不是正确的优惠 {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

此问题可能有多个原因：

* 使用第三方标签管 `mbox.js` 理系 `at.js`统异步加载目标客户端库（或）可能会随机中断定位。 目标库应同步加载到页面头中。 从AEM提供库时，这一点始终如一。

* 同时加载两个目标客 `at.js`户端库()，例如，一个使用DTM，另一个使用AEM中的目标配置。 如果版本不同，这可 `adobe.target` 能会导致定义 `at.js` 冲突。

#### Solution {#solution-5}

您可以尝试以下解决方案：

* 确保加载类似DTM的库(依次加载目标库)的客户代码在页面头中同 [步执行](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages)。
* 如果将站点配置为使用DTM传送目标库，则确保 **在站点的目标配置中** ，选中由DTM [传送的Clientlib](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) 。

### 使用AT.js 1.3+时，始终显示默认优惠，而不是正确的优惠 {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

现成的AEM 6.2和6.3与AT.js版本1.3.0+不兼容。 AT.js版本1.3.0引入了API的参数验证 `adobe.target.applyOffer()` ，要求代码未提供“mbox”参 `atjs-itegration.js` 数。

#### Solution {#solution-6}

要解决此问题，请 `atjs-itegration.js` 编辑并在 `"mbox": mboxName` 参数对象中添加字段， `adobe.target.applyOffer()` 如下所示：

```
adobe.target.getOffer({
    "mbox": mboxName,
    "params": params,
    "success": function (response) {
        adobe.target.applyOffer({
            "mbox": mboxName, //<--- ADDED PARAM
            "selector": "#" + mboxName,
            "offer": response
        })
    },
```

### “目标和设置”页面不显示“报告源”部分 {#the-goals-settings-page-does-not-show-the-reporting-sources-section}

此问题很可能是A4T [Analytics Cloud配置设置问题](/help/sites-administering/target-configuring.md) 。

#### Solution {#solution-7}

您需要通过向AEM发出以下验证请求来验证目标帐户是否正确启用了A4T:

```
http://localhost:4502/etc/cloudservices/testandtarget/<YOUR-CONFIG>/jcr:content.a4t.json
 
{
    "a4tEnabled": true,
    "sharedsecret": "SECRET",
    "proxyUrl": "/libs/cq/contentinsight/content/proxy.reportingservices.json",
    "active": "true",
    "pageName": "",
    "url": "https://api5.omniture.com/rs/0.5/",
    "username": "USER@DOMAIN"
}
```

如果响应包含此行，请 `a4tEnabled:false`联系Adobe [客户关怀](https://helpx.adobe.com/contact.html) ，以正确设置您的帐户。

### 实用的目标API {#helpful-target-apis}

以下是两个目标API，在对目标问题进行故障诊断时，这些API可能会很有用：

* 检索给定客户端代码的目标端点

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json
 
{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* 检索客户端的用户档案

```
https://admin<N>.testandtarget.omniture.com/admin/rest/v1/clients/<CLIENT>?email=<EMAIL>&password=<PASSWORD>
 
Response for N=4, CLIENT-dayintegrationintern
{
    "clientCode": "dayintegrationintern",
    "companyName": "Day Integration - Internal",
    "omnitureCompanyId": "Day Integration Internal",
    "softTraxId": -1,
    "address1": "XYZ",
    "city": "San Francisco",
    "state": "ca",
    "zip": "94107",
    "country": "UNITED STATES",
    "locale": "de_DE",
    "timeZone": "Europe/Berlin",
    "phone": "XX-XX-XXXX",
    "serviceLevel": "Up to 100,000",
    "privileges": [
        "a4t",
        "hosts",
        "TnT-SC-integration",
        "mvt",
        "steps",
        "testing-campaigns",
        "view-snapshot",
        "on-site-editor",
        "optimizing-campaign",
        "third-party-id-support",
        "landing-page-campaigns",
        "segment",
        "rest-create-user",
        "advanced-targeting",
        "mobile-device-targeting",
        "beta",
        "geolocation"
    ]
}
```

