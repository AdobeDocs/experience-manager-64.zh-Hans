---
title: We.Gov参考站点演练
seo-title: We.Gov参考站点演练
description: '请访问We.Gov参考网站演练，了解AEM Forms如何帮助政府管理个人信息。 '
seo-description: '请访问We.Gov参考网站演练，了解AEM Forms如何帮助政府管理个人信息。 '
uuid: 348f9067-28b5-47ed-8e83-0dbadeff0854
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 25a6d702-9995-4c63-99d8-3e5d710bb0c4
translation-type: tm+mt
source-git-commit: 7e58d1d861f832d073fb178868804995ee8d855b
workflow-type: tm+mt
source-wordcount: '2737'
ht-degree: 0%

---


# We.Gov参考站点演练 {#we-gov-reference-site-walkthrough}

## 先决条件 {#pre-requisite}

按照设置和配置AEM Forms参考站点中的 [说明设置您的We.Gov参考站点](/help/forms/using/setup-reference-sites.md)。

## 参考站点方案 {#reference-site-scenario}

We.Gov是一个州立组织，允许养父母在收养孩子时报到抚养孩子。 该站点管理以下内容：

* 申请人、养父母的资格
* 申请人的个人和专业详细信息（如果申请人有资格获得儿童支持）
* 被收养儿童的个人详情

   申请人可以提供多个子项的详细信息
* 申请人可在其中获得子女支持福利的银行帐户详细信息
* 收回应用程序费
* 应用程序评估
* 申请的批准
* 与申请人的自动通信

申请提交并支付费用后，申请人将收到来自组织的一封电子邮件，其中附有提交申请的确认书。

We.Gov组织收到该应用程序。 组织会对申请进行评估，并批准正版申请。

申请获得批准后，申请人会从We.Gov网站收到一封电子邮件。 电 **子邮件中** 的视图文档选项链接到具有申请人注册详细信息的文档。

以下信息图显示了We.Gov参考站点方案的分步工作流程。

![workflow_aem_gov_2](assets/workflow_aem_gov_2.png)

此方案涉及以下角色：

* 萨拉·罗斯，要求抚养孩子的养父母
* 乔，收养的孩子
* We.Gov审批部门主管Gloria Rios
* 负责应用评估的现场代理Conard Simms

## Sarah发起资格检查 {#sarah-initiates-her-eligibility-check}

申请人可以检查申请儿童支持福利的资格。 该站点允许用户回答问题，以便确定他们的应用程序是否有资格享受优惠。 养父母莎拉是申请者。 资格表是We.Gov站点的儿童支持申请服务的一部分。 要检查她的资格，Sarah单击 **[!UICONTROL We.Gov网]** 站上的“儿童支持”。 在“子级支持”页面中，Sarah单击“ **[!UICONTROL 检查您的资格]**”。

除了上述方法之外，Sarah还可以单击主 **[!UICONTROL 页上的]** “入门”。 Sarah会导航到“所有应用程序”页面，在该页面上，她可以单击“Application for Child Support Services”( **[!UICONTROL 子级支持服务应用程序)下的“Apply]**”（应用）。 然后，Sarah将进入资格检查。

在“检查子级支持资格”页面中，Sarah会被询问一组问题，以确定她是否有资格享受子级支持福利。 通过这些问题，她被问到：

* 如果她是孩子的监护人
* 如果她和孩子生活在GX状态
* 儿童的年龄组和儿童的教育。

Sarah回答这些问题，并验证其资格。 她的答案决定她是否有资格获得儿童抚养权。

Sarah被告知她有资格获得儿童支持，申请费为25美元。

### 工作方式 {#how-it-works}

Sarah的资格通过使用规则编辑器创建的资格障碍进行验证。 规则编辑器允许您指定在申请人填写申请表之前满足的条件。 当申请人Sarah符合所有资格条件时，她将登录申请表。

资格检查是子支持应用程序自适应表单的一部分。 规则在以下情况下验证资格：

* 申请人是监护人的父母
* 申请人和儿童处于GX状态
* 申请人负责儿童的日常护理
* 儿童获得支助服务的年龄在16岁以下。

### 亲自查看 {#see-it-yourself}

