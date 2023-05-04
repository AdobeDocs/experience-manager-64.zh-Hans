---
title: 为登陆页面扩展和配置设计导入程序
seo-title: Extending and Configuring the Design Importer for Landing Pages
description: 了解如何为登陆页面配置设计导入程序。
seo-description: Learn how to configure the Design Importer for landing pages.
uuid: b2bfe831-bfaf-43f3-babc-687bf229dd44
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: f8991416-995b-4160-a705-d131e78089ee
exl-id: 4b37c866-30c3-45ff-b7a3-013b69598668
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3526'
ht-degree: 0%

---

# 为登陆页面扩展和配置设计导入程序{#extending-and-configuring-the-design-importer-for-landing-pages}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本节介绍如何配置和（如果需要）扩展登陆页面的设计导入程序。 在 [登陆页面。](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md)

**使设计导入程序解压自定义组件**

以下是使设计导入程序识别自定义组件的逻辑步骤

1. 创建TagHandler

   * 标记处理程序是用于处理特定类型的HTML标记的POJO。 TagHandler可以处理的“类型”HTML标记通过TagHandlerFactory的OSGi属性“tagpattern.name”定义。 此OSGi属性本质上是一个正则表达式，它应该与您希望处理的输入html标记匹配。 所有嵌套的标记都将提交给标记处理程序进行处理。 例如，如果注册的div包含嵌套 &lt;p> 标记， &lt;p> 标记也会投放到您的TagHandler中，具体如何处理取决于您自己。
   * 标记处理程序界面类似于SAX内容处理程序界面。 它接收每个html标记的SAX事件。 作为标记处理程序提供程序，您需要实施某些生命周期方法，这些方法将由设计导入程序框架自动调用。

1. 创建其相应的TagHandlerFactory。

   * 标记处理程序工厂是一个OSGi组件（单点），负责生成标记处理程序的实例。
   * 您的标记处理程序工厂必须公开名为“tagpattern.name”的OSGi属性，其值与输入html标记匹配。
   * 如果有多个标记处理程序与输入html标记匹配，则会选取排名较高的标记处理程序。 排名本身作为OSGi属性公开 **service.ranking**.
   * TagHandlerFactory是OSGi组件。 您要向TagHandler提供的任何引用都必须通过此工厂。

1. 如果要覆盖默认值，请确保TagHandlerFactory具有更好的排名。

## 准备导入HTML {#preparing-the-html-for-import}

创建导入程序页面后，可以导入完整的HTML登陆页面。 要导入HTML登陆页面，您需要先将其内容压缩到设计包中。 设计包包含您的HTML登录页面以及引用的资产（图像、css、图标、脚本等）。

以下备忘录提供了如何准备导入HTML的示例：

登陆页面备忘单

[获取文件](assets/cheatsheet.zip)

### Zip文件布局和要求 {#zip-file-layout-and-requirements}

>[!NOTE]
>
>此时，ZIP文件只能包含一个HTML页面或页面的一部分。

zip的布局示例如下：

* /index.html ->登陆页面HTML文件
* /css ->添加到CSS clientlib中
* /img ->所有图像和资产
* /js ->添加到JS clientlib中

