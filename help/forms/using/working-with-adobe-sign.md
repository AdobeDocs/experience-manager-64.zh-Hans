---
title: 在自适应表单中使用Acrobat Sign
seo-title: Using Acrobat Sign in an adaptive form
description: 为自适应表单启用电子签名(Acrobat Sign)工作流，以自动执行签名工作流，简化单个和多签名流程，以及通过移动设备对表单进行电子签名。
seo-description: Enable e-signature (Acrobat Sign) workflows for an adaptive form to automate signing workflows, simplify single and multi-signature processes, and to electronically sign forms from mobile devices.
uuid: 9c65dc44-c1a5-44df-8659-6efbe347575b
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 29fc297e-0a95-4d2a-bfe6-5676d53624db
noindex: true
feature: Adaptive Forms, Acrobat Sign
exl-id: 5922ea6e-8be9-4e65-89a6-67b6cc12c4ee
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3598'
ht-degree: 0%

---

# 在自适应表单中使用Acrobat Sign {#using-adobe-sign-in-an-adaptive-form}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

为自适应表单启用电子签名(Acrobat Sign)工作流，以自动执行签名工作流，简化单个和多签名流程，以及通过移动设备对表单进行电子签名。

Acrobat Sign为自适应表单启用电子签名工作流。 电子签名可改进工作流程，以处理法律、销售、工资、人力资源管理等领域的文档。

在典型的Acrobat Sign和自适应表单场景中，用户填充自适应表单以申请服务。 例如，抵押贷款和信用卡申请要求所有借款人和共同申请人签名。 要为类似情景启用电子签名工作流，您可以将Acrobat Sign与AEM Forms集成。 还有一些示例，您可以使用Acrobat Sign执行以下操作：

* 通过完全自动化的建议书、报价和合同流程，与任何设备达成交易。
* 更快地完成人力资源流程，并为员工提供数字体验。
* 缩短合同周期并更快地载入您的供应商。
* 创建可自动处理常见流程的数字工作流。

Acrobat Sign与AEM Forms的集成支持：

* 单用户和多用户签名工作流
* 顺序和同时的签名工作流
* 表单内和表单外的签名体验
* 以匿名或已登录用户的身份对表单进行签名
* 动态签名流程(与AEM Forms工作流集成)
* 通过知识库、电话和社交用户档案进行身份验证

了解 [将Acrobat Sign与自适应表单结合使用的最佳实践](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684) 以创建更好的签名体验。

## 前提条件 {#prerequisites}

在自适应表单中使用Acrobat Sign之前：

* 确保将AEM Forms云服务配置为使用Acrobat Sign。 有关详细信息，请参阅 [将Acrobat Sign与AEM Forms集成](/help/forms/using/adobe-sign-integration-adaptive-forms.md).
* 请准备好签名者列表。 您至少需要每个签名者的电子邮件地址。

## 为自适应表单配置Acrobat Sign {#configure-adobe-sign-for-an-adaptive-form}

执行以下步骤来配置自适应表单的Acrobat Sign:

