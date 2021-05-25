---
title: 管理视频资产
description: 了解如何上传、预览、注释和发布视频资产。
uuid: 56a8c221-409f-4605-97b1-a054dd2abfab
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: f341fae1-dda3-4917-b6db-ad02fec63702
feature: 资产管理，视频
role: Business Practitioner
exl-id: eb652414-5b10-45af-a8b6-f1de649994c5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 15%

---

# 管理视频资产 {#managing-video-assets}

了解如何在Adobe Experience Manager(AEM)资产中管理和编辑视频资产。 此外，如果您获得使用Dynamic Media的许可，请参阅[Dynamic Media视频文档](video.md)。

## 上传和预览视频资产{#uploading-and-previewing-video-assets}

AEM Assets会为扩展名为MP4的视频资产生成预览。 如果资产的格式不是MP4，请安装FFmpeg包以生成预览。 FFmpeg创建OGG和MP4类型的视频演绎版。 您可以在AEM Assets用户界面中预览这些演绎版。

1. 在数字资产文件夹或子文件夹中，导航到要添加数字资产的位置。
1. 要上传资产，请单击或点按工具栏中的&#x200B;**[!UICONTROL 创建]**，然后选择&#x200B;**[!UICONTROL 文件]**。 或者，直接将其拖放到资产区域。 有关上传操作的详细信息，请参阅[上传资产](managing-assets-touch-ui.md#uploading-assets)。
1. 要在卡片视图中预览视频，请点按视频资产上的&#x200B;**[!UICONTROL 播放]**&#x200B;按钮。

   ![chlimage_1-201](assets/chlimage_1-201.png)

   您只能在&#x200B;**[!UICONTROL 卡片]**&#x200B;视图中暂停或播放视频。 “播放/暂停”按钮在&#x200B;**[!UICONTROL 列表]**&#x200B;视图中不可用。

1. 点按卡上的&#x200B;**[!UICONTROL 编辑]**&#x200B;图标，以在&#x200B;**[!UICONTROL 详细信息]**&#x200B;视图中预览视频。

   视频会在浏览器自带的视频播放器中播放。您可以播放视频，暂停视频，控制视频音量，以及将视频放大到全屏。

   ![chlimage_1-202](assets/chlimage_1-202.png)

## 上传大于2 GB的资产的配置{#configuration-to-upload-video-assets-that-are-larger-than-gb}

默认情况下，由于文件大小限制，AEM Assets不允许您上传任何大于2 GB的资产。 但是，您可以进入CRXDE Lite并在`/apps`目录下创建一个节点，以覆盖此限制。 节点必须具有相同的节点名称、目录结构和类似的节点顺序属性。

除了AEM Assets配置之外，还要更改以下配置以上传大型资产：

