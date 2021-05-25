---
title: 时间轴中的活动流
description: '本文介绍了如何在时间轴上显示资产的活动日志。 '
contentOwner: AG
feature: 资产管理
role: Business Practitioner,Administrator
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 48%

---

# 时间轴中的活动流 {#activity-stream-in-timeline}

这项功能可将资产的活动日志显示在时间轴上。如果您在Adobe Experience Manager(AEM)资产中执行以下任何与资产相关的操作，活动流功能会更新时间轴以反映该活动。

活动流中记录以下操作：

* 创建
* 删除
* 下载（包括演绎版）
* 发布
* 取消发布
* 批准
* 拒绝
* 移动

时间轴中显示的活动日志是从 CRX 中的 `/var/audit/com.day.cq.dam/content/dam` 位置获取的，日志文件就存储在该位置。

此外，当上传新资产或通过 [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) 或 [AEM 桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html)修改现有资产并签入 AEM 时，会记录时间轴活动。

>[!NOTE]
>
>临时工作流不会显示在时间轴中，因为没有保存这些工作流的历史记录信息。

要查看活动流，请对资产执行一个或多个操作，选择资产，然后从GlobalNav列表中选择&#x200B;**[!UICONTROL Timeline]**。

![时间轴–3](assets/timeline-3.png)

时间轴显示您对资产所执行操作的活动流。

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>**发布**&#x200B;和&#x200B;**取消发布**&#x200B;任务的默认日志存储位置为 `/var/audit/com.day.cq.replication/content`。对于&#x200B;**移动**&#x200B;任务，默认位置为 `/var/audit/com.day.cq.wcm.core.page`。
