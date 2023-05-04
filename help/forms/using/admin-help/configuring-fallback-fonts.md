---
title: 配置回退字体
seo-title: Configuring fallback fonts
description: 了解如何配置回退字体。
seo-description: Learn how to configure fallback fonts.
uuid: 2745541c-8c6d-4bb4-aa14-ec19afd6bc35
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d997a268-a40a-462d-badd-94f0731f7ba4
feature: PDF Generator
exl-id: 6942b6fc-8d04-429f-8433-1ab74c68fcc1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 1%

---

# 配置回退字体 {#configuring-fallback-fonts}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以手动配置FontManagerResources.properties文件，以将默认的AEM表单字体映射到回退（或替换）（如果服务器上没有默认字体）。 此属性文件位于adobe-fontmanager.jar文件中。

>[!NOTE]
>
>回退字体配置也适用于汇编程序服务。

1. 导航到adobe-livecycle-*[appserver]*.ear文件(位于 *[aem-forms根]*/configurationManager/export目录，创建备份副本，并解包原始副本。
1. 找到adobe-fontmanager.jar文件并将其解包。
1. 找到FontManagerResources.properties文件，并在文本编辑器中将其打开。
1. 根据需要修改通用字体和回退字体位置和名称，并保存文件。

   FontManagerResources.properties文件中的字体条目与 *[aem-forms根]*/fonts目录。 如果指定的字体不是默认的AEM表单字体，则必须在此目录结构中（在现有目录中或新创建的目录中）安装这些字体。

   >[!NOTE]
   >
   >如果指定的字体或默认字体不包含特定的unicode字符，或者如果不可用，则根据以下优先级从回退字体中提取该字符：

   * 特定于区域设置的字体
   * 未设置区域设置时的根字体
   * 通用字体，按回退表中的顺序集搜索

1. 重新打包adobe-fontmanager.jar文件。
1. 重新打包adobe-livecycle-*[appserver]*.ear文件，然后手动或通过运行Configuration Manager重新部署它。

>[!NOTE]
>
>请勿使用Configuration Manager重新打包adobe-livecycle-[appserver].ear文件，因为它将使用AEM表单默认值覆盖您的修改。
