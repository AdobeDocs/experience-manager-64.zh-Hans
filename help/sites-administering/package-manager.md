---
title: 如何使用包
seo-title: How to Work With Packages
description: 了解在AEM中处理包的基础知识。
seo-description: Learn the basics of working with packages in AEM.
uuid: e9eb4f88-9df6-4019-92e0-2aafcffe1aab
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 8e568c59-5455-422f-94a6-baf6d2aae070
exl-id: eebc10fa-1d49-4797-a9e6-b6615bfe0173
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4057'
ht-degree: 1%

---

# 如何使用包{#how-to-work-with-packages}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

包允许导入和导出存储库内容。 例如，您可以使用包来安装新功能、在实例之间传输内容以及备份存储库内容。

可以从以下页面访问和/或维护资源包：

* [包管理器](#package-manager)，用于管理本地AEM实例中的包。

* [包共享](#package-share)，一个中央服务器，其中既包含公开可用的包，也包含对贵公司私有的包。 公共资源包可以包含修补程序、新功能、文档等。

可以在包管理器、包共享和文件系统之间传输包。

## 什么是包？ {#what-are-packages}

资源包是一个zip文件，其中包含以文件系统序列化（称为“保管库”序列化）形式存储库内容。 这为文件和文件夹提供了易于使用和编辑的表示形式。

包中包含使用过滤器选择的页面内容和项目相关内容。

资源包还包含保管库元信息，包括过滤器定义和导入配置信息。 包中可以包含其他内容属性（不用于包提取），例如描述、可视图像或图标；这些属性仅用于内容包使用者和信息目的。

>[!NOTE]
>
>包表示生成包时内容的当前版本。 它们不包括AEM保留在存储库中的内容的任何以前版本。

您可以对包或对包执行以下操作：

* 创建新资源包；根据需要定义包设置和过滤器
* 预览包内容（在生成之前）
* 生成包
* 查看包信息
* 查看包内容（构建后）
* 修改现有包的定义
* 重建现有资源包
* 重新包装包
* 将包从AEM下载到文件系统
* 将包从文件系统上传到本地AEM实例
* 安装前验证包内容
* 执行干式运行安装
* 安装包(AEM在上传后不会自动安装包)
* 删除资源包
* 从包共享库中下载包，如修补程序
* 将包上传到包共享库的公司内部部分

## 包信息 {#package-information}

包定义由各种类型的信息组成：

* [包设置](#package-settings)
* [包过滤器](#package-filters)
* [包屏幕截图](#package-screenshots)
* [包图标](#package-icons)

### 包设置 {#package-settings}

您可以编辑各种包设置来定义一些方面，如包描述、相关错误、依赖项和提供程序信息。

的 **包设置** 对话框可通过 **编辑** 按钮 [创建](#creating-a-new-package) 或 [编辑](#viewing-and-editing-package-information) 包中提供了三个用于配置的选项卡。 进行任何更改后，单击 **确定** 来保存这些。

![包编辑](assets/packagesedit.png)

| **字段** | **描述** |
|---|---|
| 名称 | 包的名称。 |
| 组 | 要将包添加到的组的名称，用于组织包。 键入新组的名称，或选择现有组。 |
| 版本 | 用于自定义版本的文本。 |
| 描述 | 包的简要描述。 HTML标记可用于进行格式设置。 |
| 缩略图 | 包列表中显示的图标。 单击浏览以选择本地文件。 |

![chlimage_1-344](assets/chlimage_1-344.png)

<table> 
 <tbody> 
  <tr> 
   <th><strong>字段</strong></th> 
   <th><strong>描述</strong></th> 
   <th><strong>格式/示例</strong></th> 
  </tr> 
  <tr> 
   <td>名称</td> 
   <td>提供商的名称。</td> 
   <td><em>AEMGeometrixx<br /> </em></td> 
  </tr> 
  <tr> 
   <td>URL</td> 
   <td>提供商的URL。</td> 
   <td><em>https://www.aem-geometrixx.com</em></td> 
  </tr> 
  <tr> 
   <td>链接</td> 
   <td>指向提供程序页面的特定于包的链接。</td> 
   <td><em>https://www.aem-geometrixx.com/mypackage.html</em></td> 
  </tr> 
  <tr> 
   <td>需要<br /> </td> 
   <td> 
    <ul> 
     <li>管理员：选择包何时只能由具有管理员权限的帐户安装。</li> 
     <li>重新启动：选择在安装包后需要重新启动服务器的时间。</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td>AC 处理</td> 
   <td><p>指定在导入资源包时如何处理资源包中定义的访问控制信息：</p> 
    <ul> 
     <li><strong>忽略</strong></li> 
     <li><strong>覆盖</strong></li> 
     <li><strong>合并</strong></li> 
     <li><strong>清除</strong></li> 
     <li><strong>MergePreserve</strong></li> 
    </ul> <p>默认值为 <strong>忽略</strong>.</p> </td> 
   <td> 
    <ul> 
     <li><strong>忽略</strong>  — 在存储库中保留ACL</li> 
     <li><strong>覆盖</strong>  — 覆盖存储库中的ACL</li> 
     <li><strong>合并</strong>  — 合并两组ACL</li> 
     <li><strong>清除</strong>  — 清除ACL</li> 
     <li><strong>MergePreserve</strong>  — 通过添加内容中不存在的主体的访问控制条目，将内容中的访问控制与包中提供的访问控制合并</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

![包依赖关系](assets/packagesdependencies.png)

| **字段** | **描述** | **格式/示例** |
|---|---|---|
| 已通过 | 此产品包的目标产品名称和版本或与之兼容。 | *AEM6* |
| 修复了错误/问题 | 允许您列出使用此包修复的错误详细信息的文本字段。 请在单独的行上列出每个错误。 | bug-nr摘要 |
| 依赖于 | 列出在需要其他包才能按预期运行当前包时需要遵守的依赖关系信息。 使用修补程序时，此字段很重要。 | groupId:name:版本 |
| 替换 | 此包替换的已弃用包列表。 在安装之前，请检查此包是否包含过时包中的所有必需内容，以便不会覆盖任何内容。 | groupId:name:版本 |

### 包过滤器 {#package-filters}

过滤器标识要包含在包中的存储库节点。 A **过滤器定义** 指定以下信息：

* 的 **根路径** 要包含的内容。
* **规则** 包含或排除根路径下的特定节点。

过滤器可以包含零个或多个规则。 未定义规则时，资源包包含根路径下的所有内容。

您可以为包定义一个或多个过滤器定义。 使用多个过滤器包含多个根路径中的内容。

![chlimage_1-345](assets/chlimage_1-345.png)

下表介绍了这些规则并提供了示例：

<table> 
 <tbody> 
  <tr> 
   <th> 规则类型</th> 
   <th>描述 </th> 
   <th>示例 </th> 
  </tr> 
  <tr> 
   <td> include</td> 
   <td>您可以定义路径，或使用正则表达式指定要包含的所有节点。<br /> <br /> 包含目录将： 
    <ul> 
     <li>包括目录 <i>和</i> 该目录中的所有文件和文件夹（即整个子树）</li> 
     <li><strong>not</strong> 从指定的根路径下包含其他文件或文件夹</li> 
    </ul> </td> 
   <td>/libs/sling/install(/)*)? </td> 
  </tr> 
  <tr> 
   <td> 排除</td> 
   <td>您可以指定路径或使用正则表达式指定要排除的所有节点。<br /> <br /> 排除目录将排除该目录 <i>和</i> 该目录中的所有文件和文件夹（即整个子树）。<br /> </td> 
   <td>/libs/wcm/foundation/components(/)*)?</td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>一个包可以包含多个过滤器定义，因此来自不同位置的节点可以容易地合并到一个包中。

首次定义包过滤器时，通常会定义包过滤器 [创建资源包](#creating-a-new-package)，但也可以在稍后进行编辑（应在此之后重新构建包）。

### 包屏幕截图 {#package-screenshots}

您可以将屏幕截图附加到包中，以直观地呈现内容的外观；例如，通过提供新功能的屏幕截图。

### 包图标 {#package-icons}

您还可以向包附加一个图标，以提供包所含内容的快速参考可视表示形式。 然后，该代码包会显示在资源包列表中，并有助于您轻松识别资源包或资源包类。

由于包可以包含图标，因此以下约定将用于正式包：

>[!NOTE]
>
>为避免造成混淆，请为包使用描述性图标，而不要使用任何官方图标。

正式修补程序包：

![](do-not-localize/chlimage_1-28.png)

正式的AEM安装或扩展包：

官方功能包：

![](do-not-localize/chlimage_1-29.png)

## 包管理器 {#package-manager}

包管理器管理本地AEM安装上的包。 在 [分配了必要的权限](#permissions-needed-for-using-the-package-manager) 您可以将包管理器用于各种操作，包括配置、构建、下载和安装包。 要配置的关键元素包括：

* [包设置](#package-settings)
* [包过滤器](#package-filters)

### 使用包管理器所需的权限 {#permissions-needed-for-using-the-package-manager}

要授予用户创建、修改、上传和安装包的权限，您必须在以下位置为用户授予相应的权限：

* **/etc/packages** （删除除外）完全权限
* 包含包内容的节点

请参阅 [设置权限](/help/sites-administering/security.md) 以了解有关更改权限的说明。

### 创建新资源包 {#creating-a-new-package}

要创建新的包定义，请执行以下操作：

1. 在AEM欢迎屏幕上，单击 **包** (或 **工具** 控制台双击 **包**)。

1. 然后选择 **包管理器**.
1. 单击 **创建资源包**.

   >[!NOTE]
   >
   >如果您的实例具有许多包，则可能存在一个文件夹结构，因此您可以在创建新包之前导航到所需的目标文件夹。

1. 在对话框中：

   ![packagenew](assets/packagesnew.png)

   输入：

   * **组名称**

      目标组（或文件夹）名称。 组将用于帮助您组织包。

      如果组不存在，则将为其创建文件夹。 如果将组名称留空，它将在主包列表（主页>包）中创建包。

   * **包名称**

      新包的名称。 选择一个描述性名称，以帮助您（和其他人）轻松识别包的内容。

   * **版本号**

      用于指示版本的文本字段。 此名称将附加到包名称中，以构成zip文件的名称。
   单击 **确定** 创建资源包。

1. AEM会在相应的组文件夹中列出新包。

   ![packagesitem](assets/packagesitem.png)

   单击要打开的图标或包名称。

   ![packagesitemclicked](assets/packagesitemclicked.png)

   >[!NOTE]
   >
   >您可以在以后的阶段（如果需要）返回此页面。

1. 单击 **编辑** 编辑 [包设置](#package-settings).

   在此，您可以添加信息和/或定义某些设置；例如，这包括描述、 [图标](#package-icons)、相关错误和添加提供程序详细信息。

   单击 **确定** 编辑完设置后。

1. 添加 **[屏幕截图](#package-screenshots)** 包中。 创建包后，有一个实例可用，如果需要，可使用 **包屏幕截图** 从sidekick。

   双击 **屏幕截图** ，然后单击 **确定**.

1. 定义 **[包过滤器](#package-filters)** 通过拖动实例 **过滤器定义** 在sidekick中，双击以打开进行编辑：

   ![packagesfilter](assets/packagesfilter.png)

   指定：

   * **根路径**
要打包的内容；这可以是子树的根。
   * **规则**
规则是可选的；对于简单的包定义，无需指定包含或排除规则。

      如果需要，您可以定义 [**包括** 或 **排除** 规则](#package-filters) 以准确定义包内容。

      使用 **+** 符号，或者使用删除规则 **-** 符号。 规则将根据其顺序应用，以便使用 **向上** 和 **向下** 按钮。
   然后，单击 **确定** 来保存过滤器。

   >[!NOTE]
   >
   >您可以根据需要使用任意数量的过滤器定义，但必须谨慎确保它们不会发生冲突。 使用 **预览** 确认包内容。

1. 要确认包将包含的内容，您可以使用 **预览**. 此操作将执行构建过程的练习，并列出在实际构建包时将添加到包中的所有内容。
1. 您现在可以 [生成](#building-a-package) 包。

   >[!NOTE]
   >
   >此时不强制构建包，可以在稍后的时间点完成。

### 构建资源包 {#building-a-package}

资源包通常是在您同时构建的 [创建包定义](#creating-a-new-package)，但您可以稍后返回以构建或重建包。 如果存储库中的内容发生更改，则此功能会非常有用。

>[!NOTE]
>
>在生成包之前，预览包的内容会非常有用。 要执行此操作，请单击 **预览**.

1. 从中打开包定义 **包管理器** （单击包图标或名称）。

1. 单击 **生成**. 此时会出现一个对话框，要求您确认是否确实要构建包。

   >[!NOTE]
   >
   >当您重建资源包时，这特别重要，因为资源包内容将被覆盖。

1. 单击&#x200B;**确定**。AEM将生成包，并列出添加到包中的所有内容。 完成AEM时，会显示一条确认消息，确认已生成资源包，并且（关闭对话框时）会更新资源包列表信息。

### 重新包装包 {#rewrapping-a-package}

构建包后，可以根据需要重新包装该包。

重新包装更改了包信息 —  *无* 更改包内容。 资源包信息是缩略图、描述等，换言之，您可以通过 **包设置** 对话框(打开此单击 **编辑**)。

重新包装的主要用例是在为包共享准备包时。 例如，您可能已拥有一个现有资源包，并决定与他人共享该资源包。 添加缩略图并添加描述。 您无需使用其所有功能重新创建整个资源包（可能需要一些时间，并且可能会面临资源包不再与原始资源包相同的风险），而是可以重新包装资源包，并只添加缩略图和描述。

1. 从中打开包定义 **包管理器** （单击包图标或名称）。

1. 单击 **编辑** 并更新 **[包设置](#package-settings)** 。 单击 **确定** 保存。

1. 单击 **重新换行**，则会出现一个对话框要求进行确认。

### 查看和编辑包信息 {#viewing-and-editing-package-information}

要查看或编辑有关资源包定义的信息，请执行以下操作：

1. 在包管理器中，导航到要查看的包。
1. 单击要查看的包的包图标。 此时将打开包页面，其中列出了有关包定义的信息：

   ![packagesitemclicked-1](assets/packagesitemclicked-1.png)

   >[!NOTE]
   >
   >您还可以通过此页面对资源包进行编辑和执行某些操作。
   >
   >可用的按钮取决于包是否已构建。

1. 如果包已生成，请单击 **内容**，将打开一个窗口，并列出包的整个内容：

### 查看包内容和测试安装 {#viewing-package-contents-and-testing-installation}

生成包后，您可以查看内容：

1. 在包管理器中，导航到要查看的包。
1. 单击要查看的包的包图标。 这将打开包页面，其中列出了有关包定义的信息。

1. 要查看内容，请单击 **内容**，将打开一个窗口，并列出包的整个内容：

   ![包内容](assets/packgescontents.png)

1. 要执行安装的干式运行，请单击 **测试安装**. 确认操作后，将打开一个窗口，并列出与执行安装一样的结果：

   ![packagestestinstall](assets/packagestestinstall.png)

### 将包下载到文件系统 {#downloading-packages-to-your-file-system}

本节介绍如何使用 **包管理器**.

>[!NOTE]
>
>请参阅 [包共享](#package-share) 有关从公共区域和您公司内部的包共享区域下载修补程序、功能包和包的信息。
>
>从包共享中，您可以：
>
>* 从下载包 [将共享包直接发送到您的本地AEM实例](#downloading-and-installing-packages-from-package-share).\
   >  下载包后，该包会导入到您的存储库中，之后，您可以使用 **包管理器**. 这些包包括修补程序和其他共享包。
>
>* 从下载包 [将共享包到文件系统](#downloading-packages-to-your-file-system-from-package-share).
>


1. 在AEM欢迎屏幕上，单击 **包**，然后选择 **包管理器**.
1. 导航到要下载的包。

   ![packagedownload](assets/packagesdownload.png)

1. 单击要下载的包的zip文件名称（带下划线）所形成的链接；例如 `export-for-offline.zip`.

   AEM会将包下载到您的计算机（使用标准的浏览器下载对话框）。

### 从文件系统上传包 {#uploading-packages-from-your-file-system}

包上传允许您将包从文件系统上传到AEM包管理器。

>[!NOTE]
>
>请参阅 [将包上传到公司内部包共享](#uploading-a-package) 将包上传到您公司的包共享专用区域。

要上传资源包，请执行以下操作：

1. 导航到 **包管理器**. 然后，转到要将包上传到的组文件夹。

   ![packagesuploadbutton](assets/packagesuploadbutton.png)

1. 单击 **上传包**.

   ![packagesuploadalog](assets/packagesuploaddialog.png)

   * **文件**

      您可以直接键入文件名，也可以使用 **浏览……** 对话框，从本地文件系统中选择所需的包(选择后，单击 **确定**)。

   * **强制上传**

      如果具有此名称的包已存在，则可以单击此名称以强制上传（并覆盖现有包）。
   单击 **确定** 以便新包上载并列在包管理器列表中。

   >[!NOTE]
   >
   >要使内容可供AEM使用，请务必 [安装包](#installing-packages).

### 验证包 {#validating-packages}

在安装包之前，您可能希望验证其内容。 由于资源包可以在 `/apps` 和/或添加、修改和删除ACL时，在安装前验证这些更改通常非常有用。

#### 验证选项 {#validation-options}

验证机制可以检查包的以下特征：

* OSGi包导入
* 叠加
* ACL

下面详细介绍了这些选项。

* **验证 OSGi 包的导入情况**

   **已检查的内容**

   此验证会检查所有JAR文件（OSGi包）的包，提取其 `manifest.xml` （其中包含所述OSGi包所依赖的版本化依赖项），并验证AEM实例使用正确的版本导出所述依赖项。

   **报告方式**

   AEM实例无法满足的任何版本化依赖项都列在 **活动日志** 包管理器的子目录。

   **错误状态**

   如果不满足依赖关系，则包中具有这些依赖关系的OSGi包将不会启动。 这会导致应用程序部署中断，因为任何依赖未启动的OSGi包的部署都将无法正常工作。

   **错误解决**

   要解决由于未满足要求的OSGi包而导致的错误，需要调整包中具有未满足的导入的依赖项版本。

* **验证覆盖**

   **已检查的内容**

   此验证可确定所安装的包是否包含目标AEM实例中已叠加的文件。

   例如，假定在 `/apps/sling/servlet/errorhandler/404.jsp`，包含的包 `/libs/sling/servlet/errorhandler/404.jsp`，以便更改现有文件(位于 `/libs/sling/servlet/errorhandler/404.jsp`.

   **报告方式**

   任何此类叠加均在 **活动日志** 包管理器的子目录。

   **错误状态**

   错误状态表示资源包尝试部署的文件已经覆盖，因此资源包中的更改将被覆盖（并因此被“隐藏”），且不会生效。

   **错误解决**

   要解决此问题，请在 `/apps` 必须在 `/libs` 并根据需要将更改纳入叠加( `/apps`)，并重新部署覆盖的文件。

   >[!NOTE]
   >
   >请注意，如果叠加的内容已正确纳入叠加文件中，则验证机制无法进行协调。 因此，即使进行了必要的更改，此验证仍将继续报告冲突。

* **验证 ACL**

   **已检查的内容**

   此验证会检查添加的权限、处理权限的方式（合并/替换），以及当前权限是否会受到影响。

   **报告方式**

   有关权限的介绍，请参见 **活动日志** 包管理器的子目录。

   **错误状态**

   无法提供显式错误。 验证仅指示是否将通过安装包来添加或影响任何新ACL权限。

   **错误解决**

   使用验证提供的信息，可以在CRXDE中查看受影响的节点，并且可以根据需要在包中调整ACL。

   >[!CAUTION]
   >
   >作为最佳实践，建议软件包不要影响AEM提供的ACL，因为这可能会导致意外的产品行为。

#### 执行验证 {#performing-validation}

可以采用两种不同的方式来验证包：

* 通过包管理器UI
* 通过HTTPPOST请求（例如使用cURL）

>[!NOTE]
>
>上传包后但安装包之前，应始终进行验证。

**通过包管理器进行包验证**

1. 在以下位置打开包管理器 `https://<server>:<port>/crx/packmgr`
1. 在列表中选择包，然后选择 **更多** 从标题中下拉，然后 **验证** 下拉菜单中。

   >[!NOTE]
   >
   >这应在上传内容包之后、安装包之前完成。

1. 在随后显示的模式对话框中，使用复选框选择验证类型，然后通过单击开始验证 **验证**. 或者，单击 **取消**.

1. 随后将运行所选验证。 结果显示在包管理器的活动日志中。

**通过HTTPPOST请求进行包验证**

POST请求采用以下形式。

```
https://<host>:<port>/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls
```

>[!NOTE]
>
>的 `type` 参数可以是以逗号分隔的无序列表，其中包含：
>
>* `osgiPackageImports`
>* `overlays`
>* `acls`
>
>的值 `type` 默认为 `osgiPackageImports` 如果未传递。

以下是使用cURL执行包验证的示例。

1. 如果使用cURL，则执行类似于以下语句：

   ```shell
   curl -v -X POST --user admin:admin -F file=@/Users/SomeGuy/Desktop/core.wcm.components.all-1.1.0.zip 'http://localhost:4502/crx/packmgr/service.jsp?cmd=validate&type=osgiPackageImports,overlays,acls'
   ```

1. 将运行所请求的验证，并将响应作为JSON对象发送回来。

>[!NOTE]
>
>对验证HTTPPOST请求的响应将是一个JSON对象，其验证结果为。

### 安装包 {#installing-packages}

上传包后，您需要安装内容。 要安装包内容并使其正常工作，它需要同时满足以下条件：

* 加载到AEM( [从文件系统上传](#uploading-packages-from-your-file-system) 或 [从包共享下载](#downloading-and-installing-packages-from-package-share))

* 已安装

>[!CAUTION]
>
>安装资源包可能会覆盖或删除现有内容。 仅当您确定包不会删除或覆盖您需要的内容时，才上传包。
>
>要查看包的内容或影响，您可以：
>
>* 在不修改任何内容的情况下，对包执行测试安装：\
   >  打开包（单击包图标或名称），然后单击 **测试安装**.
>
>* 请参阅包内容列表：\
   >  打开包并单击 **内容**.
>


>[!NOTE]
>
>在安装包之前，将立即创建一个快照包，以包含将被覆盖的内容。
>
>如果/当您卸载包时，将重新安装此快照。

>[!CAUTION]
>
>如果要安装数字资产，您必须：
>
>* 首先，停用WorkflowLauncher。\
   >  使用OSGi控制台的“组件”菜单选项停用 `com.day.cq.workflow.launcher.impl.WorkflowLauncherImpl`.
>
>* 接下来，安装完成后，重新激活WorkflowLauncher。
>
>取消激活WorkflowLauncher可确保资产导入器框架不会（无意中）在安装时处理资产。

1. 在包管理器中，导航到要安装的包。

   安 **安装** 按钮。

   >[!NOTE]
   >
   >或者，您也可以通过单击资源包的图标来打开资源包，以访问 **安装** 按钮。

1. 单击 **安装** 以开始安装。 对话框将请求确认并列出所做的所有更改。 完成后，单击 **关闭** 对话框。

   词 **已安装** 安装包后，该包旁会显示。

### 基于文件系统的上传和安装 {#file-system-based-upload-and-installation}

有另一种方法可以将包上载并安装到实例。 在文件系统中，您有 `crx-quicksart` 文件夹，以及jar和 `license.properties` 文件。 您需要创建一个名为 `install` 在 `crx-quickstart`. 然后，您将获得如下内容： `<aem_home>/crx-quickstart/install`

在此安装的文件夹中，您可以直接添加包。 系统将自动在您的实例上传和安装这些组件。 完成后，您可以在包管理器中看到包。

如果您的实例正在运行，请向 `install` 文件夹将直接启动上传和实例上的安装。 如果您的实例未运行，则放置在 `install` 文件夹将在启动时按字母顺序进行安装。

>[!NOTE]
>
>您还可以在首次启动实例之前执行此操作。 要实现此目的，您需要创建 `crx-quickstart` 手动创建文件夹， `install` 文件夹，然后将包放在那里。 然后，当您首次启动实例时，将按字母顺序安装包。

### 卸载包 {#uninstalling-packages}

AEM允许您卸载包。 此操作会还原受到在安装软件包之前立即生成的快照影响的存储库的内容。

>[!NOTE]
>
>安装后，将创建一个快照包，其中包含将被覆盖的内容。
>
>卸载该包后，将重新安装该包。

1. 在包管理器中，导航到要卸载的包。
1. 单击要卸载的包的包图标。
1. 单击 **卸载** 从存储库中删除此包的内容。 对话框将请求确认并列出所做的所有更改。 完成后，单击 **关闭** 对话框。

### 删除资源包 {#deleting-packages}

要从包管理器列表中删除包，请执行以下操作：

>[!NOTE]
>
>包中已安装的文件/节点为 **not** 已删除。

1. 在 **工具** 控制台中，展开 **包** 文件夹来显示包。

1. 单击要删除的包，以将其突出显示，然后执行以下任一操作：

   * 单击 **删除** 中。
   * 右键单击并选择 **删除**.

   ![包删除](assets/packagesdelete.png)

1. AEM会要求您确认是否要删除该包。 单击 **确定** 以确认删除。

>[!CAUTION]
>
>如果此包已安装，则 *已安装* 内容 **not** 删除。

### 复制包 {#replicating-packages}

复制包的内容以将其安装到发布实例：

1. 在 **包管理器**，导航到要复制的包。

1. 单击要复制的资源包的图标或名称以展开该资源包。
1. 在 **更多** 工具栏上的下拉菜单，选择 **复制**.

## 包共享 {#package-share}

Package Share是一个可公开共享内容包的中央服务器。

它已被 [软件分发。](#software-distribution)

## Software Distribution {#software-distribution}

[Software Distribution](https://downloads.experiencecloud.adobe.com) 是旨在简化AEM包搜索和下载的新用户界面。

有关更多信息，请查看 [Software Distribution文档。](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html)

>[!CAUTION]
>
>AEM包管理器当前不适用于Software Distribution。 将包下载到本地磁盘。
