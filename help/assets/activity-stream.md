---
title: 时间轴中的活动流
description: 本文介绍了如何在时间轴上显示资产的活动日志。
contentOwner: AG
feature: Asset Management
role: User,Admin
exl-id: 52fa2d59-177f-49ca-a480-7213ce0ca7d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 23%

---

# 时间轴中的活动流 {#activity-stream-in-timeline}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

此功能可在时间轴上显示资产的活动日志。 如果您在 [!DNL Adobe Experience Manager Assets]，活动流功能会更新时间轴以反映活动。

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

此外，当上传新资产或通过修改现有资产并签入Experience Manager时，会记录时间轴活动 [Adobe资产链接](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) 或 [[!DNL Experience Manager] 桌面应用程序](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html).

>[!NOTE]
>
>临时工作流不会显示在时间轴中，因为没有保存这些工作流的历史记录信息。

要查看活动流，请对资产执行一个或多个操作，选择资产，然后选择 **[!UICONTROL 时间轴]** GlobalNav列表中。

![时间轴–3](assets/timeline-3.png)

时间轴显示您对资产执行的操作的活动流。

![activity_stream](assets/activity_stream.png)

>[!NOTE]
>
>**发布**&#x200B;和&#x200B;**取消发布**&#x200B;任务的默认日志存储位置为 `/var/audit/com.day.cq.replication/content`。对于&#x200B;**移动**&#x200B;任务，默认位置为 `/var/audit/com.day.cq.wcm.core.page`。
