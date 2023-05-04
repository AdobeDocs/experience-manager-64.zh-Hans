---
title: 将Acrobat Sign与AEM Forms集成
seo-title: Integrate Acrobat Sign with AEM Forms
description: 了解如何配置Acrobat Sign for AEM Forms
seo-description: Learn how to configure Acrobat Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Acrobat Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 13%

---

# 将Acrobat Sign与AEM Forms集成 {#integrate-adobe-sign-with-aem-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Acrobat Sign为自适应表单启用电子签名工作流。 电子签名改进了法律、销售、工资单、人力资源管理和其他许多方面的文档的处理工作流。

在典型的Acrobat Sign和自适应表单场景中，用户将自适应表单填充到 **申请服务**. 例如，信用卡申请表和公民权益表。在用户填写、签署和提交申请表后，该表将发送给服务提供商以执行后续操作。服务提供商会审核应用程序，并使用Acrobat Sign标记已批准的应用程序。 要启用类似的电子签名工作流，您可以将Acrobat Sign与AEM Forms集成。

要将Acrobat Sign与AEM Forms结合使用，请在AEM云服务中配置Acrobat Sign:

## 前提条件 {#prerequisites}

要将Acrobat Sign与AEM Forms集成，您需要满足以下条件：

* 活动 [Acrobat Sign开发人员帐户。](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)
* 安 [启用SSL](/help/sites-administering/ssl-by-default.md) AEM Forms服务器。
* 安 [Acrobat Sign API应用程序](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Acrobat Sign API应用程序的凭据（客户端ID和客户端密钥）。
* 重新配置时，请从创作实例和发布实例中删除现有Acrobat Sign配置。
* 针对创作实例和发布实例，使用[相同的加密密钥](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed)。

## 使用Acrobat Sign配置AEM Forms {#configure-adobe-sign-with-aem-forms}

在满足先决条件后，执行以下步骤以在创作实例上使用AEM Forms配置Acrobat Sign:

1. 在AEM Forms创作实例上，导航到 **工具** ![锤子](assets/hammer.png) > **常规** > **配置浏览器**.
   * 请参阅 [配置浏览器文档](/help/sites-administering/configurations.md) 以了解更多信息。
1. 在 **[!UICONTROL 配置浏览器]** 页面，点按 **[!UICONTROL 创建]**.
1. 在 **[!UICONTROL 创建配置]** 对话框，指定 **[!UICONTROL 标题]** 对于配置，请启用 **[!UICONTROL 云配置]**，然后点按 **[!UICONTROL 创建]**. 它会为云服务创建一个配置容器。
1. 导航到 **工具** ![锤子](assets/hammer.png) > **Cloud Services** > **Acrobat Sign** ，然后选择在上述步骤中创建的配置容器。

   >[!NOTE]
   >
   >您可以执行步骤1-4以在容器中创建新配置容器并创建Acrobat Sign配置，也可以使用现有 `global` 文件夹 **工具** ![锤子](assets/hammer.png) > **Cloud Services** > **Acrobat Sign**. 如果在新配置容器中创建配置，请确保在 **[!UICONTROL 配置容器]** 字段。

   >[!NOTE]
   确保云服务配置页面的URL以开头 **HTTPS**. 如果没有， [启用SSL](/help/sites-administering/ssl-by-default.md) (对于AEM Forms服务器)。

1. 在配置页面上，点按 **[!UICONTROL 创建]** 在AEM Forms中创建Acrobat Sign配置。
1. 在 **[!UICONTROL 常规]** 选项卡 **[!UICONTROL 创建Acrobat Sign配置]** 页面，指定 **名称** ，然后点按 **下一个**. 您可以选择指定标题并浏览以选择配置的缩略图。

1. 将当前浏览器窗口中的 URL 复制到记事本。需要使用AEM Forms配置Acrobat Sign应用程序。

1. 为Acrobat Sign应用程序配置OAuth设置：

   1. 打开浏览器窗口并登录到Acrobat Sign开发人员帐户。
   1. 选择为AEM Forms配置的应用程序，然后点按为应用程序配置OAuth 。
   1. 在 **重定向URL** 框中，添加在上一步中复制的HTTPS URL，然后单击 **保存**.
   1. 为Acrobat Sign应用程序启用以下OAuth设置，然后单击 **保存**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   有关为Acrobat Sign应用程序配置OAuth设置并获取键的分步信息，请参阅 [为应用程序配置oAuth设置](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) 开发人员文档。

   ![OAuth 配置](assets/oauthconfig_new.png)

1. 返回到 **创建Acrobat Sign配置** 页面。 在 **[!UICONTROL 设置]** 选项卡 **[!UICONTROL OAuth URL]** 字段会提及以下默认URL:

   `https://secure.na1.echosign.com/public/oauth`

   其中：

   **na1** 指默认数据库分片。

   您可以修改数据库分片的值。重新启动服务器，以便能够将新值用于数据库共享。

1. 指定 **客户端ID** （也称为应用程序ID）和 **客户端密钥**. 选择 **还为附件启用Acrobat Sign** 选项，将附加到自适应表单的文件附加到相应的Acrobat Sign文档，以进行签名。

   点按 **[!UICONTROL 连接到Acrobat Sign]**. 提示输入凭据时，请提供创建Acrobat Sign应用程序时所用帐户的用户名和密码。

   点按 **[!UICONTROL 创建]** 创建Acrobat Sign配置。

1. 打开AEM Web Console。 URL为 `https://'[server]:[port]'/system/console/configMgr`
1. 打开 **Forms通用配置服务。**
1. 在 **允许** 字段， **选择** 所有用户 — 所有用户（匿名或已登录）都可以预览附件、验证和签名表单，然后单击 **保存。** 创作实例配置为使用Acrobat Sign。
1. 使用 [复制](/help/sites-deploying/replication.md) 以在相应的发布实例上创建相同的配置。

现在，Acrobat Sign已与AEM Forms集成，可在自适应表单中使用。 至 [在自适应表单中使用Acrobat Sign服务](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form)，在自适应表单属性中指定上面创建的配置容器。

## 配置Acrobat Sign调度程序以同步签名状态 {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

只有在所有签名者完成签名过程后，才会提交启用Acrobat Sign的自适应表单。 默认情况下，Acrobat Sign计划程序服务将安排在每24小时后检查（轮询）签名者响应。 您可以为您的环境更改此默认间隔。执行以下步骤以更改默认间隔：

1. 使用管理员凭据登录AEM Forms服务器，然后导航到 **工具** > **操作** > **Web控制台**.

   您还可以在浏览器窗口中打开以下URL:
   `https://[localhost]:'port'/system/console/configMgr`

1. 找到并打开 **Acrobat Sign配置服务** 选项。 指定 [cron表达式](https://en.wikipedia.org/wiki/Cron#CRON_expression) 在 **状态更新调度程序表达式** 字段，单击 **保存**. 例如，要每天00:00 am运行配置服务，请指定 `0 0 0 1/1 * ? *` 在 **状态更新调度程序表达式** 字段。

Acrobat Sign的同步状态的默认间隔现已更改。

## 相关文章 {#related-articles}

* [在自适应表单中使用Acrobat Sign](../../forms/using/working-with-adobe-sign.md)
* [将Acrobat Sign与AEM Forms结合使用（视频）](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [将Acrobat Sign与AEM Forms集成](../../forms/using/adobe-sign-integration-adaptive-forms.md)
