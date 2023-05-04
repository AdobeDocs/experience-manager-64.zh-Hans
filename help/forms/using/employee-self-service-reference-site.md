---
title: 员工自助参考站点演练
seo-title: Employee self-service
description: AEM Forms参考网站展示了组织如何利用AEM Forms功能来实施员工招聘和自助服务工作流。
seo-description: AEM Forms reference site showcases how organizations can leverage AEM Forms features to implement employee recruitment and self-service workflows.
uuid: ecc98e0d-c964-44dc-b219-9ebe92632d22
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d2695f71-5126-477c-ae6b-a964fb55728b
exl-id: 7fbdd976-5a70-4af4-b449-7c2d6bcfd915
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1659'
ht-degree: 0%

---

# 员工自助参考站点演练 {#employee-self-service-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 先决条件 {#prerequisite}

按照 [设置和配置AEM Forms引用站点](/help/forms/using/setup-reference-sites.md).

## 概述 {#overview}

员工自助服务系统通常托管在公司的内联网上，它使员工能够访问从其办公桌上可以使用的大量信息和服务。 它赋予员工权力并赋予员工完全控制权，以执行访问其雇佣详情、申请休假和提交费用报告等操作。 另一方面，它有助于组织提高流程效率并降低成本，同时让员工随时了解情况并参与其中。

员工自助服务参考网站展示了如何利用AEM Forms在您的组织中实施员工自助服务系统。

>[!NOTE]
>
>员工自助服务用例可在We.Finance和We.Gov参考网站中使用。 演练中使用的示例、图像和描述使用We.Finance参考网站。 但是，您也可以使用We.Gov运行这些用例和查看工件。 为此，必须将 **we-finance** with **we-gov** 在提到的URL中。

## 利益冲突问卷演练 {#conflict-of-interest-questionnaire-walkthrough}

组织会不时要求员工提交利益冲突调查表，以确定员工可能与其组织发生冲突的外部活动或个人关系。

Sarah组织的合规部门要求员工提交利益冲突调查问卷。

### Sarah提交利益冲突调查表 {#sarah-submits-the-conflict-of-interest-questionnaire}

Sarah转到其组织的门户，登录并单击“员工”以访问员工仪表板。 她在员工仪表板和点击中找到利益冲突调查表 **[!UICONTROL 应用]**.

![we-finance-home](assets/we-finance-home.png)
**图：** *组织门户*

![employee-dashboard](assets/employee-dashboard.png)
**图：** *员工仪表板*

Sarah使用“下一步”按钮浏览表单，并阅读“简介”和“定义”部分。 她回答了“问题”部分中的问题。 最后，她签了字并提交了调查表。

组织门户和调查表具有响应性，且对移动设备友好。 以下工作流展示了Sarah如何在其移动设备上浏览并提交调查表。

![移动设备冲突形式](assets/conflict-form-on-mobile.png)

**工作原理**

组织门户和员工仪表板是AEM Sites页面。 功能板列出了若干自助选项，如利益冲突调查表。 “应用”按钮链接到自适应表单。

