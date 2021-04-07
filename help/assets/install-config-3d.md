---
title: 安装和配置 AEM 3D
seo-title: 安装和配置 AEM 3D
description: 了解如何安装和配置AEM 3D
seo-description: 了解如何安装和配置AEM 3D
uuid: a60732ff-fd66-4f29-b901-42a3cfd58b65
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 5898d084-4b45-41bc-ad2e-2fcc65b0392c
exl-id: 5baaef61-5c70-4796-8ae2-44053e855ad9
feature: 3D资产
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1681'
ht-degree: 1%

---

# 安装和配置 AEM 3D {#installing-and-configuring-aem-d}

>[!IMPORTANT]
>
>不再支持AEM 6.4中的AEM 3D。 Adobe建议您使用[AEM中的3D资源功能作为Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html#dynamicmedia)或[AEM 6.5.3或更高版本。](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/assets-3d.html#dynamic)

AEM 3D（版本3.0）的安装和配置涉及以下事项：

1. 安装Autodesk® FBX® SDK库。
1. 下载和安装本机3D代码包。
1. 配置3D资产摄取工作流并重新启动AEM。
1. 验证AEM 3D的设置。

另请参阅[使用3D资产](assets-3d.md)。

另请参阅[AEM 3D资产发行说明](/help/release-notes/aem3d-release-notes.md)，了解先决条件、支持的浏览器和其他重要的发行信息。

另请参阅[使用3D站点组件](using-the-3d-sites-component.md)。

>[!NOTE]
>
>在下载和安装3D包之前，请确保您已成功安装所有必备AEM包。 请参阅[AEM 3D发行说明。](install-config-3d.md)

## 安装Autodesk FBX SDK库{#installing-the-autodesk-fbx-sdk-library}

本机AEM 3D代码需要Autodesk FBX库以支持FBX文件格式。 (Adobe当前无法再分发此库。)

另请参阅[高级配置设置](advanced-config-3d.md)。

1. 登录到安装了AEM的主机。

   * 如果这是Windows Server部署，请以管理员身份登录到服务器。
   * 如果这是MAC或Windows桌面，请确保您具有管理员权限。

1. 使用适用于您的操作系统的链接下载&#x200B;**FBX SDK版本2016.1.2**

   * **Windows**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_vs2010_win.exe)

   * **OS X**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_clang_mac.pkg.tgz)

   * **Linux**

      [https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz](https://download.autodesk.com/us/fbx_release_older/2016.1.2/fbx20161_2_fbxsdk_linux.tar.gz)

1. 安装FBX SDK:

   * Windows. 安装到AEM所在的同一驱动器。
   * Mac。 安装到AEM所在的同一分区。
   * Linux. 解压下载的包，并按照`<yourFBXSDKpath>/Install_FbxFileSdk.txt`中的说明操作。 将SDK安装到`/usr`。

## 下载和安装本机3D代码包{#downloading-and-installing-the-native-d-code-package}

>[!NOTE]
>
>在您继续安装和配置AEM 3D之前，Adobe建议您部署任何适用的服务包和其他相关功能包。 请参阅[AEM 3D发行说明](/help/release-notes/aem3d-release-notes.md)。

另请参阅[高级配置设置](advanced-config-3d.md)。

**要安装本机3D代码包**:

1. 执行下列操作之一：

   * 如果这是Windows Server部署，请以管理员身份登录到服务器。
   * 如果这是Mac或Windows桌面，请确保您具有管理员权限。

1. 确保您拥有可访问AEM的受支持浏览器。

   请参阅[系统要求](/help/release-notes/aem3d-release-notes.md#system-requirements)。

1. 访问[软件分发门户](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)。 找到`AEM-6.4-DynamicMedia-3D`功能包的3.0.1版并下载。

1. 在AEM中，单击&#x200B;**[!UICONTROL 工具>管理>部署>包管理器]**。

1. 将下载的功能包上传到AEM。 找到它并单击&#x200B;**[!UICONTROL 安装]**。

1. 在&#x200B;**[!UICONTROL 安装包]**&#x200B;对话框中，展开&#x200B;**高级设置**，然后将&#x200B;**[!UICONTROL 访问控制处理]**&#x200B;设置为&#x200B;**合并**。
1. 单击&#x200B;**[!UICONTROL 安装]**&#x200B;开始安装软件包。

   文件`sample-3D-content.zip`位于&#x200B;**[!UICONTROL Assets]**&#x200B;根文件夹中。 有关其他信息，请参阅[验证AEM 3D](#validating-the-setup-of-aem-d)的设置。

## 配置3D资产摄取工作流并重新启动AEM {#configuring-the-d-asset-ingestion-workflow-and-restarting-aem}

**要配置3D资产摄取工作流**:

1. 在AEM中，单击AEM徽标以访问全局导航控制台，然后单击&#x200B;**[!UICONTROL 工具]**&#x200B;图标并导航到&#x200B;**[!UICONTROL 工作流>模型]**。
1. 在&#x200B;**[!UICONTROL 工作流模型]**&#x200B;页面上，将指针悬停在&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;工作流上，当出现复选标记时，选择它。

1. 在工具栏上，单击&#x200B;**[!UICONTROL 编辑]**。
1. 在&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;屏幕的AEM浮动面板中，单击工作流右侧的&#x200B;**[!UICONTROL 加号]**&#x200B;图标以展开列表。 在列表中选择&#x200B;**[!UICONTROL 处理步骤]**。
1. 拖动&#x200B;**[!UICONTROL 处理步骤]**&#x200B;并将它放到工作流末尾附近的&#x200B;**[!UICONTROL DAM更新资产工作流已完成]**&#x200B;组件之前的工作流中。

   ![3d_process_step_underaem6-4](assets/3d_process_step_underaem6-4.png)

1. 多次单击新添加的进程步骤。
1. 在&#x200B;**[!UICONTROL 步骤属性]**&#x200B;对话框的&#x200B;**[!UICONTROL 公用]**&#x200B;选项卡的&#x200B;**[!UICONTROL 标题]**&#x200B;字段中，输入适合该流程的说明，如`Process 3D content`。
1. 单击&#x200B;**[!UICONTROL 进程]**&#x200B;选项卡。

1. 从&#x200B;**[!UICONTROL Process]**&#x200B;下拉菜单中，选择&#x200B;**[!UICONTROL Geometric 3D Object Service]**，然后选中&#x200B;**[!UICONTROL Handler Advance]**&#x200B;复选框。

   ![3d_install-process-steppropertysdlg](assets/3d_install-process-steppropertiesdlg.png)

1. 在对话框的右上角附近，单击复选标记图标以返回到DAM更新资产页面。
1. 在&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;页面的右上角附近，单击&#x200B;**[!UICONTROL 同步]**&#x200B;以保存已编辑的工作流模型。
1. 重新启动AEM。

   重新启动后，您便可以上传3D内容并让AEM处理它。

   继续[验证AEM 3D](#validating-the-setup-of-aem-d)的设置。

## 验证AEM 3D {#validating-the-setup-of-aem-d}的设置

1. 在AEM中，单击&#x200B;**[!UICONTROL 工具>资产]**，然后下载`sample-3D-content.zip`并展开下载的文件。 (您现在可以在AEM中删除`sample-3D-content.zip`。)

   确保您在&#x200B;**[!UICONTROL 卡片视图]**&#x200B;中，以在其余步骤中视图上传和处理反馈。

1. 创建名为`test3d`的文件夹以接收测试内容。
1. 将所有文件从`sample-3D-content/images`上载到`test3d`文件夹。
1. 等待上传和处理完成。 您可能需要刷新浏览器。

   将三个`.fbx`文件从`sample-3D-content/`上载到`test3d`文件夹。

   尚未上载.ma模型文件。

1. 在卡片视图中，观察3d资产卡上显示的消息横幅。

   每个资产都会执行多个处理步骤。 当&#x200B;**[!UICONTROL 创建预览...]**&#x200B;处理步骤完成后，卡将更新为缩略图。 完成最终处理后，横幅将替换为&#x200B;**[!UICONTROL NEW]**&#x200B;指示符。

   >[!NOTE]
   >
   >3D处理正在进行中，期望CPU利用率很高。 根据可用的CPU容量，完成所有处理可能需要花费大量时间。

   ![screeshot_2017-01-2518-29-32](assets/screenshot_2017-01-2518-29-32.png)

1. 您现在将学习如何解析文件依赖关系。

   在`stage-helipad.fbx`卡的&#x200B;**[!UICONTROL 未解析的依赖项]**&#x200B;横幅上，单击&#x200B;**[!UICONTROL 感叹号]**&#x200B;图标以导航到资产的属性，并打开&#x200B;**依赖项**&#x200B;选项卡。

   ![chlimage_1-372](assets/chlimage_1-372.png)

1. 单击文件名右侧的&#x200B;**[!UICONTROL 文件夹/放大镜]**&#x200B;图标以打开资产浏览器并解析依赖关系，如下所示：

   ![chlimage_1-373](assets/chlimage_1-373.png)

1. 单击&#x200B;**[!UICONTROL 保存]**&#x200B;和&#x200B;**[!UICONTROL 关闭]**&#x200B;以完成资产处理并分别返回至&#x200B;**[!UICONTROL 卡视图]**。
1. 处理完成后，您会在&#x200B;**[!UICONTROL 卡视图]**&#x200B;中看到以下内容：

   ![chlimage_1-374](assets/chlimage_1-374.png)

1. 在test3d页上，单击`logo-sphere.fbx`卡以在&#x200B;**[!UICONTROL 详细视图]**&#x200B;中打开模型。

   在logo-sphere.fbx页面的右上角附近，单击“舞台聚光灯”图标以展开下拉菜单，然后选择`stage-spotlights.fbx`。

   ![chlimage_1-376](assets/chlimage_1-375.png)

1. 从&#x200B;**[!UICONTROL 舞台聚光灯]**&#x200B;下拉列表中，选择`stage-helipad.fbx`。

   使用鼠标左键调整视图。 背景和模型光照会更改以反映新舞台选择。

   ![chlimage_1-376](assets/chlimage_1-376.png)

## 配置对Adobe Dimension资产{#configuring-support-for-adobe-dimension-assets}的支持

>[!NOTE]
>
>此配置任务是可选的。

您可以选择在AEM 3D中为Adobe Dimension资产配置支持。

您必须配置外部转换服务，以便在AEM中获取、预览和发布Adobe Dimension 3D资产。 服务将从专有的Adobe Dimension(`.dn`)格式转换为glTF（格式为`.glb`文件）的变体，该变体与Dn资产一起保存为再现。 `.glb`再现用于在AEM Assets、站点和屏幕中基于Web查看3D资产，也可供下载以用于第三方应用程序。

>[!NOTE]
>
>转换服务由Adobe在Amazon AWS中托管。 在正确配置服务后，上传到AEM的`.dn`文件随后会通过Amazon S3中的临时存储安全地复制到转换服务。 转换结果通过临时S3存储传回到AEM。 所有转让和存储均有担保。 此外，内容仅在S3中持续存在，而且转换服务仅短暂（通常不超过几分钟）。

**要为Adobe Dimension资产配置支持**:

1. 请与您的AdobeAEM客户经理、供应专家或支持代表联系，请求&#x200B;**AEM3D服务**&#x200B;的凭据。

   >[!NOTE]
   >
   >每个组织只需要一组凭据，而不管安装了凭据的AEM实例的数量如何。

1. 确认您收到以下信息：

   * accountId
   * customerId
   * 密码
   * identityPoolId
   * userPoolId
   * clientId

1. 作为管理员，登录到要安装凭据的AEM作者实例，然后打开&#x200B;**[!UICONTROL CRXDE Lite]**。
1. 通过在CRXDE Lite中执行以下操作，配置新凭据信息：

   1. 导航到`/libs/settings/dam/v3D/services/dncr`并将`clientId`属性设置为新值。
   1. 导航到`/libs/settings/dam/v3D/services/aws`并将`accountId`、`customerId`、`identityPoolId`和`userPoolId`属性设置为新值。
   1. 将新密码值加载到`encryptedPassword`属性中。 点按&#x200B;**[!UICONTROL 全部保存]**&#x200B;时，将自动加密此值。
   1. 点按&#x200B;**[!UICONTROL 全部保存]**，重新加载页面，然后验证`encryptedPassword`属性是否显示由花括号括起来的其他字符串。 此外观表示密码已正确加密且安全。

1. 通过在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中执行以下操作，指定`.glb`转换演绎版的格式：

   1. 导航到&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中的`/libs/settings/dam/v3D/services/dncr`。
   1. 将`outputFormat`属性设置为`Dn`或`generic`。

      设置为`Dn`时， `.glb`转换包括特定于Adobe的扩展，如IBL光照，以在AEM中查看Dn资源时获得最佳品质。 但是，转换的.glb再现在第三方应用程序中可能无法正常呈现。

      设置为`generic`时，`.glb`再现是通用的，没有Adobe特定的扩展。 此设置允许在第三方应用程序中使用它，而使用AEM 3D查看器进行查看在视觉上将不理想。

1. 通过在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中执行以下操作，启用Dn文件格式：

   1. 导航至 `/libs/settings/dam/v3D/assetTypes/Dn`.
   1. 将`Enabled`属性设置为true。

1. 通过执行以下操作验证配置：

   1. 打开AEM Assets。
   1. 将`logo_sphere.dn`上载到`test3d`文件夹。 文件位于`sample-3D-content/models`中。

      请注意，之前已下载`sample-3D-content.zip`以验证基本3D功能。
   1. 返回至&#x200B;**[!UICONTROL 卡片视图]**&#x200B;并观察已上传资产上显示的消息横幅。 **[!UICONTROL 转换格式……]**&#x200B;横幅在转换过程中显示。
   1. 完成所有处理后，请在&#x200B;**[!UICONTROL 详细信息视图]**&#x200B;中打开资产，以验证已转换的资产是否正确显示以及查看器的导航控件是否可用。

   ![image2018-11-2_15-51-19](assets/image2018-11-2_15-51-19.png)

   如果在10-15分钟后卡片视图&#x200B;]**的Dn资产上显示“处理错误”，则转换失败。**[!UICONTROL 

   如果出现这种情况，您可以通过执行以下操作来排除转换故障：

   * 删除资产，然后再次上传它。
   * 确保已在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;中正确设置所有配置参数。
   * 验证是否没有防火墙阻止访问转换服务和AWS端点。
