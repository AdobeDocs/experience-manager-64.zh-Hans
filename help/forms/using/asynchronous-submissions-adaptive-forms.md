---
title: 异步提交自适应表单
seo-title: Asynchronous submission of adaptive forms
description: 了解如何为自适应表单配置异步提交。
seo-description: Learn to configure asynchronous submission for adaptive forms.
uuid: 3b8aeac8-cb38-4a2b-8375-556b2736d58b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 6e4e3af5-4260-4f38-9b29-0818e92bc182
feature: Adaptive Forms
exl-id: 1ca492e9-9832-4e5d-8020-2690ac4f5505
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# 异步提交自适应表单 {#asynchronous-submission-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

传统上，Web表单配置为同步提交。 当用户提交表单时，会将他们重定向到确认页面，或者在提交失败时，会重定向到错误页面。 但是，诸如单页应用程序等现代Web体验越来越受欢迎，其中网页保持静态，而客户端 — 服务器交互在后台进行。 您现在可以通过配置异步提交，为此体验提供自适应表单。 在这种情况下，自适应表单的行为与单页应用程序类似，因为当在服务器上验证提交的表单数据后，表单不会重新加载或其URL不会更改。

请阅读有关自适应表单中异步提交的详细信息。

## 配置异步提交 {#configure}

要配置自适应表单的异步提交，请执行以下操作：

1. 在自适应表单创作模式中，选择表单容器对象并点按 ![cmppr1](assets/cmppr1.png) 以打开其资产。
1. 在 **[!UICONTROL 提交]** 属性部分，启用 **[!UICONTROL 使用异步提交]**.
1. 在 **[!UICONTROL 提交时]** 部分，选择以下选项之一以成功提交表单。

   * **[!UICONTROL 重定向到URL]**:在表单提交时重定向到指定的URL或页面。 您可以指定URL或浏览以在 **[!UICONTROL 重定向URL/路径]** 字段。
   * **[!UICONTROL 显示消息]**:在表单提交时显示消息。 您可以在“显示消息”选项下方的文本字段中写入消息。 文本字段支持富文本格式。

1. 点按 ![check-button1](assets/check-button1.png) 以保存属性。

## 异步提交的工作原理 {#how-asynchronous-submission-works}

AEM Forms为表单提交提供了开箱即用的成功和错误处理程序。 处理程序是基于服务器响应执行的客户端函数。 在提交表单时，数据被传输到服务器进行验证，服务器会向客户端返回响应，其中包含有关提交的成功或错误事件的信息。 该信息作为参数传递给相关处理程序以执行该函数。

此外，表单作者和开发人员可以在表单级别编写规则以覆盖默认处理程序。 有关更多信息，请参阅 [使用规则覆盖默认处理程序](#custom).

让我们首先查看服务器对成功事件和错误事件的响应。

### 提交成功事件的服务器响应 {#server-response-for-submission-success-event}

提交成功事件的服务器响应的结构如下：

```
{
  contentType : "<xmlschema or jsonschema>", 
  data : "<dataXML or dataJson>" , 
  thankYouOption : <page/message>, 
  thankYouContent : "<thank you page url/thank you message>"
}
```

成功提交表单时的服务器响应包括：

* 表单数据格式类型：XML或JSON
* XML或JSON格式的表单数据
* 选择了重定向到页面或显示消息的选项，该选项在表单中进行了配置
* 表单中配置的页面URL或消息内容

成功处理程序读取服务器响应并相应地重定向到配置的页面URL或显示消息。

### 针对提交错误事件的服务器响应 {#server-response-for-submission-error-event}

服务器响应提交错误事件的结构如下：

```
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

表单提交出错时的服务器响应包括：

* 错误、CAPTCHA或服务器端验证失败的原因
* 错误对象列表，包括验证失败的字段的SOM表达式和相应的错误消息

错误处理程序读取服务器响应，并相应地在表单上显示错误消息。

## 使用规则覆盖默认处理程序 {#custom}

表单开发人员和作者可以在表单级别的代码编辑器中编写规则，以覆盖默认处理程序。 成功事件和错误事件的服务器响应在表单级别显示，开发人员可以使用 `$event.data` 在规则中。

执行以下步骤以在代码编辑器中写入规则以处理成功事件和错误事件。

1. 在创作模式下打开自适应表单，选择任意表单对象，然后点按 ![edit-rules1](assets/edit-rules1.png) 以打开规则编辑器。
1. 选择 **[!UICONTROL 表单]** 在表单对象树中，点按 **[!UICONTROL 创建]**.
1. 选择 **[!UICONTROL 代码编辑器]** 从“模式选择”下拉列表中。
1. 在代码编辑器中，点按 **[!UICONTROL 编辑代码]**. 点按 **[!UICONTROL 编辑]** 在确认对话框中。
1. 选择 **[!UICONTROL 成功提交]** 或 **[!UICONTROL 提交错误]** 从 **[!UICONTROL 事件]** 下拉菜单。
1. 为选定事件编写规则并点按 **[!UICONTROL 完成]** 来保存规则。
