---
title: 视频
description: 了解集中式Experience Manager资产管理，您可以在其中上传视频以用于视频资产，并自动编码到Dynamic Media Classic。 您还可以直接从Dynamic Media Assets访问Experience Manager Classic视频。 Dynamic Media Classic视频集成通过自动设备和自动带宽检测功能将优化视频的范围扩展到所有屏幕。
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
exl-id: 081e7db0-95cc-4260-8f08-318cd7d9d5b4
feature: Video
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '1604'
ht-degree: 29%

---

# 视频 {#video}

资产提供了集中式视频资产管理，您可以通过它将视频直接上传到资产，以便自动编码到Dynamic Media Classic。 您还可以直接从资产中访问Dynamic Media Classic视频以进行页面创作。

Dynamic Media Classic视频集成将优化视频的范围扩展到所有屏幕（自动设备和带宽检测）。

**[!UICONTROL Scene7 Video]**&#x200B;组件可自动执行设备和带宽检测，以在台式机、平板电脑和移动设备上播放格式正确且质量正确的视频。

您可以包含自适应视频集，而不是仅包含单个视频资产。 自适应视频集是所有视频演绎版的容器，这些视频演绎版需要在多个屏幕之间无缝播放视频。 “自适应视频集”对以不同比特率和格式编码的同一视频的各个版本进行分组。 例如，400 kbps、800 kbps和1000 kbps。 您可以使用自适应视频集和S7视频组件来跨多种屏幕类型实现自适应视频流。 例如，桌面、iOS、Android、BlackBerry和Windows移动设备。

