---
title: 内容片段 - 删除注意事项
seo-title: 内容片段 - 删除注意事项
description: 内容片段 - 删除注意事项
seo-description: 内容片段 - 删除注意事项
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: aheimoz
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: 内容片段
role: Business Practitioner
translation-type: tm+mt
source-git-commit: f9faa357f8de92d205f1a297767ba4176cfd1e10
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 12%

---

# 内容片段 - 删除注意事项 {#content-fragments-delete-considerations}

>[!CAUTION]
>
>某些内容片段功能要求应用[AEM 6.4 Service Pack 2(6.4.2.0)或更高版本](/help/release-notes/sp-release-notes.md)。

## 权限 — 删除或不删除{#permissions-delete-or-not-delete}

删除内容的功能非常强大，但可能非常敏感，许多行业需要限制和控制这些权限的分配方式。

关于删除权限，内容片段必须考虑在两个级别：

1. **内容片段作为单个实体。**

   * **用例**:需要编辑/更新内容片段并删除整 **个片段的用户**。
   * **权限**:可以 [](/help/sites-administering/security.md#actions) 通过“用 [户”和/或“组管理”来分配“删除”权限](/help/sites-administering/security.md#managing-permissions)。

1. **组成内容片段的多个子实体；例如，variations， sub-nodes。**

   内容片段编辑器的基本操作要求可以删除这种临时子元素。 例如，当操作变量时；此外，在编辑元数据或管理关联的内容时也是如此。

   * **用例**:需要编辑/更新内容片段的用户，不 **允许删除整个片段**。
   * **权限**:请参 [阅仅编辑器功能所需的权限](content-fragments-delete.md#permissions-required-for-editor-functionality-only)。

>[!NOTE]
>
>当用户没有任何[删除](/help/sites-administering/security.md#actions)权限时，内容片段编辑器以&#x200B;*只读*&#x200B;模式运行。

>[!NOTE]
>
>另请参阅[如何审核AEM](/help/sites-administering/audit-user-management-operations.md)中的用户管理操作。

## 仅编辑器功能所需的权限{#permissions-required-for-editor-functionality-only}

对于需要编辑／更新内容片段的用户， **不允许他们删除整个片段**，必须分配特定权限，因为内容片段编辑器的基本操作要求可以删除临时子元素。

例如，当操作变量时；此外，在编辑元数据或管理关联的内容时也是如此。

>[!NOTE]
>
>编辑/更新内容片段所需的删除权限包括在通过“用户”和/或“组管理”分配的“删除”权限[中。](/help/sites-administering/security.md#managing-permissions)

编辑/更新片段所需的权限需要应用于包含内容片段的节点或相应的父节点（在`/content/dam`下的任何级别）。 当分配给此类父节点时，权限将应用于该分支中的所有节点。

例如，将包含所有内容片段的文件夹，例如：

* `/content/dam/contentfragments`

>[!CAUTION]
>
>也可以设置`/content/dam`的权限，因为所有内容片段都存储在此处。
>
>但是，此操作也会将相同的删除权限应用于&#x200B;*all*&#x200B;其他资产类型。

允许特定用户和/或组编辑/更新内容片段的先决条件是：

>[!NOTE]
>
>此列表显示所需的所有权限，而不仅仅是删除权限。

* 对于内容片段节点或文件夹：

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* 对于所有内容片段的`jcr:content`节点：

   * `jcr:addChildNodes`, `jcr:modifyProperties` 和  `jcr:removeChildNodes`

* 对于所有内容片段`jcr:content`下的所有节点：

   * `jcr:addChildNodes`, `jcr:modifyProperties` 和 `jcr:removeChildNodes`,  `jcr:removeNode`

这些`remove`权限必须使用访问控制列表在CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management)内进行[管理。

`add`和`modify`权限也可以在CRXDE Lite中管理，或使用用户管理控制台。

例如，组`content-authors-no-delete`的`remove`权限定义：

![cf-delete-03](assets/cf-delete-03.png)
