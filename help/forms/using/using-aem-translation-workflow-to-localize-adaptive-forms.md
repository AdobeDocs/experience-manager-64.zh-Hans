---
title: 使用AEM翻译工作流程本地化自适应表单和记录文档
seo-title: 使用AEM翻译工作流程本地化自适应表单和记录文档
description: 了解如何使用AEM翻译工作流本地化自适应表单和记录文档。
seo-description: 了解如何使用AEM翻译工作流本地化自适应表单和记录文档。
uuid: 6c87a283-0203-4cf7-989a-3770ddbbbd6e
content-type: reference
topic-tags: develop
discoiquuid: f5642571-9657-4ca1-93c5-4ae2eb91e967
noindex: true
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 0%

---


# 使用AEM翻译工作流程本地化自适应表单和记录文档 {#using-aem-translation-workflow-to-localize-adaptive-forms-and-document-of-record}

本地化的表单可帮助您跨地域提供更广泛的受众。 Adobe Experience Manager翻译工作流程可帮助您本地化自适应表单及其文档记录。 您可以使用 **机器翻译** 或 **人类翻** 译器对自适应表单进行本地化。

本文说明了将AEM翻译工作流与自适应表单和记录文档结合使用的过程。

## 使用机器翻译来定位自适应表单和记录文档 {#localizing-an-adaptive-form-and-document-of-record-using-machine-translation}

机器翻译服务会立即以自适应形式和记录文档翻译您的内容。 AEM Forms已预配置为使用Microsoft Translator的试用版进行机器翻译。 请执行以下步骤，为自适应表单启用机器翻译并文档记录：

1. 在AEM FormsUI中，选择一个表单，然后点按添 **加词典** 选项。
1. 在“ **将词典添加到翻译项目** ”屏幕中，选 **择“创建新翻译项目** ”或“添 **加到现有翻译项目”选项** 。
1. 在“项 **目标题** ”字段中，指定标题。 例如，`Government Reference Site - German locale.`
1. 在“目标 **语言** ”字段中，指定区域设置(例如， `German(de)`)，然后单击“完 **成”**。 您可以指定多个区域设置。 表单将翻译为“目标语言”字段中指定的 **所有语言** 。
1. 在“已添加词典”对话框中，单击“ **打开项目”**。 在“项目”屏幕中，打开新创建的项目。
1. 单击“ **翻译** 摘要”拼贴底 **部的椭圆** 。 将打开“翻译摘要”屏幕。
1. 单击“ **翻译** 摘要”屏幕顶部 **的“编辑** ”图标。 打开“ **翻译** ”选项卡，在“翻译方法”屏 **幕中选择“机** 器翻译”。 选择相应的 **翻译提供程序****和云配置**。 Click the **Done** icon at the top of the screen.
1. 在“转 **换作业** ”拼贴中，单 ![击aem62forms_downarrow图标](assets/aem62forms_downarrow.png) ，然后单击 **开始**。 拼贴的状态将更改为“草稿”。 翻译完成后，状态将变为“准 **备审阅”**。 几分钟后刷新页面并验证状态。
1. 在“翻译作业”拼 **贴上的状态** 更改 **为“准备审** 阅”后，在浏览器窗口中打开表单。 将显示表单的本地化版本。

   >[!NOTE]
   >
   >* 在浏览器窗口中打开表单的本地化版本之前，请确保将浏览器的区域设置设置为与表单的区域设置相匹配。 例如，如果表单已翻译为德语(de)语言，则将浏览器的区域设置设置为德语(de)。
   >* 自适应表单组件不支持从右到左(RTL)语言。 例如，希伯来语。


   与自适应表单一起，自动生成的记录文档也已本地化。

   有关记录设置和配置文档的详细信息，请参阅：

   [记录文档模板配置](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-template-configuration-p)

   [文档记录设置](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#p-document-of-record-settings-p)

1. [自定义记录文档的品牌信息](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) ，并确保将浏览器区域设置设置为您使用机器语言本地化自适应表单的同一语言。 浏览器区域设置有助于在记录文档中本地化品牌信息。
1. 要视图记录的本地化文档，请点按生成预览。 记录PDF的文档在您的浏览器中的新选项卡中生成并打开。

## 使用人文翻译实现自适应表单的本地化及其记录文档 {#localizing-an-adaptive-form-and-its-document-of-record-using-human-translation}

在人文翻译中，内容将发送给翻译提供商并由专业翻译人员翻译。 完成后，将返回译文内容并导入AEM。 将您的翻译提供者与AEM集成后，内容会在AEM和翻译提供者之间自动发送。

对于翻译，将与专业翻译人员共享包含XLIFF格式的文件的词典。 词典包括每个区域设置的单独XLIFF文件。 每个XLIFF文件都包含将向最终用户显示的文本以及相应本地化文本的占位符。

使用“人类翻译员”，执行以下步骤来本地化表单及其记录文档:

1. [将AEM与您的翻译服务提供商连接](/help/sites-administering/tc-tic.md) ，并 [创建翻译集成框架配置](/help/sites-administering/tc-tic.md)。

1. [将您语言的页面与翻译服务](/help/sites-administering/tc-tic.md) 和框架配置主控关联。

1. [确定要翻译的内容类](/help/sites-administering/tc-rules.md) 型。

1. [通过创作语言主控](/help/sites-administering/tc-prep.md) ，并创建语言副本的根页面，准备要翻译的内容。

1. [创建翻译项目](/help/sites-administering/tc-manage.md) ，以收集要翻译的内容并准备翻译过程。

1. 使用翻译项目 [管理内容翻译流程](/help/sites-administering/tc-manage.md)。

>[!NOTE]
>
>* 自适应表单组件不支持从右到左(RTL)语言。 例如，希伯来语。

>



