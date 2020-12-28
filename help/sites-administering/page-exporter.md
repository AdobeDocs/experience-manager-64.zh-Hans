---
title: 页面导出器
seo-title: 页面导出器
description: 了解如何使用AEM Page Exporter。
seo-description: 了解如何使用AEM Page Exporter。
uuid: 2ca2b8f1-c723-4e6b-8c3d-f5886cd0d3f1
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 6ab07b5b-ee37-4029-95da-be2031779107
translation-type: tm+mt
source-git-commit: aac5026a249e1cb09fec66313cc03b58597663f0
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# 页面导出器{#the-page-exporter}

AEM允许您将页面导出为包含图像、.js和。css文件的完整网页。

配置导出后，您只需在浏览器中请求一个页面，即可在URL中将`html`替换为`export.zip`，然后获得一个zip文件下载，其中包含以html格式呈现的页面和引用的资产。 页面中的所有路径（如图像路径）都将重写，以指向zip文件中包含的文件或指向服务器上的资源。

## 导出页面{#exporting-a-page}

以下步骤介绍了如何导出页面，并假定站点存在导出配置模板。 配置模板可定义页面的导出方式，并特定于您的站点。 要创建配置模板，请参阅[为站点创建页面导出器配置](#creating-a-page-exporter-configuration-for-your-site)部分。

要导出页面，请执行以下操作：

1. 在您的浏览器中，打开页面。 例如：
1. `http://localhost:4502/content/geometrixx/en/products/triangle.html`
1. 打开页面属性对话框，选择&#x200B;**高级**&#x200B;选项卡并展开&#x200B;**导出**&#x200B;字段集。

1. 单击放大镜图标，然后选择配置模板。 选择&#x200B;**geometrixx**&#x200B;模板，因为它是Geometrixx站点的默认模板。 单击&#x200B;**确定**。

1. 单击&#x200B;**确定**&#x200B;以关闭页面属性对话框。
1. 通过将URL中的`html`替换为`export.zip`来请求页面。

1. 将`<page-name>.export.zip`文件下载到文件系统。

1. 在文件系统中，解压缩文件：

   * 页面html文件(`<page-name>.html`)位于`<unzip-dir>/<page-path>`下
   * 其他资源（.js文件、.css文件、图像……）根据导出模板中的设置进行定位。 在本示例中，某些资源位于`<unzip-dir>/etc`下，有些位于`<unzip-dir>/<page-path>`下。

1. 在浏览器中打开页面html文件(`<unzip-dir>/<page-path>.html`)以检查呈现。

## 为站点{#creating-a-page-exporter-configuration-for-your-site}创建页面导出器配置

页面导出器基于内容同步框架。 页面属性对话框中的可用配置是配置模板。 它们为页面定义了所有必需的依赖关系。 触发页面导出时，将使用配置模板，并将页面路径和设计路径动态应用到配置。 然后，使用标准内容同步功能创建zip文件。

AEM嵌入了几个模板，包括：

* `/etc/contentsync/templates/default`处的默认值。 此模板：

   * 是在存储库中未找到配置模板时的回退模板。
   * 可用作新配置模板的基础。

* 专用于&#x200B;**Geometrixx**&#x200B;站点的`/etc/contentsync/templates/geometrixx`。 此模板可用作创建新模板的示例。

要创建页面导出器配置模板，请执行以下操作：

1. 在&#x200B;**CRXDE Lite**&#x200B;中，在`/etc/contentsync/templates`下创建一个节点：

   * 名称：例如，`mysite`。 选择页面导出器模板时，该名称将显示在页面属性对话框中。
   * 类型: `nt:unstructured`

1. 在此处调用的模板节点`mysite`下，使用下面描述的配置节点创建一个节点结构。

### 页面导出器配置节点{#page-exporter-configuration-nodes}

配置模板包含在节点结构中。 每个节点都有一个`type`属性，该属性定义了zip文件创建过程中的特定操作。 有关type属性的更多详细信息，请参阅内容同步框架页中的配置类型概述部分。

以下节点可用于构建导出配置模板：

**页面** 节点页面节点用于将页面html复制到zip文件。具有以下特点：

* 是必需节点。
* 位于`/etc/contentsync/templates/<sitename>`下。
* 其名称为`page`。
* 其节点类型为`nt:unstructured`

`page`节点具有以下属性：

* 设置了值`pages`的`type`属性。

* 它没有`path`属性，因为当前页面路径是动态复制到配置的。

* 其他属性在内容同步框架的配置类型概述部分中进行了介绍。

**重写** 节点重写节点定义链接在导出页面中的重写方式。重写的链接可以指向包含在zip文件中的文件，也可以指向服务器上的资源。

有关`rewrite`节点的完整说明，请参阅“内容同步”页。

**设计** 节点设计节点用于复制用于导出页面的设计。具有以下特点：

* 是可选的。
* 位于`/etc/contentsync/templates/<sitename>`下。
* 其名称为`design`。
* 其节点类型为`nt:unstructured`。

`design`节点具有以下属性：

* 设置为值`copy`的`type`属性。

* 它没有`path`属性，因为当前页面路径是动态复制到配置的。

**通用** 节点通用节点用于将clientlibs .js或。css文件等资源复制到zip文件。具有以下特点：

* 是可选的。
* 位于`/etc/contentsync/templates/<sitename>`下。
* 没有特定名称。
* 其节点类型为`nt:unstructured`。
* 具有`type`属性和任何`type`相关属性，如Content Sync框架的“配置类型概述”部分中所定义。

例如，以下配置节点将geometrixx clientlibs .js文件复制到zip文件：

```xml
"geometrixx.clientlibs.js": {
    "extension": "js",
    "type": "clientlib",
    "path": "/etc/designs/geometrixx/clientlibs",
    "jcr:primaryType": "nt:unstructured"
}
```

**Geometrixx**&#x200B;页面导出配置模板显示如何配置页面导出。 要将浏览器中模板的节点结构视图为json格式，请请求以下URL:

`http://localhost:4502/etc/contentsync/templates/geometrixx.-1.json`

**实现自定义配置**

正如您在节点结构中注意到的，**Geometrixx**&#x200B;页面导出配置模板有一个`logo`节点，其属性设置为`image`。 `type`这是一种特殊的配置类型，已创建该配置类型以将图像标志复制到zip文件。 要满足某些特定要求，您可能需要实现自定义`type`属性：要执行此操作，请参阅“内容同步”页中的实施自定义更新处理程序部分。

## 以编程方式导出页面{#programmatically-exporting-a-page}

要以编程方式导出页面，可以使用[PageExporter](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/wcm/contentsync/PageExporter.html) OSGI服务。 此服务允许您：

* 导出页面并写入HTTP servlet响应。
* 导出页面并在特定位置保存zip文件。

绑定到`export`选择器和`zip`扩展的servlet使用PageExporter服务。

## 疑难解答 {#troubleshooting}

如果下载zip文件时遇到问题，可删除存储库中的`/var/contentsync`节点，然后再次发送导出请求。

