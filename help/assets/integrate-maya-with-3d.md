---
title: 将AEM 3D与Autodesk Maya集成
seo-title: 将AEM 3D与Autodesk Maya集成
description: 您可以选择将AEM 3D与Autodesk® Maya®软件集成，以支持本机Maya文件（.MA和。MB），并允许您使用任何可用的Maya渲染器在AEM中渲染3D资源。
seo-description: 您可以选择将AEM 3D与Autodesk® Maya®软件集成，以支持本机Maya文件（.MA和。MB），并允许您使用任何可用的Maya渲染器在AEM中渲染3D资源。
uuid: 07ff17b6-bdfc-4617-8b16-42aaf5c73fc7
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 3d063268-17d7-4db6-8028-682537645377
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 0%

---


# 将AEM 3D与Autodesk Maya{#integrating-aem-d-with-autodesk-maya}集成

>[!NOTE]
>
>此任务是可选的，仅适用于Windows。

您可以选择将AEM 3D与Autodesk® Maya®软件集成，以支持本机Maya文件（`.MA`和`.MB`），并可以在AEM中使用任何可用的Maya渲染器渲染3D资源。

*此集成仅适用于Windows*。

与Autodesk Maya集成时，必须安装和配置Autodesk Maya，添加Maya可执行文件夹的路径，启用Maya以进行摄取和渲染，以及测试集成。

请参阅[高级配置设置](advanced-config-3d.md)。

另请参阅[将AEM 3D与AutoDesk 3ds Max](integrating-aem-3d-with-autodesk-3ds-max.md)集成。

**要将AEM 3D与Autodesk Maya集成**:

1. 在托管AEM的同一服务器上安装Autodesk Maya 2016软件。

   安装后，请验证您是否可以打开和使用Maya，并且不存在许可问题。

   >[!NOTE]
   >
   >AEM仅使用Maya命令行渲染工具(`render.exe`)。 一个Maya网络许可证最多允许五台服务器同时处理或渲染Maya内容。

1. 在Maya中，启用Autodesk FBX®插件。
1. 安装MentalRay渲染插件或其他所需的渲染器。

   安装后，验证MentalRay是否在Maya中可用。

1. 将Maya可执行文件文件夹的路径添加到Windows PATH环境变量。

   例如，在Windows Server 2012上，点按&#x200B;**[!UICONTROL 开始] > [!UICONTROL 控制面板] > [!UICONTROL 系统和安全] > [!UICONTROL 系统] > [!UICONTROL 高级系统设置] [!UICONTROL 环境变量]**。 将`Maya2016\bin`文件夹的完整路径追加到`Path`系统变量。

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. 要启用Maya以进行摄取和渲染，请打开&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;并导航到`/libs/settings/dam/v3D/assetTypes/maya`，将&#x200B;**[!UICONTROL Enabled]**&#x200B;属性设置为`true`。

   ![image2018-6-22_12-42-7](assets/image2018-6-22_12-42-7.png)

1. 要启用JT(Siemens PLM Open CAD)文件格式，请导航到`/libs/settings/dam/v3D/assetTypes/jt`并将&#x200B;**[!UICONTROL Enabled]**&#x200B;属性设置为`true`。
1. 在AEM中，启用Maya作为渲染器。 首先，导航到&#x200B;**[!UICONTROL 工具>常规>CRXDE Lite]**。
1. 在左面板的&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;页面中，导航到以下内容：

   `/libs/settings/dam/v3D/renderers/maya`

   ![image2018-6-22_12-46-18](assets/image2018-6-22_12-46-18.png)

1. 将&#x200B;**[!UICONTROL Enabled]**&#x200B;属性设置为`true`。

1. 在&#x200B;**[!UICONTROL CRXDE Lite]**&#x200B;页面的左上角附近，点按&#x200B;**[!UICONTROL 全部保存]**。

   Maya现在启用为渲染器。

## 测试AEM 3D与Autodesk Maya {#testing-the-integration-of-aem-d-with-autodesk-maya}的集成

