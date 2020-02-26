---
title: 管理视频资产
description: 了解如何上传、预览、批注和发布视频资产。
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
translation-type: tm+mt
source-git-commit: 9ced187ddc9bb2d12922fcc734b20ef9767d8fbf

---


# 管理视频资产 {#managing-video-assets}

了解如何在Adobe Experience Manager(AEM)资产中管理和编辑视频资产。 此外，如果您获得使用Dynamic Media的许可，请参阅 [Dynamic Media视频文档](video.md)。

## 上传和预览视频资产 {#uploading-and-previewing-video-assets}

AEM资产会为扩展名为MP4的视频资产生成预览。 如果资产的格式不是MP4，请安装FFmpeg包以生成预览。 FFmpeg创建OGG和MP4类型的视频演绎版。 您可以在AEM资产用户界面中预览这些演绎版。

1. 在“数字资产”文件夹或子文件夹中，导航到要添加数字资产的位置。
1. 要上传资产，请单击或点按工 **[!UICONTROL 具栏中]** 的创建，然后选择 **[!UICONTROL 文件]**。 或者，直接将其拖放到资产区域。 See [Uploading assets](managing-assets-touch-ui.md#uploading-assets) for details around the upload operation.
1. To preview a video in the Card view, tap the **[!UICONTROL Play]** button on the video asset.

   ![chlimage_1-201](assets/chlimage_1-201.png)

   You can pause or play video in the **[!UICONTROL Card]** view only. “列表”视图中不提供“播放／暂 **[!UICONTROL 停]** ”按钮。

1. 点按卡 **[!UICONTROL 上的]** “编辑”图标以在“详细信息”视图中预 **[!UICONTROL 览视频]** 。

   视频会在浏览器自带的视频播放器中播放。您可以播放视频，暂停视频，控制视频音量，以及将视频放大到全屏。

   ![chlimage_1-202](assets/chlimage_1-202.png)

## 用于上传大于2 GB的资产的配置 {#configuration-to-upload-video-assets-that-are-larger-than-gb}

默认情况下，AEM资产不允许您上传任何大于2 GB的资产，因为文件大小限制。 但是，您可以通过进入CRXDE Lite并在目录下创建一个节点来覆盖此限 `/apps` 制。 该节点必须具有相同的节点名称、目录结构和可比的节点属性。

除AEM资产配置外，还要更改以下配置以上传大型资产：

* 增加令牌到期时间。 请参 [!UICONTROL 阅Web控制台中的] Adobe Granite CSRF Servlet `https://[aem_server]:[port]/system/console/configMgr`，网址为。 有关详细信息，请参 [阅CSRF保护](/help/sites-developing/csrf-protection.md)。
* 增加调 `receiveTimeout` 度程序配置。 有关详细信息，请参 [阅Experience Manager Dispatcher配置](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)。

>[!NOTE]
>
>AEM Classic用户界面没有2GB文件大小限制。 此外，大型视频的端对端工作流程不完全受支持。

要配置更高的文件大小限制，请在目录中执行以下 `/apps` 步骤。

1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。
1. 在 **[!UICONTROL CRXDE Lite]** 页面左侧的目录窗口中，导航到 `/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`。 要查看目录窗口，请使用触控 `>>` 图标。
1. From the toolbar, tap **[!UICONTROL Overlay Node]**. 或者，从上下文菜单中选择&#x200B;**[!UICONTROL 覆盖节点]**。
1. 在&#x200B;**[!UICONTROL 覆盖节点]**&#x200B;对话框中，点按&#x200B;**[!UICONTROL 确定]**。

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. 刷新浏览器。 叠加节 `/jcr_root/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload` 点被选中。
1. 在“属 **[!UICONTROL 性]** ”选项卡中，输入相应的字节值，以将大小限制增加到所需大小。 例如，输入以下值以将大小限制增加到30 GB:

   `{sizeLimit : "32212254720"}`

1. 在工具栏中，点按全 **[!UICONTROL 部保存]**。
1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 操作 > Web Console]**。
1. 在 **[!UICONTROL Adobe Experience Manager Web Console捆绑包页面]** ，在表的“名称”列下，找到并点按 **[!UICONTROL Adobe Granite Workflow External Process Job Handler]******。
1. In the **[!UICONTROL Adobe Granite Workflow External Process Job Handler]** page, set the seconds for both **[!UICONTROL Default Timeout]** and **[!UICONTROL Max Timeout]** fields to `18000` (five hours).
1. 点按&#x200B;**[!UICONTROL 保存]**。
1. 在AEM中，点按工 **[!UICONTROL 具>工作流>模型]**。
1. 在“工 **[!UICONTROL 作流模型]** ”页面上，选择“ **[!UICONTROL Dynamic Media编码视频]**”，然后点按 **[!UICONTROL 编辑]**。
1. 在“工 **[!UICONTROL 作流]** ”页面上，双击 **[!UICONTROL Dynamic Media视频服务进程组件]** 。
1. 在&#x200B;**[!UICONTROL 步骤属性]**&#x200B;对话框的&#x200B;**[!UICONTROL 常用]**&#x200B;选项卡下，展开&#x200B;**[!UICONTROL 高级设置]**。
1. 在&#x200B;**[!UICONTROL 超时]**&#x200B;字段中，指定值 `18000`，然后点按&#x200B;**[!UICONTROL 确定]**，以返回到 **[!UICONTROL Dynamic Media 编码视频]**&#x200B;工作流页面。
1. 在页面顶部附近，在Dynamic Media编码视 **[!UICONTROL 频页面标题下]** ，点按 **[!UICONTROL 保存]**。

## 发布视频资产 {#publishing-video-assets}

发布视频资产后，您便可以通过URL或在网页上嵌入这些资产，以将其包含在网页中。 请参阅 [发布资产](publishing-dynamicmedia-assets.md)。

## 注释视频资产 {#annotating-video-assets}

1. 从资产控制台中，点按资 **[!UICONTROL 产卡片上的]** “编辑”图标以显示资产详细信息页面。
1. 点按“ **[!UICONTROL 预览]** ”图标以播放视频。
1. 要对视频添加注释，请点按“ **[!UICONTROL 注释]** ”按钮。 注释会添加到视频中的特定时间点（帧）。

   添加注释时，您可以在画布上绘图并在绘图中加入注释。注释会自动保存在Adobe Experience Manager资产中。

   ![chlimage_1-204](assets/chlimage_1-204.png)

   要退出注释向导，请点按关 **[!UICONTROL 闭]**。

1. To jump to a specific point in the video, specify the time in seconds in the text field and click **[!UICONTROL Jump]**. 例如，要跳过视频的前 秒，请在`20`文本字段中输入 10。

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. 单击注释可在时间轴中查看它。 Tap **[!UICONTROL Delete]** to remove the annotation from the timeline.

   ![chlimage_1-206](assets/chlimage_1-206.png)
