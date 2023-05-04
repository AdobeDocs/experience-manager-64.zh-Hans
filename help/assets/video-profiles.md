---
title: Dynamic Media视频配置文件
description: Dynamic Media附带预定义的自适应视频编码配置文件。 此开箱即用配置文件中的设置经过优化，可为客户提供最佳的视频观看体验。
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
exl-id: 3602e1b9-624d-408f-a7f6-1598b62dbd22
feature: Video Profiles,Video
role: Admin,User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3104'
ht-degree: 17%

---

# Dynamic Media视频配置文件 {#video-profiles}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Dynamic Media已附带预定义的自适应视频编码配置文件。 此现成配置文件中的设置经过优化，可为客户提供最佳的查看体验。 当您使用自适应视频编码配置文件对主控视频进行编码时，在播放视频时，视频播放器会根据客户的Internet连接速度自动调整视频流的质量。 这称为自适应流播放。

以下是决定视频质量的其他因素：

* **上传主控视频的分辨率**

   如果MP4视频以较低的分辨率（如240p或360p）进行录制，则无法以高清晰度对其进行流式处理。

* **视频播放器大小**

   默认情况下， **[!UICONTROL 宽度]** 在“自适应视频编码”配置文件中，设置为 **[!UICONTROL 自动]**. 同样，在播放期间，会根据播放器的大小使用最佳质量。

