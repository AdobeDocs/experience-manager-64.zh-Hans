---
title: 用于从自适应表单调用表单数据模型服务的API
seo-title: 用于从自适应表单调用表单数据模型服务的API
description: '说明可用于从自适应表单字段中调用以WSDL编写的Web服务的invokeWebServices API。 '
seo-description: '说明可用于从自适应表单字段中调用以WSDL编写的Web服务的invokeWebServices API。 '
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
feature: 自适应表单
exl-id: 0653b0e4-a697-472a-8093-5ed48ede3c75
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# 从自适应表单{#api-to-invoke-form-data-model-service-from-adaptive-forms}调用表单数据模型服务的API

## 概述 {#overview}

AEM Forms允许表单作者通过从自适应表单字段中调用在表单数据模型中配置的服务，进一步简化和增强表单填充体验。 要调用数据模型服务，您可以在可视编辑器中创建规则，或在[规则编辑器](/help/forms/using/rule-editor.md)的代码编辑器中使用`guidelib.dataIntegrationUtils.executeOperation` API指定JavaScript。

本文档重点介绍如何使用`guidelib.dataIntegrationUtils.executeOperation` API编写JavaScript以调用服务。

## 使用API {#using-the-api}

`guidelib.dataIntegrationUtils.executeOperation` API从自适应表单字段中调用服务。 API语法如下所示：

```
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

API需要以下参数。

| 参数 | 描述 |
|---|---|
| `operationInfo` | 指定表单数据模型标识符、操作标题和操作名称的结构 |
| `inputs` | 用于指定其值输入到服务操作的表单对象的结构 |
| `outputs` | 用于指定将使用服务操作返回的值填充的表单对象的结构 |

`guidelib.dataIntegrationUtils.executeOperation` API的结构指定了有关服务操作的详细信息。 结构的语法如下所示。

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
   <td>将一个或多个表单对象映射到服务操作中的输出值以填充表单字段<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 调用服务{#sample-script-to-invoke-a-service}的示例脚本

以下示例脚本使用`guidelib.dataIntegrationUtils.executeOperation` API调用在`employeeAccount`表单数据模型中配置的`getAccountById`服务操作。

`getAccountById`操作将`employeeID`表单字段中的值作为`empId`参数的输入，并返回相应员工的员工姓名、帐号和帐户余额。 输出值将填充在指定的表单字段中。 例如，`name`参数中的值填充在`fullName`表单元素中，而`accountNumber`参数的值填充在`account`表单元素中。

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
