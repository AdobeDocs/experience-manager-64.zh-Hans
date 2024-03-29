---
title: Digital Rights Management [!DNL Adobe Experience Manager Assets].
description: 了解如何在 [!DNL Experience Manager].
contentOwner: AG
feature: DRM,Asset Management
role: User,Admin
exl-id: 3eea4983-9dd5-4d69-ad93-3cd37a656d22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1466'
ht-degree: 7%

---

# 资源的 Digital Rights Management {#digital-rights-management-in-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

数字资产通常与指定使用条款和持续时间的许可证相关联。 因为 [!DNL Adobe Experience Manager Assets] 与 [!DNL Experience Manager] 平台中，您可以高效地管理资产到期信息和资产状态。 您还可以将授权信息与资产关联。

## 资产过期 {#asset-expiration}

资产到期是强制执行资产许可证要求的有效方式。 它可确保已发布的资产在过期时取消发布，这样就不会发生任何许可证违规的情况。 没有管理员权限的用户无法编辑、复制、移动、发布和下载已过期的资产。

您可以在 [!DNL Assets] 控制台。

![expired_flag_card](assets/expired_flag_card.png)

*图：在卡片视图中，卡片上的标记表示已过期的资产。*

![expired_flag_list](assets/expired_flag_list.png)

*图：在列表视图中， [!UICONTROL 状态] 列显示 [!UICONTROL 过期] 横幅。*

您可以在 [!UICONTROL 时间轴] 在左边栏中。

![chlimage_1-144](assets/chlimage_1-144.png)

>[!NOTE]
>
>对于处于不同时区的用户，资产的过期日期会以不同的方式显示。

您还可以在 **[!UICONTROL 引用]** 边栏。 它可管理复合资产与引用的子资产、收藏集和项目之间的资产到期状态和关系。

1. 导航到要查看其引用网页和复合资产的资产。
1. 选择资产，然后单击 [!DNL Experience Manager] 徽标。

   ![chlimage_1-145](assets/chlimage_1-145.png)

1. 选择 **[!UICONTROL 引用]** 中。

   ![chlimage_1-146](assets/chlimage_1-146.png)

   对于已过期的资产，引用边栏会显示到期状态 **[!UICONTROL 资产已过期]** 在顶部。

   ![chlimage_1-147](assets/chlimage_1-147.png)

   如果资产已过期的子资产，则引用边栏会显示状态 **[!UICONTROL 资产已过期子资产]**.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### 搜索已过期的资产 {#search-expired-assets}

您可以在“搜索”面板中搜索过期的资产，包括过期的子资产。

1. 在 [!DNL Assets] 控制台中，单击 **[!UICONTROL 搜索]** 在工具栏中显示Omnisearch框。

   ![chlimage_1-149](assets/chlimage_1-149.png)

1. 将光标置于Omnisearch框中，按Enter键以显示搜索结果页面。

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. 单击 [!DNL Experience Manager] 徽标以显示搜索面板。

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. 单击 **[!UICONTROL 到期状态]** 选项来展开它。

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. 选择 **[!UICONTROL 过期]**. 过期的资产会显示在搜索结果中。

   ![chlimage_1-153](assets/chlimage_1-153.png)

当您选择 **[!UICONTROL 过期]** 选项， [!DNL Assets] 控制台仅显示复合资产引用的已过期资产和子资产。 在子资产过期后，不会立即显示引用已过期子资产的复合资产。 而是会在 [!DNL Experience Manager] 检测下次计划程序运行时，它们是否引用过期的子资产。

如果您将已发布资产的过期日期修改为早于当前计划程序周期的日期，计划仍会在下次运行时将此资产检测为已过期资产，并相应地反映状态。

此外，如果故障或错误阻止调度程序检测当前周期中的过期资产，则调度程序在下一个周期中重新检查这些资产并检测其过期状态。

启用 [!DNL Assets] 控制台以显示引用的复合资产以及过期的子资产，请配置 **[!UICONTROL Adobe CQ DAM到期通知]** 工作流 [!DNL Experience Manager] 配置管理器。

1. 打开 [!DNL Experience Manager] 配置管理器。
1. 选择 **[!UICONTROL Adobe CQ DAM到期通知]**. 默认情况下， **[!UICONTROL 基于时间的调度程序]** ，该设置会安排作业在特定时间检查资产是否已过期的子资产。 作业完成后，已过期的子资产和引用的资产会在搜索结果中显示为已过期。

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. 要定期运行该作业，请清除&#x200B;**[!UICONTROL 基于时间的计划程序规则]**&#x200B;字段，并在&#x200B;**[!UICONTROL 周期性计划程序]**&#x200B;字段中修改时间（以秒为单位）。例如，示例表达式“0 0 0 &amp;ast; &amp;ast; ?”会在 00 小时开始作业。
1. 选择 **[!UICONTROL 发送电子邮件]** ，以在资产过期时接收电子邮件。

   >[!NOTE]
   >
   >仅资产创建者（将特定资产上传到的人员） [!DNL Assets])会在资产过期时收到一封电子邮件。 请参阅 [如何配置电子邮件通知](/help/sites-administering/notification.md) 有关在整个 [!DNL Experience Manager] 级别。

