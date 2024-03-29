---
title: 创建自定义工具栏布局
seo-title: Creating custom toolbar layout
description: 您可以为表单指定工具栏布局。 工具栏布局定义表单上工具栏的命令和布局。
seo-description: You can specify a toolbar layout for the form. The toolbar layout defines the commands and the layout of the toolbar on the form.
uuid: da60342c-f802-4264-9da4-c333df9359c2
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: c69bb229-d680-4a55-9b2d-cd5ad0f83a9e
exl-id: 1b273437-8d71-4224-bdcd-0ae522ae8913
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 1%

---

# 创建自定义工具栏布局 {#creating-custom-toolbar-layout}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 工具栏布局 {#layout}

创建自适应表单时，可以为表单指定工具栏布局。 工具栏布局定义表单上工具栏的命令和布局。

工具栏布局使用的方式严重依赖由复杂的JavaScript和CSS代码驱动的客户端处理。 组织和优化此代码的服务可能是一个复杂的问题。 为了帮助解决此问题，AEM提供了客户端库文件夹，用于将客户端代码存储在存储库中，将其组织成各个类别，并定义何时以及如何将每个类别的代码提供给客户端。 然后，客户端库系统会负责在最终网页中生成正确的链接，以加载正确的代码。 有关详细信息，请参阅 [客户端库在AEM中的工作方式。](/help/sites-developing/clientlibs.md)

![工具栏的示例布局](assets/default_toolbar_layout.png)
**图：** *工具栏的示例布局*

自适应表单提供一组现成的布局：

![现成可用的工具栏布局 ](assets/toolbar1.png)
**图：** *现成可用的工具栏布局*

此外，您还可以创建自定义工具栏布局。

以下过程详细介绍了创建自定义工具栏的步骤，该工具栏在工具栏中显示三个操作，在工具栏的下拉列表中显示其他操作。

附加的内容包包含下面描述的整个代码。 安装内容包后，打开 `/content/forms/af/CustomLayoutDemo.html` 查看自定义工具栏布局演示。

CustomToolbarLayoutDemo.zip

[获取文件](assets/customtoolbarlayoutdemo.zip)
演示自定义工具栏布局

## 创建自定义工具栏布局 {#layout-1}

1. 创建文件夹以维护自定义工具栏布局。 例如：

   `/apps/customlayout/toolbar`。

   要创建自定义布局，您可以使用（和自定义）以下文件夹中提供的一个现成工具栏布局：

   `/libs/fd/af/layouts/toolbar`

   例如，复制 `mobileFixedToolbarLayout` 节点 `/libs/fd/af/layouts/toolbar` 文件夹 `/apps/customlayout/toolbar` 文件夹。

   此外，将toolbarCommon.jsp复制到 `/apps/customlayout/toolbar` 文件夹。

   >[!NOTE]
   >
   >为维护自定义布局而创建的文件夹，可以使用 `apps` 文件夹。

1. 重命名复制的节点， `mobileFixedToolbarLayout`，更改为 `customToolbarLayout.`

   此外，还为节点提供相关描述。 例如，将节点的jcr:description更改为 **工具栏的自定义布局**.

   的 `guideComponentType` 节点的属性确定布局类型。 在这种情况下，布局类型是工具栏，因此它会显示在工具栏布局选择下拉列表中。

   ![具有相关描述的节点](assets/toolbar3.png)

   具有相关描述的节点

   您的新自定义工具栏布局显示在 **自适应表单工具栏** 对话框配置。

   ![可用工具栏布局列表](assets/toolbar4.png)

   可用工具栏布局列表

   >[!NOTE]
   >
   >在上一步中更新的描述将显示在布局下拉列表中。

