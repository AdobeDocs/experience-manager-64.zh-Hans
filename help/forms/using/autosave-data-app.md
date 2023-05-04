---
title: 在AEM Forms应用程序中使用自动保存
seo-title: Using autosave in AEM Forms app
description: 了解如何在AEM Forms应用程序中使用自动保存功能，以避免数据丢失。
seo-description: Learn how to use autosave feature in AEM Forms app that lets you avoid data loss.
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
exl-id: 6eb00c31-6806-478a-99d1-55912798ea69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 1%

---

# 在AEM Forms应用程序中使用自动保存 {#using-autosave-in-aem-forms-app}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

当用户在Adobe Experience Manager Forms应用程序中输入数据时，自动保存功能会定期保存数据。 AEM Forms应用程序中的自动保存功能可帮助您避免在应用程序意外关闭时丢失数据。

您的应用程序可能会意外关闭：

* 如果设备因电池不足而关闭
* 如果用户杀死应用程序
* 如果发生意外崩溃

您可以指定应用程序保存输入数据的间隔。

>[!NOTE]
>
>谨慎选择自动保存频率。 频繁的自动保存操作可能会对设备的性能产生显着影响。

执行以下步骤以使用AEM Forms应用程序中的自动保存功能：

1. 登录应用程序，然后导航到 **[!UICONTROL 设置>常规]**.
1. 在“常规”屏幕中，使用 **[!UICONTROL 自动保存频率]** 选项，以选择您希望应用程序保存输入数据的间隔。
   [ ![设置自动保存频率](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. 重新启动应用程序并使用同一用户登录时，系统会提示您使用恢复未保存的任务对话框还原任务。 单击 **[!UICONTROL 确定]** 在恢复未保存的任务对话框中，以继续处理已保存的任务。 您可以单击 **[!UICONTROL 取消]** 删除与上次触发的自动保存对应的已保存数据，然后开始处理新任务。

   单击 **[!UICONTROL 确定]**，则会还原任务，并在应用程序崩溃之前触发与最新自动保存对应的数据。 它包括表单数据以及与任务关联的所有附件。
   [ ![正在恢复任务&#x200B;](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**A.** 正在进行的表单 **B.** 应用程序被强制关闭 **C.** 使用恢复未保存的任务对话框重新启动了应用程序 **D.** 使用原始数据还原的表单
