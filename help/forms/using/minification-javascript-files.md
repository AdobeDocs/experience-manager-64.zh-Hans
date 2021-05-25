---
title: 缩小JavaScript文件
seo-title: 缩小JavaScript文件
description: 有关在AEM Forms工作区自定义后生成缩小代码以优化Web JS文件的说明。
seo-description: 有关在AEM Forms工作区自定义后生成缩小代码以优化Web JS文件的说明。
uuid: ad91e380-a988-4740-9534-e09657e0322a
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c88a3013-5da2-4b09-9f29-ac1fb00822ec
exl-id: 8394151e-e9cf-4f68-97a3-ba1d1dd6a2d2
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# 缩小JavaScript文件{#minification-of-the-javascript-files}

缩小会从源代码中删除冗余字符，如空格、新行和注释。 这会通过减小代码大小来提高性能。 虽然缩小不会影响功能，但会降低代码的可读性。

要生成缩小的代码以进行语义更改，请执行以下步骤。

1. 从文件系统上的src-package复制`client-html/src/main/webapp/js`。

   >[!NOTE]
   >
   >有关包的更多详细信息，请参阅[自定义AEM Forms工作区简介](/help/forms/using/introduction-customizing-html-workspace.md)。

1. 更新`main.js`中位于client-html/src/main/webapp/js下的路径，以获取已添加/已更新的模型/视图。

   例如，添加了新的“共享队列”模型（如mySharequeue），请更改：

   ```
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   
   To
   
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. 如果`main.js`中存在别名的更改/添加，请更新`registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,`。

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
