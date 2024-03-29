---
title: 将Adobe Analytics跟踪添加到组件
seo-title: Adding Adobe Analytics Tracking to Components
description: 将Adobe Analytics跟踪添加到组件
seo-description: null
uuid: 447b140c-678c-428d-a1c9-ecbdec75cd42
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: a11c39b4-c23b-4207-8898-33aea25f2ad0
exl-id: f3926a15-4378-464f-968f-661745af117c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1299'
ht-degree: 0%

---

# 将Adobe Analytics跟踪添加到组件{#adding-adobe-analytics-tracking-to-components}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 在页面组件中包含Adobe Analytics模块 {#including-the-adobe-analytics-module-in-a-page-component}

页面模板组件(例如 `head.jsp, body.jsp`)需要包含JSP才能加载ContextHub和Adobe Analytics集成(这是Cloud Services的一部分)。 所有文件都包含加载的JavaScript文件。

ContextHub条目应包含在 `<head>` 标记中，而Cloud Services应包含在 `<head>` 和之前 `</body>` 部分；例如：

```xml
<head>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub" />
...
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
...
</head>
<body>
...
    <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
</body>
```

的 `contexthub` 在之后插入的脚本 `<head>` 元素会将ContextHub功能添加到页面。

的 `cloudservices` 您在 `<head>` 和 `<body>` 部分适用于添加到页面的云服务配置。 (如果页面使用多个Cloud Services配置，则只需包含一次ContextHub jsp和Cloud Servicesjsp。)

将Adobe Analytics框架添加到页面后， `cloudservices` 脚本会生成与Adobe Analytics相关的javascript和对客户端库的引用，如下例所示：

```xml
<div class="sitecatalyst cloudservice">
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/util.js"></script>
<script type="text/javascript" src="/content/geometrixx-outdoors/_jcr_content/analytics.sitecatalyst.js"></script>
<script type="text/javascript" src="/etc/clientlibs/mac/mac-sc.js"></script>
<script type="text/javascript" src="/etc/clientlibs/foundation/sitecatalyst/plugins.js"></script>
<script type="text/javascript">
<!--
CQ_Analytics.Sitecatalyst.frameworkComponents = ['foundation/components/page'];
/**
 * Sets Adobe Analytics variables accordingly to mapped components. If <code>options</code> 
 * object is provided only variables matching the options.componentPath are set.
 *
 * @param {Object} options Parameter object from CQ_Analytics.record() call. Optional.
 */
CQ_Analytics.Sitecatalyst.updateEvars = function(options) {
    this.frameworkMappings = [];
 this.frameworkMappings.push({scVar:"pageName",cqVar:"pagedata.title",resourceType:"foundation/components/page"});
    for (var i=0; i<this.frameworkMappings.length; i++){
  var m = this.frameworkMappings[i];
  if (!options || options.compatibility || (options.componentPath == m.resourceType)) {
   CQ_Analytics.Sitecatalyst.setEvar(m);
  }
    }
}

CQ_Analytics.CCM.addListener("storesinitialize", function(e) {
 var collect = true;
    var lte = s.linkTrackEvents;
    s.pageName="content:geometrixx-outdoors:en";
    CQ_Analytics.Sitecatalyst.collect(collect);
    if (collect) {
  CQ_Analytics.Sitecatalyst.updateEvars();
     /************* DO NOT ALTER ANYTHING BELOW THIS LINE ! **************/
     var s_code=s.t();if(s_code)document.write(s_code);
     s.linkTrackEvents = lte;
     if(s.linkTrackVars.indexOf('events')==-1){delete s.events};
     $CQ(document).trigger("sitecatalystAfterCollect");
    }
});
//-->
</script>
<script type="text/javascript">
<!--
if(navigator.appVersion.indexOf('MSIE')>=0)document.write(unescape('%3C')+'\!-'+'-')
//-->
</script>
<noscript><img src="https://daydocumentation.112.2o7.net/b/ss/daydocumentation/1/H.25--NS/1380120772954?cdp=3&gn=content%3Ageometrixx-outdoors%3Aen" height="1" width="1" border="0" alt=""/></noscript>
<span data-tracking="{event:'pageView', values:{}, componentPath:'foundation/components/page'}"></span>
<div id="cq-analytics-texthint" style="background:white; padding:0 10px; display:none;">
 <h3 class="cq-texthint-placeholder">Component clientcontext is missing or misplaced.</h3>
</div>
<script type="text/javascript">
$CQ(function(){
 if( CQ_Analytics &&
  CQ_Analytics.ClientContextMgr &&
  !CQ_Analytics.ClientContextMgr.isConfigLoaded ) 
  {
   $CQ("#cq-analytics-texthint").show();
  }
});
</script>
</div>
```

