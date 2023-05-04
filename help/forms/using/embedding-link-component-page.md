---
title: 在页面中嵌入链接组件
seo-title: Embedding link component in a page
description: 您可以使用链接组件从任何页面链接自适应文档或自适应表单。
seo-description: You can use the link component to link an adaptive document or an adaptive form from any page.
uuid: fde56b5f-634c-406f-a026-875f972f7c8f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: a4a36e73-3f7a-4173-8807-931f26daa35a
exl-id: eb816a35-0773-4eda-95b2-1d351c71be8b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 2%

---

# 在页面中嵌入链接组件{#embedding-link-component-in-a-page}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 前提条件 {#prerequisites}

链接组件是“文档服务”类别的成员。 确保“文档服务”类别在AEM组件浏览器中可见。 如果未列出类别，请按照 [启用表单门户组件](/help/forms/using/enabling-forms-portal-components.md).

## 链接组件 {#link-component}

链接组件允许表单门户作者从页面上的任意位置创建指向自适应表单的链接。 链接组件位于组件浏览器的文档服务部分中。

执行以下步骤以将链接组件添加到页面：

1. 拖动 **链接** 组件。 选择组件并点按 ![cppr](assets/cmppr.png). 将打开编辑链接组件对话框。

   ![edit-link-component](assets/edit-link-component.png)

1. 在 **显示** 选项卡，请指定以下内容：

   * **链接标题**:链接文本或描述。
   * **链接工具提示**:链接的工具提示。
   * **布局模板**:链接组件布局的模板。

1. 打开 **资产信息** 选项卡，然后指定资产类型。 资产可以是 **表单**. 根据所选资产的类型，将显示以下列出的选项：

   * **资产路径**:存储资产的存储库路径。
   * **呈现类型**:呈现格式 — PDF、HTML或自动。 自动渲染类型会检测用户环境，并相应地将表单渲染为HTML或PDF。 例如，如果从移动设备访问表单，则“自动渲染”类型会以HTML呈现表单。
   * **提交URL:**  提交表单数据的Servlet的URL。
   * **HTML配置文件**:用于将表单渲染为HTML的配置文件。
   * **PDF配置文件**:用于将表单渲染为PDF文档的配置文件。

1. 打开&#x200B;**高级**&#x200B;选项卡。您可以以键值对格式指定其他参数。 单击链接后，这些附加参数将随表单一起传递。

   点按 **完成** 以保存配置。

## 使用链接组件的最佳实践 {#best-practices-for-using-link-component-br}

* 如果在“表单路径”中指定的路径指向文档，且该文档具有PDF作为允许的呈现格式，请确保选择“PDF”作为呈现类型。
* 表单的提交URL可以在多处指定，其优先顺序如下：

   1. 表单中嵌入的提交URL（在提交按钮中）具有最高优先级。
   1. 在Forms Manager中提及的提交URL具有中等优先级。
   1. 在Forms Portal中提及的提交URL优先级最低。
