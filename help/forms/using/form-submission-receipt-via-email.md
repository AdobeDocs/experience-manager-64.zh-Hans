---
title: 通过电子邮件发送表单提交确认
seo-title: 通过电子邮件发送表单提交确认
description: AEM Forms允许您配置电子邮件提交操作，在用户提交表单时向其发送确认。
seo-description: AEM Forms允许您配置电子邮件提交操作，在用户提交表单时向其发送确认。
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 1%

---


# 通过电子邮件发送表单提交确认 {#sending-a-form-submission-acknowledgement-via-email}

## 自适应表单数据提交 {#adaptive-form-data-submission}

自适应表单为将表单数据提交到不同端点提 [供了多](/help/forms/using/configuring-submit-actions.md) 个现成的提交操作工作流。

例如，“电子邮件 **操作** ”提交操作在成功提交自适应表单时发送电子邮件。 还可以将其配置为发送电子邮件中的表单数据和PDF。

本文详细介绍了在自适应表单上启用“电子邮件”操作的步骤及其提供的不同配置。

>[!NOTE]
>
>您还可以使用“电 **子邮件PDF** ”动作以PDF附件的形式通过电子邮件发送完成的表单。 此操作的可用配置选项与“电子邮件”操作的可用选项相同。 “通过电子邮件发送PDF”操作仅对基于XFA的自适应表单可用

## Email action {#email-action}

使用“电子邮件”操作，作者可以在自适应表单成功提交时自动向一个或多个收件人发送电子邮件。

>[!NOTE]
>
>要使用电子邮件操作，您需要按照配置邮件服务中的说明配 [置AEM邮件服务](/help/sites-administering/notification.md#configuring-the-mail-service)。

### 在自适应表单上启用电子邮件操作 {#enabling-email-action-on-an-adaptive-form}

1. 在编辑模式下打开自适应表单。

1. 单 **击** “自适应表 **单”工具栏的** 开始旁边的“编辑”。

   此时将打开编辑组件对话框。

   ![自适应表单的编辑组件对话框](assets/start_of_adp_form.png)

1. 选择提 **交操作** 选项卡，并从提 **交操作下拉** 列表中选择电子邮件操作。

   该选项卡显示用于为当前表单配置电子邮件操作的选项。

   ![“提交操作”选项卡](assets/dialog.png)

1. 在“邮件收件人”、“抄送”和“密件抄送”字段中指定有效的电子邮件ID。

   在“主题”和“电子邮件”模板字段中分别指定电子邮件的主题和正文。

   您还可以在字段中指定变量占位符，在这种情况下，当最终用户成功提交表单时，将处理字段的值。 有关详细信息，请参 [阅使用自适应表单字段名称动态创建电子邮件内容](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p)。

   如果表单包含文件附件，并且您希望将这些文件附加到电子邮件中，请选择“包含附件”。

   >[!NOTE]
   >
   >如果选择“电子邮 **件PDF”动作**，则必须选择“包括附件”选项。

1. 单击&#x200B;**确定**&#x200B;以保存更改。

### 使用自适应表单字段名称动态创建电子邮件内容 {#using-adaptive-form-field-names-to-dynamically-create-email-content}

自适应表单中的字段名称称为占位符，用户提交表单后，将替换为该字段的值。

在“电子邮件操作”选项卡中，您可以使用在执行操作时处理的占位符。 这意味着用户提交表单时会生成电子邮件的标题（如Mailto、CC、密送、主题）。

要定义占位符，请在“提 `${<field name>}` 交操作”选项卡的字段中指定。

例如，如果表单包含用 **于捕获用户电子邮** 件ID的名为的“电子邮件地址”字段 `email_addr`，则可以在“邮件到”、“抄送”或“密件抄送”字段中指定以下内容。

`${email_addr}`

当用户提交表单时，将向表单字段中输入的电子邮件ID `email_addr` 发送电子邮件。

>[!NOTE]
>
>您可以在字段的“编辑”对话 **框中** ，找到字段的名称。

变量占位符还可用于“主题” **和“电子** 邮 **件”模板字段** 。

例如：

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>可重复面板中的字段不能用作变量占位符。

