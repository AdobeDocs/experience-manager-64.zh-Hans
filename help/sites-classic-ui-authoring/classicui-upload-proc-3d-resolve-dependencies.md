---
title: 解析文件依赖关系
seo-title: 解析文件依赖关系
description: 在可能的情况下，主 3D 模型文件依赖关系（例如纹理映射文件）会自动进行解析。通过让 AEM 在附近的资产文件夹中搜索与 3D 文件具有相同名称的文件，可实现此功能。
seo-description: 在可能的情况下，主 3D 模型文件依赖关系（例如纹理映射文件）会自动进行解析。通过让 AEM 在附近的资产文件夹中搜索与 3D 文件具有相同名称的文件，可实现此功能。
uuid: b1b83cb7-b6e5-4417-9a53-b6d8bcf8d2e0
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: authoring
content-type: reference
discoiquuid: 14754023-e7c4-4dc5-a9d8-408b81861d95
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 55%

---


# 解析文件依赖关系{#resolving-file-dependencies}

在可能的情况下，主 3D 模型文件依赖关系（例如纹理映射文件）会自动进行解析。通过让 AEM 在附近的资产文件夹中搜索与 3D 文件具有相同名称的文件，可实现此功能。如果在创建预览处理阶段有一个或多个依赖关系无法解析，则资产的卡片会在[!UICONTROL 卡片视图]中显示以下红色横幅消息：

![chlimage_1-109](assets/chlimage_1-189.png)

**要解析文件依赖关系**:

1. 在&#x200B;**[!UICONTROL 卡视图]**&#x200B;中，将指针悬停在卡上的&#x200B;**[!UICONTROL 未解析的依赖关系]**&#x200B;横幅消息上，然后点按感叹号图标。

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. 在元数据属性页面上，点按&#x200B;**[!UICONTROL 依赖关系]**&#x200B;选项卡。

   AEM 无法自动解析的文件会以红色列在“原始路径”列下方。

1. 执行以下一项或多项操作：

   * **[!UICONTROL 浏览到依赖关系并将其选中]**。（此选项假定您已上传依赖关系文件。）

      1. 点按红色路径左侧的&#x200B;**[!UICONTROL 文件浏览]**&#x200B;图标。
      1. 在&#x200B;**[!UICONTROL 选择内容]**&#x200B;页面上，导航到缺少的文件，然后点按文件卡以选择它。
      1. 在&#x200B;**[!UICONTROL 选择内容]**&#x200B;页面的左上角，点按&#x200B;**[!UICONTROL 关闭]**（X图标）以返回至&#x200B;**[!UICONTROL 视图属性]**&#x200B;页面。
   * **[!UICONTROL 上传依赖关系]**。（此选项假定您尚未上传缺少的文件。）

      1. 请注意缺少的路径和文件名。
      1. 在属性页面的右上角附近，点按&#x200B;**[!UICONTROL 关闭]**。

   上传文件后，返回至&#x200B;**[!UICONTROL 视图属性>依赖项]**&#x200B;页。 新上传的资产现在将正确列为引用的资产。

   * **[!UICONTROL 忽略依赖关系]**。

      如果不再需要缺少的依赖关系，请在&#x200B;**[!UICONTROL 引用的资产]**&#x200B;列下缺少文件左侧的文本字段中键入`n/a`以便AEM 3D忽略该文件。



1. 在&#x200B;**[!UICONTROL 视图属性]**&#x200B;页面的右上角附近，点按&#x200B;**[!UICONTROL 保存]**。
1. 点按&#x200B;**[!UICONTROL 关闭]**&#x200B;以返回至&#x200B;**[!UICONTROL 卡视图]**。

   资产会使用新解析的依赖关系自动重新处理。

