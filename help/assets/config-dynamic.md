---
title: 配置Dynamic Media — 混合模式
seo-title: 配置Dynamic Media — 混合模式
description: 了解如何配置Dynamic Media — 混合模式。
seo-description: 了解如何配置Dynamic Media — 混合模式。
uuid: de88f68f-4697-4ff0-8008-3ae6a4684a84
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 821eb27e-67c9-4589-9196-30dacb84fa59
exl-id: 1e122f97-ac37-44f5-a1cd-bf53ffda6f5b
feature: 配置，混合模式
role: Admin,User,Developer
source-git-commit: 9bd173e99c2bbedc77afb11b4c1eac423c62ef30
workflow-type: tm+mt
source-wordcount: '7796'
ht-degree: 1%

---

# 配置Dynamic Media — 混合模式 {#configuring-dynamic-media-hybrid-mode}

Dynamic Media — 需要启用并配置混合功能以供使用。 根据您的用例，Dynamic Media具有多个[受支持的配置](#supported-dynamic-media-configurations)。

>[!NOTE]
>
>如果您打算在Scene7运行模式下配置和运行Dynamic Media，请参阅[配置Dynamic Media - Scene7模式](config-dms7.md)。
>
>如果您打算在混合运行模式下配置和运行Dynamic Media，请按照本页中的说明操作。

了解有关在Dynamic Media中使用[video](video.md)的更多信息。

如果您使用Adobe Experience Manager为不同的环境（如开发环境、暂存环境和实时生产环境）进行设置，则需要为每个环境配置Dynamic MediaCloud Services。

如果您在Dynamic Media配置方面遇到问题，一个重要的查找位置是特定于Dynamic Media的日志文件。 在启用Dynamic Media时，会自动安装这些组件：

* `s7access.log`
* `ImageServing.log`

[监控和维护AEM实例](/help/sites-deploying/monitoring-and-maintaining.md)中介绍了这些参数。

混合发布和交付是Dynamic Media新增的Adobe Experience Manager的核心功能。 混合发布允许您从云而不是AEM发布节点交付Dynamic Media资产，例如图像、集和视频。

其他内容(如Dynamic Media查看器、网站页面和静态内容)将继续从AEM发布节点提供。

如果您是Dynamic Media客户，则需要使用混合投放作为所有Dynamic Media内容的投放机制。

## 视频的混合发布架构 {#hybrid-publishing-architecture-for-videos}

![chlimage_1-506](assets/chlimage_1-506.png)

## 图像的混合发布架构 {#hybrid-publishing-architecture-for-images}

![chlimage_1-507](assets/chlimage_1-507.png)

## 支持的Dynamic Media配置 {#supported-dynamic-media-configurations}

以下配置任务引用了以下术语：

| **术语** | **Dynamic Media已启用** | **描述** |
|---|---|---|
| AEM创作节点 | 绿色圆圈中的白色复选标记 | 您部署到内部部署或通过Managed Services的创作节点。 |
| AEM发布节点 | 红方的白色“X”。 | 您部署到内部部署或通过Managed Services的发布节点。 |
| 图像服务发布节点 | 绿色圆圈中的白色复选标记。 | 您在由Adobe管理的数据中心上运行的发布节点。 指图像服务URL。 |

您可以选择仅为成像、视频或成像和视频实施Dynamic Media。 要确定为特定方案配置Dynamic Media的步骤，请参阅下表。

<table> 
 <tbody> 
  <tr> 
   <td><strong>方案</strong></td> 
   <td><strong>工作原理</strong></td> 
   <td><strong>配置步骤</strong></td> 
  </tr> 
  <tr> 
   <td>在生产中仅提供图像</td> 
   <td>图像通过Adobe全球数据中心的服务器交付，然后由CDN缓存，以实现可扩展的性能和全球覆盖范围。</td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>节点上， <a href="#enabling-dynamic-media">启用Dynamic Media</a>。</li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services</a>中配置成像。</li> 
     <li><a href="#configuring-image-replication">配置图像复制</a>。</li> 
     <li><a href="#replicating-catalog-settings">复制目录设置</a>。</li> 
     <li><a href="#replicating-viewer-presets">复制查看器预设</a>。</li> 
     <li><a href="#using-default-asset-filters-for-replication">使用默认资产过滤器进行复制</a>。</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">配置Dynamic Media图像服务器设置</a>。</li> 
     <li><a href="#delivering-assets">交付资产</a>。</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>仅在预生产（开发、QE、暂存等）中提供图像。</td> 
   <td>图像通过AEM发布节点交付。 在这种情况下，由于流量很小，因此无需将图像交付到Adobe的数据中心。 另一个好处是，这允许在生产启动之前安全预览内容</td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>节点上， <a href="#enabling-dynamic-media">启用Dynamic Media</a>。</li> 
     <li>在AEM <strong>publish</strong>节点上， <a href="#enabling-dynamic-media">启用Dynamic Media</a>。</li> 
     <li><a href="#replicating-viewer-presets">复制查看器预设</a>。</li> 
     <li>为非生产图像设置<a href="#setting-up-asset-filters-for-imaging-in-non-production-deployments">资产筛选器</a>。</li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">配置Dynamic Media图像服务器设置。</a></li> 
     <li><a href="#delivering-assets">交付资产。</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>在任何环境（生产、开发、QE、暂存等）中仅提供视频</td> 
   <td>视频由CDN交付和缓存，以实现可扩展的性能和全球范围。 视频海报图像（在开始播放之前显示的视频缩略图）将由AEM发布实例交付。</td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>节点上， <a href="#enabling-dynamic-media">启用Dynamic Media</a>。</li> 
     <li>在AEM <strong>publish</strong>节点上， <a href="#enabling-dynamic-media">启用dynamic media</a>（发布实例提供视频海报图像并提供视频播放的元数据）。</li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services中配置视频。</a></li> 
     <li><a href="#replicating-viewer-presets">复制查看器预设</a>。</li> 
     <li>为纯视频</a>设置<a href="#setting-up-asset-filters-for-video-only-deployments">资产筛选器。</a></li> 
     <li><a href="#delivering-assets">交付资产。</a></li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>在生产中提供图像和视频</td> 
   <td><p>视频由CDN交付和缓存，以实现可扩展的性能和全球范围。 图像和视频海报图像通过Adobe全球数据中心的服务器提供，然后由CDN缓存，以实现可扩展的性能和全球覆盖范围。</p> <p>有关在预生产中设置图像或视频的信息，请参阅前面的章节。 </p> </td> 
   <td> 
    <ol> 
     <li>在AEM <strong>author</strong>节点上， <a href="#enabling-dynamic-media">启用Dynamic Media</a>。</li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services中配置视频。</a></li> 
     <li>在<a href="#configuring-dynamic-media-cloud-services">Dynamic MediaCloud Services中配置成像。</a></li> 
     <li><a href="#configuring-image-replication">配置图像复制</a>。</li> 
     <li><a href="#replicating-catalog-settings">复制目录设置</a>。</li> 
     <li><a href="#replicating-viewer-presets">复制查看器预设</a>。</li> 
     <li><a href="#using-default-asset-filters-for-replication">使用默认资产过滤器进行复制。</a></li> 
     <li><a href="#configuring-dynamic-media-image-server-settings">配置Dynamic Media图像服务器设置。</a></li> 
     <li><a href="#delivering-assets">交付资产。</a></li> 
    </ol> </td> 
  </tr> 
 </tbody> 
</table>

## 启用Dynamic Media {#enabling-dynamic-media}

[默认](https://www.adobe.com/solutions/web-experience-management/dynamic-media.html) 情况下，动态媒体处于禁用状态。要利用Dynamic Media功能，您需要使用&#x200B;**[!UICONTROL dynamicmedia]**&#x200B;运行模式来启用Dynamic Media，例如，使用&#x200B;**[!UICONTROL publish]**&#x200B;运行模式。 在启用之前，请确保查看[技术要求](/help/sites-deploying/technical-requirements.md#requirements-for-aem-dynamic-media-add-on)。

>[!NOTE]
>
>通过运行模式启用Dynamic Media取代了在AEM 6.1和AEM 6.0中启用Dynamic Media的功能，具体方法是将&#x200B;**[!UICONTROL dynamicMediaEnabled]**&#x200B;标记设置为&#x200B;**[!UICONTROL true]**。 此标记在AEM 6.2及更高版本中不起作用。 此外，您无需重新启动快速启动即可启用Dynamic Media。

启用Dynamic Media后，Dynamic Media功能将在UI中可用，并且每个上传的图像资产都会收到一个`cqdam.pyramid.tiff`演绎版，用于快速交付动态图像演绎版。 这些PTIFF具有显着优势，包括(1)能够仅管理单个主控图像并在无任何额外存储的情况下即时生成无限演绎版，以及(2)能够使用交互式可视化图表，例如缩放、平移、旋转等。

如果要在AEM中使用Dynamic Media Classic，则不应启用Dynamic Media，除非您使用的是[特定方案](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media)。 Dynamic Media被禁用，除非您通过runmode启用Dynamic Media。

要启用Dynamic Media，必须通过命令行或快速启动文件名启用Dynamic Media运行模式。

**要启用Dynamic Media**，请执行以下操作：

1. 在命令行中，启动快速启动时，请执行以下操作：

   * 在启动jar文件时，将&#x200B;**[!UICONTROL -r dynamicmedia]**&#x200B;添加到命令行的末尾。

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -r dynamicmedia
   ```

   如果您要发布到s7delivery，则还需要包含以下trustStore参数：

   ```shell
   -Djavax.net.ssl.trustStore=<absoluteFilePath>/customerTrustStoreFileName>
   
    -Djavax.net.ssl.trustStorePassword=<passwordForTrustStoreFile>
   ```

1. 请求`http://localhost:4502/is/image`并确保Image Server当前正在运行。

   >[!NOTE]
   >
   >要对Dynamic Media的问题进行故障诊断，请参阅&#x200B;**[!UICONTROL crx-quickstart/logs/]**&#x200B;目录中的以下日志：
   >
   >* ImageServer-&lt;PortId>-&lt;yyyy>&lt;mm>&lt;dd>.log - ImageServer日志提供用于分析内部ImageServer进程行为的统计和分析信息。

      图像服务器日志文件名的示例：`ImageServer-57346-2019-07-25.log`
   * s7access-&lt;yyyy>&lt;mm>&lt;dd>.log - s7access日志记录通过`/is/image`和`/is/content`对Dynamic Media发出的每个请求。
   这些日志仅在启用Dynamic Media时才使用。 从&#x200B;**[!UICONTROL system/console/status-Bundlelist]**&#x200B;页面生成的&#x200B;**Download Full**&#x200B;包中未包含这些参数；在致电客户支持(如果您遇到Dynamic Media问题)时，请将这两个日志附加到问题后面。

### 如果您将AEM安装到其他端口或上下文路径…… {#if-you-installed-aem-to-a-different-port-or-context-path}

如果要将[AEM部署到应用程序服务器](/help/sites-deploying/application-server-install.md)并启用Dynamic Media，则需要在外部器中配置&#x200B;**self**&#x200B;域。 否则，Dynamic Media资产将无法正常生成资产的缩略图。

此外，如果在其他端口或上下文路径上运行快速启动，则还必须更改&#x200B;**self**&#x200B;域。

启用Dynamic Media后，图像资产的静态缩略图呈现将使用Dynamic Media生成。 为了使缩略图生成功能在Dynamic Media中正常工作，AEM必须对其自身执行URL请求，并且必须知道端口号和上下文路径。

在AEM中：

* [externalizer](/help/sites-developing/externalizer.md)中的&#x200B;**self**&#x200B;域用于检索端口号和上下文路径。
* 如果未配置&#x200B;**self**&#x200B;域，则从Jetty HTTP服务中检索端口号和上下文路径。

在AEM QuickStart WAR部署中，无法派生端口号和上下文路径，因此必须配置&#x200B;**self**&#x200B;域。 有关如何配置&#x200B;**self**&#x200B;域的[外部器文档](/help/sites-developing/externalizer.md)。

>[!NOTE]
在[AEM快速启动独立部署](/help/sites-deploying/deploy.md)中，通常不需要配置&#x200B;**self**&#x200B;域，因为可以自动配置端口号和上下文路径。 但是，如果所有网络接口都关闭，则需要配置&#x200B;**self**&#x200B;域。

## 禁用Dynamic Media  {#disabling-dynamic-media}

默认情况下，Dynamic Media未启用。 但是，如果您之前已启用Dynamic Media，则可能希望稍后将其关闭。

要在启用Dynamic Media后禁用它，请删除&#x200B;**[!UICONTROL -r dynamicmedia]**&#x200B;运行模式标记。

**要在启用Dynamic Media后将其禁用，请执行以下操作**:

1. 在命令行中，启动快速启动时，可以执行以下任一操作：

   * 启动JAR文件时，请勿将`-r dynamicmedia`添加到命令行中。

   ```shell
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar
   ```

1. 请求`http://localhost:4502/is/image`。 您收到一条消息，指出Dynamic Media已禁用。

   >[!NOTE]
   禁用Dynamic Media运行模式后，将自动跳过生成`qdam.pyramid.tiff`演绎版的工作流步骤。 此外，还会禁用动态呈现支持和其他Dynamic Media功能。
   另请注意，在配置AEM服务器后，如果禁用了Dynamic Media运行模式，则在该运行模式下上传的所有资产现在都将无效。

## （可选）将Dynamic Media预设和配置从6.3迁移到6.4，零停机时间 {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

如果您将AEM Dynamic Media从6.3升级到6.4(现在包括零停机时间（也称为“选择加入”）部署)，则需要运行以下curl命令，以便在CRXDE Lite中将所有预设和配置从`/etc`迁移到`/conf`。

**注意**:如果您在兼容模式（即，已安装兼容包）下运行AEM实例，则无需运行这些命令。

要将自定义预设和配置从`/etc`迁移到`/conf`，请运行以下Linux curl命令：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

无论是否具有兼容包，您都可以对所有升级，通过运行以下命令来复制现成查看器预设：

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## 配置图像复制 {#configuring-image-replication}

Dynamic Media图像交付的工作方式是：从AEM创作中发布图像资产（包括视频缩略图），并将其复制到Adobe的按需复制服务（复制服务URL）。 然后，资产会通过按需图像交付服务（图像服务URL）来交付。

您必须执行以下操作：

1. [设置身份验证](#setting-up-authentication)。
1. [配置复制代理](#configuring-the-replication-agent)。

复制代理将Dynamic Media资产（如图像、视频元数据）和集发布到Adobe托管的图像服务。 默认情况下，复制代理未启用。

配置复制代理后，您需要[验证并测试它是否已成功设置](#validating-the-replication-agent-for-dynamic-media)。 本节将介绍这些步骤。

>[!NOTE]
创建PTIFF的默认内存限制为跨所有工作流的3 GB。 例如，您可以在其他工作流暂停时处理一个需要3 GB内存的映像，也可以并行处理10个每个需要300 MB内存的映像。
内存限制是可配置的，应适合系统资源可用性和正在处理的图像内容类型。 如果您拥有许多非常大的资产，并且系统上具有足够的内存，则可以提高此限制以确保并行处理图像。
超过最大内存限制的图像将被拒绝。
要更改PTIFF创建的内存限制，请导航至&#x200B;**[!UICONTROL 工具>操作> Web控制台> Adobe CQ Scene7 PTiffManager]**&#x200B;并更改`maxMemory`值。

### 设置身份验证 {#setting-up-authentication}

您需要在作者上设置复制身份验证，才能将图像复制到Dynamic Media图像交付服务。 为此，请获取一个KeyStore，然后将其保存在&#x200B;**[!UICONTROL dynamic-media-replication]**&#x200B;用户下，并对其进行配置。 在配置过程中，公司管理员应收到一封欢迎电子邮件，其中包含KeyStore文件和必要的凭据。 如果您未收到此邮件，请联系客户关怀团队。

**要设置身份验证**:

1. 如果您尚未获得KeyStore文件和密码，请联系客户关怀团队。 这是配置的一部分，它会将密钥关联到您的帐户。
1. 在AEM中，点按AEM徽标以访问全局导航控制台，然后点按&#x200B;**[!UICONTROL 工具>安全>用户]**。
1. 在“用户管理”页面上，导航到&#x200B;**[!UICONTROL dynamic-media-replication]**&#x200B;用户，然后点按以打开。

   ![dm复制](assets/dm-replication.png)

1. 在“编辑Dynamic-media-replication的用户设置”页中，点按&#x200B;**[!UICONTROL KeyStore]**&#x200B;选项卡，然后点按&#x200B;**[!UICONTROL 创建KeyStore]**。

   ![dm-replication-keystore](assets/dm-replication-keystore.png)

1. 在&#x200B;**[!UICONTROL Set KeyStore Access Password]**&#x200B;对话框中输入密码并确认密码。

   >[!NOTE]
   请记住您输入的密码。 以后配置&#x200B;**[!UICONTROL 复制代理]**&#x200B;时，需要再次输入。

   ![chlimage_1-508](assets/chlimage_1-508.png)

1. 在&#x200B;**[!UICONTROL 编辑Dynamic-media-replication的用户设置]**&#x200B;页面中，展开&#x200B;**[!UICONTROL 从KeyStore文件添加私钥]**&#x200B;区域，然后添加以下内容（请参阅下面的图像）：

   * 在&#x200B;**[!UICONTROL New Alias]**&#x200B;字段中，输入稍后在复制配置中使用的别名的名称；例如， **replication**。
   * 点按&#x200B;**[!UICONTROL KeyStore文件]**。 导航到通过Adobe提供给您的KeyStore文件，将其选中，然后点按&#x200B;**[!UICONTROL Open]**。
   * 在&#x200B;**[!UICONTROL KeyStore File Password]**&#x200B;字段中，输入KeyStore File密码。 这是您在步骤5中创建的KeyStore密码&#x200B;_不_，但是是在预配期间发送给您的欢迎电子邮件中提供的KeyStore文件密码Adobe。 如果您未收到KeyStore文件密码，请联系Adobe客户关怀团队。
   * 在&#x200B;**[!UICONTROL 私钥密码]**&#x200B;字段中，输入私钥密码（可能与上一步中提供的私钥密码相同）。 Adobe在预配期间向您发送的欢迎电子邮件中提供私钥密码。 如果您未收到私钥密码，请联系Adobe客户关怀。
   * 在&#x200B;**[!UICONTROL 私钥别名]**&#x200B;字段中，输入私钥别名。 例如，`companyname-alias`。 Adobe在预配期间向您发送的欢迎电子邮件中提供私钥别名。 如果您未收到私钥别名，请联系Adobe客户关怀。

   ![edit_settings_fordynamic-media-replication2](assets/edit_settings_fordynamic-media-replication2.png)

1. 点按&#x200B;**[!UICONTROL 保存并关闭]**，以将更改保存到此用户。

   接下来，您需要[配置复制代理。](#configuring-the-replication-agent)

### 配置复制代理 {#configuring-the-replication-agent}

1. 在AEM中，点按AEM徽标以访问全局导航控制台，然后点按&#x200B;**[!UICONTROL 工具>部署>复制>作者上的代理]**。
1. 在创作代理页面上，点按&#x200B;**[!UICONTROL Dynamic Media混合图像复制(s7delivery)]**。
1. 点按&#x200B;**[!UICONTROL 编辑]**。
1. 点按&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡，然后输入以下内容：

   * **[!UICONTROL 已启用]**  — 选中此复选框可启用复制代理。
   * **[!UICONTROL 区域]**  — 设置为相应的区域：北美洲、欧洲或亚洲
   * **[!UICONTROL 租户ID]**  — 此值是发布到复制服务的公司/租户的名称。此值是Adobe在配置期间发送给您的欢迎电子邮件中提供的租户ID。 如果您未收到此信息，请联系Adobe客户关怀。
   * **[!UICONTROL 密钥存储别名]**  — 此值与在设置身份验证中生成密钥时设置的**新别名** [值相同](#setting-up-authentication);例如 `replication`。（请参阅[设置身份验证](#setting-up-authentication)中的步骤7。）
   * **[!UICONTROL 密钥存储密码]**  — 这是您在点按创建密钥存储时创建的 **[!UICONTROL KeyStore密码]**。Adobe不提供此密码。 请参阅[设置身份验证](#setting-up-authentication)的步骤5。

   下图显示了包含示例数据的复制代理：

   ![chlimage_1-509](assets/chlimage_1-509.png)

1. 点按&#x200B;**[!UICONTROL 确定]**。

### 验证Dynamic Media的复制代理 {#validating-the-replication-agent-for-dynamic-media}

要验证Dynamic Media的复制代理，请执行以下操作：

点按&#x200B;**[!UICONTROL 测试连接]**。 输出示例如下：

```shell
11.03.2016 10:57:55 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
11.03.2016 10:57:55 - * Auth User: replication-receiver
11.03.2016 10:57:55 - * HTTP Version: 1.1
11.03.2016 10:57:55 - * Using OAuth 2.0 Authorization Grants
11.03.2016 10:57:55 - * OAuth 2.0 User: dynamic-media-replication
11.03.2016 10:57:55 - * OAuth 2.0 Token: '*****' initialized
11.03.2016 10:57:55 - Publishing: POST[https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=xfpuu-6613]
11.03.2016 10:57:55 - Publish response: OK[]
11.03.2016 10:57:55 - Transfer succeeded in 141 ms for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
-------------------------------------------------------------------------------------------------------------------------------
Replication test succeeded
```

>[!NOTE]
您还可以通过执行以下操作之一来检查：
* 检查复制日志，确保资产已复制。
* 发布图像。 点按图像，然后在下拉菜单中选择&#x200B;**[!UICONTROL 查看器]**。 选择查看器预设，然后点按&#x200B;**[!UICONTROL URL]**，并复制该URL并将其粘贴到浏览器中，以确认您能够看到该图像。


### 身份验证疑难解答 {#troubleshooting-authentication}

在设置身份验证时，您可能会在其解决方案中遇到以下问题。 在检查这些复制之前，请确保已设置复制。

#### 问题：包含消息的HTTP状态代码401 — 需要授权 {#problem-http-status-code-with-message-authorization-required}

此问题可能是由于未能为`dynamic-media-replication`用户设置KeyStore而引起的。

```shell
Replication test to s7delivery:https://s7bern.macromedia.com:8580/is-publish/
17.06.2016 18:54:43 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}
17.06.2016 18:54:43 - * Auth User: replication-receiver
17.06.2016 18:54:43 - * HTTP Version: 1.1
17.06.2016 18:54:43 - * Using OAuth 2.0 Authorization Grants
17.06.2016 18:54:43 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 18:54:43 - No OAuth token available. OAuth not initialized
17.06.2016 18:54:43 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 18:54:43 - Publishing: POST[https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough]
17.06.2016 18:54:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
17.06.2016 18:54:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309,
 userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
```

**解决方案**:检查是 `KeyStore` 否保存 **[!UICONTROL 到dynamic-media-]** replicationuser并提供了正确的密码。

#### 问题：无法解密密钥 — 无法解密数据 {#problem-could-not-decrypt-key-could-not-decrypt-data}

```xml
Replication test to s7delivery:https://<localhost>:8580/is-publish/
17.06.2016 19:00:16 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}
17.06.2016 19:00:16 - * Auth User: replication-receiver
17.06.2016 19:00:16 - * HTTP Version: 1.1
17.06.2016 19:00:16 - * Using OAuth 2.0 Authorization Grants
17.06.2016 19:00:16 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 19:00:16 - No OAuth token available. OAuth not initialized
17.06.2016 19:00:16 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 19:00:16 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}. java.lang.SecurityException: java.security.UnrecoverableKeyException: Could not decrypt key: Could not decrypt data.
```

**解决方案**:检查密码。复制代理中保存的密码与用于创建密钥库的密码不同。

#### 问题：InvalidAlgorithmParameterException {#problem-invalidalgorithmparameterexception}

此问题是由AEM创作实例中的配置错误引起的。 作者上的Java进程未获得正确的`javax.net.ssl.trustStore`。 您会在复制日志中看到以下错误：

```shell
14.04.2016 09:37:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
14.04.2016 09:37:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

或者错误日志：

```shell
07.25.2019 12:00:59.893 *ERROR* [sling-threadpool-db2763bb-bc50-4bb5-bb64-10a09f432712-(apache-sling-job-thread-pool)-90-com_day_cq_replication_job_s7delivery(com/day/cq/replication/job/s7delivery)] com.day.cq.replication.Agent.s7delivery.queue Error during processing of replication.
 
java.io.IOException: Failed to execute request 'https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
        at com.scene7.is.catalog.service.publish.atomic.PublishingServiceHttp.executePost(PublishingServiceHttp.scala:195)
```

**解决方案**:确保AEM Author上的java进程将系统属性-Djavax.net.ssl. **trustStore=** 设置为有效的truststore。

#### 问题：KeyStore未设置或未初始化 {#problem-keystore-is-either-not-set-up-or-it-is-not-initialized}

此问题可能由热修复或覆盖&#x200B;**[!UICONTROL dynamic-media-user]**&#x200B;或&#x200B;**[!UICONTROL keystore]**&#x200B;节点的功能包引起。

复制日志示例：

```shell
Replication test to s7delivery:https://replicate-na.assetsadobe.com/is-publish
02.08.2016 14:37:44 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}
02.08.2016 14:37:44 - * Auth User: replication-receiver
02.08.2016 14:37:44 - * HTTP Version: 1.1
02.08.2016 14:37:44 - * Using OAuth 2.0 Authorization Grants
02.08.2016 14:37:44 - * OAuth 2.0 User: dynamic-media-replication
02.08.2016 14:37:44 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}. com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised key store for user dynamic-media-replication
```

**解决方案**：

1. 导航到&#x200B;**[!UICONTROL User Management]**&#x200B;页面：

   `localhost:4502/libs/granite/security/content/useradmin.html`
1. 在&#x200B;**[!UICONTROL 用户管理]**&#x200B;页面上，导航到&#x200B;**[!UICONTROL dynamic-media-replication]**&#x200B;用户，然后点按以打开。
1. 点按&#x200B;**[!UICONTROL KeyStore]**&#x200B;选项卡。 如果出现&#x200B;**[!UICONTROL Create KeyStore]**&#x200B;按钮，则您需要重做之前[Setting up Authentication](#setting-up-authentication)下的步骤。
1. 如果必须重做&#x200B;**[!UICONTROL KeyStore]**&#x200B;设置，则可能还需要再次执行[配置复制代理](config-dynamic.md#configuring-the-replication-agent)。

   重新配置s7delivery复制代理。

   `localhost:4502/etc/replication/agents.author/s7delivery.html`

1. 点按&#x200B;**[!UICONTROL 测试连接]**&#x200B;以验证配置是否有效。

#### 问题：发布代理使用SSL而不是OAuth {#problem-publish-agent-is-using-ssl-instead-of-oauth}

此问题可能是由于修补程序或功能包未正确安装或覆盖设置所致。

复制日志示例：

```shell
01.08.2016 18:42:59 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}
01.08.2016 18:42:59 - * Auth User: replication-receiver
01.08.2016 18:42:59 - * HTTP Version: 1.1
01.08.2016 18:42:59 - * Using Client Auth SSL alias - replication-receiver *
01.08.2016 18:42:59 - Publishing: POST[https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=altayerstaging]
01.08.2016 18:42:59 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
01.08.2016 18:42:59 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
```

**解决方案：**

1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。

   `localhost:4502/crx/de/index.jsp`

1. 导航到&#x200B;**[!UICONTROL s7delivery Replication Agent]**&#x200B;节点。

   `localhost:4502/crx/de/index.jsp#/etc/replication/agents.author/s7delivery/jcr:content`

1. 将此设置添加到复制代理（值设置为&#x200B;**[!UICONTROL True]**&#x200B;的布尔值）：

   `enableOauth=true`

1. 在页面的左上角附近，点按&#x200B;**[!UICONTROL 全部保存]**。

### 测试配置 {#testing-your-configuration}

Adobe建议您对配置进行端到端测试。

在开始此测试之前，请确保您已经执行了以下操作：

* 添加了图像预设。
* 在&#x200B;**[!UICONTROL Cloud Services]**&#x200B;下配置&#x200B;**Dynamic Media配置（6.3之前）**。 此测试需要图像服务URL

要测试您的配置，请执行以下操作：

1. 上传图像资产。 （在Assets中，点按&#x200B;**[!UICONTROL 创建>文件]**，然后选择文件。）
1. 等待工作流完成。
1. 发布图像资产。 （选择资产，然后点按&#x200B;**[!UICONTROL 快速发布]**。）
1. 通过打开图像并点按&#x200B;**[!UICONTROL 演绎版]**，导航到该图像的演绎版。

   ![chlimage_1-510](assets/chlimage_1-510.png)

1. 选择任何动态演绎版。
1. 点按&#x200B;**[!UICONTROL URL]**&#x200B;以获取此资产的URL。
1. 导航到选定的URL并检查图像是否按预期运行。

测试已交付资产的另一种方法是，在URL后附加req=exists。

## 配置Dynamic MediaCloud Services {#configuring-dynamic-media-cloud-services}

Dynamic Media云服务支持云服务，例如混合发布和交付图像和视频、视频分析和视频编码等。

在配置中，您需要输入注册ID、视频服务URL、图像服务URL、复制服务URL并设置身份验证。 在帐户配置过程中，您应该已收到所有这些信息。 如果您未收到此信息，请联系Adobe Experience Manager管理员或Adobe技术支持以获取该信息。

>[!NOTE]
在设置Dynamic MediaCloud Services之前，请确保设置了您的发布实例。 在配置Dynamic MediaCloud Services之前，您还必须设置复制。

**要配置Dynamic Media云服务**:

1. 在AEM中，点按AEM徽标以访问全局导航控制台，然后点按&#x200B;**[!UICONTROL 工具>Cloud Services>Dynamic Media配置（6.3之前）]**。
1. 在&#x200B;**[!UICONTROL Dynamic Media配置浏览器]**&#x200B;页面的左窗格中，选择&#x200B;**[!UICONTROL 全局]**，然后点按&#x200B;**[!UICONTROL 创建]**。
1. 在&#x200B;**[!UICONTROL 创建Dynamic Media配置]**&#x200B;对话框的&#x200B;**[!UICONTROL 标题]**&#x200B;字段中，键入标题。
1. 如果要为视频配置Dynamic Media,

   * 在&#x200B;**[!UICONTROL 注册ID]**&#x200B;字段中，键入您的注册ID。
   * 在&#x200B;**[!UICONTROL 视频服务URL]**&#x200B;字段中，输入Dynamic Media网关的视频服务URL。

1. 如果要配置Dynamic Media以进行成像，请在&#x200B;**[!UICONTROL 图像服务URL]**&#x200B;字段中，输入Dynamic Media网关的图像服务URL。
1. 点按&#x200B;**[!UICONTROL Save]**&#x200B;以返回到Dynamic Media配置浏览器页面。
1. 点按AEM徽标以访问全局导航控制台。

## 配置视频报告 {#configuring-video-reporting}

您可以使用Dynamic Media — 混合模式在AEM的多个安装中配置视频报告。

**何时使用：** 在您配置Dynamic Media配 **[!UICONTROL 置（6.3之前）]**&#x200B;时，开始提供包括视频报告在内的多项功能。该配置会在区域Analytics公司中创建一个报表包。 如果配置多个“创作”节点，则需为每个节点创建一个单独的报表包。 因此，各安装中的报表数据不一致。 此外，如果每个作者节点引用同一混合发布服务器，则上次作者安装会更改所有视频报告的目标报表包。 此问题会在报表包过多的Analytics系统上过载。

**入门：** 通过完成以下三项任务配置视频报告。

1. 在第一个“创作”节点上配置&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**&#x200B;后，创建[!DNL Video Analytics]预设包。 此初始任务很重要，因为它允许新配置继续使用同一报表包。
1. 将[!DNL Video Analytics]预设包安装到在&#x200B;***配置Dynamic Media配置（6.3之前）之前的任何***&#x200B;新&#x200B;***创作节点***&#x200B;中。

1. 验证并调试包安装。

### 在配置第一个创作节点后创建[!DNL Video Analytics]预设包 {#creating-a-video-analytics-preset-package-after-configuring-the-first-author-node}

完成此任务后，您将拥有一个包含[!DNL Video Analytics]预设的包文件。 这些预设包含报表包、跟踪服务器、跟踪命名空间和Marketing Cloud组织ID（如果可用）。

1. 如果尚未配置&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**。
1. （可选）查看并复制&#x200B;**[!UICONTROL 报表包ID]**（您必须有权访问JCR）。 虽然不需要使用&#x200B;**[!UICONTROL 报表包ID]**，但它可以更轻松地进行验证。
1. 使用&#x200B;**[!UICONTROL 包管理器]**&#x200B;创建包。
1. 编辑包以包含过滤器。

   在AEM中：`/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

1. 构建包。
1. 下载或共享[!DNL Video Analytics]预设包，以便能够与后续的新创作节点共享该预设包。

### 在配置其他创作节点之前安装[!DNL Video Analytics]预设包 {#installing-the-video-analytics-preset-package-before-you-configure-additional-author-nodes}

确保在&#x200B;_之前完成此任务_&#x200B;配置&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**。 如果未能这样做，则会创建另一个未使用的报表包。 此外，即使视频报告可以继续正常工作，数据收集也不会得到优化。

确保新的“创作”节点上可以访问第一个“创作”节点中的[!DNL Video Analytics]预设包。

1. 将您之前创建的[!DNL Video Analytics]预设包上载到&#x200B;**[!UICONTROL 包管理器]**。
1. 安装[!DNL Video Analytics]预设包。
1. 配置&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**。

### 验证和调试包安装 {#verifying-and-debugging-the-package-installation}

1. 执行以下任一操作以验证并（如有必要）调试包安装：

   * **通过 [!DNL Video Analytics] JCRT检查预**
设或通 [!DNL Video Analytics] 过JCR检查预设，您必须有权访问 **[!UICONTROL CRXDE Lite]**。

      AEM — 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中，导航到`/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata  `

      即`http://localhost:4502/crx/de/index.jsp#/conf/global/settings/dam/dm/presets/analytics/jcr%3Acontent/userdata`

      如果您无权访问“创作”节点上的&#x200B;**[!UICONTROL CRXDE Lite]**，则可以通过“发布”服务器检查预设。

   * **通过图 [!DNL Video Analytics] 像服务器检查预设**

      您可以通过发出图像服务器`req=userdata`请求直接验证[!DNL Video Analytics]预设。

      例如，要在“创作”节点上查看[!DNL Video Analytics]预设，您可以发出以下请求：

      `http://localhost:4502/is/image/conf/global/settings/dam/dm/presets/analytics?req=userdata`

      要在发布服务器上验证预设，您可以向发布服务器发出类似的直接请求。 创作和发布节点上的响应是相同的。 响应类似于以下内容：

      ```
      marketingCloudOrgId=0FC4E86B573F99CC7F000101
       reportSuite=aemaem6397618-2018-05-23
       trackingNamespace=aemvideodal
       trackingServer=aemvideodal.d2.sc.omtrdc.net
      ```

   * **通过AEM [!DNL Video Analytics] 中的视频报告工具检查预设**

      点按&#x200B;**[!UICONTROL 工具>资产>视频报告]** `http://localhost:4502/mnt/overlay/dam/gui/content/s7dam/videoreports/videoreport.html`

      如果您看到以下错误消息，则报表包可用，但未填充。 在系统收集任何数据之前，在新安装中，此错误是正确的（也是必需的）。

      ![screen_shot_2018-05-23at52254pm](assets/screen_shot_2018-05-23at52254pm.png)
   要生成报表数据，请上传并发布一个视频。 使用&#x200B;**[!UICONTROL 复制URL]**&#x200B;并至少运行一次视频。

   请注意，使用视频查看器填充报表数据可能最长需要12小时。

   如果出现错误且报表包设置不正确，则会显示以下警报。

   ![screen_shot_2018-05-23at52612pm](assets/screen_shot_2018-05-23at52612pm.png)

   如果在配置&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**&#x200B;服务之前运行视频报告，则也会显示此错误。

### 视频报告配置疑难解答 {#troubleshooting-the-video-reporting-configuration}

* 在安装过程中，有时与Analytics API服务器的连接会超时。 安装会重试连接20次，但仍会失败。 出现这种情况时，日志文件会记录多个错误。 搜索 `SiteCatalystReportService`.
* 如果先不安装[!DNL Video Analytics]预设包，则可能会创建新报表包。
* 从AEM 6.3升级到AEM 6.4或AEM 6.4.1，然后配置&#x200B;**[!UICONTROL Dynamic Media配置（6.3之前）]**，仍会创建报表包。 此问题已知并将在AEM 6.4.2中修复。

### 关于[!DNL Video Analytics]预设 {#about-the-video-analytics-preset}

[!DNL Video Analytics]预设（有时简称为Analytics预设）存储在Dynamic Media中的查看器预设旁边。 它基本上与查看器预设相同，但包含用于配置AppMeasurement和视频心率报告的信息。

预设的属性如下所示：

* **[!UICONTROL reportSuite]**
* **[!UICONTROL trackingServer]**
* **[!UICONTROL trackingNamespace]**
* **[!UICONTROL marketingCloudOrgId]** (旧版AEM中不存在)

AEM 6.4及更高版本将此预设保存在`/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

## 复制目录设置 {#replicating-catalog-settings}

在设置过程中，您必须通过JCR发布自己的默认目录设置。 要复制目录设置，请执行以下操作：

1. 在“终端”窗口中，运行以下命令：

   `curl -u admin:admin localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

1. 在AEM中，导航到&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中的以下位置（需要管理员权限）：

   `https://<server>:<port>/crx/de/index.jsp#/conf/global/settings/dam/dm/imageserver/`

1. 点按&#x200B;**[!UICONTROL 复制]**&#x200B;选项卡。
1. 点按&#x200B;**[!UICONTROL 复制]**。

## 复制查看器预设 {#replicating-viewer-presets}

要交付带有查看器预设的资产，您必须复制/发布查看器预设。 （必须激活&#x200B;_和_&#x200B;以复制所有查看器预设，才能获取资产的URL或嵌入代码。） 有关更多信息，请参阅[发布查看器预设](managing-viewer-presets.md#publishing-viewer-presets) 。

>[!NOTE]
默认情况下，当您选择&#x200B;**[!UICONTROL 演绎版]**&#x200B;时，系统会显示各种演绎版；当您在资产的详细信息视图中选择&#x200B;**[!UICONTROL 查看器]**&#x200B;时，系统会显示各种查看器预设。 您可以增加或减少可见的数量。 请参阅[增加显示](/help/assets/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display)或[的图像预设数。增加显示](/help/assets/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display)的查看器预设数。

## 筛选复制资产 {#filtering-assets-for-replication}

在非Dynamic Media部署中，您会将&#x200B;_所有_&#x200B;资产（包括图像和视频）从AEM创作环境复制到AEM发布节点。 此工作流是必需的，因为AEM发布服务器也会交付资产。

但是，在Dynamic Media部署中，由于资产是通过云传送的，因此无需将这些资产复制到AEM发布节点。 这种“混合发布”工作流可避免复制资产所需的额外存储成本和较长的处理时间。 其他内容(如Dynamic Media查看器、网站页面和静态内容)将继续从AEM发布节点提供。

除复制资产外，还复制以下非资产：

* Dynamic Media交付配置：`/conf/global/settings/dam/dm/imageserver/configuration/jcr:content/settings`
* 图像预设: `/conf/global/settings/dam/dm/presets/macros`
* 查看器预设: `/conf/global/settings/dam/dm/presets/viewer`

这些过滤器为您提供了一种方法，可让您将&#x200B;_排除_&#x200B;资产复制到AEM发布节点。

### 使用默认资产过滤器进行复制 {#using-default-asset-filters-for-replication}

如果您在生产&#x200B;_或_ 2)图像和视频中使用Dynamic Media for 1)图像，则可以使用我们按原样提供的默认滤镜。 默认情况下，以下过滤器处于活动状态：

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>筛选器</strong></td> 
   <td><strong>Mime 类型</strong></td> 
   <td><strong>演绎版</strong></td> 
  </tr> 
  <tr> 
   <td>Dynamic Media图像交付</td> 
   <td><p>过滤图像</p> <p>筛选集</p> <p> </p> </td> 
   <td><p>以<strong>image/</strong>开头</p> <p>包含<strong>application/</strong>，以<strong>set</strong>结尾。</p> </td> 
   <td>现成的“滤镜图像”（适用于单个图像资产，包括交互式图像）和“滤镜集”（适用于旋转集、图像集、混合媒体集和轮播集）将： 
    <ul> 
     <li>包含PTIFF图像和用于复制的元数据（以<strong>cqdam</strong>开头的任何演绎版）。</li> 
     <li>从复制中排除原始图像和静态图像演绎版。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media视频交付</td> 
   <td>filter-video</td> 
   <td>以<strong>video/</strong>开头</td> 
   <td>现成的“filter-video”将： 
    <ul> 
     <li>包含用于复制的代理视频演绎版、视频缩略图/海报图像、元数据（在父视频演绎版和视频演绎版中均有）（以<strong>cqdam</strong>开头的任何演绎版）。</li> 
     <li>从复制中排除原始视频和静态缩略图演绎版。<br /> <br /> <strong>注意：</strong> 代理视频演绎版不包含二进制文件，而只是节点属性。因此，对发布者存储库大小没有影响。</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Dynamic Media Classic集成</td> 
   <td><p>过滤图像</p> <p>筛选集</p> <p>filter-video</p> </td> 
   <td><p>以<strong>image/</strong>开头</p> <p>包含<strong>application/</strong>，以<strong>set</strong>结尾。</p> <p>以<strong>video/</strong>开头</p> </td> 
   <td><p>您可以将传输URI配置为指向您的AEM发布服务器，而不是AdobeDynamic Media云复制服务URL。 设置此过滤器后，Dynamic Media Classic将能够交付资产，而不是AEM发布实例。</p> <p>现成的“filter-images”、“filter-sets”和“filter-video”将：</p> 
    <ul> 
     <li>包括PTIFF图像、代理视频演绎版和用于复制的元数据。 但是，由于运行AEM - Dynamic Media Classic集成的用户在JCR中不存在这些函数，因此JCR无法有效地执行任何操作。</li> 
     <li>从复制中排除原始图像、静态图像呈现、原始视频和静态缩略图呈现。 相反，Dynamic Media Classic将交付图像和视频资产。</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
过滤器应用于mime类型，不能特定于路径。

### 为纯视频部署设置资产过滤器 {#setting-up-asset-filters-for-video-only-deployments}

如果您使用Dynamic Media进行纯视频，请按照以下步骤设置资产过滤器以进行复制：

1. 在AEM中，点按AEM徽标以访问全局导航控制台，然后点按&#x200B;**[!UICONTROL 工具>部署>复制>作者上的代理]**。
1. 在“创作代理”页面上，点按&#x200B;**[!UICONTROL 默认代理（发布）]**。
1. 点按&#x200B;**[!UICONTROL 编辑]**。
1. 在&#x200B;**[!UICONTROL 代理设置]**&#x200B;对话框的[!UICONTROL 设置]选项卡中，选中&#x200B;**[!UICONTROL 启用]**&#x200B;以打开代理。
1. 点按&#x200B;**[!UICONTROL 确定]**。
1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。
1. 在左侧文件夹树中，导航到`/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`
1. 找到[!UICONTROL filter-video]，右键单击它并选择&#x200B;**[!UICONTROL Copy]**。
1. 在左侧文件夹树中，导航到`/etc/replication/agents.author/publish`
1. 找到[!UICONTROL jcr:content]，右键单击它并选择&#x200B;**[!UICONTROL 粘贴]**。

这会设置AEM发布实例以交付视频海报图像以及播放所需的视频元数据，而视频本身则由Dynamic Media云服务交付。 过滤器还将从复制中排除发布实例不需要的原始视频和静态缩略图演绎版。

### 在非生产部署中为成像设置资产过滤器 {#setting-up-asset-filters-for-imaging-in-non-production-deployments}

如果您在非生产部署中使用Dynamic Media进行成像，请按照以下步骤设置资产过滤器以进行复制：

1. 在AEM中，点按AEM徽标以访问全局导航控制台，然后点按&#x200B;**[!UICONTROL 工具>部署>复制>作者上的代理]**。
1. 在“创作代理”页面上，点按&#x200B;**[!UICONTROL 默认代理（发布）]**。
1. 点按&#x200B;**[!UICONTROL 编辑]**。
1. 在&#x200B;**[!UICONTROL 代理设置]**&#x200B;对话框的&#x200B;**[!UICONTROL 设置]**&#x200B;选项卡中，选中&#x200B;**[!UICONTROL 启用]**&#x200B;以打开代理。
1. 点按&#x200B;**[!UICONTROL 确定]**。
1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。
1. 在左侧文件夹树中，导航到`/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`

   ![image-2018-01-16-10-22-40-410](assets/image-2018-01-16-10-22-40-410.png)

1. 找到&#x200B;**[!UICONTROL filter-images]**，右键单击它并选择&#x200B;**[!UICONTROL Copy]**。
1. 在左侧文件夹树中，导航到`/etc/replication/agents.author/publish`
1. 找到&#x200B;**[!UICONTROL jcr:content]**，右键单击它并选择&#x200B;**[!UICONTROL 创建>创建节点]**。 输入类型`nt:unstructured`的名称`damRenditionFilters`。
1. 找到[!UICONTROL `damRenditionFilters`]，右键单击它并选择&#x200B;**[!UICONTROL 粘贴]**。

这可设置AEM发布实例以将图像交付到非生产环境。 过滤器还会从复制中排除原始图像和静态演绎版，这些在发布实例中不需要。

>[!NOTE]
如果作者中有许多不同的过滤器，则每个代理需要为其分配一个不同的用户。 Granite代码强制按用户使用一个过滤器模型。 对于每个过滤器设置，始终具有不同的用户。
如果您在服务器上使用多个过滤器（例如，一个用于复制的过滤器用于发布，另一个用于s7delivery的过滤器），则您需要确保这两个过滤器在&#x200B;**[!UICONTROL jcr:content]**&#x200B;节点中为它们分配了不同的&#x200B;**userId**。 请参阅下图：

![image-2018-01-16-10-26-28-465](assets/image-2018-01-16-10-26-28-465.png)

### 自定义用于复制的资产过滤器 {#customizing-asset-filters-for-replication}

要（可选）为复制自定义资产过滤器，请执行以下操作：

1. 在AEM中，点按AEM徽标以访问全局导航控制台，然后点按&#x200B;**[!UICONTROL 工具>常规>CRXDE Lite]**。
1. 在左侧文件夹树中，导航到`/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`以查看过滤器。

   ![chlimage_1-511](assets/chlimage_1-511.png)

1. 要为过滤器定义Mime类型，可以按如下方式找到Mime类型：

   在左边栏中，展开&#x200B;**[!UICONTROL content > dam > &lt;`locate_your_asset`> > jcr:content > metadata]**，然后在表中找到`dc:format`。

   下图是资产`dc:format`路径的示例。

   ![chlimage_1-512](assets/chlimage_1-512.png)

   请注意，资产`Fiji Red.jpg`的`dc:format`是`image/jpeg`。

   要使此过滤器应用于所有图像（无论其格式如何），请将值设置为`image/*`，其中`*`是应用于任何格式所有图像的正则表达式。

   要使过滤器仅应用于JPEG类型的图像，请输入值`image/jpeg`。

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

导航至 `content/dam/<locate_your_asset>/jcr:content/renditions`.

下图是资产演绎版的示例。

![chlimage_1-513](assets/chlimage_1-513.png)

使用上例，如果您只想复制PTIFF(Pyramid TIFF)，则可以输入`+cqdam,*`，其中包含以`cqdam`开头的所有演绎版。 在示例中，该呈现版本为`cqdam.pyramid.tiff`。

如果只想复制原件，则输入`+original`。

## 配置Dynamic Media图像服务器设置 {#configuring-dynamic-media-image-server-settings}

配置Dynamic Media图像服务器涉及编辑Adobe CQ Scene7 ImageServer包和Adobe CQ Scene7 PlatformServer包。

>[!NOTE]
Dynamic Media在启用](#enabling-dynamic-media)后即可使用[。 但是，您可以选择通过配置Dynamic Media Image Server以满足特定规范或要求来微调安装。

**先决条件**: __ 在配置Dynamic Media Image Server之前，请确保您的Windows虚拟机包含Microsoft Visual C++库的安装。运行Dynamic Media Image Server时需要这些库。 您可以在此处[下载Microsoft Visual C++ 2010 Redistributable Package(x64)](https://www.microsoft.com/en-us/download/details.aspx?id=26999)。

**要配置Dynamic Media图像服务器设置**:

1. 在AEM的左上角，点按&#x200B;**[!UICONTROL Adobe Experience Manager]**&#x200B;以访问全局导航控制台，然后点按&#x200B;**[!UICONTROL 工具>操作> Web控制台]**。
1. 在&#x200B;**[!UICONTROL Adobe Experience Manager Web控制台配置]**&#x200B;页面上，点按&#x200B;**[!UICONTROL OSGi >配置]** ，以列出AEM中当前运行的所有包。

   Dynamic Media交付服务器位于列表中的以下名称下：

   * **[!UICONTROL Adobe CQ Scene7 ImageServer]**
   * **[!UICONTROL Adobe CQ Scene7 PlatformServer]**

1. 在包列表的&#x200B;**[!UICONTROL Adobe CQ Scene7 ImageServer]**&#x200B;右侧，点按&#x200B;**[!UICONTROL 编辑]**&#x200B;图标。
1. 在&#x200B;**[!UICONTROL Adobe CQ Scene7 ImageServer]**&#x200B;对话框中，设置以下配置值：

   >[!NOTE]
   在大多数情况下，无需更改默认值。 但是，如果确实更改了默认值，则必须重新启动包才能使更改生效。

<table> 
 <tbody> 
  <tr> 
   <td><strong>属性</strong></td> 
   <td><strong>默认值</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>TcpPort.name</td> 
   <td><code><em>empty</em></code></td> 
   <td>用于与ImageServer进程通信的端口号。 默认情况下，会自动检测空闲端口。</td> 
  </tr> 
  <tr> 
   <td>AllowRemoteAccess.name</td> 
   <td><code><em>empty</em></code></td> 
   <td><p>允许或禁止远程访问ImageServer进程。 如果为false，则图像服务器仅监听本地主机。</p> <p>指向本地主机的默认外部器设置需要指定特定VM实例的实际域或IP地址。 原因是本地主机可能指向虚拟机的父系统。</p> <p>VM的域或IP地址可能需要有一个主机文件条目，以便它能够解析自身。</p> </td> 
  </tr> 
  <tr> 
   <td>MaxRenderRgnPixels</td> 
   <td>16兆帕</td> 
   <td>呈现的最大大小（以百万像素为单位）。</td> 
  </tr> 
  <tr> 
   <td>MaxMessageSize</td> 
   <td>16 MB</td> 
   <td>已传送的最大消息大小(MB)。</td> 
  </tr> 
  <tr> 
   <td>RandomAccessUrlTimeout</td> 
   <td>20</td> 
   <td>超时值，指ImageServer将等待JCR响应范围内的拼贴请求的时长（以秒为单位）。</td> 
  </tr> 
  <tr> 
   <td>WorkerThreads</td> 
   <td>10</td> 
   <td>工作线程数。</td> 
  </tr> 
 </tbody> 
</table>

1. 点按&#x200B;**[!UICONTROL 保存]**。
1. 在包列表的&#x200B;**[!UICONTROL Adobe CQ Scene7 PlatformServer]**&#x200B;右侧，点按&#x200B;**[!UICONTROL 编辑]**&#x200B;图标。
1. 在&#x200B;**[!UICONTROL Adobe CQ Scene7 PlatformServer]**&#x200B;对话框中，设置以下默认值选项：

   >[!NOTE]
   Dynamic Media Image Server使用其自己的磁盘缓存来缓存响应。 AEM HTTP缓存和Dispacher不能用于缓存来自Dynamic Media Image Server的响应。

   | **属性** | **默认值** | **描述** |
   |---|---|---|
   | **[!UICONTROL 已启用缓存]** | 已选中 | 是否启用响应缓存。 |
   | **[!UICONTROL 缓存根]** | 缓存 | 响应缓存文件夹的一个或多个路径。 相对路径针对内部s7成像包文件夹进行解析。 |
   | **[!UICONTROL 缓存最大大小]** | 200000000 | 响应缓存的最大大小（以字节为单位）。 |
   | **[!UICONTROL 缓存最大条目数]** | 100000 | 缓存中允许的最大条目数。 |

### 默认清单设置 {#default-manifest-settings}

默认清单允许您配置用于生成Dynamic Media投放响应的默认清单。 您可以微调质量（JPEG质量、分辨率、重新取样模式）、缓存（过期），并阻止渲染太大的图像(defaultpix、defaultthumbpix、maxpix)。

默认清单配置的位置取自&#x200B;**[!UICONTROL Adobe CQ Scene7 PlatformServer]**&#x200B;包的&#x200B;**[!UICONTROL 目录根]**&#x200B;默认值。 默认情况下，此值位于&#x200B;**[!UICONTROL 工具>常规>CRXDE Lite]**&#x200B;中的以下路径：

`/conf/global/settings/dam/dm/imageserver/`

![configimageservercrxdelite](assets/configimageservercrxdelite.png)

您可以通过输入新值来更改属性的值（如下表所述）。

完成对默认清单的更改后，点按页面左上角的&#x200B;**[!UICONTROL 全部保存]**。

请确保点按&#x200B;**[!UICONTROL 访问控制]**&#x200B;选项卡（位于&#x200B;**[!UICONTROL 属性]**&#x200B;选项卡的右侧），然后为每个用户和dynamic-media-replication用户将访问控制权限设置为`jcr:read`。

![configimageservercrxdeliteaccesscontroltab](assets/configimageservercrxdeliteaccesscontroltab.png)

清单设置表及其默认值：

<table> 
 <tbody> 
  <tr> 
   <td><strong>属性</strong></td> 
   <td><strong>默认值</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>bkgcolor</td> 
   <td>FFFFFF</td> 
   <td><p>默认背景颜色。 用于填充不包含实际图像数据的回复图像任何区域的RGB值。</p> <p>另请参阅图像提供API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html">BkgColor</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>defaultpix</td> 
   <td>三十万零三百</td> 
   <td><p>默认视图大小。 如果请求未使用wid=、hei=或scl=明确指定视图大小，则服务器将限制返回图像不大于此宽度和高度。</p> <p>指定为两个整数数字，0或更大，用逗号分隔。 宽度和高度（以像素为单位）。 可将任一或两个值都设置为0，以保持它们不受约束。 不适用于嵌套/嵌入的请求。</p> <p>另请参阅图像服务API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html">DefaultPix</a>。</p> <p>但是，通常情况下，您会使用查看器预设或图像预设来交付资产。 Defaultpix仅适用于未使用查看器预设或图像预设的资产。</p> </td> 
  </tr> 
  <tr> 
   <td>defaulthumbpix</td> 
   <td>十万零一百</td> 
   <td><p>默认缩略图大小。 对缩略图请求(req=tmb)使用的是：DefaultPix，而不是属性：:DefaultPix。</p> <p>如果缩略图请求(req=tmb)没有明确地指定大小，则服务器将限制返回图像不得大于此宽度和高度，而没有明确地使用wid=、hei=或scl=指定视图大小。</p> <p>指定为两个整数数字，0或更大，用逗号分隔。 宽度和高度（以像素为单位）。 可将任一或两个值都设置为0，以保持它们不受约束。 </p> <p>不适用于嵌套/嵌入的请求。</p> <p>另请参阅图像服务API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html">DefaultThumbPix</a>。 </p> </td> 
  </tr> 
  <tr> 
   <td>过期</td> 
   <td>36000000</td> 
   <td><p>默认的客户端缓存生存时间。 提供默认过期时间间隔，以防特定目录记录不包含有效的目录：：过期值。</p> <p>实数，0或更大。 自生成回复数据后到期的毫秒数。 设置为0时，将始终立即使回复图像过期，这会有效地禁用客户端缓存。 默认情况下，此值设置为10小时，这意味着如果发布了新图像，则旧图像需要10小时才能离开用户的缓存。 如果您需要尽早清除缓存，请联系客户关怀团队。</p> <p>另请参阅图像提供API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html">过期</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>jpegquality</td> 
   <td>80</td> 
   <td><p>默认JPEG编码属性。 指定JPEG回复图像的默认属性。</p> <p>整数和标记，以逗号分隔。 第一个值在1.100范围内，用于定义质量。 对于正常行为，第二个值可以为0，或者为1以禁用JPEG编码器通常使用的RGB色度下采样。</p> <p>另请参阅图像提供API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html">JpegQuality</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>maxpix</td> 
   <td>二十万零两百</td> 
   <td><p>回复图像大小限制。 返回到客户端的最大回复图像宽度和高度。</p> <p>如果请求导致返回图像的宽度或高度大于属性：:MaxPix，则服务器会返回错误。</p> <p>另请参阅图像服务API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html">MaxPix</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>resmode</td> 
   <td>SHARP2</td> 
   <td><p>默认重新取样模式。 指定用于缩放图像数据的默认重新取样属性和插值属性。</p> <p>在请求中未指定resMode=时使用。</p> <p>允许的值包括BILIN、BICUB或SHARP2。</p> <p>枚举。 对于bilin，设置为2；对于bicub，设置为3；对于sharp2插值模式，设置为4。 使用sharp2可获得最佳结果。</p> <p>另请参阅图像服务API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html">ResMode</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>分辨率</td> 
   <td>72</td> 
   <td><p>默认对象分辨率。 提供默认对象分辨率，以防特定目录记录不包含有效的目录：:Resolution值。</p> <p>实数，大于0。 通常以每英寸像素数表示，但也可以以其他单位表示，如每米像素数。</p> <p>另请参阅图像提供API中的<a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-resolution.html">分辨率</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>thumbnaitime</td> 
   <td>1%、11%、21%、31%、41%、51%、61%、71%、81%、91%</td> 
   <td>这些值表示视频播放时间的快照，并被传递到<a href="https://encoding.com/">encoding.com</a>。 有关更多信息，请参阅<a href="/help/assets/video.md#about-video-thumbnails">关于视频缩略图</a>。</td> 
  </tr> 
 </tbody> 
</table>

## 配置Dynamic Media色彩管理 {#configuring-dynamic-media-color-management}

Dynamic Media色彩管理允许您为预览资产校正颜色。

通过颜色校正，摄取的资产会在生成的金字塔TIFF呈现版本中保留其色彩空间（RGB、CMYK、灰色）和嵌入的色彩配置文件。 当您请求动态呈现时，图像颜色会校正到目标颜色空间中。 您可以在JCR的Dynamic Media发布设置中配置输出颜色配置文件。

Adobe色彩管理使用ICC配置文件，这是由国际色彩联盟(ICC)定义的格式。

您可以配置Dynamic Media色彩管理，并使用CMYK、RGB或灰度输出配置图像预设。 请参阅[配置图像预设](managing-image-presets.md)。

高级用例可以使用手动配置&#x200B;**[!UICONTROL icc=]**&#x200B;修饰符明确选择输出颜色配置文件：

* **[!UICONTROL icc]**  — 输出 [颜色配置文件。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html)

* **[!UICONTROL iccEmbed]**  — 嵌入 [颜色配置文件。](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html)

>[!NOTE]
只有安装了Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-12445)中的[功能包12445时，才能使用标准的Adobe颜色配置文件集。 所有功能包和Service Pack均可在[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)中找到。 功能包12445提供Adobe颜色配置文件。

### 安装功能包12445 {#installing-feature-pack}

您必须安装功能包12445才能使用Dynamic Media色彩管理功能。

**要安装功能包12445，请**:

1. 导航到[Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)并下载`cq-6.3.0-featurepack-12445`。

   有关在[!DNL Adobe Experience Manager]中使用包的详细信息，请参阅[如何使用包](/help/sites-administering/package-manager.md)。

1. 安装功能包。

### 配置默认颜色配置文件 {#configuring-the-default-color-profiles}

安装功能包后，在请求RGB或CMYK图像数据时，需要配置适当的默认颜色配置文件以启用颜色校正。

**要配置默认颜色配置文件**:

1. 在&#x200B;**[!UICONTROL 工具>常规>CRXDE Lite]**&#x200B;中，导航到`/conf/global/settings/dam/dm/imageserver/configuration/settings`，其中包含默认的Adobe Color配置文件。

   ![chlimage_1-514](assets/chlimage_1-514.png)

1. 通过滚动到&#x200B;**[!UICONTROL Properties]**&#x200B;选项卡的底部并手动输入属性名称、类型和值来添加颜色校正属性，下表中对该属性进行了说明。 在输入值后，点按&#x200B;**[!UICONTROL 添加]**，然后点按&#x200B;**[!UICONTROL 保存全部]**&#x200B;以保存您的值。

   颜色校正属性在&#x200B;**[!UICONTROL 颜色校正属性]**&#x200B;表中有介绍。 可以分配给颜色校正属性的值位于&#x200B;**[!UICONTROL 颜色配置文件]**&#x200B;表中。

   例如，在&#x200B;**[!UICONTROL 名称]**&#x200B;中，添加`iccprofilecmyk`，选择&#x200B;**[!UICONTROL 类型]** `String`，并将`WebCoated`添加为&#x200B;**[!UICONTROL 值]**。 点按&#x200B;**[!UICONTROL 添加]**，然后点按&#x200B;**[!UICONTROL 保存全部]**&#x200B;以保存您的值。

   ![chlimage_1-515](assets/chlimage_1-515.png)

   **颜色校正属性表**

   <table> 
    <tbody> 
      <tr> 
      <td><strong>属性</strong></td> 
      <td><strong>类型</strong></td> 
      <td><strong>默认</strong></td> 
      <td><strong>描述</strong></td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html">iccprofilergb</a></td> 
      <td>字符串</td> 
      <td>&lt;empty&gt;</td> 
      <td>默认RGB颜色配置文件的名称。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html">icprofilecmyk</a></td> 
      <td>字符串</td> 
      <td>&lt;empty&gt;</td> 
      <td>默认CMYK颜色配置文件的名称。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html">iccprofilegray</a></td> 
      <td>字符串</td> 
      <td>&lt;empty&gt;</td> 
      <td>默认灰色配置文件的名称。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcrgb.html">iccprofilescrgb</a></td> 
      <td>字符串</td> 
      <td>&lt;empty&gt;</td> 
      <td>默认RGB颜色配置文件的名称，该配置文件用于没有嵌入颜色配置文件的RGB图像</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrccmyk.html">icprofilesccmyk</a></td> 
      <td>字符串</td> 
      <td>&lt;empty&gt;</td> 
      <td>用于没有嵌入颜色配置文件的CMYK图像的默认CMYK颜色配置文件的名称。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcgray.html">iccprofilesrcgrey</a></td> 
      <td>字符串</td> 
      <td>&lt;empty&gt;</td> 
      <td>用于没有嵌入颜色配置文件的CMYK图像的默认灰色配置文件的名称。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccblackpointcompensation.html">iccblackpointcompensation</a></td> 
      <td>布尔型</td> 
      <td>True</td> 
      <td>指定在颜色校正期间是否应进行黑点补偿。 Adobe建议启用此设置。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccdither.html">icdither</a></td> 
      <td>布尔型</td> 
      <td>False</td> 
      <td>指定是否应在颜色校正期间进行抖动。</td> 
      </tr> 
      <tr> 
      <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html">icrenderintent</a></td> 
      <td>字符串</td> 
      <td>相对</td> 
      <td><p>指定渲染意图。 可接受的值包括：<strong>持久度、相对、饱和度、绝对。 </strong><i></i>Adobe建议 <strong>使 </strong><i></i>用相对作为默认值。</p> </td> 
      </tr> 
    </tbody> 
    </table>

   >[!NOTE]
   属性名称区分大小写，并且必须全部为小写。

   **颜色配置文件表**

   安装了以下颜色配置文件：

   <table> 
    <tbody> 
      <tr> 
      <th><p>名称</p> </th> 
      <th><p>色彩空间</p> </th> 
      <th><p>描述</p> </th> 
      </tr> 
      <tr> 
      <td>AdobeRGB</td> 
      <td>RGB</td> 
      <td>Adobe RGB（1998年）</td> 
      </tr> 
      <tr> 
      <td>AppleRGB</td> 
      <td>RGB</td> 
      <td>Apple RGB</td> 
      </tr> 
      <tr> 
      <td>CIERGB</td> 
      <td>RGB</td> 
      <td>CIE RGB</td> 
      </tr> 
      <tr> 
      <td>CoatedFogra27</td> 
      <td>CMYK</td> 
      <td>涂层FOGRA27(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CoatedFogra39</td> 
      <td>CMYK</td> 
      <td>涂层FOGRA39(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>CoatedGraCol</td> 
      <td>CMYK</td> 
      <td>涂层GRACoL 2006(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>ColorMatchRGB</td> 
      <td>RGB</td> 
      <td>颜色匹配RGB</td> 
      </tr> 
      <tr> 
      <td>EuropeISOCoated</td> 
      <td>CMYK</td> 
      <td>欧洲ISO涂层FOGRA27</td> 
      </tr> 
      <tr> 
      <td>EuroscaleCoated</td> 
      <td>CMYK</td> 
      <td>Euroscale Coated v2</td> 
      </tr> 
      <tr> 
      <td>EuroscaleUncoated</td> 
      <td>CMYK</td> 
      <td>Euroscale Uncoated v2</td> 
      </tr> 
      <tr> 
      <td>JapanColorCoated</td> 
      <td>CMYK</td> 
      <td>日本颜色2001涂层</td> 
      </tr> 
      <tr> 
      <td>JapanColorJeappe</td> 
      <td>CMYK</td> 
      <td>日本彩色2002报纸</td> 
      </tr> 
      <tr> 
      <td>JapanColorUncoated</td> 
      <td>CMYK</td> 
      <td>日本颜色2001无涂层</td> 
      </tr> 
      <tr> 
      <td>JapanColorWebCoated</td> 
      <td>CMYK</td> 
      <td>日本Color 2003 Web Coated</td> 
      </tr> 
      <tr> 
      <td>JapanWebCoated</td> 
      <td>CMYK</td> 
      <td>Japan Web Coated（广告）</td> 
      </tr> 
      <tr> 
      <td>新闻纸SNAP2007</td> 
      <td>CMYK</td> 
      <td>美国新闻纸（2007年快照）</td> 
      </tr> 
      <tr> 
      <td>NTSC</td> 
      <td>RGB</td> 
      <td>NTSC（1953年）</td> 
      </tr> 
      <tr> 
      <td>PAL</td> 
      <td>RGB</td> 
      <td>PAL/SECAM</td> 
      </tr> 
      <tr> 
      <td>ProPhoto</td> 
      <td>RGB</td> 
      <td>ProPhoto RGB</td> 
      </tr> 
      <tr> 
      <td>PS4Default</td> 
      <td>CMYK</td> 
      <td>Photoshop 4默认CMYK</td> 
      </tr> 
      <tr> 
      <td>PS5默认</td> 
      <td>CMYK</td> 
      <td>Photoshop 5默认CMYK</td> 
      </tr> 
      <tr> 
      <td>SheetfedCoated</td> 
      <td>CMYK</td> 
      <td>美国钣金涂层v2</td> 
      </tr> 
      <tr> 
      <td>SheetfedUncoated</td> 
      <td>CMYK</td> 
      <td>美国平板纸未涂层v2</td> 
      </tr> 
      <tr> 
      <td>SMPTE</td> 
      <td>RGB</td> 
      <td>SMPTE-C</td> 
      </tr> 
      <tr> 
      <td>sRGB</td> 
      <td>RGB</td> 
      <td>sRGB IEC61966-2.1</td> 
      </tr> 
      <tr> 
      <td>UncoatedFogra29</td> 
      <td>CMYK</td> 
      <td>无涂层FOGRA29(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCoated</td> 
      <td>CMYK</td> 
      <td>美国涂层网络(SWOP)v2</td> 
      </tr> 
      <tr> 
      <td>WebCoatedFogra28</td> 
      <td>CMYK</td> 
      <td>Web Coated FOGRA28(ISO 12647-2:2004)</td> 
      </tr> 
      <tr> 
      <td>WebCoatedGrade3</td> 
      <td>CMYK</td> 
      <td>Web版SWOP 2006三级纸</td> 
      </tr> 
      <tr> 
      <td>WebCoatedGrade5</td> 
      <td>CMYK</td> 
      <td>Web版SWOP 2006五级纸</td> 
      </tr> 
      <tr> 
      <td>WebUncoated</td> 
      <td>CMYK</td> 
      <td>美国Web Uncoated v2</td> 
      </tr> 
      <tr> 
      <td>宽色域RGB</td> 
      <td>RGB</td> 
      <td>宽色域RGB</td> 
      </tr> 
    </tbody> 
    </table>

1. 点按&#x200B;**[!UICONTROL 保存全部]**。

例如，您可以将&#x200B;**[!UICONTROL iccprofilergb]**&#x200B;设置为`sRGB`，将&#x200B;**[!UICONTROL iccprofilecmyk]**&#x200B;设置为`WebCoated`。 这样做可以执行以下操作：

* 为RGB和CMYK图像启用颜色校正。
* 假定没有颜色配置文件的RGB图像位于`sRGB`颜色空间中。
* 假定没有颜色配置文件的CMYK图像位于`WebCoated`色彩空间中。
* 返回RGB输出的动态呈现，以`sRGB`颜色空间返回。
* 返回CMYK输出的动态呈现，以`WebCoated`色彩空间返回。

## 传送资产 {#delivering-assets}

完成上述所有任务后，图像或视频服务中会提供已激活的Dynamic Media资产。 在AEM中，此功能显示在&#x200B;**[!UICONTROL 复制图像URL]**、**[!UICONTROL 复制查看器URL]**、**[!UICONTROL 嵌入查看器代码]**&#x200B;和WCM中。

请参阅[传送Dynamic Media资产](delivering-dynamic-media-assets.md)。

<table> 
 <tbody> 
  <tr> 
   <td><strong>当你……</strong></td> 
   <td><strong>结果</strong></td> 
  </tr> 
  <tr> 
   <td>复制图像URL</td> 
   <td><p>“复制URL”对话框显示一个与以下类似的URL（URL仅用于演示目的）：</p> <p><code>https://IMAGESERVICEPUBLISHNODE/is/image/content/dam/path/to/Image.jpg?$preset$</code></p> <p>其中<code>IMAGESERVICEPUBLISHNODE</code>是指图像服务URL。</p> <p>另请参阅<a href="/help/assets/delivering-dynamic-media-assets.md">传送Dynamic Media资产</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>复制查看器URL</td> 
   <td><p>“复制URL”对话框显示一个与以下内容类似的URL（URL仅用于演示目的）：</p> <p><code>https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/BasicZoomViewer.html?asset=/content/dam/path/to/Image.jpg&amp;config=/conf/global/settings/dam/dm/presets/viewer/Zoom_dark&amp;serverUrl=https://IMAGESERVICEPUBLISHNODE/is/image/&amp;contentRoot=%2F</code></p> <p>其中， <code>PUBLISHNODE</code>是常规的AEM发布节点， <code>IMAGESERVICEPUBLISHNODE</code>是图像服务URL。</p> <p>另请参阅<a href="/help/assets/delivering-dynamic-media-assets.md">传送Dynamic Media资产</a>。</p> </td> 
  </tr> 
  <tr> 
   <td>复制查看器的嵌入代码</td> 
   <td><p>“复制嵌入代码”对话框显示一个与以下内容类似的代码片段（代码示例仅用于演示目的）：</p> <p><code class="code">&lt;style type="text/css"&gt;
       #s7basiczoom_div.s7basiczoomviewer{
       width:100%;
       height:auto;
       }
       &lt;/style&gt;
       &lt;script
       type="text/javascript" src="https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/js/BasicZoomViewer.js"&gt;&lt;/script&gt;
       &lt;div id="s7basiczoom_div"&gt;&lt;/div&gt;
       &lt;script type="text/javascript"&gt;
       var s7basiczoomviewer = new s7viewers.BasicZoomViewer({
       "containerId" : "s7basiczoom_div",
       "params" : {
       "serverurl" : "https://IMAGESERVICEPUBLISHNODE/is/image/",
       "contenturl" : "https://PUBLISHNODE/",
       "config" : "/conf/global/settings/dam/dm/presets/viewer/Zoom_dark",
       "asset" : "/content/dam/path/to/Image.jpg" }
       }).init();
       &lt;/script&gt;</code></p> <p>其中， <code>PUBLISHNODE</code>是常规的AEM发布节点， <code>IMAGESERVICEPUBLISHNODE</code>是图像服务URL。</p> <p>另请参阅<a href="/help/assets/delivering-dynamic-media-assets.md">传送Dynamic Media资产</a>。</p> </td> 
  </tr> 
 </tbody> 
</table>

### WCM Dynamic Media和交互式媒体组件 {#wcm-dynamic-media-and-interactive-media-components}

引用Dynamic Media和交互式媒体组件的WCM页面引用交付服务。
