---
title: 动态媒体视频用户档案
seo-title: 动态媒体视频用户档案
description: 'Dynamic Media 附带预定义的自适应视频编码配置文件。此现成用户档案中的设置经过优化，可为客户提供最佳的观看体验。 '
seo-description: 'Dynamic Media 附带预定义的自适应视频编码配置文件。此现成用户档案中的设置经过优化，可为客户提供最佳的观看体验。 '
uuid: cfb498f8-44a0-4d94-99b0-fed7c27f575b
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: b893f366-279a-4872-9413-77626d3387ea
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '3100'
ht-degree: 38%

---


# Dynamic Media video profiles {#video-profiles}

Dynamic Media 附带预定义的自适应视频编码配置文件。此现成用户档案中的设置经过优化，可为客户提供最佳的观看体验。 如果您使用自适应视频编码配置文件对主视频进行编码，则在播放视频时，视频播放器会根据客户的 Internet 连接速度，自动调整视频流的质量。这称为自适应流。

以下是决定视频质量的其他因素：

* **已上载主控视频的分辨率**

   如果以较低的分辨率（如240p或360p）录制MP4视频，则无法以高清晰度进行流处理。

* **视频播放器大小**

   By default, the **[!UICONTROL Width]** in the Adaptive Video Encoding profile is set to **[!UICONTROL Auto]**. 同样，在播放时，会根据播放器的大小采用最佳质量。

