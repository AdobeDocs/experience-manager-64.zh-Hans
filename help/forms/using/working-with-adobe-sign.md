---
title: 在自适应表单中使用Adobe Sign
seo-title: 在自适应表单中使用Adobe Sign
description: '为自适应表单启用电子签名(Adobe Sign)工作流，以自动签署工作流、简化单一和多签名流程以及从移动设备对表单进行电子签名。 '
seo-description: 为自适应表单启用电子签名(Adobe Sign)工作流，以自动签署工作流、简化单一和多签名流程以及从移动设备对表单进行电子签名。
uuid: 9c65dc44-c1a5-44df-8659-6efbe347575b
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 29fc297e-0a95-4d2a-bfe6-5676d53624db
noindex: true
feature: 自适应Forms、Adobe Sign
translation-type: tm+mt
source-git-commit: 5944eab0bf38551970685eaa98d90c4459720245
workflow-type: tm+mt
source-wordcount: '3596'
ht-degree: 0%

---


# 在自适应表单{#using-adobe-sign-in-an-adaptive-form}中使用Adobe Sign

为自适应表单启用电子签名(Adobe Sign)工作流，以自动签署工作流、简化单一和多签名流程以及从移动设备对表单进行电子签名。

Adobe Sign支持自适应表单的电子签名工作流。 电子签名可改善处理法律、销售、工资、人力资源管理等领域文档的工作流。

在典型的Adobe Sign和自适应表单场景中，用户填充自适应表单以申请服务。 例如，抵押贷款和信用卡申请要求所有借款人和共同申请人提供合法签名。 要为类似情况启用电子签名工作流，您可以将Adobe Sign与AEM Forms集成。 还有一些示例，您可以使用Adobe Sign执行以下操作：

* 借助完全自动化的建议书、报价和合同流程，从任何设备达成交易。
* 更快地完成人力资源流程，为员工提供数字体验。
* 缩短合同周期，并更快地建立供应商。
* 创建可自动处理常见流程的数字工作流。

Adobe Sign与AEM Forms集成支持：

* 单用户和多用户签名工作流
* 顺序和同时签名工作流
* 表单内和表单外签名体验
* 以匿名或登录用户身份对表单进行签名
* 动态签名流程(与AEM Forms工作流程集成)
* 通过知识库、电话和社交用户档案进行身份验证

