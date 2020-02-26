---
title: 将AEM表单工作区与Microsoft Office SharePoint server集成
seo-title: 将AEM表单工作区与Microsoft Office SharePoint server集成
description: '您可以将AEM表单工作区与Microsoft Office SharePoint server集成。 '
seo-description: '您可以将AEM表单工作区与Microsoft Office SharePoint server集成。 '
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
translation-type: tm+mt
source-git-commit: 8cbfa421443e62c0483756e9d5812bc987a9f91d

---


# 将AEM表单工作区与Microsoft Office SharePoint server集成 {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

**-要求**

**必备知识**&#x200B;在将AEM Forms Workspace添加到SharePoint server之前，您必须具有相应权限才能访问SharePoint Server，并且必须知道要访问Workspace的URL。 以下步骤假定您已熟悉SharePoint Server。 有关SharePoint server中Web部件的详细信息，请参阅Windows SharePoint services中的Web部件。

**用户级开**&#x200B;始

您可以在Microsoft Office sharePoint Server（例如，Microsoft Office SharePoint Server 2007）中将AEM Forms Workspace用作Web部件。 用户可以使用Web浏览器连接到SharePoint Server，以提供统一的体验，从而访问AEM Forms Workspace。 在本文中，您将学习在Microsoft Office SharePoint server中将AEM Forms Workspace显示为Web部件的基本步骤。 您可以执行本文中所述的步骤以提供统一的体验，以便连接到SharePoint服务器的用户可以从同一端口访问AEM Forms Workspace。

>[!NOTE]
>
>本文中列出的步骤是特定的Microsoft SharePoint Server 2007。 您还可以使用其他支持的Microsoft sharePoint版本配置HTML Workspace。

## 将AEM Forms Workspace与Microsoft Office SharePoint Server 2007集成 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

执行以下步骤将AEM Forms Workspace集成到Web部件中：

1. 在Web浏览器中，导航到SharePoint站点，如https://*[myMOSSserver]:*44299/default.aspx，其中 *[myMOSSserver]* 是Sharepoint服务器的名称或IP地址。

   >[!NOTE]
   >
   >44299是SharePoint服务器的默认端口号。 端口号取决于SharePoint server的安装。

1. 在网页的右上侧，单击“站点操作” **并选择** “编辑 **页面”**。
1. 单击“ **添加Web部件** ”按钮。
1. 在“添加Web部件——网页对话框”对话框的“其他”下，选择“页面查看器 **Web部件”** ，然后单击“添 **加”**。
1. 在“页面查看器Web部件”框中，单击“编辑” **** ，然后选 **择“修改共享Web部件”**。

   >[!NOTE]
   >
   >“页面查看器Web部件”(Page Viewer Web Part)框出现在您在步骤3中单击的“添加Web部件 **”(Add a Web Part** )按钮下，如下图所示（图1）:

   ![Microsoft Office sharePoint服务器中的“页面查看器Web部件”框。](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **** 图：Microsoft *Office sharePoint服务器中的“页面查看器Web部件”框。*

1. 在“页面查看器”页面上，执行以下任务：

   1. 在“链接”框中，键入AEM Forms Workspace的URL，如https://*[AEM_forms_Server]:*8080/lc/ws，其中 *[AEM_forms_Server]* 表示AEM表单服务器的IP或名称。
   1. 单击 **“外观** ”并修改高度、宽度和标题，以便您能够看到整个Workspace用户界面。 例如，可以将高度和宽度分别设置为6英寸和11英寸。
   1. 单击“ **测试链接**”。 将出现一个新的Web浏览器窗口，其中显示工作区。
   1. （可选）单击“ **布局** ”，并修改Web部件中工作区的布局。
   1. （可选）单击“ **高级** ”(Advanced)并修改其他设置，如说明以及工作区在Web部件中是可以最小化还是关闭。

      单击“ **应用**”。

1. 单击 **退出编辑模式** ，并验证是否可以访问工作区。

完成上述步骤后，您的SharePoint站点的外观与下图类似（图2）:

![与Microsoft Office SharePoint server集成的AEM Forms Workspace](assets/aem-forms-workspace.jpg)

**** 图：与 *Microsoft Office SharePoint server集成的AEM Forms Workspace*

