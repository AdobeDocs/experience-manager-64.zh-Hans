---
title: 在AEM Forms应用程序中使用自动保存
seo-title: 在AEM Forms应用程序中使用自动保存
description: '了解如何在AEM Forms应用程序中使用自动保存功能，从而避免数据丢失。 '
seo-description: '了解如何在AEM Forms应用程序中使用自动保存功能，从而避免数据丢失。 '
uuid: f18ab6b4-dd4a-4dcb-88e6-e349777d47ea
contentOwner: sashanka
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 133d93b0-512c-46db-b5f9-f981d77b565f
translation-type: tm+mt
source-git-commit: e2bb2f17035e16864b1dc54f5768a99429a3dd9f
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# 在AEM Forms应用程序{#using-autosave-in-aem-forms-app}中使用自动保存

当用户在Adobe Experience Manager Forms应用程序中输入数据时，自动保存功能会定期保存数据。 AEM Forms应用程序中的自动保存功能可帮助您避免意外关闭应用程序时丢失数据。

您的应用程序可能会意外关闭：

* 如果设备因电池不足而关闭
* 如果用户杀掉应用程序
* 如果发生意外崩溃

您可以指定应用程序保存输入数据的时间间隔。

>[!NOTE]
>
>谨慎选择自动保存频率。 频繁的自动保存操作可能会对设备的性能产生显着影响。

执行以下步骤以使用AEM Forms应用程序中的自动保存功能：

1. 登录应用程序，然后导航到&#x200B;**[!UICONTROL 设置>常规]**。
1. 在“常规”屏幕中，使用&#x200B;**[!UICONTROL 自动保存频率]**选项选择您希望应用程序保存输入数据的时间间隔。
   [ ![设置自动保存频率](assets/using-autosave-freq-07.png)](assets/using-autosave-freq-07-1.png)

1. 当您重新启动应用程序并使用同一用户登录时，系统会提示您使用“恢复未保存的任务”对话框恢复任务。 单击“恢复未保存的任务”对话框中的&#x200B;**[!UICONTROL 确定]**，以继续使用保存的任务。 单击&#x200B;**[!UICONTROL 取消]**&#x200B;可删除与上次触发的自动保存和使用新任务的开始相对应的已保存数据。

   单击&#x200B;**[!UICONTROL 确定]**后，任务将恢复，其数据与应用程序崩溃前触发的最新自动保存相对应。 它包括表单数据以及与任务关联的所有附件。
   [ ![获取任务&#x200B;](assets/autosave-flow.png)](assets/using-autosave-freq-06.png)**recoveredA.** A正在处理的表单 **B.App已强制关闭C.** App，已重新启动“恢复未保存的任务” **对话框“D.A”用原始数据**  **** 还原的表单

