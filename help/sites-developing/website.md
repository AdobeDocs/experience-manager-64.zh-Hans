---
title: 创建功能完备的网站(JSP)
seo-title: Create a Fully-Featured Website (JSP)
description: 本教程让您能够使用AEM创建功能齐全的网站
seo-description: This tutorial enables you to create a fully featured website with AEM
uuid: bb8d4efd-7631-4cc5-8084-b03c6aabdef3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 8d14017d-d311-45e9-8aea-4a5ca46f1a07
exl-id: 6d408fd6-9241-4069-9b04-806e30e03ff2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4935'
ht-degree: 2%

---

# 创建功能完备的网站(JSP){#create-a-fully-featured-website-jsp}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>本文介绍了如何使用JSP和基于经典UI创建网站。 Adobe建议将最新的AEM技术用于您的网站，如文章中所述 [开发入门AEM Sites](/help/sites-developing/getting-started.md).

本教程让您能够使用Adobe Experience Manager(AEM)创建功能完备的网站。 该网站将基于一个通用网站，并且主要面向Web开发人员。 所有开发都将在创作环境中进行。

本教程介绍如何：

1. 安装AEM。
1. 访问CRXDE Lite（开发环境）。
1. 在CRXDE Lite中设置项目结构。
1. 创建模板、组件和脚本，用作创建内容页面的基础。
1. 为您的网站创建根页面，然后创建内容页面。
1. 创建以下组件以在您的页面上使用：

   * **[!UICONTROL 顶部导航]**
   * **[!UICONTROL 列出子项]**
   * **[!UICONTROL 徽标]**
   * **[!UICONTROL 图像]**
   * **[!UICONTROL 文本 — 图像]**
   * **[!UICONTROL 搜索]**

1. 包括各种基础组件。

执行所有步骤后，您的页面将如下所示：

![chlimage_1-99](assets/chlimage_1-99.png)

**下载最终结果**

要遵循本教程而不是执行练习，请下载website-1.0.zip。 此文件是一个AEM内容包，其中包含本教程的结果。 使用 [包管理器](/help/sites-administering/package-manager.md) 将包安装到创作实例。

>[!NOTE]
>安装此包将覆盖您使用本教程创建的创作实例上的所有资源。

网站内容包

[获取文件](assets/website-1_0.zip)

## 安装Adobe Experience Manager {#installing-adobe-experience-manager}

