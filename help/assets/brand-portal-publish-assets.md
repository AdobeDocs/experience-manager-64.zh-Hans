---
title: 将文件夹发布到 Brand Portal
description: 了解如何将资产发布和取消发布到Brand Portal。
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 35%

---


# 将资产发布到 Brand Portal {#publish-assets-to-brand-portal}

作为Adobe Experience Manager(AEM)资产管理员，您可以将资产发布到您的组织的AEM Assets品牌门户实例(或将发布工作流计划到以后的日期／时间)。 但是，您必须首先使用Brand Portal配置AEM Assets。 有关详细信息，请参阅[使用 Brand Portal 配置 AEM Assets](configure-aem-assets-with-brand-portal.md)。

在发布资产后，Brand Portal中的用户可使用该资产。

如果您随后对AEM Assets的原始资产进行了修改，则在您重新发布资产之前，这些更改不会反映在Brand Portal中。 此功能可确保在 Brand Portal 中不会出现进行中的更改。只有管理员发布的已批准更改才会出现在 Brand Portal 中。

复制成功后，您可以将资产、文件夹和集合发布到Brand Portal。 要将资产发布到Brand Portal，请按照以下步骤操作：

>[!NOTE]
>
>Adobe 建议实施错峰发布，最好在非高峰时段发布，这样 AEM 作者就不会占用过多的资源。

1. 从“资产”控制台中，将指针悬停在所需的资产上，然后 **[!UICONTROL 从快速操]** 作中选择“发布”选项。

   或者，选择要发布到Brand Portal的资产。

   ![publish2bp-2](assets/publish2bp-2.png)

2. 要将资产发布到Brand Portal，可以使用以下两个选项：
   * [立即发布资产](#publish-now)
   * [稍后发布资产](#publish-later)

## 立即发布资产 {#publish-now}

要将选定资产发布到 Brand Portal，请执行以下任一操作：

* 在工具栏中，选择&#x200B;**[!UICONTROL 快速发布]**。Then from the menu, select **[!UICONTROL Publish to Brand Portal]**.

* 在工具栏中，选择&#x200B;**[!UICONTROL 管理发布]**。

   1. 然后，从操 **[!UICONTROL 作中]** ，选 **[!UICONTROL 择发布到品牌门户]**，从计划 **[!UICONTROL 中选]** 择 **[!UICONTROL 立即]**&#x200B;发布。 Tap/ click **[!UICONTROL Next].**

   2. 在范 **[!UICONTROL 围内]**，确认您的选择，然后点按／单 **[!UICONTROL 击发布到品牌门户]**。

此时将显示一条消息，表明资产已排队等候发布到 Brand Portal。登录到Brand Portal界面，以查看已发布的资产。

## 稍后发布资产 {#publish-later}

要计划在稍后的日期或时间将资产发布到 Brand Portal，请执行以下操作：

1. 选择要发布的资产／文件夹后，请从顶 **[!UICONTROL 部的工具栏]** 中选择管理发布。
2. 在“管 **[!UICONTROL 理发布]** ”页面上，从“ **[!UICONTROL 操作”中选择“发布到品牌门户]** ”，然 **[!UICONTROL 后从Scheduling Portal中]**********&#x200B;选择“稍后发布”。

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。Tap/ click **[!UICONTROL Next]**.
4. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。Tap/ click **[!UICONTROL Next]**.
5. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定工作流标题。Tap/ click **[!UICONTROL Publish Later]**.

   ![publishworkflow](assets/publishworkflow.png)

现在，登录到Brand Portal，查看已发布的资产是否在Brand Portal界面上可用。

![bp_631_landing_page](assets/bp_landing_page.png)
