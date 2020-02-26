---
title: 使用智能内容服务配置基于AI的标记
description: 了解如何使用智能内容服务在AEM中配置智能标记和增强的智能标记。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90d39315207129aa4fc616e6fffb4bad5c450a7b

---


# 使用智能内容服务配置资产标记 {#configure-asset-tagging-using-the-smart-content-service}

了解如何使用智能内容服务在AEM中配置智能标记和增强的智能标记。

您可以将Adobe Experience Manager(AEM)与智能内容服务集成。 使用此配置可从AEM中访问智能内容服务并自动标记图像。

文章详细介绍了配置智能内容服务所需的以下主要任务。 在后端，AEM服务器在将请求转发到智能内容服务之前，使用Adobe IO网关验证您的服务凭据。

1. 在AEM中创建智能内容服务配置以生成公钥。 获取用于OAuth集成的公共证书。
1. 在Adobe I/O中创建集成并上传生成的公钥。
1. 使用Adobe I/O中的API密钥和其他凭据配置AEM实例。
1. （可选）在资产上传时启用自动标记。

## 前提条件 {#prerequisites}

在使用智能内容服务之前，请确保以下各项在Adobe I/O上创建集成：

* 具有组织管理员权限的Adobe ID帐户。
* 您的组织启用了智能内容服务。

除上述功能外，要启用增强的智能标记，还请安装最新的 [AEM服务包](https://helpx.adobe.com/experience-manager/aem-releases-updates.html)。

## 获取公共证书 {#obtain-public-certificate}

公共证书允许您在Adobe I/O上验证您的配置文件。

1. From the AEM user interface, tap the AEM logo, and go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Legacy Cloud Services]**.

