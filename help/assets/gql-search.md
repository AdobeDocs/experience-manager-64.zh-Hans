---
title: GQL全文搜索
description: 在中浏览GQL全文搜索功能 [!DNL Experience Manager] 资产。 可使用它根据特定元数据（如标题、描述和作者名称）搜索资产。
contentOwner: AG
feature: Search,Metadata
role: User
exl-id: e819501c-4ac3-447f-944c-67adc42e8c61
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 2%

---

# GQL全文搜索 {#gql-full-text-search}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在中浏览GQL全文搜索功能 [!DNL Experience Manager] 资产。 可使用它根据特定元数据（如标题、描述和作者名称）搜索资产。

GQL全文搜索功能允许您根据特定元数据（如标题、描述、作者等）搜索资产。

要根据资产的元数据（例如标题）搜索资产，请在搜索面板中指定元数据关键字后跟其值。 GQL全文搜索功能将仅获取其元数据与您输入的相应值完全匹配的资产。

例如，要搜索标题为“Target”的资产，请执行以下步骤：

## 搜索资产 {#searching-assets}

1. 在Assets用户界面的工具栏中，单击或点按 **[!UICONTROL 搜索]** 图标来显示Omnisearch框。

   ![](assets/do-not-localize/chlimage_1.png)

1. 在Omnisearch框中光标，按Enter。
1. 单击或点按GlobalNav图标，以显示 **[!UICONTROL 过滤器]** 的上界。
1. 在Omni Search框中，指定值“Target”。 要将搜索限制为特定文件夹，请单击或点按“筛选器”面板中的浏览图标，然后选择该文件夹。 在这种情况下，仅在文件夹及其下的子文件夹内搜索匹配项。

   >[!NOTE]
   >
   >您还可以对文件夹执行全文搜索。 在这种情况下，必须指定非空全文搜索词。

   ![gql_search](assets/gql_search.png)

1. 按 **[!UICONTROL 输入]**. 的 [!DNL Assets] 用户界面仅显示标题与“Target”完全匹配的资产。

GQL全文搜索功能允许您根据以下内容搜索资产：

* 通过And运算组合您为多个元数据字段指定的值（属性）而构建的复杂查询
* 单个元数据字段的多个值
* 子字符串匹配

GQL全文搜索功能允许您根据以下元数据属性搜索资产。 属性的名称（例如作者、标题等）和值区分大小写。

>[!NOTE]
>
>GQL全文搜索仅适用于全文谓词。

| 属性 | 搜索格式（facet值） |
|---|---|
| [!UICONTROL 标题] | title:John |
| [!UICONTROL 创建者] | 创建者：John |
| [!UICONTROL 参与者] | 参与者：John |
| [!UICONTROL 位置] | 位置：印度 |
| [!UICONTROL 描述] | description:&quot;Sample Image&quot; |
| [!UICONTROL 创建者工具] | creatortool:&quot;Adobe Photoshop 7.0&quot; |
| [!UICONTROL 版权所有者] | copyrightowner:&quot;Adobe Systems&quot; |
| [!UICONTROL 参与者] | 参与者：John |
| [!UICONTROL 使用条款] | usageterms:&quot;CopyRights Reserved&quot; |
| [!UICONTROL 创建时间] | 已创建:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 过期日期] | 过期:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 准时] | ontime:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 关闭时间] | offtime:YYYY-MM-DDTHH:MM:SS.000+05:30..YYYY-MM-DDTHH:MM:SS.000+05:30 |
| [!UICONTROL 时间范围] （过期日期，offtime） | facet字段：下限……上限 |
| [!UICONTROL 路径] | /content/dam/&lt;folder name=&quot;&quot;> |
| [!UICONTROL PDF 标题] | pdftitle:&quot;Adobe文档&quot; |
| [!UICONTROL 主题] | 主题：&quot;培训&quot; |
| [!UICONTROL 标记] | 标记：&quot;Location And Travel&quot; |
| [!UICONTROL 类型] | type:&quot;image\png&quot; |
| [!UICONTROL 图像宽度] | width:lowerbound..上限 |
| [!UICONTROL 图像高度] | height:lowerbound..上限 |
| [!UICONTROL 人员] | person:John |

以下是复杂查询的搜索格式的一些示例：

* 要显示具有多个Facet字段的所有资产(例如：title=John Doe and creator tool = Adobe Photoshop):

tiltle:&quot;John Doe&quot; creatortool :Adobe(&amp;A);

* 当Facet值不是单个词而是句子时，显示所有资产(例如：title=Scott Reynolds)

title:&quot;Scott Reynolds&quot;

* 要显示具有单个属性的多个值的资产(例如：title=Scott Reynolds或John Doe)

title:&quot;Scott Reynolds&quot; OR &quot;John Doe&quot;

* 要显示属性值以特定字符串开头的资产(例如：标题是Scott Reynolds)

title:&quot;Scott&quot;

* 要显示属性值以特定字符串结尾的资产(例如：标题是Scott Reynolds)

title:&quot;Reynolds&quot;

* 要显示包含属性值且其中包含特定字符串的资产(例如：title =巴塞尔会议室)

标题：&quot;Meeting&quot;;

* 要显示包含特定字符串且具有特定属性值的资产(例如：在标题为John Doe的资产中搜索字符串Adobe)

ast;Adobe&amp;ast;title:&quot;John Doe &quot;OR title:&quot;John Doe&quot; &amp;ast;Adobe&amp;ast;

>[!NOTE]
>
>不能将属性路径、限制、大小和orderby与任何其他属性绑定。
>
>用户生成属性的关键字是其属性编辑器中的字段标签（以小写形式显示），并删除空格。

>[!NOTE]
>
>如果您编写JCR查询以仅搜索子资产，则还会显示匹配的引用资产以及匹配的子资产。

全文搜索还支持诸如 — 、^等运算符。 要将这些字母作为字符串文字搜索，请用双引号将搜索表达式引住。 例如，使用“Notebook - Beauty”而不是“Notebook - Beauty”。

## 提升搜索 {#boosting-search}

您可以提高特定资产的关键词相关性，以帮助根据关键词提高搜索量。 换言之，在您基于这些关键词进行搜索时，向其促销特定关键词的图像会显示在搜索结果的顶部。

1. 从资产UI中，打开要提升关键词的资产的属性页面。
1. 切换到 **[!UICONTROL 高级]** 选项卡，单击/点按 **[!UICONTROL 添加]** 在 **[!UICONTROL 提升搜索关键词]**.

   ![elevate_for_search](assets/elevate_for_search.png)

1. 在 **[!UICONTROL Search Promote]** 框中，指定要提升对图像搜索的关键字，然后单击/点按 **[!UICONTROL 添加]**. 如有必要，请以相同方式指定多个关键词。

   ![add_search_word](assets/add_search_word.png)

1. 单击/点按 **[!UICONTROL 保存并关闭]**.
1. 使用Omnisearch框搜索关键词。 您为其促销此关键词的资产将显示在热门搜索结果中。
