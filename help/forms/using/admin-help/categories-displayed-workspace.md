---
title: 管理工作区中显示的类别
seo-title: Managing the categories displayed in Workspace
description: 在工作区中，用户可以启动的进程会在左侧导航窗格的类别中显示。 了解如何管理工作区中显示的这些类别。
seo-description: In Workspace, the processes that a user can start are displayed in categories in the left navigation pane. Learn how you can manage these categories displayed in Workspace.
uuid: c2a275f5-872e-467f-9f07-4b130631e8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0d1536a2-10ac-4031-bd7f-264b02d0d75f
exl-id: 5a2bd0ea-2c5e-4e0c-aff1-dba06be6a5b7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%

---

# 管理工作区中显示的类别 {#managing-the-categories-displayed-in-workspace}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在工作区中，用户可以启动的进程会在左侧导航窗格的类别中显示。 您可以在管理控制台中设置类别，流程设计人员也可以在Workbench中设置类别。 当流程设计者创建流程时，他们会将流程分配给类别。

指定类别名称时，请创建这些名称，以便它们能够正确显示在“工作区”导航窗格中。 默认情况下，左侧导航窗格的固定宽度为210像素，大约为24个字符。 如果指定的类别名称太长，无法容纳在左侧导航窗格的固定宽度内，则会被截断。 仅当鼠标指针悬停在其上方时，才显示全名。 尽量避免类别名称被截断。 以下示例说明了适合的类别名称和被截断的类别名称：

**符合以下条件的类别名称：** 出勤和休假

**被截断的类别名称：** 出席和休假（美国）

在工作区中，类别内的进程通常在“开始进程”页面上显示为卡片。 通常，在用户需要滚动查看剩余卡片之前，某个类别的屏幕上会显示六张卡片。 由于滚动会使查找过程变得更加困难，因此请考虑将每个类别限制为6个进程，或者根据您的分辨率，限制屏幕上可显示的进程数量，而无需进行任何滚动。

如果您将MySQL用作AEM表单数据库，管理控制台将无法区分两个类别名称，这两个类别名称仅在使用扩展字符时有所不同。 例如，如果创建名为abcde的类别和名为âbcdè的类别，则它们会被视为相同。

## 添加类别 {#add-a-category}

1. 在管理控制台中，单击服务>应用程序和服务>类别管理。
1. 单击添加。 如果要添加子类别，请选择类别，然后单击“添加”。
1. 在“名称”框中，键入类别的名称，然后在“描述”框中，键入类别的描述。
1. 单击添加。 类别显示在“类别管理”页面上。

   ***注释&#x200B;**:在创建类别时，最多只能添加五个层级。*

## 编辑类别 {#edit-a-category}

1. 在管理控制台中，单击服务>应用程序和服务>类别管理。
1. 选择要编辑的类别，然后单击“编辑”。 或者，您也可以双击要编辑的类别。
1. 在“名称”(Name)框中编辑类别的名称。

## 删除类别 {#remove-a-category}

您只能删除未使用的类别。

1. 在管理控制台中，单击服务>应用程序和服务>类别管理。
1. 在类别管理页面上，选中要删除的类别的复选框，然后单击删除。 不再显示类别。
