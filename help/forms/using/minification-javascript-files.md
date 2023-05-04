---
title: 缩小JavaScript文件
seo-title: Minification of the JavaScript files
description: 有关在AEM Forms工作区自定义后生成缩小代码以优化Web JS文件的说明。
seo-description: Instructions to generate minified code after AEM Forms workspace customizations to optimize the JS files for the web.
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 2%

---

# 缩小JavaScript文件 {#minification-of-the-javascript-files}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

缩小会从源代码中删除冗余字符，如空格、新行和注释。 这会通过减小代码大小来提高性能。 虽然缩小不会影响功能，但会降低代码的可读性。

要生成缩小的代码以进行语义更改，请执行以下步骤。

1. 复制 `client-html/src/main/webapp/js` 从文件系统上的src-package 。

   >[!NOTE]
   >
   >请参阅 [自定义AEM Forms工作区简介](/help/forms/using/introduction-customizing-html-workspace.md) 以了解有关包的更多详细信息。

1. 更新中的路径 `main.js` 位于client-html/src/main/webapp/js下，用于获取已添加/更新的模型/视图。

   例如，添加了新的“共享队列”模型（如mySharequeue），请更改：

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. 更新 `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` 如果 `main.js`.

   例如，添加了新的“共享队列”模型（如mySharequeue），请更改：

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   
   To
   
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. 在client-html/src/main/webapp/js/minifier中，运行命令：

   ```shell
   mvn clean install
   ```

   它会在client-html/src/main/webapp/js下生成一个文件夹，其中包含缩小的main.js和registry.js。

>[!NOTE]
>
>缩小仅适用于64位JVM。

>[!NOTE]
>
>如果您缩小，则升级会受到影响。
