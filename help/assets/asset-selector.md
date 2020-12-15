---
title: 资产选择器
description: 了解如何使用资产选择器在Adobe Experience Manager(AEM)资产内搜索、筛选、浏览和提取资产的元数据。 还了解如何自定义资产选择器界面。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 1de8efce9cd5cf47163cba8f0c962a9e2fc5116c
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 1%

---


# 资产选择器{#asset-selector}

>[!NOTE]
>
>在AEM的先前版本中，资产选择器称为[资产选取器](https://helpx.adobe.com/experience-manager/6-2/assets/using/asset-picker.html)。

通过资产选择器，您可以浏览、搜索和筛选[!DNL Adobe Experience Manager]资产中的资产。 您还可以使用资产选择器提取您选择的资产的元数据。 要自定义资产选择器界面，您可以使用支持的请求参数启动该界面。 这些参数为特定方案设置资产选择器的上下文。

当前，您可以传递请求参数`assettype`(*Image/Video/Text*)和选择`mode`(*Single/Multiple*)作为资产选择器的上下文信息，在整个选择过程中该信息将保持不变。

资产选择器使用HTML5 **Window.postMessage**&#x200B;消息将选定资产的数据发送到收件人。

资产选择器基于Granite的基础选取器词汇。 默认情况下，资产选择器在浏览模式下操作。 但是，您可以使用Omnisearch体验应用过滤器来优化对特定资产的搜索。

您可以将任何网页(不管它是否是CQ容器的一部分)与资产选择器(`https://[AEM_server]:[port]/aem/assetpicker.html`)集成。

## 上下文参数{#contextual-parameters}

您可以在URL中传递以下请求参数，以在特定上下文中启动资产选择器：

| 名称 | 值 | 示例 | 用途 |
|---|---|---|---|
| 资源后缀(B) | 作为URL中资源后缀的文件夹路径：`http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | 要启动资产选择器并选择特定文件夹（例如，选择了文件夹`/content/dam/we-retail/en/activities`）,URL应采用以下形式：`http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | 如果在启动资产选择器时需要选择特定文件夹，请将其作为资源后缀进行传递。 |
| 模式 | 单个，多个 | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | 在多个模式下，您可以使用资产选择器同时选择多个资产。 |
| 对话框 | true、false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | 使用这些参数以Granite对话框的形式打开资产选择器。 仅当您通过Granite路径字段启动资产选择器并将其配置为pickerSrc URL时，此选项才适用。 |
| 根 | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | 使用此选项可指定资产选择器的根文件夹。 在这种情况下，资产选择器允许您仅选择根文件夹下的子资产（直接／间接）。 |
| viewmode | 搜索 |  | 要在搜索模式下启动资产选择器，请使用资产类型和mimetype参数。 |
| 资源类型(S) | 图像，文档，多媒体，存档 | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives`</li> | 使用此选项可根据传递的值筛选资产类型。 |
| mimetype | 资产的mimetype(s)(`/jcr:content/metadata/dc:format`)（还支持通配符） | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker?viewmode=search&mimetype=*presentation&mimetype=*png`</li></ul> | 使用它根据MIME类型筛选资产 |

## 使用资产选择器{#using-the-asset-selector}

1. 要访问资产选择器接口，请转至`https://[AEM_server]:[port]/aem/assetpicker`。
1. 导航到所需的文件夹，然后选择一个或多个资产。

   ![chlimage_1-441](assets/chlimage_1-441.png)

   或者，您也可以从OmniSearch框中搜索所需的资产，然后选择它。

   ![chlimage_1-442](assets/chlimage_1-442.png)

   如果使用OmniSearch框搜索资产，则可以从&#x200B;**[!UICONTROL 过滤器]**&#x200B;窗格中选择各种过滤器，以细化搜索。

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. 点按／单击工具栏中的&#x200B;**[!UICONTROL 选择]**。
