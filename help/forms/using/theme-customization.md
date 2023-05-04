---
title: 主题自定义
seo-title: Theme Customization
description: 如何自定义AEM Forms应用程序的主题。
seo-description: How to customize the theme of your AEM Forms app.
uuid: 36632e67-1cc6-416d-ae80-d84bbabab4bd
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: c72f608e-052a-4bf9-b7bc-ddf57483af35
exl-id: fb1e0bec-c943-4468-920d-8ef360a01365
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 2%

---

# 主题自定义 {#theme-customization}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以自定义HTML代码和CSS文件，以便为AEM Forms应用程序提供特定于组织的不同外观。 例如，您可以更改任务的背景颜色和高度或“起点”。 以下示例提供了更改说明：

* 显示说明代替说明
* 显示路由数
* 背景渐变颜色

## 步骤 {#steps}

1. 打开您的项目。

   * 对于iOS，打开 `Capture.xcodeproj` 在Xcode中
   * 对于Android，在Eclipse中打开Android项目。
   * 对于Windows，打开 `MWSWindows.sln` 在Visual Studio中。

1. 导航到模板文件夹。

   * 在Xcode中，导航到 **Capture > www > wsmobile > js > runtime > templates** 文件夹。
   * 在Eclipse中，导航到 **资产> www > wmobile > js >运行时>模板** 文件夹。
   * 在Visual Studio中，导航到 **MWSWindows > www > wsmobile > js >运行时>模板** 文件夹。

1. 打开 `template.html` 文件进行编辑。
1. 找到以下字符串：

   ```
   <%if ( (task.description !== "") && (task.description !== null) && (typeof task.description !== null) && (typeof task.description !== 'undefined') ) {%>
                  <div class="description_details">
                    <%= task.description %>
                  </div>
                 <%} else 
   ```

   将其替换为 `<%`.

1. 在 `template.html` 文件：

   ```
   <ul id="task_menu_list">
                                   <li class="approve" title="<%= task.availableCommands.directCommands[0]%>" data-routename="<%= task.availableCommands.directCommands[0]%>">
                                       <%= task.availableCommands.directCommands[0]%>
                                   </li>
                                   <li class="reject last" title="<%= task.availableCommands.directCommands[1]%>" data-routename="<%= task.availableCommands.directCommands[1]%>">
                                       <%= task.availableCommands.directCommands[1]%>
                                   </li>
   ```

1. 注释以下行并保存文件。

   ```
   task.availableCommands.directCommands[1]%>">
   <%= task.availableCommands.directCommands[1]%>
   </li>
   ```

1. 导航到css文件夹。

   * 在Xcode中，导航到 **Capture > www > wsmobile > css**.
   * 在Eclipse中，导航到 **资产> www > wmobile > css**.
   * 在Visual Studio中，导航到 **MWSWindows > www > wsmobile > css**.

1. 打开 `_style.css` 文件进行编辑。
1. 对于背景图像，请更改 `#323232` to `#fff`.
1. 保存更改并关闭 `_style.css` 文件。
1. 打开AEM Forms应用程序。

   AEM Forms应用程序现在显示说明而不是描述。
