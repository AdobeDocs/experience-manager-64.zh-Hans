---
title: 通过电子邮件发送表单提交确认
seo-title: Sending a form submission acknowledgement via email
description: AEM Forms允许您配置电子邮件提交操作，以在提交表单时向用户发送确认。
seo-description: AEM Forms allows you to configure the email submit action that sends an acknowledgement to a user on submitting the form.
uuid: 77b3c836-6011-48bd-831c-ebc214218efb
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 7ffe6317-174b-4d80-9ac6-9bfb5eed7e29
exl-id: e850d2a5-cb5f-4bd4-81dd-57951923b6d3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 1%

---

# 通过电子邮件发送表单提交确认 {#sending-a-form-submission-acknowledgement-via-email}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 自适应表单数据提交 {#adaptive-form-data-submission}

自适应表单提供了多个现成功能 [提交操作](/help/forms/using/configuring-submit-actions.md) 用于将表单数据提交到不同端点的工作流。

例如， **电子邮件操作** 提交操作会在成功提交自适应表单时发送电子邮件。 还可以将其配置为在电子邮件中发送表单数据和PDF。

本文详细介绍了对自适应表单及其提供的不同配置启用“电子邮件”操作的步骤。

>[!NOTE]
>
>您还可以使用 **电子邮件PDF操作** 通过电子邮件作为PDF附件发送填写的表单。 此操作可用的配置选项与Email操作可用的选项相同。 “电子邮件PDF”操作仅适用于基于XFA的自适应表单

## 电子邮件操作 {#email-action}

通过“电子邮件”操作，作者可以在成功提交自适应表单时自动向一个或多个收件人发送电子邮件。

>[!NOTE]
>
>要使用Email操作，您需要按照 [配置邮件服务](/help/sites-administering/notification.md#configuring-the-mail-service).

### 在自适应表单上启用电子邮件操作 {#enabling-email-action-on-an-adaptive-form}

1. 在编辑模式下打开自适应表单。

1. 单击 **编辑** 旁边 **自适应表单的开头** 工具栏。

   此时将打开编辑组件对话框。

   ![自适应表单的编辑组件对话框](assets/start_of_adp_form.png)

1. 选择 **提交操作** 选项卡 **电子邮件操作** 从提交操作下拉列表中。

   选项卡显示用于为当前表单配置Email操作的选项。

   ![“提交操作”选项卡](assets/dialog.png)

1. 在“邮件到”、“抄送”和“密送”字段中指定有效的电子邮件ID。

   分别在主题和电子邮件模板字段中指定电子邮件的主题和正文。

   您还可以在字段中指定变量占位符，在这种情况下，当最终用户成功提交表单时，将处理字段的值。 有关更多信息，请参阅 [使用自适应表单字段名称动态创建电子邮件内容](/help/forms/using/form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   如果表单包含文件附件，并且您想要在电子邮件中附加这些文件，请选择“包含附件”。

   >[!NOTE]
   >
   >如果您选择 **电子邮件PDF操作**，则必须选择包含附件选项。

1. 单击 **确定** 以保存更改。

### 使用自适应表单字段名称动态创建电子邮件内容 {#using-adaptive-form-field-names-to-dynamically-create-email-content}

自适应表单中的字段名称称为占位符，在用户提交表单后，将替换为该字段的值。

在电子邮件操作选项卡中，您可以使用在执行操作时处理的占位符。 这意味着用户提交表单时会生成电子邮件的标题（如Mailto、CC、密送、主题）。

要定义占位符，请指定 `${<field name>}` （在“提交操作”选项卡的字段中）。

例如，如果表单包含 **电子邮件地址** 字段，已命名 `email_addr`，要捕获用户的电子邮件ID，您可以在“邮件”、“抄送”或“密送”字段中指定以下内容。

`${email_addr}`

当用户提交表单时，会向在 `email_addr` 字段。

>[!NOTE]
>
>您可以在 **编辑** 对话框。

变量占位符也可用于 **主题** 和 **电子邮件模板** 字段。

例如：

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>可重复面板中的字段不能用作变量占位符。