1. [编辑自适应表单属性以用于Acrobat Sign](#enableadobesign)
1. [将Acrobat Sign字段添加到自适应表单](#addadobesignfieldstoanadaptiveform)
1. [为自适应表单启用Acrobat Sign](#enableadobsignforanadaptiveform)
1. [为自适应表单选择Acrobat SignCloud Service](#selectadobesigncloudserviceforanadaptiveform)

1. [将Acrobat Sign签名者添加到自适应表单](#addsignerstoanadaptiveform)
1. [为自适应表单选择提交操作](#selectsubmitactionforanadaptiveform)

![signer-details](assets/signer-details.png)

### 编辑自适应表单属性以用于Acrobat Sign {#enableadobesign}

为现有或新的自适应表单配置Acrobat Sign的自适应表单属性。

[为Acrobat Sign创建自适应表单](/help/forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) 介绍创建基本自适应表单的步骤。 请参阅 [创建自适应表单](/help/forms/using/creating-adaptive-form.md) 以了解创建自适应表单时可用的其他选项。

#### 为Acrobat Sign创建自适应表单 {#create-an-adaptive-form-for-adobe-sign}

执行以下步骤为Acrobat Sign创建自适应表单：

1. 导航到 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms和文档]**.
1. 点按 **[!UICONTROL 创建]** 选择 **[!UICONTROL 自适应表单]**. 此时会显示模板列表。 选择模板并点按 **[!UICONTROL 下一个]**.
1. 在 **[!UICONTROL 基本]** 选项卡：

   1. 指定 **名称** 和 **标题** ，用于自适应表单。
   1. 选择 [配置容器](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) 在配置Acrobat Sign与AEM Forms时创建。

      >[!NOTE]
      >
      >的 **[!UICONTROL Acrobat SignCloud Service]** 下拉列表显示您在此字段中选择的配置容器中配置的云服务。 的 **[!UICONTROL Acrobat SignCloud Service]** 下拉列表在 **[!UICONTROL 电子签名]** 自适应表单属性的部分 **[!UICONTROL 启用Acrobat Sign]** 选项。

1. 在 **[!UICONTROL 表单模型]** 选项卡，选择以下选项之一：

   * 选择 **[!UICONTROL 将表单模板关联为记录文档模板]** 选项，然后选择记录文档模板。 如果您使用基于表单模板的自适应表单，则发送进行签名的文档将仅显示基于关联表单模板的字段。 它不会显示自适应表单的所有字段。
   * 选择 **[!UICONTROL 生成记录文档]** 选项。 如果使用启用了“记录文档”选项的自适应表单，则发送以供签名的文档将显示自适应表单的所有字段。

1. 点按 **[!UICONTROL 创建。]** 将创建启用符号的自适应表单，该表单可用于添加Acrobat Sign字段。

#### 编辑自适应表单以用于Acrobat Sign {#editafsign}

执行以下步骤以在现有自适应表单中使用Acrobat Sign:

1. 导航到 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]**> **[!UICONTROL Forms和文档]**.
1. 选择自适应表单并点按 **[!UICONTROL 属性]**.
1. 在 **[!UICONTROL 基本]** 选项卡，选择 [配置容器](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) 在配置Acrobat Sign与AEM Forms时创建。
1. 在 **[!UICONTROL 表单模型]** 选项卡，选择以下选项之一：

   * 选择 **[!UICONTROL 将表单模板关联为记录文档模板]** 选项，然后选择记录文档模板。 如果您使用基于表单模板的自适应表单，则发送进行签名的文档将仅显示基于关联表单模板的字段。 它不会显示自适应表单的所有字段。
   * 选择 **[!UICONTROL 生成记录文档]** 选项。 如果使用启用了“记录文档”选项的自适应表单，则发送以供签名的文档将显示自适应表单的所有字段。

1. 点按 **[!UICONTROL 保存并关闭]**. 自适应表单已为Acrobat Sign启用。

### 将Acrobat Sign字段添加到自适应表单 {#addadobesignfieldstoanadaptiveform}

Acrobat Sign具有可放置在自适应表单上的各个字段。 这些字段接受各种类型的数据（如签名、缩写、公司或标题），并帮助在签名期间收集额外信息以及签名。 您可以使用Acrobat Sign块组件将Acrobat Sign字段放置在自适应表单中的不同位置。

执行以下步骤，向自适应表单添加字段并自定义与这些字段相关的各种选项：

1. 拖放 **Acrobat Sign块** 组件从组件浏览器转换到自适应表单。 Acrobat Sign块组件具有所有受支持的Acrobat Sign字段。 默认情况下，它会添加 **签名** 字段。

   ![符号块](assets/sign-block.png)

   默认情况下，Acrobat Sign块在已发布的自适应表单中不可见。 它仅在签名文档中可见。 您可以从Acrobat Sign块组件的属性中更改Acrobat Sign块的可见性。

   >[!NOTE]
   >
   >* 要在自适应表单中使用Acrobat Sign块，并非必须使用Acrobat Sign。 如果不使用Acrobat Sign块并为签名者添加字段，则默认签名字段将显示在签名文档的底部。
   >* 仅将Acrobat Sign块用于自动生成记录文档的自适应表单。 如果您使用自定义XDP来生成记录文档或基于表单模板的自适应表单，则不需要Acrobat Sign块。


1. 选择 **Acrobat Sign块** 组件，然后点按 **编辑** ![aem_6_3_edit](assets/aem_6_3_edit.png) 图标。 它显示用于添加字段和设置字段外观格式的选项。

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** 选择并添加Acrobat Sign字段。 **B.** 将Acrobat Sign块展开为全屏视图

1. 点按 **Acrobat Sign字段** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) 图标。 它显示用于选择和添加Acrobat Sign字段的选项。

   展开 **类型** 下拉字段以选择Acrobat Sign字段，然后点按完成 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) 图标将选定字段添加到Acrobat Sign块。 的 **类型** 下拉字段包括“签名”、“签名者信息”和“数据”字段类型。 Acrobat Sign与AEM Forms支持的集成仅在“类型”下拉框中列出。 有关Acrobat Sign字段的详细信息，请参阅 [Acrobat Sign文档](https://helpx.adobe.com/sign/help/field-types.html).

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   必须为字段提供唯一的名称。 您还可以选择必需选项来将字段标记为必填。 除 **名称** 和 **必需** 选项，则某些Acrobat Sign字段会有更多选项。 例如，蒙版和多行。 此外，无论字段位于同一个Acrobat Sign块还是不同的Acrobat Sign块中，都为每个字段指定唯一的名称。

### 为自适应表单启用Acrobat Sign {#enableadobsignforanadaptiveform}

开箱即用地表示，没有为自适应表单启用Acrobat Sign。 请执行以下步骤以启用它：

1. 在内容浏览器中，点按 **表单容器**，然后点按 **配置** ![配置](assets/configure.png) 图标。 它会打开属性浏览器并显示自适应表单容器属性。
1. 在属性浏览器中，展开 **电子签名** 折叠面板，然后选择 **启用Acrobat Sign** 选项。 它为Acrobat Sign提供了自适应表单。

### 选择Acrobat SignCloud Service和签名顺序 {#selectadobesigncloudserviceforanadaptiveform}

您可以为AEM Forms实例配置多个Acrobat Sign服务。 建议为每个功能（人力资源、财务等）分别提供一组服务。 它使跟踪和报告已签名文档变得更轻松。 例如，银行有多个部门。 您可以为每个部门单独配置以更好地跟踪文档。

文档还可以有多个签名者。 例如，信用卡申请可以有多个申请人。 银行在开始处理申请之前需要所有申请人的签名。 对于多签名者方案，您可以选择按顺序或同时顺序对文档进行签名。

执行以下步骤以选择云服务和签名顺序：

![云服务](assets/cloud-service.png)

1. 在内容浏览器中，点按 **表单容器**，然后点按 **配置** ![配置](assets/configure.png) 图标。 它会打开属性浏览器并显示自适应表单容器属性。
1. 在属性浏览器中，展开 **电子签名** 折叠面板，然后选择 **启用Acrobat Sign** 选项。 它为Acrobat Sign提供了自适应表单。
1. 从已配置的Acrobat SignCloud Services列表中选择云服务。

   如果 **Acrobat SignCloud Service** 列表为空，请遵循 [使用Acrobat Sign配置AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) 用于配置服务的文章。

   下拉列表列出了 `global` 工具>中的文件夹 **[!UICONTROL Cloud Services]** > **[!UICONTROL Acrobat Sign]**. 此外，该下拉列表还列出了您在 **[!UICONTROL 配置容器]** 字段。

1. 从 **签名者可以签名** 对话框。 Acrobat Sign歌手可以签署自适应表格 **按顺序**  — 一个接一个的签名者，或 **同时**  — 按任意顺序排列。

   按顺序，一个签名者每次接收用于签名的表单。 签名者完成对文档的签名后，表单会发送给下一位签名者，依此类推。

   同时，多个签名者一次可以签署一个表单。

1. [将签名者添加到自适应表单](#addsignerstoanadaptiveform) 然后点按完成图标以保存更改。

### 将签名者添加到自适应表单 {#addsignerstoanadaptiveform}

自适应表单只能有一个或多个签名者。 添加签名者时，您还可以为签名者配置身份验证详细信息。 您还可以选择表单填充者和歌手是否是同一个人。 执行以下步骤以添加和提供有关签名者的各种详细信息：

1. 在内容浏览器中，点按 **表单容器**，然后点按 **配置** ![配置](assets/configure.png) 图标。 它会打开具有自适应表单容器属性的属性浏览器。
1. 在属性浏览器中，展开 **电子签名** 折叠面板，然后选择 **启用Acrobat Sign** 选项。 它为Acrobat Sign提供了自适应表单。
1. 点按 **添加签名者** 在 **签名者配置。** 它会向自适应表单中添加签名者。 您可以向自适应表单中添加多个Acrobat Sign签名者。
1. ![电话详细信息](assets/phone-details.png)

   单击 **编辑** ![aem_6_3_edit](assets/aem_6_3_edit.png) 图标以指定有关签名者的以下信息：

   * **标题：** 指定标题以唯一标识签名者。
   * **签名者和填写表单的人是否相同？** 选择 **是**，如果表单填写者和第一个签名者是同一个人。 如果选项设置为 **不，** 然后，请勿在自适应表单中使用签名步骤组件。 如果表单包含签名步骤组件，则字段会自动设置为“是”。
   * **签名者电子邮件地址：** 指定签名者的电子邮件地址。 签名者将收到指定电子邮件地址上的待签名文档/表单。 您可以选择使用在表单字段中提供的电子邮件地址、登录用户的AEM用户配置文件中，或手动输入电子邮件地址。 这是强制性步骤。 另请注意，如果您只配置了一名签名者，请确保该签名者的电子邮件地址与用于配置AEM云服务的Acrobat Sign帐户不相同。
   * **签名者身份验证方法：** 指定在打开表单进行签名之前验证用户的方法。 您可以在电话、知识库和基于社交身份的身份验证之间进行选择。

   >[!NOTE]
   >
   >* 默认情况下，基于社交身份的身份验证提供了使用Facebook、Google和LinkedIn进行身份验证的选项。 您可以联系Acrobat Sign支持以启用其他社交身份验证提供程序。


   * **Acrobat Sign字段填写或签名：** 为签名者选择Acrobat Sign字段。 自适应表单可以有多个Acrobat Sign字段。 您可以选择为签名者启用特定字段。 字段会显示所有可用的Acrobat Sign块。 选择块时，该块的所有字段都将被选中。 您可以使用X图标取消选择字段。

   ![signer-details-1](assets/signer-details-1.png)

   上图有两个示例Acrobat Sign块：个人信息和办公室详细信息

   点按完成 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) 图标。 添加并配置签名者。

### 为自适应表单选择提交操作 {#selectsubmitactionforanadaptiveform}

在您将Acrobat Sign字段添加到自适应表单后，从表单容器中启用Acrobat Sign，选择Acrobat SignCloud Service，然后添加Acrobat Sign签名者，为自适应表单选择适当的提交操作。 有关自适应表单提交操作的详细信息，请参阅 [配置提交操作](/help/forms/using/configuring-submit-actions.md).

此外，只有在所有签名者签署表单后，才会提交启用Acrobat Sign的自适应表单。 您可以在表单门户的“待签名”部分找到部分签名的表单。 Acrobat Sign配置服务在 [常规间隔](/help/forms/using/adobe-sign-integration-adaptive-forms.md) 以验证签名的状态。 如果所有签名者都完成了对表单的签名，则会启动提交操作服务并提交表单。 如果您使用自定义提交操作且表单使用Acrobat Sign，请更新自定义提交操作以使用提交操作服务。

>[!NOTE]
>
>自适应表单的数据会临时存储在Forms Portal中。 建议使用 [Forms门户的自定义存储](/help/forms/using/configuring-draft-submission-storage.md). 它可确保PII（个人身份信息）数据不存储到AEM服务器上。

您的表单签名体验已准备就绪。 您可以预览表单以验证签名体验。 在发布的表单上，当签名者收到通过电子邮件进行签名的表单时，会显示Acrobat Sign块字段。 此体验也称为表单外签名体验。 您还可以为第一位签名者配置表单内签名体验，有关详细步骤，请参阅 [创建表单内签名体验](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience).

## 为自适应表单配置云签名 {#configure-cloud-signatures-for-an-adaptive-form}

基于云的数字签名或远程签名是新一代的数字签名，可跨桌面、移动设备和Web使用，并满足签名者身份验证的最高级别合规性和保证。 您可以使用基于云的数字签名对自适应表单进行签名。

之后 [编辑自适应表单属性Acrobat Sign](#enableadobesign)，请执行以下步骤以将云签名字段添加到自适应表单：

1. 拖放 **Acrobat Sign块** 组件从组件浏览器转换到自适应表单。 Acrobat Sign块组件具有所有受支持的Acrobat Sign字段。 默认情况下，它会添加 **签名** 字段。

   ![符号块](assets/sign-block.png)

1. 选择 **Acrobat Sign块** 组件，然后点按 **编辑** ![aem_6_3_edit](assets/aem_6_3_edit.png) 图标。 它显示用于添加字段和设置字段外观格式的选项。

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **A.** 选择并添加Acrobat Sign字段。 **B.** 将Acrobat Sign块展开为全屏视图

1. 点按 **Acrobat Sign字段** ![aem_6_3_adobesign](assets/aem_6_3_adobesign.png) 图标。 它显示用于选择和添加Acrobat Sign字段的选项。

   展开 **类型** 要选择的下拉字段 **数字签名** 并点按完成 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) 图标将选定字段添加到Acrobat Sign块。

   ![digital_signatures](assets/digital_signatures.png)

   必须为字段提供唯一的名称。

   使用以下方法将数字签名应用于自适应表单：

   * 云签名：使用 [数字ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html) 由信任服务提供商托管。
   * Adobe Acrobat或Reader:使用Adobe Acrobat或Reader下载并打开文档，以使用智能卡、USB令牌或基于文件的数字ID进行签名。

   将云签名字段添加到自适应表单后，请执行以下步骤以完成配置过程：

   * [为自适应表单启用Acrobat Sign](#enableadobsignforanadaptiveform)
   * [为自适应表单选择Acrobat SignCloud Service](#selectadobesigncloudserviceforanadaptiveform)
   * [将Acrobat Sign签名者添加到自适应表单](#addsignerstoanadaptiveform)
   * [为自适应表单选择提交操作](#selectsubmitactionforanadaptiveform)


## 创建表单内签名体验 {#create-in-form-signing-experience}

用户在填写表单时还可以对自适应表单进行签名。 此体验也称为表单内签名体验。 表单内签名体验仅适用于多个签名者环境中的第一个歌手。 执行以下步骤为自适应表单创建表单内签名体验：

1. [添加和配置签名步骤组件](#add-and-configure-the-signature-step-component).
1. [添加摘要步骤组件](#configure-the-thank-you-page-or-summary-step-component).

![表单签名体验](assets/in-form-signing-experience.png)

### 添加和配置签名步骤组件 {#add-and-configure-the-signature-step-component}

使用“签名步骤”组件提供一个用于以电子方式对填写的表单进行签名的区域。 呈现包含签名步骤组件的部分后，会显示已填写表单的可签名PDF版本。 签名步骤组件占用表单的全宽。 建议在包含签名步骤组件的部分上不要包含任何其他组件。

执行以下步骤以配置签名步骤组件：

1. 拖放 **签名步骤** 组件。
1. 选择新添加的签名步骤组件，然后点按 **配置** ![配置](assets/configure.png) 图标。 它会打开属性浏览器并显示签名步骤属性。 配置以下属性：

   * **元素名称**:指定组件的名称。
   * **标题：** 指定组件的唯一标题。
   * **模板消息：** 指定加载签名PDF时要显示的消息。 Acrobat Sign服务需要一些时间来准备和加载签名PDF。
   * **签名服务：** 选择 **Acrobat Sign** 选项。
   * **使用旧版电子签名组件**:如果您在 [AEM Forms Workspace](/help/forms/using/introduction-html-workspace.md)、 AEM Forms应用程序或基础自适应表单具有旧版电子签名组件时，请选择 **使用旧版电子签名组件** 选项。
   * **配置**:选择配置(Acrobat SignCloud Service)。 下拉框仅在 **使用旧版电子签名组件** 选项。

   点按完成 ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) 图标以保存更改。

   ![签名步骤](assets/signature-step.png)

   >[!NOTE]
   >
   >* 当您拖放 **[!UICONTROL 签名步骤]** 组件， **[!UICONTROL 签名者和填写表单的人是否相同？]** 选项自动设置为 **是**. 需要保持表单正常工作。
   >* Acrobat Sign启用的自适应表单不支持使用签名步骤组件在部分或面板上使用提交按钮。 您可以在手动提交的“签名”步骤之后添加摘要步骤，或在使用 [Acrobat Sign配置服务](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status).


### 配置感谢页面或摘要步骤组件 {#configure-the-thank-you-page-or-summary-step-component}

的 **摘要步骤** 组件会自动提交表单，在自定义的“摘要”页面中填充信息，并显示已提交表单的摘要。 它还会获取返回图中的所需信息。 摘要步骤组件具有可用于表单的全宽。 建议在包含摘要步骤组件的部分上不要包含任何其他组件。

现在，表单中的签名体验已准备就绪。 您可以预览表单以验证签名体验。

## 常见问题 {#frequently-asked-questions}

**问：您可以将自适应表单嵌入到另一个自适应表单中。 嵌入式自适应表单是否可以启用Acrobat Sign?**

**答：** 否，AEM Forms不支持使用嵌入Acrobat Sign启用的自适应表单进行签名的自适应表单。

**问：当我使用高级模板创建自适应表单并将其打开进行编辑时，会出现一则错误消息“电子签名或签名器配置不正确”。 中。 如何解决错误消息？**

**答：** 使用高级模板创建的自适应表单配置为使用Acrobat Sign。 要解决该错误，请创建并选择Acrobat Sign云配置，并为自适应表单配置Acrobat Sign签名者。

**问：我能否在自适应表单的静态文本组件中使用Acrobat Sign文本标记？**

**答：** 是，您可以在文本组件中使用文本标记将Acrobat Sign字段添加到 [记录文档](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) （仅限自动生成的记录文档选项）启用了自适应表单。 要了解创建文本标记的过程和规则，请参阅 [Acrobat Sign文档](https://experienceleague.adobe.com/docs/document-cloud-learn/sign-learning-hub/admin-set-up/advanced-tasks-admins/adobe-sign-text-tagging.html). 另请注意，自适应表单对文本标记的支持有限。 您可以使用文本标记仅创建Acrobat Sign块支持的字段。

**问：AEM Forms提供了Acrobat Sign块和签名步骤组件。 能否在自适应表单中同时使用这些功能？**

**答：** 您可以在表单中同时使用这两个组件。 以下是使用这些组件的一些建议：

**Acrobat Sign块：** 您可以使用Acrobat Sign块在自适应表单上的任意位置添加Acrobat Sign字段。 它还有助于为签名者分配特定字段。 默认情况下，预览或发布自适应表单时，Acrobat Sign块不可见。 这些块仅在签名文档中启用。 在签名文档中，只启用分配给签名者的字段。 Acrobat Sign块可用于第一个和后续签名者。

**签名步骤组件：** 您可以使用签名步骤组件创建表单内签名体验。 它仅允许第一个签名者在填写表单时进行签名。 呈现包含签名步骤组件的部分后，会显示表单的可签名PDF版本。 它通常是表单的最后一个或倒数第二个部分，后跟摘要组件。
