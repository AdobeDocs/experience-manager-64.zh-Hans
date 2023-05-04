---
title: 添加附件
seo-title: Adding attachments
description: 在AEM Forms应用程序中，将照片和笔记作为批注添加到任务中
seo-description: Add photographs and scribble notes as annotations to your task in the AEM Forms app
uuid: cf8b54a8-e5bc-49df-90f8-c6a37533c347
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 184b5c7f-a704-4b8c-b1ec-f4d6616a1afc
exl-id: ad1cc63a-cf99-456b-8b83-0605fb3ac6ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 1%

---

# 添加附件 {#adding-attachments}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 在与AEM Forms工作流服务器(JEE上的AEM Forms)同步的表单中添加附件 {#adding-annotations}

AEM Forms应用程序允许您将图像、潦草的注释和文本注释附加到与AEM Forms JEE服务器同步的表单中。 如果您的表单是从AEM Forms工作流服务器加载的，则附件会添加到表单中。 您可以点按附件按钮 ![attachments-app](assets/attachments-app.png) 一起查看表单中的所有附件。 红色通知指定表单中的附件数。 如果表单中没有附件，则看不到红色通知按钮。 如果表单中没有附件，则在您点按附件按钮时 ![attch](assets/attch.png)，则可以选择附加照片或涂写。

您的选项包括：

* **[!UICONTROL 图库]**:用于根据设备上保存的图片添加图片。

* **[!UICONTROL 相机]**:允许您拍摄照片并将其添加到表单中。

* **[!UICONTROL 注释]**:允许您添加涂写或文本注释。 使用 ![涂写](assets/scribble.png) 添加涂写，以及 ![键盘](assets/keyboard.png) 添加文本注释。

>[!NOTE]
>
>一个用户添加的附件对其他AEM Forms应用程序用户可见。 其他用户无法删除用户添加的附件。

### “附件”屏幕 {#the-attachments-screen}

要查看某个位置中的所有附件，请点按 ![attachments-app](assets/attachments-app.png). 您可以在此处添加、重命名和删除附件。

![所有附件都在一个位置](assets/attachments-screen.png)

您可以使用 **+** “附件”屏幕中的“附件”按钮，以附加其他图片、涂写或文本。

### 添加照片 {#adding-a-photograph}

您可以使用移动设备的相机或设备中保存的图片来附加表单中的图片。

1. 点按附件按钮 ![attch](assets/attch.png) 在窗口底部。
1. 点按 **[!UICONTROL 图库]** 或 **[!UICONTROL 相机]** 中。
1. 根据您选择的选项，执行以下操作：

   1. 如果您选择 **[!UICONTROL 相机]**.

      拍照。 然后点按 **[!UICONTROL 使用]** ![use-pic](assets/use-pic.png) 按钮。

      或点按 **[!UICONTROL 重拍]** ![重修](assets/retake.png) 按钮重拍照片。

   1. 如果您选择 **[!UICONTROL 图库]**.

      此时会弹出设备的图像浏览器。 在设备的图片浏览器中，点按要附加的图片。

### 添加注释 {#adding-a-note}

的 **注释** 选项允许您在表单中添加手绘脚本和文本附件。

1. 点按附件按钮 ![attch](assets/attch.png) 在窗口底部。
1. 点按 **[!UICONTROL 注释]** 中。
1. 在启动的“注释”用户界面中，捕获手绘。

   ![涂写界面](assets/scribble-ui.png)
   **图：** *涂写*

   您可以在涂写界面中使用以下选项：

   * **[!UICONTROL 清除]**:清除屏幕。
   * **[!UICONTROL 完成]**:附加当前涂写。
   * **[!UICONTROL 取消]**:放弃当前涂写并退出涂写用户界面。
   * ![键盘](assets/keyboard.png):清除涂写，并允许您添加文本注释。

   ![AEM Forms应用程序中的键盘涂写](assets/keyboard-inapp.png)

## 表单中的附件与AEM Forms服务器同步，但没有AEM Forms工作流(OSGi上的AEM Forms) {#attachments-in-forms-synced-with-the-aem-forms-servers-without-aem-forms-workflow-aem-forms-on-osgi}

与AEM Forms OSGi服务器同步的移动表单的附件与AEM Forms JEE服务器类似。

从AEM Forms OSGi服务器在应用程序中加载的自适应表单不支持表单级别附件。 要附加图像或文本注释，请在创作表单时启用表单中的字段级附件。 将文件附件组件从组件浏览器拖放到字段上。

如果是自适应表单，则可以查看记录文档(DoR)中的附加文件。 看， [为非XFA自适应表单生成记录文档](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).
