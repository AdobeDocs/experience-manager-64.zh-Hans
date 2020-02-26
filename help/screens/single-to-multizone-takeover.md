---
title: 单区到多区接管
seo-title: 单区到多区接管
description: '可查看本页以了解AEM Screens项目中的单区到多区接管。  '
seo-description: '可查看本页以了解AEM Screens项目中的单区到多区接管。    '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# 单区到多区接管 {#single-zoneto-multizone}

## 用例描述 {#use-case-description}

本节介绍一个用例示例，其中着重介绍如何设置与单个区域布局通道替代的多区域布局通道。 每个渠道都有图像／视频资产的排序。

### 先决条件 {#preconditions}

在开始此使用案例之前，请确保您了解如何：

* **[创建和管理渠道](/help/screens/managing-channels.md)**
* **[创建和管理位置](/help/screens/managing-locations.md)**
* **[创建和管理计划](/help/screens/managing-schedules.md)**
* **[设备注册](/help/screens/device-registration.md)**

### 主要演员 {#primary-actors}

内容作者

## 设置项目 {#setting-up-the-project}

请按照以下步骤设置项目：

1. 创建一个名为 **ZonesDemo的AEM Screens项目**，如下所示。

   >[!NOTE]
   >
   >要了解有关在AEM Screens中创建和管理项目的更多信息，请参阅 [创建项目](/help/screens/creating-a-screens-project.md)。

   ![screen_shot_2019-02-21at35809pm](assets/SZtoMZ1.png)

1. **使用一个图像创建序列渠道**

   1. 选择渠 **道文件夹** ，然后单击操 **作栏中的创建** ，以打开向导以创建渠道。
   1. 从向 **导中选择序列渠道** ，然后创建标题为 **FullScreenOne的渠道**。

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ2.png)
   1. 选择渠道，然后单 **击操作栏中的** “编辑”以打开编辑器，并将图像拖放到该渠道，如下所示。
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ3.png)

1. **创建包含四个图像的2X2渠道**

   1. 选择渠 **道文件夹** ，然后单击操 **作栏中的创建** ，以打开向导以创建渠道。

   1. 从向 **导中选择** 2X2分屏渠道模板，并创建标题为TwobyTwoChannel的渠 **道**。

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ4.png)
   1. 选择渠道，然后单 **击操作栏中的** “编辑”以打开编辑器，并将四个图像（四个不同区域）拖放到该渠道，如下所示。
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ5.png)

1. **创建包含两张图像的1X2分屏渠道**

   1. 选择渠 **道文件夹** ，然后单击操 **作栏中的创建** ，以打开向导以创建渠道。

   1. 从向 **导中选择** 1X2分屏渠道模板，并创建标题为OnebyTwoChannel的渠 **道**。

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ6.png)
   1. 选择渠道，然后单 **击操作栏中的** “编辑”以打开编辑器，并将两个图像（两个不同的区域）拖放到该渠道，如下所示。
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ7.png)

1. **使用一个全屏视频创建渠道**

   1. 选择渠 **道文件夹** ，然后单击操 **作栏中的创建** ，以打开向导以创建渠道。

   1. 从向 **导中选择序列渠道** ，然后创建标题为FullScreensVideo的 **渠道**。

      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ8.png)
   1. 选择渠道并单击操 **作栏中的编辑** ，打开编辑器，将视频组件拖放到该渠道，然后添加所需的视频，如下所示。
      ![screen_shot_2019-02-21at35932pm](assets/SZtoMZ9.png)

## 设置从单一区域向多区域过渡的接管渠道 {#takeover-channel-setup}

1. **编辑单区域渠道以进行多区域接管**

   1. 选择您在步&#x200B;**骤** 1中创建的渠道(FullScreenOne)。
   1. 单击操作栏中的&#x200B;**编辑**&#x200B;以打开编辑器。将两个渠道组件和一个视频组件拖放到编辑器中。
   ![screen_shot_2019-02-21at40516pm](assets/SZtoMZ10.png)

1. **填充添加到FullScreenOne渠道的组件**

   1. 从 **FullScreenOne的编辑器中选择第一个渠道组件** ，然后单击 **配置** ，以指向在前几步中创建的渠道。 将渠道路径中的渠道路 **径添加到渠道组件** ，并将视频拖放到视频组件，如下所示。
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo1.gif)

1. **在转换时设置渠道的持续时间**

   >[!NOTE]
   >
   >默认情况下，资产将在每8秒之后过渡，但如果您希望资产在特定时间段后过渡，请按照以下步骤操作。

   1. 从 **FullScreenOne的编辑器中选择第二个渠道组件** ，然后单击 **设置** ，以配置此渠道的持续时间。 同样，设置渠道2的持续时间，如下所示。
在此示例中，时间设置为3秒。
   ![screen_shot_2019-02-21at40516pm](assets/SZ_MZvideo2.gif)

## 预览结果 {#previewing-result}

您可以单击编辑 **器中的** “预览”，并检查资产将如何从单个区域过渡到多个区域。

![](assets/SZ_MZvideo3.gif)