1. 在 **[!UICONTROL 以秒为单位的先前通知]** 字段，以秒为单位指定当您想要收到有关到期的通知时资产过期的时间。 如果您是管理员或资产创建者，则会在资产过期前收到一条消息，通知您资产将在指定的时间后过期。

   资产过期后，您会收到另一则确认到期的通知。 此外，会停用已过期的资产。

1. 单击“**[!UICONTROL 保存]**”。

## 资产状态 {#asset-states}

的 [!DNL Assets] 控制台可以显示资产的各种状态。 根据特定资产的当前状态，其卡片视图会显示一个用于描述其状态的标签，例如已过期、已发布、已批准、已拒绝等。

1. 在 [!DNL Assets] 用户界面中，选择一个资产。

   ![chlimage_1-155](assets/chlimage_1-155.png)

1. 单击 **[!UICONTROL 发布]** 中。 如果你看不到 **发布** 在工具栏上，单击 **[!UICONTROL 更多]** 在工具栏上并找到 **[!UICONTROL 发布]** 选项。

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. 选择 **[!UICONTROL 发布]** ，然后关闭确认对话框。
1. 退出选择模式。 资产的发布状态显示在卡片视图中资产缩略图的底部。 在列表视图中，已发布列显示资产发布的时间。

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. 要显示其资产详细信息页面，请在 [!DNL Assets] 界面，选择资产并单击 **[!UICONTROL 属性]**.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. 在高级选项卡中，从 **[!UICONTROL 过期]** 字段。

   ![在“过期”字段中设置资产过期日期和时间](assets/chlimage_1-159.png)

   *图： [!UICONTROL 高级] 选项卡 [!UICONTROL 属性] 页面来设置资产过期时间。*

1. 单击 **[!UICONTROL 保存]** 然后单击 **[!UICONTROL 关闭]** 以显示资产控制台。
1. 资产的发布状态会在卡片视图中资产缩略图的底部显示过期状态。 在列表视图中，资产的状态显示为 **[!UICONTROL 过期]**.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. 在 [!DNL Assets] 控制台中，选择文件夹并在文件夹上创建审核任务。
1. 审核和批准/拒绝审核任务中的资产，然后单击 **[!UICONTROL 完成]**.
1. 导航到创建审核任务的文件夹。 您批准/拒绝的资产状态将显示在卡片视图的底部。 在列表视图中，批准和到期状态会显示在相应的列中。

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. 要根据资产的状态搜索资产，请单击 **[!UICONTROL 搜索]** 以显示Omnisearch栏。

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. 按返回并单击 [!DNL Experience Manager] 以显示搜索面板。
1. 在搜索面板中，单击 **[!UICONTROL 发布状态]** 选择 **[!UICONTROL 已发布]** 要在 [!DNL Assets].

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. 单击 **[!UICONTROL 批准状态]** ，然后单击相应的选项以搜索已批准或已拒绝的资产。

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. 要根据资产的到期状态搜索资产，请在“搜索”面板中选择&#x200B;**[!UICONTROL 到期状态]**，然后选择相应的选项。

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. 您还可以根据各种搜索彩块化下的状态组合来搜索资产。 例如，您可以通过在搜索彩块化中选择相应的选项，来搜索已在审核任务中批准且尚未过期的已发布资产。

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management [!DNL Assets] {#digital-rights-management-in-assets-1}

此功能强制您在从下载授权资产之前接受许可协议 [!DNL Adobe Experience Manager Assets].

如果您选择受保护的资产，并单击 **[!UICONTROL 下载]**&#x200B;时，系统会将您重定向到许可页面以接受许可协议。 如果您不接受许可协议， **[!UICONTROL 下载]** 选项不可用。

如果选择的资产包含多个受保护的资产，请一次选择一个资产，接受许可协议，然后继续下载资产。

如果满足以下任一条件，则资产会被视为受保护：

* 资产元数据属性 `xmpRights:WebStatement` 指向包含资产许可协议的页面路径。
* 资产元数据属性的值 `adobe_dam:restrictions` 是指定许可协议的原始HTML。

>[!NOTE]
>
>位置 `/etc/dam/drm/licenses` 用于在早期版本中存储许可证 [!DNL Experience Manager] 已弃用。
>
>如果您创建或修改许可证页面，或将其从以前的页面导入 [!DNL Experience Manager] 版本，Adobe建议您将它们存储在 `/apps/settings/dam/drm/licenses` 或 `/conf/&ast;/settings/dam/drm/licenses`.

### 下载受DRM保护的资产 {#downloading-drm-assets}

1. 在卡片视图中，选择要下载的资产，然后单击 **[!UICONTROL 下载]**.
1. 在&#x200B;**[!UICONTROL 版权管理]**&#x200B;页面，从列表中选择要下载的资产。
1. 在 [!UICONTROL 许可证] 窗格，选择 **[!UICONTROL 同意]**. 资产旁边会显示一个复选标记。 单击 **[!UICONTROL 下载]** 选项。

   >[!NOTE]
   >
   >的 **[!UICONTROL 下载]** 仅当您选择同意受保护资产的许可协议时，才会启用选项。 但是，如果您的选择包含受保护和不受保护的资产，则只有受保护的资产会列在窗格中，并且 **[!UICONTROL 下载]** 选项，可下载不受保护的资产。 要同时接受多个受保护资产的许可协议，请从列表中选择资产，然后选择“同 **[!UICONTROL 意”]**。

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. 在对话框中，单击 **[!UICONTROL 下载]** 下载资产或其演绎版。
