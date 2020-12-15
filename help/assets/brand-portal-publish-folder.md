---
title: 将文件夹发布到 Brand Portal
description: 了解如何将文件夹发布和取消发布到Brand Portal。
contentOwner: VG
translation-type: tm+mt
source-git-commit: 33210032c45e38963aed429e70eec4095c5d75f1
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 27%

---


# 将文件夹发布到 Brand Portal{#publish-folders-to-brand-portal}

作为Adobe Experience Manager(AEM)资产管理员，您可以将资产和文件夹发布到您组织的AEM Assets品牌门户实例(或将发布工作流计划到以后的日期／时间)。 但是，您必须首先将AEM Assets与Brand Portal集成。 有关详细信息，请参阅[使用 Brand Portal 配置 AEM Assets](configure-aem-assets-with-brand-portal.md)。

发布资产或文件夹后，Brand Portal中的用户便可使用该资产或文件夹。

如果您随后对AEM Assets的原始资产或文件夹进行了修改，则在您重新发布资产或文件夹之前，这些更改不会反映在Brand Portal中。 此功能可确保在 Brand Portal 中不会出现进行中的更改。只有管理员发布的已批准更改才会出现在 Brand Portal 中。

## 将文件夹发布到 Brand Portal{#publish-folders-to-brand-portal-1}

1. 从AEM Assets界面，将指针悬停在所需的文件夹上，然后从快速操作中选择&#x200B;**[!UICONTROL 发布]**&#x200B;选项。

   或者，选择所需的文件夹，然后执行后续步骤。

   ![publish2bp](assets/publish2bp.png)

2. **立即发布文件夹**

   要将选定文件夹发布到 Brand Portal，请执行以下任一操作：

   * 在工具栏中，选择&#x200B;**[!UICONTROL 快速发布]**。然后，从菜单中选择&#x200B;**[!UICONTROL 发布到品牌门户]**。
   * 在工具栏中，选择&#x200B;**[!UICONTROL 管理发布]**。

3. 然后，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 发布到品牌门户]**，从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL Now]**。 点按&#x200B;**[!UICONTROL 下一步]。**
4. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中，确认您的选择，然后点按&#x200B;**[!UICONTROL 发布到品牌门户]**。

   此时将显示一条消息，表明文件夹已排队等候发布到 Brand Portal。登录到Brand Portal界面，查看已发布的文件夹。

   **稍后发布文件夹**

   要将资产文件夹的发布计划到Brand Portal工作流，请在以后的日期或时间执行以下操作：

   1. 选择要发布的资产／文件夹后，从顶部的工具栏中选择&#x200B;**[!UICONTROL 管理发布]**。
   2. 在&#x200B;**[!UICONTROL 管理发布]**&#x200B;页面上，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 发布到品牌门户]**，然后从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL 稍后]**。

      ![publishlaterbp](assets/publishlaterbp.png)

   3. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按&#x200B;**[!UICONTROL 下一步]**。
   4. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中确认您的选择。点按&#x200B;**[!UICONTROL 下一步]**。
   5. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定工作流标题。点按&#x200B;**[!UICONTROL 稍后发布]**。

      ![manageschedulepub](assets/manageschedulepub.png)

## 从 Brand Portal 取消发布文件夹{#unpublish-folders-from-brand-portal}

您可以通过从AEM作者实例中取消发布已发布到Brand Portal的任何资产文件夹，来删除该资产文件夹。 取消发布原始文件夹后，Brand Portal 用户将无法再使用其副本。

您可以选择快速从Brand Portal中取消发布文件夹，或在以后的日期和时间计划它。 要从 Brand Portal 取消发布资产文件夹，请执行以下操作：

1. 从AEM作者实例的AEM Assets界面中，选择要取消发布的文件夹。

   ![publish2bp-1](assets/publish2bp-1.png)

2. 在工具栏中，点按／单击&#x200B;**[!UICONTROL 管理发布]**。

3. **立即从Brand Portal中取消发布**

   要快速从Brand Portal中取消发布所需的文件夹，请执行以下操作：

   1. 在&#x200B;**[!UICONTROL 管理发布]**&#x200B;页面上，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 从品牌门户]**&#x200B;取消发布，从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL Now]**。
   2. 点按／单击&#x200B;**[!UICONTROL 下一步]。**
   3. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中，确认您的选择，然后点按&#x200B;**[!UICONTROL 从Brand Portal]**&#x200B;取消发布。

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **稍后从Brand Portal中取消发布**

   要将文件夹从Brand Portal发布计划到以后的日期和时间，请执行以下操作：

   1. 在&#x200B;**[!UICONTROL 管理发布]**&#x200B;页面上，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 从品牌门户]**&#x200B;取消发布，从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL 稍后]。**
   2. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按&#x200B;**[!UICONTROL 下一步]**。
   3. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中，确认您的选择，然后点按&#x200B;**[!UICONTROL 下一步]**。
   4. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定&#x200B;**[!UICONTROL 工作流标题]**。 点按&#x200B;**[!UICONTROL 稍后取消发布]。**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>将资产发布／取消发布到／从Brand Portal的过程与文件夹的相应过程类似。
