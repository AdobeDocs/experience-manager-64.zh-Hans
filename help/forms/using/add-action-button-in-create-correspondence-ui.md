---
title: 在创建通信UI中添加自定义操作/按钮
seo-title: Add custom action/button in Create Correspondence UI
description: 了解如何在创建通信UI中添加自定义操作/按钮
seo-description: Learn how to add custom action/button in Create Correspondence UI
uuid: e3609371-caaa-4efe-8f63-4d982cd456ab
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 481856df-5db1-4ef5-80d3-3722b5bf8b67
feature: Correspondence Management
exl-id: 5bcb26dc-aeb7-4a81-b905-23c8fb05d6d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1891'
ht-degree: 1%

---

# 在创建通信UI中添加自定义操作/按钮 {#add-custom-action-button-in-create-correspondence-ui}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

通信管理解决方案允许您向创建通信用户界面添加自定义操作。

本文档中的情景说明如何在创建通信用户界面中创建按钮，以将信件作为附加到电子邮件的审阅PDF共享。

### 前提条件 {#prerequisites}

要完成此方案，您需要满足以下条件：

* CRX和JavaScript知识
* LiveCycle服务器

## 方案：在创建通信用户界面中创建按钮以发送信件以供审阅 {#scenario-create-the-button-in-the-create-correspondence-user-interface-to-send-a-letter-for-review}

在创建通信用户界面中添加包含操作的按钮（此处为发送信件供审阅）包括：

1. 将按钮添加到创建通信用户界面
1. 向按钮添加操作处理
1. 添加LiveCycle流程以启用操作“处理”

### 将按钮添加到“创建通信”用户界面 {#add-the-button-to-the-create-correspondence-user-interface}

1. 转到 `https://[server]:[port]/[ContextPath]/crx/de` 和以管理员身份登录。
1. 在apps文件夹中，创建一个名为 `defaultApp` 路径/结构与defaultApp文件夹类似（位于配置文件夹中）。 请按照以下步骤创建文件夹：

   * 右键单击 **[!UICONTROL defaultApp]** 文件夹，然后选择 **[!UICONTROL 覆盖节点]**:

      /libs/fd/cm/config/defaultApp/

      ![覆盖节点](assets/1_defaultapp.png)

   * 确保“覆盖节点”对话框具有以下值：

      **[!UICONTROL 路径：]** /libs/fd/cm/config/defaultApp/

      **[!UICONTROL 叠加位置：]** /apps/

      **[!UICONTROL 匹配节点类型：]** 已选中

      ![覆盖节点](assets/2_defaultappoverlaynode.png)

   * 单击&#x200B;**[!UICONTROL 确定]**。
   * 单击 **[!UICONTROL 全部保存]**.

1. 复制/apps分支下的acmExtensionsConfig.xml文件（位于/libs分支下）。

   * 转到“/libs/fd/cm/config/defaultApp/acmExtensionsConfig.xml”

   * 右键单击acmExtensionsConfig.xml文件，然后选择 **[!UICONTROL 复制]**.

      ![复制acmExtensionsConfig.xml](assets/3_acmextensionsconfig_xml_copy.png)

   * 右键单击 **[!UICONTROL defaultApp]** 文件夹（位于“/apps/fd/cm/config/defaultApp/，”），然后选择 **[!UICONTROL 粘贴]**.
   * 单击 **[!UICONTROL 全部保存]**.

