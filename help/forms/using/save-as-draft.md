---
title: 将任务或表单另存为草稿
seo-title: Saving a task or form as a draft
description: 在AEM Forms应用程序中保存任务或表单草稿副本的步骤
seo-description: Steps to save a draft copy of a task or a form in the AEM Forms app
uuid: 1192d2c2-05a4-4a96-9015-e56111aa2646
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 9950288c-b5a2-4945-afad-be9ce2abc8e9
exl-id: c21cddb3-d12d-4e1b-bd62-cf75946569be
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# 将任务或表单另存为草稿 {#saving-a-task-or-form-as-a-draft}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

另存为草稿选项保存任务或表单的快照以及在关联表单中填充的数据。 您还可以从模板创建草稿。 草稿将保存在移动设备中，并与Adobe Experience Manager Forms服务器同步，以供以后检索。

您可以 [更新表单](/help/forms/using/working-with-form.md), [在其中添加批注](/help/forms/using/add-attachments.md) 照片和笔记。 继续更新表单时，建议将其另存为草稿。 如果您决定在稍后时间提交已填写的表单，则将其另存为草稿会很有帮助。

要为在表单门户上保存的表单启用另存为草稿功能，请参阅 [将HTML5表单另存为草稿](/help/forms/using/saving-html5-form-draft.md).\
要配置自适应表单的提交，请参阅 [草稿和提交组件](/help/forms/using/draft-submission-component.md). (对于与AEM Forms JEE服务器同步的表单无效。)

要创建草稿，请打开表单并点按 **另存为草稿** ![另存为草稿](assets/save-as-draft.png). 提供草稿的名称并点按 **保存**. 草稿保存在“草稿”文件夹中，并与服务器同步。 如果应用程序处于脱机状态，则会将其保存在Outbox文件夹中。

如果您随后更新了相应的表单，则更改会立即反映出来。 将AEM Forms应用程序与AEM Forms服务器同步时，草稿会上传到AEM Forms服务器。 此外，草稿会从发件箱移动到任务或草稿文件夹。 编辑图标会在其旁边显示。

当您继续处理多个任务和开始点并保存它们时，将保存草稿。 每次将您的应用程序与AEM Forms服务器同步时，草稿都会保存到服务器。 它可确保您随时能够根据上次保存的日期和时间恢复草稿。 例如，如果重新安装应用程序或更改移动设备，则可以从服务器下载草稿。

## 删除草稿 {#delete-a-draft}

草稿文件夹列出了所有草稿。 您可以使用删除草稿选项从移动设备和服务器中永久删除草稿。

用于删除从任务创建的草稿的选项不可用。 删除从任务创建的草稿时，该任务将被放弃。

您可以在脱机和联机模式下放弃草稿。 在脱机模式下丢弃草稿时，只有在与服务器的连接恢复时，才会从服务器中删除草稿。

执行以下步骤以删除草稿：

1. 在AEM Forms应用程序中，导航到 **Forms。**
1. 选择 **草稿** 从“搜索”旁边的下拉菜单中。
1. 带有编辑图标的表单 ![edit-draft-app](assets/edit-draft-app.png) 表示草稿。 点按草稿旁边的水平省略号。
1. 在点按水平省略号时显示的选项中，点按 **删除草稿**.