有关详细信息，请参阅[有关自适应视频集的](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/video-profiles.html#dynamicmedia)Dynamic Media经典文档。

## 关于FFMPEG和Dynamic Media Classic {#about-ffmpeg-and-scene}

默认的视频编码流程以使用基于 FFMPEG 的视频配置文件集成为基础。因此，现成的DAM摄取工作流包含以下两个基于ffmpeg的工作流步骤：

* FFMPEG 缩略图
* FFMPEG 编码

启用和配置Dynamic Media经典集成不会自动从现成的DAM摄取工作流中删除或取消激活这两个工作流步骤。 如果您已经在Experience Manager中使用基于FFMPEG的视频编码，则您的创作环境可能已安装FFMPEG。 在这种情况下，使用DAM摄取的新视频将进行两次编码：一次来自FFMPEG编码器，另一次来自Dynamic Media Classic集成。

如果已在AEM和FFMPEG中配置基于FFMPEG的视频编码，则可以从DAM摄取工作流中删除两个FFMPEG工作流。

## 支持的格式 {#supported-formats}

Scene7 视频组件支持以下格式：

* F4V H.264
* MP4 H.264

## 确定要将视频上传到的位置  {#deciding-where-to-upload-your-video}

确定要将视频资产上传到的位置取决于以下因素：

* 您是否需要对视频资产使用工作流？
* 您是否需要对视频资产进行版本控制？

如果上述任一问题的答案为“是”或两个问题的答案都为“是”，请将您的视频直接上传到 Adobe DAM。如果两个问题的答案都是“否”，则直接将视频上传到Dynamic Media Classic。 以下各节将介绍每个方案的工作流。

### 如果要将视频直接上传到Adobe DAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

如果您需要资产的工作流或版本控制，请先上传到Adobe DAM。 下面是建议的工作流：

1. 将视频资产上传到Adobe DAM，并自动编码和发布到Dynamic Media Classic。
1. 在Experience Manager中，访问内容查找器&#x200B;**[!UICONTROL 电影]**&#x200B;选项卡中WCM中的视频资产。
1. 使用&#x200B;**[!UICONTROL Scene7 Video]**&#x200B;或&#x200B;**[!UICONTROL Foundation Video]**&#x200B;组件进行创作。

### 如果您要将视频上传到 Scene7 {#if-you-are-uploading-your-video-to-scene}

如果您不需要资产的工作流或版本控制，请将资产上传到Scene7。 下面是建议的工作流：

1. 在Dynamic Media Classic中，[设置到Scene7（系统自动）](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#preparing-your-assets-and-folders-for-uploading)的计划FTP上传和编码。
1. 在Experience Manager中，访问内容查找器&#x200B;**[!UICONTROL Scene7]**&#x200B;选项卡中WCM中的视频资产。
1. 使用&#x200B;**[!UICONTROL Scene7 Video]**&#x200B;组件进行创作。

## 配置与 Scene7 视频的集成 {#configuring-integration-with-scene-video}

要配置通用预设，请执行以下操作：

1. 在&#x200B;**[!UICONTROL 云服务]**&#x200B;中，导航到 **[!UICONTROL Scene7]** 配置，然后单击&#x200B;**[!UICONTROL 编辑]**。
1. 选择&#x200B;**[!UICONTROL 视频]**&#x200B;选项卡。

   ![chlimage_1-363](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >如果页面中没有云配置，则不会显示&#x200B;**[!UICONTROL 视频]**&#x200B;选项卡。

1. 选择自适应视频编码配置文件、现成的单个视频编码配置文件，或自定义视频编码配置文件。

   >[!NOTE]
   >
   >有关视频预设含义的详细信息，请参阅[Dynamic Media Classic文档](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files)。
   >
   >Adobe 建议您在配置通用预设时选择两个自适应视频集，或选择&#x200B;**[!UICONTROL 自适应视频编码]**&#x200B;选项。

1. 选定的编码配置文件会自动应用于上传到您为此 Scene7 云配置设置的 CQ DAM 目标文件夹的所有视频。您可以根据需要设置多个具有不同目标文件夹的 Scene7 云配置，以便应用不同的编码配置文件。

## 更新查看器和编码预设  {#updating-viewer-and-encoding-presets}

如果在Scene7中更新了Experience Manager中的视频预设，则必须更新查看器预设和编码预设。 在这种情况下，请导航到云配置中的Scene7配置，然后单击&#x200B;**[!UICONTROL 更新查看器和编码预设]**。

![chlimage_1-364](assets/chlimage_1-364.png)

## 将主控视频从Adobe DAM {#uploading-your-master-video}上传到Scene7

1. 导航到在其中为云配置设置了 Scene7 编码配置文件的 CQ DAM 目标文件夹。
1. 单击&#x200B;**[!UICONTROL 上传]**&#x200B;以上传主视频。在DAM更新资产工作流完成且&#x200B;**[!UICONTROL 发布到Scene7]**&#x200B;带有复选标记后，视频上传和编码即已完成。

   >[!NOTE]
   >
   >生成视频缩略图需要一些时间。

   将DAM主控视频拖动到视频组件上可访问&#x200B;*所有* Scene7编码的代理演绎版以进行投放。

## 基础视频组件与 Scene7 视频组件 {#foundation-video-component-versus-scene-video-component}

使用Experience Manager时，您可以访问站点中提供的视频组件和Scene7视频组件。 这些组件不能交换使用。

Scene7 视频组件仅适用于 Scene7 视频。基础组件可处理从Experience Manager（使用ffmpeg）和Scene7视频存储的视频。

下面的矩阵说明何时使用哪个组件：

![chlimage_1-365](assets/chlimage_1-365.png)

>[!NOTE]
>
>开箱即用的S7视频组件使用通用视频用户档案。 但是，您可以在Experience Manager中获得基于HTML5的视频播放器。 只需复制现成HTML5视频播放器的嵌入代码，并将其放入Experience Manager页面。

## Experience Manager视频组件{#aem-video-component}

即使建议使用Scene7视频组件观看Scene7视频，为了完整起见，也要将Scene7视频与基础视频组件结合使用。

### Experience Manager视频与Scene7视频比较{#aem-video-and-scene-video-comparison}

下表提供了Experience Manager Foundation Video组件与Scene7 Video组件之间支持的功能的高级比较：

|  | Experience Manager基础视频 | Scene7 视频 |
|---|---|---|
| 方法 | HTML5 为首选方法。Flash 仅用作不可使用 HTML5 时的回退方法。 | 在大多数台式机上使用 Flash。在移动设备和平板电脑上使用 HTML5。 |
| 交付 | 渐进式 | 自适应流式传输 |
| 跟踪 | 是 | 是 |
| 可扩展性 | 是 | 是（带有[HTML5查看器SDK API文档](https://s7d1.scene7.com/s7sdk/3.10/docs/jsdoc/index.html)） |
| 移动视频 | 是 | 是 |

### 设置  {#setting-up}

#### 创建视频配置文件 {#creating-video-profiles}

各种视频编码是根据您在Scene7云配置中选择的Scene7编码预设创建的。 要使用Foundation Video组件，必须为选定的每个Scene7编码预设创建视频用户档案。 此方法允许视频组件相应地选择DAM演绎版。

>[!NOTE]
>
>必须激活新的视频配置文件以及对其所做的更改，才能进行发布。

1. 在Experience Manager中，点按&#x200B;**[!UICONTROL 工具] > [!UICONTROL 配置控制台]**。
1. 从&#x200B;**[!UICONTROL 配置控制台]**&#x200B;导航到导航树中的&#x200B;**[!UICONTROL 工具> DAM >视频用户档案]**。
1. 创建Scene7视频用户档案。 在&#x200B;**[!UICONTROL 新建……]**&#x200B;下拉列表，选择&#x200B;**[!UICONTROL 创建页面]**，然后选择Scene7视频用户档案模板。 为新的视频配置文件页面指定一个名称，然后单击&#x200B;**[!UICONTROL 创建]**。

   ![chlimage_1-366](assets/chlimage_1-366.png)

1. 编辑新的视频配置文件。首先选择云配置。然后，选择在云配置中选定的相同编码预设。

   ![chlimage_1-367](assets/chlimage_1-367.png)

   | 属性 | 描述 |
   |---|---|
   | Scene7 云配置 | 用于编码预设的云配置。 |
   | Scene7 编码预设 | 要映射此视频用户档案的编码预设。 |
   | HTML5 视频类型 | 通过此属性，可设置HTML5视频源元素的type属性值。 此信息不是由 S7 编码预设提供，但却是使用 HTML5 视频元素正确渲染视频所必需的信息。提供了通用格式列表，但是通用格式可被其他格式覆盖。 |

   对要在视频组件中使用的云配置中选定的所有编码预设重复此步骤。

#### 配置设计{#configuring-design}

**[!UICONTROL 基础视频]**&#x200B;组件必须了解用于构建视频源用户档案的视频列表。 打开视频组件设计对话框，并配置组件设计以使用新的视频用户档案。

>[!NOTE]
>
>如果您在移动页面上使用&#x200B;**[!UICONTROL 基础视频]**&#x200B;组件，请在移动页面的设计中重复这些步骤。

>[!NOTE]
>
>对设计所做的更改需要对设计进行激活，以便在发布时生效。

1. 打开&#x200B;**[!UICONTROL Foundation Video]**&#x200B;组件的设计对话框，并切换到&#x200B;**[!UICONTROL 用户档案]**&#x200B;选项卡。 然后删除现成的用户档案并添加新的S7视频用户档案。 “设计”对话框中的用户档案列表顺序定义渲染时视频源元素的顺序。
1. 对于不支持HTML5的浏览器，视频组件允许您配置Flash回退。 打开“Flash组件设计”对话框，并切换到&#x200B;**[!UICONTROL 视频]**&#x200B;选项卡。 配置Flash Player设置并为Flash Player分配回退用户档案。

#### 核对清单 {#checklist}

1. 创建S7云配置。 确保已设置视频编码预设，且导入程序正在运行。
1. 为云配置中选定的每个视频编码预设创建对应的 S7 视频配置文件。
1. 必须激活视频配置文件。
1. 在页面上配置&#x200B;**[!UICONTROL 基础视频]**&#x200B;组件的设计。
1. 完成对设计的更改后，激活设计。