In your browser, open `https://<hostname>:<PublishPort>/content/we-gov/en.html`. 在We.Gov站点中，单击“子支持”。 在“子支持”页面中，单击“检查您的资格”。

要查看规则：

1. 在创作实例的编辑模式下打开表单。 URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`.
1. Select a component and click ![edit-rules](assets/edit-rules.png).

   此时将打开规则编辑器，列出表单中应用的所有规则。

1. 在左侧面板中，单击规 `passMsg` 则并 `failMsg` 了解资格检查的工作方式。

## Sarah开始她的儿童支持申请 {#sarah-starts-her-application-for-child-support}

Sarah在被 **[!UICONTROL 告知有资格]** 获得儿童支持后，单击“开始应用程序”。\
在“子项支持服务应用程序”页中，Sarah在以下各节中提供了详细信息：

* **[!UICONTROL 关于申请人]**: 让Sarah在本节中提供详细信息。

* **[!UICONTROL 子信息]**: 让Sarah提供儿童信息，该信息由支持服务覆盖。

* **[!UICONTROL 付款]**: 让Sarah提供她的银行详细信息，We.Gov可以在其中按月支付支持赔偿。

* **[!UICONTROL 费用支付]**: 让Sarah提供她的信用卡详细信息以支付申请费。

默认情况下，Sarah会转至“关于 **[!UICONTROL 申请人]** ”部分。

![桌面上的子支持应用程序](assets/desktop.png)

Sarah随时可以单击“稍后 **[!UICONTROL 回来]** ”并继续使用其应用程序。 当她单击“ **[!UICONTROL 稍后回来]**”时，她的进度将保存为草稿，并且她可以选择通过电子邮件发送草稿。

单击“发 **[!UICONTROL 送电子邮件]**”后，她会收到一封电子邮件，其中包含指向其表单草稿的链接。

We.Gov网站上的子支持表单使用自适应表单。 她可以使用电子邮件中的链接，并在移动设备上填写表单。

>[!NOTE]
>
>“从电子邮件继续”工作流程仅适用于已登录的用户。 在参考站点场景中，确保添加了用户Sarah Rose。 Sarah的登录凭据是 `srose/password`。

![mob1](assets/mob1.png)

Sarah可以在任何部分提供详细信息，但只有在所有部分提供所需信息后，才接受申请费。 如果申请不支付费用，则该申请不完整，标有星号的字段为必填字段。

### <strong>Sarah提供她的信息</strong> {#strong-sarah-provides-her-information-strong}

Sarah单击“ **[!UICONTROL 开始申请]**”后，将转到“儿童支持服务申请”页面的“申请人信息”部分。 在“申请人信息”下，Sarah浏览标签并为申请提供个人信息。 她单击“ **[!UICONTROL 下一]** 步”以浏览各个选项卡。

在“申请人信息”下，她需要在以下选项卡下提供详细信息：

* **[!UICONTROL 基本信息]**

在“基本信息”下，Sarah提供她的身份验证和个人信息。 Sarah的个人信息包括她的姓名、电子邮件ID和社会保险号。

* **[!UICONTROL 关系]**

   在“关系”下，Sarah输入有关婚姻状况的信息。

* **[!UICONTROL 附加信息]**

   在“其他信息”下，Sarah输入ID号、出生日期、当前地址和电话号码。

### Sarah提供儿童信息 {#sarah-provides-child-information}

在Sarah提供个人信息并单击“下 **[!UICONTROL 一步]**”后，她将转到“儿童信息”部分。

在“子信息”部分中，她提供以下详细信息：

* 申请儿童支助服务的儿童数
* 儿童姓名、社会保险号、出生日期和出生地

如果Sarah选择多个孩子，她会得到额外的表格，表格中包含相同的详细信息。\
莎拉选择她的独生子乔，并输入他的名字。

### Sarah提供付款信息 {#sarah-provides-payment-information}

在Sarah提供被收养的儿童（或儿童）的信息并单击“下 **[!UICONTROL 一步]**”后，她将转到“付款 **[!UICONTROL 信息]** ”部分。

在“付款信息”部分中，她提供了银行帐户详细信息，可在其中获得儿童支持福利。\
她输入她10位的银行帐号。

## Sarah支付申请费并签署表格 {#sarah-pays-the-application-fee-and-signs-the-form}

在Sarah同意申请的条款和条件后，她支付申请费25美元。 处理申请需要支付申请费。\
Sarah输入她的信用卡详细信息并单击“ **[!UICONTROL 立即付款]**”。 支付费用后，将显示PDF版本的应用程序并带有签名字段。

![sarah-sign-1](assets/sarah-sign-1.png)

Sarah可以选择输入、使用draw进行手写、插入签名图像，或使用手机的触摸屏来绘制签名。 Sarah键入自己的姓名并单击“单击以签名”。

她的申请被提交到We.Gov网站。

### <strong>Sarah收到确认电子邮件</strong> {#strong-sarah-receives-an-acknowledgement-email-strong}

Sarah支付申请费后，她会从We.Gov网站收到一封确认电子邮件。\
We.Gov处理申请，Sarah被告知，在申请获得批准后，她将每月获得报酬。

![sarah-ack-email](assets/sarah-ack-email.png)

### 工作方式 {#how-it-works-1}

子支持应用程序使用顶部选项卡、向导和折叠面板等面板布局的组合来创建体验。 它使用名为We.Gov子模板的表单模板。

申请人可以跨部分移动以填写表单的不同组件。 申请人填写表单、提交表单、同意条款和条件并支付费用时，将启动自定义工作流。 自定义工作流向确认提交申请的申请人发送自动电子邮件。 申请书转送组织有关部门核准。

表单的布局在Gov子支持服务主题中指定。 样式包括组件样式、页面背景、组件错误状态格式和字体样式。

资格检查使用在表单中指定的规则。 它使用下面指定的有效性检查：

`SHOW passMsgWHEN (Does the child live in the state of GX? is equal to Yes) AND (Do you live in the state of GX? is equal to Yes) AND ( (Who has the main day-to-day care of the child? is equal to You) AND (Are you: is equal to The custodial parent) ) AND (Is the child you are applying for: is equal to Under 16 years) ELSE Hide`

`HIDE failMsg WHEN (Does the child lives in the state of GX? is equal to Yes) AND ( (Do you live in the state of GX? is equal to Yes) AND (Who has the main day-to-day care of the child? is equal to You) ) AND (Is the child you are applying for: is equal to Under 16 years) AND (Are you: is equal to The custodial parent) ELSE Show`

### 亲自查看 {#see-it-yourself-1}

在您的浏览器中，打 `https://<hostname>:<PublishPort>/content/forms/af/we-gov/child-support/css.html` 开并填写所需的信息。 在您填写所需信息、支付费用并签署文档后提交申请时，您会收到确认电子邮件。

