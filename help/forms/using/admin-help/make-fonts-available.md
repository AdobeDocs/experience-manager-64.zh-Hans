---
title: 使字体可用
seo-title: Make fonts available
description: 确保表单中使用的字体可用于托管AEM表单的J2EE应用程序服务器。
seo-description: Ensure that the fonts used within a form are available for use on the J2EE application server hosting AEM forms.
uuid: 6588b4b6-f866-4253-91c8-3aa174340e8c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9f58a6c4-3190-49d4-800c-4a55dca7c296
exl-id: 33d63ec9-b100-48b4-b84d-a9de82c24f86
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 2%

---

# 使字体可用 {#make-fonts-available}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

确保表单中使用的字体可用于托管AEM表单的J2EE应用程序服务器。 例如，请考虑以下情景。 表单设计器将字体添加到Designer使用的字体目录中，并在单独的计算机上创建使用该字体的表单。 为了使输出服务使用字体，请将其置于Customer fonts目录中。 如果Customer fonts目录不存在，请在托管AEM表单的J2EE应用程序服务器上创建一个目录。

有关其他字体设置的信息，请参阅 [配置常规AEM表单设置](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings).

**指定Customer fonts目录的位置**

1. 在管理控制台中，单击设置>核心系统设置>配置。
1. 在“System Fonts Directory（系统字体目录的位置）”框中，键入Customer Fonts目录的路径。 可以添加多个目录，并以分号分隔 **;**
1. 单击确定。
1. 重新启动安装AEM表单的系统。

>[!NOTE]
>
>从Windows系统字体缓存中选取字体，并且需要系统重新启动才能更新缓存。 指定客户字体目录后，请确保重新启动安装AEM表单的系统。