1. 双击您新在apps文件夹中创建的acmExtensionsConfig.xml的副本。 随即会打开文件进行编辑。
1. 找到以下代码：

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <extensionsConfig>
       <modelExtensions>
           <modelExtension type="LetterInstance">
     <customAction name="Preview" label="loc.letterInstance.preview.label" tooltip="loc.letterInstance.preview.tooltip" styleName="previewButton"/>
               <customAction name="Submit" label="loc.letterInstance.submit.label" tooltip="loc.letterInstance.submit.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="SaveAsDraft" label="loc.letterInstance.saveAsDraft.label" tooltip="loc.letterInstance.saveAsDraft.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="Close" label="loc.letterInstance.close.label" tooltip="loc.letterInstance.close.tooltip" styleName="closeButton"/>
           </modelExtension>
       </modelExtensions>
   </extensionsConfig> 
   ```

1. 要发送电子邮件，您可以使用LiveCycleForms Workflow。 在acmExtensionsConfig.xml的modelExtension标记下添加customAction标记，如下所示：

   ```xml
    <customAction name="Letter Review" label="Letter Review" tooltip="Letter Review" styleName="" permissionName="forms-users" actionHandler="CM.domain.CCRCustomActionHandler">
         <serviceName>Forms Workflow -> SendLetterForReview/SendLetterForReviewProcess</serviceName>
       </customAction>
   ```

   ![customAction标记](assets/5_acmextensionsconfig_xml.png)

   modelExtension标记包含一组customAction子标记，用于配置操作按钮的操作、权限和外观。 以下是customAction配置标记的列表：

   | **名称** | **描述** |
   |---|---|
   | name | 要执行的操作的字母数字名称。 此标记的值是必需的，必须是唯一的（在modelExtension标记内），且必须以字母表开头。 |
   | 标签 | 要在操作按钮上显示的标签 |
   | 工具提示 | 按钮的工具提示文本，当用户将鼠标悬停在按钮上时，将显示该文本。 |
   | styleName | 应用于操作按钮的自定义样式的名称。 |
   | permissionName | 仅当用户具有permissionName指定的权限时，才会显示相应的操作。 将permissionName指定为 `forms-users`，则所有用户都有权访问此选项。 |
   | actionHandler | 用户单击按钮时调用的ActionHandler类的完全限定名称。 |

   除了上述参数之外，还可能有其他与customAction关联的配置。 这些附加配置可通过CustomAction对象提供给处理程序。

   | **名称** | **描述** |
   |---|---|
   | serviceName | 如果customAction包含名为serviceName的子标记，则在单击相关按钮/链接时，将调用一个进程，该进程的名称由serviceName标记表示。 确保此过程与Letter PostProcess具有相同的签名。 在服务名称中添加“Forms Workflow->”前缀。 |
   | 标记名称中包含cm_前缀的参数 | 如果customAction包含以名称cm_开头的子标记，则在后处理（无论是信件后处理还是由serviceName标记表示的特殊过程）中，这些参数可在删除了cm_前缀的相关标记下的输入XML代码中使用。 |
   | actionName | 每当发生点击后进程时，提交的XML都会在标记下包含一个特殊标记，该标记名称带有用户操作名称。 |

1. 单击 **[!UICONTROL 全部保存]**.

#### 在/apps分支中使用属性文件创建区域设置文件夹 {#create-a-locale-folder-with-properties-file-in-the-apps-branch}

ACMExtensionsMessages.properties文件包含“创建通信”用户界面中各个字段的标签和工具提示消息。 要使自定义操作/按钮正常工作，请在/apps分支中复制此文件。

1. 右键单击 **[!UICONTROL 语言]** 文件夹，然后选择 **[!UICONTROL 覆盖节点]**:

   /libs/fd/cm/config/defaultApp/locale

1. 确保“覆盖节点”对话框具有以下值：

   **[!UICONTROL 路径：]** /libs/fd/cm/config/defaultApp/locale

   **[!UICONTROL 叠加位置：]** /apps/

   **[!UICONTROL 匹配节点类型：]** 已选中

1. 单击&#x200B;**[!UICONTROL 确定]**。
1. 单击 **[!UICONTROL 全部保存]**.
1. 右键单击以下文件并选择 **[!UICONTROL 复制]**:

   `/libs/fd/cm/config/defaultApp/locale/ACMExtensionsMessages.properties`

1. 右键单击 **[!UICONTROL 语言]** 文件夹，然后选择 **[!UICONTROL 粘贴]**:

   `/apps/fd/cm/config/defaultApp/locale/`

   ACMExtensionsMessages.properties文件将复制在区域设置文件夹中。

1. 要将新添加的自定义操作/按钮的标签本地化，请在 `/apps/fd/cm/config/defaultApp/locale/`.

   例如，要本地化本文中创建的自定义操作/按钮，请创建一个名为ACMExtensionsMessages_fr.properties的文件，并包含以下条目：

   `loc.letterInstance.letterreview.label=Revue De Lettre`

   同样，您也可以在此文件中添加更多属性，如工具提示和样式。

1. 单击 **[!UICONTROL 全部保存]**.

#### 重新启动Adobe资产编辑器构建基块包 {#restart-the-adobe-asset-composer-building-block-bundle}

在进行每次服务器端更改后，重新启动Adobe资产编辑器构建基块包。 在此方案中，服务器端的acmExtensionsConfig.xml和ACMExtensionsMessages.properties文件会进行编辑，因此Adobe资产编辑器构建基块包需要重新启动。

>[!NOTE]
>
>您可能需要清除浏览器缓存。

1. 转到 `https://[host]:[port]/system/console/bundles`. 如有必要，请以管理员身份登录。

