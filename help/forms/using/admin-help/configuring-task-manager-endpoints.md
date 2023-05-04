---
title: 配置任务管理器端点
seo-title: Configuring Task Manager endpoints
description: 了解如何配置Task Manager端点。
seo-description: Learn how to configure Task Manager endpoints.
uuid: 07604b10-0bd7-4bce-9624-7ebac4754f56
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9c55feb9-23d8-4798-a3c5-70ec736df3ad
exl-id: 546a699e-975f-42a1-8ab5-0de4bd7f4a8f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 1%

---

# 配置任务管理器端点 {#configuring-task-manager-endpoints}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

任务管理器端点使工作区用户能够调用服务。

**任务管理器端点设置**

使用以下设置配置任务管理器端点。

**名称：** （必需）标识端点。 该名称显示在工作区的卡片视图中。 不要包含&lt;字符，因为它将截断工作区中显示的名称。 如果输入URL作为端点的名称，请确保它符合RFC1738中指定的语法规则。

**描述：** 端点的描述。 请勿包含&lt;字符，因为它将截断工作区中显示的描述。

**任务说明：** 启动此工作流的用户的说明。

**流程所有者：** 负责流程的人员的姓名。

**用户可以转发任务：** 允许用户转发初始任务。

**显示附件窗口：** 允许用户查看附件窗口。

**允许附件添加：** 允许用户添加附件和注释。

**任务最初锁定：** 锁定初始任务。

**为共享队列添加ACL:** 使用ACL为共享队列用户创建初始任务。

**分类：** （必需）用户在工作区中将看到表单的类别。 从列表中选择类别，或选择新建类别以添加类别。

**操作名称：** （必需）可分配给端点的操作列表。
