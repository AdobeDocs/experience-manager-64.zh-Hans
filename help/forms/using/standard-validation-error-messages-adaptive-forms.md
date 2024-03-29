---
title: 自适应表单的标准验证错误消息
seo-title: Standard validation error messages for adaptive forms
description: 使用自定义错误处理程序将自适应表单的验证错误消息转换为标准格式
seo-description: Transform the validation error messages for adaptive forms into standard format using custom error handlers
uuid: 0d1f9835-3e28-41d3-a3b1-e36d95384328
contentOwner: anujkapo
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
discoiquuid: ec062567-1c6b-497b-a1e7-1dbac2d60852
feature: Adaptive Forms
exl-id: 864e6b0d-178b-4b91-85d3-34b90e999ee3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 0%

---

# 自适应表单的标准验证错误消息 {#standard-validation-error-messages}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

自适应表单会根据预设的验证条件验证您在字段中提供的输入。 验证标准是指自适应表单中字段的可接受输入值。 您可以根据与自适应表单一起使用的数据源设置验证标准。 例如，如果使用RESTful Web服务作为数据源，则可以在Swagger定义文件中定义验证条件。

如果输入值符合验证标准，则会将值提交到数据源。 否则，自适应表单会显示一条错误消息。

与这种方法类似，自适应表单现在可以与自定义服务集成以执行数据验证。 如果输入值不符合验证标准且服务器返回的验证错误消息为标准消息格式，则错误消息将在表单的字段级别显示。

如果输入值不满足验证标准并且服务器验证错误消息不是标准消息格式，自适应表单提供一种机制，用于将验证错误消息转换为标准格式，以便它们在表单的字段级别显示。 您可以使用以下两种方法中的任意一种将错误消息转换为标准格式：

* 在自适应表单提交中添加自定义错误处理程序
* 添加自定义处理程序以使用规则编辑器调用服务操作

本文介绍了验证错误消息的标准格式以及将错误消息从自定义格式转换为标准格式的说明。

## 标准验证错误消息格式 {#standard-validation-message-format}

