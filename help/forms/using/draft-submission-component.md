---
title: 草稿和提交组件
seo-title: 草稿和提交组件
description: 草稿和提交组件列表处于草稿状态且已提交的表单。 您可以自定义组件的外观和样式。
seo-description: 草稿和提交组件列表处于草稿状态且已提交的表单。 您可以自定义组件的外观和样式。
uuid: 351d6df5-0dc3-4f7a-8bdf-0f1c8dd80f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 219dd379-5bc9-40b0-bdc2-2fb347da29d8
translation-type: tm+mt
source-git-commit: 2abf448e0231eb6fcd9295f498a24e81e1ead11a
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 0%

---


# 草稿和提交组件 {#drafts-and-submissions-component}

草稿和提交组件将列表处于草稿状态的所有表单以及已提交的表单。 该组件具有用于草稿和提交表单的单独部分（选项卡）。 用户只能视图其草稿和提交的表单。

## 配置组件 {#configuring-the-component}

“草稿和提交”组件包含两个选项卡： 草稿和提交。

要使自适应表单的提交显示在提交选项卡中，请将“提交”操 **作设置** 到 **[Forms门户提交操作](/help/forms/using/configuring-submit-actions.md)。**或者，启用“Forms门户提交”选项。 每当用户提交表单时，表单即添加到提交选项卡。

草稿功能现已启用。 当用户单击自 **适应表** 单上的“保存”时，表单将添加到草稿选项卡。

执行以下步骤以添加和配置草稿和提交组件：

1. 将组件浏览器中“ **文档服务** ”类别下的“草稿和提交”组件拖放到您的页面上。
1. 点按组件，然后点 ![按settings_icon](assets/settings_icon.png) ，以打开组件的编辑对话框。

   ![草稿和提交组件](assets/drafts-submissions-edit.png)

1. 在编辑对话框中，指定以下详细信息，然后点 **按完** 成以保存设置。

<table>
 <tbody>
  <tr>
   <th>选项卡·</th>
   <th>配置</th>
   <th>描述</th>
  </tr>
  <tr>
   <td>常规</td>
   <td>总结果</td>
   <td>指定要显示的结果的最大数量。 如果结果计数增加了“总结果”限制， <strong>则 </strong>组件底部会显示一个“更多”链接。 单击 <strong>更 </strong>多将显示所有表单。 </td>
  </tr>
  <tr>
   <td> </td>
   <td>样式类型</td>
   <td>指定组件的样式。 可以指定“ <strong>无样式</strong>”、“ <strong>默认样式</strong>”或“自 <strong>定义样式</strong> ”来列出表单。 对于“自定义样式选项”，可在“自定义样式路径”字段中指定自 <strong>定义CSS文件的 </strong>路径<strong>。</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>自定义样式路径</td>
   <td>如果在“样 <strong>式类型</strong> ”字段中选 <strong>择“自定</strong> 义样式”选项 <strong>，则使用“自定</strong> 义样式路径”字段指定自定义CSS文件的路径。 </td>
  </tr>
  <tr>
   <td> </td>
   <td>显示选项</td>
   <td><p>指定要显示的选项卡。 您可以选择显示草稿表单、已提交表单或同时显示两者。 </p> <p><strong>注意</strong>:<em> 对于 <strong>显示选项</strong>，如果您选择了“两者”以外的选 <strong>项</strong>，则不 <strong>会使用“默认选</strong> 项卡”字段选项。</em></p> </td>
  </tr>
  <tr>
   <td> </td>
   <td>默认选项卡</td>
   <td>指定加载表单门户页面时显示的选项卡。 您可以选择“草稿 <strong>Forms”选项卡</strong><strong>和“已提交Forms”选项卡</strong>。</td>
  </tr>
  <tr>
   <td>草稿Forms选项卡配置</td>
   <td>自定义标题</td>
   <td>指定“草稿Forms <strong>”选项卡</strong> 的标题。 默认值为“草 <strong>稿Forms”。</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>布局模板</td>
   <td><p>指定用于“Forms草案”列表的布局。</p> <p><strong>注意：</strong> 请勿使用默认（已弃用）选项。<br /> </p> </td>
  </tr>
  <tr>
   <td>已提交的Forms选项卡配置</td>
   <td>自定义标题 </td>
   <td>指定“已提交的 <strong>Forms”选 </strong>项卡的标题。 默认值为 <strong>SubmittedForms。</strong></td>
  </tr>
  <tr>
   <td> </td>
   <td>布局模板</td>
   <td>指定用于已提交的Forms<strong> 列表的 </strong>布局。 </td>
  </tr>
 </tbody>
</table>

## 自定义存储 {#customizing-the-storage}

当您使用Forms门户提交操作或启用自适应表单中的“在表单门户中存储数据”选项时，表单数据将存储在AEM存储库中。 在生产环境中，建议不要将草稿或提交的表单数据存储在AEM存储库中。 您必须将草稿和提交组件与安全存储（如企业数据库）集成，以存储草稿和提交的表单数据。

Forms门户允许您在本地AEM存储库、远程AEM存储库或数据库中存储数据。 AEM Forms允许您自定义为草稿和提交文件存储用户数据的实施。 您可以覆盖默认方法，以指定在您选择的存储存储草稿和提交数据的方式。 例如，可以将数据存储在组织中当前实施的数据存储中。

Forms门户提供开箱即用服务(API)，以在本地和远程AEM Forms发布实例的crx-repository上存储数据。 您可以将默认实现(如为草稿和提交 [配置存储服务文章中所述](/help/forms/using/configuring-draft-submission-storage.md) )替换为自定义实现以替换默认功能。 有关在安全位置存储内容的自定义实施中所需的方法的详细信息，请参 [阅自定义草稿和提交数据服务](/help/forms/using/custom-draft-submission-data-services.md)[以及草稿和提交组件的自定义存储。](/help/forms/using/adding-custom-storage-provider-forms.md)

AEM Forms文档提 [供将草稿和提交组件与数据库集成的示例](https://helpx.adobe.com/in/experience-manager/6-4/forms/using/integrate-draft-submission-database.html)。 您可以使用示例实现来开发您自己的自定义实现。

## 相关文章

* [启用表单门户组件](/help/forms/using/enabling-forms-portal-components.md)
* [创建表单门户页面](/help/forms/using/creating-form-portal-page.md)
* [使用API在网页上列表表单](/help/forms/using/listing-forms-webpage-using-apis.md)
* [使用草稿和提交组件](/help/forms/using/draft-submission-component.md)
* [自定义草稿和已提交表单的存储](/help/forms/using/draft-submission-component.md)
* [将草稿和提交组件与数据库集成的示例](/help/forms/using/integrate-draft-submission-database.md)
* [自定义表单门户组件的模板](/help/forms/using/customizing-templates-forms-portal-components.md)
* [在门户上发布表单简介](/help/forms/using/introduction-publishing-forms.md)
