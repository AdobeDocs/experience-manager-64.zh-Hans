---
title: 将集合发布到Brand Portal
description: 了解如何将集合发布和取消发布到Brand Portal。
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1

---


# Publish collections to Brand Portal {#publish-collections-to-brand-portal}

作为Adobe Experience Manager(AEM)资产管理员，您可以将集合发布到您组织的AEM Assets Brand Portal实例。 但是，您必须先将AEM资产与Brand Portal集成。 有关详细信息，请 [参阅配置AEM资产与Brand Portal](configure-aem-assets-with-brand-portal.md)。

如果您在AEM资产中对原始集合进行后续修改，则在您再次发布集合之前，这些更改不会反映在Brand Portal中。 此特性可确保在品牌门户中不提供进行中的更改。 只有管理员发布的已批准更改才可在Brand Portal中使用。

>[!NOTE]
>
>内容片段无法发布到Brand Portal。 因此，如果您在AEM作者上选择内容片段，则“发布 **[到品牌门户]** ”操作将不可用。
>
>如果包含内容片段的集合从AEM作者发布到Brand Portal，则文件夹中除内容片段之外的所有内容都将被复制到Brand Portal界面。

## 将集合发布到Brand Portal {#publish-a-collection-to-brand-portal}

1. 在AEM资产UI中，点按／单击AEM徽标。 然后，从导航 **[!UICONTROL 页面转至资产]** > **[!UICONTROL 收藏集]** 。
2. 从“集合”控制台中，选择要发布到Brand Portal的集合。

   ![select_collection](assets/select_collection.png)

3. 在工具栏中，点按／单击发 **[!UICONTROL 布到品牌门户]**。

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. 在确认对话框中，点按／单击 **[!UICONTROL 发布]**。
5. 关闭确认消息。
6. 以管理员身份登录到Brand Portal。 已发布的集合在“集合”控制台中可用。

   ![published_collection](assets/published_collection.png)

## 取消发布集合 {#unpublish-collections}

您可以取消发布从AEM资产发布到Brand Portal的集合。 在取消发布原始集合后，Brand Portal用户将无法再使用其副本。

1. 从AEM资产实例的收藏集控制台中，选择要取消发布的收藏集。

   ![select_collection-1](assets/select_collection-1.png)

2. 在工具栏中，点按／单击从Brand Portal **[!UICONTROL 中删除]** 。

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. 在对话框中，点按／单击取 **[!UICONTROL 消发布]**。
4. 关闭确认消息。 集合将从Brand Portal界面中删除。
