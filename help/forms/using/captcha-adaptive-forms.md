---
title: 在自适应表单中使用CAPTCHA
seo-title: Using CAPTCHA in adaptive forms
description: 了解如何在自适应表单中配置AEM CAPTCHA或Google reCAPTCHA服务。
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in adaptive forms.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: Adaptive Forms
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# 在自适应表单中使用CAPTCHA {#using-captcha-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

CAPTCHA(Completely Automated Public Turing test to tell Computers and Humans Apart)是一种在线交易中常用的程序，用于区分人类和自动程序或机器人。 它会给用户带来挑战并评估用户响应，以确定它是人还是机器人与站点进行交互。 它可阻止用户在测试失败时继续操作，并通过防止机器人发布垃圾邮件或恶意目的，帮助确保在线交易的安全。

AEM Forms支持自适应表单中的CAPTCHA。 您可以使用Google提供的reCAPTCHA服务来实施CAPTCHA。

>[!NOTE]
>
>AEM Forms仅支持reCaptcha v2。 不支持任何其他版本。
>
>在AEM Forms应用程序的离线模式下，不支持自适应表单中的验证码。

## 通过Google配置ReCAPTCHA服务 {#google-recaptcha}

表单作者可以使用Google提供的reCAPTCHA服务在自适应表单中实施CAPTCHA。 它提供高级验证码功能以保护您的网站。 有关reCAPTCHA工作原理的更多信息，请参阅 [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![recapcha](assets/recaptcha.png)

要在AEM Forms中实施reCAPTCHA服务，请执行以下操作：

1. 获取 [reCAPTCHA API密钥对](https://www.google.com/recaptcha/admin) 从Google。 它包括站点密钥和密钥。
1. 为云服务创建配置容器。

   1. 转到 **[!UICONTROL 工具>常规>配置浏览器]**.
      * 请参阅 [配置浏览器文档](/help/sites-administering/configurations.md) 以了解更多信息。
   1. 执行以下操作可为云配置启用全局文件夹，或跳过此步骤以为云服务配置创建和配置其他文件夹。

      1. 在配置浏览器中，选择 **[!UICONTROL 全球]** 文件夹，然后点按 **[!UICONTROL 属性]**.
      1. 在配置属性对话框中，启用 **[!UICONTROL 云配置]**.
      1. 点按 **[!UICONTROL 保存并关闭]** 保存配置并退出对话框。
   1. 在配置浏览器中，点按 **[!UICONTROL 创建]**.
   1. 在创建配置对话框中，指定文件夹的标题并启用 **[!UICONTROL 云配置]**.
   1. 点按 **[!UICONTROL 创建]** 创建云服务配置启用的文件夹。


1. 为reCAPTCHA配置云服务。

   1. 在您的AEM创作实例中，转到 ![工具](assets/tools.png) >  **Cloud Services**.
   1. 点按 **[!UICONTROL reCAPTCHA]**. 此时将打开“配置”页面。 选择在上一步中创建的配置容器，然后点按 **[!UICONTROL 创建]**.
   1. 为reCAPTCHA服务指定名称、站点密钥和密钥，然后点按 **[!UICONTROL 创建]** 创建云服务配置。
   1. 在编辑组件对话框中，指定在步骤1中获取的站点和密钥。 点按 **[!UICONTROL 保存设置]** 然后点按 **[!UICONTROL 确定]** 以完成配置。

   配置reCAPTCHA服务后，即可在自适应表单中使用。 有关更多信息，请参阅 [在自适应表单中使用CAPTCHA](#using-captcha).

## 在自适应表单中使用CAPTCHA {#using-captcha}

要在自适应表单中使用CAPTCHA，请执行以下操作：

1. 在编辑模式下打开自适应表单。

   >[!NOTE]
   >
   >确保在创建自适应表单时选择的配置容器包含reCAPTCHA云服务。 您还可以编辑自适应表单属性以更改与表单关联的配置容器。

1. 在组件浏览器中，拖放 **[!UICONTROL 验证码]** 组件添加到自适应表单。

   >[!NOTE]
   >
   >不支持在自适应表单中使用多个Captcha组件。 此外，不建议在标记为延迟加载的面板或片段中使用CAPTCHA。

   >[!NOTE]
   >
   >验证码对时间敏感，大约一分钟后过期。 因此，建议将Captcha组件放在自适应表单中“提交”按钮之前。

1. 选择您添加的Captcha组件，然后点按 ![cppr](assets/cmppr.png) 以编辑其属性。
1. 指定CAPTCHA小组件的标题。 默认值为 **验证码**. 选择 **[!UICONTROL 隐藏标题]** 如果您不希望显示标题，请执行以下操作：
1. 从 **[!UICONTROL 验证码服务]** 下拉列表，选择 **[!UICONTROL reCaptcha]** 启用reCAPTCHA服务(如果您按照 [ReCAPTCHA服务，由Google提供](#google-recaptcha). 从设置下拉列表中选择配置。 此外，将大小选择为 **[!UICONTROL 正常]** 或 **[!UICONTROL 紧凑]** 用于reCAPTCHA小组件。

   >[!NOTE]
   >
   >不选择 **[!UICONTROL 默认]** 从Captcha服务下拉列表中，作为默认的AEM CAPTCHA服务已弃用。

1. 保存属性。

reCAPTCHA服务在自适应表单上启用。 您可以预览表单并查看CAPTCHA正常工作。
