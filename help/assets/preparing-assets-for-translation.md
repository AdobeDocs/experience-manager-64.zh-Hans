---
title: 准备要翻译的资产
description: 创建语言根文件夹，为翻译多语言资产做准备。
contentOwner: AG
feature: Projects,Translation
role: Business Practitioner,Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 3%

---


# 准备翻译资产{#preparing-assets-for-translation}

多语言资产是指包含多语言二进制文件、元数据和标记的资产。 通常，资产的二进制文件、元数据和标记以一种语言存在，然后将它们翻译为其他语言，以用于多语言项目。

在Adobe Experience Manager(AEM)资产中，多语言资产包含在文件夹中，其中每个文件夹都包含不同语言的资产。

每个语言文件夹都称为语言副本。 语言副本的根文件夹（称为语言根）标识语言副本中内容的语言。 例如，*/content/dam/it*&#x200B;是意大利语语言副本的意大利语根。 语言副本必须使用[正确配置的语言根](preparing-assets-for-translation.md#creating-a-language-root)，以便在执行源资源的翻译时锁定正确的语言。

您最初为其添加资产的语言副本是主要语言。 主语言是翻译为其他语言的源。

示例文件夹层次结构包括几个语言根：

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

请执行以下步骤来准备要翻译的资产：

1. 创建主语言的语言根。 例如，示例文件夹层次结构中英文副本的语言根目录为`/content/dam/en`。 确保根据[创建语言根](preparing-assets-for-translation.md#creating-a-language-root)中的信息正确配置语言根。

1. 将资产添加到主语言。
1. 创建您需要语言副本的每种目标语言的语言根。

## 创建语言根{#creating-a-language-root}

要创建语言根目录，请创建一个文件夹并使用ISO语言代码作为“名称”属性的值。 创建语言根目录后，可以在语言根目录的任何级别创建语言副本。

例如，示例层次结构的意大利语语言副本的根页面具有`it`作为“名称”属性。 名称属性用作存储库中资产节点的名称，因此可确定资产的路径。(`https://[AEM_server]:[port]/assets.html/content/dam/it/*`)

1. 在资产控制台中，单击／点按创 **[!UICONTROL 建]** ，然后从 **[!UICONTROL 菜单中选]** 择文件夹。

   ![chlimage_1-120](assets/chlimage_1-120.png)

1. 在“名称”字段中，键入格式为`<language-code>`的国家/地区代码。

   ![chlimage_1-121](assets/chlimage_1-121.png)

1. 单击或点按&#x200B;**[!UICONTROL 创建]**。语言根目录是在“资产”控制台中创建的。

## 查看语言根{#viewing-language-roots}

触屏优化UI提供了一个“引用”面板，其中显示了在AEM Assets中创建的语言根列表。

1. 在“资产”控制台中，选择要为其创建语言副本的语言主要版本。
1. 单击或点按GlobalNav图标，然后选择&#x200B;**[!UICONTROL 引用]**&#x200B;以打开“引用”窗格。

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. 在“引用”窗格中，单击或点按&#x200B;**[!UICONTROL 语言副本]**。 “语言副本”面板显示资源的语言副本。

   ![chlimage_1-123](assets/chlimage_1-123.png)

