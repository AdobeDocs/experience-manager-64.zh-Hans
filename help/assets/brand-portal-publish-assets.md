---
title: 将文件夹发布到 Brand Portal
description: 了解如何将资产发布和取消发布到Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: de5632ff0ee87a4ded88e792b57e818baf4c01a3
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 30%

---

# 将资产发布到 Brand Portal {#publish-assets-to-brand-portal}

作为Adobe Experience Manager Assets管理员，您可以将资产发布到您组织的[!DNL Experience Manager Assets Brand Portal]实例（或将发布工作流安排到稍后的日期/时间）。 但是，您必须首先使用[!DNL Brand Portal]配置[!DNL Assets]。 有关详细信息，请参阅[使用 [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md)配置 [!DNL Assets] 。

发布资产后，Brand Portal中的用户便可以使用该资产。

如果您随后在[!DNL Assets]中对原始资产进行了修改，则在重新发布资产之前，这些更改不会反映在Brand Portal中。 此功能可确保在 Brand Portal 中不会出现进行中的更改。只有管理员发布的已批准更改才会出现在 Brand Portal 中。

复制成功后，您可以将资产、文件夹和收藏集发布到[!DNL Brand Portal]。 要将资产发布到Brand Portal，请执行以下步骤：

>[!NOTE]
>
>Adobe建议错开发布，最好在非高峰时间发布，这样[!DNL Experience Manager]作者就不会占用过多的资源。

1. 在“资产”控制台中，将鼠标悬停在所需的资产上，然后从快速操作中选择&#x200B;**[!UICONTROL 发布]**&#x200B;选项。

   或者，选择要发布到Brand Portal的资产。

   ![publish2bp-2](assets/publish2bp-2.png)

2. 要将资产发布到Brand Portal，可使用以下两个选项：
   * [立即发布资产](#publish-now)
   * [稍后发布资产](#publish-later)

## 立即发布资产 {#publish-now}

要将选定资产发布到 Brand Portal，请执行以下任一操作：

* 在工具栏中，选择&#x200B;**[!UICONTROL 快速发布]**。然后，从菜单中选择&#x200B;**[!UICONTROL 发布到Brand Portal]**。

* 在工具栏中，选择&#x200B;**[!UICONTROL 管理发布]**。

   1. 然后，从&#x200B;**[!UICONTROL Action]**&#x200B;中选择&#x200B;**[!UICONTROL Publish to Brand Portal]**，从&#x200B;**[!UICONTROL Scheduling]**&#x200B;中选择&#x200B;**[!UICONTROL Now]**。 点按/单击&#x200B;**[!UICONTROL 下一步]。**

   2. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中，确认您的选择，然后点按/单击&#x200B;**[!UICONTROL 发布到Brand Portal]**。

此时将显示一条消息，表明资产已排队等候发布到 Brand Portal。登录到Brand Portal界面以查看已发布的资产。

## 稍后发布资产 {#publish-later}

要计划在稍后的日期或时间将资产发布到 Brand Portal，请执行以下操作：

1. 选择要发布的资产/文件夹后，从顶部工具栏中选择&#x200B;**[!UICONTROL 管理发布]** 。
2. 在&#x200B;**[!UICONTROL 管理发布]**&#x200B;页面上，从&#x200B;**[!UICONTROL 操作]**&#x200B;中选择&#x200B;**[!UICONTROL 发布到Brand Portal]**，然后从&#x200B;**[!UICONTROL 计划]**&#x200B;中选择&#x200B;**[!UICONTROL 稍后]**。

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按/单击&#x200B;**[!UICONTROL 下一步]**。
4. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按/单击&#x200B;**[!UICONTROL 下一步]**。
5. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定工作流标题。点按/单击&#x200B;**[!UICONTROL 稍后发布]**。

   ![publishworkflow](assets/publishworkflow.png)

现在，登录到Brand Portal ，查看已发布的资产在Brand Portal界面上是否可用。

![bp_631_landing_page](assets/bp_landing_page.png)