1. 找到Adobe资产编辑器构建基块包。 重新启动包：单击停止，然后单击开始。

   ![Adobe资产编辑器构建基块](assets/6_assetcomposerbuildingblockbundle.png)

重新启动Adobe资产编辑器构建基块包后，自定义按钮会显示在创建通信用户界面中。 您可以在创建通信用户界面中打开信件以预览自定义按钮。

### 向按钮添加操作处理 {#add-action-handling-to-the-button}

默认情况下，“创建通信”用户界面在cm.domain.js文件中的以下位置实施了ActionHandler:

/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccr/js/cm.domain

对于自定义操作处理，请在CRX的/apps分支中创建cm.domain.js文件的叠加。

在单击操作/按钮时处理操作/按钮包括以下逻辑：

* 使新添加的操作变为可见/不可见：通过覆盖actionVisible()函数来完成。
* 启用/禁用新添加的操作：通过覆盖actionEnabled()函数来完成。
* 用户单击按钮时实际操作：通过覆盖handleAction()函数的实现来完成。

1. 转到 `https://[server]:[port]/[ContextPath]/crx/de`. 如有必要，请以管理员身份登录。

1. 在apps文件夹中，创建一个名为 `js` 在CRX的/apps分支中，其结构类似于以下文件夹：

   `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   请按照以下步骤创建文件夹：

   1. 右键单击 **[!UICONTROL js]** 文件夹，然后选择 **[!UICONTROL 覆盖节点]**:

      `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   1. 确保“覆盖节点”对话框具有以下值：

      **[!UICONTROL 路径：]** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js

      **[!UICONTROL 叠加位置：]** /apps/

      **[!UICONTROL 匹配节点类型：]** 已选中

   1. 单击&#x200B;**[!UICONTROL 确定]**。
   1. 单击 **[!UICONTROL 全部保存]**.

