---
title: Livefyre Feature Pack 2.0.6发行说明
seo-title: Livefyre Feature Pack 2.0.6发行说明
description: Livefyre Feature Pack 2.0.6发行说明
seo-description: Livefyre Feature Pack 2.0.6发行说明
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: 715cff841252d79504d702817f91db92df919bfc

---


# Livefyre Feature Pack 2.0.6发行说明 {#livefyre-feature-pack-release-notes}

## 发行信息 {#release-information}

<table> 
 <tbody>
  <tr>
   <td>产品</td> 
   <td>Livefyre功能包2.0.6</td> 
  </tr>
  <tr>
   <td>版本</td> 
   <td>2.0.6</td> 
  </tr>
  <tr>
   <td>类型</td> 
   <td>功能发布</td> 
  </tr>
  <tr>
   <td>日期</td> 
   <td>2018年8月31日</td> 
  </tr>
  <tr>
   <td>下载 URL<br /> </td> 
   <td>联系您的管理员</td> 
  </tr>
  <tr>
   <td>兼容性 (*)</td> 
   <td>AEM 6.4 SP1、6.4、6.3 GA和6.2 SP1</td> 
  </tr>
  <tr>
   <td>描述</td> 
   <td>此包允许您将Livefyre行业领先的特选功能与AEM实例集成，使您能在几分钟内将宝贵的用户生成内容(UGC)从社交网络发布到您的站点。</td> 
  </tr>
 </tbody>
</table>

## Livefyre Feature Pack 2.0.6包含的功能 {#what-is-included-in-livefyre-feature-pack}

该软件包将Livefyre业界领先的特选功能与您的AEM实例相集成，使您能在几分钟内将宝贵的用户生成内容(UGC)从社交网络发布到您的站点。 此包有三个不同的组件：

**将UGC内容导入AEM资产**

* 使用UGC导入程序将Twitter和Instagram用户生成的内容(UGC)从Livefyre studio导入AEM资产。
* 访问Livefyre库。
* 使用Livefyre社交搜索在Twitter和Instagram上实时搜索。
* 在UGC上管理权限。

**将Livefyre组件添加到AEM Sites或Communities**

* 使用包括地图、画廊和媒体墙在内的一套社交组件，即时构建和自定义动态、引人入胜的体验。
* 在AEM站点或社区中发布UGC。

**通过AEM Commerce将产品目录导入Livefyre**

* 将现有产品目录无缝集成到Livefyre中，以推动用户在您的站点中的参与和转化，并提供可购物的UGC体验。
* 编辑或删除AEM Commerce产品目录中的项目，并自动更新Livefyre中的更改。

有关安装的帮助，请参阅 [与Livefyre集成](https://https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html)。

### 其他发行信息 {#additional-release-information}

由于更新影响Instagram非商业用户帐户中内容的汇总，我们无法再代表您发布评论或自动检查作者的回复。 [单击此处了解更多信息](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/)。

>[!NOTE]
>
>Livefyre功能包2.0.6不支持AEM Classic UI。

#### 新增功能或改进 {#new-feature-or-improvement}

* 添加了在Livefyre中设置权限请求社交帐户之前搜索UGC的功能。 您必须设置社交帐户才能请求权限，或者如果您拥有内容，则覆盖权限请求。
* Instagram和Twitter [UGC权限请求工作流程已更新](https://https://helpx.adobe.com/experience-manager/6-4/sites/administering/using/livefyre.html) ，以符合最新的API。
* 权限状态和相应的操作现在显示在权限请求屏幕上。

#### 错误修复 {#bug-fixes}

* 修复了在Livefyre studio中删除用于权限请求的社交帐户时，在AEM中加载UGC库时出错的问题。
* 修复了Livefyre Studio中的资产计数与AEM UGC库中的资产计数不匹配的问题。
* 修复了UGC库中的一个问题，该问题导致在重置筛选器选项后显示筛选结果。
* 修复了AEM Commerce中的一个问题，该问题导致行动动员按钮将用户重定向到错误的URL。
* 修复了AEM站点中将多个组件拖放到parsys占位符中导致其消失的问题。
* 修复了在发送权限请求时，禁用的社交帐户可供选择的问题。
* 修复了将UGC从资产拖放到站点时会出错的问题。
* 修复了将聊天和Liveblog组件拖放到站点中不创建应用程序的问题。
* 修复了用户尝试评论时评论应用程序产生错误的问题。
* 修复了将Livefyre Media Wall应用程序添加到站点时在Java内容存储库中创建额外节点的问题。
* 修复了在Instagram UGC搜索中导致分页和控制台错误的问题。
* 修复了Instagram用户图标在资产中生成API错误的问题。
* 修复了将“审阅”应用程序添加到没有预定义格式的站点的问题。
* 修复了触屏UI功能和内联编辑的问题。
* 修复了导入某些Instagram图像资源时导致错误的问题。
* 修复了AEM中的Livefyre HTTP客户端不支持代理配置的问题。

