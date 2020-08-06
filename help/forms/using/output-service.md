---
title: 输出服务
seo-title: 输出服务
description: 描述输出服务，它是AEM文档服务的一部分
seo-description: 描述输出服务，它是AEM文档服务的一部分
uuid: acd64bbb-91df-49bc-9216-2e860812bbe9
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services
discoiquuid: 8b96ba2d-007e-472a-875f-2caedd35ecf4
translation-type: tm+mt
source-git-commit: de440f57091d814a0a7ff48e9a0383c5415a0a5b
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# 输出服务 {#output-service}

## 概述 {#overview}

输出服务是AEM文档服务的一部分的OSGi服务。 输出服务支持AEM Forms设计器的各种输出格式和输出设计功能。 输出服务可以转换XFA模板和XML数据以生成各种格式的打印文档。

输出服务允许您创建应用程序，它们允许您：

* 使用XML数据填充模板文件，生成最终表单文档。
* 以各种格式生成输出表单，包括非交互式PDF、PostScript、PCL和ZPL打印流。
* 从XFA表单PDF生成打印PDF。
* 通过将多组数据与提供的模板合并，批量生成PDF、PostScript、PCL和ZPL文档。

>[!NOTE]
>
>输出服务是32位应用程序。 在Microsoft Windows上，32位应用程序最多可使用2 GB内存。 该限制也适用于输出服务。

## 创建非交互式表单文档 {#creating-non-interactive-form-documents}

![usingoutput_modified](assets/usingoutput_modified.png)

通常，您使用AEM Forms设计器创建模板。 输出 `generatePDFOutput` 服 `generatePrintedOutput` 务的和API允许您直接将这些模板转换为各种格式，包括PDF、PostScript、ZPL和PCL。

操 `generatePDFOutput` 作生成PDF，而操 `generatePrintedOutput` 作生成PostScript、ZPL和PCL格式。 这两个操作的第一个参数接受模板文件的名称（例如）或 `ExpenseClaim.xdp`包含模板的文档对象。 指定模板文件的名称时，还应指定内容根作为包含模板的文件夹的路径。 您可以使用或参数指 `PDFOutputOptions` 定内容 `PrintedOutputOptions` 根。 有关可以使用这些参数指定的其他选项的详细信息，请参阅Javadoc。

第二个参数接受与模板合并的XML文档，同时生成输出文档。

操 `generatePDFOutput` 作还可以接受基于XFA的PDF表单作为输入，并将非交互式版本的PDF表单作为输出返回。

## 生成非交互式表单文档 {#generating-non-interactive-form-documents}

考虑一种情况，即您拥有一个或多个模板以及每个模板的多个XML数据记录。

使用输 `generatePDFOutputBatch` 出服 `generatePrintedOutputBatch` 务的和操作为每条记录生成打印文档。

您还可以将记录合并为一个文档。 这两个操作都采用四个参数。

第一个参数是一个映射，它包含一个任意字符串作为键，模板文件的名称作为值。

第二个参数是另一个Map，其值是包含XML数据的文档对象。 该键与您为第一个参数指定的相同。

或的第三个参 `generatePDFOutputBatch` 数 `generatePrintedOutputBatch` 的类型或 `PDFOutputOptions` 分别 `PrintedOutputOptions` 为。

参数类型与和操作的参数类型相 `generatePDFOutput` 同， `generatePrintedOutput` 且效果相同。

第四个参数的类型 `BatchOptions`是，用于指定是否可以为每个记录生成单独的文件。 此参数的默认值为false。

同 `generatePrintedOutputBatch` 时返 `generatePDFOutputBatch` 回类型值 `BatchResult`。 该值包含一列表生成的文档。 它还包含一个XML格式的元数据文档，其中包含与生成的每个文档相关的信息。
