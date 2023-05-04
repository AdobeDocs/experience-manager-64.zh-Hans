---
title: 搜索表单和资产
seo-title: Searching for forms and assets
description: 您可以使用AEM搜索在AEM实例中搜索表单和资产。 通过基本和高级搜索，您可以快速找到资产。
seo-description: You can search forms and assets in your AEM instance using AEM search. Basic and advanced search allows you to quickly locate your assets.
uuid: db6970aa-910a-4190-9790-9ffbbdc8adcc
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: f7f19679-cfc2-4ac0-9a26-685fad09276f
role: Admin
exl-id: c6e5c19a-9d93-470f-916e-7ef06c3de141
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 4%

---

# 搜索表单和资产 {#searching-for-forms-and-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以使用文本字符串或文本字符串以及通配符搜索表单或表单资产。 您还可以使用“搜索”面板中各个类别中提供的标准来缩小搜索范围。

当您选择一个或多个标准并指定文本字符串时，将返回文本和标准的交集作为搜索结果。 搜索结果与提供的表单和资产元数据一样好。

单击 ![aem6forms_search](assets/aem6forms_search.png)，以显示或隐藏搜索面板。

## 基本搜索 {#basic-search}

基本搜索是默认搜索，在不指定任何过滤器的情况下运行。 元数据属性的全文搜索由AEM Forms执行。

要运行基本搜索，请在文本字段中输入搜索查询并返回点击。 您还可以输入通配符(&amp;ast;)以匹配任意数量的字符。

Adobe Experience Manager会搜索元数据属性中输入的文本，并返回相应的结果。 如果键入多个词，则搜索操作将匹配要搜索的完整文本。

请注意以下有关基本搜索的要点：

* 使用表单和资产元数据属性进行搜索。
* 如果键入多个词，则搜索操作将匹配要搜索的完整文本。
* 搜索不区分大小写。 例如，在您键入 `geometrixx`，带有标题的资产 `Geometrixx`, `GEOMETRIXX`和 `GeoMetRixx` 会显示在搜索结果中。

* 不支持单词的部分匹配。 要使用部分字符串进行搜索，请使用&amp;ast;通配符。 但是，如果搜索查询与一个完整单词匹配，则会显示相应的表单或资产。
* 在搜索期间，会遵守并且不会裁切额外的空格。 例如， `My form` 与的搜索查询不同 `My form`.

* 如果元数据属性中字段的数据和显示值不同，则不能将显示值用作搜索参数。 例如，您无法根据状态（如“已修改”或“已发布”）进行搜索，因为这些属性以不同的格式存储。

## 高级搜索 {#advanced-search}

在搜索标准中，除了查询之外，您还可以指定一些搜索参数，以使基本搜索更加高效和集中。

![用于AEM表单和资产搜索的搜索字段和参数或过滤器](assets/search_forms_assets.png)

### 资产路径 {#asset-path}

通过使用资产路径筛选器，您可以将搜索结果限制为当前目录。 如果未选择在当前目录中搜索选项，则搜索结果将包含基目录中的资产。 如果当前页面不是目录，并且选择了“在当前目录中搜索”选项，则搜索会返回父目录中存在的资产。

### 资产修改 {#asset-modification}

选择以下选项之一，以在特定时间段内修改的所有资产中搜索。

| **选项** | **描述** |
|---|---|
| 2 小时前 | 搜索在过去两小时内修改的所有资产。 |
| 1 个星期前 | 搜索在过去一周内修改的所有资产。 |
| 1 个月前 | 搜索过去一个月内修改的所有资产。 |
| 1 年前 | 搜索过去一年内修改的所有资产。 |

### 资产状态 {#asset-status}

您可以使用以下状态之一搜索资产：

* **已发布**:搜索发布后发布且未修改的所有资产。

* **未发布**:搜索所有从未发布的资产。

* **已修改**:搜索发布后修改或取消发布的所有资产。

### 资产类型 {#asset-type}

您可以选择任意数量的资产类型。 搜索会返回所有选定资产类型的并集。

<table> 
 <tbody>
  <tr>
   <th>选项</th> 
   <th>描述</th> 
  </tr>
  <tr>
   <td>表单模板<br /> </td> 
   <td>在所有表单模板中搜索。<br /> </td> 
  </tr>
  <tr>
   <td>PDF表单</td> 
   <td>搜索所有PDF文档。</td> 
  </tr>
  <tr>
   <td>文档</td> 
   <td>搜索所有文档。</td> 
  </tr>
  <tr>
   <td>自适应表单<br /> </td> 
   <td>在所有自适应表单中搜索。</td> 
  </tr>
  <tr>
   <td>资源</td> 
   <td>搜索所有资源。<br /> </td> 
  </tr>
 </tbody>
</table>

### 标记 {#tags}

标记是附加到资产的标签，用于标识。 搜索时，从下拉列表中选择任意数量的标记，或根据需要添加自定义标记。 搜索结果包含所选标记的交集。
