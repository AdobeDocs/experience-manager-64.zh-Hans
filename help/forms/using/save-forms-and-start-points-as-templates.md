---
title: 将表单另存为模板
seo-title: Save forms as templates
description: 了解如何使用重复需要的数据从表单创建模板。
seo-description: Learn how to create templates from forms with data required repeatedly.
uuid: 090c6271-4061-4adc-a063-9df4953b47ce
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: e0df2f85-664a-47b3-a8c5-e986b975d421
exl-id: 355c4810-6e45-41cb-9b60-73225bd53526
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---

# 将表单另存为模板 {#save-forms-as-templates}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

有时，当用户填写表单时，对几个字段的输入将保持不变。 对于此类情况，您可以在每个实例中填写要求相同值的字段，并将表单或草稿另存为模板。 现在，每次创建模板实例时，指定的字段都已填充模板中指定的值。 它有助于您节省填写表单所需的时间和精力。

执行以下步骤以创建模板：

1. 打开一个表单，并选择或填写每次使用时具有几乎相同值的字段。 您可以包含一个附件，其中包含您通常在填写表单时添加的模板。
1. 点按 **另存为模板** ![save_as_template](assets/save_as_template.png)图标。 此时会出现一个用于指定模板名称的对话框。
1. 指定模板的名称并点按 **保存**. 模板将显示在模板文件夹中。

   如果存在具有相同名称的模板，则会显示一个用于确认覆盖现有模板的对话框。 要将现有模板替换为新模板，请点按 **继续** 或者，若要使用其他名称保存模板，请点按 **取消**.

现在，您可以打开保存的模板。 每次打开模板时，都会创建一个新表单或任务，并且该表单会显示保存的数据和选项。 使用模板，您可以编辑预填充的数据、添加附件、另存为草稿、提交任务或使用该任务创建其他模板。 模板特定于移动设备，不会与Adobe Experience Manager Forms服务器同步。

如果模板不再需要，您还可以删除该模板。 要删除模板，请导航到模板文件夹，点按省略号，然后点按 **删除模板**.

>[!NOTE]
>
>模板在本地可用，且不会与服务器同步。 清除应用程序的本地数据会删除模板。
