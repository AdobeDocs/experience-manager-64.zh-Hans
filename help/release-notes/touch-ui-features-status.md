---
title: 触屏UI功能状态
seo-title: 触屏UI功能状态
description: 特定于Adobe Experience Manager6.3触屏UI的发行说明。
seo-description: 特定于Adobe Experience Manager6.3触屏UI的发行说明。
uuid: dc335334-6c50-4cee-8a2e-183958742686
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 482b5eb0-1b15-4f10-a9d8-3b72dd74acf8
translation-type: tm+mt
source-git-commit: db26dd05f6c0997eeda462f27971cbcfa6737527
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 14%

---


# 触屏UI功能状态{#touch-ui-feature-status}

>[!CAUTION]
>
>对于AEM的6.4版，[经典UI已弃用](/help/release-notes/deprecated-removed-features.md)。 Adobe不打算对经典UI进行进一步的增强，并鼓励用户利用触屏优化UI中提供的强大新功能。

从6.0版开始，AEM引入了称为“触屏优化UI”（也称为“触屏优化UI”）的新用户界面，该界面与Adobe Marketing Cloud和整个Adobe用户界面指南保持一致。 在几乎达到功能特性的情况下，它已成为AEM中的标准UI，具有传统的、面向桌面的界面，称为“经典UI”。

虽然触屏优化UI中提供的大多数功能尚未完整，并且将在未来版本中添加。

以下列表显示了AEM 6.4中实现的功能的当前状态。

有关升级到AEM 6.4的客户的建议，请参见[客户的用户界面Recommendations](/help/sites-deploying/ui-recommendations.md)以了解详细信息。

>[!NOTE]
>
>请注意，本页仅涵盖与经典UI的功能对等性。
>
>未列出触屏优化UI中不存在的新增功能和特有功能。

>[!NOTE]
>
>本列表力求完整，但不应视为详尽无遗。

## 图例 {#legend}

* **完成**:该功能在触屏优化UI中完全可用
* **主要**:该功能在触屏优化UI中大多可用。
* **缺失**:该功能在触屏优化UI中不存在，必须使用经典UI才能执行此操作。
* **已替换**:该功能被替换为新实现，其工作方式不同。
* **删除**:该功能在触屏优化UI中不再存在，将不会被替换。

## 功能状态：站点管理员{#feature-status-sites-admin}

这是经典UI站点管理员(`/siteadmin`)所具有的列表功能以及触屏优化UI(`/sites.html`)的状态。

<table> 
 <tbody>
  <tr>
   <td><strong>功能<br /> </strong></td> 
   <td><strong>状态<br /> </strong></td> 
   <td><strong>注释</strong></td> 
  </tr>
  <tr>
   <td>导航站点层次结构</td> 
   <td>完成<br /> </td> 
   <td>AEM 6.4引入了<a href="/help/sites-authoring/basic-handling.md#content-tree">内容树视图</a>。</td> 
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
   <td>新建Live Copy <br /> </td> 
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
   <td>大多数</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>搜索</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>复制／粘贴页面(重复)</td> 
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
   <td>无复制权限的发布页面</td> 
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
   <td>锁定／解锁</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>视图/编辑属性</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>设置页面权限</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>版本历史记录</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>恢复版本</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>恢复树和恢复已删除的页面</td> 
   <td>缺失</td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>显示旧版本与当前版本的差异<br /> </td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>Live Copy操作（滚出）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>查看语言副本</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>查找并替换</td> 
   <td>缺少<br /> </td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>通知收件箱(JCR事件)</td> 
   <td>缺失</td> 
   <td>使用经典UI。 将替换为不同的实现。</td> 
  </tr>
  <tr>
   <td>引用</td> 
   <td>大多数</td> 
   <td>AEM 2019版中将添加传入页面链接的显示。</td> 
  </tr>
 </tbody>
</table>

## 功能状态：页面编辑器{#feature-status-page-editor}

这是经典UI页面编辑器(`/cf#`)所具有的列表功能以及触屏启用(`/editor.html`)的状态。