自适应表单会根据“问题”选项卡中提供的答案，使用规则来显示和隐藏信息。 此外，表单还使用涂写组件在“声明”选项卡中进行签名。 查看自适应表单(位于 `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/conflict-of-interest.html`.

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` 使用登录 `srose/srose` 作为Sarah的用户名/密码。 单击 **[!UICONTROL 员工]** 访问功能板，然后单击 **[!UICONTROL 应用]** 利益冲突调查表。 审查并提交调查表。

### Gloria审查并核准利益冲突问卷提交 {#gloria-reviews-and-approves-the-conflict-of-interest-questionnaire-submission}

Sarah提交的利益冲突调查表被指派给Gloria Rios审查。 Gloria在组织中担任合规官。 Gloria登录到其AEM收件箱并检查分配给她的任务。 她核准了莎拉提交的调查表，并完成了任务。

![冲突收件箱](assets/conflict-inbox.png)
**图：** *格洛丽亚的收件箱*

![冲突批准](assets/conflict-approved.png)
**图：** *打开任务*

**工作原理**

利益冲突调查表中的提交操作会触发一个工作流，该工作流会在Gloria的收件箱中创建一个任务以供审批。 查看Forms Workflow: `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-conflict-of-interest.html`

![employee-self-service-reference-site](assets/employee-self-service-reference-site.png)

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` 使用登录 `grios/password` 作为Gloria Rios的用户名/密码。 打开为利益冲突调查表创建的任务并批准它。

## 公司卡应用程序演练 {#corporate-card-application-walkthrough}

莎拉出差很多，她需要公司信用卡来支付手续费。 她通过公司的员工门户申请公司卡。

### Sarah提交公司卡申请 {#sarah-submits-the-corporate-card-application}

Sarah转到组织的门户、登录并单击 **[!UICONTROL 员工]** 以访问员工仪表板。 她在员工仪表板上找到公司卡应用程序并单击 **[!UICONTROL 应用]**.

![we-finance-home-1](assets/we-finance-home-1.png)
**图：** *组织门户*

![employee-dashboard-1](assets/employee-dashboard-1.png)
**图：** *员工仪表板*

她点击 **[!UICONTROL 应用]** 在公司卡应用程序上。 将打开单页应用程序。 她会填满所有细节和点击 **[!UICONTROL 应用]** 提交申请。

![卡形式](assets/card-form.png)

**工作原理**

组织门户和员工仪表板是AEM Sites页面。 功能板列出了一些自助服务选项，如公司卡应用程序。 应用程序上的“应用”按钮已链接到自适应表单。

公司卡应用程序的自适应表单是一个简单、一页的响应式自适应表单。 它使用基本的自适应表单组件，如文本、电话、数字框和数字步进器。 查看自适应表单：\
`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/corporate-card.html`。

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` 使用登录 `srose/srose` 作为Sarah的用户名/密码。 单击 **[!UICONTROL 员工]** 访问功能板，然后单击 **[!UICONTROL 应用]** 在公司卡应用程序上。 填写详细信息并提交申请。

### Gloria审核并批准公司卡申请 {#gloria-reviews-and-approves-the-corporate-card-application}

Sarah提交的公司卡申请已分配给Gloria Rios进行审核。 Gloria登录到其AEM收件箱并检查分配给她的任务。 她批准了Sarah提交的申请并完成了任务。

![公司卡收件箱](assets/corporate-card-inbox.png)
**图：** *格洛丽亚的收件箱*

![公司卡批准](assets/corporate-card-approved.png)
**图：** *打开任务*

**工作原理**

企业卡应用程序中的提交工作流会触发Forms工作流，该工作流会在Gloria的收件箱中创建一个任务以供审批。 查看Forms Workflow: `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-corporate-card.html`

![企业卡 — 工作流模型](assets/corporate-card-workflow-model.png)

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` 使用登录 `grios/password` 作为Gloria Rios的用户名/密码。 打开为公司卡应用程序创建的任务并批准它。

## 费用报表提交演练 {#expense-report-submission-walkthrough}

由于莎拉在出差期间花费了很多钱，她需要提交费用报表以获得批准。 她的组织中的自助选项允许她在线提交费用报表。

### Sarah提交费用报表申请 {#sarah-submits-the-expense-report-application}

Sarah转到组织的门户、登录并单击 **[!UICONTROL 员工]** 以访问员工仪表板。 她在员工仪表板上查找“费用报表”应用程序并单击 **[!UICONTROL 应用]**.

![we-finance-home-2](assets/we-finance-home-2.png)
**图：** *组织门户*

![employee-dashboard-2](assets/employee-dashboard-2.png)
**图：** *员工仪表板*

她点击 **[!UICONTROL 应用]** （在费用报表应用程序中）。 此时将打开一个应用程序表单，其中包含两个选项卡：“报表名称”和“报表详细信息”。 的 **+** 图标，以便她在一个报表中添加超过支出的报表。

组织门户和应用程序具有响应性，且对移动设备友好。 以下工作流显示Sarah如何浏览并提交其移动设备上的费用报表。

![移动设备上的费用报告](assets/expense-report-on-mobile.png)

**工作原理**

组织门户和员工仪表板是AEM Sites页面。 功能板列出了一些自助选项，如“费用报表”应用程序。 “应用”按钮链接到自适应表单。

自适应表单中的报表名称和报表详细信息选项卡是面板组件。 “报表详细信息”面板包含“费用”面板。 它是一个可重复的面板，允许在报表中添加多项支出。 查看自适应表单及其配置，网址为 `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/expense-report.html`.

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` 使用登录 `srose/srose` 作为Sarah的用户名/密码。 单击 **[!UICONTROL 员工]** 访问功能板，然后单击 **[!UICONTROL 应用]** （在费用报表应用程序中）。 填写详细信息并提交申请。

### Gloria审核并批准费用报表 {#gloria-reviews-and-approves-the-expense-report}

Sarah提交的费用报表被分配给Gloria Rios进行审核。 Gloria登录到其AEM收件箱并检查分配给她的任务。 她批准了Sarah提交的申请并完成了任务。

![expense-report-inbox](assets/expense-report-inbox.png)
**图：** *格洛丽亚的收件箱*

![expense-report-approved](assets/expense-report-approved.png)
**图：** *打开任务*

**工作原理**

费用报表应用程序中的提交工作流会触发Forms工作流，该工作流会在Gloria的收件箱中创建任务以供审批。 查看Forms Workflow: `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-expense-report-workflow.html`

![企业卡费用 — 报表 — 工作流 — 模型](assets/corporate-card-expense-report-workflow-model.png)

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` 使用登录 `grios/password` 作为Gloria Rios的用户名/密码。 打开为费用报表应用程序创建的任务并审批它。

## 离开应用程序演练 {#leave-application-walkthrough}

莎拉正计划下月度家庭假，想申请一周的休假。

### Sarah提交休假申请 {#sarah-submits-the-leave-application}

Sarah转到组织的门户、登录并单击 **[!UICONTROL 员工]** 以访问员工仪表板。 她在员工仪表板上找到离职申请并单击 **[!UICONTROL 应用]**.

![we-finance-home-3](assets/we-finance-home-3.png)
**图：** *组织门户*

![employee-dashboard-3](assets/employee-dashboard-3.png)
**图：** *员工仪表板*

随即会打开休假申请，其中Sarah的姓名和员工ID已预填入表单。 它还显示她的休假平衡和历史。 她填写了休假细节，并提交了批准申请。

组织门户和应用程序具有响应性，且对移动设备友好。 以下工作流展示了Sarah如何在其移动设备上浏览并提交应用程序。

![移动设备上的表单](assets/leave-form-on-mobile.png)

**工作原理**

组织门户和员工仪表板是AEM Sites页面。 功能板列出了若干自助选项，如离职申请。 “应用”按钮链接到自适应表单。

离职申请的自适应表单基于员工离职表单数据模型。 在“剩余余额”部分中，使用 `getLeavesOf` 表单数据模型服务。 “开始日期”和“结束日期”字段使用规则来验证日期值是否等于当前日期或晚于当前日期。 休假持续时间使用 `calcBusinessDays` 函数。

您可以在以下位置查看自适应表单和表单数据模型：

`https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/employee/self-service/leave-application.html`

`https://[authorHost]:[authorPort]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/db`

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/self-service-forms.html` 使用登录 `srose/srose` 作为Sarah的用户名/密码。 单击 **[!UICONTROL 员工]** 访问功能板，然后单击 **[!UICONTROL 应用]** 在离开申请时。 填写详细信息并提交申请。

### 格洛丽亚审查并批准休假申请 {#gloria-reviews-and-approves-the-leave-application}

Sarah提交的休假申请被指派给Gloria Rios审查。 Gloria登录到其AEM收件箱并检查分配给她的任务。 她批准了Sarah提交的申请并完成了任务。

![leave-inbox](assets/leave-inbox.png)
**图：** *格洛丽亚的收件箱*

![休假批准](assets/leave-approved.png)
**图：** *打开任务*

**工作原理**

离开应用程序中的提交工作流会触发Forms工作流，该工作流会在Gloria的收件箱中创建一个任务以供审批。 查看Forms Workflow: `https://[authorHost]:[authorPort]/editor.html/conf/global/settings/workflow/models/we-finance/employee/self-service/we-finance-employee-leave-application.html`

![企业信息卡 — 休假 — 应用 — 工作流 — 模型](assets/corporate-card-leave-application-workflow-model.png)

**亲眼看看**

转到 `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html` 使用登录 `grios/password` 作为Gloria Rios的用户名/密码。 打开为离开应用程序创建的任务并批准该任务。
