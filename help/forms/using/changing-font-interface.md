---
title: 更改界面上的字体
seo-title: Changing the font on the interface
description: 如何有选择地更改用户界面上的字体。
seo-description: How to change the fonts on the user interface selectively.
uuid: d079f656-76f8-4908-9989-dde79e215eb2
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: 487e3966-443a-408e-b5af-899fcba6fca6
exl-id: bd7ec9d6-b1d2-4f01-8cef-05e5e1eceda1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 3%

---

# 更改界面上的字体 {#changing-the-font-on-the-interface}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

您可以更改在AEM Forms工作区中显示的字体。 在用户界面的特定部分中使用的字体在样式表的相应部分中定义。 您可以选择性地更改用户界面上的字体。

关注 [AEM Forms工作区自定义的一般步骤](/help/forms/using/generic-steps-html-workspace-customization.md) 并根据您的要求，按照自定义CSS和/或HTML的步骤操作。

1. 更改或添加现有样式的字体系列。
1. 更改或添加HTML元素的内嵌字体系列。
1. 添加样式并将其用于HTML元素。

例如，要将顶部导航栏锚点文本的字体更改为Courier New，请执行以下步骤：

1. 通过访问以登录CRXDE Lite `https://[server]:[port]/lc/crx/de/index.jsp`.
1. 执行下列操作之一：

   1. 要更改现有样式的字体系列，请在/apps/ws/css的newStyle.css文件中添加以下内容。

      ```css
      #topnav a {
         font-family: "Courier New";
      }
      ```

   1. 要为HTML元素添加内嵌的字体系列，请复制 `/libs/ws/js/runtime/templates/appnavigation.html` 文件到 `/apps/ws/js/runtime/templates/appnavigation.html`.

      按如下方式更新/apps/ws/js/runtime/templates/appnavigation.html文件：

      ```
      <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
      <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.todo.name')%></a></li>
      <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
      <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" style="font-family:Courier New;" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
      ```

      打开/apps/ws/js/registry.js文件进行编辑和替换 `text!/lc/libs/ws/js/runtime/templates/appnavigation.html` with `text!/lc/apps/ws/js/runtime/templates/appnavigation.html`.

   1. 要添加定义font-family的样式，请在/apps/ws/css的newStyle.css文件中添加以下内容。

      ```css
      .myNewFontStyle a {
         font-family: "Courier New";
      }
      ```

      要为HTML元素添加内联的字体系列，请在apps/ws/js/runtime/templates的appnavigation.html文件中添加以下内容。

      ```css
      <div id="topnav" class="myNewFontStyle">
          <ul>
              <li class="process"><a href="#" title="<%= $.t('index.header.topnav.startprocess.detail')%>" ><%= $.t('index.header.topnav.startprocess.name')%></a></li>
              <li class="todo"><a href="#/todo" title="<%= $.t('index.header.topnav.todo.detail')%>"><%= $.t('index.header.topnav.todo.name')%></a></li>
              <li class="track"><a href="#/tracking" title="<%= $.t('index.header.topnav.tracking.detail')%>" ><%= $.t('index.header.topnav.tracking.name')%></a></li>
              <li class="preference"><a href="#/preferences" title="<%= $.t('index.header.topnav.preferences.detail')%>" ><%= $.t('index.header.topnav.preferences.name')%></a></li>
          </ul>
      </div>
      ```

1. 重新启动工作区并清除浏览器缓存，以使更改可见。

![change_font_before](assets/change_font_before.png)
**图：** *字体自定义前的顶部导航栏*

![change_font_after](assets/change_font_after.png)
**图：** *自定义第一个选项卡的字体后显示顶部导航栏*
