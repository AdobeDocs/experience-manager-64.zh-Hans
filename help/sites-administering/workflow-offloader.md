---
title: 资产工作流卸载程序
seo-title: 资产工作流卸载程序
description: 了解资产工作流卸载程序。
seo-description: 了解资产工作流卸载程序。
uuid: d1c93ef9-a0e1-43c7-b591-f59d1ee4f88b
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: content
content-type: reference
discoiquuid: 91f0fd7d-4b49-4599-8f0e-fc367d51aeba
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '601'
ht-degree: 0%

---


# 资产工作流卸载程序{#assets-workflow-offloader}

资产工作流卸载程序允许您启用Adobe Experience Manager(AEM)资产的多个实例，以减少主（引导）实例的处理负荷。 处理负载分布在引线实例和添加到引线实例的各种卸载程序（工作器）实例之间。 分配资产的处理负荷，提高了AEM Assets处理资产的效率和速度。 此外，它还有助于分配专用资源以处理特定MIME类型的资产。 例如，您可以在拓扑中分配特定节点，以仅处理InDesign资产。

## 配置卸载器拓扑{#configure-offloader-topology}

使用Configuration Manager为引线实例添加URL，为引线实例上的连接请求添加卸载程序实例的主机名。

1. 点按／单击AEM徽标，然后选择&#x200B;**工具** > **操作** > **Web控制台**&#x200B;以打开配置管理器。
1. 从Web控制台中，选择&#x200B;**Sling** > **拓扑管理**。

   ![chlimage_1-44](assets/chlimage_1-44.png)

1. 在拓扑管理页面中，点按／单击&#x200B;**配置Discovery.Oak服务**&#x200B;链接。

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. 在“发现服务配置”页中，在&#x200B;**拓扑连接器URL**&#x200B;字段中指定引线实例的连接器URL。

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. 在&#x200B;**拓扑连接器白名单**&#x200B;字段中，指定允许与引线实例连接的卸载程序实例的IP地址或主机名。 点按／单击&#x200B;**保存**。

   ![chlimage_1-47](assets/chlimage_1-47.png)

1. 要查看连接到引导实例的卸载程序实例，请转至&#x200B;**工具** > **部署** > **拓扑**，然后点按／单击群集视图。

## 禁用卸载{#disable-offloading}

1. 点按／单击AEM徽标，然后选择&#x200B;**工具** > **部署** > **卸载**。 **卸载浏览器**&#x200B;页面显示主题和可以使用这些主题的服务器实例。

   ![chlimage_1-48](assets/chlimage_1-48.png)

1. 禁用用户与之交互以上传或更改AEM资产的领导实例上的&#x200B;*com/adobe/granite/workflow/offloading*&#x200B;主题。

   ![chlimage_1-49](assets/chlimage_1-49.png)

## 在引导实例{#configure-workflow-launchers-on-the-leader-instance}上配置工作流启动器

将工作流启动器配置为在引导实例上使用&#x200B;**DAM更新资产卸载**&#x200B;工作流，而不是&#x200B;**Dam更新资产**&#x200B;工作流。

1. 点按／单击AEM徽标，然后选择&#x200B;**工具** > **工作流** > **启动器**&#x200B;以打开&#x200B;**工作流启动器**&#x200B;控制台。

   ![chlimage_1-50](assets/chlimage_1-50.png)

1. 找到事件类型分别为&#x200B;**已创建节点**&#x200B;和&#x200B;**已修改节点**&#x200B;的两个启动器配置，它们运行&#x200B;**DAM更新资产**&#x200B;工作流。
1. 对于每个配置，选中前面的复选框，然后点按／单击工具栏中的&#x200B;**视图属性**&#x200B;图标以显示&#x200B;**启动器属性**&#x200B;对话框。

   ![chlimage_1-51](assets/chlimage_1-51.png)

1. 在&#x200B;**Workflow**&#x200B;列表中，选择&#x200B;**DAM更新资产卸载**，然后点按／单击&#x200B;**保存**。

   ![chlimage_1-52](assets/chlimage_1-52.png)

1. 点按／单击AEM徽标，然后选择&#x200B;**工具** > **工作流** > **模型**&#x200B;以打开&#x200B;**工作流模型**&#x200B;页。
1. 选择&#x200B;**DAM更新资产卸载**&#x200B;工作流，然后点按／单击工具栏中的&#x200B;**编辑**&#x200B;以显示其详细信息。

   ![chlimage_1-53](assets/chlimage_1-53.png)

1. 显示&#x200B;**DAM工作流卸载**&#x200B;步骤的上下文菜单，然后选择&#x200B;**编辑**。 验证配置对话框的&#x200B;**通用参数**&#x200B;选项卡的&#x200B;**作业主题**&#x200B;字段中的条目。

   ![chlimage_1-54](assets/chlimage_1-54.png)

## 禁用卸载器实例{#disable-the-workflow-launchers-on-the-offloader-instances}上的工作流启动器

禁用在引导实例上运行&#x200B;**DAM更新资产**&#x200B;工作流的工作流启动程序。

1. 点按／单击AEM徽标，然后选择&#x200B;**工具** > **工作流** > **启动器**&#x200B;以打开&#x200B;**工作流启动器**&#x200B;控制台。

   ![chlimage_1-55](assets/chlimage_1-55.png)

1. 找到事件类型分别为&#x200B;**已创建节点**&#x200B;和&#x200B;**已修改节点**&#x200B;的两个启动器配置，它们运行&#x200B;**DAM更新资产**&#x200B;工作流。
1. 对于每个配置，选中前面的复选框，然后点按／单击工具栏中的&#x200B;**视图属性**&#x200B;图标以显示&#x200B;**启动器属性**&#x200B;对话框。

   ![chlimage_1-56](assets/chlimage_1-56.png)

1. 在**激活**部分，拖动滑块以禁用工作流启动器，然后点按／单击保存&#x200B;**以禁用它。**

   ![chlimage_1-57](assets/chlimage_1-57.png)

1. 在引导实例上传任何图像类型的资产。 验证卸载的实例为资产生成并移回的缩略图。

