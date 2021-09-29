---
title: 视频演绎版
description: 视频演绎版
contentOwner: AG
feature: Video,Renditions
role: User
exl-id: 9fc93034-e83a-42b5-901d-7867b4a850a8
source-git-commit: 1e3cd6ce3138113721183439f7cfb9daed6e0e58
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 5%

---

# 视频演绎版 {#video-renditions}

Adobe Experience Manager Assets可为各种格式（包括OGG、FLV等）的视频资产生成视频演绎版。

AEM Assets 支持媒体资产的静态和动态演绎版（DM 编码的演绎版）。

静态演绎版是使用FFMPEG（在系统路径上安装并可用）在本地生成的，并存储在内容存储库中。

DM编码的演绎版存储在代理服务器中，并在运行时提供。

AEM资产在客户端为这些演绎版提供播放支持。

要查看特定视频资产的演绎版，请打开其资产页面，然后点按全局导航图标。 然后，从列表中选择&#x200B;**[!UICONTROL 演绎版]**。

![chlimage_1-478](assets/chlimage_1-478.png)

视频演绎版列表显示在&#x200B;**[!UICONTROL 演绎版]**&#x200B;面板中。

![chlimage_1-479](assets/chlimage_1-479.png)

要为DM编码的呈现版本配置代理服务器，请[配置Dynamic Media云服务。](config-dynamic.md)

要使用所需的参数生成视频演绎版，请[创建相应的视频配置文件](video-profiles.md)。

配置代理服务器并创建视频配置文件后，您可以将此视频预设包含在处理配置文件中，并将处理配置文件应用到文件夹。

>[!NOTE]
>
>Internet Explorer 11上的OGG和WAV文件无法播放音频。 对于扩展名为OGG或WAV的资产，资产详细信息页面上会显示错误“源无效”。
>
>在MS Edge和iPad上，OGG文件不播放，并引发“不支持”格式错误。
