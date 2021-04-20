---
title: 高级配置设置
seo-title: 高级配置设置
description: 了解适用于Maya和非Maya部署的AEM 3D集成的高级配置设置。
seo-description: 了解适用于Maya和非Maya部署的AEM 3D集成的高级配置设置。
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
exl-id: fdc82bca-e676-4052-b3e9-a198c685df96
feature: 3D Assets
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 1%

---

# 高级配置设置{#advanced-configuration-settings}

尽管默认配置设置适用于典型用例，但在某些情况下可能需要您进行更改。

以下高级配置设置适用于AEM 3D的Maya和非Maya部署的集成。

所有设置均使用AEM中的&#x200B;**CRXDE Lite**&#x200B;访问(**[!UICONTROL 工具>常规>CRXDE Lite]**)。

>[!NOTE]
>
>如果重新安装该包，它将所有设置重置为其默认值。

>[!CAUTION]
>
>编辑下表中未列出的任何设置可能会导致意外或不希望的项目行为。

## 资产类型配置{#asset-types-configuration}

在AEM的&#x200B;**CRXDE Lite**(**[!UICONTROL 工具>常规>CRXDE Lite]**)中，访问以下配置：

| 路径 | 描述 |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | 指定在摄取过程中创建的中间3D格式的文件类型。 对于“fbx”和“obj”文件格式，必须为空；对于由Maya启用的格式，必须为“fbx”。 |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | 设置为true或false可在&#x200B;**[!UICONTROL assetTypes]**&#x200B;列表中启用或禁用此条目。 |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | 指定一个或多个要与此资产类型关联的以逗号分隔的文件后缀或文件扩展名。 |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | 对于FBX和OBJ文件格式，必须为`native`；对于Maya启用的格式，必须为`maya`。 |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | 指定此资产类型的mime类型。 对于Maya启用的格式，建议使用`application/x-ext`，其中`ext`是指定为`Extension`值的字符串。 |

## 摄取配置{#ingestion-configuration}

在AEM的&#x200B;**CRXDE Lite**(**[!UICONTROL 工具>常规>CRXDE Lite]**)中，访问以下配置：

<table> 
 <tbody> 
  <tr> 
   <td><strong>路径</strong></td> 
   <td><strong>描述</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnIngest</td> 
   <td>支持在使用IBL舞台查看或渲染时生成环境遮挡投影。 适用于使用RapidRefine进行预览和渲染</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>设置为<strong>false</strong>可在转换和渲染后将临时文件保留在MayaWork文件夹中。 调试Maya转换和渲染问题时可能很有用。</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnIngest</td> 
   <td><p>启用后，服务器上会安装ImageMagick并配置magickPath。 Rapid Refine用于为3D对象创建简单的动画，这些对象在卡视图和其他视图中用作缩略图。</p> <p>创建动画会在摄取过程中消耗大量CPU资源。</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnIngest</td> 
   <td>支持在摄取时自动创建光映射。 设置为<strong>false</strong>可禁用自动创建光映射；这可以大幅降低CPU消耗，同时降低预览和渲染的质量。 不影响使用Maya进行渲染。</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>当设置为<strong>true</strong>（默认）时，如有必要，将对象垂直移动，以确保对象的所有部分都位于地平面之上(y=0)。</p> <p>当设置为<strong>false</strong>（默认）时，对象不会重新定位，可能会被舞台的地平面部分隐藏。 (仅适用于使用Rapid Refine进行预览和渲染。) 但是，它不会影响使用Maya进行渲染。 设置为<strong>true</strong>时，对象在Maya中的垂直位置可能与在预览中或在使用Rapid Refine进行渲染时不同。</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>ImageMagick转换实用程序的路径和名称。 如果启用了创建动画缩览图，则需要绝对路径。</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>指定最多用于3D资源的摄取处理的CPU数。</p> <p>值越高，摄取速度越快，但可能导致AEM总体响应不太灵敏。 此设置是近似的。 即，准确性随可用CPU核心数量而提高。</p> </td> 
  </tr> 
 </tbody> 
</table>

## Cloud Services配置设置{#cloud-services-configuration-settings}

以下设置的值由您的Adobe客户经理、供应专家或支持代表提供。

| **路径** | **描述** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | Adobe AWS帐户的帐户ID。 |
| `/libs/settings/dam/v3D/services/aws/bucketName` | S3传输桶的名称；通常为`aem3d`。 |
| `/libs/settings/dam/v3D/services/aws/customerId` | 由Adobe分配给您的组织的唯一ID。 用作AWS Cognito用户ID。 |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | 与此customerId关联的密码。 用作AWS Cognito密码。 |
| `/libs/settings/dam/v3D/services/aws/region` | 部署云服务的AWS区域。 |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | 适用的AWS Cognito用户池ID。 |
| `/libs/settings/dam/v3D/services/dncr/clientId` | dncr转换服务的AWS Cognito客户端ID。 |

## 常见处理设置{#common-processing-settings}