了解将Adobe Sign与自适应表单结合使用的[最佳实践，以创建更好的签名体验。](https://medium.com/adobetech/using-adobe-sign-to-e-sign-an-adaptive-form-heres-the-best-way-to-do-it-dc3e15f9b684)

## 前提条件 {#prerequisites}

在自适应表单中使用Adobe Sign之前：

* 确保将AEM Forms云服务配置为使用Adobe Sign。 有关详细信息，请参阅[将Adobe Sign与AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)集成。
* 让签名者的列表保持就绪。 您至少需要为每位签名者提供电子邮件地址。

## 为自适应表单{#configure-adobe-sign-for-an-adaptive-form}配置Adobe Sign

请执行以下步骤为自适应表单配置Adobe Sign:

1. [编辑Adobe签名的自适应表单属性](#enableadobesign)
1. [将Adobe Sign字段添加到自适应表单](#addadobesignfieldstoanadaptiveform)
1. [为自适应表单启用Adobe Sign](#enableadobsignforanadaptiveform)
1. [为自适应表单选择Adobe SignCloud Service](#selectadobesigncloudserviceforanadaptiveform)

1. [将Adobe Sign签名者添加到自适应表单](#addsignerstoanadaptiveform)
1. [为自适应表单选择提交操作](#selectsubmitactionforanadaptiveform)

![签名者 — 详细信息](assets/signer-details.png)

### 编辑Adobe Sign {#enableadobesign}的自适应表单属性

为现有或新的自适应表单配置Adobe Sign的自适应表单属性。

[为Adobe签名创建自适应](/help/forms/using/working-with-adobe-sign.md#create-an-adaptive-form-for-adobe-sign) 表单介绍创建基本自适应表单的步骤。有关创建自适应表单时可用的其他选项，请参阅[创建自适应表单](/help/forms/using/creating-adaptive-form.md)。

#### 为Adobe Sign {#create-an-adaptive-form-for-adobe-sign}创建自适应表单

请执行以下步骤为Adobe Sign创建自适应表单：

1. 导航到&#x200B;**[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms和文档]**。
1. 点按&#x200B;**[!UICONTROL 创建]**&#x200B;并选择&#x200B;**[!UICONTROL 自适应表单]**。 将显示一列表模板。 选择模板，然后点按&#x200B;**[!UICONTROL 下一步]**。
1. 在&#x200B;**[!UICONTROL 基本]**&#x200B;选项卡中：

   1. 为自适应表单指定&#x200B;**名称**&#x200B;和&#x200B;**标题**。
   1. 选择在使用AEM Forms配置Adobe Sign时创建的[配置容器](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms)。

      >[!NOTE]
      >
      >**[!UICONTROL Adobe Sign Cloud Service]**&#x200B;下拉列表显示在您在此字段中选择的配置容器中配置的云服务。 当您选择&#x200B;**[!UICONTROL 启用Adobe Sign]**&#x200B;选项时，自适应表单属性的&#x200B;**[!UICONTROL 电子签名]**&#x200B;部分中提供&#x200B;**[!UICONTROL Adobe SignCloud Service]**&#x200B;下拉列表。

1. 在&#x200B;**[!UICONTROL 表单模型]**&#x200B;选项卡中，选择以下选项之一：

   * 选择&#x200B;**[!UICONTROL 将表单模板关联为“记录模板”]**&#x200B;选项，然后选择“记录模板”的文档。 如果您使用基于表单模板的自适应表单，则发送的用于签名的文档仅显示基于关联表单模板的字段。 它不显示自适应表单的所有字段。
   * 选择&#x200B;**[!UICONTROL 生成记录文档]**&#x200B;选项。 如果您使用“记录文档”选项启用的自适应表单，则发送的用于签名的文档将显示自适应表单的所有字段。

1. 点按&#x200B;**[!UICONTROL 创建。]** 将创建启用签名的自适应表单，该表单可用于添加Adobe Sign字段。

#### 编辑Adobe Sign {#editafsign}的自适应表单

执行以下步骤以在现有自适应表单中使用Adobe Sign:

1. 导航到&#x200B;**[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]**> **[!UICONTROL Forms和文档]**。
1. 选择自适应表单，然后点按&#x200B;**[!UICONTROL 属性]**。
1. 在&#x200B;**[!UICONTROL 基本]**&#x200B;选项卡中，选择在使用AEM Forms配置Adobe Sign时创建的[配置容器](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms)。
1. 在&#x200B;**[!UICONTROL 表单模型]**&#x200B;选项卡中，选择以下选项之一：

   * 选择&#x200B;**[!UICONTROL 将表单模板关联为“记录模板”]**&#x200B;选项，然后选择“记录模板”的文档。 如果您使用基于表单模板的自适应表单，则发送的用于签名的文档仅显示基于关联表单模板的字段。 它不显示自适应表单的所有字段。
   * 选择&#x200B;**[!UICONTROL 生成记录文档]**&#x200B;选项。 如果您使用“记录文档”选项启用的自适应表单，则发送的用于签名的文档将显示自适应表单的所有字段。

1. 点按&#x200B;**[!UICONTROL 保存并关闭]**。 自适应表单已启用Adobe Sign。

### 将Adobe Sign字段添加到自适应表单{#addadobesignfieldstoanadaptiveform}

Adobe Sign具有可放置在自适应表单上的各种字段。 这些字段接受各种类型的数据(如签名、缩写签名、公司或标题)，并帮助在签名过程中收集额外信息以及签名。 您可以使用Adobe Sign块组件将Adobe Sign字段放置在自适应表单的不同位置。

请执行以下步骤将字段添加到自适应表单并自定义与这些字段相关的各种选项：

1. 将&#x200B;**Adobe Sign块**&#x200B;组件从组件浏览器拖放到自适应表单。 Adobe Sign块组件具有所有受支持的Adobe Sign字段。 默认情况下，它会向自适应表单添加&#x200B;**签名**&#x200B;字段。

   ![sign-block](assets/sign-block.png)

   默认情况下，Adobe Sign块在已发布的自适应表单中不可见。 仅在签名文档中可见。 您可以从Adobe Sign块组件的属性更改Adobe Sign块的可见性。

   >[!NOTE]
   >
   >* 在自适应表单中使用Adobe Sign块不是必需的。 如果您不使用Adobe Sign块并为签名者添加字段，则默认签名字段将显示在签名文档的底部。
   >* 仅将Adobe Sign块用于自动生成“记录”文档的自适应表单。 如果您使用自定义XDP生成记录文档或基于表单模板的自适应表单，则不需要Adobe Sign块。


1. 选择&#x200B;**Adobe Sign块**&#x200B;组件，然后点按&#x200B;**编辑** ![ aem_6_3_edit](assets/aem_6_3_edit.png)图标。 它显示用于添加字段和设置字段外观格式的选项。

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **答：选** 择并添加Adobe Sign字段。**B.将** Adobe Sign块展开为全屏视图

1. 点按&#x200B;**Adobe Sign字段** ![ aem_6_3_adobesign](assets/aem_6_3_adobesign.png)图标。 它显示用于选择和添加Adobe Sign字段的选项。

   展开&#x200B;**Type**&#x200B;下拉字段以选择Adobe Sign字段，然后点按完成![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)图标以将所选字段添加到Adobe Sign块。 **类型**&#x200B;下拉字段包括签名、签名者信息和数据字段类型。 Adobe Sign与AEM Forms支持字段集成(仅在“类型”(Type)下拉框中列出)。 有关Adobe Sign字段的详细信息，请参阅[Adobe Sign文档](https://helpx.adobe.com/sign/help/field-types.html)。

   ![adobe-sign-block-fields-options](assets/adobe-sign-block-fields-options.png)

   必须为字段提供唯一的名称。 您还可以选择所需选项，将字段标记为必填。 除了&#x200B;**名称**&#x200B;和&#x200B;**必需**&#x200B;选项之外，某些Adobe Sign字段还有更多选项。 例如，蒙版和多行。 此外，为每个Adobe Sign字段指定唯一名称，无论这些字段位于相同或不同的Adobe Sign块中。

### 为自适应表单{#enableadobsignforanadaptiveform}启用Adobe Sign

开箱即用，不为自适应表单启用Adobe Sign。 请执行以下步骤以启用它：

1. 在内容浏览器中，点按&#x200B;**表单容器**，然后点按&#x200B;**配置** ![配置](assets/configure.png)图标。 它打开属性浏览器并显示自适应表单容器属性。
1. 在属性浏览器中，展开&#x200B;**电子签名**&#x200B;折叠面板，然后选择&#x200B;**启用Adobe Sign**&#x200B;选项。 它使Adobe Sign能够实现自适应表单。

### 选择Adobe SignCloud Service和签名顺序{#selectadobesigncloudserviceforanadaptiveform}

您可以为AEM Forms实例配置多个Adobe Sign服务。 建议为每个功能（人力资源、财务等）单独提供一组服务。 它使跟踪和报告已签名的文档变得更轻松。 例如，银行有多个部门。 您可以为每个部门单独配置，以便更好地跟踪文档。

文档还可以有多个签名者。 例如，信用卡申请可以有多个申请人。 银行在开始处理申请之前需要所有申请人的签名。 对于多签名者方案，您可以选择按顺序或同时顺序对文档进行签名。

请执行以下步骤来选择云服务和签名顺序：

![云服务](assets/cloud-service.png)

1. 在内容浏览器中，点按&#x200B;**表单容器**，然后点按&#x200B;**配置** ![配置](assets/configure.png)图标。 它打开属性浏览器并显示自适应表单容器属性。
1. 在属性浏览器中，展开&#x200B;**电子签名**&#x200B;折叠面板，然后选择&#x200B;**启用Adobe Sign**&#x200B;选项。 它使Adobe Sign能够实现自适应表单。
1. 从已配置的Adobe SignCloud Services列表中选择云服务。

   如果&#x200B;**Adobe Sign Cloud Service**&#x200B;列表为空，请按照[使用AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)文章配置Adobe Sign以配置服务。

   下拉列表列表了存在于“工具”>**[!UICONTROL “Cloud Services”]**>>**[!UICONTROL Adobe Sign]**&#x200B;中的`global`文件夹中的云服务。 此外，下拉列表还列表了在创建自适应表单时在&#x200B;**[!UICONTROL 配置容器]**&#x200B;字段中选择的文件夹中存在的云服务。

1. 从&#x200B;**签名者可以签名**&#x200B;对话框中选择签名顺序。 Adobe Sign歌手可以按任意顺序签署自适应格式&#x200B;**Securly** — 一个接一个的签名者，或&#x200B;**Montilize** -。

   按顺序，一个签名者一次接收签名表单。 签名者完成对文档的签名后，表单将发送给下一位签名者，依此类推。

   同时，多个签名者可以一次对表单进行签名。

1. [将签名者添加到自适应](#addsignerstoanadaptiveform) 格式，然后点按完成图标以保存更改。

### 将签名者添加到自适应表单{#addsignerstoanadaptiveform}

对于自适应表单，只能有一个或多个签名者。 添加签名者时，您还可以为签名者配置身份验证详细信息。 您还可以选择表单填写者和歌手是否相同。 请执行以下步骤来添加和提供有关签名者的各种详细信息：

1. 在内容浏览器中，点按&#x200B;**表单容器**，然后点按&#x200B;**配置** ![配置](assets/configure.png)图标。 它打开具有自适应表单容器属性的属性浏览器。
1. 在属性浏览器中，展开&#x200B;**电子签名**&#x200B;折叠面板，然后选择&#x200B;**启用Adobe Sign**&#x200B;选项。 它使Adobe Sign能够实现自适应表单。
1. 点按&#x200B;**签名者配置下的**&#x200B;添加签名者&#x200B;**。** 它会向自适应表单中添加签名者。您可以向自适应表单添加多个Adobe Sign签名者。
1. ![电话详细信息](assets/phone-details.png)

   单击&#x200B;**编辑** ![ aem_6_3_edit](assets/aem_6_3_edit.png)图标以指定有关签名者的以下信息：

   * **标题：** 指定标题以唯一标识签名者。
   * **签名者和填写表单的人是否相同？：如果** 表单填 **写者**&#x200B;和第一个签名者是同一人，请选择是。如果选项设置为&#x200B;**否，**，则不要在自适应表单中使用签名步骤组件。 如果表单包含签名步骤组件，则字段会自动设置为是。
   * **签名者电子邮件地址：** 指定签名者的电子邮件地址。签名者在指定的电子邮件地址收到待签名的文档/表单。 您可以选择在登录用户的AEM用户用户档案中使用表单字段中提供的电子邮件地址，也可以手动输入电子邮件地址。 这是必须采取的步骤。 另请注意，如果您只配置了一个签名者，请确保签名者的电子邮件地址与用于配置AEM云服务的Adobe Sign帐户不相同。
   * **签名者身份验证方** 法：指定在打开用于签名的表单之前对用户进行身份验证的方法。您可以在电话、知识库和基于社交身份的身份验证之间进行选择。

   >[!NOTE]
   >
   >* 默认情况下，基于社交身份的身份验证提供了使用Facebook、Google和LinkedIn进行身份验证的选项。 您可以联系Adobe Sign支持以启用其他社交身份验证提供商。


   * **Adobe Sign字段以填写或签名：为** 签名者选择Adobe Sign字段。自适应表单可以有多个Adobe Sign字段。 您可以选择为签名者启用特定字段。 该字段显示所有可用的Adobe Sign块。 当您选择块时，该块的所有字段都将被选中。 可以使用X图标取消选择字段。

   ![signer-details-1](assets/signer-details-1.png)

   上图有两个Adobe Sign块示例：个人信息和办公室详细信息

   点按完成![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)图标。 将添加并配置签名者。

### 为自适应表单{#selectsubmitactionforanadaptiveform}选择提交操作

添加Adobe Sign字段到自适应表单后，从表单容器启用Adobe Sign，选择Adobe SignCloud Service，并添加Adobe Sign签名者，为自适应表单选择适当的提交操作。 有关自适应表单提交操作的详细信息，请参阅[配置提交操作](/help/forms/using/configuring-submit-actions.md)。

此外，只有所有签名者对表单进行签名后，才会提交启用Adobe Sign的自适应表单。 您可以在表单门户的“待签名”部分找到部分签名的表单。 Adobe Sign Configuration Service以[定期间隔](/help/forms/using/adobe-sign-integration-adaptive-forms.md)对Adobe Sign服务器进行轮询以验证签名的状态。 如果所有签名者都完成了表单的签名，则会启动提交操作服务并提交表单。 如果您使用自定义提交操作，而表单使用Adobe Sign，请更新您的自定义提交操作以使用提交操作服务。

>[!NOTE]
>
>自适应表单的数据临时存储在Forms Portal上。 建议对Forms Portal](/help/forms/using/configuring-draft-submission-storage.md)使用[自定义存储。 它可确保PII（个人身份信息）数据不存储在AEM服务器上。

您的表单签名体验已就绪。 您可以预览表单以验证签名体验。 在发布的表单上，当签名者收到通过电子邮件进行签名的表单时，将显示Adobe Sign阻止字段。 这种体验也称为表外签名体验。 您还可以为第一位签名者配置表单内签名体验，有关详细步骤，请参阅[创建表单内签名体验](/help/forms/using/working-with-adobe-sign.md#create-in-form-signing-experience)。

## 为自适应表单{#configure-cloud-signatures-for-an-adaptive-form}配置云签名

基于云的数字签名或远程签名是新一代的数字签名，可跨桌面、移动设备和Web使用，并满足签名者身份验证的最高级别合规和保证。 您可以使用基于云的数字签名对自适应表单进行签名。

在[编辑Adobe符号](#enableadobesign)的自适应表单属性后，请执行以下步骤将云签名字段添加到自适应表单：

1. 将&#x200B;**Adobe Sign块**&#x200B;组件从组件浏览器拖放到自适应表单。 Adobe Sign块组件具有所有受支持的Adobe Sign字段。 默认情况下，它会向自适应表单添加&#x200B;**签名**&#x200B;字段。

   ![sign-block](assets/sign-block.png)

1. 选择&#x200B;**Adobe Sign块**&#x200B;组件，然后点按&#x200B;**编辑** ![ aem_6_3_edit](assets/aem_6_3_edit.png)图标。 它显示用于添加字段和设置字段外观格式的选项。

   ![adobe-sign-block-select-fields](assets/adobe-sign-block-select-fields.png)

   **答：选** 择并添加Adobe Sign字段。**B.将** Adobe Sign块展开为全屏视图

1. 点按&#x200B;**Adobe Sign字段** ![ aem_6_3_adobesign](assets/aem_6_3_adobesign.png)图标。 它显示用于选择和添加Adobe Sign字段的选项。

   展开&#x200B;**类型**&#x200B;下拉字段以选择&#x200B;**数字签名**，然后点按完成![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)图标以将所选字段添加到Adobe Sign块。

   ![digital_signatures](assets/digital_signatures.png)

   必须为字段提供唯一的名称。

   使用以下方式将数字签名应用于自适应表单：

   * 云签名：使用由信任服务提供商托管的[数字ID](https://helpx.adobe.com/sign/kb/digital-certificate-providers.html)进行签名。
   * Adobe Acrobat或Reader:下载并打开Adobe Acrobat或Reader的文档，使用智能卡、USB令牌或基于文件的数字ID进行签名。

   在将云签名字段添加到自适应表单后，请执行以下步骤以完成配置过程：

   * [为自适应表单启用Adobe Sign](#enableadobsignforanadaptiveform)
   * [为自适应表单选择Adobe SignCloud Service](#selectadobesigncloudserviceforanadaptiveform)
   * [将Adobe Sign签名者添加到自适应表单](#addsignerstoanadaptiveform)
   * [为自适应表单选择提交操作](#selectsubmitactionforanadaptiveform)


## 创建表单内签名体验{#create-in-form-signing-experience}

用户还可以在填写表单时对自适应表单进行签名。 此体验也称为表单签名体验。 表单内签名体验仅对多个签名者环境中的第一位歌手可用。 请执行以下步骤以创建自适应表单的表单内签名体验：

1. [添加和配置签名步骤组件](#add-and-configure-the-signature-step-component)。
1. [添加摘要步骤组件](#configure-the-thank-you-page-or-summary-step-component)。

![表单签名体验](assets/in-form-signing-experience.png)

### 添加和配置签名步骤组件{#add-and-configure-the-signature-step-component}

使用签名步骤组件提供一个区域以对填写的表单进行电子签名。 呈现包含签名步骤组件的部分时，将显示已填写表单的可签名PDF版本。 签名步骤组件具有表单可用的全宽。 建议在包含签名步骤组件的部分上不要使用任何其他组件。

请执行以下步骤以配置签名步骤组件：

1. 将&#x200B;**签名步骤**&#x200B;组件从组件浏览器拖放到表单中。
1. 选择新添加的签名步骤组件，然后点按&#x200B;**配置** ![配置](assets/configure.png)图标。 它打开属性浏览器并显示签名步骤属性。 配置以下属性：

   * **元素名称**:指定组件的名称。
   * **标题：** 指定组件的唯一标题。
   * **模板消** 息：指定加载签名PDF时要显示的消息。Adobe Sign服务需要一些时间来准备和加载签名PDF。
   * **签名服务：** 选择 **Adobe** 签名。
   * **使用旧版电子签名组件**:如果您正在AEM Forms Workspace、AEM Forms应用程序中使 [用相应的自适应表单](/help/forms/using/introduction-html-workspace.md)，或者基础自适应表单具有旧版电子签名组件，请选择 **使用旧版电子签名组** 件选项。
   * **配置**:选择配置(Adobe SignCloud Service)。只有启用了&#x200B;**使用旧版E-sign组件**&#x200B;选项时，下拉框才可用。

   点按完成![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)图标以保存更改。

   ![signature-step](assets/signature-step.png)

   >[!NOTE]
   >
   >* 当您将&#x200B;**[!UICONTROL 签名步骤]**&#x200B;组件拖放到表单时，**[!UICONTROL 签名者和填写表单的人是否相同？]** 的子菜单。 ****&#x200B;需要使表单继续工作。
   >* Adobe Sign启用的自适应表单不支持使用签名步骤组件的章节或面板上的“提交”按钮。 您可以在手动提交的签名步骤后添加摘要步骤，或在使用[Adobe Sign Configuration Service](/help/forms/using/adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-scheduler-to-sync-the-signing-status)设置的间隔后触发自动提交。


### 配置感谢页面或摘要步骤组件{#configure-the-thank-you-page-or-summary-step-component}

**摘要步骤**&#x200B;组件会自动提交表单，在自定义的“摘要”页面中填充信息，并显示已提交表单的摘要。 它还会在返回图中获得所需的信息。 摘要步骤组件具有表单可用的全宽。 建议在包含摘要步骤组件的部分上不要使用任何其他组件。

现在，表单签名体验已准备就绪。 您可以预览表单以验证签名体验。

## 常见问题 {#frequently-asked-questions}

**问：您可以将自适应表单嵌入到另一个自适应表单中。嵌入式自适应表单是否可以启用Adobe Sign?**

**答：** 不，AEM Forms不支持使用嵌入支持Adobe Sign的自适应表单进行签名的自适应表单。

**问：当我使用高级模板创建自适应表单并打开它进行编辑时，将显示一条错误消息“电子签名或签名者配置不正确。”。 如何解析错误消息？**

**Ans：使** 用高级模板创建的自适应表单配置为使用Adobe Sign。要解决该错误，请创建并选择Adobe Sign云配置，并为自适应表单配置Adobe Sign签名者。

**问：是否可以在自适应表单的静态文本组件中使用Adobe Sign文本标签？**

**答案：** 是的，您可以在文本组件中使用文本标签将Adobe Sign字段添加到启用了自 [适应表单的](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) “记录”文档(仅“自动生成记录文档”选项)。要了解创建文本标记的过程和规则，请参阅[Adobe Sign文档](https://helpx.adobe.com/sign/help/text-tags.html)。 另请注意，自适应表单对文本标签的支持有限。 您可以使用文本标记仅创建Adobe Sign Block支持的字段。

**问：AEM Forms提供Adobe Sign块和签名步骤组件。这些功能是否可以同时在自适应形式中使用？**

**答案：** 您可以在表单中同时使用这两个组件。以下是使用这些组件的一些建议：

**Adobe Sign块：** 您可以使用Adobe Sign块在自适应表单的任意位置添加Adobe Sign字段。它还有助于为签名者分配特定字段。 默认情况下，当预览或发布自适应表单时，Adobe Sign块不可见。 这些块仅在签名文档中启用。 在签名文档中，只启用分配给签名者的字段。 Adobe Sign块可与第一个和后续签名者一起使用。

**签名步骤组件：** 您可以使用签名步骤组件创建表单内签名体验。它只允许第一个签名者在填写表单时进行签名。 呈现包含签名步骤组件的部分时，会显示表单的可签名PDF版本。 它通常是表单的最后一个或倒数第二个部分，后跟摘要组件。

