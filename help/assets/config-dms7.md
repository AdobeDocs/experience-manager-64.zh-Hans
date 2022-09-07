---
title: 配置 Dynamic Media — Scene7 模式
description: 了解如何配置Dynamic Media - Scene7模式。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: b0f0c6e4-77c8-40db-a9f4-699d1a633571
feature: Configuration,Scene7 Mode
role: Admin,User,Developer
source-git-commit: a045c70f8cbfa03295c4fcbfbb2df1831c3f7292
workflow-type: tm+mt
source-wordcount: '5619'
ht-degree: 4%

---

# 配置 Dynamic Media — Scene7 模式 {#configuring-dynamic-media-scene-mode}

如果您使用为不同环境（如开发、暂存和实时生产）设置的Adobe Experience Manager，则必须为每个环境配置Dynamic MediaCloud Services。

## Dynamic Media - Scene7模式的架构图 {#architecture-diagram-of-dynamic-media-scene-mode}

以下架构图介绍了Dynamic Media - Scene7模式的工作方式。

使用新架构时，Experience Manager将负责主资产并与Dynamic Media进行同步，以便进行资产处理和发布：

1. 将主资产上传到Experience Manager后，该资产会复制到Dynamic Media。 此时，Dynamic Media将处理所有资产处理和演绎版生成，如图像的视频编码和动态变体。
1. 生成演绎版后，Experience Manager可以安全地访问和预览远程Dynamic Media演绎版(不会将二进制文件发送回Experience Manager实例)。
1. 在内容准备好发布和批准后，它将触发Dynamic Media服务，以将内容推送到CDN的分发服务器并缓存内容。

![chlimage_1](assets/chlimage_1.png)

## 在Scene7模式下启用Dynamic Media {#enabling-dynamic-media-in-scene-mode}

