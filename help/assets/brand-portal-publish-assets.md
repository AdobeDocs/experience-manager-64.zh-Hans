---
title: 将文件夹发布到Brand Portal
description: 了解如何将资产发布和取消发布到Brand Portal。
contentOwner: VG
translation-type: tm+mt
source-git-commit: f09853921dec6602952f369982a1563c7e4a9727

---


# Publish assets to Brand Portal {#publish-assets-to-brand-portal}

作为Adobe Experience Manager(AEM)资产管理员，您可以将资产发布到AEM Assets Brand Portal实例（或将发布工作流计划到以后的日期／时间），以供您的组织使用。 但是，您必须首先将AEM资产配置为Brand Portal。 有关详细信息，请 [参阅配置AEM资产与Brand Portal](configure-aem-assets-with-brand-portal.md)。

发布资产后，该资产便可供Brand Portal中的用户使用。

如果您在AEM资产中对原始资产进行了后续修改，则在重新发布资产之前，这些更改不会反映在Brand Portal中。 此功能可确保在Brand Portal中不提供进行中的更改。 只有管理员发布的已批准更改才可在Brand Portal中使用。

复制成功后，您可以将资产、文件夹和集合发布到Brand Portal。 要将资产发布到Brand Portal，请执行以下步骤：

>[!NOTE]
>
>Adobe建议交错发布，最好在非高峰时段发布，这样AEM作者就不会占用过多的资源。

1. 从“资产”控制台中，将指针悬停在所需的资产上，然后从快速操 **[!UICONTROL 作中选择]** “发布”选项。

   或者，选择要发布到Brand Portal的资产。

   ![publish2bp-2](assets/publish2bp-2.png)

2. 要将资产发布到Brand Portal，可以使用以下两个选项：
   * [立即发布资产](#publish-now)
   * [稍后发布资产](#publish-later)

## 立即发布资产 {#publish-now}

要将选定资产发布到Brand Portal，请执行以下任一操作：

* 从工具栏中，选择“快 **[!UICONTROL 速发布”]**。 然后从菜单中，选择 **[!UICONTROL 发布到Brand Portal]**。

* 从工具栏中，选择管 **[!UICONTROL 理发布]**。

   1. 然后，从“操 **[!UICONTROL 作]** ”中选 **[!UICONTROL 择发布到品牌门户]**，从“计划”中选 **[!UICONTROL 择“]******&#x200B;立即发布”。 Tap/ click **[!UICONTROL Next].**

   2. 在范 **[!UICONTROL 围内]**，确认您的选择，然后点按／单 **[!UICONTROL 击发布到品牌门户]**。

将显示一条消息，指明资产已排队等候发布到Brand Portal。 登录到Brand Portal界面，查看已发布的资产。

## 稍后发布资产 {#publish-later}

要计划将资产发布到Brand Portal以后的日期或时间，请执行以下操作：

1. 选择要发布的资产／文件夹后，从顶 **[!UICONTROL 部的工具栏中选择]** “管理发布”。
2. 在“管 **[!UICONTROL 理发布]** ”页面上，从Action **[!UICONTROL Portal中选择发布到Brand Portal]** ，然后从Scheduling Portal中选 ************&#x200B;择Publish to Brand Portal。

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. 选择激 **[!UICONTROL 活日期]** ，然后指定时间。 Tap/ click **[!UICONTROL Next]**.
4. 选择激 **[!UICONTROL 活日期]** ，然后指定时间。 Tap/ click **[!UICONTROL Next]**.
5. 在“工作流”下指定工作流 **[!UICONTROL 标题]**。 点按／单击稍 **[!UICONTROL 后发布]**。

   ![发布工作流](assets/publishworkflow.png)

现在，登录到Brand Portal，查看已发布的资产是否在Brand Portal界面上可用。

![bp_631_landing_page](assets/bp_landing_page.png)