请在此处查看We.Gov子模板： `https://<hostname>:<AuthorPort>/editor.html/conf/we-gov/settings/wcm/templates/we-gov-child-template/structure.html`

请在此处查看主题： `https://<hostname>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-gov/we-gov-theme-A/jcr:content`

要查看所有规则，请执行以下步骤：

1. 在创作模式下打开表单。

   URL: `https://<hostname>:<AuthorPort>/editor.html/content/forms/af/we-gov/child-support/css.html`

1. 选择一个组件，然后点 ![按edit-rules](assets/edit-rules.png)。 所有规则都列在规则编辑器中，包括上面列出的规则。

## Gloria收到申请 {#gloria-receives-the-application}

We.Gov的审批主管Gloria可以视图、批准或拒绝提交的申请。 AEM Inbox使她能够在一个位置查看所有提交的应用程序。

### 工作方式 {#how-it-works-2}

当Sarah填充并提交子支持应用程序时，将创建该应用程序的PDF或文档记录并发送到Gloria Rios的收件箱。 Gloria可以视图提交的申请，并接受或拒绝它。

### 亲自查看 {#see-it-yourself-2}

打开页面 `https://<hostname***>:<PublishPort>/content/we-gov/en.html`. 在该页上，点按 **[!UICONTROL 登录]**，选中登 **[!UICONTROL 录为代表复选框]** ，使用grios/password作为Gloria Rios的用户名／密码登录AEM收件箱。 出现子支持应用程序。 有关将AEM收件箱用于以表单为中心的工作流任务的信息，请参 [阅在AEM收件箱中管理Forms应](/help/forms/using/manage-applications-inbox.md)用程序和任务。

