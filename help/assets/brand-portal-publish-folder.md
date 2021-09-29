---
title: 将文件夹发布到 Brand Portal
description: 了解如何将文件夹发布和取消发布到Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 27%

---

# 将文件夹发布到 Brand Portal {#publish-folders-to-brand-portal}

作为Adobe Experience Manager Assets管理员，您可以将资产和文件夹发布到您组织的[!DNL Experience Manager Assets Brand Portal]实例（或将发布工作流安排到稍后的日期/时间）。 但是，您必须先将[!DNL Experience Manager Assets]与[!DNL Brand Portal]集成。 有关详细信息，请参阅[使用Brand Portal](configure-aem-assets-with-brand-portal.md)配置 [!DNL Experience Manager Assets] 。

发布资产或文件夹后，Brand Portal中的用户便可以使用该资产或文件夹。

如果您随后对[!DNL Assets]中的原始资产或文件夹进行了修改，则在重新发布资产或文件夹之前，这些更改不会反映在Brand Portal中。 此功能可确保在 Brand Portal 中不会出现进行中的更改。只有管理员发布的已批准更改才会出现在 Brand Portal 中。

## 将文件夹发布到 Brand Portal {#publish-folders-to-brand-portal-1}

1. 在[!DNL Assets]界面中，将鼠标悬停在所需文件夹上，然后从快速操作中选择&#x200B;**[!UICONTROL 发布]**&#x200B;选项。

   或者，选择所需的文件夹并执行进一步的步骤。

   ![publish2bp](assets/publish2bp.png)

2. **立即发布文件夹**

   要将选定文件夹发布到 Brand Portal，请执行以下任一操作：

   * 在工具栏中，选择&#x200B;**[!UICONTROL 快速发布]**。然后，从菜单中选择&#x200B;**[!UICONTROL 发布到Brand Portal]**。
   * 在工具栏中，选择&#x200B;**[!UICONTROL 管理发布]**。

3. 然后，从&#x200B;**[!UICONTROL Action]**&#x200B;中选择&#x200B;**[!UICONTROL Publish to Brand Portal]**，从&#x200B;**[!UICONTROL Scheduling]**&#x200B;中选择&#x200B;**[!UICONTROL Now]**。 点按&#x200B;**[!UICONTROL Next]。**
4. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中，确认您的选择，然后点按&#x200B;**[!UICONTROL 发布到Brand Portal]**。

   此时将显示一条消息，表明文件夹已排队等候发布到 Brand Portal。登录到Brand Portal界面以查看已发布的文件夹。

   **稍后发布文件夹**

   要计划在稍后的日期或时间将资产文件夹发布到Brand Portal工作流，请执行以下操作：

   1. 选择要发布的资产/文件夹后，从顶部工具栏中选择&#x200B;**[!UICONTROL 管理发布]** 。
   2. 在&#x200B;**[!UICONTROL 管理发布]**&#x200B;页面上，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 发布到Brand Portal]**，然后从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL 稍后]**。

      ![publishlaterbp](assets/publishlaterbp.png)

   3. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按&#x200B;**[!UICONTROL Next]**。
   4. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中确认您的选择。点按&#x200B;**[!UICONTROL Next]**。
   5. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定工作流标题。点按&#x200B;**[!UICONTROL 稍后发布]**。

      ![manageschedulepub](assets/manageschedulepub.png)

## 从 Brand Portal 取消发布文件夹 {#unpublish-folders-from-brand-portal}

您可以通过从[!DNL Experience Manager]创作实例中取消发布已发布到Brand Portal的任何资产文件夹，来删除该文件夹。 取消发布原始文件夹后，Brand Portal 用户将无法再使用其副本。

您可以选择快速从Brand Portal中取消发布文件夹，或安排在稍后的日期和时间取消发布文件夹。 要从 Brand Portal 取消发布资产文件夹，请执行以下操作：

1. 从[!DNL Experience Manager]创作实例的[!DNL Assets]界面中，选择要取消发布的文件夹。

   ![publish2bp-1](assets/publish2bp-1.png)

2. 在工具栏中，点按/单击&#x200B;**[!UICONTROL 管理发布]**。

3. **立即从Brand Portal取消发布**

   要快速从Brand Portal中取消发布所需的文件夹，请执行以下操作：

   1. 在&#x200B;**[!UICONTROL 管理发布]**&#x200B;页面上，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 从Brand Portal]**&#x200B;取消发布，从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL Now]**。
   2. 点按/单击&#x200B;**[!UICONTROL 下一步]。**
   3. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中，确认您的选择，然后点按&#x200B;**[!UICONTROL 从Brand Portal取消发布]**。

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **稍后从Brand Portal取消发布**

   要计划将文件夹从Brand Portal发布到稍后的日期和时间，请执行以下操作：

   1. 在&#x200B;**[!UICONTROL 管理发布]**&#x200B;页面上，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 从Brand Portal]**&#x200B;取消发布，从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL 稍后]。**
   2. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按&#x200B;**[!UICONTROL Next]**。
   3. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中，确认您的选择，然后点按&#x200B;**[!UICONTROL 下一个]**。
   4. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定&#x200B;**[!UICONTROL 工作流标题]**。 点按&#x200B;**[!UICONTROL 稍后取消发布]。**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>向Brand Portal发布/取消发布资产的过程与文件夹的相应过程类似。
