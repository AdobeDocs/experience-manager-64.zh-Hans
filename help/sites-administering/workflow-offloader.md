---
title: 资产工作流卸载程序
seo-title: Assets Workflow Offloader
description: 了解资产工作流卸载程序。
seo-description: Learn about the Assets Workflow Offloader.
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
exl-id: 2ca8e786-042b-44f6-ac60-834eca64f79f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '628'
ht-degree: 0%

---

# 资产工作流卸载程序{#assets-workflow-offloader}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

资产工作流卸载程序允许您启用Adobe Experience Manager(AEM)资产的多个实例，以减少主（领导）实例的处理负载。 处理负载分布在领导实例和您添加到该实例的各种卸载程序（工作程序）实例之间。 分配资产的处理负载可提高AEM Assets处理资产的效率和速度。 此外，它还有助于分配专用资源以处理特定MIME类型的资产。 例如，您可以在拓扑中分配特定节点，以仅处理InDesign资产。

## 配置卸载程序拓扑 {#configure-offloader-topology}

使用配置管理器为引导实例添加URL，为引导实例上的连接请求添加卸载程序实例的主机名。

1. 点按/单击AEM徽标，然后选择 **工具** > **操作** > **Web控制台** 打开配置管理器。
1. 从Web控制台中，选择 **Sling** >  **拓扑管理**.

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 在拓扑管理页面中，点按/单击 **配置Discovery.Oak服务** 链接。

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. 在发现服务配置页面中，为中的领导实例指定连接器URL **拓扑连接器URL** 字段。

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. 在 **拓扑连接器白名单** 字段中，指定允许与领导实例连接的卸载程序实例的IP地址或主机名。 点按/单击 **保存**.

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. 要查看与引线实例连接的卸载程序实例，请转到 **工具** > **部署** > **拓扑** ，然后点按/单击“群集”视图。

## 禁用卸载 {#disable-offloading}

1. 点按/单击AEM徽标，然后选择 **工具** > **部署** > **卸载**. 的 **卸载浏览器** 页面显示主题和服务器实例，这些主题可以使用。

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. 禁用 *com/adobe/granite/workflow/offloading* 主题介绍用户通过交互上传或更改AEM资产的领导实例。

   ![chlimage_1-49](assets/chlimage_1-49.png)

## 在领导实例上配置工作流启动器 {#configure-workflow-launchers-on-the-leader-instance}

配置工作流启动器以使用 **DAM更新资产卸载** 在领导实例而不是 **Dam更新资产** 工作流。

1. 点按/单击AEM徽标，然后选择 **工具** > **工作流** > **启动器** 打开 **工作流启动器** 控制台。

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. 找到事件类型的两个启动器配置 **已创建节点** 和 **已修改节点** 分别运行 **DAM更新资产** 工作流。
1. 对于每个配置，选中其前面的复选框，然后点按/单击 **查看属性** 图标来显示 **启动器属性** 对话框。

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. 从 **工作流** 列表，选择 **DAM更新资产卸载** 然后点按/单击 **保存**.

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. 点按/单击AEM徽标，然后选择 **工具** > **工作流** > **模型** 打开 **工作流模型** 页面。
1. 选择 **DAM更新资产卸载** 工作流，然后点按/单击 **编辑** 来显示其详细信息。

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. 显示 **DAM工作流卸载** 步骤，然后选择 **编辑**. 验证 **作业主题** 字段 **通用参数** 选项卡。

   ![chlimage_1-54](assets/chlimage_1-54.png)

## 在卸载程序实例上禁用工作流启动器 {#disable-the-workflow-launchers-on-the-offloader-instances}

禁用运行 **DAM更新资产** 工作流。

1. 点按/单击AEM徽标，然后选择 **工具** > **工作流** > **启动器** 打开 **工作流启动器** 控制台。

   ![chlimage_1-55](assets/chlimage_1-55.png)

1. 找到事件类型的两个启动器配置 **已创建节点** 和 **已修改节点** 分别运行 **DAM更新资产** 工作流。
1. 对于每个配置，选中其前面的复选框，然后点按/单击 **查看属性** 图标来显示 **启动器属性** 对话框。

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. 在**激活**部分中，拖动滑块以禁用工作流启动器，然后点按/单击 **保存** 来禁用它。

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. 在领导者实例上传图像类型的任何资产。 验证已卸载的实例为资产生成并移回的缩略图。