![We.Gov refsite中的Gloria收件箱](assets/gloria-inbox.png)

Gloria可以从应用程序仪表板查看、批准或拒绝应用程序。

### 工作方式 {#how-it-works-3}

We.Gov的审批主管Gloria打开了她的AEM收件箱。 她在列表任务时看到了评论任务。 她打开，视图评论任务。

她看到表单的PDF中填满了Sarah与Sarah上传的文档一起输入的详细信息。\
Gloria可以批准或拒绝该应用程序。 但是，Gloria单击“ **[!UICONTROL 需要评估]** ”以对申请进行评估。

![Gloria发送评估](assets/gloria-sends-assessment.png)

Sarah的应用程序是AEM工作流程的一个起点。 在提交子支持应用程序表单时，它将启动AEM工作流。 AEM工作流程为Gloria创建一个任务，它显示在她的AEM收件箱中。 当Gloria请求现场评估时，将为现场代理创建新任务。

### 亲自查看 {#see-it-yourself-3}

如果配置完成，AEM工作流会在提交表单后立即开始。 使用Gloria的凭据登录到收件箱。

访问位于https://&lt;***hostname***>:&lt;***PublishPort***>/content/we-gov/en.html的收件箱。 在页面上，点按登 **[!UICONTROL 录]**，选中登 **[!UICONTROL 录为代表复选框]** ，使用Gloria的默认凭据：

* 用户名： 格里奥
* 密码： 口令

在她的AEM收件箱中，Sarah的应用程序被添加为评论任务。 选择任务，然后单 **击“需要** 评估”以继续执行下一步。

### Conard获得评估任务 {#conard-assessment-task}

当Gloria单击“ **[!UICONTROL 需要评估]**”时，Conard将在其AEM收件箱中收到审阅任务。 任务是AEM工作流模型中定义的下一步。 他看到评论任务并打开它。

Conard将获得申请人评估任务，如下所示。

![conrad-inbox](assets/conrad-inbox.png)

子支持评估是与任务关联的表单。 他得到了莎拉的详细信息，以及支持文档(附在任务详细信息中)。 Conard将填写设备上的字段中的评估表单并提交以重新评估。

Conard验证了Sarah提供的所有细节，Sarah签署了评估书。 AEM Forms可以获取地点和时间戳，并将其添加到签名中。

![submit-for-reevaluation](assets/submit-for-re-evaluation.png)

Conard单击 **[!UICONTROL “提交以重新评估]**”,AEM工作流会将评估提交给We.Gov组织。

### 工作方式 {#how-it-works-4}

当Gloria请求评估时，将启动AEM工作流中的下一步，并将评估任务添加到Conard的收件箱中。 康纳德是现场工作者角色。

康纳德拜访了莎拉的住处，确认了莎拉提供的信息是真实的，并填写了评估表。 Conard可以访问Sarah填写的完整表单的PDF。

### 亲自查看 {#see-it-yourself-4}

在平板电脑上打开AEM收件箱，然后使用Conard的凭据登录。

Conard的默认凭据为：

* 用户名： csimms
* 密码： 口令

您可以在收件箱中看到新的评估请求任务。 提交完成的评估并继续执行下一步。

### Gloria审阅评估并批准申请 {#gloria-reviews-the-assessment-and-approves-the-application}

在Conard提交评估后，Gloria在其收件箱中看到“审阅”任务。 她选择并打开“ **[!UICONTROL 评论]**”。

![gloriabox-1](assets/gloriainbox-1.png)

在“任务详细信息”下，Gloria将Last Action Taked视为“Submit for Re-evaluation”（由Conard提交）。 格洛丽亚看到科纳德·西姆斯评估了申请。

![光荣授权](assets/gloriaapproves.png)

### 工作方式 {#how-it-works-5}

在Conard提交评估后，Gloria在其收件箱中看到“审阅”任务。 她选择并打开“审阅”。 在“任务详细信息”下，Gloria看到Conard的评估评论，即“一切按顺序找到”。

