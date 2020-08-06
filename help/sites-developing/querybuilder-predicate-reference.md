---
title: 查询生成器谓词引用
seo-title: 查询生成器谓词引用
description: 完整的查询生成器API谓词引用。
seo-description: 完整的查询生成器API谓词引用。
uuid: af0e269e-7d52-4032-b22e-801c7b5dccfa
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 94a05894-743a-4ace-a292-bfee90ba9068
translation-type: tm+mt
source-git-commit: 14daff213297d2435765dd46039f346ce3868ac5
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 3%

---


# 查询生成器谓词引用{#query-builder-predicate-reference}

## 常规 {#general}

* [根](#root)
* [组](#group)
* [orderby](#orderby)

## 谓词 {#predicates}

* [布尔属性](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [达朗日](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [排除路径](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [全文](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [语言](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [mainasset](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [memberOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [诺登姆](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [路径](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [属性](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [牧场属性](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [相对变化](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [savedquery](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [相似](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [标签](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [tagid](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [标语](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [类型](/help/sites-developing/querybuilder-predicate-reference.md#type)

### 布尔属性 {#boolproperty}

在JCR布尔属性上匹配。 仅接受值“ `true`”和“ `false`”。 对于“ ” `false`，如果属性具有值“ ”或 `false`其根本不存在，则匹配。 这对于检查仅在启用时设置的布尔标志非常有用。

继承的“ `operation`”参数没有含义。

支持facet提取。 将为每个或每个值 `true` 提供 `false` 存储段，但仅为现有属性提供存储段。

#### 属性 {#properties}

* **boolproperty**&#x200B;相对属性路径，例如 
`myFeatureEnabled` 或 `jcr:content/myFeatureEnabled`

* **要**&#x200B;检查属性的值， &quot; 
`true`&quot; 或 &quot; `false`&quot;

### contentfragment {#contentfragment}

将结果限制为内容片段。

不支持筛选。

不支持facet提取。

#### 属性 {#properties-1}

* **contentfragment**&#x200B;它可与任何值一起使用以检查内容片段。

### dateComparison {#datecomparison}

将两个JCR DATE属性相互比较。 可以测试它们是否相等、不等、是否大于或大于等。

这是只筛选谓词，无法利用搜索索引。

#### 属性 {#properties-2}

* **property1**

   第一个日期属性的路径

* **property2**

   路径到第二个日期属性

* **操作**

   “ `=`”表示精确匹配，“ `!=`”表示不等式比较，“ ”表示属性1大于属性2,“ `>``>=`”表示属性1大于或等于属性2。 默认值为 &quot; `=`&quot;.

### 达朗日 {#daterange}

将JCR DATE属性与日期／时间间隔匹配。 它使用ISO8601\
日期和时间()的格 `YYYY-MM-DDTHH:mm:ss.SSSZ`式，并允许部分表示，如 `YYYY-MM-DD`。 或者，时间戳可以以UTC时区（UNIX时间格式）自1970年以来的毫秒数提供。

您可以在两个时间戳之间查找任何内容，即任何比给定日期更新或更旧的内容，也可以在包含时间间隔和打开时间间隔之间进行选择。

支持facet提取。 将提供“今天”、“本周”、“本月”、“过去3个月”、“今年”、“去年”和“比去年更早”的桶。

不支持筛选。

#### 属性 {#properties-3}

* **属性**

   属性的相 `DATE` 对路径，例如 `jcr:lastModified`

* **lowerBound**

   用于检查属性(例如， `2014-10-01`

* **lowerOperation**

   “ `>`”（新）或“ `>=`”（新）适用于 `lowerBound`。 默认为 &quot; `>`&quot;.

* **上界**

   上界检查属性，例如 `2014-10-01T12:15:00`

* **upperOperation**

   “ `<`”（旧）或“ `<=`”（旧）适用于 `upperBound`。 默认为 &quot; `<`&quot;.

* **时区**

   未作为ISO-8601日期字符串给定时使用的时区ID。 默认值是系统的默认时区。

### 排除路径 {#excludepaths}

从其路径与常规表达式匹配的结果中排除节点。

这是只筛选谓词，无法利用搜索索引。

不支持facet提取。

#### 属性 {#properties-4}

* **排除路径**

   与结果路径匹配的常规表达式，从结果中排除匹配的路径。

### fulltext {#fulltext}

在全文索引中搜索词。

不支持筛选。

不支持facet提取。

#### 属性 {#properties-5}

* **全文**

   全文搜索词

* **relPath**

   要在属性或子节点中搜索的相对路径。 此属性是可选的。

### 组 {#group}

允许构建嵌套条件。 组可以包含嵌套组。 querybuilder查询中的所有内容都隐式地位于根组中，根组 `p.or` 也可 `p.not` 以有和参数。

将两个属性中的任何一个与值匹配的示例：

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

这从概念上 `(1_property` 讲或 `2_property)`说。

嵌套用户组的示例：

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

这将在页面中或资&#x200B;**产**&#x200B;中搜索 `/content/geometrixx/en` 术语“管理” `/content/dam/geometrixx`。

从概念上讲 `fulltext AND ( (path AND type) OR (path AND type) )`。 请注意，此类OR连接需要良好的性能索引。

#### 属性 {#properties-6}

* **p.or**

   如果设置为“ `true`”，则组中只有一个谓词必须匹配。 此默认值为“ `false`”，表示所有内容必须匹配

* **p.not**

   如果设置为“ `true`”，则它会否定该组(默认为“ `false`”)

* **&lt;谓词>**

   添加嵌套谓词

* **N_&lt;谓词>**

   添加多个同时嵌套的谓词，如 `1_property, 2_property, ...`

### hasPermission {#haspermission}

将结果限制为当前会话具有指定JCR权限 [的项目。](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

这是只筛选谓词，无法利用搜索索引。 它不支持facet提取。

#### 属性 {#properties-7}

* **hasPermission**

   当前用户会话必须全部具有的以逗号分隔的JCR权限，该权限用于相关节点； 例如 `jcr:write`, `jcr:modifyAccessControl`

### 语言 {#language}

查找特定语言的CQ页面。 这会查看页面语言属性和页面路径，它们通常包括顶级站点结构中的语言或区域设置。

这是只筛选谓词，无法利用搜索索引。

支持facet提取。 将为每个唯一语言代码提供存储段。

#### 属性 {#properties-8}

* **语言**

   ISO语言代码，例如“ `de`”

### mainasset {#mainasset}

检查节点是DAM主资产还是子资产。 这基本上是“子资产”节点中不存在的每个节点。 请注意，这不会检查节点 `dam:Asset` 类型。 要使用此谓词，只需设 `mainasset=true`置“”或“ `mainasset=false`”，就没有其他属性。

这是只筛选谓词，无法利用搜索索引。

支持facet提取。 将为主资产和子资产提供2个存储段。

#### 属性 {#properties-9}

* **mainasset**

   布尔值，主 `true`资产为“”，子资 `false`产为“”

### memberOf {#memberof}

查找属于特定sling资源集合 [的项目](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/resource/collection/ResourceCollection.html)。

这是只筛选谓词，无法利用搜索索引。 不支持facet提取。

#### 属性 {#properties-10}

* **memberOf**

   Sling资源收集路径

### 诺登姆 {#nodename}

在JCR节点名称上匹配。

支持facet提取。 将为每个唯一节点名称（文件名）提供存储段。

#### 属性 {#properties-11}

* **诺登姆**

   允许通配符的节点名称模式： `*` =任何或无字符， `?` =任何字符， `[abc]` =只有括号中的字符

### notexpired {#notexpired}

通过检查JCR DATE属性是否大于或等于当前服务器时间来匹配项。 它可用于检查“”类日 `expiresAt`期属性，并仅限于尚未过期()或已过 `notexpired=true`期()的日 `notexpired=false`期属性。

不支持筛选。

支持facet提取，方法与更改谓词相同。

#### 属性 {#properties-12}

* **notexpired**

   布尔值， &quot; `true`&quot;表示未过期（将来日期或等于日期）, &quot; `false`&quot;表示过期（过去日期）（必需）

* **属性**

   要检查的属 `DATE` 性的相对路径（必需）

### orderby {#orderby}

允许对结果进行排序。 如果需要按多个属性排序，则需要使用数字前缀多次添加此谓词， `1_orderby=first`如 `2_oderby=second`。

#### 属性 {#properties-13}

* **orderby**

   JCR属性名称由前导@表示， `@jcr:lastModified` 例如 `@jcr:content/jcr:title`或查询中的其他谓词， `2_property`例如，要对其排序

* **排序**

   排序方向，“” `desc`表示降序，“” `asc`表示升序（默认）

* **案例**

   如果设置为“ `ignore`”，则排序将不区分大小写，即“a”在“B”之前； 如果为空或未排除，则排序区分大小写，即“B”在“a”之前

### 路径 {#path}

在给定路径内搜索。

不支持facet提取。

#### 属性 {#properties-14}

* **路径**

   路径模式； 根据具体情况，整个子树将进行匹配(如附加到 `//*` xpath中，但请注意，这不包括基本路径)（exact=false，默认值），或仅进行精确的路径匹配，其中可以包括通配符( `*`); 如果设置了“自”，则将搜索包括基节点的整个子树

* **精确**

   如 `exact` 果为true/on，则精确路径必须匹配，但它可以包含简单通配符( `*`)，该通配符与名称匹配，但不 `/`是“”; 如果为false（默认），则包括所有后代（可选）

* **扁平**

   仅搜索直接子项(如在xpath `/*`中附加“ ”)(仅在“ ”不 `exact`是true时使用，可选)

* **self**

   搜索子树，但包括作为路径给定的基节点（无通配符）

### 属性 {#property}

与JCR属性及其值匹配。

支持facet提取。 将为结果中的每个唯一属性值提供时段。

#### 属性 {#properties-15}

* **属性**

   属性相对路径，例如 `jcr:title`

* **value**

   值：检查属性； 跟在JCR属性类型到字符串转换之后

* **N_value**

   使 `1_value`用、 `2_value`、...检查多个值(默认 `OR` 与if和= `AND` true结合)（从5.3开始）

* **和**

   设置为true，将多个值()与 `N_value`AND（自5.3开始）组合

* **操作**

   “ `equals`”表示精确匹配（默认）,“ `unequals`”表示不相等比较，“ `like`”表示使用xpath函数（可选）,“ `jcr:like``not`”表示不匹配(例如 xpath中 `not(@prop)`的“ ”、值参数将被忽略)或“ `exists`”是否存在检查(值可以为true —— 属性必须存在，默认值——或false —— 与“ `not`”相同)

* **深度**

   属性／相对路径可存在的通配符级别数(例 `property=size depth=2` 如，将检查节点／大小、节点/&amp;ast;/size和node/&amp;ast;/&amp;ast;/size)

### 牧场属性 {#rangeproperty}

将JCR属性与间隔匹配。 这适用于线性类型（如、和） `LONG`的 `DOUBLE` 属性 `DECIMAL`。 有关 `DATE` 信息，请参阅已优化日期格式输入的日期谓词。

您可以定义下界和上界，也可以只定义其中一个。 操作(例如 “小于”或“小于或等于”)也可单独指定用于下界和上界。

不支持facet提取。

#### 属性 {#properties-16}

* **属性**

   属性相对路径

* **lowerBound**

   下界检查属性

* **lowerOperation**

   “ `>`”（默认）或“ `>=`”应用于 `lowerValue`

* **上界**

   上界检查属性

* **upperOperation**

   “ `<`”（默认）或“ `<=`”应用于 `lowerValue`

* **小数**

   “ `true`”（如果选中的属性类型为Decimal）

### 相对变化 {#relativedaterange}

使用 `JCR DATE` 相对于当前服务器时间的时间偏移，将属性与日期／时间间隔匹配。 您可以指 `lowerBound` 定并 `upperBound` 使用毫秒值或bugzilla语法(一秒、两分钟、三 `1s 2m 3h 4d 5w 6M 7y` 小时、四天、五周、六个月、七年)。 前缀为“ `-`”，表示当前时间之前的负偏移。 如果仅指 `lowerBound` 定或 `upperBound`，则另一个将默认为0，表示当前时间。

例如：

* `upperBound=1h` (并且不 `lowerBound`会)将在下一小时选择任何内容
* `lowerBound=-1d` (并且不 `upperBound`会)在过去24小时内选择任何内容
* `lowerBound=-6M` 选择 `upperBound=-3M` 任何6个月到3个月的
* `lowerBound=-1500` 并 `upperBound=5500` 选择过去1500毫秒和将来5500毫秒之间的任何内容
* `lowerBound=1d` 然后 `upperBound=2d` 在后天选择任何东西

请注意，它不需要花上几年时间考虑，所有月份都是30天。

不支持筛选。

支持facet提取，方法与更改谓词相同。

#### 属性 {#properties-17}

* **上界**

   相对于当前服务器时间 `1s 2m 3h 4d 5w 6M 7y` （一秒、二分钟、三小时、四天、五周、六个月、七年）的上限日期，使用“-”表示负偏移

* **lowerBound**

   相对于当前服务器时间 `1s 2m 3h 4d 5w 6M 7y` （一秒、两分钟、三小时、四天、五周、六个月、七年），较低日期的界限以毫秒为单位，使用“-”表示负偏移

### root {#root}

根谓词组。 支持组的所有功能并允许设置全局查询参数。

名称“root”在查询中从不使用，它是隐式的。

#### 属性 {#properties-18}

* **p.offset**

   表示结果页面开始的数字，即要跳过的项目数

* **p.limit**

   指示页面大小的数字

* **p.guessTotal**

   推荐： 避免计算全部结果总和，代价昂贵； 一个数字，表示最大总数最多可计算（例如1000，该数字为用户提供对粗细大小和精确数字的足够反馈以获得较小结果），或者“ `true`”只计算最多必要 `p.offset` + `p.limit`

* **p.摘录**

   如果设置为“”, `true`则在结果中包含全文摘录

* **p.hits**

   （仅用于JSON servlet）选择将点击编写为JSON的方式，使用这些标准点击（可通过ResultHitWriter服务扩展）:

   * **简单**:

      最小项 `path`, `title`如 `lastmodified`、 `excerpt` （如果已设置）

   * **全部**:

      sling JSON呈现节点，并 `jcr:path` 指示点击的路径： 默认情况下，仅列表节点的直接属性，包含一个更深的树， `p.nodedepth=N`其中0表示整个无限子树； 添 `p.acls=true` 加以包含当前会话在给定结果项上的JCR权限(映射： `create` = `add_node`, `modify` = `set_property`, `delete` = `remove`)

   * **选定属性**:

      仅在中指定 `p.properties`的属性，即相对路径的空格分隔（在URL中使用“+”）列表; 如果相对路径深度大于1，则这些路径将表示为子对象； 特殊的jcr:path属性包括点击的路径

### savedquery {#savedquery}

作为子组谓词，将保留的querybuilder查询的所有谓词包含到当前查询中。

请注意，这不会执行额外查询，而会扩展当前查询。

查询可以使用以编程方式持 `QueryBuilder#storeQuery()`久。 该格式可以是多行字符串属性，也可以 `nt:file` 是包含查询的节点，该节点采用Java属性格式。

不支持已保存提取的谓词的facet查询。

#### 属性 {#properties-19}

* **savedquery**

   保存查询的路径(字符串属性或 `nt:file` 节点)

### 相似 {#similar}

使用JCR XPath的相似性搜索 `rep:similar()`。

不支持筛选。 不支持facet提取。

#### 属性 {#properties-20}

* **类**&#x200B;似绝对路径，指向要查找相似节点的节点

* **到**&#x200B;子节点或子节点的本地相对路径 
`.` 对于当前节点(可选，默认为“ `.`”)

### tag {#tag}

通过指定标记标题路径搜索用一个或多个标记标记的内容。

支持facet提取。 将使用每个唯一标记的当前标记标题路径为每个唯一标记提供存储段。

#### 属性 {#properties-21}

* **标签**

   标记要查找的标题路径，例如“资产属性： 方向／横向”

* **N_value**

   使 `1_value`用 `2_value`、、...检查多个标记(默认 `OR` 与if `AND` and=true结合)（自5.6起）

* **属性**

   要查看的属性（或属性的相对路径）(默认 `cq:tags`为“”)

### tagid {#tagid}

通过指定标记ID搜索用一个或多个标记标记的内容。

支持facet提取。 将使用每个唯一标记的当前标记ID为其提供桶。

#### 属性 {#properties-22}

* **tagid**

   要查找的标记id，例如“ `properties:orientation/landscape`”

* **N_value**

   使 `1_value`用 `2_value`、、...检查多个标签(默认 `OR` 与if和 `AND` =true结合)（自5.6起）

* **属性**

   要查看的属性（或属性的相对路径）(默认 `cq:tags`为“”)

### tagsearch {#tagsearch}

通过指定关键字搜索用一个或多个标记标记的内容。 这将首先搜索标题中包含这些关键字的标记，然后将结果限制为仅包含这些关键字的标记。

不支持facet提取。

#### 属性 {#Properties-1}

* **标语**

   用于在标记标题中搜索的关键字

* **属性**

   要查看的属性（或属性的相对路径）(默认 `cq:tags`为“”)

* **朗**

   仅搜索特定的本地化标记标题(例如， &quot; `de`&quot;)

* **全部**

   (bool)搜索整个标记全文，即所有标题、描述等。 (优先于“l” `ang`)

### 类型 {#type}

将结果限制为特定的JCR节点类型，主节点类型或混合类型。 此外，还将查找该节点类型的子类型。 请注意，存储库搜索索引需要涵盖节点类型，以便有效执行。

支持facet提取。 将为结果中的每个唯一类型提供时段。

#### 属性 {#Properties-2}

* **类型**

   要搜索的节点类型或混合名称，例如 `cq:Page`