1. 在js文件夹中，使用用于按钮操作处理的代码创建一个名为ccrcustomization.js的文件，步骤如下：

   1. 右键单击 **[!UICONTROL js]** 文件夹，然后选择 **[!UICONTROL 创建>创建文件]**:

      `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

      将文件命名为ccrcustomization.js。

   1. 双击ccrcustomization.js文件以在CRX中将其打开。
   1. 在文件中，粘贴以下代码并单击 **[!UICONTROL 全部保存]**:

      ```
      /* for adding and handling custom actions in Extensible Toolbar.
        * One instance of handler will be created for each action.
        * CM.domain.CCRCustomActionHandler is actionHandler class.
        */
      var CCRCustomActionHandler;
          CCRCustomActionHandler = CM.domain.CCRCustomActionHandler = new Class({
              className: 'CCRCustomActionHandler',
              extend: CCRDefaultActionHandler,
              construct : function(action,model){
              }
          });
          /**
           * Called when user user click an action
           * @param extraParams additional arguments that may be passed to handler (For future use)
           */
          CCRCustomActionHandler.prototype.handleAction = function(extraParams){
              if (this.action.name == CCRCustomActionHandler.SEND_FOR_REVIEW) {
                  var sendForReview = function(){
                      var serviceName = this.action.actionConfig["serviceName"];
                      var inputParams = {};
                      inputParams["dataXML"] = this.model.iccData.data;
                      inputParams["letterId"] = this.letterVO.id;
                      inputParams["letterName"] = this.letterVO.name;
                      inputParams["mailId"] = $('#email').val();
                      /*function to invoke the LivecyleService */
                      ServiceDelegate.callJSONService(this,"lc.icc.renderlib.serviceInvoker.json","invokeProcess",[serviceName,inputParams],this.onProcessInvokeComplete,this.onProcessInvokeFail);
                      $('#ccraction').modal("hide");
                  }
                  if($('#ccraction').length == 0){
                      /*For first click adding popup & setting letterName.*/
                      $("body").append(popUp);
                      $("input[id*='letterName']").val(this.letterVO.name);   
                      $(document).on('click',"#submitLetter",$.proxy( sendForReview, this ));
                  }
                  $('#ccraction').modal("show");
              }
          };
          /**
           * Should the action be enabled in toolbar
           * @param extraParams additional arguements that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
         CCRCustomActionHandler.prototype.actionEnabled = function(extraParams){
                  /*can be customized as per user requirement*/
                  return true;
          };
          /**
           * Should the action be visible in toolbar
           * @param extraParams additional arguments that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
          CCRCustomActionHandler.prototype.actionVisible = function(extraParams){
              /*Check can be enabled for Non-Preview Mode.*/
              return true;
          };
          /*SuccessHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeComplete = function(response) {
              ErrorHandler.showSuccess("Letter Sent for Review");
          };
          /*FaultHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeFail = function(event) {
              ErrorHandler.showError(event.message);
          };
          CCRCustomActionHandler.SEND_FOR_REVIEW  = "Letter Review";
      /*For PopUp*/
          var popUp = '<div class="modal fade" id="ccraction" tabindex="-1" role="dialog" aria-hidden="true">'+
          '<div class="modal-dialog modal-sm">'+
              '<div class="modal-content">' +
                  '<div class="modal-header">'+
                      '<button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>'+
                      '<h4 class="modal-title"> Send Review </h4>'+
                  '</div>'+
                  '<div class="modal-body">'+
                      '<form>'+
                          '<div class="form-group">'+
                              '<label class="control-label">Email Id</label>'+
                              '<input type="text" class="form-control" id="email">'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<label  class="control-label">Letter Name</label>'+
                              '<input id="letterName" type="text" class="form-control" readonly>'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<input id="letterData" type="text" class="form-control hide" readonly>'+
                          '</div>'+
                      '</form>'+
                  '</div>'+
                  '<div class="modal-footer">'+
                     '<button type="button" class="btn btn-default" data-dismiss="modal"> Cancel </button>'+
                     '<button type="button" class="btn btn-primary" id="submitLetter"> Submit </button>'+
                  '</div>'+
              '</div>'+
          '</div>'+
      '</div>';
      ```

### 添加LiveCycle进程以启用操作 <span class="acrolinxCursorMarker"></span>处理 {#add-the-livecycle-process-to-enable-action-span-class-acrolinxcursormarker-span-handling}

在此方案中，请启用以下组件，这些组件是附加的components.zip文件的一部分：

* DSC组件罐(`DSCSample.jar`)
* 发送信函以供审核流程LCA(`SendLetterForReview.lca`)

下载并解压缩 `components.zip` 要获取的文件 `DSCSample.jar` 和 `SendLetterForReview.lca` 文件。 按照以下过程中指定的使用这些文件。

[获取文件](assets/components.zip)

#### 配置LiveCycle服务器以运行LCA进程 {#configure-the-livecycle-server-to-run-the-lca-process}

>[!NOTE]
>
>仅当您处于“ OSGI设置中，并且要实施的自定义类型需要LC集成时，才需要执行此步骤。

LCA进程在LiveCycle服务器上运行，需要服务器地址和登录凭据。

1. 转到 `https://[server]:[port]/system/console/configMgr` 和以管理员身份登录。
1. 找到AdobeLiveCycle客户端SDK配置，然后单击 **[!UICONTROL 编辑]** （编辑图标）。 此时将打开“配置”面板。

1. 输入以下详细信息并单击 **[!UICONTROL 保存]**:

   * **[!UICONTROL 服务器Url]**:操作处理程序代码使用的Send For Review服务的LC服务器的URL。
   * **[!UICONTROL 用户名]**:LC服务器的管理员用户名
   * **[!UICONTROL 密码]**:管理员用户名的密码

   ![AdobeLiveCycle客户端SDK配置](assets/3_clientsdkconfiguration.png)

#### 安装LiveCycle存档(LCA) {#install-livecycle-archive-lca}

启用电子邮件服务流程所需的LiveCycle流程。

>[!NOTE]
>
>要查看此流程的功能或创建您自己的类似流程，您需要Workbench。

