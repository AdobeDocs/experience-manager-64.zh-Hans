---
title: 内容片段 – 删除注意事项
seo-title: Content Fragments - Delete Considerations
description: 内容片段 – 删除注意事项
seo-description: Content Fragments - Delete Considerations
uuid: b4161a0e-7e17-4547-9bdd-cf3b1d0d7d63
contentOwner: AEM Docs
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
content-type: reference
discoiquuid: eaf65bdd-9091-4985-90bd-5eb2148965e3
exl-id: 43b11355-ee21-421c-8809-cd8a0443a03a
feature: Content Fragments
role: User
source-git-commit: 3358f6b8b492ff2b5858867a1f48a57b06944b1e
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 72%

---

# 内容片段 – 删除注意事项 {#content-fragments-delete-considerations}

>[!CAUTION]
>
>某些内容片段功能需要应用 [AEM 6.4 Service Pack 2(6.4.2.0)或更高版本](/help/release-notes/sp-release-notes.md).

## 权限 – 删除或不删除 {#permissions-delete-or-not-delete}

删除内容的功能非常强大，但可能很敏感，许多行业都需要限制和控制这些权限的分配方式。

关于删除权限，内容片段必须考虑在两个级别：

1. **内容片段作为单个实体。**

   * **用例**：需要编辑/更新内容片段的用户 – **并删除整个片段**。
   * **权限**:的 [删除](/help/sites-administering/security.md#actions) 权限可以 [通过用户和/或群组管理分配](/help/sites-administering/security.md#managing-permissions).

1. **构成内容片段的多个子实体；例如，变体、子节点。**

   内容片段编辑器的基本操作要求可以删除此类临时子元素。 例如，在处理变量时；在编辑元数据或管理关联的内容时，也可以。

   * **用例**：需要编辑/更新内容片段的用户 – **不允许删除整个片段**。
   * **权限**：请参阅 [仅编辑器功能所需的权限](content-fragments-delete.md#permissions-required-for-editor-functionality-only)。

>[!NOTE]
>
>当用户没有 [删除](/help/sites-administering/security.md#actions) 权限，内容片段编辑器在 *只读* 模式。

>[!NOTE]
>
>另请参阅 [如何在AEM中审核用户管理操作](/help/sites-administering/audit-user-management-operations.md).

## 仅编辑器功能所需的权限 {#permissions-required-for-editor-functionality-only}

对于需要编辑／更新内容片段的用户，**不允许他们删除整个片段**，必须分配特定权限，因为内容片段编辑器的基本操作要求可以删除临时子元素。

例如，在处理变量时；在编辑元数据或管理关联的内容时，也可以。

>[!NOTE]
>
>编辑/更新内容片段所需的删除权限包含在“删除”权限中 [通过用户和/或群组管理分配](/help/sites-administering/security.md#managing-permissions).

编辑/更新片段所需的权限需要应用于包含内容片段的节点或适当的父节点（在 `/content/dam` 下的任何级别）。当分配给此类父节点时，权限将应用于该分支中的所有节点。

例如，将包含所有内容片段的文件夹，例如：

* `/content/dam/contentfragments`

>[!CAUTION]
>
>在 `/content/dam` 也是可能的，因为此处存储了所有内容片段。
>
>但是，此操作会将相同的删除权限应用到 *全部* 其他资产类型。

允许特定用户和/或群组编辑/更新内容片段的先决条件是：

>[!NOTE]
>
>此列表显示所需的所有权限，而不只是删除权限。

* 对于内容片段节点或文件夹：

   * `jcr:addChildNodes`、`jcr:modifyProperties`

* 对于 `jcr:content`所有内容片段的节点：

   * `jcr:addChildNodes`、`jcr:modifyProperties` 和 `jcr:removeChildNodes`

* 对于所有内容片段的`jcr:content`以下的所有节点：

   * `jcr:addChildNodes`, `jcr:modifyProperties` 和 `jcr:removeChildNodes`, `jcr:removeNode`

这些 `remove` 权限必须 [在CRXDE Lite中使用访问控制列表进行管理](/help/sites-administering/user-group-ac-admin.md#access-right-management).

的 `add` 和 `modify` 权限也可以在CRXDE Lite中管理，或使用“用户管理”控制台管理。

例如， `remove` 群组的权限 `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)
