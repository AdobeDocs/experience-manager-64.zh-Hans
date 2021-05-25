---
title: 将Adobe Sign与AEM Forms集成
seo-title: 将Adobe Sign与AEM Forms集成
description: 了解如何配置Adobe Sign for AEM Forms
seo-description: 了解如何配置Adobe Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: 自适应Forms,Adobe Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 0%

---

# 将Adobe Sign与AEM Forms集成{#integrate-adobe-sign-with-aem-forms}

Adobe Sign为自适应表单启用电子签名工作流。 电子签名可改进工作流，以处理法律、销售、工资单、人力资源管理等许多领域的文档。

在典型的Adobe Sign和自适应表单场景中，用户将自适应表单填充到&#x200B;**申请服务**。 例如，信用卡申请和公民福利表。 当用户填写、提交和签署申请表时，该表单将发送给服务提供商以进一步操作。 服务提供商会审核应用程序，并使用Adobe Sign标记已批准的应用程序。 要启用类似的电子签名工作流，您可以将Adobe Sign与AEM Forms集成。

要将Adobe Sign与AEM Forms结合使用，请在AEM云服务中配置Adobe Sign:

## 前提条件 {#prerequisites}

要将Adobe Sign与AEM Forms集成，您需要满足以下条件：

* 活动的[Adobe Sign开发人员帐户。](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* [启用SSL的](/help/sites-administering/ssl-by-default.md)AEM Forms服务器。
* [Adobe Sign API应用程序](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md)。
* Adobe Sign API应用程序的凭据（客户端ID和客户端密钥）。
* 重新配置时，请从创作实例和发布实例中删除现有Adobe Sign配置。
* 对创作实例和发布实例使用[相同的加密密钥](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed)。

## 使用AEM Forms配置Adobe Sign {#configure-adobe-sign-with-aem-forms}

在满足先决条件后，执行以下步骤以在创作实例上使用AEM Forms配置Adobe Sign:

1. 在AEM Forms创作实例上，导航至&#x200B;**工具** ![hammer](assets/hammer.png) > **常规** > **配置浏览器**。
   * 有关更多信息，请参阅[配置浏览器文档](/help/sites-administering/configurations.md)。
1. 在&#x200B;**[!UICONTROL 配置浏览器]**&#x200B;页面上，点按&#x200B;**[!UICONTROL 创建]**。
1. 在&#x200B;**[!UICONTROL 创建配置]**&#x200B;对话框中，为配置指定&#x200B;**[!UICONTROL 标题]**，启用&#x200B;**[!UICONTROL 云配置]**，然后点按&#x200B;**[!UICONTROL 创建]**。 它会为云服务创建一个配置容器。
1. 导航到&#x200B;**工具** ![hammer](assets/hammer.png) > **Cloud Services** > **Adobe Sign**，然后选择您在上述步骤中创建的配置容器。

   >[!NOTE]
   >
   >您可以执行步骤1-4以在容器中创建新配置容器并创建Adobe Sign配置，或使用&#x200B;**工具** ![hammer](assets/hammer.png) > **Cloud Services** > **Adobe Sign**&#x200B;中的现有`global`文件夹。 如果在新配置容器中创建配置，请确保在创建自适应表单时在&#x200B;**[!UICONTROL 配置容器]**&#x200B;字段中指定容器名称。

   >[!NOTE]
   确保云服务配置页面的URL以&#x200B;**HTTPS**&#x200B;开头。 如果没有，则[为AEM Forms服务器启用SSL](/help/sites-administering/ssl-by-default.md)。

1. 在配置页面上，点按&#x200B;**[!UICONTROL 创建]** ，以在AEM Forms中创建Adobe Sign配置。
1. 在&#x200B;**[!UICONTROL 创建Adobe Sign配置]**&#x200B;页面的&#x200B;**[!UICONTROL 常规]**&#x200B;选项卡中，为配置指定&#x200B;**名称**，然后点按&#x200B;**下一步**。 您可以选择指定标题并浏览以选择配置的缩略图。

1. 将当前浏览器窗口中的URL复制到记事本。 需要使用AEM Forms配置Adobe Sign应用程序。

1. 为Adobe Sign应用程序配置OAuth设置：

   1. 打开浏览器窗口并登录到Adobe Sign开发人员帐户。
   1. 选择为AEM Forms配置的应用程序，然后点按为应用程序配置OAuth 。
   1. 在&#x200B;**重定向URL**&#x200B;框中，添加在上一步中复制的HTTPS URL，然后单击&#x200B;**Save**。
   1. 为Adobe Sign应用程序启用以下OAuth设置，然后单击&#x200B;**Save**。
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   有关为Adobe Sign应用程序配置OAuth设置并获取键的分步信息，请参阅[为应用程序](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md)开发人员文档配置oAuth设置。

   ![OAuth配置](assets/oauthconfig_new.png)

1. 返回至&#x200B;**创建Adobe Sign配置**&#x200B;页面。 在&#x200B;**[!UICONTROL Settings]**&#x200B;选项卡中， **[!UICONTROL OAuth URL]**&#x200B;字段提及以下默认URL:

   `https://secure.na1.echosign.com/public/oauth`

   其中：

   **na1** 是指默认的数据库共享。

   您可以修改数据库共享的值。 重新启动服务器，以便能够将新值用于数据库共享。

1. 指定&#x200B;**客户端ID**（也称为应用程序ID）和&#x200B;**客户端密钥**。 选择&#x200B;**为附件启用Adobe Sign还**&#x200B;选项，将附加到自适应表单的文件附加到相应的Adobe Sign文档，以发送该文档进行签名。

   点按&#x200B;**[!UICONTROL 连接到Adobe Sign]**。 提示输入凭据时，请提供创建Adobe Sign应用程序时所用帐户的用户名和密码。

   点按&#x200B;**[!UICONTROL 创建]**&#x200B;以创建Adobe Sign配置。

1. 打开AEM Web Console。 URL为`https://'[server]:[port]'/system/console/configMgr`
1. 打开&#x200B;**Forms Common Configuration Service。**
1. 在&#x200B;**允许**&#x200B;字段中， **选择**&#x200B;所有用户 — 所有用户（匿名或已登录）都可以预览附件、验证和签署表单，然后单击&#x200B;**保存。** 创作实例配置为使用Adobe Sign。
1. 使用[replication](/help/sites-deploying/replication.md)在相应的发布实例上创建相同的配置。

现在，Adobe Sign已与AEM Forms集成，可在自适应表单中使用。 要在自适应表单](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)中使用Adobe Sign服务，请在自适应表单属性中指定上面创建的配置容器。[

## 配置Adobe Sign调度程序以同步签名状态{#configure-adobe-sign-scheduler-to-sync-the-signing-status}

只有在所有签名者完成签名过程后，才会提交启用Adobe Sign的自适应表单。 默认情况下，Adobe Sign计划程序服务将安排在每24小时后检查（轮询）签名者响应。 您可以更改环境的默认间隔。 执行以下步骤以更改默认间隔：

1. 使用管理员凭据登录到AEM Forms服务器，然后导航到&#x200B;**工具** > **操作** > **Web控制台**。

   您还可以在浏览器窗口中打开以下URL:
   `https://[localhost]:'port'/system/console/configMgr`

1. 找到并打开&#x200B;**Adobe Sign配置服务**&#x200B;选项。 在&#x200B;**状态更新调度程序表达式**&#x200B;字段中指定[cron表达式](https://en.wikipedia.org/wiki/Cron#CRON_expression)，然后单击&#x200B;**保存**。 例如，要在每天上午00:00运行配置服务，请在&#x200B;**状态更新调度程序表达式**&#x200B;字段中指定`0 0 0 1/1 * ? *`。

Adobe Sign的同步状态的默认间隔现已更改。

## 相关文章{#related-articles}

* [在自适应表单中使用Adobe Sign](../../forms/using/working-with-adobe-sign.md)
* [将Adobe Sign与AEM Forms结合使用（视频）](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [将Adobe Sign与AEM Forms集成](../../forms/using/adobe-sign-integration-adaptive-forms.md)
