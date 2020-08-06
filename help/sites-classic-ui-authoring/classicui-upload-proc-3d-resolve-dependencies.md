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

在可能的情况下，主 3D 模型文件依赖关系（例如纹理映射文件）会自动进行解析。通过让 AEM 在附近的资产文件夹中搜索与 3D 文件具有相同名称的文件，可实现此功能。If one or more dependencies are unresolvable during the Creating preview processing stage, the asset&#39;s card displays the following red banner message in the [!UICONTROL Card View]:

![chlimage_1-189](assets/chlimage_1-189.png)

**要解析文件依赖关系**:

1. In the **[!UICONTROL Card View]**, hover the pointer over the **[!UICONTROL Unresolved Dependencies]** banner message on the card, then tap the exclamation point icon.

   ![chlimage_1-190](assets/chlimage_1-190.png)

1. 在元数据属性页面上，点按&#x200B;**[!UICONTROL 依赖关系]**&#x200B;选项卡。

   AEM 无法自动解析的文件会以红色列在“原始路径”列下方。

1. 执行以下一项或多项操作：

   * **[!UICONTROL 浏览到依赖关系并将其选中]**。（此选项假定您已上传依赖关系文件。）

      1. Tap the **[!UICONTROL File Browse]** icon to the left of the red path.
      1. On the **[!UICONTROL Select Content]** page, navigate to the missing file, then tap on the file&#39;s card to select it.
      1. In the upper-left corner of the **[!UICONTROL Select Content]** page, tap **[!UICONTROL Close]** (X icon) to return to the **[!UICONTROL View Properties]** page.
   * **[!UICONTROL 上传依赖关系]**。（此选项假定您尚未上传缺少的文件。）

      1. 请注意缺少的路径和文件名。
      1. 在属性页面的右上角附近，点按&#x200B;**[!UICONTROL 关闭]**。

   After the files are uploaded return to **[!UICONTROL View Properties > Dependencies]** page. 新上传的资产现在将正确列为引用的资产。

   * **[!UICONTROL 忽略依赖关系]**。

      If a missing dependency is no longer needed, under the **[!UICONTROL Referenced Asset]** column, in the text field to the left of the missing file, type `n/a` so that AEM 3D ignores the file.



1. Near the upper-right corner of the **[!UICONTROL View Properties]** page, tap **[!UICONTROL Save]**.
1. Tap **[!UICONTROL Close]** to return to the **[!UICONTROL Card View]**.

   资产会使用新解析的依赖关系自动重新处理。

