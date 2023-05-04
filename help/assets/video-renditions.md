---
title: 视频演绎版
description: 视频演绎版
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 1%

---

# 视频演绎版 {#video-renditions}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets可为各种格式（包括OGG、FLV等）的视频资产生成视频演绎版。

AEM Assets支持媒体资产的静态和动态演绎版（DM编码的演绎版）。

静态演绎版是使用FFMPEG（在系统路径上安装并可用）在本地生成的，并存储在内容存储库中。

DM编码的演绎版存储在代理服务器中，并在运行时提供。

AEM资产在客户端为这些演绎版提供播放支持。

要查看特定视频资产的演绎版，请打开其资产页面，然后点按全局导航图标。 然后，选择 **[!UICONTROL 演绎版]** 列表。

![chlimage_1-478](assets/chlimage_1-478.png)

视频演绎版的列表显示在 **[!UICONTROL 演绎版]** 的上界。

![chlimage_1-479](assets/chlimage_1-479.png)

要为DM编码的演绎版配置代理服务器，请执行以下操作： [配置Dynamic Media云服务。](config-dynamic.md)

要使用所需的参数生成视频演绎版，请执行以下操作： [创建相应的视频配置文件](video-profiles.md).

配置代理服务器并创建视频配置文件后，您可以将此视频预设包含在处理配置文件中，并将处理配置文件应用到文件夹。

>[!NOTE]
>
>Internet Explorer 11上的OGG和WAV文件无法播放音频。 对于扩展名为OGG或WAV的资产，资产详细信息页面上会显示错误“源无效”。
>
>在MS Edge和iPad上，OGG文件不会播放，并引发“不支持的格式”错误。
