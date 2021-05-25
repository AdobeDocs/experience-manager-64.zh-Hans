---
title: 更改组织标识以进行品牌推广
seo-title: 更改组织标识以进行品牌推广
description: 要品牌AEM Forms工作区，请通过自定义默认徽标来提供您组织的徽标。
seo-description: 要品牌AEM Forms工作区，请通过自定义默认徽标来提供您组织的徽标。
uuid: f0c340ee-2e54-4bb0-9c30-383cc1bbadb8
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 2c651302-f4ef-4211-b897-f5942ed0ffb1
exl-id: 890e98af-0491-4b59-9a9b-6c245db54f0f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 0%

---

# 更改{#changing-the-organization-logo-for-branding}品牌的组织徽标

组织徽标显示在AEM Forms工作区的左上角。 要更新徽标，请按照[AEM Forms工作区自定义的常规步骤](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization)执行，然后执行以下步骤。

1. 创建徽标并将文件命名为`NewWorkspace.png`。 使用WebDAV客户端将图像文件放置在/apps/ws/images文件夹中。

   >[!NOTE]
   >
   >推荐的徽标图像大小为218 px × 20 px。

   >[!NOTE]
   >
   >有关WebDAV访问的更多信息，请参阅[https://dev.day.com/docs/en/crx/current/how_to/webdav_access.html](https://docs.adobe.com/docs/en/crx/current/how_to/webdav_access.html)。

1. 通过添加以下样式，在/apps/ws/css/newStyle.css的样式表中引用新的徽标图像。

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px; 
         }
   ```