1. 以管理员身份登录到Livecycle Server adminui( `https:/[lc server]/:[lc port]/adminui`.

1. 导航到 **[!UICONTROL 首页>服务>应用程序和服务>应用程序管理]**.

1. 如果SendLetterForReview应用程序已存在，请跳过此过程中的其余步骤，否则请继续执行后续步骤。

   ![UI中的SendLetterForReview应用程序](assets/12_applicationmanagementlc.png)

1. 单击 **[!UICONTROL 导入]**.

1. 单击 **[!UICONTROL 选择文件]** 选择 **[!UICONTROL SendLetterForReview.lca]**.

   ![选择SendLetterForReview.lca文件](assets/14_sendletterforreview_lca.png)

1. 单击 **[!UICONTROL 预览]**.

1. 选择 **[!UICONTROL 在导入完成后将资产部署到运行时]**.

1. 单击 **[!UICONTROL 导入]**.

#### 将ServiceName添加到列入允许列表的服务列表 {#adding-servicename-to-the-allowlisted-service-list}

在AEM服务器中提及要访问AEM服务器的LiveCycle服务。

1. 以管理员身份登录到 `https:/[host]/:[port]/system/console/configMgr`.

1. 找到并单击 **[!UICONTROL AdobeLiveCycle客户端SDK配置]**. 出现“AdobeLiveCycle客户端SDK配置”面板。
1. 在“服务名称”列表中，单击+图标，然后添加服务名称 **[!UICONTROL SendLetterForReview/SendLetterForReviewProcess]**.

1. 单击“**[!UICONTROL 保存]**”。

#### 配置电子邮件服务 {#configure-the-email-service}

在此方案中，为使通信管理能够发送电子邮件，请在LiveCycle服务器中配置电子邮件服务。

1. 使用管理员凭据登录到Livecycle Server adminui() `https:/[lc server]:[lc port]/adminui`.

1. 导航到 **[!UICONTROL 首页>服务>应用程序和服务>服务管理]**.

1. 找到并单击 **[!UICONTROL EmailService]**.

1. 在 **[!UICONTROL SMTP主机]**，配置电子邮件服务。

1. 单击“**[!UICONTROL 保存]**”。

#### 配置DSC服务 {#configure-the-dsc-service}

要使用通信管理API，请下载 `DSCSample.jar` (作为 `components.zip`)并将其上传到LiveCycle服务器。 在 `DSCSample.jar` 文件上传到LiveCycle服务器时，AEM服务器会使用 `DSCSample.jar` 用于访问renderLetter API的文件。

有关更多信息，请参阅 [将AEM Forms与AdobeLiveCycle](/help/forms/using/aem-livecycle-connector.md).

1. 在的cmsa.properties中更新AEM服务器URL `DSCSample.jar`，其位置如下：

   DSCSample.jar\com\adobe\livecycle\cmsa.properties

1. 在配置文件中提供以下参数：

   * **crx.serverUrl**=https:/[主机]/:[端口]/[上下文路径]/[AEM URL]
   * **crx.username**= AEM用户名
   * **crx.password**= AEM密码
   * **crx.appRoot**=/content/apps/cm

   >[!NOTE]
   >
   >每次在服务器端进行任何更改时，请重新启动服务器。

   的 `DSCSample.jar` 文件使用 `renderLetter` API。 有关renderLetter API的更多信息，请参阅 [接口LetterRenderService](https://helpx.adobe.com/aem-forms/6-2/javadocs/com/adobe/icc/ddg/api/LetterRenderService.html).

#### 在JEE上将DSC导入AEM Forms {#import-dsc-to-livecyle}

`DSCSample.jar` 文件使用 `renderLetter` 用于将信件呈现为PDF字节的XML数据（C提供作为输入）的API。 有关renderLetter和其他API的更多信息，请参阅 [信件呈现服务](https://helpx.adobe.com/aem-forms/6-2/javadocs/com/adobe/icc/ddg/api/LetterRenderService.html).

1. 启动Workbench并登录。
1. 选择 **[!UICONTROL 窗口>显示视图>组件]**. 将“组件”视图添加到Workbench ES2。

1. 右键单击 **[!UICONTROL 组件]** 选择 **[!UICONTROL 安装组件]**.

1. 选择 `DSCSample.jar` 文件，然后单击 **[!UICONTROL 打开]**.
1. 右键单击 **[!UICONTROL RenderWrapper]** 选择 **[!UICONTROL 启动组件]**. 如果组件启动，则组件名称旁边会显示一个绿色箭头。

## 发送信件供审阅 {#send-letter-for-review}

在配置了用于发送信件以供审阅的操作和按钮后：

1. 清除浏览器缓存。

1. 在创建通信UI中，单击 **[!UICONTROL 信件审阅]** 并指定审阅人的电子邮件ID。

1. 单击 **[!UICONTROL 提交]**.

![sendreview](assets/sendreview.png)

审阅人从系统收到一封电子邮件，信件作为PDF附件。
