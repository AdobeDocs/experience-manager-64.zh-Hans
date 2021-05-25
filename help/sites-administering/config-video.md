---
title: 配置视频组件
seo-title: 配置视频组件
description: 了解如何配置视频组件。
seo-description: 了解如何配置视频组件。
uuid: f4755a13-08ea-4096-a951-46a590f8d766
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: a1efef3c-0e4b-4a17-bcad-e3cc17adbbf7
exl-id: 46d0765d-fb77-4332-8fbb-5bd2abcd6806
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 7%

---

# 配置视频组件{#configure-the-video-component}

[视频组件](/help/sites-authoring/default-components-foundation.md#video)允许您在页面上放置一个预定义的OOTB（现成）视频元素。

要进行正确转码，管理员必须[安装FFmpeg并单独配置AEM](#install-ffmpeg)。 它们还可以[配置视频配置文件](#configure-video-profiles)以便与 HTML5 元素结合使用。

>[!CAUTION]
>
>如果没有进行广泛的项目级别自定义，此组件将不再能够开箱即用运行。

## 配置视频配置文件{#configure-video-profiles}

您可能需要定义用于HTML5元素的视频配置文件。 这里选择的按顺序使用。 要访问，请使用[设计模式](/help/sites-authoring/default-components-designmode.md)（仅限经典UI），然后选择&#x200B;**[!UICONTROL 配置文件]**&#x200B;选项卡：

![chlimage_1-317](assets/chlimage_1-317.png)

您还可以为[!UICONTROL Playback]、[!UICONTROL Flash]和[!UICONTROL Advanced]配置视频组件和参数的设计。

## 安装FFmpeg并配置AEM {#install-ffmpeg}

视频组件依赖于第三方开源产品FFmpeg来正确转码可从[https://ffmpeg.org/](https://ffmpeg.org/)下载的视频。 安装FFmpeg后，必须将AEM配置为使用特定的音频编解码器和特定的运行时选项。

**要为您的平台安装FFmpeg，请执行以下操作**:

* **在 Windows 中：**

   1. 将编译的二进制文件下载为`ffmpeg.zip`
   1. 解压缩到一个文件夹中.
   1. 将系统环境变量`PATH`设置为`<*your-ffmpeg-locatio*n>\bin`
   1. 重新启动AEM。

* **在 Mac OS X 中：**

   1. 安装Xcode([https://developer.apple.com/technologies/tools/xcode.html](https://developer.apple.com/technologies/tools/xcode.html))
   1. 安装XQuartz/X11。
   1. 安装MacPorts([https://www.macports.org/](https://www.macports.org/))
   1. 在控制台中，运行以下命令并按照说明操作：

      `sudo port install ffmpeg`

      `FFmpeg` 必须位 `PATH` 于中，以便AEM可以通过命令行选取它。

* **将预编译的版本用于 OS X 10.6：**

   1. 下载预编译版本。
   1. 将其解压到`/usr/local`目录。
   1. 从终端执行：

      `sudo ln -s /usr/local/Cellar/ffmpeg/0.6/bin/ffmpeg /usr/bin/ffmpeg`

**要配置AEM**，请执行以下操作：

1. 在Web浏览器中打开[!UICONTROL CRXDE Lite]。 ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))
1. 选择`/libs/settings/dam/video/format_aac/jcr:content`节点，并确保节点属性如下所示：

   * audioCodec：

      ```
       aac
      ```

   * customArgs：

      ```
       -flags +loop -me_method umh -g 250 -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -bf 16 -b_strategy 1 -i_qfactor 0.71 -cmp chroma -subq 8 -me_range 16 -coder 1 -sc_threshold 40 -b-pyramid normal -wpredp 2 -mixed-refs 1 -8x8dct 1 -fast-pskip 1 -keyint_min 25 -refs 4 -trellis 1 -direct-pred 3 -partitions i8x8,i4x4,p8x8,b8x8
      ```

1. 要自定义配置，请在`/apps/settings/`节点中创建一个叠加，并在`/conf/global/settings/`节点下移动相同的结构。 无法在`/libs`节点中编辑。 例如，要叠加路径`/libs/settings/dam/video/fullhd-bp`，请在`/conf/global/settings/dam/video/fullhd-bp`处创建路径。

   >[!NOTE]
   >
   >叠加并编辑整个配置文件节点，而不仅仅是需要修改的属性。 此类资源不会通过SlingResourceMebarer进行解析。

1. 如果更改了其中任一属性，请单击&#x200B;**[!UICONTROL Save All]**。

>[!NOTE]
>
>升级AEM实例时，OOTB工作流模型不会保留。 Adobe建议您先复制OOTB工作流模型，然后再对其进行编辑。 例如，在DAM更新资产模型中编辑FFmpeg转码步骤之前，请复制OOTB DAM更新资产模型，以选取升级前存在的视频配置文件名称。 然后，您可以叠加`/apps`节点，以便AEM检索对OOTB模型的自定义更改。