另请参阅[视频编码的最佳实践](video.md#best-practices-for-encoding-videos)。

>[!NOTE]
>
>要生成视频的元数据和关联的视频图像缩略图，视频本身需要在 Dynamic Media 中完成编码过程。在 AEM 中，如果您已启用 Dynamic Media 并设置了视频云服务，则 **[!UICONTROL Dynamic Media 编码视频]**&#x200B;工作流会对视频进行编码。此工作流会捕获工作流进程历史记录和失败信息。
>
>请参阅[监视视频编码和 YouTube 发布进度](video.md#monitoring-video-encoding-and-youtube-publishing-progress)。If you have enabled Dynamic Media and set up video cloud services, the **[!UICONTROL Dynamic Media Encode Video]** workflow automatically takes effect when you upload a video. （如果您未使用 Dynamic Media，则 **[!UICONTROL DAM 更新资产]**&#x200B;工作流将生效。）
>
>在搜索资产时，元数据很有用。 缩略图是编码过程中生成的静态视频图像。 They are required by the AEM system and used in the user interface to help you visually identify videos in the **[!UICONTROL Cards View]**, **[!UICONTROL Search Results]** view, and the **[!UICONTROL Asset List]** view. You can see the generated thumbnails when you tap the **[!UICONTROL Renditions]** icon (a painter&#39;s palette) of an encoded video.

创建完视频用户档案后，可将其应用到一个或多个文件夹。 See [Applying a video profile to folders.](#applying-a-video-profile-to-folders)

要为其他资产类型定义高级处理参数，请参 [阅配置资产处理](config-dms7.md#configuring-asset-processing)。

## 自适应视频编码预设 {#adaptive-video-encoding-presets}

下表显示了可作为最佳实践的编码配置文件，这些配置文件适用于移动和平板电脑设备及台式计算机上的自适应视频流播放。您可以针对任何宽高比的视频使用这些预设。

<table> 
 <tbody> 
  <tr> 
   <td><strong>视频格式编解码器</strong></td> 
   <td><strong>视频大小——宽度（像素）</strong></td> 
   <td><strong>视频大小——高度（像素）</strong></td> 
   <td><strong>保持宽高比？</strong></td> 
   <td><strong>视频比特率 (Kbps)</strong></td> 
   <td><strong>视频帧速率 (Fps)</strong></td> 
   <td><strong>音频编解码器</strong></td> 
   <td><strong>音频比特率(Kbps)</strong></td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>360</td> 
   <td>是</td> 
   <td>730</td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
   <td>auto</td> 
   <td>540</td> 
   <td>是</td> 
   <td>2000<br /> </td> 
   <td>30</td> 
   <td>Dolby HE-AAC</td> 
   <td>128</td> 
  </tr> 
  <tr> 
   <td><p>MP4 H.264 (mp4)</p> </td> 
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

## Creating a Dynamic Media video encoding profile for adaptive streaming {#creating-a-video-encoding-profile-for-adaptive-streaming}

Dynamic Media已附带预定义的自适应视频编码用户档案-一组针对MP4 H.264的视频上传设置，该设置为获得最佳观看体验而优化。 您可以在上传视频时使用此用户档案。

但是，如果该预定义的配置文件不符合您的需求，您也可以选择自行创建自适应视频编码配置文件。When you use the setting **[!UICONTROL Encode for adaptive streaming]**–*a best practice*– all encoding presets that you add to the profile are validated to ensure that all videos have the same aspect ratio. 此外，编码的视频会被视为流播放的多比特率集。

在创建视频编码配置文件时，您会注意到大部分编码选项均已预填充建议的默认设置，以便于您操作。但是请注意，如果您不使用建议的默认值，而选择其他值，这可能会导致在播放视频时视频质量较差，以及出现其他性能问题。

因此，对于用户档案中的所有MP4 H.264视频编码预设，将验证以下值，以确保用户档案中各个编码预设中的这些值相同，从而实现自适应流播放：

* 视频格式编解码器 - MP4 H.264 (.mp4)
* 音频编解码器
* 音频比特率
* 保持宽高比
* 两次编码
* 恒定比特率
* H264 配置文件
* 音频采样速率

如果这些值不相同，您仍然可以继续创建该配置文件。但是请注意，在这种情况下，将无法实现自适应流播放。用户所体验的而是单一比特率流播放。建议您编辑编码设置，以在配置文件内的各个编码预设中均使用相同的值。(请注意，如果启用了自适应流播放的编码，视频用户档案/预设编辑器应强 **[!UICONTROL 制使用自适应视频编码]** 设置的奇偶校验。)

另请参阅[为渐进式流播放创建视频编码配置文件](#creating-a-video-encoding-profile-for-progressive-streaming)。

另请参阅[视频编码的最佳实践](video.md#best-practices-for-encoding-videos)。

要为其他资产类型定义高级处理参数，请参 [阅配置资产处理](config-dms7.md#configuring-asset-processing)。

创建完视频用户档案后，可将其应用到一个或多个文件夹。

**要为自适应流播放创建Dynamic Media视频编码用户档案，请执行以下操作**:

1. Tap or click the AEM logo and navigate to **[!UICONTROL Tools > Assets > Video Profiles]**.
1. 点按 **[!UICONTROL 创建]** ，以添加新视频用户档案。

1. 输入配置文件的名称和描述。
1. 确保选中&#x200B;**[!UICONTROL 自适应流播放的编码]**（默认设置）。
1. 点按&#x200B;**[!UICONTROL 添加视频编码预设]**。
1. 在&#x200B;**[!UICONTROL 基本]**选项卡中，设置视频和音频选项。


   点按每个选项旁边的信息图标，以根据选定的视频格式编解码器获得更多说明或推荐的设置。

1. Under the Video Size heading, ensure that **[!UICONTROL Keep aspect ratio]** is checked.
1. 以像素为单位设置视频帧大小分辨率。 使用“ **[!UICONTROL 自动]** ”值自动缩放以匹配源长宽比（宽高比）。 例如，“自动x 480”或“640 x自动”。

   执行下列操作之一：

   * In the **[!UICONTROL Width]** field, enter **[!UICONTROL auto]**. In the **[!UICONTROL Height]** field, enter a value in pixels.
   * 要帮助您可视化视频的大小，请点 **[!UICONTROL 按]** “高度”右侧的“信息”图标(i) **[!UICONTROL 以打开“大]** 小计算器 **** ”页面。 使 **[!UICONTROL 用大小计]** 算器来设置所需的视频尺寸（由蓝色框表示）。 完成后，点按右上角的 **[!UICONTROL X]**。

1. (Optional) Tap the **[!UICONTROL Advanced]** tab and ensure the **[!UICONTROL Use Default Values]** check box is selected (recommended). 或者，修改高级视频和音频设置。
1. 在该页面的右上角，点按&#x200B;**[!UICONTROL 保存]**&#x200B;以保存预设。
1. 执行下列操作之一：

   * 重复第 5-10 步来创建其他编码预设。（自适应视频流播放需要多个视频预设。）
   * 在该页面的右上角，再次点按&#x200B;**[!UICONTROL 保存]**&#x200B;以保存配置文件。

## 监测编码作业的进度 {#monitoring-the-progress-of-an-encoding-job}

将显示处理指示器（或进度栏），以便您可以以可视方式监视视频编码作业的进度。

您还可以视图文 `error.log` 件以监视编码作业的进度、查看编码是否完成或查看任何作业错误。 在安 `error.log` 装AEM实例 `logs` 的文件夹中找到。

## Creating a Dynamic Media video encoding profile for progressive streaming {#creating-a-video-encoding-profile-for-progressive-streaming}

如果选择不使用自适应流播放的编码选项 ****，请注意，您添加到配置文件的所有编码预设都将被视为单个比特率流播放或渐进式视频交付的单个视频演绎版。 此外，不会进行验证，以确保所有视频呈现具有相同的纵横比。

根据您正在运行的模式，支持的视频格式编解码器如下：

* 动态媒体-Scene7模式： H.264(.mp4)
* 动态媒体——混合模式： H.264(.mp4),WebM

另请参阅[为自适应流播放创建视频编码配置文件](#creating-a-video-encoding-profile-for-adaptive-streaming)。

另请参阅[视频编码的最佳实践](video.md#best-practices-for-encoding-videos)。

要为其他资产类型定义高级处理参数，请参 [阅配置资产处理](config-dms7.md#configuring-asset-processing)。

创建完视频用户档案后，可将其应用到一个或多个文件夹。

**要为渐进式流播放创建Dynamic Media视频编码用户档案，请执行以下操作：**

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 点按 **[!UICONTROL 创建]** ，以添加新视频用户档案。
1. 输入配置文件的名称和描述。
1. Clear the **[!UICONTROL Encode for adaptive streaming]** check box.
1. 点按&#x200B;**[!UICONTROL 添加视频编码预设]**。
1. 在&#x200B;**[!UICONTROL 基本]**选项卡中，设置视频和音频选项。


   Tap the **[!UICONTROL Information]** icon next to each option for additional descriptions or recommended settings based on the selected video format codec.

1. （可选）在“视频大 **小”标题** 下，取消选 **[!UICONTROL 中“保持宽高比”]**。
1. 在“宽 **[!UICONTROL 度]** ”字段中，输 **[!UICONTROL 入auto]**; 在“高度”字 **[!UICONTROL 段的右侧]** ，点按“信 **[!UICONTROL 息]** ”图标。 Use the **[!UICONTROL Size Calculator]** page to further set the video dimension (blue box) how you want. 完成后，点按 **[!UICONTROL X]**。
1. （可选）执行以下操作之一：

   * 点按高 **[!UICONTROL 级]** 选项卡，并确保选中 **[!UICONTROL 使用默认值]** （建议）复选框。
   * Clear the **[!UICONTROL Use Default Values]** check box and specify the video settings and audio settings you want.

      Tap the **[!UICONTROL Information]** icon next to each option for additional descriptions or recommended settings based on the selected video format codec.

1. 在该页面的右上角，点按&#x200B;**[!UICONTROL 保存]**&#x200B;以保存预设。
1. 执行下列操作之一：

   * 重复第 5-10 步来创建其他编码预设。
   * 在页面的右上角，点按保 **[!UICONTROL 存]** ，以保存配置文件。

## 使用自定义添加的视频编码参数 {#using-custom-added-video-encoding-parameters}

您可以编辑现有视频编码用户档案，以利用在AEM中创建或编辑视频用户档案时在用户界面中找不到的高级视频编码参数。 您可以自定义向现有用户档案添 **[!UICONTROL 加一个或多个]** (如 **[!UICONTROL minBitrate]**&#x200B;和maxBitrate)高级参数。

**要使用自定义添加的视频编码参数**:

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > 常规 > CRXDE Lite]**。
1. 从CRXDE Lite **[!UICONTROL 页]** ，在左侧的“ **[!UICONTROL Explorer]** ”（资源管理器）面板中，导航到以下内容：

   `/conf/global/settings/dam/dm/presets/video/*name_of_video_encoding_profile_to_edit*`

1. In the panel on the lower-right side of the page, from the **[!UICONTROL Properties]** tab, specify the **[!UICONTROL Name]**, **[!UICONTROL Type]**, and **[!UICONTROL Value]** of the parameter you want to use.

   可以使用以下高级参数：

   <table> 
    <tbody> 
    <tr> 
    <td><strong>名称</strong></td> 
    <td><strong>描述</strong><br /> </td> 
    <td><strong>类型</strong><br /> </td> 
    <td><strong>值</strong></td> 
    </tr> 
    <tr> 
    <td><code>h264Level</code></td> 
    <td>用于编码的H.264级别。 通常，这会根据您使用的编码设置自动确定。</td> 
    <td><code>String</code></td> 
    <td><p>10 * h264级</p> <p>例如，3.0 = 30, 1.3 = 13)</p> <p>无默认值。</p> </td> 
    </tr> 
    <tr> 
    <td><code>keyframe</code></td> 
    <td>关键帧之间的目标帧数。 计算此值以每2-10秒生成一个关键帧。 例如，在每秒30帧时，关键帧间隔应为60-300。<br /> <br /> 较低的关键帧间隔改善了自适应视频编码的流搜索和流切换行为，还可改善具有大量运动的视频的质量。 但是，由于关键帧增加了文件的大小，因此较低的关键帧间隔通常会导致给定比特率的整体视频质量降低。</td> 
    <td><code>String</code></td> 
    <td><p>正数。</p> <p>默认值为300。</p> <p>HLS（HTTP实时流）的建议值为60-90。</p> </td> 
    </tr> 
    <tr> 
    <td><code>minBitrate</code></td> 
    <td><p>允许可变比特率编码的最小比特率，以Kbps（千比特／秒）为单位。</p> <p>仅当在创建或编辑视频编码用户档案<strong> 时，在</strong> “高级”选项卡中取消选择“使用恒定比特率”时，此参数才适用。</p> <p>另请参阅 <a href="/help/assets/video.md#bitrate">比特率</a>。</p> </td> 
    <td><code>String</code></td> 
    <td><p>正数，以Kbps为单位。</p> <p>无默认值。</p> </td> 
    </tr> 
    <tr> 
    <td><code>maxBitrate</code></td> 
    <td><p>允许可变比特率编码的最大比特率，以Kbps为单位。</p> <p>仅当在创建或编辑视频编码用户档案<strong> 时，在</strong> “高级”选项卡中取消选择“使用恒定比特率”时，此参数才适用。</p> <p>另请参阅 <a href="/help/assets/video.md#bitrate">比特率</a>。</p> </td> 
    <td><code>String</code></td> 
    <td><p>正数，以Kbps为单位。</p> <p>无默认值。 但是，建议的值是编码比特率的两倍。</p> </td> 
    </tr> 
    <tr> 
    <td><code>audioBitrateCustom</code></td> 
    <td>如果音频编 <code>true</code> 解码器支持，请设置值以强制音频流使用恒定比特率。</td> 
    <td><code>String</code></td> 
    <td><p><code>true</code>/<code>false</code></p> <p>Default is <code>false</code>.</p> <p>HLS（HTTP实时流）的建议值为 <code>false</code>。</p> <p> </p> </td> 
    </tr> 
    </tbody> 
   </table>

   ![chlimage_1-516](assets/chlimage_1-516.png)

1. Near the lower-right corner of the page, tap **[!UICONTROL Add]**.
1. 执行下列操作之一：

   * 重复第3步和第4步，向视频编码用户档案添加其他参数。
   * Near the upper-left corner of the page, tap **[!UICONTROL Save All]**.

1. 在CRXDE Lite页面的左上角 **** ，点按 **[!UICONTROL “返回主页]** ”图标以返回AEM。

### 编辑Dynamic Media视频编码用户档案 {#editing-a-video-encoding-profile}

您可以编辑已创建的任何视频编码用户档案，以在该用户档案中添加、编辑或删除视频预设。

By default, you cannot edit the predefined, out-of-the-box **[!UICONTROL Adaptive Video Encoding]** profile that came with Dynamic Media. 相反，您可以轻松复制用户档案并用新名称保存它。 然后，您可以在复制的用户档案中编辑所需的预设。

另请参阅[视频编码的最佳实践](video.md#best-practices-for-encoding-videos)。

要为其他资产类型定义高级处理参数，请参 [阅配置资产处理](config-dms7.md#configuring-asset-processing)。

**要编辑Dynamic Media视频编码用户档案，请执行以下操作**:

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. On the **[!UICONTROL Video Profiles]** page, check one video profile name.
1. 在工具栏中，点按&#x200B;**[!UICONTROL 编辑]**。
1. On the **[!UICONTROL Video Encoding Profile]** page, edit the name and description, as desired.
1. 作为最佳实践，请确保选中“自 **[!UICONTROL 适应流播放的编码]** ”复选框。

   点按信息图标以获取自适应流播放的说明。 (如果您正在编辑渐进式视频用户档案，请勿选中此复选框。)

1. Under the **[!UICONTROL Video Encoding Presets]** heading, add, edit, or delete video encoding presets that make up the profile.

   Tap the **[!UICONTROL Information]** icon next to each option on the **[!UICONTROL Basic]** and **[!UICONTROL Advanced]** tabs for additional descriptions or recommended settings based on the selected video format codec.

1. 在该页面的右上角，点按&#x200B;**[!UICONTROL 保存]**。

### 复制Dynamic Media视频编码用户档案 {#copying-a-video-encoding-profile}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. On the **[!UICONTROL Video Profiles]** page, check one video profile name.
1. On the toolbar, tap **[!UICONTROL Copy]**.
1. 在“视 **[!UICONTROL 频编码用户档案]** ”页面上，输入用户档案的新名称。
1. 作为最佳实践，请确保选中“自 **[!UICONTROL 适应流播放的编码]** ”复选框。 点按信息图标以获取自适应流播放的说明。 （如果要复制渐进式视频配置文件，请勿选中此复选框。）

   在Dynamic Media —— 混合模式中，如果WebM视频预设是视频用户档案的一部分，则无法进 **[!UICONTROL 行自适应流播放的编码]** ，因为所有预设都必须是MP4。
1. Under the **[!UICONTROL Video Encoding Presets]** heading, add, edit, or delete video encoding presets that make up the profile.

   点按基 **[!UICONTROL 本]** 和高级选项卡上各个选项旁 **[!UICONTROL 边的]** “信 **[!UICONTROL 息”图标，]** 查看建议的设置和说明。

1. 在该页面的右上角，点按&#x200B;**[!UICONTROL 保存]**。

### 删除Dynamic Media视频编码用户档案 {#deleting-a-video-encoding-profile}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. On the **[!UICONTROL Video Profiles]** page, check one or more video profile names.
1. 在工具栏中，点按 **[!UICONTROL 删除]**。
1. 点按 **[!UICONTROL 确定]**。

## 将Dynamic Media视频用户档案应用到文件夹 {#applying-a-video-profile-to-folders}

当您将视频配置文件分配给文件夹之后，该文件夹中的所有子文件夹都会自动继承父文件夹的配置文件。这就意味着您只能为每个文件夹分配一个视频配置文件。因此，您在上传、存储、使用资产以及将资产存档的过程中，请妥善安排文件夹结构。

如果您为文件夹分配了一个不同的视频配置文件，新配置文件就会取代之前的配置文件。此前存在的文件夹资产将保持不变。新用户档案将应用于稍后添加到该文件夹的资产。

在用户界面中，卡名称中显示的用户档案名称会指示已为其分配用户档案的文件夹。

![chlimage_1-517](assets/chlimage_1-517.png)

您可以将视频用户档案应用到特定文件夹或全局应用于所有资产。

### 将视频用户档案应用于特定文件夹 {#applying-video-profiles-to-specific-folders}

您可以从“工具”菜单中将视频配置文件应用到 **[!UICONTROL 文件夹]** ，或者如果您在文件夹中，也可以从“属 **[!UICONTROL 性”]**。 本节将介绍这两种将视频配置文件应用到文件夹的方法。

如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

#### Applying Dynamic Media video profiles to folders from Profiles user interface {#applying-video-profiles-to-folders-from-profiles-user-interface}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 选择您要应用到一个或多个文件夹的视频配置文件。
1. 点按&#x200B;**[!UICONTROL 将配置文件应用到文件夹]**，然后选择一个或多个用于接收新上传资产的文件夹，然后点按&#x200B;**[!UICONTROL 应用]**。如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

#### 从属性将Dynamic Media视频用户档案应用到文件夹 {#applying-video-profiles-to-folders-from-properties}

1. 点按AEM徽标，导 **[!UICONTROL 航至]** “资产”，然后导航到要应用视频用户档案的文件夹。
1. 在文件夹中，点按复选标记以将其选中，然后点按 **[!UICONTROL 属性]**。
1. Select the **[!UICONTROL Video Profiles]** tab and select the profile from the drop-down menu and tap **[!UICONTROL Save &amp; Close]**. 如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

   ![chlimage_1-518](assets/chlimage_1-518.png)

### 全局应用Dynamic Media视频用户档案 {#applying-a-video-profile-globally}

除了将用户档案应用到文件夹之外，您还可以全局应用一个用户档案，以便上传到任何文件夹中的AEM资产的任何内容都应用了选定的。

**要全局应用Dynamic Media视频用户档案**:

1. 导航到CRXDE Lite到以下节点： `/content/dam/jcr:content`.
1. 添加属性 **[!UICONTROL videoProfile]**: `/etc/dam/video/dynamicmedia/<name_of_video_encoding_profile>`
1. 点按 **[!UICONTROL 全部保存]**。

![chlimage_1-519](assets/chlimage_1-519.png)

## 从文件夹删除Dynamic Media视频用户档案 {#removing-a-video-profile-from-folders}

当您将视频配置文件从文件夹删除之后，该文件夹中的所有子文件夹都会自动删除从父文件夹继承的配置文件。但是，此前对文件夹中的文件所做的处理均予以保留。

您可以从“工具”菜单中将视频配置文件从文件夹删除 **** ，如果您在文件夹中，也可以从“文件夹设 **[!UICONTROL 置”中删除]**。 本节将介绍这两种将视频配置文件从文件夹删除的方法。

### 通过用户档案用户界面将Dynamic Media视频用户档案从文件夹删除 {#removing-video-profiles-from-folders-via-profiles-user-interface}

1. 点按 AEM 徽标，然后导航到&#x200B;**[!UICONTROL 工具 > Assets > 视频配置文件]**。
1. 选择您要从一个或多个文件夹删除的视频配置文件。
1. Tap **[!UICONTROL Remove Profile from Folder(s)]** and select the folder or multiple folders you want use to remove the profile from and tap **[!UICONTROL Remove]**.

   您可以确认视频用户档案不再应用于文件夹，因为该名称不再显示在文件夹名称的下方。

### 通过属性将Dynamic Media视频用户档案从文件夹删除 {#removing-video-profiles-from-folders-via-properties}

1. 点按AEM徽标，导 **[!UICONTROL 航至]** “资产”，然后导航到要从中删除视频用户档案的文件夹。
1. 在文件夹中，点按复选标记以选择它，然后点按 **[!UICONTROL 属性]**。
1. Select the **[!UICONTROL Video Profiles]** tab and select **[!UICONTROL None]** from the drop-down menu and tap **[!UICONTROL Save &amp; Close]**. 如果文件夹已经分配了配置文件，则文件夹名称正下方会显示配置文件的名称。

