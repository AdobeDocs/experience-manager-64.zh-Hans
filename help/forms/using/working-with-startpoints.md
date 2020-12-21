---
title: 使用起点
seo-title: 使用起点
description: 从Workbench中定义的移动设备处理AEM Forms流程的步骤。
seo-description: 从Workbench中定义的移动设备处理AEM Forms流程的步骤。
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# 使用起点{#working-with-startpoints}

起始点调用在Workbench中创建的流程。 它与提交表单时调用流程的表单相关联。 请参阅[Geometrixx财务参考站点演练](/help/forms/using/finance-reference-site-walkthrough.md)以了解流程。

>[!NOTE]
>
>术语起点、开始过程和表单在提及此概念时可交互使用。

要从AEM Forms应用程序启动进程，您需要在进程中具有类型为&#x200B;**Workspace**&#x200B;的起点。 此外，您还需要为起点选择&#x200B;**[!UICONTROL Visible in Mobile Workspace]**&#x200B;选项。

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**开始在工作台中定义的流程**

1. 要视图AEM Forms应用程序中可用的起始点，请转到[主屏幕](/help/forms/using/home-screen.md)。
1. 默认情况下，在&#x200B;**[!UICONTROL Home]**&#x200B;屏幕上显示&#x200B;**[!UICONTROL 所有Forms]**&#x200B;列表。

   起始点与表单关联。 点按列表中的起始点关联表单以将其打开。

   此时将打开与起始点关联的表单。

1. 在&#x200B;**[!UICONTROL 起始点]**&#x200B;表单中输入详细信息。

   可以使用[attachment](/help/forms/using/add-attachments.md)按钮向此任务添加注释。

1. 填写表单后，点按&#x200B;**提交**&#x200B;按钮。

如果应用程序处于脱机状态，则表单及其数据将保存在“发件箱”文件夹中。

如果应用程序处于联机状态，则任务将与AEM Forms服务器同步，并分配给进程中指定的用户。

要在任务列表中使用任务，请参阅[打开任务](/help/forms/using/open-task.md)。
