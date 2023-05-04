---
title: 触屏 UI 功能状态
seo-title: Touch UI Feature Status
description: 特定于Adobe Experience Manager 6.3触屏UI的发行说明。
seo-description: Release notes specific to Adobe Experience Manager 6.3 Touch UI.
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
exl-id: e1422581-143b-4fce-976e-e5aa3360e2d0
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 15%

---

# 触屏 UI 功能状态 {#touch-ui-feature-status}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

>[!CAUTION]
>
>对于版本6.4的AEM, [已弃用经典UI](/help/release-notes/deprecated-removed-features.md). Adobe不打算进一步增强经典UI，同时鼓励用户利用触屏UI下提供的强大新功能。

从版本6.0开始， AEM引入了称为“触屏优化UI”（也称为“触屏优化UI”）的新用户界面，该界面与Adobe Marketing Cloud和整个Adobe用户界面准则保持一致。 由于几乎达到了功能部分，这已成为AEM中的标准UI，该界面采用了以桌面为导向的旧版界面，称为“经典UI”。

虽然触屏优化UI中存在大多数功能，但仍有一些功能尚未完整，且将在未来版本中添加。

以下列表显示了在AEM 6.4中实施的功能的当前状态。

有关升级到AEM 6.4的客户的建议，请参阅 [面向客户的用户界面Recommendations](/help/sites-deploying/ui-recommendations.md) 以了解详细信息。

>[!NOTE]
>
>请注意，本页仅包含与经典UI的功能对等性。
>
>在触屏优化UI中添加的功能和唯一功能在经典UI中不存在。

>[!NOTE]
>
>此列表力求完成，但不应视为详尽无遗。

## 图例 {#legend}

* **完成**:该功能在触屏UI中完全可用
* **大部分**:该功能在触屏UI中大多可用。
* **缺少**:触屏优化UI中不存在该功能，必须使用经典UI才能执行此操作。
* **已更换**:该功能已被替换为新实施（其工作方式不同）。
* **已删除**:触屏优化UI中不再存在该功能，也不会被替换。

## 功能状态：站点管理员 {#feature-status-sites-admin}

这是经典UI站点管理( `/siteadmin`)在触屏优化UI( `/sites.html`)。

<table> 
 <tbody>
  <tr>
   <td><strong>专题<br /> </strong></td> 
   <td><strong>状态<br /> </strong></td> 
   <td><strong>注释</strong></td> 
  </tr>
  <tr>
   <td>导航网站层次结构</td> 
   <td>完成<br /> </td> 
   <td>AEM 6.4引入了 <a href="/help/sites-authoring/basic-handling.md#content-tree">内容树视图</a>.</td> 
  </tr>
  <tr>
   <td>启动工作流</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>创建新页面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>创建新站点</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>创建新启动项</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>创建新Live Copy <br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>创建文件夹</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>显示发布状态</td> 
   <td>大部分</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>搜索</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>复制/粘贴页面（复制）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>移动页面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>发布页面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>没有复制权限的发布页面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>稍后发布</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>发布树</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消发布页面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消发布页面（不具有复制权限）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>稍后取消发布</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>删除</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>锁定/解锁</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>查看/编辑属性</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>在页面上设置权限</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>版本历史记录</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>还原版本</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>恢复树并恢复已删除的页面</td> 
   <td>缺少</td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>显示旧版本与当前版本之间的差异<br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Live Copy操作（转出）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>请参阅语言副本</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>查找并替换</td> 
   <td>缺少<br /> </td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>通知收件箱（JCR事件）</td> 
   <td>缺少</td> 
   <td>使用经典UI。 将替换为不同的实施。</td> 
  </tr>
  <tr>
   <td>引用</td> 
   <td>大部分</td> 
   <td>传入页面链接的显示将在2019版AEM中添加。</td> 
  </tr>
 </tbody>
</table>

## 功能状态：页面编辑器 {#feature-status-page-editor}

这是经典UI页面编辑器( `/cf#`)具有，且状态在触屏启用( `/editor.html`)。

