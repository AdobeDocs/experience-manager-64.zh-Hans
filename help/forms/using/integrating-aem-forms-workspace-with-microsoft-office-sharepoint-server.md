---
title: 将AEM Forms工作区与Microsoft Office SharePoint服务器集成
seo-title: Integrating AEM forms workspace with Microsoft Office SharePoint Server
description: 您可以将AEM Forms工作区与Microsoft Office SharePoint Server集成。
seo-description: You can integrate AEM forms workspace with Microsoft Office SharePoint Server.
uuid: d43396d4-117f-47ea-91e4-10ee96107bc8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: 1bada670-3e0e-40f4-b9be-8b090df910be
exl-id: 43149456-8ff8-4ce1-9c51-1d950f60ff5d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 1%

---

# 将AEM Forms工作区与Microsoft Office SharePoint服务器集成 {#integrating-aem-forms-workspace-with-microsoft-office-sharepoint-server}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

**- 要求**

**先决知识**
在将AEM Forms Workspace添加到SharePoint Server之前，您必须拥有对SharePoint Server的访问权限，并且您必须知道用于访问Workspace的URL。 以下步骤假定您熟悉SharePoint Server。 有关SharePoint Server中Web部件的更多信息，请参阅Windows SharePoint Services中的Web部件。

**用户级别**
开始

您可以在Microsoft Office SharePoint Server中将AEM Forms Workspace用作Web部件(例如，Microsoft Office SharePoint Server 2007)。 用户可以使用Web浏览器连接到SharePoint Server，以提供统一的体验，从而访问AEM Forms工作区。 在本文中，您将了解在AEM Forms Office SharePoint Server中将Microsoft Workspace显示为Web部件的基本步骤。 您可以执行本文中描述的步骤来提供统一的体验，以便连接到SharePoint服务器的用户可以从同一端口访问AEM Forms Workspace。

>[!NOTE]
>
>本文中列出的步骤是特定的Microsoft SharePoint Server 2007。 您还可以使用其他受支持的Microsoft SharePoint版本配置HTML工作区。

## 将AEM Forms工作区与Microsoft Office SharePoint Server 2007集成 {#integrate-aem-forms-workspace-with-microsoft-office-sharepoint-server}

执行以下步骤将AEM Forms Workspace集成到Web部件中：

1. 在Web浏览器中，导航到SharePoint网站，如https://*[myMOSSserver]:*44299/default.aspx其中 *[myMOSSserver]* 是Sharepoint服务器的名称或IP地址。

   >[!NOTE]
   >
   >44299是SharePoint服务器的默认端口号。 端口号取决于您安装的SharePoint Server。

1. 在网页的右上方，单击 **网站操作** 选择 **编辑页面**.
1. 单击 **添加Web部件** 按钮。
1. 在“添加Web部件 — 网页”对话框的“其他”下，选择 **页面查看器Web部件** 然后单击 **添加**.
1. 在“页面查看器Web部件”(Page Viewer Web Part)框中，单击 **编辑** 选择 **修改共享Web部件**.

   >[!NOTE]
   >
   >“页面查看器Web部件”(Page Viewer Web Part)框显示在 **添加Web部件** 按钮（如下图1所示）：

   ![Microsoft Office SharePoint服务器中的“页面查看器Web部件”框。](assets/page-viewer-web-part-box-in-microsoft-office-sharepoint-server.png)

   **图：** *Microsoft Office SharePoint服务器中的“页面查看器Web部件”框。*

1. 在“页面查看器”页面上，执行以下任务：

   1. 在“链接”框中，键入AEM Forms工作区的URL，如https://*[AEM_forms_Server]:*8080/lc/ws，其中 *[AEM_forms_Server]* 表示AEM Forms服务器的IP或名称。
   1. 单击 **外观** 并修改高度、宽度和标题，以便您能够看到整个工作区用户界面。 例如，您可以将高度和宽度分别设置为6英寸和11英寸。
   1. 单击 **测试链接**. 此时将显示一个新的Web浏览器窗口，其中会显示工作区。
   1. （可选）单击 **布局** 和修改Web部件中工作区的布局。
   1. （可选）单击 **高级** 并修改其他设置，如描述以及工作区是否可以在Web部件中最小化或关闭。

      单击 **应用**.

1. 单击 **退出编辑模式** 并验证您是否可以访问工作区。

完成上述步骤后，您的SharePoint网站将类似于下图（图2）：

![AEM Forms Workspace与Microsoft Office SharePoint Server集成](assets/aem-forms-workspace.jpg)

**图：** *AEM Forms Workspace与Microsoft Office SharePoint Server集成*
