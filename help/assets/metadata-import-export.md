---
title: 批量元数据导入和导出
description: 本文介绍了如何批量导入和导出元数据。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 956cdec4-2ba8-43c9-9122-564d764f4681
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 9%

---

# 批量元数据导入和导出 {#bulk-metadata-import-and-export}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[!DNL Experience Manager] 资产允许您使用CSV文件批量导入资产元数据。 您可以通过导入CSV文件，对最近上传的资产或现有资产进行批量更新。 您还可以以CSV格式从第三方系统批量摄取资产元数据。

## 导入元数据 {#import-metadata}

元数据导入是异步的，不会影响系统性能。 如果选中了工作流标记，则由于XMP写回活动，因此同时更新多个资产的元数据可能会占用大量资源。 在精益服务器使用期间规划此类导入，以防止对其他用户的性能产生影响。

>[!NOTE]
>
>要导入自定义命名空间的元数据，请首先注册命名空间。

要批量导入元数据，请执行以下步骤：

1. 导航到Assets用户界面，然后点按/单击 **[!UICONTROL 创建]** 中。
1. 从菜单中，选择 **[!UICONTROL 元数据]**.
1. 在 **[!UICONTROL 元数据导入]** 页面，点按/单击 **[!UICONTROL 选择文件]**.  选择包含元数据的 CSV 文件。
1. 确保CSV文件包含以下参数：

   | 元数据导入参数 | 描述 |
   |:---|:---|
   | [!UICONTROL 批量大小] | 要为其导入元数据的批次中的资产数量。 默认值为 50。最大值为100。 |
   | [!UICONTROL 字段分隔符] | 默认值为 `,`  — 逗号。 您可以指定任何其他字符。 |
   | [!UICONTROL 多值分隔符] | 元数据值的分隔符。 默认值为 `|`  — 管道。 |
   | [!UICONTROL 启动工作流] | 默认为False。 如果设置为true，则默认设置对 `DAM Metadata WriteBack Workflow` (将元数据写入二进制XMP数据)。 启用工作流会对系统产生性能影响。 |
   | [!UICONTROL 资产路径列名称] | 为包含资产的CSV文件定义列名称。 |

1. 点按/单击 **[!UICONTROL 导入]** 中。 导入元数据后，系统会向您的通知收件箱发送通知。 导航到资产属性页面，并验证是否为资产正确导入了元数据值。

要在导入元数据时添加日期和时间戳，请使用 `YYYY-MM-DDThh:mm:ss.fff-00:00` 日期和时间的格式。 日期和时间以 `T`, `hh` 是24小时格式， `fff` 为纳秒，并且 `-00:00` 是时区偏移。 例如， `2020-03-26T11:26:00.000-07:00` 于2020年3月26日11时:26:太平洋标准时间上午00点。

>[!CAUTION]
>
>如果日期格式不匹配 `YYYY-MM-DDThh:mm:ss.fff-00:00`，则不会设置日期值。 导出的元数据CSV文件的日期格式为 `YYYY-MM-DDThh:mm:ss-00:00`. 如果要导入该值，请通过添加表示为的纳秒值，将其转换为可接受的格式 `fff`.

## 导出元数据 {#export-metadata}

批量导出元数据的一些用例包括：

* 迁移资产时，在第三方系统中导入元数据。
* 与更广的项目团队共享资产元数据。
* 测试或审核元数据以确保合规性。
* 将元数据外部化以实现单独的本地化。

您可以以CSV格式导出多个资产的元数据。 元数据是异步导出的，不会影响系统性能。 要导出元数据， [!DNL Experience Manager] 遍历资产节点的属性 `jcr:content/metadata` 及其子节点，并将元数据属性导出为CSV文件。

要批量导出多个资产的元数据，请执行以下步骤：

1. 选择包含要导出元数据的资产的资产文件夹。 在工具栏中，选择 **[!UICONTROL 导出元数据]**.

1. 在 [!UICONTROL 元数据导出] 对话框，请指定CSV文件的名称。 要导出子文件夹中资产的元数据，请选择 **[!UICONTROL 在子文件夹中包含资产]**.

   ![export_metadata_page](assets/export_metadata_page.png)

1. 选择所需的选项。 提供文件名，并在必要时提供日期。
1. 在 **[!UICONTROL 要导出的属性]**，指定是要导出全部属性还是特定属性。 如果您选择 **[!UICONTROL 选择性]** 要导出的属性，请添加所需的属性。

1. 在工具栏中，点按/单击 **[!UICONTROL 导出]**. 系统会显示一条消息，确认已导出元数据。 关闭消息。

1. 打开导出作业的收件箱通知。选择作业，然后单击工具栏中的&#x200B;**[!UICONTROL 打开]**。要下载包含元数据的 CSV 文件，请点按/单击工具栏中的 **[!UICONTROL CSV 下载]**。单击&#x200B;**[!UICONTROL 关闭]**。

   ![csv_download](assets/csv_download.png)
