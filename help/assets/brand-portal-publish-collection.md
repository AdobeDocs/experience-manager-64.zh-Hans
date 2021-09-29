---
title: 将收藏集发布到 Brand Portal
description: 了解如何将收藏集发布和取消发布到Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: c2c6759e-f763-405e-9e45-5a90b9d32df2
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 21%

---

# 将收藏集发布到 Brand Portal {#publish-collections-to-brand-portal}

作为Adobe Experience Manager Assets管理员，您可以将收藏集发布到您组织的[!DNL Experience Manager Assets Brand Portal]实例。 但是，您必须先将Assets与Brand Portal集成。 有关详细信息，请参阅[使用 Brand Portal 配置 Assets](configure-aem-assets-with-brand-portal.md)。

如果您随后在Assets中对原始收藏集进行了修改，则在再次发布该收藏集之前，所做的更改不会反映在Brand Portal中。 此特性可确保在Brand Portal中不提供正在进行的更改。 只有管理员发布的已批准更改才会出现在 Brand Portal 中。

>[!NOTE]
>
>无法将内容片段发布到 Brand Portal。因此，如果在[!DNL Experience Manager]创作中选择内容片段，则&#x200B;**[发布到Brand Portal]**&#x200B;操作将不可用。
>
>如果包含内容片段的集合从[!DNL Experience Manager]创作发布到Brand Portal，则文件夹（内容片段除外）的所有内容都会复制到Brand Portal界面。

## 将收藏集发布到Brand Portal {#publish-a-collection-to-brand-portal}

1. 在Assets UI中，点按/单击[!DNL Experience Manager]徽标。 然后，从&#x200B;**[!UICONTROL 导航]**&#x200B;页面中，转到&#x200B;**[!UICONTROL Assets >收藏集]**。
2. 从收藏集控制台中，选择要发布到Brand Portal的收藏集。

   ![select_collection](assets/select_collection.png)

3. 在工具栏中，点按/单击&#x200B;**[!UICONTROL 发布到Brand Portal]**。

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. 在确认对话框中，点按/单击&#x200B;**[!UICONTROL 发布]**。
5. 关闭确认消息。
6. 以管理员身份登录Brand Portal。 已发布的收藏集将显示在“收藏集”控制台中。

   ![published_collection](assets/published_collection.png)

## 取消发布收藏集 {#unpublish-collections}

您可以取消发布从Assets发布到Brand Portal的收藏集。 取消发布原始收藏集后，其副本将不再可供Brand Portal用户使用。

1. 从[!DNL Assets]实例的收藏集控制台中，选择要取消发布的收藏集。

   ![select_collection-1](assets/select_collection-1.png)

2. 在工具栏中，点按/单击&#x200B;**[!UICONTROL 从Brand Portal中删除]**&#x200B;图标。

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. 在对话框中，点按/单击&#x200B;**[!UICONTROL 取消发布]**。
4. 关闭确认消息。收藏集将从 Brand Portal 界面中删除。
