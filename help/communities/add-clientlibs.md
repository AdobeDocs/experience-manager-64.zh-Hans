---
title: 添加Clientlibs
seo-title: Add Clientlibs
description: 添加ClientLibraryFolder
seo-description: Add a ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
exl-id: 9b8c3d1c-a9b1-4dde-9044-46c8f2b22c22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 2%

---

# 添加Clientlibs {#add-clientlibs}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 添加ClientLibraryFolder(clientlibs) {#add-a-clientlibraryfolder-clientlibs}

创建名为的ClientLibraryFolder `clientlibs`其中将包含用于呈现网站页面的JS和CSS。

的 `categories`给予此客户端库的属性值是用于从内容页面直接包含此clientlib或将其嵌入到其他clientlib的标识符。

1. 使用 **[!UICONTROL CRXDE Lite]**，展开 `/etc/designs`

1. 右键单击 `an-scf-sandbox` 选择 `Create Node`

   * 名称: `clientlibs`
   * 类型: `cq:ClientLibraryFolder`

1. 单击 **[!UICONTROL 确定]**

![chlimage_1-220](assets/chlimage_1-220.png)

在 **[!UICONTROL 属性]** 选项卡 `clientlibs` 节点，输入 **`categories`** 属性：

* 名称： **[!UICONTROL 类别]**
* 类型： **[!UICONTROL 字符串]**
* 值： **[!UICONTROL apps.an-scf-sandbox]**
* 单击 **[!UICONTROL 添加]**
* 单击 **[!UICONTROL 全部保存]**

注意：使用“apps”为类别值添加前缀。 是将“拥有的应用程序”标识为位于/apps文件夹中，而不是/libs中的约定。  重要信息：添加占位符 `js.txt` 和 `css.txt` 文件。 （没有cq:ClientLibraryFolder，它不是正式的。）


1. 右键单击 **`/etc/designs/an-scf-sandbox/clientlibs`**
1. 选择 **[!UICONTROL 创建文件……]**
1. 输入 **[!UICONTROL 名称]**: `css.txt`

1. 选择 **[!UICONTROL 创建文件……]**
1. 输入 **[!UICONTROL 名称]**: `js.txt`

1. 单击 **[!UICONTROL 全部保存]**

![chlimage_1-221](assets/chlimage_1-221.png)

css.txt和js.txt的第一行标识可从中找到以下文件列表的基本位置。

尝试将css.txt的内容设置为：

```
#base=.
 style.css
```

然后，在名为style.css的clientlibs下创建文件，并将内容设置为：

`body {`

`background-color: #b0c4de;`

`}`

## 嵌入SCF Clientlib {#embed-scf-clientlibs}

在 **[!UICONTROL 属性]** 选项卡 `clientlibs` 节点，输入多值字符串属性 **[!UICONTROL 嵌入]**. 这将嵌入必要的 [用于SCF组件的客户端库(clientlibs)](client-customize.md#clientlibs-for-scf). 在本教程中，我们将为社区组件添加许多必需的clientlib。

**注意** 这可能是生产站点使用的所需方法，也可能不是，因为考虑到了方便性与为每个页面下载的clientlib的大小/速度。

如果只在一个页面上使用一项功能，则可以直接在页面上包含该功能的完整clientlib，例如&lt;% ui:includeClientLib类别=cq.social.hbs.forum&quot; %>

在本例中，我们将全部包含在内，因此，我们希望使用更基本的SCF clientlib，即作者clientlib:

* 名称: **`embed`**
* 类型: **`String`**

* 单击 **`Multi`**
* 价值: **`cq.social.scf`**

   *&lt;enter> 将弹出对话框*

   *单击&#x200B;**[+]**在每个条目之后添加以下clientlib类别：*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * 单击 **[!UICONTROL 确定]**

* 单击 **[!UICONTROL 全部保存]**

![chlimage_1-222](assets/chlimage_1-222.png)

这就是方法 `/etc/designs/an-scf-sandbox/clientlibs` 现在应显示在存储库中：

![chlimage_1-223](assets/chlimage_1-223.png)

## 在PlayPage模板中包含Clientlib {#include-clientlibs-in-playpage-template}

不包含 `apps.an-scf-sandbox` ClientLibraryFolder类别中，SCF组件将无法正常工作，也不会按照必需的Javascript设置样式，并且样式将不可用。

例如，如果不包含clientlibs，则SCF注释组件将显示为未设置样式：

![chlimage_1-224](assets/chlimage_1-224.png)

在包含apps.an-scf-sandbox clientlibs后，SCF评论组件会显示样式：

![chlimage_1-225](assets/chlimage_1-225.png)

include语句属于 `<head>` 部分 `<html>` 脚本。 默认 **`foundation head.jsp`** 包含可以覆盖的脚本： **`headlibs.jsp`**.

**复制headlibs.jsp并包含clientlibs:**

1. 使用 **[!UICONTROL CRXDE Lite]**，选择 **`/libs/foundation/components/page/headlibs.jsp`**
1. 右键单击并选择 **[!UICONTROL 复制]** （或从工具栏中选择复制）
1. 选择 **`/apps/an-scf-sandbox/components/playpage`**
1. 右键单击并选择 **[!UICONTROL 粘贴]** （或从工具栏中选择粘贴）
1. 双击 **`headlibs.jsp`** 打开
1. 在文件末尾附加以下行

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. 单击 **[!UICONTROL 全部保存]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

在浏览器中加载您的网站，并查看背景是否不是蓝色阴影。

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## 省下你的工作 {#saving-your-work-so-far}

此时，存在一个极简主义的沙箱，可能值得另存为一个包，这样在播放时，如果您的存储库已损坏并且您希望重新开始，您就可以关闭服务器、重命名或删除文件夹crx-quickstart/、打开服务器、上载并安装此保存的包，并且不必重复这些最基本的步骤。

此包存在于 [创建示例页面](create-sample-page.md) 教那些迫不及待地跳进来开始玩的人……

要创建资源包，请执行以下操作：


* 从 **[!UICONTROL CRXDE Lite]**，请单击 [包图标](http://localhost:4502/crx/packmgr/)
* 单击 **[!UICONTROL 创建资源包]**

   * 包名称: `an-scf-sandbox-minimal-pkg`
   * 版本: `0.1`
   * 群组： &lt;leave as=&quot;&quot; default=&quot;&quot;>
   * 单击 **[!UICONTROL 确定]**

* 单击 **[!UICONTROL 编辑]**

   * 选择 **[!UICONTROL 过滤器]** 选项卡

      * 单击 **[!UICONTROL 添加过滤器]**
      * 根路径： &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/apps/an-scf-sandbox`
      * 单击 **[!UICONTROL 完成]**
      * 单击 **[!UICONTROL 添加过滤器]**
      * 根路径： &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/etc/designs/an-scf-sandbox`
      * 单击 **[!UICONTROL 完成]**
      * 单击 **[!UICONTROL 添加过滤器]**
      * 根路径： &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/content/an-scf-sandbox`
      * 单击 **[!UICONTROL 完成]**
   * 单击 **[!UICONTROL 保存]**


* 单击 **[!UICONTROL 生成]**

现在，您可以选择 **[!UICONTROL 下载]** 将其保存到磁盘， **[!UICONTROL 上传包]** ，以及选择 **[!UICONTROL 更多>复制]** 要将沙盒推送到localhost发布实例，以扩展沙盒的领域。
