---
title: 在维护模式下运行AEM表单
seo-title: 在维护模式下运行AEM表单
description: 维护模式在执行诸如修补DSC、升级AEM表单或应用Service Pack之类的任务时非常有用。 了解有关在维护模式下运行AEM表单的更多信息。
seo-description: 维护模式在执行诸如修补DSC、升级AEM表单或应用Service Pack之类的任务时非常有用。 了解有关在维护模式下运行AEM表单的更多信息。
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# 在维护模式下运行AEM表单{#running-aem-forms-in-maintenance-mode}

维护模式在执行诸如修补DSC、升级AEM表单或应用Service Pack之类的任务时非常有用。

避免在服务器处于维护模式时调用任何进程。 如果在服务器处于维护模式时调用进程，则会发生以下情况：

* 如果该过程的生命周期较长，则会将其添加到作业数据库，但不会启动。 退出维护模式时，AEM Forms会处理其队列中长期存在的作业，即使服务器在维护模式下重新启动也是如此。
* 如果该流程的生命周期很短，则会立即进行处理。

**将AEM表单置于维护模式**

1. 在Web浏览器中，输入：

   `https://`*[]*`:`*[]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[hostnameportadministrator用&#x200B;]*`&password=`*[户名密码]*

   浏览器窗口中将显示“现在已暂停”消息。

   >[!NOTE]
   >
   >如果在服务器处于维护模式时关闭服务器，则重新启动服务器后仍将处于维护模式。 完成维护任务后，必须关闭维护模式。

**检查AEM表单是否在维护模式下运行**

1. 在Web浏览器中，输入：

   `https://`*[主机名]:[]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[portadministrator]* `&password=`*[usernamepassword ]*

   状态显示在浏览器窗口中。 状态为“true”表示服务器在维护模式下运行，而“false”表示服务器未处于维护模式。

**关闭维护模式**

1. 在Web浏览器中，输入：

   `https://`*[主机名]:[]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[portadministrator]* `&password=`*[usernamepassword ]*

   浏览器窗口中会显示“当前正在运行”消息。
