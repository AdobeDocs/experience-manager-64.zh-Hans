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

在可能的情况下，主 3D 模型文件依赖关系（例如纹理映射文件）会自动进行解析。通过让 AEM 在附近的资产文件夹中搜索与 3D 文件具有相同名称的文件，可实现此功能。If one or more dependencies are unresolvable during the Creating preview processing stage, the asset&#39;s card displays the following red banner message in the **[!UICONTROL Card View]**:

![chlimage_1-124](assets/chlimage_1-124.png)

**要解析文件依赖关系**:

1. In the **[!UICONTROL Card View]**, hover the pointer over the **[!UICONTROL Unresolved Dependencies]** banner message on the card, then tap the **[!UICONTROL Exclamation Point]** icon.

   ![chlimage_1-125](assets/chlimage_1-125.png)

1. On the **[!UICONTROL Metadata Properties]** page, tap the **[!UICONTROL Dependencies]** tab.

   The files that AEM could not auto-resolve are listed under the **[!UICONTROL Original Paths]** column, in red.

1. 执行以下一项或多项操作：

   * **浏览到依赖关系并将其选中**。（此选项假定您已上传依赖关系文件。）

      1. Tap the **[!UICONTROL File Browse]** icon to the left of the red path.
      1. On the **[!UICONTROL Select Content]** page, navigate to the missing file, then tap on the file&#39;s card to select it.
      1. In the upper-left corner of the **[!UICONTROL Select Content]** page, tap **[!UICONTROL Close]** (X icon) to return to the **[!UICONTROL View Properties]** page.
   * **上传依赖关系**。（此选项假定您尚未上传缺少的文件。）

      1. 请注意缺少的路径和文件名。
      1. 在属性页面的右上角附近，点按&#x200B;**[!UICONTROL 关闭]**。

   After the files are uploaded return to **[!UICONTROL View Properties > Dependencies]** page. 新上传的资产现在将正确列为引用的资产。

   * **忽略依赖关系**。

      If a missing dependency is no longer needed, under the **[!UICONTROL Referenced Asset]** column, in the text field to the left of the missing file, type `n/a` so that AEM 3D ignores the file.



1. Near the upper-right corner of the **[!UICONTROL View Properties]** page, tap **[!UICONTROL Save]**.
1. Tap **[!UICONTROL Close]** to return to the **[!UICONTROL Card View]**.

   资产会使用新解析的依赖关系自动重新处理。