格洛丽亚批准了申请。

### 亲自查看 {#see-it-yourself-5}

打开收件箱，然后使用Gloria的凭据登录。 名为“审阅”的新任务会显示在收件箱中。

打开任务以查看上次执行的操作的状态。 根据评估批准申请。

## Sarah收到一封批准电子邮件 {#sarah-receives-an-approval-email}

Gloria批准该申请后，Sarah收到We.Gov发来的一封电子邮件，表明她的申请已获得批准。

电子 **[!UICONTROL 邮件中的]** “视图文档”按钮链接到她的注册详细信息。 Sarah点击 **[!UICONTROL 视图文档。]**

![approval-agtrory-kit-email](assets/approval-enrolment-kit-email.png)

登记文档列表详细信息，如参考ID、受保儿童、开始日期、银行帐户号、付款频率和付款金额。

![sarah-enrment-details](assets/sarah-enrollment-details.png)

Sarah可以视图她在同一页面上传的文档。

![上传的文档](assets/uploaded-documents.png)

### 工作方式 {#how-it-works-6}

Gloria批准该应用程序后，Sarah会收到一封自动电子邮件，其中包含指向注册文档的链接。

注册文档是一种交互式通信，可在任何设备上查看。 它包含儿童支持服务的详细信息以及Sarah提供的信息。

### 亲自查看 {#see-it-yourself-6}

检查您为自动电子邮件配置的电子邮件客户端，其中包含指向注册文档的链接。

或者，要在浏览器中查看文档，请打开： `https://<hostname>:<PublishPort>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-gov/child-support/enrollment-document&referenceId=[reference-id]&channel=web`

## We.Gov分析应用程序的性能 {#we-gov-analyzes-the-performance-of-the-application}

We.Gov会不时检查其子支持服务应用程序的性能，以检查客户可能面临的任何问题。 他们使用此分析对儿童支持服务应用程序中所需的更改做出明智决策，以增强用户体验、降低表单弃用率，从而提高转化率。 他们利用AEM Forms和Adobe Analytics的融合来分析。 以下图像描绘了其分析仪表板。

![child-support-analytics-仪表板](assets/child-support-analytics-dashboard.png)

### 工作方式 {#how-it-works-7}

使用Adobe Analytics跟踪子支持服务应用程序表单的性能指标。 有关配置Adobe Analytics和查看报告的详细信息，请参 [阅配置表单和文档的分析](/help/forms/using/configure-analytics-forms-documents.md)。

### 亲自查看 {#see-it-yourself-7}

为了视图和浏览分析报告，我们将在参考站点为子支持服务应用程序提供种子数据。 在使用种子数据之前，请参 [阅配置分析](/help/forms/using/setup-reference-sites.md#configureanalytics)。 在创作实例中执行以下步骤，将报表视图为种子数据：

1. 转至 **[!UICONTROL Forms和文档]** UI，网址&#x200B;*为https://&lt;hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments。

1. 单击以打 **开We.Gov** 文件夹。
1. 选择 **[!UICONTROL “子支持服务应用程序]** ”自适应表单，然后单 **[!UICONTROL 击工具栏中的“启]** 用分析”。

1. 再次选择表单，然后单 **[!UICONTROL 击工具栏]** 中的分析报表以生成报表。 您最初会看到一个空白报告。

要使用种子数据生成分析报告，请执行以下操作：

1. 在CRXDE lite的地址浏览器中，键入： **/apps/we-gov/demo-artifacts/analyticsTestData/Child支持服务分析测试数据**
1. 在左侧目录结构中选择种子数据。
1. 多次单击所选文件以在右侧面板中打开其内容。
1. 复制测试数据文件中的所有内容。
1. 在CRXDE中，导航到： **/content/dam/formsanddocuments/we-gov/child-support/css/jcr:content/analyticsdatanode/lastsevdays**
1. 在“Properties（属性）”下的“Analyticsdata（分析数据）”字段中，粘贴测试数据文件的复制内容。
1. 现在，再次为“子支持服 **[!UICONTROL 务应用程序”生成分析报告]**。 您可以在生成的报告中查看种子数据。

