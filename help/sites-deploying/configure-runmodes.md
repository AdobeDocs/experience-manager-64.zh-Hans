---
title: 运行模式
seo-title: 运行模式
description: 了解如何使用运行模式调整AEM实例以实现特定用途。
seo-description: 了解如何使用运行模式调整AEM实例以实现特定用途。
uuid: 8a0c6e5c-4fae-43e2-b745-eee58f346ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 12329e26-40bc-4c94-bc60-6d9cbd01345f
translation-type: tm+mt
source-git-commit: d97828afee7a65e7a4036912c1cc8726404088c9
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 1%

---


# 运行模式{#run-modes}

运行模式允许您针对特定目的调整AEM实例； 例如，创作或发布、测试、开发、内部网或其他。

您可以：

* [为每个运行模式定义配置参数的集合](#defining-configuration-properties-for-a-run-mode)。

   基本的配置参数集将应用于所有运行模式，然后您可以根据特定环境的目的调整其他设置。 这些属性将根据需要应用。

* [定义要为特定模式安装的其他捆绑包](#defining-additional-bundles-to-be-installed-for-a-run-mode)。

所有设置和定义都存储在一个存储库中，并通过设置“运行模式” **来激活**。

## 安装运行模式 {#installation-run-modes}

安装（或固定）运行模式在安装时使用，然后在实例的整个生命周期中进行修复，这些模式无法更改。

现成安装运行模式：

* `author`
* `publish`
* `samplecontent`
* `nosamplecontent`

这是两对相互排斥的运行模式； 例如，您可以：

* 同时 `author` 定义 `publish`或（或）不同时定义

* 组合 `author` 使用 `samplecontent` 或(但 `nosamplecontent` 不同时使用两者)

>[!CAUTION]
>
>当使用上述运行模式之一（作者、发布、示例content、nosamplecontent）时，安装时使用的值定义该安装整个生命周期 *的运行* 模式。
>
>对于这些运行模式， *安装后* ，将无法更改它们。

## 自定义运行模式 {#customized-run-modes}

您还可以创建自己的自定义运行模式。 这些功能可以合并，以涵盖以下情形：

* `author` + `development`

* `publish` + `test`

* `publish` + `test` + `golive`

* `publish` + `intranet`

* 。 . .

在每次启动时也可以选择自定义运行模式。

## 使用samplecontent和nosamplecontent {#using-samplecontent-and-nosamplecontent}

这些模式允许您控制示例内容的使用。 在构建快速启动之前定义示例内容，其中可以包括包、配置等：

* 运行 `samplecontent` 模式将安装此内容（默认模式）。

* 该 `nosamplecontent` 模式将不安装示例内容。

nosamplecontent运行模式专为生产安装而设计。

## 为运行模式定义配置属性 {#defining-configuration-properties-for-a-run-mode}

配置属性的值集合（用于特定运行模式）可保存在存储库中。

运行模式由文件夹名称的后缀表示。 这允许您将所有配置作为存储在一个存储库中。 例如：

* `config`

   适用于所有运行模式

* `config.author`

   用于创作运行模式

* `config.publish`

   用于发布运行模式

* `config.<run-mode>`

   用于适用的运行模式； 例如，config

有关在 [这些文件夹中定义单个配置节点以及为多种运行模式组合创建配置的更多信息](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) ，请参阅存储库中的OSGi配置。

>[!NOTE]
>
>对 [于安装运行模](#installation-run-modes) 式（例如作者），安装后无法更改运行模式。 但是，对单个配置属性所做的更改将在重新启动后生效。

## 定义要为运行模式安装的其他捆绑包 {#defining-additional-bundles-to-be-installed-for-a-run-mode}

还可以指定应为特定运行模式安装的其他捆绑包。 对于这些定义，安装文件夹用于保存包。 同样，运行模式由前缀表示：

* `install.author`
* `install.publish`

这些文件夹的类型 `nt:folder` 应包含相应的捆绑包。

## 以特定运行模式启动CQ {#starting-cq-with-a-specific-run-mode}

如果您为多个运行模式定义了配置，则需要定义启动时要使用的配置。 有几种方法可指定要使用的运行模式； 决议的顺序是：

1. [ `sling.properties` 文件](#using-the-sling-properties-file)
1. [ `-r` 选项](#using-the-r-option)
1. [系统属性(`-D`)](#using-a-system-property-in-the-start-script)

1. [文件名检测](#filename-detection-renaming-the-jar-file)

当您使用应用程序服务器时，还 [可以在web.xml中定义运行模式](#defining-the-run-mode-in-web-xml-with-application-server)。

### 使用sling.properties文件 {#using-the-sling-properties-file}

文 `sling.properties` 件可用于定义所需的运行模式：

1. 编辑配置文件：

   `<cq-installation-dir>/crx-quickstart/conf/sling.properties`

1. 添加以下属性； 以下示例适用于作者：

   `sling.run.modes=author`

### 使用-r选项 {#using-the-r-option}

启动快速启动时，可以使用选项 `-r` 激活自定义运行模式。 例如，使用以下命令启动AEM实例，运行模式设置为dev。 &quot;

```shell
java -jar cq-56-p4545.jar -r dev
```

### 在开始脚本中使用系统属性 {#using-a-system-property-in-the-start-script}

开始脚本中的系统属性可用于指定运行模式。

* 例如，使用以下方法将实例作为位于美国的生产发布实例启动：

   `-Dsling.run.modes=publish,prod,us`

### 文件名检测——重命名jar文件 {#filename-detection-renaming-the-jar-file}

可以在安装前重命名安装jar文件来激活以下两种安装运行模式：

* 发布
* 作者

jar文件必须使用命名约定：

`cq5-<run-mode>-p<port-number>`

例如，通过命 `publish` 名jar文件设置运行模式：

`cq5-publish-p4503`

### 在web.xml中定义运行模式（使用Application Server） {#defining-the-run-mode-in-web-xml-with-application-server}

使用应用程序服务器时，还可以配置以下属性：

`sling.run.modes`

在文件中：

`WEB-INF/web.xml`

它位于AEM文 `war` 件中，应在部署前更新。

有关 [更多详细信息，请参阅将AEM与Application](/help/sites-deploying/application-server-install.md) Server一起安装。
