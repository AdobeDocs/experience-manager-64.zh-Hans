---
title: 将AEM Assets与Adobe InDesign Server整合
description: 了解如何将AEM Assets与InDesign Server相结合。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 5%

---


# 将AEM Assets与Adobe InDesign Server整合 {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager(AEM)资产使用：

* 用于分配特定处理任务的负载的代理。 代理是AEM实例，它与代理工作器通信以实现特定任务，而其他AEM实例则提供结果。
* 用于定义和管理特定任务的代理工作器。

这些任务可以涵盖多种领域； 例如，使用Adobe InDesign Server处理文件。

要将文件完全上传到您用Adobe InDesign创建的AEM Assets，将使用代理。 它使用代理工作者与Adobe InDesign Server通信，在 [运行脚本](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) ，以提取元数据并为AEM Assets生成各种再现。 代理工作程序在云配置中启用InDesign Server与AEM实例之间的双向通信。

>[!NOTE]
>
>Adobe InDesign有两种产品：
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  这允许您为印刷和／或数字分发设计页面布局。
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  此引擎使您能够根据您使用文档创建的内容有计划地创建自动InDesign。 它作为一种服务运行，为其ExtendScript引擎提供 [接口](https://www.adobe.com/devnet/scripting.html) 。\
   >  脚本在ExtendScript编写，与javascript类似。 有关Indesign脚本的信息，请参 [阅https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>



## 提取的工作方式 {#how-the-extraction-works}

InDesign Server可以与AEM Assets集成，以便上传使用InDesign()创 `.indd`建的文件、生成再现 ** 、提取所有媒体（例如，视频）并存储为资产：

>[!NOTE]
>
>先前版本的AEM能够提取XMP和缩略图，现在可以提取所有媒体。

1. 将文件 `.indd` 上传到AEM Assets。
1. 框架通过SOAP（简单对象访问协议）将命令脚本发送到InDesign Server。

   此命令脚本将：

   * 检索文 `.indd` 件。
   * 执行InDesign Server命令：

      * 将解压结构、文本和任何媒体文件。
      * 将生成PDF和JPG再现。
      * 将生成HTML和IDML再现。
   * 将结果文件发回AEM Assets。

   >[!NOTE]
   >
   >IDML是一种基于XML的格式，可呈现 *InDesign文* 件中的所有内容。 它使用Zip压缩存储为压缩 [包](https://www.techterms.com/definition/zip) 。
   >
   >有关 [更多信息，请参阅Adobe InDesign交换格式](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) INX和IDML。

   >[!CAUTION]
   >
   >如果InDesign Server未安装或未配置，则仍可将文件上 `.indd` 传到AEM。 但是，生成的演绎版将 `png` 限 `jpeg`于，并且您将无法生成 `html`, `idml` 或者页面演绎版。

1. 生成提取和再现后：

   * 此结构将被复制到 `cq:Page` （演绎版类型）。
   * 提取的文本和文件存储在AEM Assets。
   * 所有演绎版都存储在AEM Assets，位于资产本身中。

## 将InDesign Server与AEM集成 {#integrating-the-indesign-server-with-aem}

要集成InDesign Server以与AEM Assets一起使用，并在配置代理后，您需要：

1. [安装InDesign Server](#installing-the-indesign-server)。
1. 如果需要， [请配置AEM Assets工作流](#configuring-the-aem-assets-workflow)。

   仅当默认值不适用于您的实例时，才需要这样做。

1. 为InDesign Server [配置代理工作器](#configuring-the-proxy-worker-for-indesign-server)。

### 安装InDesign Server {#installing-the-indesign-server}

安装和开始InDesign Server以与AEM一起使用：

1. 下载并安装Adobe InDesign Server。

   >[!NOTE]
   >
   >InDesign Server（CS6和更高）。

1. 如果需要，您可以自定义InDesign Server实例的配置。

1. 从命令行开始服务器：

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   这将使服务器开始SOAP插件监听端口8080。 所有日志消息和输出都直接写入命令窗口。

   >[!NOTE]
   >
   >如果要将输出消息保存到文件，则使用重定向； 例如，在Windows下：
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### 配置AEM Assets工作流 {#configuring-the-aem-assets-workflow}

AEM Assets has a pre-configured workflow **DAM Update Asset**, that has several process steps specifically for InDesign:

* [媒体提取](#media-extraction)
* [页面提取](#page-extraction)

此工作流设置了默认值，这些默认值可以适应您在各种创作实例上的设置(这是一个标准工作流，因此在编辑工作流下可 [以获取更多信息](/help/sites-developing/workflows-models.md#configuring-a-workflow-step))。 如果您使用默认值（包括SOAP端口），则不需要任何配置。

设置完成后，将InDesign文件上传到AEM Assets（通过任何常用方法）将触发处理资产和准备各种演绎版所需的工作流。 将文件上传到AEM Assets, `.indd` 以确认您看到IDS在 `<*your_asset*>.indd/Renditions`

#### 媒体提取 {#media-extraction}

此步骤控制文件中媒体的提取 `.indd` 情况。

要进行自定义，可以编辑&#x200B;**[!UICONTROL 媒体提取]**&#x200B;步骤的&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡。

![媒体提取参数和脚本路径](assets/media_extraction_arguments_scripts.png)

媒体提取参数和脚本路径

* **ExtendScript图书馆**: 这是一个简单的http get/post方法库，其他脚本需要它。

* **扩展脚本**: 您可以在此处指定不同的脚本组合。 如果希望在InDesign Server上执行您自己的脚本，请将脚本保存在 `/apps/settings/dam/indesign/scripts`。

   有关Indesign脚本的信息，请参 [阅https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>[!CAUTION]
>
>请勿更改 ExtendScript 库。库提供与Sling通信所需的HTTP功能。 此设置指定要发送到Adobe InDesign Server以供在那里使用的库。

由媒 `ThumbnailExport.jsx` 体提取工作流步骤运行的脚本生成。jpg格式的缩略图再现。 此演绎版由流程缩略图工作流步骤用于生成AEM所需的静态演绎版。

您可以配置流程缩略图工作流步骤以生成不同大小的静态演绎版。 确保不删除默认值，因为AEM AssetsUI要求使用默认值。 最后，删除图像预览再现工作流步骤将删除。jpg缩略图再现，因为不再需要它。

#### 页面提取 {#page-extraction}

这将从提取的元素创建AEM页面。 提取处理程序用于从再现（当前为HTML或IDML）中提取数据。 此数据随后用于使用PageBuilder创建页面。

要进行自定义，可以编辑&#x200B;**页面提取**&#x200B;步骤的&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡。

![chlimage_1-289](assets/chlimage_1-289.png)

* **页面提取处理程序**: 从下拉列表卡中，选择要使用的处理函数。 提取处理程序对由相关 `RenditionPicker` 选择的特定呈现进行操作（请参阅 `ExtractionHandler` API）。
默认情况下，IDML导出提取处理程序可用。 它对在MediaExtract步 `IDML` 骤中生成的再现进行操作。

* **页面名称**: 指定要分配给结果页面的名称。 如果留空，则名称为“page”（如果“page”已存在，则为衍生项）。

* **页面标题**: 指定要分配给结果页面的标题。

* **页面根路径**: 生成页面的根位置的路径。 如果留空，则会使用包含资产演绎版的节点。

* **页面模板**: 生成结果页面时使用的模板。

* **页面设计**: 生成结果页面时要使用的页面设计。

### 配置代理工作器以进行InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>该工作器驻留在代理实例上。

1. 在“工具”控制台中，展 **[!UICONTROL 开左窗格中]** 的“Cloud Services配置”。 然后展开 **[!UICONTROL 云代理配置]**。

1. 双击 **[!UICONTROL IDS worker]** 以打开进行配置。

1. 单击 **[!UICONTROL 编辑]** ，打开配置对话框并定义所需的设置：

   ![proxy_disworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS池**: 用于与InDesign Server通信的SOAP端点。 您可以添加、删除和订购项目。

1. 单击&#x200B;**[!UICONTROL 确定]**&#x200B;进行保存。

### 配置Day CQ链接外部器  {#configuring-day-cq-link-externalizer}

如果InDesign服务器和AEM在不同的主机上运行，或者上述两种应用程序都未在默认端口上运行，请配置 **Day CQ Link Externalizer** ，以设置InDesign服务器的主机名、端口和内容路径。

1. 访问URL上的Configuration Manager `https://[AEM_server]:[port]/system/console/configMgr`。
1. 找到配置 **[!UICONTROL Day CQ Link Externalizer]**，然后单击&#x200B;**[!UICONTROL 编辑]**&#x200B;图标以将其打开。
1. 指定Indesign服务器的主机名和上下文路径，然后单击“保 **[!UICONTROL 存”]**。

   ![chlimage_1-290](assets/chlimage_1-290.png)

### 为InDesign Server启用并行作业处理 {#enabling-parallel-job-processing-for-indesign-server-s}

您现在可以为IDS启用并行作业处理。

首先，您需要确定InDesign Server可以处理的最大并行 `x`作业数():

* 在单个多处理器计算机上，InDesign Server可处理的并行作业(x)的最大数目比运行IDS的处理器数少一个。
* 在多台计算机上运行ID时，您需要计算可用处理器总数（即在所有计算机上），然后减去计算机总数。

要配置并行IDS作业数：

1. 打开 **[!UICONTROL Felix]** Console的“配置”选项卡； 例如：

   `http://localhost:4502/system/console/configMgr`

1. 在以下位置选择IDS处理队列：

   `Apache Sling Job Queue Configuration`

1. 套:

   * **[!UICONTROL 类型]** - `Parallel`
   * **[!UICONTROL 最大并行作业]** - `<*x*>` （如上所计算）

1. 保存这些更改。
1. 要启用AdobeCS6和更新版本的多会话支持，请选中下 `enable.multisession.name` 的复选框 `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`。
1. 通过向 [IDS Worker配 `*x*>` 置添加SOAP端点，创建&lt; IDS Worker池](#configuring-the-proxy-worker-for-indesign-server)。

   如果有多台计算机运行InDesign Server，请为每台计算机添加SOAP端点（每台计算机的处理器数-1）。

   >[!NOTE]
   >
   >使用工作池时，您可以启用IDS工作者的阻止列表。
   >
   >为此，请启用配置下的“enable.retry.name”复选框，该 `com.day.cq.dam.ids.impl.IDSJobProcessor.name` 配置将启用IDS作业检索。
   >
   >此外，在配 `com.day.cq.dam.ids.impl.IDSPoolImpl.name` 置下，为参数设置一个正值，该 `max.errors.to.blacklist` 参数在禁止IDS进入作业处理程序列表之前确定作业检索的数量
   >
   >默认情况下，在IDS工作`retry.interval.to.whitelist.name`器经过可配置（分钟）时间重新验证后。 如果在线找到该工作者，则从阻止列表中删除该工作者。

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## 支持Adobe InDesign服务器10.0或更高版本 {#enabling-support-for-indesign-server-or-higher}

对于InDesign服务器10.0或更高版本，请执行以下步骤以启用多会话支持。

1. 从实例中打开Configuration [!DNL Assets] Manager `https://[aem_server]:[port]/system/console/configMgr`。
1. 编辑配置 `com.day.cq.dam.ids.impl.IDSJobProcessor.name`。
1. 选择 **[!UICONTROL ids.cc.en]** able选项，然后单 **[!UICONTROL 击保存]**。

>[!NOTE]
>
>要 [!DNL InDesign Server] 与集 [!DNL Assets]成，请使用多核处理器，因为单核系统不支持集成所必需的会话支持功能。

## 配置Experience Manager凭据 {#configure-aem-credentials}

您可以更改从AEM实例访问InDesign服务器的默认管理员凭据（用户名和密码），而不中断与Adobe InDesign服务器的集成。

1. 转到 `/etc/cloudservices/proxy.html`.
1. 在对话框中，指定新的用户名和密码。
1. 保存凭据。
