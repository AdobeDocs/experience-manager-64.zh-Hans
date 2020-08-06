---
title: 生成XDP表单的HTML5预览
seo-title: 生成XDP表单的HTML5预览
description: 预览设计器中的“LiveCycleHTML”选项卡可用于预览表单，就像表单在浏览器中显示一样。
seo-description: 预览设计器中的“LiveCycleHTML”选项卡可用于预览表单，就像表单在浏览器中显示一样。
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
translation-type: tm+mt
source-git-commit: 801941c060e1a912f3969bca1e89962241e7fbe0
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---


# 生成XDP表单的HTML5预览 {#generate-html-preview-of-an-xdp-form}

在AEM Forms设计器中设计表单时，除了预览表单的PDF再现外，您还可以预览表单的HTML5再现。 您可以使用“ **预览** ”HTML选项卡预览表单，就像在浏览器中一样。

## 在设计器中为XDP表单启用HTML预览 {#html-preview-of-forms-in-forms-designer}

要使设计人员能够生成XDP表单的HTML预览，请执行以下配置：

* 配置Apache Sling Authentication Service
* 禁用保护模式
* 提供AEM Forms服务器的详细信息

### 配置Apache Sling Authentication Service {#configure-apache-sling-authentication-service}

1. 转到AEM Forms `https://[server]:[port]/system/console/configMgr` 在OSGi上运行，或

   `https://[server]:[port]/lc/system/console/configMgr` AEM Forms在JEE上跑。

1. 找到并单 **击Apache Sling Authentication Service** （Apache Sling身份验证服务）配置，以在编辑模式下打开它。

1. 根据您是在OSGi还是JEE上运行AEM Forms，在“身份验证要求”字 **段中添加** :

   * AEM FormsJEE

      * -/content/xfaforms
      * -/etc/clientlibs
   * AEM FormsOSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >请勿复制粘贴“身份验证要求”字段中的指定值，因为它可能损坏该值中的特殊字符。 而是在字段中键入指定的值。

1. 在“匿名用户名”和“匿名 **[!UICONTROL 用户密码]** ”字 **[!UICONTROL 段中分别指定用]** 户名和密码。 指定的凭据用于处理匿名身份验证并允许匿名用户访问。
1. Click **Save** to save the configuration.

### 禁用保护模式 {#disable-protected-mode}

默认 [情况下](/help/forms/using/get-xdp-pdf-documents-aem.md) ，保护模式处于打开状态。 让它为生产环境启用。 您可以将其禁用，以在设计师中预览HTML5Forms。 请执行以下步骤以禁用它：

1. 以管理员身份登录到AEM Web Console。

   * OSGi上的AEM Forms的URL `https://[server]:[port]/system/console/configMgr`
   * JEE上的AEM Forms的URL是 `https://[server]:[port]/lc/system/console/configMgr`

1. 打开 **[!UICONTROL 移动Forms配置]** ，进行编辑。
1. 取消选择“ **[!UICONTROL 保护模式]** ”选项，然后单 **[!UICONTROL 击“保存]**”。

### 提供AEM Forms服务器的详细信息 {#provide-details-of-aem-forms-server}

1. 在设计器中，转到“工 **具** ”> **“选项**”。
1. 在“选项”窗口中，选 **择“服务器** 选项”页，提供以下详细信息，然后单 **击“确定”**。

   * **服务器URL**: AEM Forms服务器URL。
   * **HTTP端口号**: AEM服务器端口。 默认值为 4502。
   * **HTML预览上下文：** 呈现XFA表单的用户档案路径。 以下默认用户档案用于在设计器中预览表单。 但是，您也可以指定自定义用户档案的路径。

      * `/content/xfaforms/profiles/default.html` (AEM FormsOSGi)
      * `/lc/content/xfaforms/profiles/default.html` (AEM FormsJEE)
   * **Forms经理背景：** 部署Forms管理器UI的上下文路径。 默认值为：

      * `/aem/forms` (AEM FormsOSGi)
      * `/lc/forms` (AEM FormsJEE)

   **注意：** *确保AEM Forms服务器已启动并运行。 HTML预览连接到CRX服务器以*&#x200B;生成&#x200B;*预览。*

   ![AEM Forms设计师选项 ](assets/server_options.png)

   AEM Forms设计师选项

1. 要预览HTML中的表单，请单击“ **预览HTML** ”选项卡。

   >[!NOTE]
   >
   >如果HTML预览选项卡已关闭，请按F4打开预览HTML选项卡。 还可以从“预览”菜单中选择“预览HTML”以打开“视图HTML”选项卡。

   >[!NOTE]
   >
   >HTML预览不支持PDF文档,HTML预览仅用于XDP文档。

## 使用示例预览表单 {#to-preview-a-form-using-sample-data}

Designer允许您使用范例XML数据预览和测试表单。 建议您经常使用示例数据测试表单，以确保表单正确呈现。

如果您没有示例数据，设计人员可以创建它，您也可以自己创建它。 (请参 [阅自动生成预览表单的示例数据](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) , [以及创建预览表单的示例数据](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2)。)

使用示例数据源测试表单可确保映射数据和字段，并确保重复的子表单按您期望的方式重复。 您可以创建平衡的表单布局，为每个对象提供显示合并数据的适当空间。

1. 选择“ **文件”>“表单属性**”。

1. 单击 **预览** 选项卡，在“数据文件”框中，键入测试数据文件的完整路径。 您还可以使用“浏览”按钮导航到文件。

1. 单击&#x200B;**确定**。下次在“预览HTML”选项卡中 **预览表单** 时，示例XML文件中的数据值将出现在相应的对象中。

## 预览库中的表单 {#html-preview-of-forms-in-forms-manager}

在AEM Forms，您可以预览存储库中的表单和文档。 预览有助于准确了解表单的外观和行为，就像最终用户一样。

[**联系支持&#x200B;**](https://www.adobe.com/account/sign-in.supportportal.html)
