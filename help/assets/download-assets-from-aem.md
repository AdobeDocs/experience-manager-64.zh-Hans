---
title: 从下载数字资产 [!DNL Adobe Experience Manager].
description: 了解如何从下载资产 [!DNL Adobe Experience Manager] 以及启用或禁用下载功能。
contentOwner: AG
feature: Asset Management,Asset Distribution
role: User
exl-id: bfe4d597-1080-4de5-a100-73a5175863d7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 2%

---

# 从下载资产 [!DNL Adobe Experience Manager] {#download-assets-from-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以下载资产，包括静态和动态演绎版。 或者，您也可以直接从发送包含指向资产链接的电子邮件 [!DNL Adobe Experience Manager Assets]. 下载的资产捆绑在ZIP文件中。 对于导出作业，压缩的ZIP文件的最大文件大小为1 GB。 每个导出作业最多允许资产总数为500个。

>[!NOTE]
>
>电子邮件的收件人必须是 `dam-users` 群组，访问电子邮件中的ZIP下载链接。 要能够下载资产，成员必须有权启动可触发资产下载的工作流。

无法下载资产类型图像集、旋转集、混合媒体集和轮播集。

要下载资产，请执行以下步骤：

1. 在AEM的左上角，点按 [!DNL Experience Manager] 徽标，然后在左边栏中，点按 **[!UICONTROL 导航]**.
1. 在导航页面上，点按 **[!UICONTROL 资产]** > **[!UICONTROL 文件。]**
1. 导航到包含要下载的资产的文件夹。
1. 选择文件夹，或在文件夹中选择一个或多个资产。
1. 在工具栏中，点按 **[!UICONTROL 下载。]**

   ![从Experience Manager Assets下载资产时可用的选项](/help/assets/assets/asset_download_dialog.png)

   *图：下载对话框选项。*

1. 在“下载”对话框中，选择所需的下载选项。

   | 导出或下载选项 | 描述 |
   |---|---|
   | **[!UICONTROL 为每个资产创建单独的文件夹]** | 选择此选项可将您下载的每个资产（包括嵌套在资产父文件夹下的子文件夹中的资产）包含到本地计算机上的一个文件夹中。 如果未选择此选项，则默认情况下将忽略文件夹层次结构，所有资产都会下载到本地计算机的一个文件夹中。 |
   | **[!UICONTROL 电子邮件]** | 系统会向用户发送电子邮件通知。 标准电子邮件模板可在以下位置使用：<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`。</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`。</li></ul> 在部署过程中自定义的模板可在以下位置使用： <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`。</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`。</li></ul>您可以在以下位置存储特定于租户的自定义模板：<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`。</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`。</li></ul> |
   | **[!UICONTROL Assets]** | 选择此选项可下载其原始形式的资产，而不包含任何演绎版。<br>如果原始资产具有子资产，则子资产选项可用。 |
   | **[!UICONTROL 演绎版]** | 演绎版是资产的二进制表示形式。 资产具有主要表示形式 — 上传文件的表示形式。 它们可以有任意数量的表示形式。 <br> 通过此选项，您可以选择要下载的演绎版。 可用的演绎版取决于您选择的资产。 如果资产具有任何演绎版，则选项将可用。 |
   | **[!UICONTROL 动态演绎版]** | 选择此选项可实时生成一系列替代演绎版。 当您选择此选项时，您还可以从 [图像预设](image-presets.md) 列表。 <br>此外，您还可以选择大小和单位、格式、色彩空间、分辨率以及任何可选的图像修饰符（如反转图像）。 仅当您具有 [!DNL Dynamic Media] 已启用。 |

1. 在对话框中，点按 **[!UICONTROL 下载。]**.

选择要下载的文件夹时，将下载该文件夹下的完整资产层次结构。 要在单个文件夹中包含您下载的每个资产（包括嵌套在父文件夹下的子文件夹中的资产），请选择 **[!UICONTROL 为每个资产创建单独的文件夹]**.

## 启用资产下载Servlet {#enable-asset-download-servlet}

中的默认Servlet [!DNL Experience Manager] 允许经过身份验证的用户发出任意大的并发下载请求，以创建对他们可见的资产的ZIP文件，这可能会使服务器和网络过载。 要降低此功能所导致的潜在DoS风险， `AssetDownloadServlet` 对于发布实例，OSGi组件默认处于禁用状态。

要允许从DAM下载资产，例如，在使用资产共享共用或其他类似门户的实施时，通过OSGi配置手动启用Servlet。 Adobe建议将允许的下载大小设置得尽可能低，而不影响日常下载要求。 高值可能会影响性能。

1. 创建具有针对发布运行模式的命名约定的文件夹(`config.publish`): `/apps/<your-app-name>/config.publish`. 要为运行模式定义配置属性，请参阅 [运行模式](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. 在配置文件夹中，创建类型为 `nt:file` 已命名 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. 填充 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` 以下内容。 将下载的最大大小（以字节为单位）设置为值 `asset.download.prezip.maxcontentsize`. 以下示例将ZIP下载的最大大小配置为不超过100千字节。

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## 禁用资产下载Servlet {#disable-asset-download-servlet}

的 `Asset Download Servlet` 可在 [!DNL Experience Manager] 通过更新调度程序配置以阻止任何资产下载请求来发布实例。 也可以直接通过OSGi控制台手动禁用Servlet。

1. 要通过调度程序配置阻止资产下载请求，请编辑 `dispatcher.any` 配置，并向添加规则 [过滤器区域](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring-access-to-content-filter). `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. 要在发布实例上禁用OSGi组件，请访问OSGi控制台，网址为 `http://[aem_server]:[port]/system/console/components`. 定位 `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` 单击 **[!UICONTROL 禁用]**.

>[!MORELIKETHIS]
>
>* [下载受DRM保护的资产](drm.md).
>* [在Win或Mac桌面上使用Experience Manager桌面应用程序下载资产](https://helpx.adobe.com/cn/experience-manager/desktop-app/aem-desktop-app.html).
>* [从支持的Adobe Creative Cloud应用程序中使用Adobe资产链接下载资产](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html).

