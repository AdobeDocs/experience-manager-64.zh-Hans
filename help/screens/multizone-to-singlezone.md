---
title: 多区到单区接管循环
seo-title: 多区到单区接管循环
description: '可查看本页以了解AEM Screens项目中的多区域到单区域接管循环。  '
seo-description: 'AEM Screens项目中的多区域到单区域接管循环。  '
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# 多区到单区接管循环{#single-zoneto-multizone}

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

1. 创建一个名为 **TakeoverLoop的AEM Screens项目**，如下所示。

   >[!NOTE]
   >
   >要了解有关在AEM Screens中创建和管理项目的更多信息，请参阅 [创建项目](/help/screens/creating-a-screens-project.md)。

   ![](assets/takeover-loop1.png)

1. **创建分屏渠道**

   1. 选择渠 **道文件夹** ，然后单击操 **作栏中的创建** ，以打开向导以创建渠道。
   1. 从向 **导中选择Left-L Bar Split Screen Channel** ，然后创建标题为MultiZoneLayout的 **渠道**。

      ![](assets/takeover-loop2.png)

   1. Select the **MultiZoneLayout** channel and click **Edit** from the action bar to open the editor. 将资产拖放到每个区域。 以下示例展示了渠道中的视频、图像和文本横幅，如下所示。
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