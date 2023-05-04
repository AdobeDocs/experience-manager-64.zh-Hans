---
title: 创建您的第一个自适应表单
seo-title: Create your first adaptive form
description: 了解如何创建业务类、交互式和响应式表单。
seo-description: Learn to create business class, interactive, and responsive forms.
page-status-flag: de-activated
uuid: 62f5222c-c787-46be-95fa-a701aa0e6115
topic-tags: introduction
discoiquuid: 4e247e70-c50a-4571-8ac1-fbbb07100262
feature: Adaptive Forms
exl-id: f634a73a-e720-4a38-a459-6ddbe4fdc565
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '986'
ht-degree: 1%

---

# 创建您的第一个自适应表单 {#do-not-publish-create-your-first-adaptive-form}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## 简介 {#introduction}

您是否在寻找适合移动设备的 **表单体验** 简化注册、增加参与度并缩短周转时间， **自适应表单** 非常适合你。 自适应表单可提供移动、自动化和分析友好的表单体验。 您可以轻松构建具有响应性和交互性的表单，使用自动化流程减少管理和重复性任务，并使用数据分析来改进和个性化客户在您的表单上的体验。

本教程提供了用于创建自适应表单的端到端框架。 本教程分为一个用例和多个指南。 每个指南都可帮助您学习并将新功能添加到本教程中创建的自适应表单。 您在每个指南之后都有一个有效的自适应表单。 有关创建自适应表单的指南，请参阅。 随后的指南即将推出。 在本教程结束时，您将能够：

* 创建自适应表单和表单数据模型。
* 设置自适应表单的样式。
* 使用自适应表单规则编辑器来构建业务规则。
* 测试和发布自适应表单。

![创建 — 适应 — 表单 — 工作流](assets/create-daptive-form-workflow.png)

历程从学习用例开始：

网站为不同的客户提供一系列产品。 客户浏览门户，选择并订购产品。 每个客户都创建一个帐户并提供送货和帐单地址。 现有客户莎拉·罗丝正在寻求将她的送货地址添加到网站。 该网站提供在线表格以添加和更新送货地址。

该网站在Adobe Experience Manager(AEM)上运行，并使用AEM Forms进行数据捕获和处理。 地址添加和更新表单是自适应表单。 网站将客户详细信息存储在数据库中。 他们使用地址添加和更新表单来检索和显示可用地址。 他们还使用自适应表单来接受更新的地址和新地址。

### 先决条件 {#prerequisite}

* 设置AEM创作实例。
* 安装 [AEM Forms附加组件](/help/forms/using/installing-configuring-aem-forms-osgi.md) 在创作实例上。
* 从数据库提供程序获取JDBC数据库驱动程序（JAR文件）。 本教程中的示例以MySQL数据库为基础，并使用Oracle [MySQL JDBC数据库驱动程序](https://dev.mysql.com/downloads/connector/j/5.1.html).

* 使用下面显示的字段设置包含客户数据的数据库。 数据库对于创建自适应表单并不是必需的。 本教程使用数据库来显示AEM Forms的表单数据模型和持久性功能。

![自适应格式数据](assets/adaptiveformdata.png)

## 步骤1:创建自适应表单 {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small_new](assets/03-create-adaptive-form-main-image_small_new.png)

自适应表单是新一代，具有吸引力、响应性、动态性和自适应性。 使用自适应表单，您可以提供个性化且有针对性的体验。 AEM Forms提供拖放WYSIWYG编辑器以创建自适应表单。 有关自适应表单的更多信息，请参阅 [创作自适应表单简介](/help/forms/using/introduction-forms-authoring.md).

目标：

* 创建允许客户添加送货地址的自适应表单
* 用于显示和接受客户信息的自适应表单的布局字段
* 创建提交操作以发送包含表单内容的电子邮件
* 预览和提交自适应表单

[ ](create-adaptive-form.md)

## 步骤2:创建表单数据模型 {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

表单数据模型允许将自适应表单连接到不同的数据源。 例如，AEM用户配置文件、RESTful Web服务、基于SOAP的Web服务、OData服务和关系数据库。 表单数据模型是业务实体和服务在连接数据源中提供的统一数据表示模式。 您可以将表单数据模型与自适应表单结合使用，以检索、更新、删除数据，并将数据添加到连接的数据源。

目标：

* 将网站的数据库实例（MySQL数据库）配置为数据源
* 使用MySQL数据库作为数据源创建表单数据模型
* 添加数据模型对象以形成数据模型
* 为表单数据模型配置读写服务
* 测试表单数据模型和配置有测试数据的服务

[ ](create-form-data-model.md)

## 步骤3:将规则应用于自适应表单字段 {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

自适应表单提供一个编辑器，用于在自适应表单对象上写入规则。 这些规则根据表单上的预设条件、用户输入和用户操作定义要在表单对象上触发的操作。 它有助于确保准确性并加快表单填写体验的速度。

目标：

* 创建规则并将其应用于自适应表单字段
* 使用规则触发表单数据模型服务以将数据更新到数据库

## 步骤4:设置自适应表单的样式 {#step-style-your-adaptive-form}

![09-Style-your-adaptive-form_small](assets/09-Style-your-adaptive-form_small.png)

自适应表单提供主题和 [编辑者](/help/forms/using/themes.md) 创建自适应表单的主题。 主题包含组件和面板的样式详细信息，您可以以不同的形式重复使用主题。 样式包括背景颜色、状态颜色、透明度、对齐方式和大小等属性。 将主题应用于表单时，指定的样式将反映在表单的相应组件上。 自适应表单还支持特定于表单的样式的内嵌样式。

目标：

* 将现成主题应用于自适应表单
* 使用主题编辑器创建自适应表单的主题
* 在自定义主题中使用Web字体

[ ](style-your-adaptive-form.md)

## 步骤5:测试自适应表单 {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

自适应表单是客户交互的必备组件。 测试自适应表单时，务必要进行每项更改。 测试表单的每个字段都很繁琐。 AEM Forms提供了一个SDK(Calvin SDK)来自动测试自适应表单。 Calvin允许您在Web浏览器中自动测试自适应表单。

目标：

* 安装Calvin SDK
* 为更改地址表单创建测试包和测试案例

要了解SDK，请参阅 [在AEM自适应表单中使用自动测试](/help/forms/using/calvin.md).

## 步骤6:发布自适应表单 {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

您可以将自适应表单作为独立表单（单页应用程序）发布，并包含在AEM中 [站点页面](/help/forms/using/embed-adaptive-form-aem-sites.md)，或列在AEM网站上使用 [Forms门户](/help/forms/using/introduction-publishing-forms.md).

目标：

* 将自适应表单作为单页应用程序发布