* 增加令牌过期时间。 请参阅`https://[aem_server]:[port]/system/console/configMgr`的Web控制台中的[!UICONTROL AdobeGranite CSRF Servlet]。 有关更多信息，请参阅[CSRF保护](/help/sites-developing/csrf-protection.md)。
* 在Dispatcher配置中增加`receiveTimeout`。 有关更多信息，请参阅[Experience ManagerDispatcher配置](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#renders-options)。

>[!NOTE]
>
>AEM Classic用户界面没有2 GB的文件大小限制。 此外，大型视频的端对端工作流不完全支持。

要配置更高的文件大小限制，请在`/apps`目录中执行以下步骤。

1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。
1. 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;页面的左侧目录窗口中，导航到`/libs/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`。 要查看目录窗口，请触摸`>>`图标。
1. 在工具栏中，点按&#x200B;**[!UICONTROL 覆盖节点]**。 或者，从上下文菜单中选择&#x200B;**[!UICONTROL 覆盖节点]**。
1. 在&#x200B;**[!UICONTROL 覆盖节点]**&#x200B;对话框中，点按&#x200B;**[!UICONTROL 确定]**。

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. 刷新浏览器。 选择覆盖节点`/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`。
1. 在&#x200B;**[!UICONTROL 属性]**&#x200B;选项卡中，输入相应的字节值，以将大小限制增加到所需的大小。 例如，输入`32212254720`值，将大小限制增加到30 GB。

1. 在工具栏中，点按&#x200B;**[!UICONTROL 全部保存]**。
1. 在 AEM 中，点按&#x200B;**[!UICONTROL 工具 > 操作 > Web Console]**。
1. 在&#x200B;**[!UICONTROL Adobe Experience Manager Web控制台包]**&#x200B;页面的表的&#x200B;**[!UICONTROL 名称]**&#x200B;列下，找到并点按&#x200B;**[!UICONTROL AdobeGranite工作流外部进程作业处理程序]**。
1. 在&#x200B;**[!UICONTROL AdobeGranite工作流外部进程作业处理程序]**&#x200B;页面中，将&#x200B;**[!UICONTROL 默认超时]**&#x200B;和&#x200B;**[!UICONTROL 最大超时]**&#x200B;字段的秒数设置为`18000`（5小时）。
1. 点按&#x200B;**[!UICONTROL 保存]**。
1. 在AEM中，点按&#x200B;**[!UICONTROL 工具>工作流>模型]**。
1. 在&#x200B;**[!UICONTROL 工作流模型]**&#x200B;页面上，选择&#x200B;**[!UICONTROL Dynamic Media编码视频]**，然后点按&#x200B;**[!UICONTROL 编辑]**。
1. 在&#x200B;**[!UICONTROL Workflow]**&#x200B;页面上，双击&#x200B;**[!UICONTROL Dynamic Media视频服务进程]**&#x200B;组件。
1. 在&#x200B;**[!UICONTROL 步骤属性]**&#x200B;对话框的&#x200B;**[!UICONTROL 常用]**&#x200B;选项卡下，展开&#x200B;**[!UICONTROL 高级设置]**。
1. 在&#x200B;**[!UICONTROL 超时]**&#x200B;字段中，指定值 `18000`，然后点按&#x200B;**[!UICONTROL 确定]**，以返回到 **[!UICONTROL Dynamic Media 编码视频]**&#x200B;工作流页面。
1. 在页面顶部附近的&#x200B;**[!UICONTROL Dynamic Media编码视频]**&#x200B;页面标题下，点按&#x200B;**[!UICONTROL Save]**。

## 发布视频资产{#publishing-video-assets}

发布视频资产后，您便可以通过URL或嵌入到网页中的方式，将这些资产包含在网页中。 请参阅[发布资产](publishing-dynamicmedia-assets.md)。

## 在视频资产中添加批注{#annotating-video-assets}

1. 在资产控制台中，点按资产卡片上的&#x200B;**[!UICONTROL 编辑]**&#x200B;图标，以显示资产详细信息页面。
1. 点按&#x200B;**[!UICONTROL 预览]**&#x200B;图标以播放视频。
1. 要对视频添加注释，请点按&#x200B;**[!UICONTROL 注释]**&#x200B;按钮。 注释会添加到视频中的特定时间点（帧）。

   在添加注释时，您可以在画布上绘制图形，并在绘图中包含注释。评论会自动保存在Adobe Experience Manager Assets中。

   ![chlimage_1-204](assets/chlimage_1-204.png)

   要退出注释向导，请点按&#x200B;**[!UICONTROL 关闭]**。

1. 要跳转到视频中的特定点，请在文本字段中以秒为单位指定时间，然后单击&#x200B;**[!UICONTROL 跳转]**。 例如，要跳过视频的前 20 秒，请在`20`文本字段中输入 。

   ![chlimage_1-205](assets/chlimage_1-205.png)

1. 单击注释以在时间轴中查看该注释。 点按&#x200B;**[!UICONTROL Delete]**&#x200B;以从时间轴中删除注释。

   ![chlimage_1-206](assets/chlimage_1-206.png)
