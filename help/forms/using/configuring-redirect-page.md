---
title: 配置重定向页面
seo-title: Configuring redirect page
description: 填写自适应表单后，可以将用户重定向到表单作者在创建表单时可以配置的网页。
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: 5a5f912a-9696-4bc1-af3f-ead78f767e02
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c51817aa-193a-4d4f-bd83-06518ddfb395
feature: Adaptive Forms
exl-id: bbe10952-d6a7-4adc-bab9-388c1ee8e56a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 1%

---

# 配置重定向页面 {#configuring-redirect-page}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

表单作者可以为每个表单配置一个页面，表单用户在提交表单后将被重定向到该页面。

1. 在编辑模式下，选择一个组件，然后单击 ![字段级别](assets/field-level.png) > **自适应表单容器**，然后单击 ![cppr](assets/cmppr.png).

1. 在侧栏中，单击 **提交**.

1. 在提交部分的感谢页面下提供重定向页面的URL。
1. 或者，在提交操作下方的提交到REST端点操作中，您可以配置要传递到重定向页面的参数。

![重定向页面配置](assets/thank-you-setting-1.png)
**图：** *重定向页面配置*

表单作者可以使用传递到感谢页面的以下参数。 对于所有可用的提交操作， `status` 和 `owner` 参数被传递。 除了这两个参数之外，还会为以下提交操作传递一些其他参数：

* **存储内容操作** （已弃用）： `contentPath` — 传递存储提交数据的存储库中节点的路径。

* **存储PDF操作** （已弃用）： `contentPath` — 已提交的数据和到存储库中存储PDF文件的节点的路径，将被传递。

* **提交到Forms工作流**:传递从表单工作流返回的输出参数。

* **提交到REST端点**:将传递为字段内参数映射添加的参数。 `status` 和 `owner` 此提交操作中未传递参数。 有关更多信息，请参阅 [配置提交到REST端点提交操作](/help/forms/using/configuring-submit-actions.md).
