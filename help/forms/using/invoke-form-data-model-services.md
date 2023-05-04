---
title: 用于从自适应表单调用表单数据模型服务的API
seo-title: API to invoke form data model service from adaptive forms
description: 说明可用于从自适应表单字段中调用以WSDL编写的Web服务的invokeWebServices API。
seo-description: Explains the invokeWebServices API that you can use to invoke web services written in WSDL from within an adaptive form field.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: Adaptive Forms
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 2%

---

# 用于从自适应表单调用表单数据模型服务的API {#api-to-invoke-form-data-model-service-from-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

AEM Forms允许表单作者通过从自适应表单字段中调用在表单数据模型中配置的服务，进一步简化和增强表单填充体验。 要调用数据模型服务，您可以在可视编辑器中创建规则，或使用 `guidelib.dataIntegrationUtils.executeOperation` 代码编辑器中的API [规则编辑器](/help/forms/using/rule-editor.md).

本文档重点介绍如何使用 `guidelib.dataIntegrationUtils.executeOperation` 用于调用服务的API。

## 使用API {#using-the-api}

的 `guidelib.dataIntegrationUtils.executeOperation` API从自适应表单字段内调用服务。 API语法如下所示：

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

API需要以下参数。

| 参数 | 描述 |
|---|---|
| `operationInfo` | 指定表单数据模型标识符、操作标题和操作名称的结构 |
| `inputs` | 用于指定其值输入到服务操作的表单对象的结构 |
| `outputs` | 用于指定将使用服务操作返回的值填充的表单对象的结构 |

的结构 `guidelib.dataIntegrationUtils.executeOperation` API指定有关服务操作的详细信息。 结构的语法如下所示。

```
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

API结构指定了有关服务操作的以下详细信息。

<table> 
 <tbody> 
  <tr> 
   <th>参数</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>指定表单数据模型的存储库路径（包括其名称）</td> 
  </tr> 
  <tr> 
   <td><code>operationName</code></td> 
   <td>指定要执行的服务操作的名称</td> 
  </tr> 
  <tr> 
   <td><code>input</code></td> 
   <td>将一个或多个表单对象映射到服务操作的输入参数</td> 
  </tr> 
  <tr> 
   <td>输出</td> 
   <td>映射一个或多个表单对象以从服务操作输出值以填充表单字段<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 调用服务的示例脚本 {#sample-script-to-invoke-a-service}

以下示例脚本使用 `guidelib.dataIntegrationUtils.executeOperation` 用于调用的API `getAccountById` 在 `employeeAccount` 表单数据模型。

的 `getAccountById` 操作采用 `employeeID` 表单字段作为输入 `empId` 参数和返回相应员工的员工名称、帐号和帐户余额。 输出值将填充在指定的表单字段中。 例如， `name` 参数会填充在 `fullName` 表单元素和值 `accountNumber` 参数 `account` 表单元素。

```
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```