1. 选择此自定义工具栏布局，然后单击确定。

   在 `/etc/customlayout` 节点，并在 `customToolbarLayout.jsp`.

   ![customToolbarLayout.css文件的路径](assets/toolbar_3.png)

   customToolbarLayout.css文件的路径

   样本 `customToolbarLayout.jsp`:

   ```php
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <cq:includeClientLib categories="customtoolbarlayout" />
   <c:if test="${isEditMode}">
           <cq:includeClientLib categories="customtoolbarlayoutauthor" />
   </c:if>
   <div class="guidetoolbar mobileToolbar mobilecustomToolbar" data-guide-position-class="guide-element-hide">
       <div data-guide-scroll-indicator="true"></div>            
       <%@include file="../toolbarCommon.jsp" %>
   </div>
   ```

   >[!NOTE]
   >
   >为布局添加指南工具栏类。 工具栏的现成样式是针对指导工具栏类定义的。

   样本 `toolBarCommon.jsp`:

   ```php
   <%@taglib prefix="fn" uri="https://java.sun.com/jsp/jstl/functions"%>
   <%--------------------  
   This code iterates over all the tool bar items using the guideToolbar bean.
   If the number of toolbar items are more than 3, then we create a dropdown menu using bootstrap for other actions present in the toolbar.
   In both desktop and mobile devices, the layout is different.    
   ---------------------------------%>
   
   <c:forEach items="${guideToolbar.items}" var="toolbarItem" varStatus="loop">
       <c:choose>
         <c:when test="${loop.index gt 2}">
      <c:choose>
       <c:when test="${loop.index eq 3}">
                     <div class="btn-group dropdown">   
                       <button type="button" class="btn btn-primary dropdown-toggle label" data-toggle="dropdown">Actions <span class="caret"></span></button>
                       <button type="button" class="btn btn-primary dropdown-toggle icon" data-toggle="dropdown"><span class="glyphicon glyphicon-th-list"></span></button>
             <ul class="dropdown-menu" role="menu">
                           <li>
                               <div id="${toolbarItem.id}_guide-item">
                                 <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
                              </div>
                           </li>
                           <c:if test="${loop.index eq (fn:length(guideToolbar.items)-1)}">
                                </ul>
                                </div>
                           </c:if>
       </c:when>
       <c:when test="${loop.index eq (fn:length(guideToolbar.items)-1)}">
                          <li>
                                     <div id="${toolbarItem.id}_guide-item">
                                         <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
                                     </div>
                           </li>
                       </ul>
                     </div>
   
       </c:when>
       <c:otherwise>
         <li>
          <div id="${toolbarItem.id}_guide-item">
           <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
          </div>
         </li>
       </c:otherwise>
      </c:choose>
         </c:when>
         <c:otherwise>         
     <div id="${toolbarItem.id}_guide-item">
           <sling:include path="${toolbarItem.path}" resourceType="${toolbarItem.resourceType}"/>
        </div>
         </c:otherwise>
    </c:choose>   
   </c:forEach>
   ```

   clientlib节点内存在的CSS:

   ```css
   .mobilecustomToolbar .dropdown {
       display: inline-block;    
   }
   
   .mobilecustomToolbar .dropdown {
       float: right;   
   }
   
   .mobilecustomToolbar .dropdown > button {
      padding: 6px 12px;  
   }         
   
   .mobilecustomToolbar .dropdown .guideFieldWidget, .mobilecustomToolbar .dropdown .guideFieldWidget button {
       width: 100%;   
   }         
   
   .mobilecustomToolbar .dropdown .caret{
       border-bottom: 6px solid;
       border-right: 6px solid transparent;
       border-left: 6px solid transparent;
    border-top: transparent;                                     
   }
   
   .mobilecustomToolbar .dropdown-menu{
    top: auto;
    bottom: 100%;                            
   }
   
   .mobilecustomToolbar .btn-group {            
    vertical-align: super;            
   }
   
   .mobilecustomToolbar .glyphicon {
    font-size: 24px;
   }
   
   @media (max-width: 767px){                                       
   
    .mobilecustomToolbar .dropdown .guideButton .iconButton-icon {
      display: none;
       }  
   
       .mobilecustomToolbar .dropdown .guideButton .iconButton-label {
      display: inline-block;
       } 
   
       .mobilecustomToolbar .dropdown .guideButton button {
      background-color: #013853;
       }
   
    .mobilecustomToolbar .btn-group {            
     vertical-align: top;            
    }    
   
   }
   ```

>[!NOTE]
>
>在上一步中更新的描述将显示在布局下拉列表中。

![自定义布局工具栏的桌面视图](assets/toolbar_1.png)
**图：** *自定义布局工具栏的桌面视图*
