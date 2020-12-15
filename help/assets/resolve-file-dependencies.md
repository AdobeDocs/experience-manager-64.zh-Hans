---
title: 解析文件依赖关系
seo-title: 解析文件依赖关系
description: 如何在自动解析失败时解析3D文件依赖关系，如纹理映射文件。
seo-description: 如何在自动解析失败时解析3D文件依赖关系，如纹理映射文件。
uuid: 49cefabf-147b-4a78-90f3-0f2d6a8e8cae
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 05b7410b-82a1-4267-ac07-2edbc29e9ee8
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 33%

---


# 解析文件依赖关系 {#resolving-file-dependencies}

在可能的情况下，主 3D 模型文件依赖关系（例如纹理映射文件）会自动进行解析。通过让 AEM 在附近的资产文件夹中搜索与 3D 文件具有相同名称的文件，可实现此功能。如果在创建预览处理阶段有一个或多个依赖关系无法解析，则资产的卡片会在&#x200B;**[!UICONTROL 卡片视图]**&#x200B;中显示以下红色横幅消息：

![chlimage_1-124](assets/chlimage_1-124.png)

**要解析文件依赖关系**:

1. 在&#x200B;**[!UICONTROL 卡视图]**&#x200B;中，将指针悬停在卡上的&#x200B;**[!UICONTROL 未解析的依赖项]**&#x200B;横幅消息上，然后点按&#x200B;**[!UICONTROL 感叹号]**&#x200B;图标。

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. 在&#x200B;**[!UICONTROL 元数据属性]**&#x200B;页面上，点按&#x200B;**[!UICONTROL 依赖项]**&#x200B;选项卡。

   AEM无法自动解析的文件以红色列在&#x200B;**[!UICONTROL 原始路径]**&#x200B;列下。

1. 执行以下一项或多项操作：

   * **浏览到依赖关系并将其选中**。（此选项假定您已上传依赖关系文件。）

      1. 点按红色路径左侧的&#x200B;**[!UICONTROL 文件浏览]**&#x200B;图标。
      1. 在&#x200B;**[!UICONTROL 选择内容]**&#x200B;页面上，导航到缺少的文件，然后点按文件卡以选择它。
      1. 在&#x200B;**[!UICONTROL 选择内容]**&#x200B;页面的左上角，点按&#x200B;**[!UICONTROL 关闭]**（X图标）以返回至&#x200B;**[!UICONTROL 视图属性]**&#x200B;页面。
   * **上传依赖关系**。（此选项假定您尚未上传缺少的文件。）

      1. 请注意缺少的路径和文件名。
      1. 在属性页面的右上角附近，点按&#x200B;**[!UICONTROL 关闭]**。

   上传文件后，返回至&#x200B;**[!UICONTROL 视图属性>依赖项]**&#x200B;页。 新上传的资产现在将正确列为引用的资产。

   * **忽略依赖关系**。

      如果不再需要缺少的依赖关系，请在&#x200B;**[!UICONTROL 引用的资产]**&#x200B;列下缺少文件左侧的文本字段中键入`n/a`以便AEM 3D忽略该文件。



1. 在&#x200B;**[!UICONTROL 视图属性]**&#x200B;页面的右上角附近，点按&#x200B;**[!UICONTROL 保存]**。
1. 点按&#x200B;**[!UICONTROL 关闭]**&#x200B;以返回至&#x200B;**[!UICONTROL 卡视图]**。

   资产会使用新解析的依赖关系自动重新处理。