1. 打开AEM Assets，然后将位于`sample-3D-content/models`的`.MA`文件上传到`test3d`文件夹。

   请注意，之前已下载`sample-3D-content.zip`以验证基本3D功能。

1. 返回至&#x200B;**[!UICONTROL 卡片]**&#x200B;视图并观察已上传资产上显示的消息横幅。

   当Maya将本机`.MA`格式转换为`.FBX`时，将显示“转换格式”横幅。

1. 完成所有处理后，打开`logo-sphere.ma`资产并选择`stage-helipad.ma`阶段。

   预览体验与`logo_sphere.fbx`和`stage-helipad.fbx`相同。

1. 在页面的左上角附近，点按或单击下拉列表，然后选择&#x200B;**[!UICONTROL CRender]**。

   ![chlimage_1-54](assets/chlimage_1-54.png)

1. 在&#x200B;**[!UICONTROL 渲染器]**&#x200B;下拉列表中，选择&#x200B;**[!UICONTROL 自动桌面Maya]**，然后点按&#x200B;**[!UICONTROL 开始渲染器]**。
1. 在页面的右上角附近，点按或单击&#x200B;**[!UICONTROL 关闭]**&#x200B;以返回到&#x200B;**[!UICONTROL 卡]**&#x200B;视图。

   观察正在渲染的图像资产上的消息横幅（`logo-sphere`，除非指定了其他图像名称）。 横幅上的进度栏显示渲染进度。

   >[!NOTE]
   >
   >渲染占用大量CPU，可能需要几分钟时间才能完成

1. 渲染完成后，打开渲染后的图像资产。

   检查渲染后的图像是否与您单击&#x200B;**[!UICONTROL Render Now]**&#x200B;时所查看的图像合理匹配。

## 启用Maya {#enabling-additional-formats-supported-by-maya}支持的其他格式

（可选）Maya支持许多3D输入格式，任何3D输入格式均可启用，这样AEM都可以识别文件类型。 启用后，AEM会将文件发送给Maya，以将其转换为中间格式，而后者可直接由AEM摄取。

根据格式，功能支持可能受到限制（例如，材料可能不会通过），质量／保真度可能受到限制（例如，反面）。 Adobe只支持一般机制，但不支持任何特定格式转换。

请参阅[支持的数据导入格式 | Maya](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-69BC066D-D4D8-4B12-900C-CF42E798A5D6-htm.html)，了解有关Maya支持的格式的信息。

**要启用AEM支持的其他格式**:

1. 使用&#x200B;**[!UICONTROL CRXDE Lite]**，导航到`/libs/settings/dam/v3D/assetTypes`。
1. 复制&#x200B;**[!UICONTROL jt]**&#x200B;节点。 右键单击&#x200B;**[!UICONTROL jt]**&#x200B;节点并选择&#x200B;**[!UICONTROL 复制]**，然后右键单击&#x200B;**[!UICONTROL assetTypes]**&#x200B;文件夹，然后选择&#x200B;**[!UICONTROL 粘贴]**。 这应该生成新节点`/apps/cq-scene7-v3D/config/assetTypes/Copy of jt`。
1. 重命名新节点，为其赋予一个唯一名称，该名称表示要添加的文件类型。 可以使用文件后缀或任何其他唯一标识符。

1. 将新节点的&#x200B;**[!UICONTROL Enabled]**&#x200B;属性设置为`true`。

1. 将新注释的&#x200B;**[!UICONTROL Extension]**&#x200B;属性设置为要添加的格式的文件后缀／扩展名。
1. 将&#x200B;**[!UICONTROL MimeType]**&#x200B;属性设置为相应的值。 `application/x-` 后跟Extension属性的值 **** 应适用于大多数文件类型。
1. 确保将&#x200B;**[!UICONTROL Conversion]**&#x200B;属性设置为`fbx`和&#x200B;**[!UICONTROL IngestScrive]**&#x200B;设置为`Maya`。
1. 单击页面左上角附近的&#x200B;**[!UICONTROL 全部保存]**。

以下屏幕截图以COLLADA DAE为例说明了添加的文件格式：

![image2018-6-22_12-50-39](assets/image2018-6-22_12-50-39.png)

