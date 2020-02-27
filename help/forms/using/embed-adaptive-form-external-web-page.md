---
title: 在外部网页中嵌入自适应表单
seo-title: 在外部网页中嵌入自适应表单
description: 了解如何在外部网页中嵌入自适应表单
seo-description: 了解如何在外部HTML网页中嵌入自适应表单
uuid: c612ca3b-62f7-4021-939b-e0c05dbbf0d7
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: author
discoiquuid: b99c7b93-ba05-42ee-9ca8-0079e15d8602
translation-type: tm+mt
source-git-commit: 7a5fb38ada7e7ad76525449e35f64b133aa5e39f

---


# 在外部网页中嵌入自适应表单{#embed-adaptive-form-in-external-web-page}

了解如何在外部网页中嵌入自适应表单

您可以 [在AEM站点页面或AEM外部托管的网页中嵌入自适应表单](/help/forms/using/embed-adaptive-form-aem-sites.md) 。 嵌入式自适应表单功能齐全，用户无需离开页面即可填写和提交表单。 它帮助用户保持在网页上其他元素的上下文中并与表单同时交互。

## 前提条件 {#prerequisites}

在将自适应表单嵌入到外部网站之前，请执行以下步骤：

* 在AEM发布实例上发布自适应表单。
* 在您的网站上创建或标识网页以托管自适应表单。 确保网页可以 [从CDN读取jQuery文件](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) ，或嵌入了jQuery的本地副本。 渲染自适应表单时需要jQuery。
* 当AEM服务器和网页位于不同的域上时，请执行部分中列出的步骤，使 [AEM Forms能够向跨域站点提供自适应表单](#cross-domain-sites)。
* [设置反向代理](#reveseproxy) ，以启用外部页面与AEM Forms服务器之间的通信。

## 嵌入自适应表单 {#embed-adaptive-form}

通过在网页中插入几行JavaScript，可以嵌入自适应表单。 代码中的API向AEM服务器发送HTTP请求以获取自适应表单资源，并在指定的表单容器中插入自适应表单。 以下是将自适应表单嵌入到外部页面的示例代码。 请勿使用代码，因为它位于生产环境中。 自定义代码以适合您的网站，如为使用自己版本的jQuery的网站使用iFrame。 使用iFrame有助于避免jQuery版本中的冲突：


1. 将以下代码嵌入到您网站的网页中：

   ```
   
   
<!doctype html>
<html>
  <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <title>这是网页的标题！</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  </head>
  <body>
  <div class="customafsection"/>
    <p>此部分将替换为自适应表单。</p>


    &lt;script>
    var options = {path:&quot;/content/forms/af/locbasic.html&quot;, dataRef:&quot;&quot;, themepath:&quot;&quot;,CSS_Selector:&quot;。customafsection&quot;};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
    if(options.path){//options.path){/.path.path.自适应表单
    
    //的URL，例如：http:myserver:4503/content/forms/af/ABC，其中ABC是自适应表单
    //注意：如果AEM服务器在上下文路径上运行，则自适应表单URL必须包含上下文
    pathvar path = options.path;
    path += &quot;/jcr:content/guideContainer.html&quot;;
    $.ajax({
    url:路径，
    类型：“GET”,
    数据：{
    //将wcmmode设置为禁用
    wcmmode:“disabled”
    //设置数据引用(如果有
    // &quot;dataRef&quot;):options.dataRef
    //为表单对象
    // &quot;themeOverride&quot;指定其他主题：options.themepath
    },
    async:false,
    success:function(data){
    //如果加载了jquery，请设置container
    //的内部html；如果未加载jquery，请使用文档提供的API设置内部HTML，但这些API不会按照HTML5规范
    //评估HTML中的script标记，例如：document.getElementById()。innerHTMLif(
    window)。$ &amp;&amp; options.CSS_Selector){
    //jquery的HTML API提取标记，更新DOM，并评估嵌入在脚本标记中的代码。
    $(options.CSS_Selector)。html(data);
    }
    },
    错误：function(data){
    // any error handler
    }
    });
    } else {
    if(typeof(console)!== &quot;undefined&quot;){
    console.log（&quot;未指定自适应表单的路径到loadAdaptiveForm&quot;）;
    }
    }
    }（选项）;
    
    &lt;/script>
</body>
</html>
   ```

1. 在嵌入式代码中：

   * 使用自适应 `options.path` 表单的发布URL路径更改变量的值。 如果AEM服务器在上下文路径上运行，请确保URL包含上下文路径。 例如，上述代码和adaptive from驻留在同一aem表单服务器上，因此该示例使用自适应表单/content/forms/af/locbasic.html的上下文路径。
   * 用要 `options.dataRef` 传递的URL属性替换。 您可以使用dataref变量预填自 [适应表单](/help/forms/using/prepopulate-adaptive-form-fields.md)。
   * 使用 `options.themePath` 自适应表单中配置的主题以外的主题路径替换。 或者，您也可以使用request属性指定主题路径。
   * `CSS_Selector` 是嵌入自适应表单的表单容器的CSS选择器。 例如，.customafsection css类是上例中的CSS选择器。

自适应表单嵌入到网页中。 在嵌入的自适应表单中观察以下内容：

* 原始自适应表单中的页眉和页脚不包括在嵌入的表单中。
* 草稿和提交的表单位于表单门户的“草稿和提交”选项卡中。
* 在原始自适应表单上配置的提交操作将保留在嵌入式表单中。
* 自适应表单规则在嵌入的表单中保留并完全可用。
* 在原始自适应表单中配置的体验定位和A/B测试在嵌入式表单中不起作用。
* 如果在原始表单上配置了Adobe Analytics，则Adobe Analytics服务器会捕获分析数据。 但是，表单分析报告中不提供此功能。

## 设置反向代理 {#reveseproxy}

嵌入自适应表单的外部网页会向AEM服务器发送请求，该服务器通常位于专用网络中防火墙的后面。 要确保将请求安全定向到AEM服务器，建议设置反向代理服务器。

让我们看一个示例，了解如何在不使用调度程序的情况下设置Apache 2.4反向代理服务器。 在此示例中，您将承载具有上下文路径的AEM服 `/forms` 务器并映射 `/forms` 反向代理。 它可确保Apache服务器上 `/forms` 的任何请求都定向到AEM实例。 此拓扑有助于减少调度程序层的规则数，因为所有请求都以路由到AEM服 `/forms` 务器为前缀。

1. 打开配 `httpd.conf` 置文件并取消以下几行代码的注释。 或者，您也可以在文件中添加这些代码行。

   ```
   LoadModule proxy_html_module modules/mod_proxy_html.so 
    LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. 通过在配置文件中添加以下几行代码来设置代 `httpd-proxy.conf` 理规则。

   ```
   ProxyPass /forms https://[AEM_Instance]/forms 
    ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   在规 `[AEM_Instance`则中，替换为AEM服务器发布URL。

如果不在上下文路径上装载AEM服务器，则Apache层的代理规则将如下：

```java
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json
  
ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>如果设置了任何其他拓扑，请确保将提交、预填充和其他URL列在调度程序层的白名单中。

## Best practices {#best-practices}

在网页中嵌入自适应表单时，请考虑以下最佳实践：

* 确保网页CSS中定义的样式规则与表单对象CSS不冲突。 要避免冲突，您可以使用AEM客户端库在自适应表单主题中重用网页CSS。 有关在自适应表单主题中使用客户端库的信息，请参 [阅AEM Forms中的主题](/help/forms/using/themes.md)。
* 使网页中的表单容器使用整个窗口宽度。 它确保为移动设备配置的CSS规则工作而无需任何更改。 如果表单容器不占用整个窗口宽度，您需要编写自定义CSS以使表单适应不同的移动设备。
* 使 ` [getData](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` 用API在客户端获取表单数据的XML或JSON表示形式。
* 使 ` [unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-3/forms/javascript-api/GuideBridge.html)` 用API从HTML DOM卸载自适应表单。
* 从AEM服务器发送响应时设置访问控制源头。

## 使AEM Forms能够向跨域站点提供自适应表单 {#cross-domain-sites}

1. 在AEM作者实例上，转到AEM Web Console Configuration Manager（位于） `http://[server]:[port]/system/console/configMgr`。
1. 找到并打开 **Apache Sling Referrer** Filter配置。
1. 在“允 **许的主机** ”字段中，指定网页所在的域。 它使主机能够向AEM服务器发出POST请求。 您还可以使用正则表达式指定一系列外部应用程序域。