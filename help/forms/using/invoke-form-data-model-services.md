---
title: 从自适应表单调用表单数据模型服务的API
seo-title: 从自适应表单调用表单数据模型服务的API
description: '解释了invokeWebServices API，您可以使用它从自适应表单字段中调用以WSDL编写的Web服务。 '
seo-description: '解释了invokeWebServices API，您可以使用它从自适应表单字段中调用以WSDL编写的Web服务。 '
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 1%

---


# 从自适应表单调用表单数据模型服务的API {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## 概述 {#overview}

AEM Forms使表单作者能够从自适应表单字段中调用表单数据模型中配置的服务，从而进一步简化和增强表单填写体验。 要调用数据模型服务，您可以在可视编辑器中创建规则，或使用规则编辑器的代码 `guidelib.dataIntegrationUtils.executeOperation` 编辑器中的API指定 [JavaScript](/help/forms/using/rule-editor.md)。

此文档侧重于使用API调 `guidelib.dataIntegrationUtils.executeOperation` 用服务编写JavaScript。

## 使用API {#using-the-api}

API `guidelib.dataIntegrationUtils.executeOperation` 从自适应表单字段中调用服务。 API语法如下：

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

API需要以下参数。

| 参数 | 描述 |
|---|---|
| `operationInfo` | 用于指定表单数据模型标识符、操作标题和操作名称的结构 |
| `inputs` | 用于指定其值输入到服务操作的表单对象的结构 |
| `outputs` | 用于指定将填充服务操作返回值的表单对象的结构 |

API的结构指定 `guidelib.dataIntegrationUtils.executeOperation` 了有关服务操作的详细信息。 结构的语法如下所示。

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

API结构指定有关服务操作的以下详细信息。

<table> 
 <tbody> 
  <tr> 
   <th>参数</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td><code>forDataModelId</code></td> 
   <td>指定表单数据模型的存储库路径，包括其名称</td> 
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
   <td>将一个或多个表单对象映射到服务操作中的输出值以填充表单字段<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 调用服务的示例脚本 {#sample-script-to-invoke-a-service}

以下示例脚本使用 `guidelib.dataIntegrationUtils.executeOperation` API调用表单 `getAccountById` 数据模型中配置的 `employeeAccount` 服务操作。

此操 `getAccountById` 作将表单字段中的 `employeeID` 值作为参数的输入，并返回 `empId` 相应员工的员工姓名、帐户编号和帐户余额。 输出值将填充到指定的表单字段中。 例如，参数中的值 `name` 将填充在表单元 `fullName` 素中，而参数的 `accountNumber` 值将填充 `account` 在表单元素中。

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