[默认情况下，Dynamic Media 处于禁用状态。](https://www.adobe.com/marketing-cloud/enterprise-content-management/dynamic-media.html)要利用Dynamic Media功能，您必须启用它。

>[!WARNING]
>
>Dynamic Media - Scene7模式适用于 *仅Experience Manager创作实例*. 因此，请配置 `runmode=dynamicmedia_scene7`在Experience Manager创作实例上， *not* Experience Manager发布实例。

要启用Dynamic Media，您必须使用 `dynamicmedia_scene7` 通过在终端窗口中输入以下命令行来运行模式（使用的示例端口为4502）：

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## （可选）将Dynamic Media预设和配置从6.3迁移到6.4零停机时间 {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

如果您将Experience ManagerDynamic Media从6.3升级到6.4（包括零停机时间部署的功能），请运行以下curl命令以从 `/etc` to `/conf` CRXDE Lite。

>[!NOTE]
>
>如果您在兼容性模式下运行Experience Manager实例（即，已安装兼容包），则无需运行这些命令。

要从 `/etc` to `/conf`，运行以下Linux® curl命令：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

无论是否具有兼容包，您都可以对所有升级，通过运行以下命令来复制现成查看器预设：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## （可选）安装用于批量资产迁移的功能包18912 {#installing-feature-pack}

功能包18912允许您通过FTP批量摄取资产，或在Experience Manager中将资产从Dynamic Media — 混合模式或Dynamic Media Classic迁移到Dynamic Media - Scene7模式。 可从Adobe Professional Services购买。

请参阅 [安装用于批量资产迁移的功能包18912](bulk-ingest-migrate.md) 以了解更多信息。

## 配置Dynamic MediaCloud Services {#configuring-dynamic-media-cloud-services}

在配置Dynamic MediaCloud Services之前，请更改密码。 在收到包含Dynamic Media凭据的配置电子邮件后，您必须 [登录](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) 到Dynamic Media Classic桌面应用程序以更改密码。 预配电子邮件中提供的密码是系统生成的，并且仅准备为临时密码。 请务必更新密码，以便使用正确的凭据设置Dynamic MediaCloud Service。

>[!NOTE]
>
>默认情况下，Cloud Services的配置路径为 `/content/dam`. Dynamic Media - Scene7模式不支持任何其他配置路径。

**要配置Dynamic MediaCloud Services:**

1. 在Experience Manager创作实例中，点按Experience Manager徽标以访问全局导航控制台，然后点按工具图标，然后点按 **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media配置]**.
1. 在Dynamic Media配置浏览器页面的左窗格中，点按 **[!UICONTROL 全球]** 点按 **[!UICONTROL 创建]**. 请勿点按或选择左侧的文件夹图标 [!UICONTROL 全球].
1. 在 [!UICONTROL 创建Dynamic Media配置] 页面，输入标题、Dynamic Media帐户电子邮件地址和密码。 选择您所在的地区。 此信息通过您的配置电子邮件中的Adobe提供给您。 如果您未收到电子邮件，请联系Adobe客户支持。

   点按 **[!UICONTROL 连接到Dynamic Media]**.

   >[!NOTE]
   >
   >在收到包含Dynamic Media凭据的配置电子邮件后，打开 [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然后登录到您的公司帐户以更改密码。 预配电子邮件中提供的密码是系统生成的，并且仅准备为临时密码。 请务必更新密码，以便使用正确的凭据设置Dynamic MediaCloud Service。

1. 如果连接成功，您还可以设置以下内容：

   * **[!UICONTROL 公司]** -Dynamic Media帐户的名称。

      >[!IMPORTANT]
      >
      >在Experience Manager实例上，仅支持Cloud Services中的一个Dynamic Media配置；请勿添加多个配置。 Experience Manager实例上的多个Dynamic Media配置是 *not* 受Adobe支持或推荐。<!-- CQDOC-19579 and CQDOC-19612 -->
   * **[!UICONTROL 公司根文件夹路径]**  — 您公司的根文件夹路径。
   * **[!UICONTROL 发布资产]**  — 选项 **[!UICONTROL 立即]** 是指上传资产后，系统会摄取资产并立即提供URL/嵌入。 发布资产无需用户干预。 选项 **[!UICONTROL 激活时]** 表示在提供URL/嵌入链接之前，必须先明确发布资产。
   * **[!UICONTROL 安全预览服务器]**  — 用于指定安全演绎版预览服务器的URL路径。 也就是说，在生成演绎版后，Experience Manager可以安全地访问和预览远程Dynamic Media演绎版(不会将二进制文件发送回Experience Manager实例)。

      除非您有使用自己公司服务器或特殊服务器的特殊安排，否则Adobe建议您使用默认设置。
   >[!NOTE]
   >
   >DMS7中不支持版本控制。 此外，仅当“编辑 Dynamic Media 配置”页面中的&#x200B;**[!UICONTROL 发布资产]**设置为&#x200B;**[!UICONTROL 激活时]**&#x200B;时，并且直到首次激活资产时延迟激活才适用。
   >
   >激活资产后，任何更新都会立即实时发布到S7交付。

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. 点按&#x200B;**[!UICONTROL 保存]**。
1. 要在发布Dynamic Media内容之前安全预览内容，您必须“”允许列表Experience Manager创作实例才能连接到Dynamic Media:

   * 打开 [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然后登录到您的帐户。 您的凭据和登录详细信息由Adobe在配置时提供。 如果您没有此信息，请联系技术支持。
   * 在页面右上方的导航栏上，点按 **[!UICONTROL 设置]** > **[!UICONTROL 应用程序设置]** > **[!UICONTROL 发布设置]** > **[!UICONTROL 图像服务器]**.
   * 在图像服务器发布页面的发布上下文下拉列表中，选择 **[!UICONTROL 测试图像提供]**.
   * 对于客户端地址过滤器，点按 **[!UICONTROL 添加]**.
   * 要启用（打开）地址，请选中复选框。 输入Experience Manager创作实例的IP地址（而非Dispatcher IP）。
   * 点按&#x200B;**[!UICONTROL 保存]**。

您现在已完成基本配置；您已准备好使用Dynamic Media - Scene7模式。

如果要进一步自定义配置，可以选择完成 [（可选）在Dynamic Media - Scene7模式下配置高级设置](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

## （可选）在Dynamic Media - Scene7模式下配置高级设置 {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

如果要进一步自定义Dynamic Media - Scene7模式的配置和设置，或优化其性能，则可以完成以下一个或多个可选任务：

* [（可选）Dynamic Media - Scene7模式设置的设置和配置](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [（可选）调整Dynamic Media - Scene7模式的性能](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [（可选）筛选用于复制的资产](#optional-filtering-assets-for-replication)

### （可选）Dynamic Media - Scene7模式设置的设置和配置</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

在 **dynamicmedia_scene7** 运行模式时，您可以使用Dynamic Media Classic用户界面更改Dynamic Media设置。

上述一些任务要求您打开 [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然后登录到您的帐户。

安装和配置任务包括：

* [发布图像服务器的设置](#publishing-setup-for-image-server)
* [配置应用程序常规设置](#configuring-application-general-settings)
* [配置色彩管理](#configuring-color-management)
* [编辑支持的格式的MIME类型](#editing-mime-types-for-supported-formats)
* [为不支持的格式添加MIME类型](#adding-mime-types-for-unsupported-formats)
* [创建批集预设以自动生成图像集和旋转集](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### 发布图像服务器的设置 {#publishing-setup-for-image-server}

“发布设置”设置可确定默认情况下如何从Dynamic Media交付资产。 如果未指定任何设置，Dynamic Media会根据发布设置中定义的默认设置来传送资产。 例如，如果请求传送的图像不包含分辨率属性，则会生成一个具有默认对象分辨率设置的图像。

要配置发布设置，请执行以下操作：在Dynamic Media Classic中，点按 **[!UICONTROL 设置]** > **[!UICONTROL 应用程序设置]** > **[!UICONTROL 发布设置]** > **[!UICONTROL 图像服务器]**.

“图像服务器”屏幕为传送图像建立了默认设置。 有关每个设置的说明，请参阅用户界面。

* **[!UICONTROL 请求属性]**  — 这些设置对可从服务器传送的图像施加了限制。
* **[!UICONTROL 默认请求属性]**  — 这些设置与图像的默认外观有关。
* **[!UICONTROL 常见缩略图属性]**  — 这些设置与缩略图图像的默认外观有关。
* **[!UICONTROL 目录字段的默认值]**  — 这些设置与图像的分辨率和默认缩略图类型有关。
* **[!UICONTROL 色彩管理属性]**  — 这些设置确定使用的ICC颜色配置文件。
* **[!UICONTROL 兼容性属性]**  — 为了向后兼容，此设置允许文本层中的前导和尾随段落与版本3.6中的段落一样进行处理。
* **[!UICONTROL 本地化支持]**  — 这些设置允许您管理多个区域设置属性。 它还允许您指定区域设置映射字符串，以便定义要在查看器中支持各种工具提示的语言。 有关设置本地化支持的详细信息，请参阅 [实施本地化支持时的重要注意事项](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#image-server).

#### 配置应用程序常规设置 {#configuring-application-general-settings}

要打开 [!UICONTROL 应用程序常规设置] 页面中，在Dynamic Media Classic全局导航栏中，点按 **[!UICONTROL 设置]** > **[!UICONTROL 应用程序设置]** > **[!UICONTROL 常规设置]**.

**[!UICONTROL 服务器]**  — 在进行帐户配置时，Dynamic Media会自动为您的公司提供分配的服务器。 这些服务器用于为您的网站和应用程序构建URL字符串。 这些URL调用特定于您的帐户。 请勿更改任何服务器名称，除非Experience Manager支持明确指示执行此操作。

**[!UICONTROL 覆盖图像]** - Dynamic Media不允许两个文件具有相同的名称。 每个项目的URL ID（文件名减去扩展名）必须唯一。 以下选项指定了如何上传替换资产：是替换原始内容还是变为重复内容。 重复资产将使用“–1”重命名（例如，chair.tif将chair-1.tif重命名）。 这些选项会影响上传到与原始文件夹不同的文件夹的资产，或文件扩展名与原始文件夹不同的资产(例如JPG、TIF或PNG)。

* **[!UICONTROL 在当前文件夹中覆盖，基本图像名称/扩展名相同]**  — 此选项是最严格的替换规则。 它要求您将替换图像上传到与原始图像相同的文件夹，并且替换图像的文件扩展名与原始图像相同。 如果未满足这些要求，则会创建重复项。

>[!NOTE]
>
>要保持与Experience Manager的一致性，请选择 **[!UICONTROL 在当前文件夹中覆盖，基本图像名称/扩展名相同]**.

* **[!UICONTROL 在任何文件夹中覆盖相同的基本资产名称/扩展名]**  — 要求替换图像的文件扩展名与原始图像相同(例如， `chair.jpg` 替换 `chair.jpg` 否 `chair.tif`)。 但是，您可以将替换图像上传到与原始图像不同的文件夹。 更新后的图像位于新文件夹中；在文件的原始位置中无法再找到该文件。
* **[!UICONTROL 在任意文件夹中覆盖相同的基本资产名称，而不考虑扩展名]**  — 此选项是包含性最强的替换规则。 您可以将替换图像上传到与原始图像不同的文件夹，上传文件扩展名不同的文件，然后替换原始文件。 如果原始文件位于其他文件夹中，则替换图像将位于上传到的新文件夹中。

**[!UICONTROL 默认颜色配置文件]**  — 请参阅 [配置色彩管理](#configuring-color-management) 以了解其他信息。

>[!NOTE]
>
>默认情况下，当您选择&#x200B;**[!UICONTROL 呈现]**&#x200B;时，系统会显示 15 种呈现形式，当您在资产的详细信息视图中选择&#x200B;**[!UICONTROL 查看器]**&#x200B;时，系统会显示 15 个查看器预设。您可以提高此限制。请参阅 [增加显示的图像预设数](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) 或 [增加显示的查看器预设数](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### 配置色彩管理 {#configuring-color-management}

Dynamic Media色彩管理允许您对资产进行颜色校正。 通过颜色校正，摄取的资产会保留其色彩空间(RGB、CMYK、灰色)和嵌入的色彩配置文件。 请求动态呈现时，图像颜色会使用CMYK、RGB或灰色输出校正为目标颜色空间。 请参阅 [配置图像预设](managing-image-presets.md).

**要配置默认颜色属性，以在请求图像时启用颜色校正，请执行以下操作：**

1. 打开 [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然后使用配置期间提供的凭据登录到您的帐户。 导航到 **[!UICONTROL 设置]** > **[!UICONTROL 应用程序设置]**.
1. 展开&#x200B;**[!UICONTROL 发布设置]**&#x200B;区域，然后选择&#x200B;**[!UICONTROL 图像服务器]**。设置发布实例的默认设置时，将&#x200B;**[!UICONTROL 发布上下文]**&#x200B;设置为&#x200B;**[!UICONTROL 图像提供]**。
1. 滚动到必须更改的属性。 例如， **[!UICONTROL 色彩管理属性]** 的上界。

   您可以设置以下颜色校正属性：

   * [!UICONTROL CMYK默认色彩空间]  — 默认CMYK颜色配置文件的名称
   * [!UICONTROL 灰阶默认色彩空间]  — 默认灰色配置文件的名称
   * [!UICONTROL RGB默认色彩空间]  — 默认RGB颜色配置文件的名称
   * [!UICONTROL 颜色转换渲染意图]  — 指定渲染意图。 可接受的值为 `perceptual`, `relative` `colometric`, `saturation`和 `absolute colometric`. Adobe建议 `relative` 作为默认设置。

1. 点按&#x200B;**[!UICONTROL 保存]**。

例如，可以将 **[!UICONTROL RGB 默认色彩空间]**&#x200B;设置为 `sRGB`，将 **[!UICONTROL CMYK 默认色彩空间]**&#x200B;设置为 `WebCoated`。

这样做可以执行以下操作：

* 为RGB和CMYK图像启用颜色校正。
* 没有颜色配置文件的RGB图像假定位于 `sRGB` 色彩空间。
* 假定没有颜色配置文件的CMYK图像位于 `WebCoated` 色彩空间。
* 返回RGB输出的动态演绎版，在 `sRGB` 色彩空间。
* 返回CMYK输出的动态呈现，在 `WebCoated` 色彩空间。

#### 编辑支持的格式的MIME类型 {#editing-mime-types-for-supported-formats}

您可以定义Dynamic Media处理的资产类型，并自定义高级资产处理参数。 例如，您可以指定资产处理参数以执行以下操作：

* 将Adobe PDF转换为eCatalog资产。
* 将Adobe Photoshop文档(.PSD)转换为横幅模板资产以进行个性化。
* 将Adobe Illustrator文件(.AI)或Adobe Photoshop封装的PostScript®文件(.EPS)栅格化。
* [视频配置文件](/help/assets/video-profiles.md) 和 [图像配置文件](/help/assets/image-profiles.md) 可以分别用于定义视频和图像的处理。

请参阅[上传资产](managing-assets-touch-ui.md#uploading-assets)。

**要编辑支持格式的mime类型，请执行以下操作：**

1. 在Experience Manager中，点按Experience Manager徽标以访问全局导航控制台，然后点按 **[!UICONTROL 工具]** （锤子）图标，然后导航到 **[!UICONTROL 常规]** > **[!UICONTROL CRXDE Lite]**.
1. 在左边栏中，导航到以下内容：

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. 在 `mimeTypes` 文件夹中，选择mime类型。
1. 在CRXDE Lite页面的右侧，在下部：

   * 双击 **[!UICONTROL 已启用]** 字段。 默认情况下，所有资产mime类型均启用(设置为 **[!UICONTROL true]**)，这表示资产将同步到Dynamic Media进行处理。 如果要排除此资产mime类型，请将此设置更改为 **[!UICONTROL false]**.
   * 双击 **[!UICONTROL jobParam]** 打开其关联的文本字段。 请参阅 [支持的Mime类型](assets-formats.md#supported-mime-types) 以获取可用于给定mime类型的允许处理参数值列表。

1. 执行下列操作之一：

   * 重复步骤3-4以编辑更多mime类型。
   * 在CRXDE Lite页面的菜单栏上，点按 **[!UICONTROL 全部保存]**.

1. 在页面的左上角，点按 **[!UICONTROL CRXDE Lite]** 返回Experience Manager。

#### 为不支持的格式添加自定义MIME类型 {#adding-custom-mime-types-for-unsupported-formats}

您可以为Experience Manager Assets中不支持的格式添加自定义MIME类型。 要确保您在CRXDE Lite中添加的任何新节点未被Experience Manager删除，请将MIME类型移到 **[!UICONTROL image_]** 且其启用值设置为 **[!UICONTROL false]**.

**要为不支持的格式添加自定义MIME类型，请执行以下操作：**

1. 在Experience Manager中，单击 **[!UICONTROL 工具]** > **[!UICONTROL 操作]** > **[!UICONTROL Web控制台]**.

   ![Web 控制台](assets/2019-08-02_16-13-14.png)

1. 将打开一个新的浏览器选项卡，该选项卡将显示 **[!UICONTROL Adobe Experience Manager Web控制台配置]** 页面。

   ![Experience ManagerWeb控制台配置](assets/2019-08-02_16-17-29.png)

1. 在页面上，向下滚动到该名称 **[!UICONTROL Adobe CQ Scene7资产MIME类型服务]**. 在名称的右侧，点按 **[!UICONTROL 编辑配置值]** （铅笔图标）。

   ![编辑配置值](assets/2019-08-02_16-44-56.png)

1. 在 **[!UICONTROL Adobe CQ Scene7资产MIME类型服务]** 页面，单击任意加号图标 `+`. 在表格中单击加号以添加新mime类型的位置很琐碎。

   ![加号图标](assets/2019-08-02_16-27-27.png)

1. 类型 `DWG=image/vnd.dwg` 的空文本字段中。

   示例 `DWG=image/vnd.dwg` 仅用于演示目的。 您在此处添加的MIME类型可以是任何其他不支持的格式。

   ![MIME类型添加示例](assets/2019-08-02_16-36-36.png)

1. 在页面的右下角，单击 **[!UICONTROL 保存]**.

   此时，您可以关闭已打开Adobe Experience Manager Web Console配置页面的浏览器选项卡。

1. 返回到具有打开的Experience Manager控制台的浏览器选项卡。

1. 在Experience Manager中，单击 **[!UICONTROL 工具]** > **[!UICONTROL 常规]** > **[!UICONTROL CRXDE Lite]**.

   ![CRXDE Lite页面](assets/2019-08-02_16-55-41.png)

1. 在左边栏中，导航到以下内容：

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. 拖动mime类型 `image_vnd.dwg` 直接放在上面 `image_` 在树上。

   ![拖动mime类型](assets/CRXDELite_CQDOC-14627.png)

1. 具有mime类型 `image_vnd.dwg` 仍在树中选择，从 **[!UICONTROL 属性]** 选项卡 **[!UICONTROL 已启用]** 行，在 **[!UICONTROL 值]** 列标题中，双击值以打开 **[!UICONTROL 值]** 下拉列表。

1. 类型 `false` (或选择 `false` )。

   ![False值](assets/2019-08-02_16_60_30.png)

1. 在CRXDE Lite页面的左上角附近，单击 **[!UICONTROL 全部保存]**.

#### 创建批集预设以自动生成图像集和旋转集 {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

在将资产上传到Dynamic Media时，使用批集预设自动创建图像集或旋转集。

首先，定义资产在一组中分组的命名约定。 然后，您可以创建一个批集预设，该预设是一组唯一命名的自包含说明，这些说明定义了如何使用与预设方法中定义的命名约定相匹配的图像来构建该集。

上传文件时，Dynamic Media会自动创建一个文件集，其中包含与活动预设中定义的命名约定相匹配的所有文件。

**配置默认命名**

创建默认命名约定，以在任何批集预设方法中使用该命名约定。 在批量集预设定义中选择的默认命名约定可能是贵公司生成批量集所需的全部内容。 将创建批集预设，以使用您定义的默认命名约定。 如果公司定义的默认命名存在例外，您可以为特定内容集创建任意数量的批量集预设，并使用所需的替代自定义命名约定。

虽然使用批量集预设功能不需要设置默认的命名约定，但您可以使用它来定义要分组到一组中的命名约定的任意多个元素。 这样做有助于简化批集创建过程。

作为替代方法，您可以使用 **[!UICONTROL 查看代码]** 没有可用的表单字段。 在此视图中，您可以完全使用正则表达式创建命名约定定义。

有两个元素可供定义， **[!UICONTROL 匹配]** 和 **[!UICONTROL 基本名称]**. 利用这些字段，可定义命名约定的所有元素，并标识用于命名包含这些元素的集合的约定部分。 公司的单个命名约定可以对其中每个元素使用一行或多行定义。 使用任意数量的行进行唯一定义，并将它们分组为不同的元素。 例如，“主图像”、“颜色”元素、“替代视图”元素和“色板”元素。

**要配置默认命名，请执行以下操作：**

1. 打开 [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然后登录到您的帐户。

   您的凭据和登录详细信息由Adobe在配置时提供。 如果您没有此信息，请联系技术支持。

1. 在页面顶部附近的导航栏中，点按 **[!UICONTROL 设置]** > **[!UICONTROL 应用程序设置]** > **[!UICONTROL 批集预设]** > **[!UICONTROL 默认命名]**.
1. 选择&#x200B;**[!UICONTROL 查看表单]**&#x200B;或&#x200B;**[!UICONTROL 查看代码]**，以指定要查看的方式并输入有关每个元素的信息。

   您可以选择 **[!UICONTROL 查看代码]** 复选框，以查看生成的正则表达式值与表单选项的旁边。 如果表单视图因任何原因限制您，则您可以输入或更改这些值以帮助定义命名约定的元素。 如果无法在表单视图中分析您的值，则表单字段将变为不活动。

   >[!NOTE]
   >
   >取消激活的表单字段不会验证正则表达式是否正确。 您会看到在结果行之后为每个元素构建的正则表达式的结果。 完整的正则表达式显示在页面底部。

1. 根据需要展开每个元素，然后输入要使用的命名约定。
1. 根据需要，执行以下任一操作：

   * 点按 **[!UICONTROL 添加]** 为元素添加其他命名约定。
   * 点按 **[!UICONTROL 删除]** 删除元素的命名约定。

1. 执行下列操作之一：

   * 点按 **[!UICONTROL 另存为]** 并键入预设的名称。
   * 点按 **[!UICONTROL 保存]** 编辑现有预设时，才会显示该预设。

**创建批集预设**

Dynamic Media使用批量集预设将资产组织为一组图像（替代图像、颜色选项、360旋转），以便在查看器中显示。 批集预设会随Dynamic Media中的资产上传流程自动运行。

您可以创建、编辑和管理批集预设。 有两种形式的批集预设定义：一个用于您设置的默认命名约定，另一个用于您动态创建的自定义命名约定。

您可以使用表单字段方法定义批集预设，也可以使用代码方法来使用正则表达式。 与默认命名一样，您可以选择 [!UICONTROL 查看代码] 同时，您在 [!UICONTROL 表单视图] 和使用正则表达式来构建定义。 或者，您也可以取消选中任一视图以独占使用其中一个视图。

**要创建批集预设，请执行以下操作：**

1. 打开 [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然后登录到您的帐户。

   您的凭据和登录详细信息由Adobe在配置时提供。 如果您没有此信息，请联系技术支持。

1. 在页面顶部附近的导航栏中，点按 **[!UICONTROL 设置]** > **[!UICONTROL 应用程序设置]** > **[!UICONTROL 批集预设]** > **[!UICONTROL 批集预设]**.

   [!UICONTROL 查看表单]，如 [!UICONTROL 详细信息] 页面，则为默认视图。

1. 在预设列表面板中，点按 **[!UICONTROL 添加]** 激活 **[!UICONTROL 详细信息]** 面板。
1. 在 **[!UICONTROL 详细信息]** 面板，在 **[!UICONTROL 预设名称]** 字段中，键入预设的名称。
1. 在 **[!UICONTROL 批集类型]** 下拉菜单中，选择预设类型。
1. 执行下列操作之一：

   * 如果您使用的是之前在 **[!UICONTROL 应用程序设置]** > **[!UICONTROL 批集预设]** > **[!UICONTROL 默认命名]**，展开 **[!UICONTROL 资产命名约定]**，然后在 **[!UICONTROL 文件命名]** 下拉列表中，点按 **[!UICONTROL 默认]**.
   * 要在设置预设时定义新的命名约定， **[!UICONTROL 资产命名约定]**，然后在 **[!UICONTROL 文件命名]** 下拉列表中，点按 **[!UICONTROL 自定义]**.

1. 对于 [!UICONTROL 序列顺序]，定义在图像集分组到Dynamic Media后图像的显示顺序。

   默认情况下，您的资产按字母数字顺序排序。 但是，您可以使用逗号分隔的正则表达式列表来定义顺序。

1. 对于 **[!UICONTROL 设置命名]** 和 **[!UICONTROL 《创建公约》]**，指定在 **[!UICONTROL 资产命名约定]**. 此外，定义在Dynamic Media文件夹结构中创建集的位置。

   如果您定义大量集，请将它们与包含资产本身的文件夹分开。 例如，创建一个“图像集”文件夹，并将生成的集放置在此处。

1. 在 **[!UICONTROL 详细信息]** 面板，点按 **[!UICONTROL 保存]**.
1. 点按 **[!UICONTROL 活动]** 新预设名称旁边。

   激活预设可确保在您将资产上传到Dynamic Media时，会应用批量集预设来生成资产集。

**创建批量集预设以自动生成2D旋转集**

您可以使用批集类型 **[!UICONTROL 多轴旋转集]** 创建可自动生成2D旋转集的方法。 图像分组使用行和列正则表达式，以便图像资产在多维数组中的相应位置中正确对齐。 在多轴旋转集中，没有必须具有的最小或最大行数或列数。

例如，假定要创建一个名为 `spin-2dspin`. 您有一组包含三行的旋转集图像，每行12个图像。 这些图像的名称如下所示：

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

通过此信息， [!UICONTROL 批集类型] 方法可创建如下：

![chlimage_1-1](assets/chlimage_1-1.png)

旋转集的共享资产名称部分的分组将添加到 **[!UICONTROL 匹配]** 字段（高亮显示）。 资产名称中包含行和列的变量部分将分别添加到 **[!UICONTROL 行]** 和 **[!UICONTROL 列字段]** 。

上传和发布旋转集后，您会激活2D旋转集方法的名称，该方法位于 **[!UICONTROL 批集预设]** 在 **[!UICONTROL 上载作业选项]** 对话框。

**要创建批量集预设以自动生成2D旋转集，请执行以下操作：**

1. 打开 [Dynamic Media Classic桌面应用程序](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)，然后登录到您的帐户。

   您的凭据和登录详细信息由Adobe在配置时提供。 如果您没有此信息，请联系技术支持。

1. 在页面顶部附近的导航栏中，点按 **[!UICONTROL 设置]** > **[!UICONTROL 应用程序设置]** > **[!UICONTROL 批集预设]** > **[!UICONTROL 批集预设]**.

   [!UICONTROL 查看表单]，如 [!UICONTROL 详细信息] 页面，则为默认视图。

1. 在 **[!UICONTROL 预设列表]** 面板，点按 **[!UICONTROL 添加]** 激活 **[!UICONTROL 详细信息]** 面板。
1. 在 **[!UICONTROL 详细信息]** 面板，在 [!UICONTROL 预设名称] 字段中，键入预设的名称。
1. 在 **[!UICONTROL 批集类型]** 下拉菜单，选择 **[!UICONTROL 资产集]**.
1. 在 **[!UICONTROL 子类型]** 下拉列表中，选择 **[!UICONTROL 多轴旋转集]**.
1. 展开 **[!UICONTROL 资产命名约定]**，然后在 **[!UICONTROL 文件命名]** 下拉列表中，点按 **[!UICONTROL 自定义]**.
1. 使用&#x200B;**[!UICONTROL 匹配]**&#x200B;和（可选）**[!UICONTROL 基本名称]**&#x200B;属性定义组成分组的图像资产命名的正则表达式。

   例如，您的文字“匹配”正则表达式可能如下所示：

   `(w+)-w+-w+`

1. 展开 **[!UICONTROL 行列位置]**，然后为图像资产在2D旋转集数组中的位置定义名称格式。

   使用圆括号将行或列在文件名中的位置括起来。

   例如，对于行正则表达式，它可能如下所示：

   `\w+-R([0-9]+)-\w+`

   或

   `\w+-(\d+)-\w+`

   对于列正则表达式，可能如下所示：

   `\w+-\w+-C([0-9]+)`

   或

   `\w+-\w+-C(\d+)`

   请记住，这些表达式只是用于演示目的的示例。 您可以根据需要创建正则表达式。

   >[!NOTE]
   >
   >如果行和列正则表达式的组合无法确定资产在多维旋转集数组中的位置，则不会将该资产添加到旋转集，并且会记录错误。

1. 对于 **[!UICONTROL 设置命名]** 和 **[!UICONTROL 《创建公约》]**，指定在 **[!UICONTROL 资产命名约定]**.

   此外，定义在Dynamic Media Classic文件夹结构中创建旋转集的位置。

   如果您定义大量集，请将它们与包含资产本身的文件夹分开。 例如，创建一个旋转集文件夹，将生成的集放在此处。

1. 在 **[!UICONTROL 详细信息]** 面板，点按 **[!UICONTROL 保存]**.
1. 点按 **[!UICONTROL 活动]** 新预设名称旁边。

   激活预设可确保在您将资产上传到Dynamic Media时，会应用批量集预设来生成资产集。

### （可选）调整Dynamic Media - Scene7模式的性能 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

为保持Dynamic Media - Scene7模式顺利运行，Adobe建议使用以下同步性能/可伸缩性微调提示：

* 更新预定义的作业参数，以处理不同的文件格式。
* 更新预定义的Granite工作流（视频资产）队列工作线程。
* 更新预定义的Granite临时工作流（图像和非视频资产）队列工作线程。
* 更新与Dynamic Media Classic服务器的最大上传连接数。

#### 更新预定义的作业参数以处理不同的文件格式

您可以在上传文件时调整作业参数以加快处理速度。 例如，如果您上传PSD文件，但不希望将它们作为模板进行处理，则可以将层提取设置为false(off)。 在这种情况下，调整的作业参数如下所示： `process=None&createTemplate=false`.

如果确实要打开模板创建，请使用以下参数： `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`.

<!-- REMOVED BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe建议对PDF、PostScript®和PSD文件使用以下“已调整”的作业参数：

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| 文件类型 | 推荐的作业参数 |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

要更新其中的任何参数，请按照 [启用基于MIME类型的Assets/Dynamic Media Classic上传作业参数支持](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

#### 更新Granite Transient工作流队列 {#updating-the-granite-transient-workflow-queue}

Granite传输工作流队列用于 **[!UICONTROL DAM更新资产]** 工作流。 在Dynamic Media中，它用于图像摄取和处理。

**要更新Granite Transient工作流队列，请执行以下操作：**

1. 导航到 [https://&lt;server>/system/console/configMgr](http://localhost:4502/system/console/configMgr) 和搜索 **[!UICONTROL 队列：Granite Transient工作流队列]**.

   >[!NOTE]
   >
   >由于OSGi PID是动态生成的，因此需要进行文本搜索，而不是直接URL。

1. 在 **[!UICONTROL 最大并行作业数]** 字段，请将数字更改为所需的值。

   您可以 **[!UICONTROL 最大并行作业数]** 以充分支持将文件重量上传到Dynamic Media。 具体值取决于硬件容量。 在某些情况下（例如初始迁移或一次性批量上传），您可以使用较大的值。 但是，请注意，使用较大的值（如内核数的两倍）可能会对其他并发活动产生负面影响。 因此，请根据您的特定用例测试和调整值。

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. 点按&#x200B;**[!UICONTROL 保存]**。

#### 更新Granite工作流队列 {#updating-the-granite-workflow-queue}

Granite工作流队列用于非临时工作流。 在Dynamic Media中，它使用 **[!UICONTROL Dynamic Media编码视频]** 工作流。

**要更新Granite工作流队列，请执行以下操作：**

1. 导航到 `https://<server>/system/console/configMgr` 和搜索 **[!UICONTROL 队列：Granite工作流队列]**.

   >[!NOTE]
   >
   >由于OSGi PID是动态生成的，因此需要进行文本搜索，而不是直接URL。

1. 在 **[!UICONTROL 最大并行作业数]** 字段，请将数字更改为所需的值。

   默认情况下，最大并行作业数取决于可用CPU核心的数量。 例如，在4核服务器上，它分配两个工作线程。 （0.0到1.0之间的值基于比率，或者大于1的任何数字都分配工作线程的数量。）

   对于大多数用例，0.5的默认设置已足够。

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. 点按&#x200B;**[!UICONTROL 保存]**。

#### 更新Scene7上传连接 {#updating-the-scene-upload-connection}

Scene7上传连接设置可将Experience Manager Assets同步到Dynamic Media Classic服务器。

**要更新Scene7上传连接，请执行以下操作：**

1. 导航至 `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. 在 [!UICONTROL 连接数] 字段和/或 [!UICONTROL 活动作业超时] 字段，请根据需要更改数字。

   的 **[!UICONTROL 连接数]** 设置控制允许Experience Manager到Dynamic Media上传的HTTP连接的最大数量；通常，十个连接的预定义值就足够了。

   的 **[!UICONTROL 活动作业超时]** 设置可确定在交付服务器中发布已上传的Dynamic Media资产的等待时间。 默认情况下，此值为2100秒或35分钟。

   对于大多数用例，设置2100便已足够。

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. 点按&#x200B;**[!UICONTROL 保存]**。

### （可选）筛选用于复制的资产 {#optional-filtering-assets-for-replication}

在非Dynamic Media部署中，您会复制 *全部* 资产（包括图像和视频）从Experience Manager创作环境到Experience Manager发布节点。 此工作流是必需的，因为Experience Manager发布服务器也会交付资产。

但是，在Dynamic Media部署中，由于资产是通过Cloud Service交付的，因此无需将这些资产复制到Experience Manager发布节点。 这种“混合发布”工作流可避免复制资产所需的额外存储成本和较长的处理时间。 其他内容（如网站页面）将继续从Experience Manager发布节点提供。

这些过滤器为您提供了一种 *排除* 资产复制到Experience Manager发布节点。

#### 使用默认资产过滤器进行复制 {#using-default-asset-filters-for-replication}

如果您使用Dynamic Media进行成像或视频，或者同时使用视频，则可以按原样使用Adobe提供的默认过滤器。 默认情况下，以下过滤器处于活动状态：

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>过滤器</strong></td> 
   <td><strong>Mime 类型</strong></td> 
   <td><strong>演绎版</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media图像交付</td> 
   <td><p>过滤图像</p> <p>筛选集</p> <p> </p> </td> 
   <td><p>开始于 <strong>图像/</strong></p> <p>包含 <strong>application/</strong> 结尾为 <strong>set</strong>.</p> </td> 
   <td>现成的“滤镜图像”（适用于单个图像资产，包括交互式图像）和“滤镜集”（适用于旋转集、图像集、混合媒体集和轮播集）将： 
    <ul> 
     <li>从复制中排除原始图像和静态图像演绎版。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media视频交付</td> 
   <td>filter-video</td> 
   <td>开始于 <strong>video/</strong></td> 
   <td>现成的“filter-video”将： 
    <ul> 
     <li>从复制中排除原始视频和静态缩略图演绎版。<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>过滤器应用于MIME类型，并且不能特定于路径。

#### 为复制自定义资产过滤器 {#customizing-asset-filters-for-replication}

1. 在Experience Manager中，点按Experience Manager徽标以访问全局导航控制台，然后点按 **[!UICONTROL 工具]** 图标，然后导航到 **[!UICONTROL 常规]** > **[!UICONTROL CRXDE Lite]**.
1. 在左侧文件夹树中，导航到 `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` 以查看过滤器。

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. 要为过滤器定义Mime类型，可以按如下方式找到Mime类型：

   在左边栏中，展开 **[!UICONTROL 内容]** > **[!UICONTROL dam]** > **[!UICONTROL &lt;`locate_your_asset`>]** > **[!UICONTROL jcr:content]** > **[!UICONTROL 元数据]**，然后在右侧的表中找到 **[!UICONTROL dc:format]**.

   下图是资产dc:format路径的示例。

   ![chlimage_1-3](assets/chlimage_1-3.png)

   请注意， `dc:format` （对于资产） `Fiji Red.jpg` is `image/jpeg`.

   要使此过滤器应用于所有图像（无论其格式如何），请将值设置为 `image/*` where `*` 是应用于任何格式的所有图像的正则表达式。

   要使过滤器仅应用于JPEG类型的图像，请输入值 `image/jpeg`.

1. 定义要在复制中包含或排除的演绎版。

   可用于筛选复制字符的字符包括：

   <table> 
    <tbody> 
    <tr> 
    <td><strong>要使用的字符</strong></td> 
    <td><strong>如何筛选用于复制的资产</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>通配符<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>包括用于复制的资产。</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>从复制中排除资产。</td> 
    </tr> 
    </tbody> 
   </table>

   导航到 **content/dam/&lt;`locate your asset`>/jcr:content/renditions**.

   下图是资产演绎版的示例。

   ![chlimage_1-4](assets/chlimage_1-4.png)

   如果您只想复制原件，则可以输入 `+original`.
