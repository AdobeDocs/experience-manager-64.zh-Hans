---
title: 页面导出程序
seo-title: The Page Exporter
description: 了解如何使用AEM Page Exporter。
seo-description: Learn how to use the AEM Page Exporter.
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
exl-id: a5cb3b7b-d40f-4d86-8473-fb584f1d486c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 1%

---

# 页面导出程序{#the-page-exporter}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

AEM允许您将页面导出为包含图像、.js和.css文件的完整网页。

配置导出后，您只需在浏览器中通过将 `html` with `export.zip` 在URL中，您会获得一个zip文件下载，其中包含以html格式呈现的页面和引用的资产。 页面中的所有路径（例如图像路径）都将被重写，以指向zip文件中包含的文件或服务器上的资源。

## 导出页面 {#exporting-a-page}

以下步骤描述如何导出页面，并假定您的站点存在导出配置模板。 配置模板可定义页面的导出方式，并特定于您的网站。 要创建配置模板，请参阅 [为站点创建页面导出程序配置](#creating-a-page-exporter-configuration-for-your-site) 中。

要导出页面，请执行以下操作：

1. 在浏览器中，打开页面。 例如：
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. 打开页面属性对话框，选择 **高级** 选项卡，并展开 **导出** 字段。

1. 单击放大镜图标，然后选择配置模板。 选择 **geometrixx** 模板，因为它是Geometrixx站点的默认模板。 单击&#x200B;**确定**。

1. 单击 **确定** 以关闭页面属性对话框。
1. 通过将 `html` with `export.zip` 中。

1. 下载 `<page-name>.export.zip` 文件到文件系统。

1. 在文件系统中，解压缩文件：

   * 页面html文件( `<page-name>.html`) `<unzip-dir>/<page-path>`
   * 其他资源（.js文件、.css文件、图像……）会根据导出模板中的设置进行定位。 在本例中，以下是一些资源 `<unzip-dir>/etc`，下面有些 `<unzip-dir>/<page-path>`.

1. 打开页面html文件( `<unzip-dir>/<page-path>.html`)以检查渲染。

## 为站点创建页面导出程序配置 {#creating-a-page-exporter-configuration-for-your-site}

页面导出器基于内容同步框架。 页面属性对话框中可用的配置是配置模板。 它们为页面定义了所有必需的依赖项。 触发页面导出时，将使用配置模板，并且页面路径和设计路径都会动态应用于配置。 然后，可使用标准的内容同步功能创建zip文件。

AEM嵌入了一些模板，包括：

* 默认值为 `/etc/contentsync/templates/default`. 此模板：

   * 在存储库中未找到配置模板时是回退模板。
   * 可用作新配置模板的基础。

* 专门用于 **Geometrixx** 站点，在 `/etc/contentsync/templates/geometrixx`. 此模板可用作创建新模板的示例。

要创建页面导出器配置模板，请执行以下操作：

1. 在 **CRXDE Lite**，请在下面创建节点 `/etc/contentsync/templates`:

   * 名称：例如 `mysite`. 选择页面导出器模板时，该名称会显示在页面属性对话框中。
   * 类型: `nt:unstructured`

1. 在模板节点下方，调用此处 `mysite`，请使用下面描述的配置节点创建节点结构。

### 页面导出程序配置节点 {#page-exporter-configuration-nodes}

配置模板包含在节点结构中。 每个节点都有 `type` 属性，该属性定义在zip文件创建过程中执行的特定操作。 有关type属性的更多详细信息，请参阅内容同步框架页面中的配置类型概述一节。

以下节点可用于构建导出配置模板：

**页面节点** 页面节点用于将页面html复制到zip文件。 具有以下特点：

* 是强制节点。
* 位于下方 `/etc/contentsync/templates/<sitename>`.
* 其名称为 `page`.
* 其节点类型为 `nt:unstructured`

的 `page` 节点具有以下属性：

* A `type` 为值设置的属性 `pages`.

* 它没有 `path` 属性，因为当前页面路径会动态复制到配置中。

* 其他属性在内容同步框架的配置类型概述部分中有介绍。

**重写节点** 重写节点定义链接在导出的页面中的重写方式。 重写的链接可以指向zip文件中包含的文件，也可以指向服务器上的资源。

有关 `rewrite` 节点。

**设计节点** 设计节点用于复制用于导出页面的设计。 具有以下特点：

* 是可选的。
* 位于下方 `/etc/contentsync/templates/<sitename>`.
* 其名称为 `design`.
* 其节点类型为 `nt:unstructured`.

的 `design` 节点具有以下属性：

* A `type` 属性设置为值 `copy`.

* 它没有 `path` 属性，因为当前页面路径会动态复制到配置中。

**通用节点** 通用节点用于将clientlibs .js或.css文件等资源复制到zip文件。 具有以下特点：

* 是可选的。
* 位于下方 `/etc/contentsync/templates/<sitename>`.
* 没有特定名称。
* 其节点类型为 `nt:unstructured`.
* 具有 `type` 属性和任何 `type` 相关属性，如内容同步框架的配置类型概述部分中定义。

例如，以下配置节点将geometrixx clientlibs .js文件复制到zip文件：

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

的 **Geometrixx** 页面导出配置模板可显示如何配置页面导出。 要以json格式查看浏览器中模板的节点结构，请请求以下URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**实施自定义配置**

如您在节点结构中注意到的， **Geometrixx** 页面导出配置模板具有 `logo` 节点 `type` 属性设置为 `image`. 这是一种特殊的配置类型，已创建此类型以将图像徽标复制到zip文件。 要满足某些特定要求，您可能需要实施自定义 `type` 属性：为此，请参阅“内容同步”页面中的实施自定义更新处理程序一节。

## 以编程方式导出页面 {#programmatically-exporting-a-page}

要以编程方式导出页面，您可以使用 [PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI服务。 此服务允许您：

* 导出页面并写入HTTP Servlet响应。
* 导出页面并在特定位置保存zip文件。

绑定到的Servlet `export` 选择器和 `zip` 扩展使用PageExporter服务。

## 疑难解答 {#troubleshooting}

如果您在下载zip文件时遇到问题，可以删除 `/var/contentsync` 节点，然后再次发送导出请求。