所有AEM示例网站(如Geometrixx Outdoors)都包含此代码。

### sitecatalystAfterCollect事件 {#the-sitecatalystaftercollect-event}

的 `cloudservices` 脚本触发器 `sitecatalystAfterCollect` 事件：

```
$CQ(document).trigger("sitecatalystAfterCollect");
```

此事件会触发，以指示页面跟踪已完成。 如果要在此页面上执行其他跟踪操作，则应侦听此事件，而不是文档加载或文档就绪事件。 使用 `sitecatalystAfterCollect` 事件可避免冲突或其他不可预知的行为。

>[!NOTE]
>
>的 `/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js` 库中包含来自Adobe Analytics的代码 `s_code.js` 文件。

## 为自定义组件实施Adobe Analytics跟踪 {#implementing-adobe-analytics-tracking-for-custom-components}

允许您的AEM组件与Adobe Analytics框架进行交互。 然后，配置框架，以便Adobe Analytics跟踪组件数据。

编辑框架时，与Adobe Analytics框架交互的组件会显示在SideKick中。 将组件拖到框架后，将显示组件属性，然后您可以使用Adobe Analytics属性映射它们。 (请参阅 [设置基本跟踪框架](/help/sites-administering/adobeanalytics-connect.md#creating-a-adobe-analytics-framework).)

当组件具有名为的子节点时，组件可以与Adobe Analytics框架进行交互 `analytics`. 的 `analytics` 节点具有以下属性：

* `cq:trackevents`:标识组件公开的CQ事件。 （请参阅自定义事件。）
* `cq:trackvars`:将映射到Adobe Analytics属性的CQ变量命名为。
* `cq:componentName`:Sidekick中显示的组件名称。
* `cq:componentGroup`:Sidekick中包含该组件的组。

组件JSP中的代码将Javascript添加到触发跟踪的页面，并定义要跟踪的数据。 Javascript中使用的事件名称和数据名称必须匹配 `analytics` 节点属性。

* 使用数据跟踪属性跟踪页面加载时的事件数据。 (请参阅 [在页面加载时跟踪自定义事件](/help/sites-developing/extending-analytics.md#tracking-custom-events-on-page-load).)
* 使用CQ_Analytics.record函数可在用户与页面功能交互时跟踪事件数据。 (请参阅 [页面加载后跟踪自定义事件](/help/sites-developing/extending-analytics.md#tracking-custom-events-after-page-load).)

使用这些数据跟踪方法时，Adobe Analytics集成模块会自动执行对Adobe Analytics的调用，以记录事件和数据。

### 示例：跟踪主题导航点击量 {#example-tracking-topnav-clicks}

扩展foundation topnav组件，以便Adobe Analytics跟踪页面顶部导航链接的点击。 单击导航链接后，Adobe Analytics会记录已单击的链接以及已单击该链接的页面。

以下过程要求您已执行以下任务：

* 已创建CQ应用程序。
* 创建了Adobe Analytics配置和Adobe Analytics框架。

#### 复制topnav组件 {#copy-the-topnav-component}

将topnav组件复制到CQ应用程序。 该过程要求您的应用程序在CRXDE Lite中设置。

1. 右键单击 `/libs/foundation/components/topnav` 节点，然后单击复制。
1. 右键单击应用程序文件夹下的Components文件夹，然后单击粘贴。
1. 单击“全部保存”。

#### 将Topnav与Adobe Analytics框架集成 {#integrating-topnav-with-the-adobe-analytics-framework}

配置topnav组件并编辑JSP文件以定义跟踪事件和数据。

1. 右键单击顶部导航节点，然后单击创建>创建节点。 指定以下属性值，然后单击“确定”：

   * 名称: `analytics`
   * 类型: `nt:unstructured`

1. 将以下属性添加到Analytics节点以命名跟踪事件：

   * 名称：cq:trackevents
   * 类型：字符串
   * 值：topnavClick

1. 将以下属性添加到Analytics节点以命名数据变量：

   * 名称：cq:trackvars
   * 类型：字符串
   * 值：topnavTarget，topnavLocation

1. 将以下属性添加到Analytics节点以命名Sidekick的组件：

   * 名称：cq:componentName
   * 类型：字符串
   * 值：topnav（跟踪）

1. 将以下属性添加到Analytics节点以命名Sidekick的组件组：

   * 名称：cq:componentGroup
   * 类型：字符串
   * 值：常规

1. 单击“全部保存”。
1. 打开topnav.jsp文件。
1. 在元素中，添加以下属性：

   ```xml
   onclick = "tracknav('<%= child.getPath() %>.html')" 
   ```

1. 在页面底部，添加以下javascript代码：

   ```xml
   <script type="text/javascript">
       function tracknav(target) {
               if (CQ_Analytics.Sitecatalyst) {
                   CQ_Analytics.record({
                       event: 'topnavClick',
                       values: {
                           topnavTarget: target,
                           topnavLocation:'<%=currentPage.getPath() %>.html'
                       },
                       componentPath: '<%=resource.getResourceType()%>'
                   });
               }
       }
   </script> 
   ```

1. 单击“全部保存”。

topnav.jsp文件的内容应如下所示：

```xml
<%@page session="false"%><%--
  Copyright 1997-2008 Day Management AG
  Barfuesserplatz 6, 4001 Basel, Switzerland
  All Rights Reserved.

  This software is the confidential and proprietary information of
  Day Management AG, ("Confidential Information"). You shall not
  disclose such Confidential Information and shall use it only in
  accordance with the terms of the license agreement you entered into
  with Day.

  ==============================================================================

  Top Navigation component

  Draws the top navigation

--%><%@include file="/libs/foundation/global.jsp"%><%
%><%@ page import="java.util.Iterator,
        com.day.text.Text,
        com.day.cq.wcm.api.PageFilter,
        com.day.cq.wcm.api.Page,
        com.day.cq.commons.Doctype,
        org.apache.commons.lang3.StringEscapeUtils" %><%

    // get starting point of navigation
    long absParent = currentStyle.get("absParent", 2L);
    String navstart = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);

    //if not deep enough take current node
    if (navstart.equals("")) navstart=currentPage.getPath();

    Resource rootRes = slingRequest.getResourceResolver().getResource(navstart);
    Page rootPage = rootRes == null ? null : rootRes.adaptTo(Page.class);
    String xs = Doctype.isXHTML(request) ? "/" : "";
    if (rootPage != null) {
        Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
        while (children.hasNext()) {
            Page child = children.next();
            %><a onclick = "tracknav('<%= child.getPath() %>.html')"  href="<%= child.getPath() %>.html"><%
            %><img alt="<%= StringEscapeUtils.escapeXml(child.getTitle()) %>" src="<%= child.getPath() %>.navimage.png"<%= xs %>></a><%
        }
    }
%><script type="text/javascript">
    function tracknav(target) {
            if (CQ_Analytics.Sitecatalyst) {
                CQ_Analytics.record({
                    event: 'topnavClick',
                    values: {
                        topnavTarget:target,
                        topnavLocation:'<%=currentPage.getPath() %>.html'
                    },
                    componentPath: '<%=resource.getResourceType()%>'
                });
            }
    }
</script>  
```

>[!NOTE]
>
>通常需要跟踪ContextHub中的数据。 有关使用javascript获取此信息的信息，请参阅 [在ContextHub中访问值](/help/sites-developing/extending-analytics.md#accessing-values-in-the-contexthub).

#### 将跟踪组件添加到Sidekick {#adding-the-tracking-component-to-sidekick}

将为通过Adobe Analytics进行跟踪而启用的组件添加到Sidekick，以便您可以将它们添加到框架中。

1. 从Adobe Analytics配置中打开Adobe Analytics框架。 ([http://localhost:4502/etc/cloudservices/sitecatalyst.html](http://localhost:4502/etc/cloudservices/sitecatalyst.html))
1. 在Sidekick上，单击“设计”按钮。

   ![](do-not-localize/chlimage_1.png)

1. 在链接跟踪配置区域，单击配置继承。

   ![chlimage_1](assets/chlimage_1.png)

1. 在允许的组件列表中，在常规部分中选择topnav（跟踪），然后单击确定。
1. 展开Sidekick以进入编辑模式。 组件现在在“常规”组中可用。

#### 将topnav组件添加到框架 {#adding-the-topnav-component-to-your-framework}

将顶部导航组件拖动到Adobe Analytics框架，并将组件变量和事件映射到Adobe Analytics变量和事件。 (请参阅 [设置基本跟踪框架](/help/sites-administering/adobeanalytics-connect.md).)

![chlimage_1-1](assets/chlimage_1-1.png)

topnav组件现在已与Adobe Analytics框架集成。 将组件添加到页面时，单击顶部导航栏中的项目会将跟踪数据发送到Adobe Analytics。

### 将s.products数据发送到Adobe Analytics {#sending-s-products-data-to-adobe-analytics}

组件可以为发送到Adobe Analytics的s.products变量生成数据。 设计组件以对s.products变量做出贡献：

* 记录名为 `product` 具体结构。
* 显示 `product` 值，以便它们可以在Adobe Analytics框架中与Adobe Analytics变量进行映射。

Adobe Analytics s.products变量使用以下语法：

```
s.products="category;product;quantity;price;eventY={value}|eventZ={value};evarA={value}|evarB={value}"
```

Adobe Analytics集成模块构建 `s.products` 变量 `product` AEM组件生成的值。 的 `product` AEM组件生成的javascript值是具有以下结构的值数组：

```
"product": [{
    "category": "",
    "sku"     : "path to product node",
    "quantity": quantity,
    "price"   : price,
    "events   : {
      "eventName1": "eventValue1",
      "eventName_n": "eventValue_n"
    }
    "evars"   : {
      "eVarName1": "eVarValue1",
      "eVarName_n": "eVarValue_n"
    }
}]
```

当 `product` 值时，它将作为空字符串在s.products中发送。

>[!NOTE]
>
>当没有事件与产品值关联时，Adobe Analytics会使用 `prodView` 事件。

的 `analytics` 组件的节点必须使用 `cq:trackvars` 属性：

* product.category
* product.sku
* product.quantity
* product.price
* product.events.eventName1
* product.events.eventName_n
* product.evars.eVarName1
* product.evars.eVarName_n

电子商务模块提供了几个可生成s.products变量数据的组件。 例如，提交订单组件([http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp](http://localhost:4502/crx/de/index.jsp#/libs/commerce/components/submitorder/submitorder.jsp))会生成与以下示例类似的javascript:

```
<script type="text/javascript">
    function trackCartPurchase() {
        if (CQ_Analytics.Sitecatalyst) {
            CQ_Analytics.record({
                "event": ["productsCartPurchase"],
                "values": {
                    "product": [
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/1",
                            "quantity": 3,
                            "price"   : 179.7,
                            "evars"   : {
                                "childSku": "/path/to/prod/1/green/xs",
                                "size"    : "XS"
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/2",
                            "quantity": 10,
                            "price"   : 150,
                            "evars"   : {
                                "childSku": "/path/to/prod/2",
                                "size"    : ""
                            }
                        },
                        {
                            "category": "",
                            "sku"     : "/path/to/prod/3",
                            "quantity": 2,
                            "price"   : 102,
                            "evars"   : {
                                "childSku": "/path/to/prod/3/m",
                                "size"    : "M"
                            }
                        }
                    ]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["discountRedemption"],
                "values": {
                    "discount": "/path/to/discount/1 - /path/to/discount/2",
                    "product" : [{
                        "category": "",
                        "sku"     : "Promotional Discount",
                        "events"  : {"discountRedemption": 20.00}
                    }]
                },
                "componentPath": "commerce/components/submitorder"
            });
            CQ_Analytics.record({
                "event": ["cartPurchase"],
                "values": {
                    "orderId"       : "00e40e2d-13a2-4a00-a8ee-01a9ebb0bf68",
                    "shippingMethod": "overnight",
                    "paymentMethod" : "Amex",
                    "billingState"  : "NY",
                    "billingZip"    : "10458",
                    "product"       : [{"category": "", "sku": "", "quantity": "", "price": ""}]
                },
                "componentPath": "commerce/components/submitorder"
            });
        }
        return true;
    }
</script>
```

#### 限制跟踪调用的大小 {#limiting-the-size-of-tracking-calls}

通常，Web浏览器会限制GET请求的大小。 由于CQ产品和SKU值是存储库路径，因此包含多个值的产品阵列可能会超出请求大小限制。 因此，您的组件应限制 `product` 每个 `CQ_Analytics.record function`. 如果需要跟踪的项目数量超过限制，请创建多个函数。

例如，电子商务提交订单组件限制了 `product` 对4的调用中的项目。 当购物车包含四个以上的产品时，会生成多个 `CQ_Analytics.record` 函数。
