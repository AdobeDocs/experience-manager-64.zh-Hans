---
title: 视图和了解AEM Forms分析报告
seo-title: 视图和了解AEM Forms分析报告
description: AEM Forms与Adobe Analytics集成，为您提供有关已发布自适应表单的摘要和详细分析。
seo-description: AEM Forms与Adobe Analytics集成，为您提供有关已发布自适应表单的摘要和详细分析。
uuid: 193f472d-4aa3-4c31-b3c7-b5a2957dfb3d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: a9045816-cae7-42cf-a734-6c3a25d0f522
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 0%

---


# 视图和了解AEM Forms分析报告 {#view-and-understand-aem-forms-analytics-reports}

Adobe Experience Manager Forms与Adobe Analytics集成，使您能够捕获和跟踪已发布表单和文档的绩效指标。 分析这些指标的目的是根据使表单或文档更可用所需的更改数据做出明智决策。

## 设置分析 {#setting-up-analytics}

AEM Forms的分析功能可作为AEM Forms加载项包的一部分提供。 有关安装加载项包的信息，请参阅安 [装和配置AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md)。

除了附加包，您还需要一个Adobe Analytics帐户。 有关该解决方案的信息，请参 [阅Adobe Analytics](https://www.adobe.com/solutions/digital-analytics.html)。

获得AEM Forms加载项包和Adobe Analytics帐户后，请将Adobe Analytics帐户与AEM Forms集成，并按照配置分析和报告中的说明启 [用表单或文档跟踪](/help/forms/using/configure-analytics-forms-documents.md)。

## 如何记录用户交互信息 {#how-user-interaction-information-is-recorded}

当用户与表单交互时，会记录交互并将其发送到Analytics服务器。 以下列表指示服务器调用各种用户活动:

* 每次现场访问2次
* 1个小组访问
* 保存1
* 提交2
* 2，节省
* 1个帮助
* 每个验证错误为1
* 表单演绎版为1 + 1（默认面板为1），默认第1次现场访问为1
* 2表单放弃

>[!NOTE]
>
>此列表并非完全。

## 查看分析报告 {#summary-report}

执行以下步骤来视图分析报告：

1. 登录AEM门户网站： `https://[hostname]:[port]`
1. 单击 **Forms>Forms和文档**。

1. 选择要视图分析报告的表单。
1. 选择 **更多>分析报告**。

![分析报告](assets/analyticsreport.png)

**A.** Analytics报告命令

AEM Forms显示表单中每个面板的分析报告，如下所示。

![自适应表单的摘要报告](assets/analyticsdashboard_callout.png)

**A.** B. **表单级摘要** C.D. **访客的面板级摘要** D.D **.的面板级摘要********** -访客的过滤器E.OS —— 的过滤器转换-访客的过滤器F.滤镜语言-

默认情况下，将显示最近七天的分析报告。 您可以视图最近15天、上个月等的报表，或指定日期范围。

>[!NOTE]
>
>过去7天和过去15天等选项不包括生成分析报告的当天的数据。 要包含当天的数据，您需要指定包括当天在内的日期范围，然后运行报告。

![日期范围](assets/date-range.png)

## 自适应和HTML5表单的转换图 {#conversions-graph-for-adaptive-and-html-forms}

通过表单级转换图，您可以深入了解表单在以下关键绩效指标(KPI)上的表现：

* **演绎版**: 表单的打开次数
* **访客**: 表单的访客数
* **提交**: 提交表单的次数

![转换图](assets/conversion-graph.png)

## 自适应和HTML5表单的分析报告 {#analytics-report-for-adaptive-and-html-forms}

通过表单级摘要部分，您可以深入了解表单在以下关键绩效指标(KPI)上的表现：

* **平均填充时间**: 填写表单的平均时间。 当用户在表单上花费时间但未提交时，该时间不会包括在此计算中。
* **演绎版**: 表单的呈现或打开次数

* **草稿**: 表单已保存为草稿的次数
* **提交**: 提交表单的次数
* **中止**: 用户开始填写表单后离开而不填写表单的次数
* **唯一访客**: 表单由唯一访客呈现的次数。 有关独特访客的更多信息，请 [参阅独特访客、访问和客户行为](https://helpx.adobe.com/analytics/kb/unique-visitors-visitor-behavior.html)。

![扩展的表单级摘要分析报告](assets/analytics-report.png)

## Panel report {#bottom-summary-report}

面板级摘要部分在表单中提供了有关每个面板的以下信息：

* **平均填充时间**: 在面板上花费的平均时间，无论表单是否提交

* **遇到错误**: 用户在面板中的字段上遇到的平均错误数。 “遇到的错误”是按字段中的总错误除以表单的演绎版数量得出的。

* **访问的帮助**: 用户访问面板中字段的上下文帮助的平均次数。 “帮助访问”是按字段的“帮助”访问总次数除以表单的演绎版数得出的。

### 详细面板报告 {#detailed-panel-report}

您还可以通过在面板报告中单击面板名称来视图每个面板的详细信息。

![详细面板报告](assets/panel-report-detailed.png)

详细报告显示面板中所有字段的值。

面板报告有三个选项卡：

* **时间报告** （默认）: 显示填写面板中每个字段所花的时间（以秒为单位）
* **错误报告**: 显示填写字段时用户遇到的错误数
* **帮助报告**: 访问特定字段的帮助次数

如果多个面板可用，则可以在这些面板之间导航。

### 过滤器: 浏览器、操作系统和语言 {#filters-browser-os-and-language}

“浏览器分发”、“操作系统分发”和“语言分发”表按表单用户的浏览器、操作系统和语言显示再现、访客和提交。 默认情况下，这些表最多显示五个条目。 单击“显示更多”可显示更多条目，单击“显示更少”可返回到五个或更少的常规条目。

要进一步筛选分析数据，您可以单击任意表中的条目。 例如，如果单击“浏览器分发”表中的Google Chrome，则报表将再次呈现，并显示与Google Chrome浏览器相关的数据，如下所示：

![应用于Analytics报告的筛选器- Google Chrome ](assets/filter.png)

如果在应用过滤器后视图面板报告，面板报告数据也会根据应用的过滤器显示。

应用过滤器后：

* 分发表变为只读，因为一次只能应用一个筛选器。
* 应用的过滤器表消失。
* 您可以单击“关闭”按钮（在下面突出显示）以删除已应用的筛选器。

![关闭按钮以删除已应用的筛选器](assets/close-filter.png)

## A/B测试 {#a-b-testing}

如果启用了A/B测试并为表单进行了设置，则报表页面中会显示一个下拉框，您可以使用它显示A/B测试报表。 A/B测试报告显示您已设置的两个版本的表单的比较性能。

有关A/B测试的详细信息，请参 [阅创建和管理自适应表单的A/B测试](/help/forms/using/ab-testing-adaptive-forms.md)。
