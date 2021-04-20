---
title: 将AEM Assets与Adobe InDesign Server集成
description: 了解如何将AEM Assets与InDesign Server集成。
contentOwner: AG
feature: Publishing
role: Administrator
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '1704'
ht-degree: 4%

---


# 将AEM Assets与Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}集成

Adobe Experience Manager(AEM)资产使用：

* 用于分配特定处理任务负载的代理。 代理是一个AEM实例，它与一个代理工作器通信以实现特定任务，而其他AEM实例则提供结果。
* 用于定义和管理特定任务的代理Worker。

这可以涵盖各种任务;例如，使用Adobe InDesign Server处理文件。

要将文件完全上传到您使用AEM Assets创建的Adobe InDesign，将使用代理。 它使用代理worker与Adobe InDesign Server通信，其中运行[脚本](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)以提取元数据并为AEM Assets生成各种再现。 代理worker在云配置中启用InDesign Server与AEM实例之间的双向通信。

>[!NOTE]
>
>Adobe InDesign有两个产品：
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  这允许您为打印和/或数字分发设计页面布局。
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  此引擎使您能够根据您使用InDesign创建的内容有计划地创建自动文档。 它作为服务运行，为其[ExtendScript](https://www.adobe.com/devnet/scripting.html)引擎提供接口。\
   >  脚本是在ExtendScript中编写的，与javascript类似。 有关Indesign脚本的信息，请参阅[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>



## 提取的工作原理{#how-the-extraction-works}

该InDesign Server可以与AEM Assets集成，以便能够上传使用InDesign(`.indd`)创建的文件，生成演绎版，提取&#x200B;*所有*&#x200B;媒体（例如，视频），并存储为资产：

>[!NOTE]
>
>以前版本的AEM能够提取XMP和缩略图，现在可以提取所有媒体。

1. 将`.indd`文件上传到AEM Assets。
1. 框架通过SOAP（简单对象访问协议）将命令脚本发送到InDesign Server。

   此命令脚本将：

   * 检索`.indd`文件。
   * 执行InDesign Server命令：

      * 将提取结构、文本和任何媒体文件。
      * 将生成PDF和JPG再现。
      * 将生成HTML和IDML再现。
   * 将生成的文件发布回AEM Assets。

   >[!NOTE]
   >
   >IDML是一种基于XML的格式，可在InDesign文件中呈现&#x200B;*所有内容*。 它使用[Zip](https://www.techterms.com/definition/zip)压缩作为压缩包存储。
   >
   >有关详细信息，请参阅[Adobe InDesign Interchange Formats INX和IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8)。

   >[!CAUTION]
   >
   >如果未安装或未配置InDesign Server，则仍可将`.indd`文件上载到AEM。 但是，生成的演绎版将限制为`png`和`jpeg`，您将无法生成`html`、`idml`或页面演绎版。

1. 生成提取和再现后：

   * 结构将复制到`cq:Page`（格式副本类型）。
   * 提取的文本和文件存储在AEM Assets中。
   * 所有演绎版都存储在AEM Assets中，位于资产本身中。

## 将InDesign Server与AEM {#integrating-the-indesign-server-with-aem}集成

要集成InDesign Server以与AEM Assets一起使用，并在配置代理后，您需要：

1. [安装InDesign Server](#installing-the-indesign-server)。
1. 如果需要，[配置AEM Assets Workflow](#configuring-the-aem-assets-workflow)。

   仅当默认值不适合您的实例时，才需要这样做。

1. 为InDesign Server](#configuring-the-proxy-worker-for-indesign-server)配置[代理worker。

### 安装InDesign Server{#installing-the-indesign-server}

安装和开始InDesign Server以与AEM一起使用：

1. 下载并安装Adobe InDesign Server。

   >[!NOTE]
   >
   >InDesign Server（CS6和更高版本）。

1. 如果需要，您可以自定义InDesign Server实例的配置。

1. 从命令行中开始服务器：

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   这将使服务器在端口8080上开始SOAP插件。 所有日志消息和输出都直接写入命令窗口。

   >[!NOTE]
   >
   >如果要将输出消息保存到文件，则使用重定向；例如，在Windows下：
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### 配置AEM Assets Workflow {#configuring-the-aem-assets-workflow}

AEM Assets具有预配置的工作流&#x200B;**DAM更新资产**，该工作流具有几个专门用于InDesign的流程步骤：

* [媒体提取](#media-extraction)
* [页面提取](#page-extraction)

此工作流设置了默认值，这些默认值可以适用于各种创作实例的设置（这是一个标准工作流，因此在[编辑工作流](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)下提供了更多信息）。 如果您使用默认值（包括SOAP端口），则不需要任何配置。

设置完成后，将InDesign文件上传到AEM Assets（通过任何常用方法）将触发处理资产和准备各种演绎版所需的工作流。 将`.indd`文件上传到AEM Assets，以测试您的配置，以确认您看到IDS在`<*your_asset*>.indd/Renditions`下创建的不同再现

#### 媒体提取 {#media-extraction}

此步骤控制`.indd`文件中媒体的提取。

要进行自定义，可以编辑&#x200B;**[!UICONTROL 媒体提取]**&#x200B;步骤的&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡。

![媒体提取参数和脚本路径](assets/media_extraction_arguments_scripts.png)

媒体提取参数和脚本路径

* **ExtendScript库**:这是一个简单的http get/post方法库，其他脚本需要它。

* **扩展脚本**:您可以在此处指定不同的脚本组合。如果希望在InDesign Server上执行您自己的脚本，请将脚本保存在`/apps/settings/dam/indesign/scripts`。

   有关InDesign脚本的信息，请参阅[https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)。

>[!CAUTION]
>
>请勿更改 ExtendScript 库。库提供与Sling通信所需的HTTP功能。 此设置指定要发送到Adobe InDesign Server以供在此使用的库。

由媒体提取工作流步骤运行的`ThumbnailExport.jsx`脚本生成JPG格式的缩略图再现。 此演绎版由流程缩略图工作流步骤用于生成AEM所需的静态演绎版。

您可以配置“流程缩略图”工作流步骤，以生成不同大小的静态演绎版。 请确保不要删除默认值，因为AEM Assets UI要求使用默认值。 最后，删除图像预览再现工作流步骤会删除.jpg缩略图再现，因为不再需要它。

#### 页面提取 {#page-extraction}

这将从提取的元素创建AEM页面。 提取处理函数用于从再现（当前为HTML或IDML）中提取数据。 然后，此数据用于使用PageBuilder创建页面。

要进行自定义，可以编辑&#x200B;**页面提取**&#x200B;步骤的&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡。

![chlimage_1-289](assets/chlimage_1-289.png)

* **页面提取处理程序**:从下拉列表中，选择要使用的处理函数。提取处理程序对由相关 `RenditionPicker` 选择的特定呈现进行操作（请参阅 `ExtractionHandler` API）。
默认情况下，IDML导出提取处理程序可用。 它对在MediaExtract步骤中生成的`IDML`再现进行操作。

* **页面名称**:指定要分配给生成页面的名称。如果留空，则名称为“page”（如果“page”已存在，则为派生名称）。

* **页面标题**:指定要分配给生成页面的标题。

* **页面根路径**:生成页面的根位置的路径。如果留空，则使用包含资产演绎版的节点。

* **页面模板**:生成生成页面时要使用的模板。

* **页面设计**:生成生成页面时要使用的页面设计。

### 为InDesign Server{#configuring-the-proxy-worker-for-indesign-server}配置Proxy Worker

>[!NOTE]
>
>该worker驻留在代理实例上。

1. 在“工具”控制台中，展开左窗格中的&#x200B;**[!UICONTROL Cloud Services配置]**。 然后展开&#x200B;**[!UICONTROL 云代理配置]**。

1. 双击 **[!UICONTROL IDS worker]** 以打开进行配置。

1. 单击&#x200B;**[!UICONTROL 编辑]**&#x200B;以打开配置对话框并定义所需的设置：

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS池**:用于与InDesign Server通信的SOAP端点。您可以添加、删除和订购项目。

1. 单击&#x200B;**[!UICONTROL 确定]**&#x200B;进行保存。

### 配置Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

如果InDesign Server和AEM位于不同的主机上，或者其中一个或两个应用程序在默认端口上不工作，请配置&#x200B;**Day CQ Link Externalizer**&#x200B;以设置InDesign Server的主机名、端口和内容路径。

1. 访问位于URL `https://[AEM_server]:[port]/system/console/configMgr`的Configuration Manager。
1. 找到配置&#x200B;**[!UICONTROL Day CQ Link Externalizer]**。 单击&#x200B;**[!UICONTROL 编辑]**&#x200B;以打开。
1. 链接Externalizer设置有助于为[!DNL Experience Manager]部署和[!DNL InDesign Server]创建绝对URL。 使用&#x200B;**[!UICONTROL 域]**&#x200B;字段指定[!DNL Adobe InDesign Server]的主机名和上下文路径。 按照屏幕上的说明操作。单击&#x200B;**[!UICONTROL 保存]**。

   ![链接外部器设置](assets/link-externalizer-config.png)

### 为InDesign Server{#enabling-parallel-job-processing-for-indesign-server}启用并行作业处理

您现在可以为IDS启用并行作业处理。

首先，您需要确定InDesign Server可以处理的最大并行作业数(`x`):

* 在单个多处理器计算机上，InDesign Server可处理的并行作业(x)的最大数目比运行IDS的处理器数少一个。
* 在多台计算机上运行IDS时，您需要计算可用处理器总数（即在所有计算机上），然后减去计算机总数。

要配置并行IDS作业数：

1. 打开Felix控制台的&#x200B;**[!UICONTROL 配置]**&#x200B;选项卡；例如：

   `http://localhost:4502/system/console/configMgr`

1. 在以下位置选择IDS处理队列：

   `Apache Sling Job Queue Configuration`

1. 套:

   * **[!UICONTROL 类型]** - `Parallel`
   * **[!UICONTROL 最大并行作业]** - `<*x*>` （如上所计算）

1. 保存这些更改。
1. 要启用对Adobe CS6和更新的多会话支持，请选中`com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`下的`enable.multisession.name`复选框。
1. 通过向IDS Worker配置](#configuring-the-proxy-worker-for-indesign-server)添加SOAP端点，创建`*x*>` IDS Worker的[池。

   如果有多台计算机运行InDesign Server，请为每台计算机添加SOAP端点（每台计算机的处理器数–1）。

   >[!NOTE]
   >
   >使用工作池时，您可以启用IDS工作者的阻止列表。
   >
   >要执行此操作，请在`com.day.cq.dam.ids.impl.IDSJobProcessor.name`配置下启用“enable.retry.name”复选框，该配置将启用IDS作业检索。
   >
   >此外，在`com.day.cq.dam.ids.impl.IDSPoolImpl.name`配置下，为`max.errors.to.blacklist`参数设置一个正值，该值确定在禁止作业处理程序中的IDS之前的作业检索数列表
   >
   >默认情况下，在以分钟为单位的可配置(`retry.interval.to.whitelist.name`)时间后，IDSworker将重新验证。 如果在线找到该工作者，则从阻止列表中删除该工作者。

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## 启用对Adobe InDesign server 10.0或更高版本{#enabling-support-for-indesign-server-or-higher}的支持

对于InDesign Server 10.0或更高版本，请执行以下步骤以启用多会话支持。

1. 从您的[!DNL Assets]实例`https://[aem_server]:[port]/system/console/configMgr`中打开Configuration Manager。
1. 编辑配置`com.day.cq.dam.ids.impl.IDSJobProcessor.name`。
1. 选择&#x200B;**[!UICONTROL ids.cc.enable]**&#x200B;选项，然后单击&#x200B;**[!UICONTROL 保存]**。

>[!NOTE]
>
>对于与[!DNL Assets]的[!DNL InDesign Server]集成，请使用多核处理器，因为单核系统不支持集成所需的会话支持功能。

## 配置Experience Manager凭据{#configure-aem-credentials}

您可以更改从AEM实例访问InDesign服务器的默认管理员凭据（用户名和密码），而不中断与Adobe InDesign服务器的集成。

1. 转到 `/etc/cloudservices/proxy.html`.
1. 在对话框中，指定新的用户名和密码。
1. 保存凭据。
