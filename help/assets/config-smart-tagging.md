---
title: 使用智能内容服务配置资产标记。
description: 了解如何使用智能内容服务在 [!DNL Adobe Experience Manager]中配置智能标记和增强的智能标记。
contentOwner: AG
translation-type: tm+mt
source-git-commit: ddfcb74451f41cea911700a64abceaaf47e7af49
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 34%

---


# 使用智能内容服务{#configure-asset-tagging-using-the-smart-content-service}配置资产标记

可以使用[!DNL Adobe Developer Console]将[!DNL Adobe Experience Manager]与智能内容服务集成。 使用此配置从[!DNL Experience Manager]中访问智能内容服务。

文章详细列出了配置智能内容服务所需的以下主要任务。 在后端，[!DNL Experience Manager]服务器使用[!DNL Adobe Developer Console]网关验证您的服务凭据，然后将请求转发给智能内容服务。

1. [在中创建智](#obtain-public-certificate) 能内容服 [!DNL Experience Manager] 务配置以生成公钥。为 OAuth 集成[获取公共证书](#obtain-public-certificate)。

1. [在 Adobe 开发人员控制台中创建集成](#create-adobe-i-o-integration)，并上传生成的公共密钥。

1. [使用API](#configure-smart-content-service) 密钥和其他凭据配置您的部署 [!DNL Adobe Developer Console]。

1. [测试配置](#validate-the-configuration)。

1. （可选）[在资产上传时启用自动标记](#enable-smart-tagging-in-the-update-asset-workflow-optional)。

## 前提条件 {#prerequisites}

在使用智能内容服务之前，请确保在[!DNL Adobe Developer Console]上创建集成：

* 具备拥有组织管理员权限的 Adobe ID 帐户。

* 您的组织已启用智能内容服务。

要启用增强的智能标记，除上述功能外，还要安装最新的[Experience Manager服务包](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)。

## 创建智能内容服务配置以获取公共证书{#obtain-public-certificate}

公共证书允许您对[!DNL Adobe Developer Console]上的用户档案进行身份验证。

1. 在[!DNL Experience Manager]用户界面中，访问&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL 旧Cloud Services]**。

1. 在Cloud Services页面中，单击&#x200B;**[!UICONTROL 资产智能标记]**&#x200B;下的&#x200B;**[!UICONTROL 立即配置]**。

1. 在&#x200B;**[!UICONTROL 创建配置]**&#x200B;对话框中，指定智能标记配置的标题和名称。 单击&#x200B;**[!UICONTROL 创建]**。

1. 在&#x200B;**[!UICONTROL AEM智能内容服务]**&#x200B;对话框中，使用以下值：

   **[!UICONTROL 服务 URL]**: `https://mc.adobe.io/marketingcloud/smartcontent`

   **[!UICONTROL 授权服务器]**: `https://ims-na1.adobelogin.com`

   现在将其他字段留空（稍后提供）。 单击&#x200B;**[!UICONTROL 确定]**。

   ![Experience Manager智能内容服务对话框，用于提供内容服务URL](assets/aem_scs.png)


   *图：用于提供内容服务URL的智能内容服务对话框*

   >[!NOTE]
   >
   >作为[!UICONTROL 服务URL]提供的URL无法通过浏览器访问，并生成404错误。 配置工作正常，与[!UICONTROL 服务URL]参数的值相同。 有关总体服务状态和维护计划，请参阅[https://status.adobe.com](https://status.adobe.com)。

1. 单击&#x200B;**[!UICONTROL 下载OAuth集成的公共证书]**，然后下载公共证书文件`AEM-SmartTags.crt`。

   ![为智能标记服务创建的设置的表示形式](assets/smart-tags-download-public-cert.png)


   *图：智能标记服务的设置*

### 证书过期{#certrenew}时重新配置

证书过期后，它不再受信任。 无法续订已过期的证书。要添加新证书，请执行以下步骤。

1. 以管理员身份登录 [!DNL Experience Manager] 部署。单击&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 安全]** > **[!UICONTROL 用户]**。

1. 找到并单击 **[!UICONTROL dam-update-service]** 用户。单击&#x200B;**[!UICONTROL 密钥库]**&#x200B;选项卡。

1. 删除包含已过期证书的现有 **[!UICONTROL similaritysearch]** KeyStore。单击&#x200B;**[!UICONTROL 保存并关闭]**。

   ![删除密钥库中现有的相似性搜索条目以添加新的安全证书](assets/smarttags_delete_similaritysearch_keystore.png)

   *图：删除 Keystore 中的现有 `similaritysearch` 条目以添加新的安全证书。*

1. 导航到&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 云服务]** > **[!UICONTROL 旧版云服务]**。单击 **[!UICONTROL 资产智能标记]** >显 **[!UICONTROL 示配置]** >可 **[!UICONTROL 用配置]**。 单击所需的配置。

1. 要下载公共证书，请单击&#x200B;**[!UICONTROL 下载OAuth集成的公共证书]**。

1. 访问[https://console.adobe.io](https://console.adobe.io)并导航到&#x200B;**[!UICONTROL 集成]**&#x200B;页面上的现有智能内容服务。 上传新证书。 有关详细信息，请参阅[创建Adobe开发者控制台集成](#create-adobe-i-o-integration)中的说明。

## 创建Adobe开发者控制台集成{#create-adobe-i-o-integration}

要使用智能内容服务API，请在Adobe开发者控制台中创建集成，以获取[!UICONTROL API密钥](在Adobe开发者控制台集成的[!UICONTROL 客户端ID]字段中生成)、[!UICONTROL 技术帐户ID]、[!UICONTROL 组织[!UICONTROL &lt;a10/>资产智能标记服务设置]中云配置的ID]和[!UICONTROL 客户端机密]。[!DNL Experience Manager]

1. 在浏览器中访问 [https://console.adobe.io](https://console.adobe.io/)。选择相应的帐户并验证关联的组织角色是否为系统管理员。

1. 创建具有任何所需名称的项目。单击&#x200B;**[!UICONTROL 添加 API]**。

1. 在&#x200B;**[!UICONTROL 添加API]**&#x200B;页面上，选择&#x200B;**[!UICONTROL Experience Cloud]**，然后选择&#x200B;**[!UICONTROL 智能内容]**。 单击&#x200B;**[!UICONTROL 下一步]**。

1. 选择&#x200B;**[!UICONTROL 上传您的公共密钥]**。提供从 [!DNL Experience Manager] 下载的证书文件。此时将显示“[!UICONTROL 公共密钥上传成功]”消息。单击&#x200B;**[!UICONTROL 下一步]**。

   “[!UICONTROL 创建新的服务帐户 (JWT) 凭证]”页面将显示刚刚配置的服务帐户的公共密钥。

1. 单击&#x200B;**[!UICONTROL 下一步]**。

1. 在&#x200B;**[!UICONTROL 选择产品配置文件]**&#x200B;页面上，选择&#x200B;**[!UICONTROL 智能内容服务]**。单击&#x200B;**[!UICONTROL 保存配置的 API]**。

   页面会显示有关配置的更多信息。使此页保持打开状态，以复制这些值并在[!DNL Experience Manager]云配置的[!UICONTROL 资产智能标记服务设置]中添加这些值，以配置智能标记。

   ![在“概述”选项卡中，您可以查看为集成提供的信息。](assets/integration_details.png)

   *图：Adobe开发人员控制台中集成的详细信息*

## 配置智能内容服务{#configure-smart-content-service}

要配置集成，请使用Adobe开发者控制台集成中的[!UICONTROL 技术帐户ID]、[!UICONTROL 组织ID]、[!UICONTROL 客户端机密]和[!UICONTROL 客户端ID]字段的值。 创建智能标记云配置允许验证来自[!DNL Experience Manager]部署的API请求。

1. 在[!DNL Experience Manager]中，导航到&#x200B;**[!UICONTROL 工具>Cloud Service>旧Cloud Services]**&#x200B;以打开[!UICONTROL Cloud Services]控制台。

1. 在&#x200B;**[!UICONTROL 资产智能标记]**&#x200B;下，打开以上创建的配置。 在服务设置页面上，单击&#x200B;**[!UICONTROL 编辑]**。

1. 在 **[!UICONTROL AEM 智能内容服务]**&#x200B;对话框中，为&#x200B;**[!UICONTROL 服务 URL]** 和&#x200B;**[!UICONTROL 授权服务器]**&#x200B;字段使用预填充的值。

1. 对于字段[!UICONTROL Api密钥]、[!UICONTROL 技术帐户ID]、[!UICONTROL 组织ID]和[!UICONTROL 客户机密码]，复制并使用在[Adobe开发者控制台集成](#create-adobe-i-o-integration)中生成的以下值。

   | [!UICONTROL 资产智能标记服务设置] | [!DNL Adobe Developer Console] 集成字段 |
   |--- |--- |
   | [!UICONTROL API 键] | [!UICONTROL 客户端ID] |
   | [!UICONTROL 技术帐户 ID] | [!UICONTROL 技术帐户ID] |
   | [!UICONTROL 组织 ID] | [!UICONTROL 组织 ID] |
   | [!UICONTROL 客户端密钥] | [!UICONTROL 客户端机密] |

## 验证配置 {#validate-the-configuration}

完成配置后，使用JMX MBean验证配置。 要验证，请按照以下步骤操作。

1. 访问`https://[aem_server]:[port]`的[!DNL Experience Manager]服务器。

1. 转到&#x200B;**[!UICONTROL 工具>操作> Web Console]**&#x200B;以打开OSGi控制台。 单击&#x200B;**[!UICONTROL 主> JMX]**。

1. 单击&#x200B;**[!UICONTROL com.day.cq.dam.similaritysearch.internal.impl]**。 它打开&#x200B;**[!UICONTROL SimilaritySearch其他任务]**。

1. 单击&#x200B;**[!UICONTROL validateConfigs()]**。 在&#x200B;**[!UICONTROL 验证配置]**&#x200B;对话框中，单击&#x200B;**[!UICONTROL 调用]**。

   验证结果将显示在同一对话框中。

## 在DAM更新资产工作流中启用智能标记（可选）{#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. 在[!DNL Experience Manager]中，转至&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL 工作流]** > **[!UICONTROL 模型]**。

1. 在&#x200B;**[!UICONTROL 工作流模型]**&#x200B;页面上，选择 **[!UICONTROL DAM 更新资产]**&#x200B;工作流模式。

1. 单击工具栏中的&#x200B;**[!UICONTROL 编辑]**。

1. 展开侧面板以显示步骤。拖动 DAM 工作流部分中可用的&#x200B;**[!UICONTROL 智能标记资产]**&#x200B;步骤，并将其放在&#x200B;**[!UICONTROL 流程缩略图]**&#x200B;步骤之后。

   ![在 DAM 更新资产工作流中的流程缩略图步骤之后添加智能标记资产步骤](assets/smart-tag-in-dam-update-asset-workflow.png)

   *图：在 DAM 更新资产工作流中的流程缩略图步骤之后添加智能标记资产步骤。*

1. 在编辑模式下打开该步骤。在&#x200B;**[!UICONTROL 高级设置]**&#x200B;下，确保选中&#x200B;**[!UICONTROL 处理程序前进]**&#x200B;选项。

   ![配置DAM更新资产工作流并添加智能标记步骤](assets/smart-tag-step-properties-workflow1.png)


   *图：配置DAM更新资产工作流并添加智能标记步骤*

1. 在&#x200B;**[!UICONTROL 参数]**&#x200B;选项卡中，如果希望完成工作流，请选择&#x200B;**[!UICONTROL 忽略错误]**，即使自动标记步骤失败也是如此。

   ![配置DAM更新资产工作流以添加智能标记步骤和提前选择处理程序](assets/smart-tag-step-properties-workflow2.png)


   *图：配置DAM更新资产工作流以添加智能标记步骤和提前选择处理程序*

   要在上传资产时标记资产，而不考虑是否对文件夹启用了智能标记，请选择&#x200B;**[!UICONTROL 忽略智能标记标志]**。

   ![配置DAM更新资产工作流以添加智能标记步骤并选择忽略智能标记标记](assets/smart-tag-step-properties-workflow3.png)


   *图：配置DAM更新资产工作流以添加智能标记步骤并选择忽略智能标记标记*

1. 单击&#x200B;**[!UICONTROL 确定]**，以关闭流程步骤，然后保存工作流。

>[!MORELIKETHIS]
>
>* [管理智能标记](managing-smart-tags.md)
>* [智能标记概述和培训方法](enhanced-smart-tags.md)
>* [培训智能内容服务的准则和规则](smart-tags-training-guidelines.md)

