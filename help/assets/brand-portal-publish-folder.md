---
title: 将文件夹发布到 Brand Portal
description: 了解如何将文件夹发布和取消发布到Brand Portal。
contentOwner: VG
feature: Brand Portal
role: User
exl-id: f41ab750-5780-42ae-a131-5bc748280215
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 26%

---

# 将文件夹发布到 Brand Portal {#publish-folders-to-brand-portal}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

作为Adobe Experience Manager Assets管理员，您可以将资产和文件夹发布到 [!DNL Experience Manager Assets Brand Portal] 实例（或将发布工作流安排到稍后的日期/时间）。 但是，您必须先集成 [!DNL Experience Manager Assets] with [!DNL Brand Portal]. 有关详细信息，请参阅 [配置 [!DNL Experience Manager Assets] 与Brand Portal](configure-aem-assets-with-brand-portal.md).

发布资产或文件夹后，Brand Portal中的用户便可以使用该资产或文件夹。

如果您随后在 [!DNL Assets]，则在重新发布资产或文件夹之前，所做的更改不会反映在Brand Portal中。 此功能可确保在 Brand Portal 中不会出现进行中的更改。只有管理员发布的已批准更改才会出现在 Brand Portal 中。

## 将文件夹发布到 Brand Portal {#publish-folders-to-brand-portal-1}

1. 从 [!DNL Assets] 界面中，将鼠标悬停在所需的文件夹上并选择 **[!UICONTROL 发布]** 选项。

   或者，选择所需的文件夹并执行进一步的步骤。

   ![publish2bp](assets/publish2bp.png)

2. **立即发布文件夹**

   要将选定文件夹发布到 Brand Portal，请执行以下任一操作：

   * 在工具栏中，选择&#x200B;**[!UICONTROL 快速发布]**。然后，从菜单中，选择 **[!UICONTROL 发布到Brand Portal]**.
   * 在工具栏中，选择&#x200B;**[!UICONTROL 管理发布]**。

3. 然后，从 **[!UICONTROL 操作]** 选择 **[!UICONTROL 发布到Brand Portal]**，从 **[!UICONTROL 计划]** 选择 **[!UICONTROL 现在]**. 点按 **[!UICONTROL 下一个].**
4. 在 **[!UICONTROL 范围]**，确认您的选择并点按 **[!UICONTROL 发布到Brand Portal]**.

   此时将显示一条消息，表明文件夹已排队等候发布到 Brand Portal。登录到Brand Portal界面以查看已发布的文件夹。

   **稍后发布文件夹**

   要计划在稍后的日期或时间将资产文件夹发布到Brand Portal工作流，请执行以下操作：

   1. 选择要发布的资产/文件夹后，请选择 **[!UICONTROL 管理发布]** 工具栏。
   2. 开 **[!UICONTROL 管理发布]** 页面，选择 **[!UICONTROL 发布到Brand Portal]** 从 **[!UICONTROL 操作]** 选择 **[!UICONTROL 稍后]** 从 **[!UICONTROL 计划]**.

      ![publishlaterbp](assets/publishlaterbp.png)

   3. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按 **[!UICONTROL 下一个]**.
   4. 在&#x200B;**[!UICONTROL 范围]**&#x200B;中确认您的选择。点按 **[!UICONTROL 下一个]**.
   5. 在&#x200B;**[!UICONTROL 工作流]**&#x200B;下指定工作流标题。点按 **[!UICONTROL 稍后发布]**.

      ![manageschedulepub](assets/manageschedulepub.png)

## 从 Brand Portal 取消发布文件夹 {#unpublish-folders-from-brand-portal}

您可以通过从中取消发布已发布到Brand Portal的任何资产文件夹，来删除该文件夹 [!DNL Experience Manager] 创作实例。 取消发布原始文件夹后，Brand Portal 用户将无法再使用其副本。

您可以选择快速从Brand Portal中取消发布文件夹，或安排在稍后的日期和时间取消发布文件夹。 要从 Brand Portal 取消发布资产文件夹，请执行以下操作：

1. 从 [!DNL Assets] 界面 [!DNL Experience Manager]  创作实例，选择要取消发布的文件夹。

   ![publish2bp-1](assets/publish2bp-1.png)

2. 在工具栏中，点按/单击 **[!UICONTROL 管理发布]**.

3. **立即从Brand Portal取消发布**

   要快速从Brand Portal中取消发布所需的文件夹，请执行以下操作：

   1. 开 **[!UICONTROL 管理发布]** 页面，从 **[!UICONTROL 操作]** 选择 **[!UICONTROL 从Brand Portal取消发布]** 从 **[!UICONTROL 计划]** 选择 **[!UICONTROL 现在]**.
   2. 点按/单击 **[!UICONTROL 下一个].**
   3. 在 **[!UICONTROL 范围]**，确认您的选择并点按 **[!UICONTROL 从Brand Portal取消发布]**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **稍后从Brand Portal取消发布**

   要计划将文件夹从Brand Portal发布到稍后的日期和时间，请执行以下操作：

   1. 开 **[!UICONTROL 管理发布]** 页面，从 **[!UICONTROL 操作]** 选择 **[!UICONTROL 从Brand Portal取消发布]** 从 **[!UICONTROL 计划]** 选择 **[!UICONTROL 稍后].**
   2. 选择&#x200B;**[!UICONTROL 激活日期]**，并指定时间。点按 **[!UICONTROL 下一个]**.
   3. 在 **[!UICONTROL 范围]**，确认您的选择并点按 **[!UICONTROL 下一个]**.
   4. 指定 **[!UICONTROL 工作流标题]** 在 **[!UICONTROL 工作流]**. 点按 **[!UICONTROL 稍后取消发布].**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>向Brand Portal发布/取消发布资产的过程与文件夹的相应过程类似。