<table> 
 <tbody>
  <tr>
   <td><strong>功能</strong></td> 
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
   <td>编辑移动应用程序</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑Forms</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>编辑优惠</td> 
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
   <td>转出页</td> 
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
   <td>大多数</td> 
   <td>在触屏优化UI中完全可访问。 在经典UI中仍显示多个工作流有效负荷。<br /> </td> 
  </tr>
  <tr>
   <td>锁定／解锁页面</td> 
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
   <td>使用站点管理员复制页面<a href="/help/sites-authoring/managing-pages.md#copying-and-pasting-a-page">。</a><br /> </td> 
  </tr>
  <tr>
   <td>移动页面</td> 
   <td>已删除</td> 
   <td>使用站点管理员移动页面<a href="/help/sites-authoring/managing-pages.md#moving-or-renaming-a-page">。</a><br /> </td> 
  </tr>
  <tr>
   <td>删除页面</td> 
   <td>已删除</td> 
   <td>使用站点管理员删除<a href="/help/sites-authoring/managing-pages.md#deleting-a-page">页面</a>。<br /> </td> 
  </tr>
  <tr>
   <td>显示引用</td> 
   <td>已删除</td> 
   <td>使用站点管理<a href="/help/sites-authoring/author-environment-tools.md#references">查看详细的参考列表</a>。<br /> </td> 
  </tr>
  <tr>
   <td>审查日志</td> 
   <td>已删除</td> 
   <td>使用站点管理员和<a href="/help/sites-authoring/author-environment-tools.md#events-timeline">打开活动边栏</a>。<br /> </td> 
  </tr>
  <tr>
   <td>创建版本</td> 
   <td>已删除</td> 
   <td>使用站点管理员<a href="/help/sites-authoring/working-with-page-versions.md#creating-a-new-version">创建新版本</a>。<br /> </td> 
  </tr>
  <tr>
   <td>恢复版本</td> 
   <td>已删除</td> 
   <td>使用站点管理员恢复版本<a href="/help/sites-authoring/working-with-page-versions.md#reverting-to-a-page-version">。</a></td> 
  </tr>
  <tr>
   <td>切换启动项</td> 
   <td>已删除</td> 
   <td>使用站点管理员在启动项<a href="/help/sites-authoring/launches-promoting.md">之间切换。</a><br /> </td> 
  </tr>
  <tr>
   <td>翻译页面</td> 
   <td>已删除</td> 
   <td>使用站点管理员<a href="/help/sites-administering/tc-manage.md">向翻译项目</a>添加页面。<br /> </td> 
  </tr>
  <tr>
   <td>时间扭曲（选择日期／时间，浏览站点，视图）<br /> </td> 
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
   <td>已替换</td> 
   <td>将使用<a href="/help/sites-authoring/ch-previewing.md">ContextHub</a> UI。</td> 
  </tr>
  <tr>
   <td>各种媒体类型的内容查找器<br /> </td> 
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
   <td>缺失</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>撤消／重做</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>将内容拖放到组件占位符中</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>将内容直接拖放到parsys占位符中，组件自动创建<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## 功能状态：文本、表和图像编辑器{#feature-status-text-table-and-image-editors}

这是经典UI文本、表和图像编辑器的功能列表以及触屏优化UI中的状态。

<table> 
 <tbody>
  <tr>
   <td><strong>功能</strong></td> 
   <td><strong>状态 </strong></td> 
   <td><strong>注释<br /> </strong></td> 
  </tr>
  <tr>
   <td>富文本编辑器</td> 
   <td>完成</td> 
   <td>可用于就地、对话和全屏。</td> 
  </tr>
  <tr>
   <td>启用／禁用RTE插件</td> 
   <td>完成<br /> </td> 
   <td>可以使用<a href="/help/sites-authoring/templates.md">模板编辑器</a>完成。</td> 
  </tr>
  <tr>
   <td>将RTE用于纯文本</td> 
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
   <td>RTE插件：复制／粘贴</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：从Microsoft Word<br />粘贴 </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：查找并替换</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：文本格式（粗体， ...）</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：子和上标</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：两端对齐</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：列表语（项目符号／数字）</td> 
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
   <td>RTE插件：源代码编辑器（编辑HTML）<br /> </td> 
   <td>完成<br /> </td> 
   <td>仅在对话框和全屏中可用。<br /> </td> 
  </tr>
  <tr>
   <td>RTE插件：拼写检查器</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：表（嵌入式表编辑器）</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：撤消／重做<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>RTE插件：允许联机图像</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>表编辑器</td> 
   <td>完成</td> 
   <td>可用于就地、对话和全屏。<br /> </td> 
  </tr>
  <tr>
   <td>将图像拖放到表单元格<br /> </td> 
   <td>完成</td> 
   <td>可用的联机</td> 
  </tr>
  <tr>
   <td>图像编辑器<br /> </td> 
   <td>完成</td> 
   <td>可用于就地、对话和全屏。<br /> </td> 
  </tr>
  <tr>
   <td>启用／禁用IPE插件</td> 
   <td>完成</td> 
   <td><a href="/help/sites-authoring/templates.md">模板编辑器</a>中现在有一个UI。</td> 
  </tr>
  <tr>
   <td>IPE插件：裁剪</td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：翻转</td> 
   <td>完成<br /> </td> 
   <td> </td> 
  </tr>
  <tr>
   <td>IPE插件：撤消／重做</td> 
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

## 功能状态：工具{#feature-status-tools}

这是经典UI具有的各种工具的列表，以及触屏优化UI中的状态。

<table> 
 <tbody>
  <tr>
   <td><strong>功能<br /> </strong></td> 
   <td><strong>状态<br /> </strong></td> 
   <td><strong>注释</strong></td> 
  </tr>
  <tr>
   <td>任务管理</td> 
   <td>已替换</td> 
   <td>6.0引入了<a href="/help/sites-authoring/projects.md">项目和任务</a>。<br /> </td> 
  </tr>
  <tr>
   <td>Workflow收件箱<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>页面模板配置的工作流(<code>/etc/workflow/wcm/templates.html</code>)</td> 
   <td>缺少<br /> </td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>标记管理员UI<br /> </td> 
   <td>完成</td> 
   <td> </td> 
  </tr>
  <tr>
   <td>MSM/Blueprint Control Center</td> 
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
   <td>缺失</td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>用户、组和权限UI<br /> </td> 
   <td>Martily Complete<br /> </td> 
   <td>对于高级权限编辑，请使用经典UI。<br /> </td> 
  </tr>
  <tr>
   <td>清除版本(<code>/etc/versioning/purge.html</code>)</td> 
   <td>缺失</td> 
   <td>使用经典UI。</td> 
  </tr>
  <tr>
   <td>外部链接检查程序 (<code>/etc/linkchecker.html</code>)</td> 
   <td>缺失</td> 
   <td>使用经典UI。<br /> </td> 
  </tr>
  <tr>
   <td>批量编辑器(<code>/etc/importers/bulkeditor.html</code>)</td> 
   <td>缺少<br /> </td> 
   <td>使用经典UI。</td> 
  </tr>
 </tbody>
</table>

