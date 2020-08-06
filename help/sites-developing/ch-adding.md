---
title: 将ContextHub添加到页面和访问商店
seo-title: 将ContextHub添加到页面和访问商店
description: 将ContextHub添加到您的页面以启用ContextHub功能并链接到ContextHub Javascript库
seo-description: 将ContextHub添加到您的页面以启用ContextHub功能并链接到ContextHub Javascript库
uuid: ade37960-21c4-4d64-a525-68f0d199f955
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: ac8f44df-39fb-44ea-ae17-ead0dbd1f6c0
translation-type: tm+mt
source-git-commit: 39b6af8ee815e8f6fa6e0b4a0a6dc80f29165243
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---


# 将ContextHub添加到页面和访问商店 {#adding-contexthub-to-pages-and-accessing-stores}

将ContextHub添加到您的页面以启用ContextHub功能并链接到ContextHub Javascript库

ContextHub Javascript API提供对ContextHub管理的上下文数据的访问。 本页简要介绍了用于访问和操作上下文数据的API的主要功能。 按照指向API参考文档的链接查看详细信息和代码示例。

## 将ContextHub添加到页面组件 {#adding-contexthub-to-a-page-component}

要启用ContextHub功能并链接到ContextHub Javascript库，请在页面的部分包含 `head` contexthub组件。 页面组件的JSP代码类似于以下示例：

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
</head>
```

请注意，您还需要配置ContextHub工具栏是否以预览模式显示。 请参 [阅显示和隐藏ContextHub UI](/help/sites-administering/contexthub-config.md#showing-and-hiding-the-contexthub-ui)。

## 关于ContextHub存储 {#about-contexthub-stores}

使用ContextHub存储保留上下文数据。 ContextHub提供以下类型的存储，这些存储构成了所有存储类型的基础：

* [PersistedStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)
* [SessionStore](/help/sites-developing/contexthub-api.md#contexthub-store-sessionstore)
* [JSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedjsonpstore)
* [PersitedJSONPStore](/help/sites-developing/contexthub-api.md#contexthub-store-persistedstore)

所有存储类型都是类的扩 [`ContextHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) 展。 有关创建新商店类型的信息，请参阅创 [建自定义商店](/help/sites-developing/ch-extend.md#creating-custom-store-candidates)。 有关示例存储类型的信息，请参 [阅示例ContextHub存储候选项](/help/sites-developing/ch-samplestores.md)。

### 持久性模式 {#persistence-modes}

Context Hub存储区使用以下持久性模式之一：

* **本地：** 使用HTML5 localStorage保留数据。 本地存储会跨会话在浏览器上保留。
* **会话：** 使用HTML5 sessionStorage保留数据。 会话存储在浏览器会话的持续时间内持续存在，并且可用于所有浏览器窗口。
* **Cookie:** 使用浏览器对cookie的本机支持进行数据存储。 在HTTP请求中，Cookie数据会发送到服务器或从服务器发送。
* **Window.name:** 使用window.name属性保留数据。
* **内存：** 使用Javascript对象保留数据。

默认情况下，Context Hub使用本地持久性模式。 如果浏览器不支持或允许HTML5 localStorage，则使用会话持久性。 如果浏览器不支持或允许HTML5 sessionStorage，则使用Window.name持久性。

### 存储数据 {#store-data}

在内部，存储数据以树形结构的形式，使值能够添加为主类型或复杂对象。 在向存储添加复杂对象时，对象属性在数据树中形成分支。 例如，以下复杂对象将添加到名为location的空存储区：

```xml
Object {
   number: 321,
   data: {
      city: "Basel",
      country: "Switzerland",
      details: {
         population: 173330,
         elevation: 260
      }
   }
}
```

存储数据的树结构可以概念化为：

```xml
/
|- number
|- data
      |- city
      |- country
      |- details
            |- population
            |- elevation
```

树结构将存储中的数据项定义为键／值对。 在上例中，键与 `/number` 值对应， `321`键与 `/data/country` 值对应 `Switzerland`。

### 处理对象 {#manipulating-objects}

ContextHub提供用 [`ContextHub.Utils.JSON.tree`](/help/sites-developing/contexthub-api.md#contexthub-utils-json-tree) 于处理Javascript对象的类。 在将Javascript对象添加到商店或从商店获取它们之前，使用此类的函数来处理这些对象。

此外，该类 [`ContextHub.Utils.JSON`](/help/sites-developing/contexthub-api.md#contexthub-utils-json) 还提供用于对对象进行序列化和对对象反序列化字符串的函数。 使用此类处理JSON数据以支持本机不包含和函数的 `JSON.parse` 浏 `JSON.stringify` 览器。

## 与ContextHub存储区交互 {#interacting-with-contexthub-stores}

使用Javascript [`ContextHub`](/help/sites-developing/contexthub-api.md#ui-event-constants) 对象将存储作为Javascript对象获取。 获得存储对象后，您可以处理它包含的数据。 使用 [`getAllStores`](/help/sites-developing/contexthub-api.md#getallstores) 或函 [`getStore`](/help/sites-developing/contexthub-api.md#getstore-name) 数获取存储。

### 访问存储数据 {#accessing-store-data}

Javascript [`ContexHub.Store.Core`](/help/sites-developing/contexthub-api.md#contexthub-store-core) 类定义与存储数据交互的多个函数。 以下函数存储和检索对象中包含的多个数据项：

* [addAllItems](/help/sites-developing/contexthub-api.md#addallitems-tree-options)
* [getTree](/help/sites-developing/contexthub-api.md#gettree-includeinternals)

单个数据项作为一组键／值对进行存储。 要存储和检索值，请指定相应的键：

* [getItem](/help/sites-developing/contexthub-api.md#getitem-key)
* [setItem](/help/sites-developing/contexthub-api.md#setitem-key-value-options)

请注意，自定义存储候选者可以定义提供存储数据访问权限的其他函数。

>[!NOTE]
>
>默认情况下，ContextHub不知道当前在发布服务器上使用的登录名，ContextHub将这些用户视为“匿名”。
>
>通过加载We.Retail参考站点中实现的用户档案存储，可以使ContextHub了解 [已登录的用户](/help/sites-developing/we-retail.md)。 请在此处 [参阅GitHub上的相关代码](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/blob/master/ui.apps/src/main/content/jcr_root/apps/weretail/components/structure/header/clientlib/js/utilities.js)。

### ContextHub事件 {#contexthub-eventing}

ContextHub包含一个事件框架，它允许您对存储事件做出自动响应。 每个存储对象都 [`ContextHub.Utils.Eventing`](/help/sites-developing/contexthub-api.md#contexthub-utils-eventing) 包含一个可用作存储属性的 [`eventing`](/help/sites-developing/contexthub-api.md#eventing) 对象。 使用或 [`on`](/help/sites-developing/contexthub-api.md#on-name-handler-selector-triggerforpastevents) 函 [`once`](/help/sites-developing/contexthub-api.md#once-name-handler-selector-triggerforpastevents) 数将Javascript函数绑定到存储事件。

## 使用Context Hub操纵Cookie {#using-context-hub-to-manipulate-cookies}

Context Hub Javascript API提供跨浏览器支持以处理浏览器cookie。 该命名空间 [`ContextHub.Utils.Cookie`](/help/sites-developing/contexthub-api.md#contexthub-utils-cookie) 定义了用于创建、处理和删除Cookie的多个函数。

## 确定已解析的ContextHub区段 {#determining-resolved-contexthub-segments}

ContextHub区段引擎允许您确定在当前上下文中解析的已注册区段。 使用类的getResolvedSegments函 [`ContextHub.SegmentEngine.SegmentManager`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segmentmanager) 数检索已解析的段。 然后，使用 `getName` 类 `getPath` 的或 [`ContextHub.SegmentEngine.Segment`](/help/sites-developing/contexthub-api.md#contexthub-segmentengine-segment) 函数测试段。

### 已安装的区段 {#installed-segments}

ContextHub区段安装在节点 `/conf/we-retail/settings/wcm/segments` 下。

* 女
* 女30岁以上
* 女30岁以下
* 男
* 男30岁以上
* 男30岁以下
* order-value-75-to-100
* 订单价值超过100
* 超过30
* 夏
* 夏女
* 夏季——女30岁以上
* 夏季——女30岁以下
* 夏季男性
* 夏季男性30岁以上
* 夏季男性30岁以下
* 30岁以下
* 冬
* 冬女
* 冬季——女性-30岁以上
* 冬——女-30岁以下
* 冬男
* 冬季男30岁以上
* 冬季男性20岁以下

用于解析这些区段的规则概述如下：

* 从用户档案存储器的 `gender` 数据项确定 [女性](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) 。

* 根据用户档案存储的年龄数据项确定年龄。
* 季节根据地理位置存储的纬 [度](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) 数据项和surferinfo存储的月份数据项确定。

>[!WARNING]
>
>安装的区段会作为参考配置提供，以帮助您为项目构建自己的专用配置，因此不应直接使用。

## 记录ContextHub的调试消息 {#logging-debug-messages-for-contexthub}

配置AdobeGranite ContextHub OSGi服务(PID =) `com.adobe.granite.contexthub.impl.ContextHubImpl`以记录详细的调试消息，这些消息在开发时很有用。

要配置服务，您可以使用Web [控制台](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) ，或 [在存储库中使用JCR节点](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* Web控制台： 要记录调试消息，请选择调试属性。
* JCR节点： 要记录调试消息，请将布尔 `com.adobe.granite.contexthub.debug` 属性设 `true`置为。

## 请参阅ContextHub Framework概述 {#see-an-overview-of-the-contexthub-framework}

ContextHub提供 [诊断页](/help/sites-developing/ch-diagnostics.md) ，您可以在其中看到ContextHub框架的概述。
