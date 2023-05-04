---
title: 使用起点
seo-title: Working with Startpoints
description: 在Workbench中定义的移动设备中使用AEM Forms进程的步骤。
seo-description: Steps to work with a AEM Forms process from your Mobile device defined in Workbench.
uuid: 9c51ce52-e7ba-43d3-a85c-67067f680ccb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 265eee8a-364e-4edf-b2a0-f42617169944
exl-id: ef9352c7-c164-4cbf-8f18-5b97aa5f56be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 1%

---

# 使用起点 {#working-with-startpoints}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

起始点会调用在Workbench中创建的进程。 它与表单相关联，表单提交时会调用该进程。 请参阅 [Geometrixx金融参考站点演练](/help/forms/using/finance-reference-site-walkthrough.md) 了解流程。

>[!NOTE]
>
>术语起点、开始过程和表单在指代此概念时可互换使用。

要从AEM Forms应用程序启动进程，您需要具有类型的起点 **工作区** 在您的过程中。 此外，您还需要选择 **[!UICONTROL 在移动设备工作区中可见]** 选项。

![mws_startpoint_select_option](assets/mws_startpoint_select_option.png)

**启动在Workbench中定义的流程**

1. 要查看AEM Forms应用程序中可用的起点，请转到 [主屏幕](/help/forms/using/home-screen.md).
1. 在 **[!UICONTROL 主页]** 屏幕，默认情况下 **[!UICONTROL 全部Forms]** 列表。

   起始点与表单关联。 点按列表中关联的起始点表单以将其打开。

   将打开与起始点关联的表单。

1. 在 **[!UICONTROL 起点]** 表单。

   您可以使用 [附件](/help/forms/using/add-attachments.md) 按钮。

1. 填写表单后，点按 **提交** 按钮。

如果应用程序处于脱机状态，则表单及其数据会保存在“发件箱”文件夹中。

如果应用程序处于联机状态，则该任务将与AEM Forms服务器同步，并分配给进程中指定的用户。

要处理任务列表中的任务，请参阅 [打开任务](/help/forms/using/open-task.md).