在AEM的&#x200B;**CRXDE Lite**(**[!UICONTROL 工具>常规>CRXDE Lite]**)中，访问以下配置：

| **路径** | **描述** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | Maya转换和渲染的工作文件夹的名称和位置。 如果文件夹不存在，则会自动创建该文件夹。 |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | 3ds Max转换的工作文件夹的名称和位置。 如果文件夹不存在，则会自动创建该文件夹。 |
| `/libs/settings/dam/v3D/settings/debugNative` | 设置为&#x200B;**[!UICONTROL true]**&#x200B;可在使用RapidRefine渲染器进行格式转换和渲染期间创建调试信息。 |

## 渲染器配置{#renderer-configuration}

在AEM的&#x200B;**CRXDE Lite**(**[!UICONTROL 工具>常规>CRXDE Lite]**)中，访问以下配置：

| **路径** | **描述** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | 当设置为&#x200B;**[!UICONTROL true]**&#x200B;且预生成的光映射不可用（即invokeLightMapsOnIngest=false）时，Rapid Refine渲染器会在渲染期间创建光映射以提高渲染质量。 该设置可以显着增加渲染时间。 设置为&#x200B;**[!UICONTROL false]**&#x200B;可在此情况下使CPU使用最小化，但可能导致较低的渲染质量。 |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | 分别设置为&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**&#x200B;以启用或禁用呈示器。 |
| `/libs/settings/dam/v3D/renderers/*/Display` | 允许您更改在“渲染”面板的“渲染器”选择器中为启用的渲染器显示的字符串。 |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | 指定渲染3D场景最多使用多少CPU。 值越高，渲染速度越快，但可能导致AEM总体响应性越差。 此设置是近似的。 即，准确性随可用CPU核心数量而提高。 |

## 3D资产预览设置{#d-asset-preview-settings}

在AEM的&#x200B;**CRXDE Lite**(**[!UICONTROL 工具>常规>CRXDE Lite]**)中，访问以下配置：

| 路径 | 描述 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | 设置为&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**&#x200B;可在页面加载时启用或禁用自动旋转（自动相机轨道）。 |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | 设置为&#x200B;**[!UICONTROL true]**&#x200B;可在按&#x200B;**[!UICONTROL 重置]**&#x200B;后重新启动自动旋转。 禁用自动旋转时忽略。 |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | 指定自动旋转的速度（每分钟旋转数）和方向，其中从右到左的值为负，从左到右的旋转为正。 |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | 设置为&#x200B;**[!UICONTROL false]**&#x200B;可禁用以渐进方式退出查看器对触摸和鼠标手势的响应来继续操作。 |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | 指定加载幕的颜色，在加载和初始化期间，可以选择覆盖3D资产预览的视区。 R，G，B值，每个颜色分量在0到255之间。 |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | 当设置为&#x200B;**[!UICONTROL true]**&#x200B;时，在查看器初始化的后半部分，负载幕将逐渐淡出。 当设置为&#x200B;**[!UICONTROL false]**&#x200B;时，帘子保持不透明，直到装载和初始化完成。 |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | 设置为&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**&#x200B;可启用或禁用3D资产预览的加载幕。 |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | 启用自动旋转并处于活动状态时，相机的垂直位置将自动调整为相对于3D对象的高度。 设置为0.5时，摄像机将垂直放置在对象高度的1/2处，这会导致水平线在视口中垂直居中。 值越大，相机将向下看到对象并提高渲染的水平线高度，值越小，相机将向上看到对象并降低水平线。 |

## 3D Sites组件设置{#d-sites-component-settings}

在AEM的&#x200B;**CRXDE Lite**(**[!UICONTROL 工具>常规>CRXDE Lite]**)中，访问以下配置：

| 路径 | 描述 |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | 设置为&#x200B;**[!UICONTROL true]**&#x200B;可在按住家后重新激活自动旋转（自动相机轨道）。 禁用自动旋转时忽略。 |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | 设置为&#x200B;**[!UICONTROL false]**&#x200B;可禁用以渐进方式退出查看器对触摸和鼠标手势的响应来继续操作。 |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | 指定加载过程中可以选择覆盖3D站点组件视区的载入窗帘的颜色。 R，G，B值，每个颜色分量在0到255之间。 |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | 当设置为&#x200B;**[!UICONTROL true]**&#x200B;时，在加载和初始化的后半部分，负载幕将逐渐淡出。 当设置为&#x200B;**[!UICONTROL false]**&#x200B;时，帘子保持不透明，直到装载和初始化完成。 |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | 设置为&#x200B;**[!UICONTROL true]**&#x200B;或&#x200B;**[!UICONTROL false]**&#x200B;可启用或禁用3D站点组件的负载帘。 |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | 启用自动旋转并处于活动状态时，相机的垂直位置将自动调整为相对于3D对象的高度。 设置为0.5时，摄像机将垂直放置在对象高度的1/2处，这会导致水平线在视口中垂直居中。 值越大，相机将向下看到对象并提高渲染的水平线高度，值越小，相机将向上看到对象并降低水平线。 |