另请参阅 [视频编码最佳实践](video.md#best-practices-for-encoding-videos).

>[!NOTE]
>
>要生成视频的元数据和关联的视频图像缩略图，视频本身需要在 Dynamic Media 中完成编码过程。在 AEM 中，如果您已启用 Dynamic Media 并设置了视频云服务，则 **[!UICONTROL Dynamic Media 编码视频]**&#x200B;工作流会对视频进行编码。此工作流会捕获工作流进程历史记录和失败信息。
>
>请参阅[监视视频编码和 YouTube 发布进度](video.md#monitoring-video-encoding-and-youtube-publishing-progress)。如果您已启用Dynamic Media并设置了视频云服务，则 **[!UICONTROL Dynamic Media编码视频]** 在您上传视频时，工作流会自动生效。 （如果您未使用 Dynamic Media，则 **[!UICONTROL DAM 更新资产]**&#x200B;工作流将生效。）
>
>在搜索资产时，元数据非常有用。 缩略图是在编码过程中生成的静态视频图像。 AEM系统需要这些参数，并在用户界面中使用，以帮助您在 **[!UICONTROL 卡片视图]**, **[!UICONTROL 搜索结果]** 视图和 **[!UICONTROL 资产列表]** 中。 您可以在点按 **[!UICONTROL 演绎版]** 图标（编码视频的画板）。

创建完视频配置文件后，可将其应用到一个或多个文件夹。 请参阅 [将视频配置文件应用到文件夹。](#applying-a-video-profile-to-folders)

要为其他资产类型定义高级处理参数，请参阅 [配置资产处理](config-dms7.md#configuring-asset-processing).

## 自适应视频编码预设 {#adaptive-video-encoding-presets}

下表列出了适用于移动和平板电脑设备以及台式计算机的自适应视频流播放的最佳实践编码配置文件。 您可以将这些预设用于任何宽高比视频。

<table> 
 <tbody> 
  <tr> 
   <td><strong>视频格式编解码器</strong></td> 
   <td><strong>视频大小 — 宽度(px)</strong></td> 
   <td><strong>视频大小 — 高度(px)</strong></td> 
   <td><strong>保持宽高比？</strong></td> 
   <td><strong>视频比特率(Kbps)</strong></td> 
   <td><strong>视频帧速率(Fps)</strong></td> 
   <td><strong>音频编解码器</strong></td> 
   <td><strong>音频比特率(Kbps)</strong></td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264(mp4)</p> </td> 
   <td>auto</td> 
   <td>360</td> 
   <td>是</td> 
   <td>730</td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264(mp4)</p> </td> 
   <td>auto</td> 
   <td>540</td> 
   <td>是</td> 
   <td>2000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264(mp4)</p> </td> 
   <td>auto</td> 
   <td>720<br /> </td> 
   <td>是</td> 
   <td>3000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
 </tbody> 
</table>

## 为自适应流播放创建Dynamic Media视频编码配置文件 {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamic Media已附带预定义的自适应视频编码配置文件，该配置文件是一组适用于MP4 H.264的视频上传设置，已针对最佳观看体验进行了优化。 您可以在上传视频时使用此用户档案。

但是，如果此预定义配置文件不符合您的需求，您可以选择创建您自己的自适应视频编码配置文件。 使用设置时 **[!UICONTROL 自适应流播放的编码]**-*最佳实践* — 系统将验证您添加到配置文件的所有编码预设，以确保所有视频具有相同的宽高比。 此外，编码视频会被视为流播放的多比特率集。

在创建视频编码配置文件时，您会注意到大多数编码选项都已预填充推荐的默认设置，以帮助您。 但是，如果您选择的值不是建议的默认值，请注意，该值可能会在播放过程中导致视频质量不佳以及出现其他性能问题。

因此，对于配置文件中的所有MP4 H.264视频编码预设，将验证以下值，以确保它们在配置文件中的各个编码预设中均相同，从而实现自适应流播放：

* 视频格式编解码器 — MP4 H.264(.mp4)
* 音频编解码器
* 音频比特率
* 保持宽高比
* 两遍编码
* 恒定比特率
* H264 配置文件
* 音频采样速率

如果值不相同，您可以继续按原样创建用户档案。 但是，请注意，自适应流播放将不可能。 用户将会体验单比特率流播放。 建议您编辑编码设置，以便在配置文件中的各个编码预设中使用相同的值。 (请注意，如果 **[!UICONTROL 自适应流播放的编码]** 启用。)

另请参阅 [为渐进式流播放创建视频编码配置文件](#creating-a-video-encoding-profile-for-progressive-streaming).

另请参阅 [视频编码最佳实践](video.md#best-practices-for-encoding-videos).

要为其他资产类型定义高级处理参数，请参阅 [配置资产处理](config-dms7.md#configuring-asset-processing).

创建完视频配置文件后，可将其应用到一个或多个文件夹。

**为自适应流播放创建Dynamic Media视频编码配置文件**:

1. 点按或单击AEM徽标，然后导航到 **[!UICONTROL 工具> Assets >视频配置文件]**.
1. 点按 **[!UICONTROL 创建]** 添加新视频配置文件。

1. 输入配置文件的名称和描述。
1. 确保 **[!UICONTROL 自适应流播放的编码]** 选中（默认）。
1. 点按 **[!UICONTROL 添加视频编码预设]**.
1. 在 **[!UICONTROL 基本]** ，请设置视频和音频选项。

   点按每个选项旁边的信息图标，以了解基于所选视频格式编解码器的其他说明或推荐的设置。

1. 在“视频大小”标题下，确保 **[!UICONTROL 保持宽高比]** 复选框。
1. 以像素为单位设置视频帧大小分辨率。 使用 **[!UICONTROL 自动]** 值以自动缩放以匹配源宽高比（宽高比）。 例如，自动x 480或640 x自动。

   执行下列操作之一：

   * 在 **[!UICONTROL 宽度]** 字段，输入 **[!UICONTROL 自动]**. 在 **[!UICONTROL 高度]** 字段中，输入以像素为单位的值。
   * 要帮助您可视化视频的大小，请点按 **[!UICONTROL 信息]** 图标(i) **[!UICONTROL 高度]** 打开 **[!UICONTROL 大小计算器]** 页面。 使用 **[!UICONTROL 大小计算器]** 来设置所需的视频尺寸（由蓝框表示）。 点按 **[!UICONTROL X]** 的位置。

1. （可选）点按 **[!UICONTROL 高级]** ，并确保 **[!UICONTROL 使用默认值]** 复选框（推荐）。 或者，修改高级视频和音频设置。
1. 在页面的右上角，点按 **[!UICONTROL 保存]** 来保存预设。
1. 执行下列操作之一：

   * 重复步骤5-10以创建其他编码预设。 （自适应视频流播放需要多个视频预设。）
   * 在页面的右上角，点按 **[!UICONTROL 保存]** 以保存用户档案。

## 监控编码作业的进度 {#monitoring-the-progress-of-an-encoding-job}

将显示处理指示器（或进度条），以便您能够直观地监视视频编码作业的进度。

您还可以查看 `error.log` 文件，用于监视编码作业的进度，查看编码是否完成，或查看任何作业错误。 的 `error.log` 在 `logs` 安装AEM实例的文件夹。

## 为渐进式流播放创建Dynamic Media视频编码配置文件 {#creating-a-video-encoding-profile-for-progressive-streaming}

如果选择不使用&#x200B;**[!UICONTROL 自适应流播放的编码]**&#x200B;选项，请注意，您添加到配置文件的所有编码预设都将被视为单比特率流或渐进式视频交付的单个视频呈现形式。此外，不会进行验证，以确保所有视频呈现具有相同的纵横比。

根据您运行的模式，支持的视频格式编解码器如下所示：

* Dynamic Media-Scene7模式：H.264(.mp4)
* Dynamic Media — 混合模式：H.264(.mp4), WebM

另请参阅 [为自适应流播放创建视频编码配置文件](#creating-a-video-encoding-profile-for-adaptive-streaming).

另请参阅 [视频编码最佳实践](video.md#best-practices-for-encoding-videos).

要为其他资产类型定义高级处理参数，请参阅 [配置资产处理](config-dms7.md#configuring-asset-processing).

创建完视频配置文件后，可将其应用到一个或多个文件夹。

**要为渐进式流播放创建Dynamic Media视频编码配置文件，请执行以下操作：**

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 点按 **[!UICONTROL 创建]** 添加新视频配置文件。
1. 输入配置文件的名称和描述。
1. 清除 **[!UICONTROL 自适应流播放的编码]** 复选框。
1. 点按 **[!UICONTROL 添加视频编码预设]**.
1. 在 **[!UICONTROL 基本]** ，请设置视频和音频选项。

   点按 **[!UICONTROL 信息]** 图标，以了解基于所选视频格式编解码器的其他说明或推荐的设置。

1. （可选）在 **视频大小** 标题，取消选中 **[!UICONTROL 保持宽高比]**.
1. 在 **[!UICONTROL 宽度]** 字段，输入 **[!UICONTROL 自动]**;权利 **[!UICONTROL 高度]** 字段，点按 **[!UICONTROL 信息]** 图标。 使用 **[!UICONTROL 大小计算器]** 页面以进一步按需设置视频维度（蓝框）。 点按 **[!UICONTROL X]** 等你完成。
1. （可选）执行以下操作之一：

   * 点按 **[!UICONTROL 高级]** ，并确保 **[!UICONTROL 使用默认值]** 复选框（推荐）。
   * 清除 **[!UICONTROL 使用默认值]** 复选框，然后指定所需的视频设置和音频设置。

      点按 **[!UICONTROL 信息]** 图标，以了解基于所选视频格式编解码器的其他说明或推荐的设置。

1. 在页面的右上角，点按 **[!UICONTROL 保存]** 来保存预设。
1. 执行下列操作之一：

   * 重复步骤5-10以创建其他编码预设。
   * 在页面的右上角，点按保 **[!UICONTROL 存]** ，以保存配置文件。

## 使用添加的自定义视频编码参数 {#using-custom-added-video-encoding-parameters}

在AEM中创建或编辑视频配置文件时，您可以编辑现有视频编码配置文件，以利用用户界面中未找到的高级视频编码参数。 自定义添加一个或多个高级参数，例如 **[!UICONTROL minBitrate]** 和 **[!UICONTROL maxBitrate]** — 到现有配置文件。

**使用自定义添加的视频编码参数**:

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。
1. 从 **[!UICONTROL CRXDE Lite]** 页面，在 **[!UICONTROL 资源管理器]** 面板，导航到以下内容：

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. 在页面右下方的面板中，从 **[!UICONTROL 属性]** 选项卡，指定 **[!UICONTROL 名称]**, **[!UICONTROL 类型]**&#x200B;和 **[!UICONTROL 值]** 的子项。

   可以使用以下高级参数：

   <table> 
    <tbody> 
    <tr> 
    <td><strong>名称</strong></td> 
    <td><strong>描述</strong><br /> </td> 
    <td><strong>类型</strong><br /> </td> 
    <td><strong>价值</strong></td> 
    </tr> 
    <tr> 
    <td><code>h264Level</code></td> 
    <td>用于编码的H.264级。 通常，系统会根据您使用的编码设置自动确定此参数。</td> 
    <td><code>String</code></td> 
    <td><p>10 * h264级</p> <p>例如，3.0 = 30,1.3 = 13)</p> <p>没有默认值。</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>关键帧之间的目标帧数。 计算此值以每2-10秒生成一个关键帧。 例如，在每秒30帧时，关键帧间隔应为60-300。<br /> <br /> 较低的关键帧间隔可改进自适应视频编码的流搜寻和流切换行为，并且还可以提高具有大量运动的视频的质量。 但是，由于关键帧会增加文件的大小，因此较低的关键帧间隔通常会导致在给定比特率下的整体视频质量降低。</td> 
    <td><code>String</code></td> 
    <td><p>正数。</p> <p>默认值为300。</p> <p>HLS（HTTP实时流）的推荐值为60-90。</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>允许使用可变比特率编码的最小比特率，以Kbps（千比特每秒）为单位。</p> <p>此参数仅在<strong> 使用常量比特率</strong> 创建或编辑视频编码配置文件时，会在“高级”选项卡中取消选中此选项。</p> <p>另请参阅 <a href="/help/assets/video.md#bitrate">比特率</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>正数，以Kbps为单位。</p> <p>没有默认值。</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>允许使用可变比特率编码的最大比特率，以Kbps为单位。</p> <p>此参数仅在<strong> 使用常量比特率</strong> 创建或编辑视频编码配置文件时，会在“高级”选项卡中取消选中此选项。</p> <p>另请参阅 <a href="/help/assets/video.md#bitrate">比特率</a>.</p> </td> 
    <td><code>String</code></td> 
    <td><p>正数，以Kbps为单位。</p> <p>没有默认值。 但是，建议的值最多是编码比特率的两倍。</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>将值设置为 <code>true</code> 强制音频流使用恒定比特率（如果音频编解码器支持）。</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>默认为 <code>false</code>.</p> <p>HLS（HTTP实时流）的推荐值为 <code>false</code>.</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. 在页面的右下角附近，点按 **[!UICONTROL 添加]**.
1. 执行下列操作之一：

   * 重复步骤3和4，以向视频编码配置文件中添加其他参数。
   * 在页面的左上角附近，点按 **[!UICONTROL 全部保存]**.

1. 在的左上角 **[!UICONTROL CRXDE Lite]** 页面，点按 **[!UICONTROL 返回主页]** 图标以返回AEM。

### 编辑Dynamic Media视频编码配置文件 {#editing-a-video-encoding-profile}

您可以编辑您创建的任何视频编码配置文件，以在该配置文件中添加、编辑或删除视频预设。

默认情况下，您无法编辑预定义的现成功能 **[!UICONTROL 自适应视频编码]** Dynamic Media的个人资料。 相反，您可以轻松复制配置文件并使用新名称进行保存。 然后，您可以在复制的配置文件中编辑所需的预设。

另请参阅 [视频编码最佳实践](video.md#best-practices-for-encoding-videos).

要为其他资产类型定义高级处理参数，请参阅 [配置资产处理](config-dms7.md#configuring-asset-processing).

**编辑Dynamic Media视频编码配置文件**:

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 在 **[!UICONTROL 视频配置文件]** ，请选中一个视频配置文件名称。
1. 在工具栏中，点按 **[!UICONTROL 编辑]**.
1. 在 **[!UICONTROL 视频编码配置文件]** 页面，根据需要编辑名称和描述。
1. 作为最佳实践，请确保选中“自 **[!UICONTROL 适应流播放的编码]** ”复选框。

   点按信息图标以获取自适应流播放的说明。 （如果正在编辑渐进式视频配置文件，请勿选中此复选框。）

1. 在 **[!UICONTROL 视频编码预设]** 标题、添加、编辑或删除构成配置文件的视频编码预设。

   点按 **[!UICONTROL 信息]** 图标 **[!UICONTROL 基本]** 和 **[!UICONTROL 高级]** 选项卡，以了解基于所选视频格式编解码器的其他描述或推荐的设置。

1. 在页面的右上角，点按 **[!UICONTROL 保存]**.

### 复制Dynamic Media视频编码配置文件 {#copying-a-video-encoding-profile}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 在 **[!UICONTROL 视频配置文件]** ，请选中一个视频配置文件名称。
1. 在工具栏中，点按 **[!UICONTROL 复制]**.
1. 在 **[!UICONTROL 视频编码配置文件]** 页面，为配置文件输入新名称。
1. 作为最佳实践，请确保选中“自 **[!UICONTROL 适应流播放的编码]** ”复选框。 点按信息图标以获取自适应流播放的说明。 （如果要复制渐进式视频配置文件，请勿选中此复选框。）

   在Dynamic Media — 混合模式中，如果WebM视频预设是视频配置文件的一部分，则 **[!UICONTROL 自适应流播放的编码]** 不可能，因为所有预设都必须是MP4预设。
1. 在 **[!UICONTROL 视频编码预设]** 标题、添加、编辑或删除构成配置文件的视频编码预设。

   点按 **[!UICONTROL 信息]** 图标 **[!UICONTROL 基本]** 和 **[!UICONTROL 高级]** 选项卡，以查看推荐的设置和描述。

1. 在页面的右上角，点按 **[!UICONTROL 保存]**.

### 删除Dynamic Media视频编码配置文件 {#deleting-a-video-encoding-profile}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 在 **[!UICONTROL 视频配置文件]** ，请选中一个或多个视频配置文件名称。
1. 在工具栏中，点按 **[!UICONTROL 删除]**.
1. 点按 **[!UICONTROL 确定]**.

## 将Dynamic Media视频配置文件应用到文件夹 {#applying-a-video-profile-to-folders}

当您将视频配置文件分配给文件夹后，该文件夹中的所有子文件夹都会自动继承父文件夹的配置文件。 这意味着您只能向文件夹分配一个视频配置文件。 因此，请仔细考虑上传、存储、使用和存档资产所在的文件夹结构。

如果您为文件夹分配了其他视频配置文件，则新配置文件会覆盖之前的配置文件。 以前存在的文件夹资产将保持不变。 新配置文件会应用于稍后添加到文件夹的资产。

在用户界面中，如果文件夹分配了配置文件，则卡片名称中会显示配置文件的名称。

![chlimage_1-517](assets/chlimage_1-517.png)

您可以将视频配置文件应用到特定文件夹或全局应用到所有资产。

### 将视频配置文件应用到特定文件夹 {#applying-video-profiles-to-specific-folders}

您可以从“工具”菜单中将视频配置文件应用到 **[!UICONTROL 文件夹]** ，或者如果您在文件夹中，也可以从“属 **[!UICONTROL 性”]**。 本节将介绍这两种将视频配置文件应用到文件夹的方法。

如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

#### 从“配置文件”用户界面将Dynamic Media视频配置文件应用到文件夹 {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 选择要应用于一个或多个文件夹的视频配置文件。
1. 点按&#x200B;**[!UICONTROL 将配置文件应用到文件夹]**，然后选择一个或多个用于接收新上传资产的文件夹，然后点按&#x200B;**[!UICONTROL 应用]**。如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

#### 从“属性”将Dynamic Media视频配置文件应用到文件夹 {#applying-video-profiles-to-folders-from-properties}

1. 点按AEM徽标，然后导航到 **[!UICONTROL 资产]** 然后，转到要将视频配置文件应用到的文件夹。
1. 在文件夹中，点按复选标记以将其选中，然后点按 **[!UICONTROL 属性]**.
1. 选择 **[!UICONTROL 视频配置文件]** 选项卡，从下拉菜单中选择用户档案，然后点按 **[!UICONTROL 保存并关闭]**. 如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

   ![chlimage_1-518](assets/chlimage_1-518.png)

### 全局应用Dynamic Media视频配置文件 {#applying-a-video-profile-globally}

除了将配置文件应用到文件夹之外，您还可以全局应用一个配置文件，以便任何文件夹中上传到AEM资产的任何内容都会应用选定的配置文件。

**在全局范围内应用Dynamic Media视频配置文件**:

1. 导航到CRXDE Lite到以下节点： `/content/dam/jcr:content`.
1. 添加属性 **[!UICONTROL videoProfile]**: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. 点按 **[!UICONTROL 全部保存]**.

![chlimage_1-519](assets/chlimage_1-519.png)

## 将Dynamic Media视频配置文件从文件夹删除 {#removing-a-video-profile-from-folders}

当您将视频配置文件从文件夹删除后，该文件夹中的所有子文件夹都会自动删除从父文件夹继承的配置文件。 但是，对文件夹中已发生的文件的任何处理均将保持不变。

您可以从“工具”菜单中将视频配置文件从文件夹删除 **** ，如果您在文件夹中，也可以从“文件夹设 **[!UICONTROL 置”中删除]**。 本节将介绍这两种将视频配置文件从文件夹删除的方法。

### 通过Profiles用户界面将Dynamic Media视频配置文件从文件夹删除 {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 选择要从一个或多个文件夹删除的视频配置文件。
1. 点按 **[!UICONTROL 从文件夹删除配置文件]** 然后，选择一个或多个要从中删除配置文件的文件夹，然后点按 **[!UICONTROL 删除]**.

   您可以确认视频配置文件不再应用于文件夹，因为该名称不再显示在文件夹名称的下方。

### 通过属性将Dynamic Media视频配置文件从文件夹删除 {#removing-video-profiles-from-folders-via-properties}

1. 点按AEM徽标，然后导航到 **[!UICONTROL 资产]** 然后转到要将视频配置文件从中删除的文件夹。
1. 在文件夹中，点按复选标记以将其选中，然后点按 **[!UICONTROL 属性]**.
1. 选择 **[!UICONTROL 视频配置文件]** 选项卡，选择 **[!UICONTROL 无]** 从下拉菜单中，点按 **[!UICONTROL 保存并关闭]**. 如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。
