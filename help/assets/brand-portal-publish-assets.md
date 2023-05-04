---
title: 将文件夹发布到 Brand Portal
description: 了解如何将资产发布和取消发布到Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: 6b78124d-4022-452f-8d0f-b667de337bf4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 29%

---

# 将资产发布到 Brand Portal {#publish-assets-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

作为Adobe Experience Manager Assets管理员，您可以将资产发布到 [!DNL Experience Manager Assets Brand Portal] 实例（或将发布工作流安排到稍后的日期/时间）。 但是，您必须首先配置 [!DNL Assets] with [!DNL Brand Portal]. 有关详细信息，请参阅 [配置 [!DNL Assets] with [!DNL Brand Portal]](configure-aem-assets-with-brand-portal.md).

发布资产后，Brand Portal中的用户便可以使用该资产。

如果您随后在 [!DNL Assets]，则在重新发布资产之前，所做的更改不会反映在Brand Portal中。 此功能可确保在 Brand Portal 中不会出现进行中的更改。只有管理员发布的已批准更改才会出现在 Brand Portal 中。

复制成功后，您可以将资产、文件夹和收藏集发布到 [!DNL Brand Portal]. 要将资产发布到Brand Portal，请执行以下步骤：

>[!NOTE]
>
>Adobe建议错开发布，最好在非高峰时段发布，以便 [!DNL Experience Manager] 作者不会占用过多的资源。

1. 在“资产”控制台中，将鼠标悬停在所需的资产上，然后选择 **[!UICONTROL 发布]** 选项。

   或者，选择要发布到Brand Portal的资产。

   ![publish2bp-2](assets/publish2bp-2.png)

2. 要将资产发布到Brand Portal，可使用以下两个选项：
   * [立即发布资产](#publish-now)
   * [稍后发布资产](#publish-later)

## 立即发布资产 {#publish-now}

要将选定资产发布到 Brand Portal，请执行以下任一操作：

* 在工具栏中，选择&#x200B;**[!UICONTROL 快速发布]**。然后，从菜单中，选择 **[!UICONTROL 发布到Brand Portal]**.

* 在工具栏中，选择&#x200B;**[!UICONTROL 管理发布]**。

   1. 然后，从 **[!UICONTROL 操作]** 选择 **[!UICONTROL 发布到Brand Portal]**，从 **[!UICONTROL 计划]** 选择 **[!UICONTROL 现在]**. 点按/单击 **[!UICONTROL 下一个].**

   2. 在 **[!UICONTROL 范围]**，确认您的选择，然后点按/单击 **[!UICONTROL 发布到Brand Portal]**.

此时将显示一条消息，表明资产已排队等候发布到 Brand Portal。登录到Brand Portal界面以查看已发布的资产。

## 稍后发布资产 {#publish-later}

要计划在稍后的日期或时间将资产发布到 Brand Portal，请执行以下操作：

1. 选择要发布的资产/文件夹后，请选择 **[!UICONTROL 管理发布]** 工具栏。
2. 开 **[!UICONTROL 管理发布]** 页面，选择 **[!UICONTROL 发布到Brand Portal]** 从 **[!UICONTROL 操作]** 选择 **[!UICONTROL 稍后]** 从 **[!UICONTROL 计划]**.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

3. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按/单击 **[!UICONTROL 下一个]**.
4. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按/单击 **[!UICONTROL 下一个]**.
5. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定工作流标题。点按/单击 **[!UICONTROL 稍后发布]**.

   ![publishworkflow](assets/publishworkflow.png)

现在，登录到Brand Portal ，查看已发布的资产在Brand Portal界面上是否可用。

![bp_631_landing_page](assets/bp_landing_page.png)
