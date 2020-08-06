---
title: 内容片段模型
seo-title: 内容片段模型
description: 内容片段模型用于创建包含结构化内容的内容片段。
seo-description: 内容片段模型用于创建包含结构化内容的内容片段。
uuid: 59176a32-1255-4a46-ad00-344bde843ea6
content-type: reference
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: 45e67357-4524-4d25-b5f1-21182b8e803c
translation-type: tm+mt
source-git-commit: 8b83be510a67fadaa666f2ba96fbb3fc82b9cb3d
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 13%

---


# 内容片段模型 {#content-fragment-models}

>[!CAUTION]
>
>某些内容片段功能需 [要应用AEM 6.4 Service Pack 2(6.4.2.0)或更高版本](../release-notes/sp-release-notes.md)。

内容片段模型定义内容片段的内 [容结构](content-fragments.md)。

## Enable Content Fragment Models {#enable-content-fragment-models}

>[!CAUTION]
>
>如果不启用内 **[!UICONTROL 容片段模型]**，则 **[!UICONTROL 创建选]** 项将不可用于创建新模型。

要启用内容片段模型，您需要：

* 在配置管理器中启用内容片段模型
* 将配置应用到您的资产文件夹

### 在Configuration Manager中启用内容片段模型 {#enable-content-fragment-models-in-configuration-manager}

要创 [建新的内容片段模型](#creating-a-content-fragment-model) , **您必须首先** 使用配置管理器启用它们：

1. 导航到&#x200B;**[!UICONTROL 工具]**、**[!UICONTROL 常规]**，然后打开&#x200B;**[!UICONTROL 配置浏览器]**。
1. 选择适合您的网站的位置。
1. 使 **[!UICONTROL 用创建]** 打开对话框，您可以：

   1. 指定 **[!UICONTROL 标题]**。
   1. 选择 **[!UICONTROL 内容片段模型]** ，以启用其使用。

   ![cfm-6420-09](assets/cfm-6420-09.png)

1. 选择 **[!UICONTROL 创建]** ，以保存定义。

### 将配置应用到您的资产文件夹 {#apply-the-configuration-to-your-assets-folder}

为内容片 **[!UICONTROL 段模型]** 启用配置全局后，用户创建的任何模型都可以用于任何资产文件夹中。

要将其他配置（即不包括全局配置）与类似的 Assets 文件夹一起使用，您必须定义连接。可使用&#x200B;**[!UICONTROL 云服务]**&#x200B;选项卡（位于相应文件夹的&#x200B;**[!UICONTROL 文件夹属性]**&#x200B;中）中的&#x200B;**[!UICONTROL 配置]**&#x200B;完成来此操作。

## 创建内容片段模型 {#creating-a-content-fragment-model}

1. 导航到 **[!UICONTROL 工具]**、资 **[!UICONTROL 产]**，然后打 **[!UICONTROL 开内容片段模型]**。
1. 导览至适合您的配置的文 [件夹](#enable-content-fragment-models)。
1. 使用 **[!UICONTROL 创建]** ，打开向导。

   >[!CAUTION]
   >
   >如果 [未启用内容片段模型的使用](#enable-content-fragment-models)，则 **“创建** ”选项将不可用。

1. 指定&#x200B;**[!UICONTROL 模型标题]**。您还可以根据需要添加&#x200B;**[!UICONTROL 描述]**。

   ![cfm-6420-10](assets/cfm-6420-10.png)

1. 使 **[!UICONTROL 用]** “创建”(Create)保存空模型。 将显示一条消息，指示操作成功，您可以选 **[!UICONTROL 择]** “打开”(Open)以立即编辑模型， **[!UICONTROL 或选择“]** 完成”(Done)以返回控制台。

## 定义内容片段模型 {#defining-your-content-fragment-model}

内容片段模型有效地定义所生成内容片段的结构。 使用模型编辑器，您可以添加和配置必填字段：

>[!CAUTION]
>
>编辑现有内容片段模型可能会影响相关片段。

1. 导航到 **[!UICONTROL 工具]**、资 **[!UICONTROL 产]**，然后打 **[!UICONTROL 开内容片段模型]**。

1. 导航到包含内容片段模型的文件夹。
1. 打开编辑所需的 **[!UICONTROL 模型]**; 使用快速操作，或先选择模型，然后从工具栏中选择操作。

   打开模型编辑器后，将显示：

   * 左： 字段已定义
   * 右侧：可用于创建字段的&#x200B;**[!UICONTROL 数据类型]**（可在创建字段后使用的&#x200B;**[!UICONTROL 属性]**）

   >[!NOTE]
   >
   >When a field is **Required**, the **Label** indicated in the left pane will be marked with an asterix (**&amp;ast;**).

   ![cfm-6420-12](assets/cfm-6420-12.png)

1. **添加字段**

   * 将所需数据类型拖动到字段的所需位置：

   ![cfm-6420-11](assets/cfm-6420-11.png)

   * 将字段添加到模型后，右侧面板将显示可为该 **特定** 数据类型定义的属性。 您可以在此处定义该字段的必需内容。 例如：

   ![cfm-6420-13](assets/cfm-6420-13.png)

1. **删除字段**

   选择所需字段，然后单击／点按垃圾桶图标。 系统将要求您确认该操作。

   ![cf-32](assets/cf-32.png)

1. 添加所有必填字段并定义属性后，请 **[!UICONTROL 使用]** “保存”保留定义。 例如：

   ![cfm-6420-14](assets/cfm-6420-14.png)

## 删除内容片段模型 {#deleting-a-content-fragment-model}

>[!CAUTION]
>
>删除内容片段模型可能会影响相关片段。

要删除内容片段模型，请执行以下操作：

1. 导航到 **[!UICONTROL 工具]**、资 **[!UICONTROL 产]**，然后打 **[!UICONTROL 开内容片段模型]**。

1. 导航到包含内容片段模型的文件夹。
1. 选择模型，然后从工 **[!UICONTROL 具栏]** 中选择删除。

   >[!NOTE]
   >
   >如果模型被引用，则会发出警告。 采取适当措施。

## 发布内容片段模型 {#publishing-a-content-fragment-model}

内容片段模型需要在发布任何相关内容片段时／之前发布。

要发布内容片段模型，请执行以下操作：

1. 导航到 **[!UICONTROL 工具]**、资 **[!UICONTROL 产]**，然后打 **[!UICONTROL 开内容片段模型]**。

1. 导航到包含内容片段模型的文件夹。
1. 选择您的模型，然后从工 **[!UICONTROL 具栏]** 中选择发布。

   >[!NOTE]
   >
   >如果发布的内容片段尚未发布模型，则将显示一个选择列表来指示此情况，并且该模型将随片段一起发布。

