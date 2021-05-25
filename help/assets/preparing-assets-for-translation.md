---
title: 准备翻译资产
description: 创建语言根文件夹以准备翻译多语言资产。
contentOwner: AG
feature: 项目，翻译
role: Business Practitioner,Administrator
exl-id: cc6c4f9e-8e22-4622-8b24-230ae258351c
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---

# 准备翻译资产{#preparing-assets-for-translation}

多语言资产是指包含多种语言的二进制文件、元数据和标记的资产。 通常，资产的二进制文件、元数据和标记以一种语言存在，然后将这些语言翻译成其他语言，以用于多语言项目。

在Adobe Experience Manager(AEM)Assets中，多语言资产包含在文件夹中，其中每个文件夹都包含使用不同语言的资产。

每个语言文件夹都称为语言副本。 语言副本的根文件夹（称为语言根）可标识语言副本中内容的语言。 例如，*/content/dam/it*&#x200B;是意大利语语言副本的意大利语根。 语言副本必须使用正确配置的语言根](preparing-assets-for-translation.md#creating-a-language-root)，以便在执行源资产的翻译时定位正确的语言。[

最初为其添加资产的语言副本是主要语言。 语言主语是翻译成其他语言的源。

示例文件夹层次结构包括多种语言根：

```java
/content
    /- dam
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

请执行以下步骤以准备资产以进行翻译：

1. 创建语言主目录的语言根目录。 例如，示例文件夹层次结构中英语语言副本的语言根目录为`/content/dam/en`。 确保根据[创建语言根](preparing-assets-for-translation.md#creating-a-language-root)中的信息正确配置语言根。

1. 将资产添加到主语言。
1. 创建您需要语言副本的每种目标语言的语言根目录。

## 创建语言根{#creating-a-language-root}

要创建语言根目录，请创建一个文件夹并使用ISO语言代码作为Name属性的值。 创建语言根目录后，可以在语言根目录的任何级别创建语言副本。

例如，示例层次结构的意大利语语言副本的根页面具有`it`作为Name属性。 名称属性用作存储库中资产节点的名称，因此可确定资产的路径。(`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. 在资产控制台中，单击／点按创 **[!UICONTROL 建]** ，然后从 **[!UICONTROL 菜单中选]** 择文件夹。

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. 在“名称”字段中，键入格式为`<language-code>`的国家/地区代码。

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. 单击或点按&#x200B;**[!UICONTROL 创建]**。语言根目录将在资产控制台中创建。

## 查看语言根{#viewing-language-roots}

触屏优化UI提供了“引用”面板，其中显示了在AEM Assets中创建的语言根列表。

1. 在资产控制台中，选择要为其创建语言副本的语言主要。
1. 单击或点按GlobalNav图标，然后选择&#x200B;**[!UICONTROL 引用]**&#x200B;以打开引用窗格。

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. 在引用窗格中，单击或点按&#x200B;**[!UICONTROL 语言副本]**。 语言副本面板会显示资产的语言副本。

   ![chlimage_1-123](assets/chlimage_1-123.png)