<table> 
 <tbody>
  <tr>
   <td><strong>专题</strong></td> 
   <td><strong>状态</strong></td> 
   <td><strong>注释</strong></td> 
  </tr>
  <tr>
   <td>编辑网页</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑移动网页<br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑通过设计导入程序导入的内容<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑电子邮件</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑移动设备应用程序</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑Forms</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑选件</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑工作流模型<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>代码：编辑和预览</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>响应式预览<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：编辑设计</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：基架</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>模式：Live Copy状态<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>添加注释</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑属性<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>转出页面</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>开始和显示工作流</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>工作流包处理</td> 
   <td>大部分</td> 
   <td>在触屏UI中完全可访问。 经典UI中仍显示多个工作流有效负载。<br /> </td> 
  </tr>
  <tr>
   <td>锁定/解锁页面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>发布页面 <br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>取消发布页面</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>复制页面</td> 
   <td>已删除<br /> </td> 
   <td>使用站点管理员 <a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">复制页面</a>.<br /> </td> 
  </tr>
  <tr>
   <td>移动页面</td> 
   <td>已删除</td> 
   <td>使用站点管理员 <a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">移动页面</a>.<br /> </td> 
  </tr>
  <tr>
   <td>删除页面</td> 
   <td>已删除</td> 
   <td>使用站点管理员 <a href="/help/sites-authoring/managing-pages.md#deleting-a-page">删除页面</a>.<br /> </td> 
  </tr>
  <tr>
   <td>显示引用</td> 
   <td>已删除</td> 
   <td>使用站点管理员 <a href="/help/sites-authoring/author-environment-tools.md#references">请参阅详细的参考列表</a>.<br /> </td> 
  </tr>
  <tr>
   <td>审查日志</td> 
   <td>已删除</td> 
   <td>使用站点管理员和 <a href="/help/sites-authoring/author-environment-tools.md#events-timeline">打开活动边栏</a>.<br /> </td> 
  </tr>
  <tr>
   <td>创建版本</td> 
   <td>已删除</td> 
   <td>使用站点管理员 <a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">创建新版本</a>.<br /> </td> 
  </tr>
  <tr>
   <td>恢复版本</td> 
   <td>已删除</td> 
   <td>使用站点管理员 <a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">恢复版本</a>.</td> 
  </tr>
  <tr>
   <td>切换启动项</td> 
   <td>已删除</td> 
   <td>使用站点管理员 <a href="/help/sites-authoring/launches-promoting.md">在启动项之间切换</a>.<br /> </td> 
  </tr>
  <tr>
   <td>翻译页面</td> 
   <td>已删除</td> 
   <td>使用站点管理员 <a href="/help/sites-administering/tc-manage.md">将页面添加到翻译项目</a>.<br /> </td> 
  </tr>
  <tr>
   <td>时间扭曲（选择日期/时间，然后按照所查看的内容浏览网站）<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>设置权限</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Client Context UI<br /> </td> 
   <td>已更换</td> 
   <td>使用 <a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> UI。</td> 
  </tr>
  <tr>
   <td>适用于各种媒体类型的内容查找器<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>组件列表</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>复制并粘贴组件<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>剪贴板中的组件列表</td> 
   <td>缺少</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>还原/重做</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>将内容拖放到组件占位符中</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>通过组件自动创建，将内容直接拖放到Parsys占位符中<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 功能状态：文本、表和图像编辑器 {#feature-status-text-table-and-image-editors}

这是经典UI文本、表和图像编辑器具有的功能列表以及触屏UI中的状态。

<table> 
 <tbody>
  <tr>
   <td><strong>专题</strong></td> 
   <td><strong>状态 </strong></td> 
   <td><strong>注释<br /> </strong></td> 
  </tr>
  <tr>
   <td>富文本编辑器</td> 
   <td>完成</td> 
   <td>可用的就地、对话框和全屏。</td> 
  </tr>
  <tr>
   <td>启用/禁用RTE插件</td> 
   <td>完成<br /> </td> 
   <td>可以使用 <a href="/help/sites-authoring/templates.md">模板编辑器</a>.</td> 
  </tr>
  <tr>
   <td>对纯文本使用RTE</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：链接和锚点</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：字符映射</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：复制/粘贴</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：从Microsoft Word粘贴<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：查找和替换</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：文本格式（粗体、...）</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：子和上标</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：正文</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：列表（项目符号/数字）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：段落格式</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：文本样式</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：源代码编辑器(编辑HTML)<br /> </td> 
   <td>完成<br /> </td> 
   <td>仅在对话框和全屏中可用。<br /> </td> 
  </tr>
  <tr>
   <td>RTE插件：拼写检查程序</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：表（嵌入式表编辑器）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：撤消/重做<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：允许内嵌图像</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>表编辑器</td> 
   <td>完成</td> 
   <td>可用的就地、对话框和全屏。<br /> </td> 
  </tr>
  <tr>
   <td>将图像拖放到表格单元格中<br /> </td> 
   <td>完成</td> 
   <td>可用内联</td> 
  </tr>
  <tr>
   <td>图像编辑器<br /> </td> 
   <td>完成</td> 
   <td>可用的就地、对话框和全屏。<br /> </td> 
  </tr>
  <tr>
   <td>启用/禁用IPE插件</td> 
   <td>完成</td> 
   <td>现在， <a href="/help/sites-authoring/templates.md">模板编辑器</a>.</td> 
  </tr>
  <tr>
   <td>IPE插件：裁切</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：翻转</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：撤消/重做</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：图像映射</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：旋转</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：缩放</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 功能状态：工具 {#feature-status-tools}

这是经典UI具有的各种工具列表以及触屏UI中的状态。

<table> 
 <tbody>
  <tr>
   <td><strong>专题<br /> </strong></td> 
   <td><strong>状态<br /> </strong></td> 
   <td><strong>注释</strong></td> 
  </tr>
  <tr>
   <td>任务管理</td> 
   <td>已更换</td> 
   <td>已引入6.0 <a href="/help/sites-authoring/projects.md">项目和任务</a>.<br /> </td> 
  </tr>
  <tr>
   <td>工作流收件箱<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>页面模板配置工作流(<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>缺少<br /> </td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>标记管理员UI<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>MSM/Blueprint控制中心</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Blueprint Manager UI</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>转出配置UI</td> 
   <td>缺少</td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>用户、组和权限UI<br /> </td> 
   <td>基本完成<br /> </td> 
   <td>要进行高级权限编辑，请使用经典UI。<br /> </td> 
  </tr>
  <tr>
   <td>清除版本(<code>/etc/versioning/purge.html</code>)</td> 
   <td>缺少</td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>外部链接检查程序 (<code>/etc/linkchecker.html</code>)</td> 
   <td>缺少</td> 
   <td>使用经典UI。<br /> </td> 
  </tr>
  <tr>
   <td>批量编辑器(<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>缺少<br /> </td> 
   <td>使用经典UI。</td> 
  </tr>
 </tbody>
</table>