如果服务器验证错误消息采用以下标准格式，则自适应表单会在字段级别显示错误：

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]

        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
}
```

其中：

* `errorCausedBy` 描述失败的原因
* `errors` 提及验证标准失败字段的SOM表达式和验证错误消息
* `originCode` 包含外部服务返回的错误代码
* `originMessage` 包含外部服务返回的原始错误数据

## 配置自适应表单提交以添加自定义处理程序 {#configure-adaptive-form-submission}

如果服务器验证错误消息未以标准格式显示，则可以启用异步提交并在自适应表单提交中添加自定义错误处理程序，以将消息转换为标准格式。

### 配置异步自适应表单提交 {#configure-asynchronous-adaptive-form-submission}

添加自定义处理程序之前，必须配置用于异步提交的自适应表单。 执行以下步骤：

1. 在自适应表单创作模式中，选择表单容器对象并点按 ![自适应表单属性](assets/configure_icon.png) 以打开其资产。
1. 在 **[!UICONTROL 提交]** 属性部分，启用 **[!UICONTROL 使用异步提交]**.
1. 选择 **[!UICONTROL 在服务器上重新验证]** 在提交之前验证服务器上的输入字段值。
1. 选择提交操作：

   * 选择 **[!UICONTROL 使用表单数据模型提交]** 如果您使用的是基于RESTful Web服务，则选择相应的数据模型 [表单数据模型](work-with-form-data-model.md) 作为数据源。
   * 选择 **[!UICONTROL 提交到REST端点]** 并指定 **[!UICONTROL 重定向URL/路径]**，如果您使用RESTful Web服务作为数据源。

   ![自适应表单提交属性](assets/af_submission_properties.png)

1. 点按 ![保存](assets/save_icon.png) 以保存属性。

### 在自适应表单提交中添加自定义错误处理程序 {#add-custom-error-handler-af-submission}

AEM Forms为表单提交提供了开箱即用的成功和错误处理程序。 处理程序是基于服务器响应执行的客户端函数。 在提交表单时，数据被传输到服务器进行验证，服务器会向客户端返回响应，其中包含有关提交的成功或错误事件的信息。 该信息作为参数传递给相关处理程序以执行该函数。

执行以下步骤，在自适应表单提交中添加自定义错误处理程序：

1. 在创作模式下打开自适应表单，选择任意表单对象，然后点按 <!--![Rule Editor](assets/af_edit_rules.png)--> 以打开规则编辑器。
1. 选择 **[!UICONTROL 表单]** 在表单对象树中，点按 **[!UICONTROL 创建]**.
1. 选择 **[!UICONTROL 提交错误]** 从事件下拉列表中。
1. 编写规则以将自定义错误结构转换为标准错误结构并点按 **[!UICONTROL 完成]** 来保存规则。

以下是将自定义错误结构转换为标准错误结构的示例代码：

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

的 `var som_map` 列出要转换为标准格式的自适应表单字段的SOM表达式。 您可以通过点按自适应表单中的任意字段并选择，来查看该字段的SOM表达式 **[!UICONTROL 查看SOM表达式]**.

自适应表单使用此自定义错误处理程序，转换 `var som_map` 格式。 因此，验证错误消息会在自适应表单的字段级别显示。

## 使用调用服务操作添加自定义处理程序

执行以下步骤以添加错误处理程序，以使用将自定义错误结构转换为标准错误结构 [规则编辑器](rule-editor.md) 调用服务操作：

1. 在创作模式下打开自适应表单，选择任意表单对象，然后点按 ![规则编辑器](assets/rule_editor_icon.png) 以打开规则编辑器。
1. 点按 **[!UICONTROL 创建]**.
1. 在 **[!UICONTROL When]** 部分。 例如，[字段名称] 中，将会更改。 选择 **[!UICONTROL 已更改]** 从 **[!UICONTROL 选择状态]** 下拉列表来实现此条件。
1. 在 **[!UICONTROL 然后]** 选择 **[!UICONTROL 调用服务]** 从 **[!UICONTROL 选择操作]** 下拉列表。
1. 从 **[!UICONTROL 输入]** 中。 例如，如果要验证 **名称**, **ID**&#x200B;和 **状态** 自适应表单中的字段，选择帖子服务(pet)，然后在 **[!UICONTROL 输入]** 中。

作为此规则的结果，您为输入的值 **名称**, **ID**&#x200B;和 **状态** 如果第2步中定义的字段发生更改，并且您跳出表单中的字段，则会立即验证字段。

1. 选择 **[!UICONTROL 代码编辑器]** 从模式选择下拉列表中。
1. 点按 **[!UICONTROL 编辑代码]**.
1. 从现有代码中删除以下行：

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
   ```

1. 编写规则以将自定义错误结构转换为标准错误结构并点按 **[!UICONTROL 完成]** 来保存规则。
例如，在末尾添加以下示例代码，以将自定义错误结构转换为标准错误结构：

   ```javascript
   var errorHandler = function(jqXHR, data) {
   var som_map = {
       "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
       "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
       "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
   };
   
   
   var errorJson = {};
   errorJson.errors = [];
   
   if (data) {
       if (data.originMessage) {
           var errorData;
           try {
               errorData = JSON.parse(data.originMessage);
           } catch (err) {
               // not in json format
           }
   
           if (errorData) {
               Object.keys(errorData).forEach(function(key) {
                   var som_key = som_map[key];
                   if (som_key) {
                       var error = {};
                       error.somExpression = som_key;
                       error.errorMessage = errorData[key];
                       errorJson.errors.push(error);
                   }
               });
           }
           window.guideBridge.handleServerValidationError(errorJson);
       } else {
           window.guideBridge.handleServerValidationError(data);
       }
     }
   };
   
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   的 `var som_map` 列出要转换为标准格式的自适应表单字段的SOM表达式。 您可以通过点按自适应表单中的任意字段并选择，来查看该字段的SOM表达式 **[!UICONTROL 查看SOM表达式]** 从 **[!UICONTROL 更多选项]** (...)菜单。

   确保将示例代码的以下行复制到自定义错误处理程序：

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   executeOperation API包含 `null` 和 `errorHandler` 参数。

   自适应表单使用此自定义错误处理程序，转换 `var som_map` 格式。 因此，验证错误消息会在自适应表单的字段级别显示。
