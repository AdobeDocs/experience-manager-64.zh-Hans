---
title: 将文件夹发布到Brand Portal
description: 了解如何将文件夹发布和取消发布到Brand Portal。
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1

---


# Publish folders to Brand Portal {#publish-folders-to-brand-portal}

作为Adobe Experience Manager(AEM)资产管理员，您可以将资产和文件夹发布到AEM Assets Brand Portal实例（或将发布工作流计划到以后的日期／时间）。 但是，您必须先将AEM资产与Brand Portal集成。 有关详细信息，请 [参阅配置AEM资产与Brand Portal](configure-aem-assets-with-brand-portal.md)。

发布资产或文件夹后，该资产或文件夹便可供Brand Portal中的用户使用。

如果您随后在AEM资产中对原始资产或文件夹进行了修改，则在重新发布资产或文件夹之前，这些更改不会反映在Brand Portal中。 此功能可确保在Brand Portal中不提供进行中的更改。 只有管理员发布的已批准更改才可在Brand Portal中使用。

## Publish folders to Brand Portal {#publish-folders-to-brand-portal-1}

1. 在AEM资产界面中，将指针悬停在所需的文件夹上，然后从快速操 **[!UICONTROL 作中选择]** “发布”选项。

   或者，选择所需的文件夹，然后执行后续步骤。

   ![publish2bp](assets/publish2bp.png)

2. **立即发布文件夹**

   要将选定文件夹发布到Brand Portal，请执行以下任一操作：

   * 从工具栏中，选择“快 **[!UICONTROL 速发布”]**。 然后从菜单中，选择 **[!UICONTROL 发布到Brand Portal]**。
   * 从工具栏中，选择管 **[!UICONTROL 理发布]**。

3. 然后，从“操 **[!UICONTROL 作]** ”中选 **[!UICONTROL 择发布到品牌门户]**，从“计划”中选 **[!UICONTROL 择“]******&#x200B;立即发布”。 点按下 **[!UICONTROL 一步]。**
4. 在范 **[!UICONTROL 围内]**，确认您的选择并点按发 **[!UICONTROL 布到品牌门户]**。

   将显示一条消息，指明文件夹已排队等候发布到Brand Portal。 登录到Brand Portal界面，查看已发布的文件夹。

   **稍后发布文件夹**

   要将资产文件夹的发布计划到Brand Portal工作流程，请在以后的日期或时间执行以下操作：

   1. 选择要发布的资产／文件夹后，从顶 **[!UICONTROL 部的工具栏中选择]** “管理发布”。
   2. 在“管 **[!UICONTROL 理发布]** ”页面上，从Action **[!UICONTROL Portal中选择发布到Brand Portal]** ，然后从Scheduling Portal中选 ************&#x200B;择Publish to Brand Portal。

      ![publishlaterbp](assets/publishlaterbp.png)

   3. 选择激 **[!UICONTROL 活日期]** ，然后指定时间。 点按下 **[!UICONTROL 一步]**。
   4. 在范围中确认您 **[!UICONTROL 的选择]**。 点按下 **[!UICONTROL 一步]**。
   5. 在“工作流”下指定工作流 **[!UICONTROL 标题]**。 点按 **[!UICONTROL 稍后发布]**。

      ![manageschedulepub](assets/manageschedulepub.png)

## Unpublish folders from Brand Portal {#unpublish-folders-from-brand-portal}

您可以通过从AEM作者实例中取消发布已发布到Brand Portal的任何资产文件夹，来删除该文件夹。 取消发布原始文件夹后，Brand Portal用户将无法再使用其副本。

您可以选择快速从Brand Portal中取消发布文件夹，或将其安排在以后的日期和时间内。 要从Brand Portal取消发布资产文件夹，请执行以下操作：

1. 从AEM作者实例的AEM资产界面中，选择要取消发布的文件夹。

   ![publish2bp-1](assets/publish2bp-1.png)

2. 在工具栏中，点按／单击管 **[!UICONTROL 理发布]**。

3. **立即从Brand Portal中取消发布**

   要从Brand Portal快速取消发布所需的文件夹，请执行以下操作：

   1. 在“管 **[!UICONTROL 理发布]** ”页面上，从 **[!UICONTROL 操作]****[!UICONTROL 中选择从Brand Portal中发布和从Scheduling Select Now Phortal中]**********&#x200B;取消发布。
   2. Tap/ click **[!UICONTROL Next].**
   3. 在范 **[!UICONTROL 围内]**，确认您的选择，然后点 **[!UICONTROL 按从Brand Portal取消发布]**。
   ![确认——取消发布](assets/confirm-unpublish.png)

   **稍后从Brand Portal中取消发布**

   要将文件夹从Brand Portal发布到以后的日期和时间，请执行以下操作：

   1. 在“管 **[!UICONTROL 理发布]** ”页面上，从“ **[!UICONTROL 操作]** ”中选 **[!UICONTROL 择“从Brand Portal中发布”和“Scheduling Select Later]** ” ******中的取消发布。**
   2. 选择激 **[!UICONTROL 活日期]** ，然后指定时间。 点按下 **[!UICONTROL 一步]**。
   3. 在范 **[!UICONTROL 围内]**，确认您的选择并点 **[!UICONTROL 按下一步]**。
   4. 在“工作流 **[!UICONTROL ”下指定工作]** 流 **[!UICONTROL 标题]**。 点按 **[!UICONTROL 稍后取消发布]。**

      ![取消发布工作流](assets/unpublishworkflows.png)


>[!NOTE]
>
>将资产发布到／从Brand Portal取消发布的过程与文件夹的相应过程类似。
