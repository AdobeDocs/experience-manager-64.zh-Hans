---
title: 将Search&amp；提升功能添加到页面
seo-title: 将Search&amp；提升功能添加到页面
description: 集成Search&amp;Promote功能后，您可以使用Search&amp;Promote组件向页面添加关键字搜索、搜索结果页面搜索优化和横幅等功能。
seo-description: 集成Search&amp;Promote功能后，您可以使用Search&amp;Promote组件向页面添加关键字搜索、搜索结果页面搜索优化和横幅等功能。
uuid: 8831aa56-9d7f-44ca-9d32-5901bf762154
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 277d7e67-5778-48cb-89bb-29bcc734a485
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# Adding Search&amp;Promote features to your page {#adding-search-promote-features-to-your-page}

To integrate Search&amp;Promote capabilities in your web site, use the [!UICONTROL Search&amp;Promote] components to add the following features to your pages:

* 关键字搜索
* 搜索结果页面
* 搜索优化
* 横幅

请注意，仅当 AEM 管理员启用了 Search&amp;Promote 功能时，您才能使用这些功能。请参阅[与 Adobe Search&amp;Promote 集成](/help/sites-administering/search-and-promote.md)。

Search＆Promote 服务器上配置了一些 facet，这也是每个组件提供的信息。下表提供了每个组件的简要描述。后续部分详细介绍了这些组件的用法。

<table> 
 <tbody> 
  <tr> 
   <th>Search&amp;Promote组件</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td>横幅</td> 
   <td>显示横幅广告。 Banners are selected based on data gathered through Search&amp;Promote.<br /> </td> 
  </tr> 
  <tr> 
   <td>痕迹导航</td> 
   <td>显示搜索关键字以及用户已应用于搜索结果的筛选器序列。</td> 
  </tr> 
  <tr> 
   <td>复选框列表彩块化</td> 
   <td>用于选择facet以筛选搜索结果的复选框列表。</td> 
  </tr> 
  <tr> 
   <td>下拉列表彩块化</td> 
   <td>用于筛选搜索结果的facet下拉列表。</td> 
  </tr> 
  <tr> 
   <td>链接列表彩块化</td> 
   <td>用于筛选搜索结果的facet链接列表。</td> 
  </tr> 
  <tr> 
   <td>分页</td> 
   <td>用于在搜索结果的页面中导航的控件。</td> 
  </tr> 
  <tr> 
   <td>结果</td> 
   <td>显示关键字搜索的结果。</td> 
  </tr> 
  <tr> 
   <td>搜索</td> 
   <td>向页面添加搜索字段。</td> 
  </tr> 
 </tbody> 
</table>

## 创建搜索结果页面 {#creating-the-search-results-page}

使用 WCM“网站”控制台可创建一个显示搜索结果的页面。如果使用相同的 Search&amp;Promote 服务，则使用任何搜索组件获取的搜索结果都可以显示在此页面上。

允许用户查看搜索结果的组件是“结果”和“分页”。**[!UICONTROL 结果]**&#x200B;组件在编辑或设计模式下没有可配置的属性。“结果”组件只会列出搜索结果，其中提供了指向其他页面的链接，并且还显示了搜索关键字的结果数量。

![srresultscomp](assets/srchresultscomp.png)

**[!UICONTROL 分页]**&#x200B;组件使用户能够浏览搜索结果的多个页面。用户可以查看页数、移到下一页或上一页、选择要打开的页面，或将所有结果合并到一个页面。

![schpageination](assets/srchpagination.png)

You can configure the following component properties in [!UICONTROL Edit] mode to control runtime behavior:

* **[!UICONTROL 隐藏单个结果页]** -选择此选项可在搜索返回单个结果页时隐藏页面导航控件。
* **[!UICONTROL 隐藏第一页／最后一页]** -选择此选项可防止用户跳转至结果的第一页或最后一页。
* **[!UICONTROL 隐藏上一页／下一页]** -确定用户是否可以相对于当前页面导航结果页面。
* **[!UICONTROL 隐藏全部查看]** -确定用户是否可以将所有搜索结果合并到单个页面。 通常，提供分页数据可以更有效地使用服务器资源。选择此选项可阻止在一个响应消息中传输较大数据集。

## 允许按 facet 筛选结果 {#enabling-the-filtering-of-results-by-facets}

您可以允许用户按 facet 筛选搜索结果。The **[!UICONTROL Checkbox List Facet]**, **[!UICONTROL Dropdown Facet]**, and **[!UICONTROL Link List Facet]** components enable users to select one or more facets for filtering. 使用这些组件时，您还应包含&#x200B;**[!UICONTROL 痕迹导航]**&#x200B;组件。痕迹导航可指示当前使用的筛选器。

