---
title: 指定要嵌入的字体
seo-title: Specify fonts to embed
description: 了解如何指定要嵌入的字体。
seo-description: Learn how to specify fonts to embed.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: e24f4123-bed3-4096-b3fb-22deb1c1e9b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 2%

---

# 指定要嵌入的字体{#specify-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以指定始终嵌入或从不嵌入由输出使用的表单的字体。 嵌入字体会增加表单的文件大小。 嵌入了用户在其系统上不太可能具有的异常字体，并且不会嵌入他们将安装的常用字体。

>[!NOTE]
>
>如果为“输出”指定了自定义XCI文件，则XCI文件中的嵌入字体选项将覆盖这些设置。 (请参阅 [为输出指定文件位置](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. 在管理控制台中，单击服务>输出。
1. 在“字体嵌入设置”下的“始终嵌入字体”框中，键入要与表单嵌入的字体名称，并用逗号分隔。 仅当在表单中使用您指定的字体时，这些字体才会嵌入生成的表单中。 如果在传递到服务的XCI文件中打开了嵌入字体选项，则忽略此设置。 在这种情况下，PDF中使用的所有字体始终会被嵌入。
1. 在“从不嵌入字体”框中，键入不要与表单嵌入的字体的名称，并使用逗号分隔。 您指定的字体不会嵌入到PDF中，即使这些字体在生成的PDF中使用也是如此。 如果在传递到服务的XCI文件中关闭了嵌入字体选项，则会忽略此设置。 在这种情况下，PDF中使用的字体均未嵌入。
1. 单击“保存”。