1. 在“云服务”页面中，点按/单击&#x200B;**[!UICONTROL 资产智能标签]**&#x200B;下的&#x200B;**[!UICONTROL 立即配置]**。
1. 在“创 **[!UICONTROL 建配置]** ”对话框中，指定智能标记配置的标题和名称。 点按/单击&#x200B;**[!UICONTROL 创建]**。
1. 在 **[!UICONTROL AEM智能内容服务对话框中]** ，使用以下值：

   **[!UICONTROL 服务 URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL 授权服务器]**: `https://ims-na1.adobelogin.com`

   现在将其他字段留空（稍后提供）。 Tap/click **[!UICONTROL OK]**.

   ![用于提供内容服务URL的AEM智能内容服务对话框](assets/aem_scs.png)

   >[!NOTE]
   >
   >作为服务URL提 [!UICONTROL 供的URL] 无法通过浏览器访问，并生成404错误。 配置与服务URL参数的值相同， [!UICONTROL 工作正常] 。 有关Adobe I/O服务状态和维护计划的整体信息，请参 [阅https://status.adobe.com](https://status.adobe.com)。

1. 点按／单 **[!UICONTROL 击下载用于OAuth集成的公共证书]**，然后下载公共证书文件 `AEM-SmartTags.crt`。

   ![为智能标记服务创建的设置的表示形式](assets/download_link.png)

## 创建Adobe I/O集成 {#create-adobe-i-o-integration}

要使用智能内容服务API，请在Adobe I/O中创建集成，以生成API密钥、技术帐户Id、组织Id和客户端机密。

1. 访问 [https://console.adobe.io](https://console.adobe.io/)。
1. 从“集 **[!UICONTROL 成]** ”页面中，选择您的组织。
1. 点按／单击 **[!UICONTROL 新集成]**。
1. 在“创 **[!UICONTROL 建新集成]** ”页面上，选 **[!UICONTROL 择访问API]**。 点按/单击&#x200B;**[!UICONTROL 继续]**。
1. 在 **[!UICONTROL Experience Cloud]** 下，选择&#x200B;**[!UICONTROL 智能内容]**。点按/单击&#x200B;**[!UICONTROL 继续]**。

   ![创建新集成时，从可用的选项中选择Experience cloud下的智能内容](assets/smart_content.png)

1. 在下一页，选择“新 **[!UICONTROL 建集成”]**。 点按/单击&#x200B;**[!UICONTROL 继续]**。
1. 在“集 **[!UICONTROL 成详细信息]** ”页面上，指定集成网关的名称并添加说明。
1. 在公 **[!UICONTROL 钥证书中]**，上 `AEM-SmartTags.crt` 传您上面下载的文件。
1. Tap/click **[!UICONTROL Create Integration]**.
1. 要查看集成信息，请点按／单击继 **[!UICONTROL 续以查看集成详细信息]**。

   ![在“概述”选项卡中，您可以查看为集成提供的信息。](assets/integration_details.png)

## 配置智能内容服务 {#configure-smart-content-service}

要配置集成，请使用Adobe I/O集成中的“技术帐户ID”、“组织ID”、“客户端机密”、“授权服务器”和API密钥字段的值。 创建智能标记云配置允许验证来自AEM实例的API请求。

1. 在AEM用户界面中，点按／单击AEM徽标。 导航到 **[!UICONTROL 工具>云服务>旧版云服务]** ，以打开云服务控制台。
1. 在资产智 **[!UICONTROL 能标记下]**，打开上面创建的配置。 在服务设置页面上，单击“编 **[!UICONTROL 辑”]**。
1. 在 **[!UICONTROL AEM 智能内容服务]**&#x200B;对话框中，为&#x200B;**[!UICONTROL 服务 URL]** 和&#x200B;**[!UICONTROL 授权服务器]**&#x200B;字段使用预填充的值。
1. 对于字段 API 密钥、技术帐户 ID、组织 ID 和客户端密钥，请使用上面生成的值。

## 验证配置 {#validate-the-configuration}

完成配置后，可使用JMX MBean验证配置。 要验证，请按照以下步骤操作。

1. 在AEM中，要打开OSGi控制台，请单击“工 **[!UICONTROL 具”>“操作”>“Web控制台]**”。 单击“ **[!UICONTROL 主> JMX]**”。
1. 单 **[!UICONTROL 击com.day.cq.dam.similaritysearch.internal.impl]**。 它打开“相似 **[!UICONTROL 性搜索杂项任务”。]**
1. 单击 **[!UICONTROL validateConfigs()]**。 在“验证 **[!UICONTROL 配置]** ”对话框中，单 **[!UICONTROL 击调用]**。

   验证结果将显示在同一对话框中。

## 在DAM更新资产工作流中启用智能标记（可选） {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. 在AEM用户界面中，点按／单击AEM徽标，然后转到工具>工 **[!UICONTROL 作流>模型]**。
1. 在&#x200B;**[!UICONTROL 工作流模型]**&#x200B;页面上，选择 **[!UICONTROL DAM 更新资产]**&#x200B;工作流模式。
1. 点按／单击工 **[!UICONTROL 具栏中]** 的编辑。
1. 展开侧面板以显示步骤。拖动 DAM 工作流部分中可用的&#x200B;**[!UICONTROL 智能标记资产]**&#x200B;步骤，并将其放在&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤之后。

   ![在DAM更新资产工作流中的流程缩略图步骤之后添加智能标记资产步骤](assets/chlimage_1-105.png)

1. 在编辑模式下打开该步骤。在&#x200B;**[!UICONTROL 高级设置]**&#x200B;下，确保选中&#x200B;**[!UICONTROL 处理程序高级]**&#x200B;选项。

   ![chlimage_1-106](assets/chlimage_1-106.png)

1. 在&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡中，如果希望完成工作流，请选择&#x200B;**[!UICONTROL 忽略错误]**，即使自动标记步骤失败也是如此。

   ![chlimage_1-107](assets/chlimage_1-107.png)

   要在上传资产时标记资产，而不管文件夹是否启用了智能标记，请选择忽 **[!UICONTROL 略智能标记标志]**。

   ![chlimage_1-108](assets/chlimage_1-108.png)

1. 点按／单 **[!UICONTROL 击确定]** ，以关闭进程步骤，然后保存工作流。

>[!MORELIKETHIS]
>
>* [了解AEM资产中的智能标记](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html)
>* [对AEM资产使用智能标记](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-use.html)
>* [对AEM资产使用增强的智能标记](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-feature-video-use.html)
>* [在AEM资产中设置增强的智能标记](https://helpx.adobe.com/experience-manager/kt/assets/using/enhanced-smart-tags-technical-video-setup.html)