The **[!UICONTROL Checkbox List Facet**, **[!UICONTROL Dropdown Facet]**, and **[!UICONTROL Link List Facet]** components each have the following properties that you configure in **[!UICONTROL Edit]** mode:

* **[!UICONTROL Facet Name]** —用于筛选器的facet的名称。

**[!UICONTROL 复选框列表 Facet]** 组件会显示包含附带复选框的 facet 列表。使用&#x200B;**[!UICONTROL 复选框列表 Facet]**，用户可以查看包含多个 facet 项目的结果子集。例如，可以使用“品牌”facet，因为多个品牌可提供相同类型的产品。

每个与搜索结果关联的 facet 都会显示一个复选框。当用户选择某个复选框时，页面将重新加载以显示更新的结果集。所有复选框均会保留在页面上，以便客户可以随时在筛选器中添加或删除 facet：

![sandcheckboxcomp](assets/sandpcheckboxcomp.png)

**[!UICONTROL 下拉列表 Facet]** 组件使客户能够从下拉列表中选择一个 facet 项目。当您希望客户一次只关注一个 facet 项目时，此组件非常有用。例如，“专栏”facet 有助于客户能够按性别缩小产品搜索范围。John 要搜索“牛仔裤”**，然后在男士专栏中进行筛选。

下拉列表中填充了与所有搜索结果关联的 facet。在下拉列表中选择一个项目后，页面将重新加载以显示更新的结果集。下拉列表中的项目不会发生更改，以便客户可以随时切换 facet。

![sanddropdowndepartment](assets/sandpdropdowndepartment.png)

**[!UICONTROL 链接列表 Facet]** 组件使客户能够将焦点逐步缩小到归类为多个 facet 成员或 facet 的项目。

facet 成员显示为链接列表。每个链接的文本是与当前搜索结果关联的 facet 成员的名称。当客户单击 facet 链接时，页面将重新加载以显示更新的结果集。链接列表会相应地更新，以便能够进一步缩小焦点。

![andplinklistcomp](assets/sandplinklistcomp.png)

The links in the list also changes when a filter is applied from a different type of [!UICONTROL Search&amp;Promote] component. 使用多种类型的筛选器组件可以提供有效的筛选器组合。

**[!UICONTROL 痕迹导航]**&#x200B;组件使客户能够按照应用筛选器的顺序查看当前应用于搜索结果的筛选器。客户可以单击痕迹导航中的项目以还原到该筛选器组合。

![痕迹导航组件](assets/sandpbreadcrumbcomp.png)

您可以在编辑模式下配置痕迹导航的以下属性，以便自定义该组件的外观：

* **[!UICONTROL 分隔符]** -定义要充当每个痕迹导航之间分隔符的字符或字符串。 分隔符字段接受任何字符串作为输入。 默认设置为“>”（不带引号）
* **[!UICONTROL 尾部分隔符]** -定义要在痕迹导航末尾显示的字符或字符串。 “结尾分隔符”字段接受任何字符串作为输入。 此字段的默认设置为“blank”（即痕迹导航行末尾不显示任何内容）

## 添加搜索框 {#adding-search-boxes}

The **[!UICONTROL Search]** component enables customers to perform keyword searches. 可将“搜索”组件添加到要提供搜索访问权限的每个页面。

Configure the following properties in **[!UICONTROL Edit]** mode to control runtime behavior:

* **[!UICONTROL 结果页面路径]** -显示搜索结果的页面的路径。
* **[!UICONTROL 启用自动完成]** -选择此选项可在客户开始在搜索框中键入内容时显示建议的搜索关键字。

![sandsearchcomp](assets/sandpsearchcomp.png)

## 添加横幅 {#adding-banners}

The **[!UICONTROL Banners]** component displays banner advertisements according to the customer&#39;s Search&amp;Promote searches. Search&amp;Promote 服务器上的逻辑会确定要显示的横幅。例如，搜索牛仔裤可能会显示与时装相关的横幅。在男士专栏中进行筛选可以进一步优化横幅的选择。

The **[!UICONTROL Banners]** component provides one configurable property named **[!UICONTROL Banner Area]**. In **[!UICONTROL Edit]** mode, select one of the property values to specify how the banner appears. Search&amp;Promote 服务会确定您可以从中选择的值列表。

## Search&amp;Promote 搜索页面示例 {#example-search-promote-search-page}

此图显示了在页面中添加的用于创建以下功能齐全的 Search&amp;Promote 结果页面的组件。

![1328213789109](assets/1328213789109.png)![沙盒示例](assets/sandppageexample.png)