布局基于HTML5 Boilerplate最佳实践布局。 有关更多信息，请参阅 [https://html5boilerplate.com/](https://html5boilerplate.com/)

>[!NOTE]
>
>至少，设计包 **必须** 包含 **index.html** 文件。 如果要导入的登陆页面也具有移动版本，则zip必须包含 **mobile.index.html** 与 **index.html** 在根级别。

### 准备登陆页面HTML {#preparing-the-landing-page-html}

要导入HTML，您需要向登陆页面HTML添加画布div。

画布div是html **div** with `id="cqcanvas"` 必须插入到HTML中 `<body>` 标记，且必须包含要转化的内容。

添加画布div后登陆页面HTML的示例代码片段如下所示：

```xml
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title></title>
  <meta name="description" content="">
</head>
<body>
 <div id="cqcanvas">
  <!-- HTML content intended for conversion -->
 </div>
</body>
</html>
```

### 准备HTML以包含可编辑的AEM组件 {#preparing-the-html-to-include-editable-aem-components}

导入登陆页面时，您可以按原样导入页面，这意味着导入登陆页面后，将无法在AEM中编辑任何导入的项目(您仍可以在页面上添加其他AEM组件)。

在导入登陆页面之前，您可能需要转换登陆页面的某些部分，以便它们是可编辑的AEM组件。 这样，即使在导入登陆页面设计后，您也可以快速编辑登陆页面的各个部分。

要执行此操作，请将 `data-cq-component` 到导入的HTML文件中的相应组件。

以下部分介绍如何编辑HTML文件，以便将登陆页面的某些部分转换为可编辑的不同AEM组件。 组件在 [登陆页面组件](/help/sites-classic-ui-authoring/classic-personalization-campaigns-landingpage.md).

>[!NOTE]
>
>用于将登录页面的部分内容转换为AEM组件的HTML标记具有长格式和短标记声明。 每个组件都描述了这两个组件。

### 限制 {#limitations}

在导入之前，请注意以下限制：

### 不会保留在&amp;lt;body>标记上应用的任何属性，如类或id {#any-attribute-like-class-or-id-applied-on-the-amp-lt-body-tag-is-not-preserved}

例如，如果对body标记应用了id或类等任何属性 `<body id="container">` 导入后不会保留。 因此，导入的设计不应与应用于 `<body>` 标记。

### 拖放zip文件 {#drag-and-drop-zip}

Internet Explorer和Firefox版本3.6及更早版本不支持拖放zip上传。 要在使用这些浏览器时上传设计，请单击拖放文件区域以打开文件上传对话框，然后使用该对话框上传您的设计。

支持设计zip文件“拖放”的浏览器包括Chrome、Safari5.x、Firefox 4及更高版本。

### 不支持Modernizr {#modernizr-is-not-supported}

`Modernizr.js` 是基于javascript的工具，它可检测浏览器的本机功能，并检测这些功能是否适合html5元素。 使用Modernizr增强不同浏览器较旧版本支持的设计，可能会导致登陆页面解决方案出现导入问题。 `Modernizr.js` 设计导入程序不支持脚本。

### 导入设计包时不会保留页面属性 {#page-properties-are-not-preserved-at-the-time-of-importing-design-package}

任何页面属性（例如，自定义域、强制HTTPS等） 在导入设计后，在导入设计包之前为页面设置（使用空白登陆页面模板）的内容将丢失。 因此，建议的做法是在导入设计包后设置页面属性。

### HTML仅假定加价 {#html-only-markup-assumed}

导入时，出于安全原因对标记进行了清理，以避免导入和发布无效标记。 此设置假定仅HTML标记，并且将过滤掉所有其他形式的元素(如内联SVG或Web组件)。

### 文本 {#text}

HTML用于插入文本组件的标记( `foundation/components/text`)HTML中：

```xml
<div data-cq-component="text"> <p>This is some editable text</p> </div>
```

在HTML中包含上述标记可执行以下操作：

* 创建可编辑的AEM文本组件( `sling:resourceType=foundation/components/text`)。
* 设置 `text` 创建的文本组件的属性添加到 `div`.

**短组件标记声明**:

```xml
<p data-cq-component="text">Text component shorthand</p>
```

**包含列表的文本**

要添加包含列表的文本，请执行以下操作：

* 1st
* 2nd

可在RTE编辑器中编辑的以下内容：

```xml
<div data-cq-component="text"><p>This is text with a list:</p><ul><li>1st</li><li>2nd</li></ul><p>It can be edited with the RTE editor</p></div>
```

**带颜色的文本**

添加可在RTE编辑器中编辑的带颜色（粉红色）的文本：

```xml
<div class="pink" data-cq-component="text"><p>This is pink text.</p><p>It can be edited with the RTE editor</p></div>
```

### 标题 {#title}

HTML标记以插入标题组件( `wcm/landingpage/components/title`)HTML中：

```xml
<div data-cq-component="title"> <h1>This is some editable title text</h1> </div>
```

在HTML中包含上述标记可执行以下操作：

* 创建可编辑的AEM标题组件( `sling:resourceType=wcm/landingpage/components/title`)。
* 设置 `jcr:title` 将创建的标题组件的属性添加到标题标记中封装在div内的文本。
* 设置 `type` 属性到标题标记中，在本例中为 `h1`.

标题组件支持7种类型 —  `h1, h2, h3, h4, h5, h6` 和 `default`.

**短组件标记声明**:

```xml
<h1 data-cq-component="title">Title component shorthand</h1>
```

### 图像 {#image}

HTML标记，用于在设计包内的HTML中插入图像组件（基础/组件/图像）：

```xml
<div data-cq-component="image">
<img src="img/video1.png" alt="Video about Polar Brake Goggles in action" title="Polar Brake Goggles" width="300" height="200" />
</div>
```

在HTML中包含上述标记可执行以下操作：

* 创建可编辑的AEM图像组件( `sling:resourceType=foundation/components/image`)。
* 设置 `fileReference` 创建的图像组件的属性添加到在src属性中指定的图像的导入路径。
* 设置 `alt` 属性的值。
* 设置 `title` 属性的值。
* 设置 `width` 属性的值。
* 设置 `height` 属性到img标记中高度属性的值。

**短组件标记声明：**

```xml
<img data-cq-component="image" src="test.png" alt="Image component shorthand"/>
```

#### 图像组件Div中不支持绝对URL img src {#absolute-url-img-src-not-supported-within-image-component-div}

如果 `<img>` 尝试使用绝对url src进行组件转换时，会使用相应的 **UnsupportedTagContentException** 的值。 例如，不支持以下内容：

`<div data-cq-component="image">`

`<img src="https://cdn.printfriendly.com/pf-button.gif" alt="Print Friendly and PDF"/>`

`</div>`

但是，对于不属于图像组件div的img标记，也支持绝对URL图像。

### 行动动员组件 {#call-to-action-components}

您可以标记登陆页面的一部分以将其导入为“可编辑的行动动员组件” — 这样，导入的行动动员组件后，便可以编辑这些组件。 AEM包括以下CTA组件：

* 点进链接 — 允许您添加一个文本链接，单击该链接后，访客即会转到目标URL。
* 图形链接 — 允许您添加一个图像，当访客单击该图像时即会转到目标URL。

#### 点进链接 {#click-through-link}

此CTA组件可用于在登陆页面上添加文本链接。

支持的属性

* 标签，带有粗体、斜体和下划线选项
* Target URL，支持第三方和AEM URL
* 页面渲染选项（同一窗口、新窗口等）

HTML标记，以在导入的zip文件中包含点进组件。 此处的href映射到目标URL，“查看产品详细信息”映射到标签，依此类推。

```xml
<div id="cqcanvas">
.
.
                <div data-cq-component="clickThroughLink">
        <a href="/content/we-retail/us/en/products/equipment/snow-sports/flying-snowboard.html">View Product Details  ></a>
  </div>
.
.
</div>
```

此组件可用于任何独立应用程序，也可从zip中导入。

**短组件标记声明**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughLink">Click Through Link shorthand</a>
```

#### 图形链接 {#graphical-link}

此CTA组件可用于在登陆页面上添加任何带有链接的图形图像。 该图像可以是一个简单的按钮，也可以是任何作为背景的图形图像。 单击图像后，会将用户转到组件属性中指定的目标URL。 它是“行动动员”组的一部分。

支持的属性

* 图像裁剪、旋转
* 悬停文本、描述、像素大小
* Target URL，支持第三方和AEM URL
* 页面渲染选项（同一窗口、新窗口等）

HTML标记，以在导入的zip文件中包含图形链接组件。 此处的href将映射到目标url，img src将作为渲染图像，“标题”将被用作悬停文本，依此类推。

```xml
<div id="cqcanvas">
  <div data-cq-component="clickThroughGraphicalLink"><a href="https://www.adobe.com/go/wem"><img src="img/call-to-action-button.png" title="Click Here to Learn More" /></a></div>
</div>
```

**短组件标记声明**:

```xml
<a href="/somelink.html" data-cq-component="clickThroughGraphicalLink"><img src="linkimage.png" alt="Click Through Graphical Link shorthand"/></a>
```

>[!NOTE]
>
>要创建clickthroughgraphical链接，您需要将锚点标记和图像标记包含在div中 `data-cq-component="clickthroughgraphicallink"` 属性。
>
>例如 `<div data-cq-component="clickthroughlink"> <a href="https://myURLhere/"><img src="image source here"></a> </div>`
>
>不支持使用CSS将图像与锚点标记关联的其他方法，例如，以下标记将无法正常使用：
>
>`<div data-cq-component="clickthroughgraphicallink">`
>
>`<a class="hasBackground" href="https://myURLhere/"></a>`
>
>`</div>`
>
>与 `css .hasbackground { background-image: pathtoimage }`

### 潜在客户表单 {#lead-form}

潜在客户表单是用于收集访客/潜在客户配置文件信息的表单。 这些信息可以存储，并稍后用于根据这些信息进行有效的营销。 此信息通常包括标题、姓名、电子邮件、出生日期、地址、兴趣等。 它是“CTA潜在客户表单”组的一部分。

**支持的功能**

* 预定义潜在客户字段 — Sidekick中提供了名字、姓氏、地址、Dob、性别、关于、userId、emailId、提交按钮。 只需在潜在客户表单中拖放所需的组件即可。
* 借助这些组件，作者可以设计一个独立的潜在客户表单，这些字段对应于潜在客户表单字段。 在独立或导入的zip应用程序中，用户可以使用cq:form或cta潜在客户表单字段添加其他字段，并根据要求对其进行命名和设计。
* 使用CTA潜在客户表单的特定预定义名称映射潜在客户表单字段，例如，firstName表示潜在客户表单中的名字，等等。
* 未映射到潜在客户表单的字段将映射到cq:form组件 — 文本、单选按钮、复选框、下拉列表、隐藏、密码。
* 用户可以使用“标签”标记提供标题，并可以使用样式属性“class”来提供样式（仅适用于CTA潜在客户表单组件）。
* 感谢页面和订阅列表可作为表单的隐藏参数提供（在index.htm中提供），也可从“潜在客户表单的开头”的编辑栏添加/编辑

   &lt;input type=&quot;hidden&quot; name=&quot;redirectUrl&quot; value=&quot;/content/we-retail/en/user/register/thank_you&quot;/>

   &lt;input type=&quot;hidden&quot; name=&quot;groupName&quot; value=&quot;leadForm&quot;/>

* 约束（如 — 必需）可通过每个组件的编辑配置来提供。

HTML标记，以在导入的zip文件中包含图形链接组件。 此处的“firstName”已映射到潜在客户表单firstName等，但复选框除外 — 这两个复选框映射到cq:form下拉组件。

```xml
<div id="cqcanvas">
   <div id="form_wrapper">
    <h2>NEWSLETTER SIGN UP</h2>
       <div data-cq-component="leadFormGeneration">
       <form method="post" action="#" onsubmit="return popupBox()">
       <label for="firstName" class="checkText">
        FIRST NAME
       </label><br />
       <input name="firstName" class="text pink" type="text" /><br />
       <label for="lastName" class="checkText">
        LAST NAME
       </label><br />
       <input name="lastName" class="text pink" type="text" /><br />
       <label for="emailId" class="checkText">
        EMAIL ADDRESS
       </label><br />
       <input name="emailId" class="text pink" type="text" /><br />

       <div class="checkboxes">
       <input type="checkbox" class="check" name="send_news" /> <label for="send_news" class="checkText">Send me the latest We.Retail news and announcements.</label><br />
       <input type="checkbox" class="check" name="send_offers" /> <label for="send_offers" class="checkText">Send me We.Retail deals and special offers.</label><br />
       </div>
       <input type="submit" name="submit" class="submit pink" value="Sign Up >" />
       </form>
     </div>
   </div>
```

### Parsys {#parsys}

AEM AEM组件是一个可包含其他Parsys组件的容器组件。 可以在导入的HTML中添加Parsys组件。 这允许用户向登陆页面添加/删除可编辑的AEM组件，即使在导入后也是如此。

段落系统允许用户使用Sidekick添加组件。

HTML用于插入Parsys组件的标记( `foundation/components/parsys`)HTML中：

```xml
<div data-cq-component="parsys">
   <div data-cq-component="title"><h2>ULTIMATE PROTECTION</h2></div>
        <div data-cq-component="title"><h3>ON SALE</h3></div>
</div>
```

在HTML中包含上述标记可执行以下操作：

* 在导入设计包后创建的登陆页面中插入AEM Parsys组件(foundation/components/parsys)。
* 使用默认组件初始化Sidekick。 通过将组件从Sidekick拖动到Parsys组件上，可以将新组件添加到登陆页面。
* 两个标题组件也是Parsys的一部分。

### 目标 {#target}

目标组件显示页面上体验的内容。 营销活动中可以创建多个体验，而目标组件可向访问该页面的不同用户动态显示不同体验的内容。

用于插入目标组件并在营销活动中创建不同体验的html标记：

```xml
<div data-cq-component="target">
 <section data-cq-component="experience" data-cq-experience="default">
  <p data-cq-component="text">Default content. Select this campaign in client context to view other experiences</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="over-30">
  <p data-cq-component="text">Content for Over 30</p>
 </section>

 <section data-cq-component="experience" data-cq-segment="under-30">
  <p data-cq-component="text">Content for Under 30</p>
 </section>
</div>
```

## 其他导入选项 {#additional-importing-options}

除了指定导入的组件是否为可编辑的AEM组件外，您还可以在导入设计包之前配置以下内容：

* 通过提取导入的HTML中定义的元数据来设置页面属性。
* 在HTML中指定字符集编码。
* 覆盖导入器页面模板。

### 通过提取导入的HTML中定义的元数据来设置页面属性 {#setting-page-properties-by-extracting-metadata-defined-in-imported-html}

设计导入程序应将导入HTML标题中声明的以下元数据作为属性“jcr:description”进行提取和保留：

* &lt;meta name=&quot;description&quot; content=&quot;&quot;>

HTML标记中设置的Lang属性将由设计导入器作为属性“jcr:language”进行提取和保留

* &lt;html lang=&quot;en&quot;>

### 在html中指定字符集编码 {#specifying-the-charset-encoding-in-the-html}

设计导入程序会读取导入的HTML中指定的编码。 编码可按如下方式指定：

`<meta charset="UTF-8">`

*或*

`<meta http-equiv="content-type" content="text/html;charset=utf-8">`

如果导入的HTML中未指定编码，则设计导入程序设置的默认编码为UTF-8。

### 覆盖模板 {#overlaying-template}

通过在以下位置创建新登陆页面，可以覆盖空白登陆页面模板： `/apps/<appName>/designimporter/templates/<templateName>`

说明了在AEM中创建新模板的步骤 [此处](/help/sites-developing/templates.md).

### 从登陆页面引荐组件 {#referring-a-component-from-landing-page}

假设您有一个组件，您想要在HTML中使用data-cq-component属性引用该组件，以便设计导入程序渲染此处包含的组件。 例如，要引用表组件( `resourceType = /libs/foundation/components/table`)。 需要在HTML中添加以下内容：

`<div data-cq-component="/libs/foundation/components/table">foundation table</div>`

data-cq-component中的路径应为组件的resourceType。

### 最佳实践 {#best-practices}

对于在导入时标记为进行组件转换的元素，不建议使用与下面类似的CSS选择器。

| E > F | E元素的F元素子项 | [子组合器](https://www.w3.org/TR/css3-selectors/#child-combinators) |
|---|---|---|
| E + F | 紧靠E元素的F元素 | [相邻同级组合器](https://www.w3.org/TR/css3-selectors/#adjacent-sibling-combinators) |
| E ~ F | 前面有E元素的F元素 | [一般同级组合器](https://www.w3.org/TR/css3-selectors/#general-sibling-combinators) |
| E:root | E元素，文档的根 | [结构伪类](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-child(n) | E元素，其父元素的第n个子元素 | [结构伪类](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-child(n) | 一个E元素，即其父代的第n个子元素，从最后一个元素开始计数 | [结构伪类](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-of-type(n) | E元素，其类型的第n个同级元素 | [结构伪类](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |
| E:nth-last-of-type(n) | E元素，其类型的第n个同级元素，从最后一个元素计数 | [结构伪类](https://www.w3.org/TR/css3-selectors/#structural-pseudos) |

这是因为其他html元素，例如 &lt;div> 标记会在导入后添加到生成的HTML中。

* 对于标记为转换到AEM组件的元素，也不建议使用依赖于类似于上述结构的脚本。
* 在标记标记上使用样式进行组件转换，如 &lt;div data-cq-component=&quot;”&amp;ast;”&quot;> 不建议。
* 设计布局应遵循HTML5 Boilerplate中的最佳实践。 阅读更多内容： [https://html5boilerplate.com/](https://html5boilerplate.com/).

## 配置OSGI模块 {#configuring-osgi-modules}

公开可通过OSGi控制台配置的属性的组件如下所示：

* 登陆页面设计导入程序
* 登陆页面生成器
* 移动设备登陆页面生成器
* 登陆页面条目预处理器

下表简要描述了以下属性：

<table> 
 <tbody> 
  <tr> 
   <td><strong>组件</strong></td> 
   <td><strong>属性名称</strong></td> 
   <td><strong>属性描述 </strong></td> 
  </tr> 
  <tr> 
   <td>登陆页面设计导入程序</td> 
   <td>提取过滤器</td> 
   <td>用于从提取中筛选文件的正则表达式列表。 <br /> 提取中将排除与任何指定模式匹配的Zip条目</td> 
  </tr> 
  <tr> 
   <td>登陆页面生成器</td> 
   <td>文件模式</td> 
   <td>登陆页面生成器可以配置为处理与由文件模式定义的正则表达式匹配的HTML文件。</td> 
  </tr> 
  <tr> 
   <td>移动设备登陆页面生成器</td> 
   <td>文件模式</td> 
   <td>登陆页面生成器可以配置为处理与由文件模式定义的正则表达式匹配的HTML文件。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>设备组</td> 
   <td>要支持的设备组列表。</td> 
  </tr> 
  <tr> 
   <td>登陆页面条目预处理器</td> 
   <td>搜索模式 </td> 
   <td>在存档条目内容中搜索的模式。 此正则表达式与条目内容逐行匹配。 匹配后，匹配的文本将被指定的替换模式替换。<br /> <br /> 请参阅下面有关登陆页面条目处理器当前限制的注释。</td> 
  </tr> 
  <tr> 
   <td> </td> 
   <td>替换模式</td> 
   <td>替换找到的匹配项的模式。 您可以使用正则表达式组引用，如$1、$2。 此外，此模式还支持在导入期间使用实际值解析的关键字，如{designPath}。</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>**登陆页面条目处理器的当前限制：**
>如果需要对搜索模式进行任何更改，则在打开felix属性编辑器时，需要手动添加反斜杠字符以对正则表达式元字符进行转义。 如果不手动添加反斜线字符，则正则表达式将被视为无效，且不会替换旧的正则表达式。
>
>例如，如果默认配置为
>
>`/\&ast *CQ_DESIGN_PATH *\*/ *(['"])`
>
>你需要替换 `CQ_DESIGN_PATH` with `VIPURL` 在搜索模式中，搜索模式应当如下所示：
>
>`/\* *VIPURL *\*/ *(['"])`

## 疑难解答 {#troubleshooting}

在导入设计包时，您可能会遇到多个错误，如本节所述。

### 使用登陆页面相关组件初始化Sidekick {#initialization-of-sidekick-with-landing-page-relevant-components}

如果设计包包含Parsys组件标记，则在导入后，Sidekick会开始显示登陆页面相关的组件。 您可以将新组件拖放到登陆页面内的parsys组件上。 您还可以转到设计模式，并向Sidekick中添加新组件。

### 导入期间显示的错误消息 {#error-messages-displayed-during-import}

如果发生任何错误（例如，导入的包不是有效的zip文件），则设计导入不会导入包，而是会在页面顶部的拖放框上方显示一条错误消息。 此处介绍了错误情景的示例。 更正错误后，您可以将更新的zip重新导入到同一空白登陆页面。 引发错误的不同情况如下：

* 导入的设计包不是有效的zip存档。
* 导入的设计包在顶级不包含index.html。

### 导入后显示警告 {#warnings-displayed-after-import}

如果出现任何警告(例如，HTML引用包中不存在的图像)，设计导入程序将导入zip文件，但同时在“结果窗格”上显示问题/警告列表，单击问题链接，将显示警告列表，其中指明了设计包中的任何问题。 设计导入程序捕获并显示警告的不同情况如下：

* HTML是指包中不存在的图像。
* HTML是指包中不存在的脚本。
* HTML是指包中不存在的样式。

### ZIP文件的文件存储在AEM中的什么位置？ {#where-are-the-files-of-the-zip-file-being-stored-in-aem}

导入登陆页面后，文件（图像、css、js等） 存储在AEM中的以下位置：

`/etc/designs/default/canvas/content/campaigns/<name of brand>/<name of campaign>/<name of landing page>`

假设登陆页面是在营销活动We.Retail下创建的，且登陆页面的名称为 **myBlankLandingPage** 然后，Zip文件的存储位置如下：

`/etc/designs/default/canvas/content/campaigns/geometrixx/myBlankLandingPage`

### 格式未保留 {#formatting-not-preserved}

创建CSS时，请注意以下限制：

如果文本和（可编辑）图像类似于以下内容：

```xml
<div class="box">
<p><div data-cq-component="image"><img src="assets/image.jpg" width="115"
height="116" /></div>Some Text </p>
</div>
```

类上应用了CSS `box` 如下所示：

```xml
.box

{ width: 450px; padding:10px; border: 1px #C5DBE7 solid; margin: 0px auto 0 auto; background-image:url(assets/box.gif); background-repeat:repeat-x,y; font-family:Verdana, Arial, Helvetica, sans-serif; font-size:12px; color:#6D6D6D; }
```

然后 `box img` 在设计导入器中使用，生成的登陆页面似乎未保留格式。 要解决此问题，请注意，AEM会在CSS中添加div标记，并相应地重写代码。 否则，某些CSS规则将无效。

```xml
.box img

{ float:right; margin: 0 0 5px 5px; border: 1px #343434 solid; }
```

>[!NOTE]
>
>此外，设计人员还应注意，只有 **id=cqcanvas** 标记被导入程序识别，否则不会保留设计。