要安装用于开发网站的AEM实例，请按照 [使用创作和发布实例的部署环境](/help/sites-deploying/deploy.md#author-and-publish-installs)，或执行 [通用安装](/help/sites-deploying/deploy.md#default-local-install). 一般安装包括下载AEM快速入门JAR文件，将license.properties文件放在与JAR文件相同的目录中，然后双击JAR文件。

安装AEM后，通过单击欢迎页面上的CRXDE Lite链接，访问CRXDE Lite开发环境：

![chlimage_1-100](assets/chlimage_1-100.png)

>[!NOTE]
>
>使用默认端口本地安装的AEM创作实例的CRXDE LiteURL为 [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/).

## 在CRXDE Lite中设置项目结构 {#setting-up-the-project-structure-in-crxde-lite}

使用CRXDE Lite在存储库中创建mywebsite应用程序结构：

1. 在CRXDE Lite左侧的树中，右键单击 **`/apps`** 文件夹，单击 **[!UICONTROL 创建>创建文件夹]**. 在 **创建文件夹** 对话框，类型 `mywebsite` 作为文件夹名称，然后单击 **确定**.
1. 右键单击 `/apps/mywebsite` 文件夹，单击 **[!UICONTROL 创建>创建文件夹]**. 在 **[!UICONTROL 创建文件夹]** 对话框，类型 `components` 作为文件夹名称，然后单击 **[!UICONTROL 确定]**.
1. 右键单击 `/apps/mywebsite` 文件夹，单击 **[!UICONTROL 创建>创建文件夹]**. 在 **[!UICONTROL 创建文件夹]** 对话框，类型 `templates` 作为文件夹名称，然后单击 **[!UICONTROL 确定]**.

   树中的结构现在应该如下所示：

   ![chlimage_1-101](assets/chlimage_1-101.png)

1. 单击 **[!UICONTROL 全部保存]**.

## 设置设计 {#setting-up-the-design}

在此部分中，您可以使用Designer工具为应用程序创建设计。 设计为您的网站提供CSS和图像资源。

>[!NOTE]
>
>单击以下链接可下载 ``mywebsite.zip``. 存档包含用于您设计的static.css和图像文件。

static.css文件和图像示例

[获取文件](assets/mywebsite.zip)

1. 在AEM欢迎页面上，单击 **[!UICONTROL 工具]**. ([http://localhost:4502/libs/cq/core/content/welcome.html](http://localhost:4502/libs/cq/core/content/welcome.html))

   ![chlimage_1-102](assets/chlimage_1-102.png)

1. 在文件夹树中，选择 **[!UICONTROL 设计]** 文件夹，然后单击 **[!UICONTROL 新建>新建页面]**. 类型 `mywebsite` 作为标题，然后单击 **[!UICONTROL 创建]**.

1. 如果我的网站项目未显示在表中，请刷新树或表。

1. [使用WebDAV](/help/sites-administering/webdav-access.md) 访问http://localhost:4502上的URL，请复制示例 `static.css` 文件和 `images` 文件夹（从下载的mywebsite.zip文件中） `/etc/designs/mywebsite` 文件夹。

   ![chlimage_1-103](assets/chlimage_1-103.png)

## 创建内容页面模板、组件和脚本 {#creating-the-contentpage-template-component-and-script}

在此部分中，您可以创建以下内容：

* 用于在示例网站中创建内容页面的内容页面模板
* 用于呈现内容页面的内容页面组件
* 内容页面脚本

### 创建内容页面模板 {#creating-the-contentpage-template}

创建模板以用作网站网页的基础。

模板可定义新页面的默认内容。 复杂网站可能使用多个模板来创建网站中不同类型的页面。 在本练习中，所有页面都基于一个简单的模板。

1. 在CRXDE Lite的文件夹树中，右键单击 `/apps/mywebsite/templates` 单击 **[!UICONTROL 创建>创建模板]**.

1. 在创建模板对话框中，键入以下值，然后单击 **[!UICONTROL 下一个]**:

   * **[!UICONTROL 标签]**:contentpage
   * **[!UICONTROL 标题]**:“我的网站内容”页面模板
   * **[!UICONTROL 描述]**:这是我的网站内容页面模板
   * **[!UICONTROL 资源类型]**:mywebsite/components/contentpage

   使用“排名”属性的默认值。

   ![chlimage_1-104](assets/chlimage_1-104.png)

   资源类型标识呈现页面的组件。 在这种情况下，使用内容页面模板创建的所有页面都由 `mywebsite/components/contentpage` 组件。

1. 要指定可以使用此模板的页面路径，请单击加号按钮并键入 `/content(/.*)?` 中。 然后，单击 **[!UICONTROL 下一个]**.

   ![chlimage_1-105](assets/chlimage_1-105.png)

   允许的路径属性的值是 *正则表达式。* 路径与表达式匹配的页面可以使用模板。 在这种情况下，正则表达式匹配 `/content` 文件夹和所有子页面。

   作者创建下面的页面时 `/content`, **[!UICONTROL contentpage]** 模板会显示在可用模板列表中。

1. 单击 **[!UICONTROL 下一个]** 在 **[!UICONTROL 允许的父项]** 和 **[!UICONTROL 允许的子项]** 面板，单击 **[!UICONTROL 确定]**. 在CRXDE Lite中，单击 **[!UICONTROL 全部保存]**.

   ![chlimage_1-106](assets/chlimage_1-106.png)

#### 创建内容页面组件 {#creating-the-contentpage-component}

创建 *组件* 定义内容并渲染使用contentpage模板的页面。 组件的位置必须与内容页面模板的Resource Type属性的值相对应。

1. 在CRXDE Lite中，右键单击 `/apps/mywebsite/components` 单击 **[!UICONTROL 创建>组件]**.
1. 在 **[!UICONTROL 创建组件]** 对话框中，键入以下属性值：

   * **[!UICONTROL 标签]**:contentpage
   * **[!UICONTROL 标题]**:我的网站内容页面组件
   * **[!UICONTROL 描述]**:这是我的网站内容页面组件

   ![chlimage_1-107](assets/chlimage_1-107.png)

   新组件的位置为 `/apps/mywebsite/components/contentpage`. 此路径与内容页面模板的资源类型（减去初始值）相对应 `/apps/` 路径的一部分)。

   此通信将模板与组件相关联，并且对于网站的正确运行至关重要。

1. 单击 **[!UICONTROL 下一个]** 直到 **[!UICONTROL 允许的子项]** ，然后单击 **[!UICONTROL 确定]**. 在CRXDE Lite中，单击 **[!UICONTROL 全部保存]**.

   此结构现在如下所示：

   ![chlimage_1-108](assets/chlimage_1-108.png)

#### 开发内容页面组件脚本 {#developing-the-contentpage-component-script}

将代码添加到contentpage.jsp脚本以定义页面内容。

1. 在CRXDE Lite中，打开文件 `contentpage.jsp` in `/apps/mywebsite/components/contentpage`. 默认情况下，文件包含以下代码：

   ```java
   <%--
   
     My Website Content Page Component component.
   
     This is My Website Content Page Component.
   
   --%><%
   %><%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" %><%
   %><%
       /* TODO add you code here */
   %>
   ```

1. 复制以下代码，并将其粘贴到默认代码之后的contentpage.jsp中：

   ```java
   <%@ page language="java" contentType="text/html; charset=ISO-8859-1"
       pageEncoding="ISO-8859-1"%>
   <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
   "https://www.w3.org/TR/html4/loose.dtd">
   <html>
   <head>
   <meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
   <title>My title</title>
   </head>
   <body>
   <div>My body</div>
   </body>
   </html>
   ```

1. 单击 **[!UICONTROL 全部保存]** 以保存更改。

### 创建网站页面和内容页面 {#creating-your-website-page-and-content-pages}

在此部分中，您可以创建以下所有页面，这些页面均使用内容页面模板：我的网站，英文、产品、服务和客户。

1. 在AEM欢迎页面([http://localhost:4502/libs/cq/core/content/welcome.html](http://localhost:4502/libs/cq/core/content/welcome.html))，请单击网站。

   ![chlimage_1-109](assets/chlimage_1-109.png)

1. 在文件夹树中，选择 **[!UICONTROL 网站]** 文件夹，然后单击 **[!UICONTROL 新建>新建页面]**.
1. 在 **[!UICONTROL 创建页面]** 窗口，输入以下内容：

   * **[!UICONTROL 标题]**: `My Website`
   * **[!UICONTROL 名称]**: `mywebsite`
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

   ![chlimage_1-110](assets/chlimage_1-110.png)

1. 单击&#x200B;**[!UICONTROL 创建]**。在文件夹树中，选择 `/Websites/My Website` 页面，单击 **[!UICONTROL 新建>新建页面]**.
1. 在 **[!UICONTROL 创建页面]** 对话框中，输入以下属性值，然后单击创建：

   * **[!UICONTROL 标题]**:英语
   * **[!UICONTROL 名称]**:en
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

1. 在文件夹树中，选择 `/Websites/My Website/English` 页面，单击 **[!UICONTROL 新建>新建页面]**.
1. 在 **[!UICONTROL 创建页面]** 对话框，输入以下属性值，然后单击 **[!UICONTROL 创建]**:

   * **[!UICONTROL 标题]**:产品
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

1. 在文件夹树中，选择 `/Websites/My Website/English` 页面，单击 **[!UICONTROL 新建>新建页面]**.
1. 在 **[!UICONTROL 创建页面]** 对话框，输入以下属性值，然后单击 **[!UICONTROL 创建]**:

   * **标题**:服务
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

1. 在文件夹树中，选择 `/Websites/My Website/English` 页面，单击 **[!UICONTROL 新建>新建页面]**.
1. 在 **[!UICONTROL 创建页面]** 对话框，输入以下属性值，然后单击 **[!UICONTROL 创建]**:

   * **标题**:客户
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

   您的结构如下所示：

   ![chlimage_1-111](assets/chlimage_1-111.png)

1. 要将您的页面链接到网站设计，请在CRXDE Lite中，选择 `/content/mywebsite/en/jcr:content` 节点。 在 **[!UICONTROL 属性]** 选项卡，为新属性键入以下值，然后单击添加：

   * **[!UICONTROL 名称]**:cq:designPath
   * **[!UICONTROL 类型]**:字符串
   * **[!UICONTROL 值]**:/etc/designs/mywebsite

   ![chlimage_1-112](assets/chlimage_1-112.png)

1. 在新的Web浏览器选项卡或窗口中，打开 [http://localhost:4502/content/mywebsite/en/products.html](http://localhost:4502/content/mywebsite/en/products.html) 要查看产品页面，请执行以下操作：

   ![chlimage_1-113](assets/chlimage_1-113.png)

### 增强Contentpage脚本 {#enhancing-the-contentpage-script}

本节介绍如何使用AEM基础组件脚本和编写您自己的脚本来增强contentpage脚本。

的 **[!UICONTROL 产品]** 页面如下所示：

![chlimage_1-4](assets/chlimage_1-4.jpeg)

#### 使用Foundation页面脚本 {#using-the-foundation-page-scripts}

在本练习中，您可以配置页面内容组件，使其超类型为AEM页面组件。 由于组件会继承其超类型的功能，因此页面内容会继承页面组件的脚本和属性。

例如，在组件JSP代码中，您可以引用超类型组件提供的脚本，就像它们包含在组件中一样。

1. 在CRXDE Lite中，将资产添加到 `/apps/mywebsite/components/contentpage` 节点。

   1. 选择 `/apps/mywebsite/components/contentpage` 节点。
   1. 在“属性”选项卡的底部，键入以下属性值，然后单击“添加”：

      * **[!UICONTROL 名称]**:sling:resourceSuperType
      * **[!UICONTROL 类型]**:字符串
      * **[!UICONTROL 值]**:foundation/components/page
   1. 单击 **[!UICONTROL 全部保存]**.


1. 打开 `contentpage.jsp` 文件下 `/apps/mywebsite/components/contentpage` 和会将现有代码替换为以下代码：

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@page session="false" contentType="text/html; charset=utf-8" %><%
   %><!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "https://www.w3.org/TR/html4/strict.dtd">
   <html>
   <cq:include script="head.jsp"/>
   <cq:include script="body.jsp"/>
   </html>
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 如下所示：

   ![chlimage_1-5](assets/chlimage_1-5.jpeg)

   打开页面源，以查看head.jsp和body.jsp脚本生成的javascript和HTML元素。 以下脚本代码片段会在您打开页面时打开Sidekick:

   ```java
   CQ.WCM.launchSidekick("/content/mywebsite/en/products",
               {propsDialog: "/libs/foundation/components/page/dialog",
                  locked: false locked: false
                }); 
   ```

#### 使用您自己的脚本 {#using-your-own-scripts}

在此部分中，您可以创建多个脚本，每个脚本都生成页面主体的一部分。 然后，在pagecontent组件中创建body.jsp文件以覆盖AEM Page组件的body.jsp。 在body.jsp文件中，包含用于生成页面主体不同部分的脚本。

**提示：** 当组件包含的文件与组件超类型中的文件具有相同的名称和相对位置时，将调用 *覆盖*.

1. 在CRXDE Lite中，创建文件 `left.jsp` 在 `/apps/mywebsite/components/contentpage`:

   1. 右键单击节点 `/apps/mywebsite/components/contentpage`，然后选择 **[!UICONTROL 创建]** then **[!UICONTROL 创建文件]**.
   1. 在窗口中，键入 `left.jsp` 作为**名称**，然后单击 **[!UICONTROL 确定]**.

1. 编辑文件 `left.jsp` 要删除现有内容并将其替换为以下代码：

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="left">
   <div>logo</div>
   <div>newslist</div>
   <div>search</div>
   </div>
   ```

1. 保存更改。
1. 在CRXDE Lite中，创建文件 `center.jsp` 在 `/apps/mywebsite/components/contentpage`:

   1. 右键单击节点 `/apps/mywebsite/components/contentpage`，选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建文件]**.
   1. 在对话框中，键入 `center.jsp` as **[!UICONTROL 名称]** 单击 **[!UICONTROL 确定]**.

1. 编辑文件 `center.jsp` 要删除现有内容并将其替换为以下代码，请执行以下操作：

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="center">
   <div>trail</div>
   <div>title</div>
   <div>parsys</div>
   </div>
   ```

1. 保存更改。
1. 在CRXDE Lite中，创建文件 `right.jsp` 在 `/apps/mywebsite/components/contentpage`:

   1. 右键单击节点 `/apps/mywebsite/components/contentpage`，选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建文件]**.
   1. 在对话框中，键入 `right.jsp` as **[!UICONTROL 名称]** 单击 **[!UICONTROL 确定]**.

1. 编辑文件 `right.jsp` 要删除现有内容并将其替换为以下代码：

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><div class="right">
   <div>iparsys</div>
   </div>
   ```

1. 保存更改。
1. 在CRXDE Lite中，创建文件 `body.jsp` 在 `/apps/mywebsite/components/contentpage`:
1. 编辑文件 `body.jsp` 要删除现有内容并将其替换为以下代码：

   ```java
   <%@include file="/libs/foundation/global.jsp"%><%
   %><body>
   <div id="CQ">
   <div class="topnav">topnav</div>
   <div class="content">
   <cq:include script="left.jsp" />
   <cq:include script="center.jsp" />
   <cq:include script="right.jsp" />
   </div>
   <div class="footer">
   <div class="toolbar">toolbar</div>
   </div>
   </div>
   </body>
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 如下所示：

   ![chlimage_1-6](assets/chlimage_1-6.jpeg)

### 创建顶部导航组件 {#creating-the-top-navigation-component}

在此部分中，您将创建一个组件，以显示指向网站所有顶级页面的链接，以便轻松导航。 此组件内容显示在使用内容页面模板创建的所有页面的顶部。

在顶部导航组件(topnav)的第一个版本中，导航项目仅为文本链接。 在第二个版本中，您使用图像导航链接实施topnav。

您的顶部导航将如下所示：

![chlimage_1-114](assets/chlimage_1-114.png)

#### 创建顶部导航组件 {#creating-the-top-navigation-component-1}

1. 在CRXDE Lite中，右键单击 `/apps/mywebsite/components`，选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建组件]**.
1. 在 **[!UICONTROL 创建组件]** 窗口，输入以下内容：

   * **[!UICONTROL 标签]**: `topnav`
   * **[!UICONTROL 标题]**: `My Top Navigation Component`
   * **[!UICONTROL 描述]**: `This is My Top Navigation Component`

1. 单击 **[!UICONTROL 下一个]** 直到您来到您单击的最后一个窗口 **[!UICONTROL 确定]**. 保存更改。

#### 使用文本链接创建顶部导航脚本 {#creating-the-top-navigation-script-with-textual-links}

将渲染脚本添加到topnav以生成指向子页面的文本链接：

1. 在CRXDE Lite中，打开文件 `topnav.jsp` 在 `/apps/mywebsite/components/topnav`.
1. 复制并粘贴以下代码以替换其中的代码：

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><% 
   %><%@ page import="java.util.Iterator,
           com.day.text.Text, 
           com.day.cq.wcm.api.PageFilter, com.day.cq.wcm.api.Page" %><% 
       /* get starting point of navigation */
       Page navRootPage = currentPage.getAbsoluteParent(2); 
       if (navRootPage == null && currentPage != null) { 
       navRootPage = currentPage; 
       }
       if (navRootPage != null) { 
           Iterator<Page> children = navRootPage.listChildren(new PageFilter(request));
           while (children.hasNext()) { 
               Page child = children.next(); 
               %><a href="<%= child.getPath() %>.html"><%=child.getTitle() %></a><% 
           } 
       } 
   %> 
   ```

#### 包括内容页面组件中的顶部导航 {#including-top-navigation-in-the-contentpage-component}

要在内容页面组件中包含topnav，请执行以下操作：

1. 在CRXDE Lite中，打开 `body.jsp` 在 `/apps/mywebsite/components/contentpage`和替换：

   ```xml
   <div class="topnav">topnav</div>
   ```

   替换为:

   ```xml
   <cq:include path="topnav" resourceType="mywebsite/components/topnav" />
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 顶部导航如下所示：

   ![chlimage_1-115](assets/chlimage_1-115.png)

#### 使用字幕增强页面 {#enhancing-pages-with-subtitles}

的 **[!UICONTROL 页面]** 组件定义允许您为页面提供字幕的属性。 添加提供页面内容相关信息的字幕。

1. 在浏览器中，打开 **[!UICONTROL 产品]** 页面。
1. 在Sidekick上 **[!UICONTROL 页面]** ，单击 **[!UICONTROL 页面属性]**.
1. 在 **[!UICONTROL 基本]** ，展开 **[!UICONTROL 更多标题和描述]** 和 **[!UICONTROL 子标题]** 属性，类型 `what we do`. 单击&#x200B;**[!UICONTROL 确定]**。
1. 重复上述步骤以添加子标题 **关于我们的服务** 到 **[!UICONTROL 服务]** 页面。
1. 重复上述步骤以添加子标题 **我们赢得的信任** 到 **[!UICONTROL 客户]** 页面。

   **提示：** 在CRXDE Lite中，选择/content/mywebsite/en/products/jcr:content节点以查看是否添加了子标题属性。

#### 使用图像链接增强顶部导航 {#enhance-top-navigation-by-using-image-links}

增强topnav组件的渲染脚本，以便将图像链接而不是超文本用于导航控件。 该图像包括链接目标的标题和子标题。

本练习表明 [Sling请求处理](/help/sites-developing/the-basics.md#sling-request-processing). topnav.jsp脚本将被修改为调用一个脚本，该脚本会动态生成用于页面导航链接的图像。 在本练习中，Sling会解析图像源文件的URL，以确定用于渲染图像的脚本。

例如，指向产品页面的图像链接的来源可以是http://localhost:4502/content/mywebsite/en/products.navimage.png。 Sling会解析此URL以确定资源类型以及用于呈现资源的脚本：

1. Sling确定资源的路径 `/content/mwebysite/en/products.png.`
1. Sling将此路径与 `/content/mywebsite/en/products` 节点。
1. Sling确定 `sling:resourceType` 的 `mywebsite/components/contentpage`.

1. Sling会在此组件中找到与URL选择器( `navimage`)和文件扩展名( `png`)。

在本练习中，Sling会将这些URL与您创建的/apps/mywebsite/components/contentpage/navimage.png.java脚本相匹配。

1. 在CRXDE Lite中，打开 `topnav.jsp` 在 `/apps/mywebsite/components/topnav.`找到锚点元素的内容（第14行）：

   ```xml
   <%=child.getTitle() %>
   ```

1. 将锚点内容替换为以下代码：

   ```xml
   <img alt="<%= child.getTitle() %>" src="<%= child.getPath() %>.navimage.png">
   ```

1. 保存更改。
1. 右键单击 `/apps/mywebsite/components/contentpage` 节点，单击 **[!UICONTROL 创建>创建文件]**.
1. 在 **[!UICONTROL 创建文件]** 窗口，作为 **[!UICONTROL 名称]**，类型 `navimage.png.java`.

   .java文件名扩展名表示Sling应使用Apache Sling脚本Java支持来编译脚本和创建Servlet。

1. 将以下代码复制到 `navimage.png.java.`该代码扩展了AbstractImageServlet类：

   * [AbstractImageServlet](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/commons/AbstractImageServlet.html) 创建用于存储当前资源属性的ImageContext对象。
   * 资源的父页面将从ImageContext对象中提取。 然后获得页面标题和字幕。
   * [ImageHelper](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/ImageHelper.html) 用于从网站设计的navimage_bg.jpg文件、页面标题和页面子标题生成图像。

   ```java
   package apps.mywebsite.components.contentpage;
   
   import java.awt.Color; 
   import java.awt.Paint; 
   import java.awt.geom.Rectangle2D; 
   
   import java.io.IOException;
   import javax.jcr.RepositoryException; 
   
   import com.day.cq.wcm.api.Page; 
   import com.day.cq.wcm.api.PageManager; 
   import com.day.cq.wcm.api.components.Component; 
   import com.day.cq.wcm.api.designer.Designer;
   
   import com.day.cq.commons.SlingRepositoryException; 
   import com.day.cq.wcm.commons.WCMUtils; 
   import com.day.cq.wcm.commons.AbstractImageServlet; 
   import com.day.cq.commons.ImageHelper; 
   
   import com.day.image.Font; 
   import com.day.image.Layer; 
   
   import org.apache.sling.api.SlingHttpServletRequest; 
   import org.apache.sling.api.SlingHttpServletResponse; 
   import org.apache.sling.api.resource.Resource; 
   import org.apache.sling.api.servlets.SlingSafeMethodsServlet; 
   
   /**
     * Renders the navigation image
     */ 
   public class navimage_png extends AbstractImageServlet {
   
         protected Layer createLayer(ImageContext ctx)
                throws RepositoryException, IOException {
            PageManager pageManager = ctx.resolver.adaptTo(PageManager.class);
            Page currentPage = pageManager.getContainingPage(ctx.resource);
   
            /* constants for image appearance */
            int scale = 6;
            int paddingX = 24;
            int paddingY = 24;
            Color bgColor = new Color(0x004a565c, true);
   
            /* obtain the page title */
            String title = currentPage.getTitle();
            if (title == null) {
                title = currentPage.getName();
            }
   
            /* format the title text */
            title = title.toUpperCase();
            Paint titleColor = Color.WHITE;
            Font titleFont = new Font("Myriad Pro", 10 * scale, Font.BOLD);
            int titleBase = 10 * scale;
   
            /* obtain and format the page subtitle */
            String subtitle = currentPage.getProperties().get("subtitle", "");
            Paint subtitleColor = new Color(0xffa9afb1, true);
            Font subTitleFont = new Font("Tahoma", 7);
            int subTitleBase = 20;
   
            /* create a layer that contains the background image from the mywebsite design */
            Designer dg = ctx.resolver.adaptTo(Designer.class);
            String imgPath = new String(dg.getDesignPath(currentPage)+"/images/navimage_bg.jpg");
            Layer bg = ImageHelper.createLayer(ctx.resolver.resolve(imgPath));
   
            /* draw the title text (4 times bigger) */
            Rectangle2D titleExtent = titleFont.getTextExtent(0, 0, 0, 0, title, Font.ALIGN_LEFT, 0, 0);
            Rectangle2D subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
   
            /* ensure subtitleExtent is wide enough */
            if ( subtitle.length() > 0 ) {
                int titleWidth = (int)titleExtent.getWidth() / scale;
                if ( subtitleExtent.getWidth() > titleWidth && subtitleExtent.getWidth() + 2 * paddingX >
    bg.getWidth() ) {
                    int charWidth = (int)subtitleExtent.getWidth() / subtitle.length();
                    int maxWidth = (bg.getWidth() > titleWidth + 2  * paddingX ? bg.getWidth() - 2 * paddingX : titleWidth);
                    int len = (maxWidth - ( 2 * charWidth) ) / charWidth;
                    subtitle = subtitle.substring(0, len) + "...";
                    subtitleExtent = subTitleFont.getTextExtent(0, 0, 0, 0, subtitle, Font.ALIGN_LEFT, 0, 0);
                }
            }
            int width = Math.max((int) titleExtent.getWidth(), (int) subtitleExtent.getWidth());
           /* create the text layer */
            Layer text = new Layer(width, (int) titleExtent.getHeight() + 40, new Color(0x01ffffff, true));
            text.setPaint(titleColor);
            text.drawText(0, titleBase, 0, 0, title, titleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0);
            text.resize(text.getWidth() / scale, text.getHeight() / scale);
            text.setX(0);
            text.setY(0);
   
            if (subtitle.length() > 0) {
                /* draw the subtitle normal sized */
                text.setPaint(subtitleColor);
                text.drawText(0, subTitleBase, 0, 0, subtitle, subTitleFont, Font.ALIGN_LEFT | Font.ALIGN_BASE, 0, 0); 
            }
   
            /* merge the image and text layers */
            text.setY(paddingY);
            text.setX(paddingX);
            text.setBackgroundColor(bgColor);
   
            int bgWidth = bg.getWidth();
            if ( text.getWidth() + 2 * paddingX > bgWidth ) {
                bgWidth = text.getWidth() + 2 * paddingX;
                bg.resize(bgWidth, bg.getHeight());
            }
            bg.merge(text);
   
            return bg;
        }
    }
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 顶部导航现在如下所示：

   ![screen_shot_2012-03-07at10047pm](assets/screen_shot_2012-03-07at10047pm.png)

### 创建列表子组件 {#creating-the-list-children-component}

创建列表子组件，以生成包含页面标题、描述和日期（例如，产品页面）的页面链接列表。 这些链接将定位当前页面或组件对话框中指定的根页面的子页面。

![chlimage_1-116](assets/chlimage_1-116.png)

#### 创建产品页面 {#creating-product-pages}

创建位于 **[!UICONTROL 产品]** 页面。 对于描述两个特定产品的每个页面，您需要设置标题、描述和日期。

1. 在 **[!UICONTROL 网站]** 页面，选择 **[!UICONTROL 网站/我的网站/英语/产品]** 项目，单击 **[!UICONTROL 新建>新建页面]**.
1. 在对话框中，输入以下属性值，然后单击 **[!UICONTROL 创建]**:

   * **[!UICONTROL 标题]**:产品1.
   * **[!UICONTROL 名称]**:product1.
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

1. 使用以下属性值在产品下创建另一个页面：

   * **[!UICONTROL 标题]**:产品2
   * **[!UICONTROL 名称]**:product2
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

1. 在CRXDE Lite中，为产品1页面设置描述和日期：

   1. 选择 `/content/mywebsite/en/products/product1/jcr:content` 节点。
   1. 在 **[!UICONTROL 属性]** ，请输入以下值：

      * **[!UICONTROL 名称]**: `jcr:description`
      * **[!UICONTROL 类型]**: `String`
      * **[!UICONTROL 值]**: `This is a description of the Product 1!.`
   1. 单击 **[!UICONTROL 添加]**.
   1. 在 **[!UICONTROL 属性]** ，请使用以下值创建其他属性：

      * **[!UICONTROL 名称]**:日期
      * **[!UICONTROL 类型]**:字符串
      * **[!UICONTROL 值]**:02/14/2008
      * 单击 **[!UICONTROL 添加]**.
   1. 单击 **[!UICONTROL 全部保存]**.



1. 在CRXDE Lite中，为产品2页面设置描述和日期：

   1. 选择 `/content/mywebsite/en/products/product2/jcr:content` 节点。
   1. 在 **[!UICONTROL 属性]** ，请输入以下值：

      * **[!UICONTROL 名称]**:jcr:description
      * **[!UICONTROL 类型]**:字符串
      * **[!UICONTROL 值]**:这是对产品2！的描述。
   1. 单击 **[!UICONTROL 添加]**.
   1. 在同一文本框中，将以前的值替换为以下值：

      * **[!UICONTROL 名称]**:日期
      * **[!UICONTROL 类型]**:字符串
      * **[!UICONTROL 值]**:05/11/2012
      * 单击 **[!UICONTROL 添加]**.
   1. 单击 **[!UICONTROL 全部保存]**.



#### 创建列表子组件 {#creating-the-list-children-component-1}

要创建列表子组件，请执行以下操作：

1. 在CRXDE Lite中，右键单击 `/apps/mywebsite/components`，选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建组件]**.
1. 在对话框中，输入以下属性值，然后单击 **[!UICONTROL 下一个]**:

   * **[!UICONTROL 标签]**:列表子项。
   * **[!UICONTROL 标题]**:我的列表子项组件。
   * **[!UICONTROL 描述]**:这是我的列表子项组件。

1. 继续单击 **[!UICONTROL 下一个]** 直到 **[!UICONTROL 允许的子项]** 面板，然后单击 **[!UICONTROL 确定]**.

#### 创建列表子脚本 {#creating-the-list-children-script}

为列表子组件开发脚本。

1. 在CRXDE Lite中，打开文件 `listchildren.jsp` 在 `/apps/mywebsite/components/listchildren`.
1. 将默认代码替换为以下代码：

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="java.util.Iterator,
            com.day.cq.wcm.api.PageFilter"%><%
        /* Create a new Page object using the path of the current page */ 
         String listroot = properties.get("listroot", currentPage.getPath());
        Page rootPage = pageManager.getPage(listroot);
        /* iterate through the child pages and gather properties */
        if (rootPage != null) {
            Iterator<Page> children = rootPage.listChildren(new PageFilter(request));
            while (children.hasNext()) {
                Page child = children.next();
                String title = child.getTitle() == null ? child.getName() : child.getTitle();
                String date = child.getProperties().get("date","");
                %><div class="item">
                <a href="<%= child.getPath() %>.html"><b><%= title %></b></a>
                <span><%= date %></span><br>
                <%= child.getProperties().get("jcr:description","") %><br>
                </div><%
            }
        }
    %>
   ```

1. 保存更改。

#### 创建列表子项对话框 {#creating-the-list-children-dialog}

创建用于配置列表子组件属性的对话框。

1. 在列表子组件下创建对话框节点：

   1. 在CRXDE Lite中，右键单击 `/apps/mywebsite/components/listchildren`节点，单击 **[!UICONTROL 创建>创建对话框]**.
   1. 在对话框中，输入以下属性值，然后单击确定

      * **[!UICONTROL 标签]**: `dialog`
      * **[!UICONTROL 标题]**: `Edit Component` 单击 **[!UICONTROL 确定]**.

   ![screen_shot_2012-03-07at45818pm](assets/screen_shot_2012-03-07at45818pm.png)

   具有以下属性：

   ![screen_shot_2012-03-07at50415pm](assets/screen_shot_2012-03-07at50415pm.png)

1. 选择 `/apps/mywebsite/components/listchildren/dialog/items/items/tab1` 节点。
1. 在 **[!UICONTROL 属性]** ，请更改 **[!UICONTROL 标题]** 属性 `List Children`

   ![chlimage_1-117](assets/chlimage_1-117.png)

1. 选择 **tab1** 节点，单击 **[!UICONTROL 创建>创建节点]**，输入以下属性值，然后单击 **[!UICONTROL 确定]**:

   * **[!UICONTROL 名称]**:项目
   * **[!UICONTROL 类型]**:cq:WidgetCollection

   ![screen_shot_2012-03-07at51018pm](assets/screen_shot_2012-03-07at51018pm.png)

1. 使用以下属性值在项目节点下创建一个节点：

   * **[!UICONTROL 名称]**:利斯特罗
   * **[!UICONTROL 类型]**:cq:Widget

   ![screen_shot_2012-03-07at51031pm](assets/screen_shot_2012-03-07at51031pm.png)

1. 添加列表节点的属性以将其配置为文本字段。 下表中的每一行都表示一个属性。 完成后，单击 **[!UICONTROL 全部保存]**.

   | 名称 | 类型 | 价值 |
   |---|---|---|
   | fieldLabel | 字符串 | 列表根的路径 |
   | name | 字符串 | 。/listroot |
   | xtype | 字符串 | textfield |

   ![screen_shot_2012-03-07at51433pm](assets/screen_shot_2012-03-07at51433pm.png)

#### 在内容页面组件中包含列表子项 {#including-list-children-in-the-contentpage-component}

要在内容页面组件中包含列表子组件，请按如下步骤继续操作：

1. 在CRXDE Lite中，打开文件 `left.jsp` 在 `/apps/mywebsite/components/contentpage` 并找到以下代码（第4行）：

   ```xml
   <div>newslist</div>
   ```

1. 将该代码替换为以下代码：

   ```xml
   <cq:include path="newslist" resourceType="mywebsite/components/listchildren" />
   ```

1. 保存更改。

#### 在页面中查看列表子项 {#viewing-list-children-in-a-page}

要查看此组件的完整操作，您可以查看产品页面：

* 未定义父页面（“列表根路径”）时。
* 定义父页面（“列表根路径”）时。

1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 列表子组件如下所示：

   ![chlimage_1-118](assets/chlimage_1-118.png)

1. ![chlimage_1-119](assets/chlimage_1-119.png)

1. 作为列表根的路径，输入： `/content/mywebsite/en`. 单击&#x200B;**[!UICONTROL 确定]**。页面上的列表子组件现在如下所示：

   ![chlimage_1-120](assets/chlimage_1-120.png)

### 创建徽标组件 {#creating-the-logo-component}

创建显示公司徽标并提供指向网站主页的链接的组件。 该组件包含一个设计模式对话框，以便将属性值存储在站点设计(/etc/designs/mywebsite)中：

* 属性值适用于添加到使用该设计的页面的组件的所有实例。
* 属性可以使用使用设计页面上组件的任何实例进行配置。

设计模式对话框包含用于设置图像和链接路径的属性。 徽标组件将位于网站所有页面的左上方。

将如下所示：

![chlimage_1-121](assets/chlimage_1-121.png)

>[!NOTE]
>
>Adobe Experience Manager提供功能更全的徽标组件( `/libs/foundation/components/logo`)。

#### 创建徽标组件节点 {#creating-the-logo-component-node}

要创建徽标组件，请按照以下步骤操作：

1. 在CRXDE Lite中，右键单击/apps/mywebsite/components，选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建组件]**.
1. 在创建组件对话框中，输入以下属性值，然后单击下一步：

   * **[!UICONTROL 标签]**: `logo`.
   * **[!UICONTROL 标题]**: `My Logo Component`.
   * **[!UICONTROL 描述]**: `This is My Logo Component`.

1. 单击下一步，直到您到达对话框的最终面板，然后单击 **[!UICONTROL 确定]**.

#### 创建徽标脚本 {#creating-the-logo-script}

本节介绍如何创建脚本以显示带有指向主页链接的徽标图像。

1. 在CRXDE Lite中，打开文件 `logo.jsp` 在 `/apps/mywebsite/components/logo`.
1. 以下代码会创建指向网站主页的链接并添加对徽标图像的引用。 将代码复制到 `logo.jsp`:

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.text.Text,
                      com.day.cq.wcm.foundation.Image,
                      com.day.cq.commons.Doctype" %><%
       /* obtain the path for home */
       long absParent = currentStyle.get("absParent", 2L);
       String home = Text.getAbsoluteParent(currentPage.getPath(), (int) absParent);
       /* obtain the image */
       Resource res = currentStyle.getDefiningResource("imageReference");
       if (res == null) {
           res = currentStyle.getDefiningResource("image");
       }
       /* if no image use text link, otherwise draw the image */
       %>
   <a href="<%= home %>.html"><%
       if (res == null) {
           %>Home<%
       } else {
           Image img = new Image(res);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out);
       }
       %></a>
   ```

1. 保存更改。

#### 创建徽标设计对话框 {#creating-the-logo-design-dialog}

创建用于在设计模式下配置徽标组件的对话框。 必须命名设计模式对话框节点 `design_dialog`.

1. 在徽标组件下创建对话框节点：

   1. 右键单击 `/apps/mywebsite/components/logo` 节点，单击 **[!UICONTROL 创建>创建对话框]**.
   1. 键入以下属性值，然后单击 **[!UICONTROL 确定]**:

      * **[!UICONTROL 标签]** `design_dialog`
      * **[!UICONTROL 标题]** `Logo (Design)`

1. 右键单击design_dialog分支中的tab1节点，然后单击“删除”。 单击 **[!UICONTROL 全部保存]**.
1. 在 `design_dialog/items/items`节点，创建名为 `img` 类型 `cq:Widget`. 添加以下属性，然后单击 **[!UICONTROL 全部保存]**:

   | 名称 | 类型 | 价值 |
   |---|---|---|
   | fileNameParameter | 字符串 | 。/imageName |
   | fileReferenceParameter | 字符串 | 。/imageReference |
   | name | 字符串 | 。/图像 |
   | 标题 | 字符串 | 图像 |
   | xtype | 字符串 | html5smartimage |

   ![chlimage_1-122](assets/chlimage_1-122.png)

#### 创建徽标渲染脚本 {#creating-the-logo-render-script}

创建脚本以检索徽标图像并将其写入页面。

1. 右键单击徽标组件节点，然后单击 **[!UICONTROL 创建>创建文件]** 创建名为img.GET.java的脚本文件。
1. 打开文件，将以下代码复制到文件中，然后单击 **[!UICONTROL 全部保存]**:

```java
package apps.mywebsite.components.logo;

import java.io.IOException;
import java.io.InputStream;

import javax.jcr.RepositoryException;
import javax.jcr.Property;
import javax.servlet.http.HttpServletResponse;

import com.day.cq.wcm.foundation.Image;
import com.day.cq.wcm.commons.RequestHelper;
import com.day.cq.wcm.commons.WCMUtils;
import com.day.cq.wcm.commons.AbstractImageServlet;
import com.day.cq.commons.SlingRepositoryException;
import com.day.image.Layer;
import org.apache.commons.io.IOUtils;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ValueMap;
import org.apache.sling.api.servlets.SlingSafeMethodsServlet;

/**
 * Renders an image
 */
public class img_GET extends AbstractImageServlet {

    protected Layer createLayer(ImageContext c)
            throws RepositoryException, IOException {
        /* don't create the layer yet. handle everything later */
        return null;
    }

    protected void writeLayer(SlingHttpServletRequest req,
                              SlingHttpServletResponse resp,
                              ImageContext c, Layer layer)
            throws IOException, RepositoryException {

        Image image = new Image(c.resource);
        image.setItemName(Image.NN_FILE, "image");
        image.setItemName(Image.PN_REFERENCE, "imageReference");
        if (!image.hasContent()) {
            resp.sendError(HttpServletResponse.SC_NOT_FOUND);
            return;
        }
        /* get pure layer */
        layer = image.getLayer(false, false, false);

        /* do not re-encode layer, just spool */
        Property data = image.getData();
        InputStream in = data.getStream();
        resp.setContentLength((int) data.getLength());
        String contentType = image.getMimeType();
        if (contentType.equals("application/octet-stream")) {
            contentType=c.requestImageType;
        }
        resp.setContentType(contentType);
        IOUtils.copy(in, resp.getOutputStream());
        in.close();

        resp.flushBuffer();
    }
}
```

#### 将徽标组件添加到Contentpage组件 {#adding-the-logo-component-to-the-contentpage-component}

1. 在CRXDE Lite中，打开 `left.jsp` 在 `/apps/mywebsite/components/contentpage file` 并找到以下代码行：

   ```xml
   <div>logo</div>
   ```

1. 将该代码替换为以下代码行：

   ```xml
   <cq:include path="logo" resourceType="mywebsite/components/logo" />
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 徽标如下所示，尽管当前仅显示基础链接：

   ![chlimage_1-123](assets/chlimage_1-123.png)

#### 在页面中设置徽标图像 {#setting-the-logo-image-in-a-page}

本节介绍如何使用设计模式对话框将图像设置为徽标。

1. 使用 **[!UICONTROL 产品]** 页面，单击 **[!UICONTROL 设计]** 按钮以输入 **[!UICONTROL 设计]** 模式。

   ![](do-not-localize/chlimage_1-10.png)

1. 在徽标栏的设计中，单击 **[!UICONTROL 编辑]** 使用对话框编辑徽标组件的设置。
1. 在对话框中，单击 **[!UICONTROL 图像]** 选项卡，浏览 `logo.png` 从 `mywebsite.zip` ，然后单击 **[!UICONTROL 确定]**.

   ![chlimage_1-124](assets/chlimage_1-124.png)

1. 单击Sidekick标题栏上的三角形以返回 **[!UICONTROL 编辑]** 模式。

   ![chlimage_1-7](assets/chlimage_1-7.jpeg)

1. 在CRXDE Lite中，转到以下节点以查看存储的属性值：

   `/etc/designs/mywebsite/jcr:content/contentpage/logo`

### 包括痕迹导航组件 {#including-the-breadcrumb-component}

在此部分中，您包括痕迹导航（跟踪）组件，该组件是基础组件之一。

1. 在CRXDE Lite中，浏览 `/apps/mywebsite/components/contentpage`，打开文件 `center.jsp` 和替换：

   ```java
   <div>trail</div>
   ```

   替换为:

   ```xml
   <cq:include path="trail" resourceType="foundation/components/breadcrumb" />
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品1]** 页面。 跟踪组件如下所示：

   ![chlimage_1-125](assets/chlimage_1-125.png)

### 包括标题组件 {#including-the-title-component}

在此部分中，您包括标题组件，该组件是基础组件之一。

1. 在CRXDE Lite中，浏览 `/apps/mywebsite/components/contentpage`，打开文件 `center.jsp` 和替换：

   ```xml
   <div>title</div>
   ```

   替换为:

   ```xml
   <cq:include path="title" resourceType="foundation/components/title" />
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 标题组件如下所示：

   ![chlimage_1-126](assets/chlimage_1-126.png)

>[!NOTE]
>您可以在 **[!UICONTROL 编辑]** 模式。

### 包括段落系统组件 {#including-the-paragraph-system-component}

段落系统(parsys)是网站的重要组成部分，因为它管理着段落列表。 它允许作者向页面中添加段落组件并提供结构。

将parsys组件（基础组件之一）添加到内容页面组件中。

1. 在CRXDE Lite中，浏览 `/apps/mywebsite/components/contentpage`，打开文件 `center.jsp` 并找到以下代码行：

   ```xml
   <div>parsys</div>
   ```

1. 将该行代码替换为以下代码，然后保存更改：

   ```xml
   <cq:include path="par" resourceType="foundation/components/parsys" />
   ```

1. 在浏览器中，刷新 **[!UICONTROL 产品]** 页面。 它现在具有parsys组件，该组件如下所示：

   ![chlimage_1-127](assets/chlimage_1-127.png)

### 创建图像组件 {#creating-the-image-component}

创建在段落系统中显示图像的组件。 为了节省时间，图像组件将创建为徽标组件的副本，并进行一些属性更改。

>[!NOTE]
>
>Adobe Experience Manager提供了功能更全的图像组件( `/libs/foundation/components/image`)。

#### 创建图像组件 {#creating-the-image-component-1}

1. 右键单击 `/apps/mywebsite/components/logo` 节点，单击 **[!UICONTROL 复制]**.
1. 右键单击 `/apps/mywebsite/components` 节点，单击 **[!UICONTROL 粘贴]**.
1. 右键单击 `Copy of logo` 节点，单击 **[!UICONTROL 重命名]**，删除现有文本和类型 `image`.

1. 选择 `image` 组件节点，并更改以下属性值：

   * `jcr:title:` 我的图像组件。
   * `jcr:description`:这是我的图像组件。

1. 将资产添加到 `image` 具有以下属性值的节点：

   * **[!UICONTROL 名称]**:componentGroup
   * **[!UICONTROL 类型]**:字符串
   * **[!UICONTROL 值]**:MyWebsite

1. 在 `image` 节点，重命名 `design_dialog` 节点到 `dialog`.

1. 重命名 `logo.jsp` to `image.jsp.`

1. 打开img.GET.java ，并将包更改为 `apps.mywebsite.components.image`.

![chlimage_1-128](assets/chlimage_1-128.png)

#### 创建图像脚本 {#creating-the-image-script}

本节将介绍如何创建图像脚本。

1. 打开 `/apps/mywebsite/components/image/` `image.jsp`
1. 将现有代码替换为以下代码，然后保存更改：

   ```xml
   <%@include file="/libs/foundation/global.jsp"%><%
   %><%@ page import="com.day.cq.commons.Doctype,
                       com.day.cq.wcm.foundation.Image,
                       com.day.cq.wcm.api.components.DropTarget,
                       com.day.cq.wcm.api.components.EditConfig,
                       com.day.cq.wcm.commons.WCMUtils" %><%
    /* global.jsp provides access to the current resource through the resource object */
           Image img = new Image(resource);
           img.setItemName(Image.NN_FILE, "image");
           img.setItemName(Image.PN_REFERENCE, "imageReference");
           img.setSelector("img");
           img.setDoctype(Doctype.fromRequest(request));
           img.setAlt("Home");
           img.draw(out); %>
   ```

1. 保存更改。

#### 创建图像cq:editConfig节点 {#creating-the-image-cq-editconfig-node}

的 `cq:editConfig` 通过节点类型，您可以在编辑组件的属性时配置组件的某些行为。

在此部分中，您使用cq:editConfig节点来允许将资产从内容查找器拖动到图像组件中。

1. 在CRXDE Lite中，在节点/apps/mywebsite/components/image下，创建一个新节点，如下所示：

   * **[!UICONTROL 名称]**:cq:editConfig。
   * **[!UICONTROL 类型]**:cq:EditConfig。

1. 在节点cq:editConfig下，创建一个新节点，如下所示：

   * **[!UICONTROL 名称]**:cq:dropTargets。
   * **[!UICONTROL 类型]**:cq:DropTargetConfig 。

1. 在节点cq:dropTargets下，创建一个新节点，如下所示：

   * **[!UICONTROL 名称]**:图像。
   * **[!UICONTROL 类型]**:nt:unstructured。

1. 在CRXDE中，按如下方式设置属性：

| 名称 | 类型 | 价值 |
|---|---|---|
| 接受 | 字符串 | image/(gif) | jpeg | png) |
| 组 | 字符串 | 媒体 |
| propertyName | 字符串 | 。/imageReference |

![chlimage_1-129](assets/chlimage_1-129.png)

#### 添加图标 {#adding-the-icon}

在此部分中，当图标在Sidekick中列出时，您会在图像组件旁边添加要显示的图标：

1. 在CRXDE Lite中，右键单击文件 `/libs/foundation/components/image/icon.png` 选择 **[!UICONTROL 复制]**.
1. 右键单击节点 `/apps/mywebsite/components/image` 单击 **[!UICONTROL 粘贴]**，然后单击 **[!UICONTROL 全部保存]**.

#### 使用图像组件 {#using-the-image-component}

在此部分中，您将查看 **[!UICONTROL 产品]** 页面，并将图像组件添加到段落系统。

1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。
1. 在Sidekick中，单击 **[!UICONTROL 设计模式]** 图标。
1. 单击 **[!UICONTROL 编辑]** 按钮来编辑段落的设计对话框。
1. 在对话框中， **[!UICONTROL 允许的组件]** 中；导航到 **[!UICONTROL MyWebsite]**，选择 **[!UICONTROL 我的图像组件]** 单击 **[!UICONTROL 确定]**.
1. 返回 **[!UICONTROL 编辑模式]**.
1. 双击Parsys框架(打开 **[!UICONTROL 将组件或资产拖动到此处]**)。 的 **[!UICONTROL 插入新组件]** 和 **[!UICONTROL Sidekick]** 选择器如下所示：

   ![chlimage_1-8](assets/chlimage_1-8.jpeg)

### 包括工具栏组件 {#including-the-toolbar-component}

在此部分中，您包括工具栏组件，该组件是基础组件之一。

在编辑模式和设计模式下，您有多个选项。

1. 在CRXDE Lite中，导航到 `/apps/mywebsite/components/contentpage`，打开 `body.jsp` 并找到以下代码：

   ```java
   <div class="toolbar">toolbar</div>
   ```

1. 将该代码替换为以下代码，然后保存更改。

   ```java
   <cq:include path="toolbar" resourceType="foundation/components/toolbar"/>
   ```

1. 在“AEM网站”页面的文件夹树中，选择 `Websites/My Website/English`，然后单击 **[!UICONTROL 新建>新建页面]**. 指定以下属性值，然后单击创建：

   * **[!UICONTROL 标题]**:工具栏
   * 选择 **[!UICONTROL “我的网站内容”页面模板]**

1. 在页面列表中，右键单击 **[!UICONTROL 工具栏]** 页面，单击 **[!UICONTROL 属性]**. 选择 **[!UICONTROL 在导航中隐藏]**，然后单击 **[!UICONTROL 确定]**.

   的 **[!UICONTROL 在导航中隐藏]** 选项可阻止页面在导航组件中显示，例如topnav和listchildren。

1. 在 **[!UICONTROL 工具栏]**，请创建以下页面：

   * 联系人
   * 反馈
   * 登录
   * 搜索

1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 如下所示：

   ![chlimage_1-130](assets/chlimage_1-130.png)

### 创建搜索组件 {#creating-the-search-component}

在此部分中，您可以创建组件以在网站上搜索内容。 此搜索组件可放置在任何页面的段落系统中（例如，放置在专门的搜索结果页面上）。

您的搜索输入框将在 **[!UICONTROL 英语]** 页面：

![chlimage_1-131](assets/chlimage_1-131.png)

#### 创建搜索组件 {#creating-the-search-component-1}

1. 在CRXDE Lite中，右键单击 `/apps/mywebsite/components`，选择 **[!UICONTROL 创建]**，则 **[!UICONTROL 创建组件]**.
1. 使用对话框配置组件：

   1. 在第一个面板中，指定以下属性值：

      * **[!UICONTROL 标签]**:搜索
      * **[!UICONTROL 标题]**:我的搜索组件
      * **[!UICONTROL 描述]**:这是我的搜索组件
      * **[!UICONTROL 组]**:MyWebsite
   1. 单击 **[!UICONTROL 下一个]**，然后单击 **[!UICONTROL 下一个]** 再次。
   1. 在 **[!UICONTROL 允许的父项]** 面板，单击 **[!UICONTROL +]** 按钮和类型 `*/parsys`.
   1. 单击 **[!UICONTROL 下一个]** 然后单击 **[!UICONTROL 确定]**.


1. 单击 **[!UICONTROL 全部保存]**.
1. 复制以下节点并将其粘贴到 `apps/mywebsite/components/search` 节点：

   * `/libs/foundation/components/search/dialog`
   * `` `/libs/foundation/components/search/i18n`
   * `/libs/foundation/components/search/icon.png`

1. 单击 **[!UICONTROL 全部保存]**.

#### 创建搜索脚本 {#creating-the-search-script}

本节介绍如何创建搜索脚本：

1. 打开 `/apps/mywebsite/components/search/search.jsp` 文件。
1. 将以下代码复制到 `search.jsp`:

   ```java
   <%@ page import="com.day.cq.wcm.foundation.Search,com.day.cq.tagging.TagManager" %>
   <%@include file="/libs/foundation/global.jsp" %><%
   %><cq:setContentBundle/><%
       Search search = new Search(slingRequest);
   
       String searchIn = (String) properties.get("searchIn");
       String requestSearchPath = request.getParameter("path");
       if (searchIn != null) {
           /* only allow the "path" request parameter to be used if it
            is within the searchIn path configured */
           if (requestSearchPath != null && requestSearchPath.startsWith(searchIn)) {
               search.setSearchIn(requestSearchPath);
           } else {
               search.setSearchIn(searchIn);
           }
       } else if (requestSearchPath != null) {
           search.setSearchIn(requestSearchPath);
       }
   
       pageContext.setAttribute("search", search);
       TagManager tm = resourceResolver.adaptTo(TagManager.class);
   %><c:set var="trends" value="${search.trends}"/><%
   %><center>
     <form action="${currentPage.path}.html">
       <input size="41" maxlength="2048" name="q" value="${fn:escapeXml(search.query)}"/>
       <input value="<fmt:message key="searchButtonText"/>" type="submit" />
     </form>
   </center>
   <br/>
   <c:set var="result" value="${search.result}"/>
   <c:choose>
     <c:when test="${empty result && empty search.query}">
     </c:when>
     <c:when test="${empty result.hits}">
       <c:if test="${result.spellcheck != null}">
         <p><fmt:message key="spellcheckText"/> <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${result.spellcheck}"/></c:url>"><b><c:out value="${result.spellcheck}"/></b></a></p>
       </c:if>
       <fmt:message key="noResultsText">
         <fmt:param value="${fn:escapeXml(search.query)}"/>
       </fmt:message>
     </c:when>
     <c:otherwise>
       <p class="searchmeta">Results ${result.startIndex + 1} - ${result.startIndex + fn:length(result.hits)} of ${result.totalMatches} for <b>${fn:escapeXml(search.query)}</b>. (${result.executionTime} seconds)</p>
      <br/>
   
     <div class="searchresults"> 
       <div class="results">
         <c:forEach var="hit" items="${result.hits}" varStatus="status">
           <div class="hit">
           <a href="${hit.URL}">${hit.title}</a>
           <div class="excerpt">${hit.excerpt}</div>
          <div class="hiturl"> ${hit.URL}<c:if test="${!empty hit.properties['cq:lastModified']}"> - <c:catch><fmt:formatDate value="${hit.properties['cq:lastModified'].time}" dateStyle="medium"/></c:catch></c:if> - <a href="${hit.similarURL}"><fmt:message key="similarPagesText"/></a>
           </div></div>
         </c:forEach>
       </div>
         <br/>
   
        <div class="searchRight">
             <c:if test="${fn:length(trends.queries) > 0}">
                 <p><fmt:message key="searchTrendsText"/></p>
                 <div class="searchTrends">
                     <c:forEach var="query" items="${trends.queries}">
                         <a href="<c:url value="${currentPage.path}.html"><c:param name="q" value="${query.query}"/></c:url>"><span style="font-size:${query.size}px"><c:out value="${query.query}"/></span></a>
                     </c:forEach>
                 </div>
             </c:if> 
             <c:if test="${result.facets.languages.containsHit}">
                 <p>Languages</p>
                 <c:forEach var="bucket" items="${result.facets.languages.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value='<%= new java.util.Locale((String) pageContext.getAttribute("bucketValue")).getDisplayLanguage(request.getLocale()) %>'/>
                     <c:choose>
                         <c:when test="${param.language != null}">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="language"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="language" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if> 
             <c:if test="${result.facets.tags.containsHit}">
                 <p>Tags</p>
                 <c:forEach var="bucket" items="${result.facets.tags.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="tag" value="<%= tm.resolve((String) pageContext.getAttribute("bucketValue")) %>"/>
                     <c:if test="${tag != null}">
                         <c:set var="label" value="${tag.title}"/>
                         <c:choose>
                             <c:when test="<%= request.getParameter("tag") != null && java.util.Arrays.asList(request.getParameterValues("tag")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="tag" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                             <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="tag" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                         </c:choose><br/>
                     </c:if>
                 </c:forEach>
             </c:if> 
             <c:if test="${result.facets.mimeTypes.containsHit}">
                 <jsp:useBean id="fileTypes" class="com.day.cq.wcm.foundation.FileTypes"/>
                 <p>File types</p>
                 <c:forEach var="bucket" items="${result.facets.mimeTypes.buckets}">
                     <c:set var="bucketValue" value="${bucket.value}"/>
                     <c:set var="label" value="${fileTypes[bucket.value]}"/>
                     <c:choose>
                         <c:when test="<%= request.getParameter("mimeType") != null && java.util.Arrays.asList(request.getParameterValues("mimeType")).contains(pageContext.getAttribute("bucketValue")) %>">${label} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:addParam name="mimeType" value="${bucket.value}"/></cq:requestURL>">${label} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
             <c:if test="${result.facets.lastModified.containsHit}">
                 <p>Last Modified</p>
                 <c:forEach var="bucket" items="${result.facets.lastModified.buckets}">
                     <c:choose>
                         <c:when test="${param.from == bucket.from && param.to == bucket.to}">${bucket.value} (${bucket.count}) - <a href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/></cq:requestURL>">remove filter</a></c:when>
                         <c:otherwise><a title="filter results" href="<cq:requestURL><cq:removeParam name="from"/><cq:removeParam name="to"/><c:if test="${bucket.from != null}"><cq:addParam name="from" value="${bucket.from}"/></c:if><c:if test="${bucket.to != null}"><cq:addParam name="to" value="${bucket.to}"/></c:if></cq:requestURL>">${bucket.value} (${bucket.count})</a></c:otherwise>
                     </c:choose><br/>
                 </c:forEach>
             </c:if>
   
         <c:if test="${fn:length(search.relatedQueries) > 0}">
   
          <br/><br/><div class="related">
           <fmt:message key="relatedSearchesText"/>
           <c:forEach var="rq" items="${search.relatedQueries}">
               <a href="${currentPage.path}.html?q=${rq}"><c:out value="${rq}"/></a>
           </c:forEach></div>
         </c:if>
         </div> 
   
         <c:if test="${fn:length(result.resultPages) > 1}">
           <div class="pagination"> 
               <fmt:message key="resultPagesText"/>
           <c:if test="${result.previousPage != null}">
             <a href="${result.previousPage.URL}"><fmt:message key="previousText"/></a>
           </c:if>
           <c:forEach var="page" items="${result.resultPages}">
             <c:choose>
               <c:when test="${page.currentPage}">${page.index + 1}</c:when>
               <c:otherwise>
                 <a href="${page.URL}">${page.index + 1}</a>
               </c:otherwise>
             </c:choose>
           </c:forEach>
           <c:if test="${result.nextPage != null}">
             <a href="${result.nextPage.URL}"><fmt:message key="nextText"/></a>
           </c:if>
           </div>
         </c:if>
         </div>
   
     </c:otherwise>
   </c:choose>
   ```

1. 保存更改。

#### 在内容页面组件中包含搜索框 {#including-a-search-box-in-the-contentpage-component}

要在内容页面的左部分包含搜索输入框，请按如下步骤继续操作：

1. 在CRXDE Lite中，打开文件 `left.jsp` 在 `/apps/mywebsite/components/contentpage` 并找到以下代码（第2行）：

   ```xml
   %><div class="left">
   ```

1. 插入以下代码 *之前* 那句话：

   ```java
   %><%@ page import="com.day.text.Text"%><%
   %><% String docroot = currentDesign.getPath(); 
   String home = Text.getAbsoluteParent(currentPage.getPath(), 2);%><%
   ```

1. 找到以下代码行：

   ```xml
   <div>search</div>
   ```

1. 将该代码替换为以下代码，然后保存更改。

   ```java
   <div class="form_1">
        <form class="geo" action="<%= home %>/toolbar/search.html" id="form" >
             <p>
                  <input class="geo" type="text" name="q"><br> 
                  <a href="<%= home %>/toolbar/search.html" class="link_1">advanced search</a> 
             </p>
        </form>
   </div>
   ```

1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 搜索组件如下所示：

   ![chlimage_1-132](assets/chlimage_1-132.png)

#### 在搜索页面中包含搜索组件 {#including-the-search-component-in-the-search-page}

在此部分中，您可以将搜索组件添加到段落系统。

1. 在浏览器中，打开 **搜索** 页面。
1. 在Sidekick中，单击 **[!UICONTROL 设计]** 模式图标。
1. 在段落设计块（在搜索标题下方）中，单击 **[!UICONTROL 编辑]**.
1. 在对话框中，向下滚动到 **[!UICONTROL 我的网站]** 群组，选择 **[!UICONTROL 我的搜索组件]** 单击 **[!UICONTROL 确定]**.
1. 在Sidekick上，单击三角形以返回 **[!UICONTROL 编辑]** 模式。
1. 拖动 **[!UICONTROL 我的搜索]** 组件从Sidekick移入parsys框架中。 如下所示：

   ![chlimage_1-133](assets/chlimage_1-133.png)

1. 导航到 **[!UICONTROL 产品]** 页面。 在输入框中搜索客户，然后按 **[!UICONTROL 输入]**. 系统会将您重定向到 **[!UICONTROL 搜索]** 页面。 切换到 **[!UICONTROL 预览]** 模式：输出的格式与以下内容类似：

   ![chlimage_1-134](assets/chlimage_1-134.png)

### 包括Iparsys组件 {#including-the-iparsys-component}

在此部分中，您包括继承段落系统(iparsys)组件，该组件是基础组件之一。 此组件允许您在父页面上创建段落结构，并让子页面继承这些段落。

对于此组件，您可以在编辑模式和设计模式下设置多个参数。

1. 在CRXDE Lite中，导航到 `/apps/mywebsite/components/contentpage`，打开文件 `right.jsp` 和替换：

   ```java
   <div>iparsys</div>
   ```

   替换为:

   ```java
   <cq:include path="rightpar" resourceType="foundation/components/iparsys" />
   ```

1. 保存更改。
1. 在浏览器中，重新加载 **[!UICONTROL 产品]** 页面。 整个页面如下所示：

   ![chlimage_1-9](assets/chlimage_1-9.jpeg)
