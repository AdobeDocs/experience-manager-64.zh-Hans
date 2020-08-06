---
title: 将HTML5表单另存为草稿
seo-title: 将HTML5表单另存为草稿
description: 将HTML5表单另存为草稿，并在以后阶段继续填写表单。
seo-description: 将HTML5表单另存为草稿，并在以后阶段继续填写表单。
uuid: 70cd5f6f-f125-470c-8cee-ee14d2127713
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
translation-type: tm+mt
source-git-commit: db4d19e3af11f04369fc7f6a7c13377962f0650a
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 4%

---


# 将HTML5表单另存为草稿 {#saving-an-html-form-as-a-draft}

您可以将HTML5表单另存为草稿，并在以后的阶段继续填写表单。 Forms门户允许任何用户保存和恢复HTML5表单。 要启用“另存为草稿”功能，请向用户档案节点添加以下配置：

## 允许“另存为草图”功能的自定义用户档案 {#custom-profile-to-allow-save-as-draft-feature}

开箱即用，AEM Forms提供“另 **存为草稿** ”用户档案。 可以使用“另存为草稿”用户档案渲染表单以启用HTML5表单的草稿功能。 可以在Forms管理器中为表单指定HTML [渲染用户档案](/help/forms/using/introduction-managing-forms.md)。

要为现有自定义用户档案启用“另存为草 [稿”功能](/help/forms/using/custom-profile.md)，请向自定义用户档案节点添加以下属性：

<table> 
 <tbody> 
  <tr> 
   <td><strong>属性名称</strong></td> 
   <td><strong>类型</strong></td> 
   <td><strong>值</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>mfAllowFPDraft</td> 
   <td>字符串</td> 
   <td>true</td> 
   <td><p>启用另存为绘制特征</p> <p>这用户档案。</p> </td> 
  </tr> 
  <tr> 
   <td>mfAllowAttachments</td> 
   <td>字符串</td> 
   <td>true</td> 
   <td><p>允许上传附件</p> <p>这用户档案。</p> </td> 
  </tr> 
 </tbody> 
</table>

## 草稿存储和列表 {#drafts-storage-and-listing}

为表单启用“另存为草稿”功能后； 保存表单后，表单将列在草稿 [和提交组件中](/help/forms/using/draft-submission-component.md)。 您可以检索并开始填写从草稿和提交组件保存的表单。

要为“草稿”和“提交”组件启用表单列表，请向“用户档案”节点添加以下属性：

<table> 
 <tbody> 
  <tr> 
   <td><strong>属性名称</strong></td> 
   <td><strong>类型</strong></td> 
   <td><strong>值</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>fp.enablePortalSubmit</td> 
   <td>字符串</td> 
   <td>true</td> 
   <td>使草稿和表单在提交后在Forms门户<br /> “草稿和提交”组件中列出</td> 
  </tr> 
 </tbody> 
</table>

默认情况下，AEM Forms将与表单草稿和提交相关的用户数据存储在Publish实例的/content/forms/fp节点中。 您可以添加自定义存储提供程序，有关详细信息，请参 [阅草稿和提交的自定义存储组件](/help/forms/using/adding-custom-storage-provider-forms.md)。
