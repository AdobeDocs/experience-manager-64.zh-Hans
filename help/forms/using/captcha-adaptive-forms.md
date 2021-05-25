---
title: 在自适应表单中使用CAPTCHA
seo-title: 在自适应表单中使用CAPTCHA
description: 了解如何在自适应表单中配置AEM CAPTCHA或Google reCAPTCHA服务。
seo-description: 了解如何在自适应表单中配置AEM CAPTCHA或Google reCAPTCHA服务。
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: 自适应表单
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '675'
ht-degree: 0%

---

# 在自适应表单{#using-captcha-in-adaptive-forms}中使用CAPTCHA

CAPTCHA(Completely Automated Public Turing test to tell Computers and Humans Apart)是一种在线交易中常用的程序，用于区分人类和自动程序或机器人。 它会给用户带来挑战并评估用户响应，以确定它是人还是机器人与站点进行交互。 它可阻止用户在测试失败时继续操作，并通过防止机器人发布垃圾邮件或恶意目的，帮助确保在线交易的安全。

AEM Forms支持自适应表单中的验证码。 您可以使用Google的reCAPTCHA服务来实施CAPTCHA。

>[!NOTE]
>
>AEM Forms仅支持reCaptcha v2。 不支持任何其他版本。
>
>在AEM Forms应用程序的离线模式下，不支持自适应表单中的验证码。

## Google {#google-recaptcha}配置ReCAPTCHA服务

表单作者可以使用Google提供的reCAPTCHA服务在自适应表单中实施CAPTCHA。 它提供高级验证码功能以保护您的网站。 有关reCAPTCHA工作原理的更多信息，请参阅[Google reCAPTCHA](https://developers.google.com/recaptcha/)。

![recapcha](assets/recaptcha.png)

要在AEM Forms中实施reCAPTCHA服务，请执行以下操作：

1. 从Google获取[reCAPTCHA API密钥对](https://www.google.com/recaptcha/admin)。 它包括站点密钥和密钥。
1. 为云服务创建配置容器。

   1. 转到&#x200B;**[!UICONTROL 工具>常规>配置浏览器]**。
      * 有关更多信息，请参阅[配置浏览器文档](/help/sites-administering/configurations.md)。
   1. 执行以下操作可为云配置启用全局文件夹，或跳过此步骤以为云服务配置创建和配置其他文件夹。

      1. 在配置浏览器中，选择&#x200B;**[!UICONTROL 全局]**&#x200B;文件夹，然后点按&#x200B;**[!UICONTROL 属性]**。
      1. 在配置属性对话框中，启用&#x200B;**[!UICONTROL 云配置]**。
      1. 点按&#x200B;**[!UICONTROL 保存并关闭]**&#x200B;以保存配置并退出对话框。
   1. 在配置浏览器中，点按&#x200B;**[!UICONTROL 创建]**。
   1. 在创建配置对话框中，为文件夹指定标题并启用&#x200B;**[!UICONTROL 云配置]**。
   1. 点按&#x200B;**[!UICONTROL 创建]** ，以创建为云服务配置启用的文件夹。


1. 为reCAPTCHA配置云服务。

   1. 在AEM创作实例中，转到![tools](assets/tools.png) > **Cloud Services**。
   1. 点按&#x200B;**[!UICONTROL reCAPTCHA]**。 此时将打开“配置”页面。 选择在上一步中创建的配置容器，然后点按&#x200B;**[!UICONTROL 创建]**。
   1. 为reCAPTCHA服务指定名称、站点密钥和密钥，然后点按&#x200B;**[!UICONTROL 创建]**&#x200B;以创建云服务配置。
   1. 在编辑组件对话框中，指定在步骤1中获取的站点和密钥。 点按&#x200B;**[!UICONTROL 保存设置]**，然后点按&#x200B;**[!UICONTROL 确定]**&#x200B;以完成配置。

   配置reCAPTCHA服务后，即可在自适应表单中使用。 有关更多信息，请参阅[在自适应表单中使用CAPTCHA](#using-captcha)。

## 在自适应表单{#using-captcha}中使用CAPTCHA

要在自适应表单中使用CAPTCHA，请执行以下操作：

1. 在编辑模式下打开自适应表单。

   >[!NOTE]
   >
   >确保在创建自适应表单时选择的配置容器包含reCAPTCHA云服务。 您还可以编辑自适应表单属性以更改与表单关联的配置容器。

1. 从组件浏览器中，将&#x200B;**[!UICONTROL Captcha]**&#x200B;组件拖放到自适应表单上。

   >[!NOTE]
   >
   >不支持在自适应表单中使用多个Captcha组件。 此外，不建议在标记为延迟加载的面板或片段中使用CAPTCHA。

   >[!NOTE]
   >
   >验证码对时间敏感，大约一分钟后过期。 因此，建议将Captcha组件放在自适应表单中“提交”按钮之前。

1. 选择您添加的Captcha组件，然后点按![cmppr](assets/cmppr.png)以编辑其属性。
1. 指定CAPTCHA小组件的标题。 默认值为&#x200B;**Captcha**。 如果不希望显示标题，请选择&#x200B;**[!UICONTROL 隐藏标题]**。
1. 从&#x200B;**[!UICONTROL Captcha服务]**&#x200B;下拉列表中，如果按照Google](#google-recaptcha)的ReCAPTCHA服务中的[所述配置了reCAPTCHA服务，请选择&#x200B;**[!UICONTROL reCaptcha]**&#x200B;以启用reCAPTCHA服务。 从设置下拉列表中选择配置。 此外，为reCAPTCHA小组件选择大小为&#x200B;**[!UICONTROL Normal]**&#x200B;或&#x200B;**[!UICONTROL Compact]**。

   >[!NOTE]
   >
   >请勿从Captcha服务下拉列表中选择&#x200B;**[!UICONTROL Default]**，因为默认的AEM CAPTCHA服务已弃用。

1. 保存属性。

reCAPTCHA服务在自适应表单上启用。 您可以预览表单并查看CAPTCHA正常工作。
