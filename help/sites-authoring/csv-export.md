---
title: 导出到 CSV
seo-title: Export to CSV
description: 将有关页面的信息导出到本地系统上的CSV文件
seo-description: Export information about your pages to a CSV file on your local system
uuid: aa03adac-bbfb-4566-a153-25fe6f6843dd
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: d4473758-674a-42d6-923a-b536f7f9c1f7
exl-id: 52eb9c2f-ce29-4622-8726-802ac40246d4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 50%

---

# 导出到 CSV{#export-to-csv}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

**创建CSV导出** 允许您将页面的相关信息导出到本地系统上的CSV文件。

* 所下载的文件名为 `export.csv`
* 其内容取决于您选择的属性。
* 您可以定义导出的路径以及深度。

>[!NOTE]
>
>系统将使用您浏览器的下载功能及默认目标位置。

创建 CSV 导出向导允许您选择以下内容：

* 要导出的属性

   * 元数据

      * 修改时间
      * 发布时间
   * 分析

      * 页面视图
      * 独特访客
      * 页面停留时间


* 深度

   * 父级路径
   * 仅直接子项
   * 其他级别的子项
   * 级别

生成的 `export.csv` 文件可以用 Excel 或任何其他兼容的应用程序打开。

![chlimage_1-58](assets/chlimage_1-58.png)

创建 **CSV导出** 选项在浏览时可用 **站点** 控制台（在列表视图中）：它是 **创建** 下拉菜单：

![screen_shot_2018-03-21at154719](assets/screen_shot_2018-03-21at154719.png)

要创建 CSV 导出，请执行以下操作：

1. 必要时，打开&#x200B;**站点**&#x200B;控制台并导航到所需的位置。
1. 在工具栏中，选择 **创建** then **CSV导出** 要打开向导，请执行以下操作：

   ![screen_shot_2018-03-21at154758](assets/screen_shot_2018-03-21at154758.png)

1. 选择要导出的所需属性。
1. 选择&#x200B;**创建**。
