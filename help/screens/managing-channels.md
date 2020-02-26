---
title: 创建和管理渠道
seo-title: 管理渠道
description: 可查看本页以了解有关创建和管理渠道的信息。本页还介绍了渠道功能板，以及如何编辑渠道的内容。
seo-description: 可查看本页以了解有关创建和管理渠道的信息。本页还介绍了渠道功能板，以及如何编辑渠道的内容。
uuid: 1f89ea18-63ef-4a42-9337-0f29d6aab938
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: edb7e73b-83e3-4e6d-85e0-f975c99931b0
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 创建和管理渠道{#creating-and-managing-channels}

渠道可显示一系列内容以及显示的图像和视频，但也可以显示网站或单页应用程序。

本页显示了如何为 Screens 创建和管理渠道。

**先决条件**：

* [配置和部署 Screens](configuring-screens-introduction.md)
* [创建和管理Screens项目](creating-a-screens-project.md)

## 创建新渠道 {#creating-a-new-channel}

创建 Screens 项目后，请按照以下步骤为 Screens 项目创建新渠道：

1. 选择 Adobe Experience Manager 链接（左上方），然后选择“屏幕”。或者，您也可以直接从 `http://localhost:4502/screens.html/content/screens`
1. Navigate to Screens project and click **Channels**.
1. Click **Create** next to the plus icon in the action bar. 此时会打开一个向导（请参阅“渠道类型”以了解更多信息&#x200B;**）。

1. Select the template from the wizard and click **Next**.
1. Enter the properties for **Title and Tags**, **More Titles and Description**, **On/Off Time**, and **Vanity URL**.

1. 单击&#x200B;**创建**，随即会创建渠道并将其添加到渠道文件夹中。

### 渠道类型 {#channel-types}

可以在向导中使用以下模板选项，例如：

| **模板选项** | **描述** |
|---|---|
| 渠道文件夹 | 允许创建一个文件夹来存储渠道的集合。 |
| 序列渠道 | 允许创建一个按顺序（在幻灯片中逐个播放）播放组件的渠道。 |
| 应用程序渠道 | 允许在 Screens 播放器中显示您的自定义 Web 应用程序。 |
| 1x1 分屏渠道 | 允许在单个区域中查看组件。 |
| 1x2 分屏渠道 | 允许在两个区域（水平拆分）中查看资产。 |
| 2x2 分屏渠道 | 允许在四个区域（在矩阵中水平和垂直拆分）中查看资产。 |
| 2x3 分屏渠道 | 允许查看两个区域（水平拆分）中的资产，其中一个区域大于另一个区域。 |

>[!NOTE]
>
>“分屏”通道将显示屏拆分为多个区域，这样您可以同时并排播放多个体验。 体验可以是静态资产／文本或嵌入式序列。

以下示例显示了如何为Screens项目DemoProject创 **建序列渠道** ChannelOne ****。

![player2-2](assets/player2-2.gif)

>[!NOTE]
>
>您可以使用模板选项（例如上面所述的 1x2 分屏渠道、2x2 分屏渠道或 2x3 分屏渠道）创建不同的区域。

***重要信息***：

在创建渠道并向渠道中添加内容后，下一步是创建位置，之后是创建显示屏。此外，您还需要将该渠道分配到显示屏。请参阅此部分末尾的资源以了解更多信息。

## 使用渠道 {#working-with-channels}

您可以编辑、复制、预览和删除渠道，以及查看渠道属性和功能板。

>[!NOTE]
>
>单击左侧的图标可选择某个项目。例如，单击渠道图标后，可执行以下操作，如下图所示。

![screen_shot_2018-08-23at10208pm](assets/screen_shot_2018-08-23at10208pm.png)

### 在渠道中添加/编辑内容 {#adding-editing-content-to-a-channel}

要在渠道中添加或编辑内容，请按照以下步骤操作：

1. 单击要编辑的渠道（如上图所示）。
1. Click **Edit** from the top left corner of the action bar to edit the channel properties. 此时会打开编辑器，您可以在其中将资产/组件添加到要发布的渠道。

![chlimage_1-44](assets/chlimage_1-44.png)

**将视频上传到渠道**&#x200B;按照以下步骤将视频上传到渠道：

1. 选择要上传视频的渠道。
1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。
1. 在“资产”下选择&#x200B;**视频**，然后拖放所需的视频。

>[!NOTE]
>
>如果您在将视频上传到渠道时遇到问题，请参阅“管理屏幕”下的[视频疑难解答](troubleshoot-videos.md)。

### 查看属性 {#viewing-properties}

要查看或编辑渠道的属性，请按照以下步骤操作：

1. 单击要编辑的渠道。
1. 单击操作栏中的**属性**以查看／编辑渠道属性。 您可以在以下选项卡中更改选项。

![player2-3](assets/player2-3.gif)

### 查看功能板 {#viewing-dashboard}

要查看渠道的功能板，请按照以下步骤操作：

1. 单击要编辑的渠道。
1. Click **View Dashboard** from the action bar to view the dashobard. 此时会打开&#x200B;**渠道信息**&#x200B;和&#x200B;**已指定显示**&#x200B;面板，如下图所示：

![player2-4](assets/player2-4.gif)

### 渠道信息 {#channel-information}

“渠道信息”面板描述了渠道属性以及渠道的预览。 此外，该面板还提供了有关渠道是处于脱机还是联机状态的信息。

单击&#x200B;**渠道信息**&#x200B;操作栏中的 (**...**) 可查看渠道属性、编辑渠道内容或更新渠道缓存（脱机内容）。

![screen_shot_2017-12-20at82048am](assets/screen_shot_2017-12-20at82048am.png)

### 联机和脱机渠道 {#online-and-offline-channels}

>[!NOTE]
>
>默认情况下，当您创建渠道时，该渠道为脱机。

创建渠道时，可以将其定义为联机渠道或脱机渠道。

“联机渠道”******&#x200B;将会在实时环境中显示更新的内容，而“脱机渠道”******&#x200B;则会显示缓存的内容。

请按照以下步骤使渠道处于联机状态：

1. 从TestProject的Channels **文件夹中** ，导 **航到TestChannel** 频道 ****。

   选择渠道。

   ![chlimage_1-45](assets/chlimage_1-45.png)

   单击操作栏中的&#x200B;**查看功能板**&#x200B;以查看播放器的状态。**渠道信息**面板提供有关渠道是联机还是脱机的信息。

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. 单击操作栏中的&#x200B;**属性**，然后导航到&#x200B;**渠道**&#x200B;选项卡，如下所示：

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. 选中使 **渠道联机** ，使渠道联机。

   单击&#x200B;**保存并关闭**&#x200B;以保存您的选项。

   ![screen_shot_2018-08-23at15525pm](assets/screen_shot_2018-08-23at15525pm.png)

   此时会显示渠道功能板，并且&#x200B;**渠道信息**&#x200B;面板会显示播放器处于联机状态。

   ![chlimage_1-48](assets/chlimage_1-48.png)

#### 设备功能板中的自动更新与手动更新 {#automatic-versus-manual-updates-from-the-device-dashboard}

下表总结了与设备功能板中的自动更新和手动更新相关的事件。

<table> 
 <tbody> 
  <tr> 
   <td><strong>事件</strong></td> 
   <td><strong>设备自动更新</strong></td> 
   <td><strong>设备手动更新</strong></td> 
  </tr> 
  <tr> 
   <td>在线渠道的更改</td> 
   <td>内容已自动更新</td> 
   <td><p>在“设备：推送配置”</p> <p>或者，</p> <p>设备上更新的 <strong><i>内容：重新启动</i></strong></p> </td> 
  </tr> 
  <tr> 
   <td>脱机渠道中的更改，但不会触发渠道“推送内容”（无脱机包重新创建）</td> 
   <td>无内容更新</td> 
   <td>无内容更新</td> 
  </tr> 
  <tr> 
   <td>将触发脱机渠道和渠道“推送内容”中的更改（新的脱机包）</td> 
   <td>内容已自动更新</td> 
   <td><p>设备上更新的 <strong><i>内容：推送配置</i></strong></p> <p>或者，</p> <p>设备上更新的 <strong><i>内容：重新启动</i></strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>配置更改</p> 
    <ul> 
     <li>显示（强制渠道）</li> 
     <li>设备</li> 
     <li>渠道分配（新渠道，已删除渠道）</li> 
     <li>渠道分配（角色、事件、计划）</li> 
    </ul> </td> 
   <td>配置已自动更新</td> 
   <td><p>在设备上更新 <strong><i>的配置：推送配置</i></strong></p> <p>或者，</p> <p>在设备上更新 <strong><i>的配置：重新启动</i></strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### 已指定显示 {#assigned-displays}

“已指定显示”面板显示了与渠道关联的显示屏。该面板提供了分配的显示屏的快照以及分辨率。

关联的显示屏将列在&#x200B;**已指定显示**&#x200B;面板中，如下所示：

![chlimage_1-49](assets/chlimage_1-49.png)

>[!NOTE]
>
>要了解如何在位置创建显示屏，请参阅：
>
>* [创建和管理位置](managing-locations.md)
>* [创建和管理显示屏](managing-displays.md)
>



此外，单击&#x200B;**已指定显示**&#x200B;面板中的显示屏可查看显示屏信息，如下所示：

![chlimage_1-50](assets/chlimage_1-50.png)

### 后续步骤 {#the-next-steps}

创建渠道并在渠道中添加/编辑内容后，下一步是了解如何创建位置和显示屏。此外，还需将渠道分配到该显示屏。

有关后续步骤，请参阅以下资源：

* [创建和管理渠道](managing-channels.md)
* [创建和管理位置](managing-locations.md)
* [创建和管理显示屏](managing-displays.md)