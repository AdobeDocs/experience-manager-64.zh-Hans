---
title: 资源映射
seo-title: 资源映射
description: 了解如何通过使用资源映射为AEM定义重定向、虚URL和虚拟主机。
seo-description: 了解如何通过使用资源映射为AEM定义重定向、虚URL和虚拟主机。
uuid: 33de7e92-8144-431b-badd-e6a667cd78e1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ddfacc63-1840-407e-8802-3730009c84f0
translation-type: tm+mt
source-git-commit: c4ac10736c937198aa0c81ecf547dd489ef93366
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 1%

---


# 资源映射{#resource-mapping}

资源映射用于为AEM定义重定向、虚URL和虚拟主机。

例如，您可以使用这些映射：

* 在所有请求前加 `/content` 上前缀，使内部结构在访客到您网站时处于隐藏状态。
* 定义重定向，以便将所有请求重 `/content/en/gateway` 定向到您网站的页面 `https://gbiv.com/`。

一个可能的HTTP映 [射将所有请求作为/content到localhost:4503的前缀](#configuring-an-internal-redirect-to-content)。 这样的映射可用于在允许的情况下将内部结构从访客隐藏到网站：

`localhost:4503/content/geometrixx/en/products.html`

要通过以下方式访问：

`localhost:4503/geometrixx/en/products.html`

因为映射将自动向添加前 `/content` 缀 `/geometrixx/en/products.html`。

>[!CAUTION]
>
>虚URL不支持正则表达式模式。

>[!NOTE]
>
>有关详细信息，请参 [阅Sling文档和资源](https://sling.apache.org/site/resources.html)[的映射](https://sling.apache.org/site/mappings-for-resource-resolution.html) 和资源。

## 查看映射定义 {#viewing-mapping-definitions}

这些映射构成两个列表,JCR资源解析程序将对它们进行评估（从上到下）以找到匹配项。

这些列表可以在Felix控制台的JCR ResourceResolver **选项下查看** （连同配置信息）; 例如， `https://<host>:<port>/system/console/jcrresolver`:

* 配置

   显示当前配置(如Apache Sling资源解 [析程序定义](/help/sites-deploying/osgi-configuration-settings.md))。

* 配置测试

   这允许您输入URL或资源路径。 单击 **“解析** ” **或“映射** ”，以确认系统将如何转换条目。

* **解析程序映**&#x200B;射条目ResourceResolver.resolve方法用来将URL映射到资源的条目的列表。

* **映射映射**&#x200B;条目ResourceResolver.map方法用于将资源路径映射到URL的条目列表。

这两个列表显示各种条目，包括应用程序定义为默认值的条目。 这些URL通常旨在简化用户的URL。

列表将一个模 **式**(与请求匹配的常规表达式)与一个 **替换** (Replacement)配对，该替换定义要实施的重定向。

例如，:

**图案** `^[^/]+/[^/]+/welcome$`

将触发：

**替换** `/libs/cq/core/content/welcome.html`.

要重定向请求，请执行以下操作：

`http://localhost:4503/welcome`

到:

`http://localhost:4503/libs/cq/core/content/welcome.html`

在存储库中创建新的映射定义。

>[!NOTE]
>
>有许多资源有助于解释如何定义常规表达式; 例如 [https://www.regular-expressions.info/](https://www.regular-expressions.info/)。

## 在AEM中创建映射定义 {#creating-mapping-definitions-in-aem}

在AEM的标准安装中，您可以找到以下文件夹：

`/etc/map/http`

这是定义HTTP协议的映射时使用的结构。 可以为要映 `sling:Folder`射的任何其他协议 `/etc/map` 创建其他文件夹()。

### 配置内部重定向到/content {#configuring-an-internal-redirect-to-content}

创建将任何请求作为前缀的映射至http://localhost:4503/，具有 `/content`:

1. 使用CRXDE导航到 `/etc/map/http`。

1. 创建新节点：

   * **类型** `sling:Mapping`

      此节点类型用于此类映射，但其使用并非强制性。

   * **名称** `localhost_any`

1. 单击“ **全部保存**”。
1. **向此** 节点添加以下属性：

   * **名称** `sling:match`

      * **类型** `String`
      * **值** `localhost.4503/`
   * **名称** `sling:internalRedirect`

      * **类型** `String`
      * **值** `/content/`


1. 单击“ **全部保存**”。

此操作将处理以下请求：\
`localhost:4503/geometrixx/en/products.html`\
如：\
`localhost:4503/content/geometrixx/en/products.html`\
被要求。

>[!NOTE]
>
>请参 [阅Sling](https://sling.apache.org/site/mappings-for-resource-resolution.html) 文档中的资源，进一步了解可用的sling属性及其配置方式。

>[!NOTE]
>
>您可以使用 `/etc/map.publish` 保存发布环境的配置。 然后，必须复制这些资源，并为发 `/etc/map.publish`布环境的Apache Sling Resource Resolver的 **映射位置** () [配置新位置](/help/sites-deploying/osgi-configuration-settings.md#apacheslingresourceresolver) ()。

