---
title: 将收藏集发布到 Brand Portal
description: 了解如何将集合发布和取消发布到Brand Portal。
contentOwner: VG
feature: Brand Portal
role: 业务从业者
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 21%

---


# 将收藏集发布到 Brand Portal {#publish-collections-to-brand-portal}

作为Adobe Experience Manager(AEM)资产管理员，您可以将集合发布到组织的AEM Assets Brand Portal实例。 但是，您必须首先将AEM Assets与Brand Portal集成。 有关详细信息，请参阅[使用 Brand Portal 配置 AEM Assets](configure-aem-assets-with-brand-portal.md)。

如果您在AEM Assets中对原始集合进行后续修改，则在您再次发布集合之前，这些更改不会反映在Brand Portal中。 此特性可确保Brand Portal中不提供进行中的更改。 只有管理员发布的已批准更改才会出现在 Brand Portal 中。

>[!NOTE]
>
>无法将内容片段发布到 Brand Portal。因此，如果您在AEM作者上选择内容片段，则&#x200B;**[发布到Brand Portal]**&#x200B;操作不可用。
>
>如果包含内容片段的集合从AEM作者发布到Brand Portal，则文件夹（内容片段除外）的所有内容将复制到Brand Portal界面。

## 将集合发布到Brand Portal {#publish-a-collection-to-brand-portal}

1. 在AEM Assets UI中，点按/单击AEM徽标。 然后，从&#x200B;**[!UICONTROL 导航]**&#x200B;页面转至&#x200B;**[!UICONTROL 资产>集合]**。
2. 从收藏集控制台中，选择要发布到Brand Portal的收藏集。

   ![select_collection](assets/select_collection.png)

3. 在工具栏中，点按/单击&#x200B;**[!UICONTROL 发布到Brand Portal]**。

   ![publish_to_bp_icon](assets/publish_to_bp_icon.png)

4. 在确认对话框中，点按/单击&#x200B;**[!UICONTROL 发布]**。
5. 关闭确认消息。
6. 以管理员身份登录到Brand Portal。 已发布的收藏集将显示在“收藏集”控制台中。

   ![published_collection](assets/published_collection.png)

## 取消发布收藏集 {#unpublish-collections}

您可以取消发布从AEM Assets发布到Brand Portal的集合。 取消发布原始集合后，Brand Portal用户将无法再使用其副本。

1. 从您的AEM Assets实例的收藏集控制台中，选择要取消发布的收藏集。

   ![select_collection-1](assets/select_collection-1.png)

2. 在工具栏中，点按/单击&#x200B;**[!UICONTROL 从Brand Portal]**&#x200B;中删除图标。

   ![remove_from_bp_icon](assets/remove_from_bp_icon.png)

3. 在对话框中，点按/单击&#x200B;**[!UICONTROL 取消发布]**。
4. 关闭确认消息。收藏集将从 Brand Portal 界面中删除。
