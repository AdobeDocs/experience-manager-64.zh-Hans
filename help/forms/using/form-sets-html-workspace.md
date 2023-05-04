---
title: 在AEM Forms工作区中使用表单集
seo-title: Working with Formsets in AEM Forms workspace
description: 表单集是HTML5个表单的集合，分组后以一组表单的形式呈现给最终用户。 了解如何在AEM Forms工作区中使用表单集。
seo-description: A formset is a collection of HTML5 forms grouped and presented as a single set of forms to end users. Learn how you can work with formsets in AEM Forms workspace.
uuid: 77f81465-bd60-4aee-8507-585fe08adb78
contentOwner: vishgupt
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: c1793e2e-413c-4b6f-b96b-09e011f06263
exl-id: 4e39f6dd-b7a3-4c6c-be1f-66b9a5743352
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 3%

---

# 在AEM Forms工作区中使用表单集 {#working-with-formsets-in-aem-forms-workspace}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

表单集是HTML5个表单的集合，分组后以一组表单的形式呈现给最终用户。 当最终用户开始填写表单集时，他们会从一个表单无缝地转换到另一个表单。 然后，只需单击一次即可提交一组表单。 有关表单集及其设置方法的详细信息，请参阅 [表单集在AEM Forms](/help/forms/using/formset-in-aem-forms.md).

AEM Forms工作区支持表单集。 使用表单集，可以将与服务或流程相关的多个表单分组，以自动执行业务流程并呈现给最终用户。 在这种情况下，用户可以将整个集合作为一个进行填充，而且无需存档、提交和跟踪单个表单或进程。

## 将表单集附加到AEM Forms工作区应用程序中的起始点 {#attaching-a-formset-to-startpoint-in-an-aem-forms-workspace-app-br}

1. 在Workbench中创建业务流程工作流。 有关更多信息，请参阅 [Workbench帮助](https://www.adobe.com/go/learn_aemforms_workbench_63).
1. 从起点的进程属性中，选择 **使用CRX资产** 在演示和数据中。

   ![1-1](assets/1-1.png)

1. 单击 ![浏览](assets/browse.png) （浏览）。 此时会出现“选择表单资产”对话框。

   ![2](assets/2.png)

1. 单击 **表单集** ，从列表中选择相关表单集，然后单击 **确定**.

1. 在更新其他相关流程属性后部署应用程序。

## 在AEM Forms工作区中使用表单集 {#using-formset-in-nbsp-aem-forms-workspace}

将表单集附加到起始点后，可以从AEM Forms工作区中调用起始点，就像调用任何其他起始点一样。

通过AEM Forms工作区对表单集支持的操作包括：

* 另存为草稿
* 锁定
* 放弃
* 提交
* 添加附件
* 添加注释
* 使用“返回”或“下一步”按钮在表单集中的表单之间移动

![3-1](assets/3-1.png)

>[!NOTE]
>
>为了在表单集中从上一个表单和下一个表单移动期间提高性能，在相关表单完全呈现之前，所有工作区按钮(“返回”、“下一个”、“保存”、“提交”和……（更多）)都处于禁用状态。
