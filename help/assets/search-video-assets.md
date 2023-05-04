---
title: 搜索视频资产
description: 使用关键字、文件属性（如Mime类型、大小或最近修改的时间戳）可快速在 [!DNL Experience Manager] 资产。
contentOwner: AG
feature: Video,Search
role: User
exl-id: d5f0beb2-e59f-47cd-8e83-698d8a1dcec3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 3%

---

# 搜索视频资产 {#searching-video-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

为了节省时间和精力，不必浏览可能数百个视频，请使用关键字、文件属性（如文件类型）或最近修改的时间戳来快速查找您的文件。

如果未看到要查找的文件，则可以单击搜索结果底部的选项之一，以更改搜索的整个范围。 例如，如果您在“文档”库中搜索文件，但找不到该文件，则可以单击“库”以将搜索扩展到其余库。 有关更多信息，请参阅 [查找文件或文件夹](https://windows.microsoft.com/en-us/windows7/find-a-file-or-folder).

您可以根据以下一个或多个属性搜索数字资产：

| 搜索字段 | 搜索属性值 |
|---|---|
| Mime 类型 | [!UICONTROL 图像], [!UICONTROL 文档], [!UICONTROL 多媒体], [!UICONTROL 存档]，或其他。 |
| [!UICONTROL 上次修改时间] | 小时、日、周、月或年。 |
| [!UICONTROL 文件大小] | 小、中或大。 |
| [!UICONTROL 发布] 状态 | 已发布或未发布。 |
| [!UICONTROL 批准] 状态 | 已批准或已拒绝。 |
| [!UICONTROL 方向] | “水平”、“垂直”或“正方形”。 |
| [!UICONTROL Style] | 颜色或黑白。 |
| 视屏高度 | 指定为最小值和最大值。值仅存储在视频演绎版的元数据中。 |
| 视频宽度 | 指定为最小值和最大值。值仅存储在视频演绎版的元数据中。 |
| 视频格式 | DVI、Flash、MPEG4、MPEG、OGG Theora、QuickTime、Windows Media.Value存储在源视频和任何演绎版的元数据中。 |
| 视频编解码器 | x264.Value仅存储在视频呈现的元数据中。 |
| 视频比特率 | 指定为最小值和最大值。值仅存储在视频演绎版的元数据中。 |
| 音频编解码器 | Libvorbis、Lame Mp3、AAC Encoding.Value仅存储在视频呈现的元数据中。 |
| 音频比特率 | 指定为最小值和最大值。值仅存储在视频演绎版的元数据中。 |

1. 在 **[!UICONTROL Experience Manager]** 页面的左边栏中，点按 **[!UICONTROL 资产]**.

   如果左边栏不可见，请点按“切换边栏”图标（图标中的线条将显示为深灰色或蓝色）。

1. 打开最适合作为搜索起点的文件夹。
1. 在工具栏中，点按搜索图标（放大镜）。
1. 通过执行以下任一操作，搜索视频资产：

   * 使用关键词搜索

      在“输入关键词”字段中，开始键入内容，然后按Enter。

      系统会根据您键入的关键词过滤当前视图。 如果您的关键字与文件的名称、元数据标记或其他属性匹配，则文件将显示为搜索结果。

   * 使用属性搜索

      要根据视频类型等属性搜索视频文件，您可以通过选择视频或音频属性来缩小搜索范围。 例如，展开“视频格式”下拉列表，然后选中一个或多个值。 某些属性要求您输入最小值和最大值。

   * 使用关键词和属性搜索

      输入关键字，但不按Enter，而是展开视频或音频属性列表，然后设置所需的值。

1. （可选）在页面底部附近，点按 **[!UICONTROL 保存智能收藏集]**，输入搜索的名称。 检查 **[!UICONTROL 公共]** 如果您希望保存的搜索可供Adobe Experience Manager帐户的其他用户使用。 如果您希望搜索仅在您登录到帐户后可供您使用，请取消选中此选项。 点按 **[!UICONTROL 保存]**.
