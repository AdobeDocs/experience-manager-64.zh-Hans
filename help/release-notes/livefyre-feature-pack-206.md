---
title: Livefyre功能包2.0.6发行说明
seo-title: Livefyre Feature Pack 2.0.6 Release Notes
description: Livefyre功能包2.0.6发行说明
seo-description: Livefyre Feature Pack 2.0.6 Release Notes
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Livefyre功能包2.0.6发行说明 {#livefyre-feature-pack-release-notes}

## 版本信息 {#release-information}

| 产品 | Livefyre功能包2.0.6 |
|--- |--- |
| 版本 | 2.0.6 |
| 类型 | 功能发布 |
| 日期 | 2018年8月31日 |
| 下载 URL | 与管理员联系 |
| 兼容性 (*) | AEM 6.4 SP1、6.4、6.3 GA和6.2 SP1 |
| 描述 | 此包允许您将Livefyre业界领先的管理功能与您的AEM实例相集成，从而在几分钟内将社交网络中用户生成的有价值内容(UGC)发布到您的网站。 |

## Livefyre功能包2.0.6中包含的内容 {#what-is-included-in-livefyre-feature-pack}

此产品包将Livefyre业界领先的管理功能与您的AEM实例集成在一起，使您能够在几分钟内将社交网络中用户生成的宝贵内容(UGC)发布到您的网站。 此包有三个不同的组件：

**将UGC内容导入AEM Assets**

* 使用UGC导入器将Twitter和Instagram用户生成的内容(UGC)从Livefyre Studio导入AEM Assets。
* 访问您的Livefyre库。
* 使用Livefyre Social搜索在Twitter和Instagram上实时搜索。
* 在UGC中管理权限。

**将Livefyre组件添加到AEM Sites或Communities**

* 使用一套社交组件（包括地图、画廊和媒体墙）即时构建和自定义动态且引人入胜的体验。
* 在AEM Sites或社区中发布UGC。

**将产品目录导入Livefyre with AEM Commerce**

* 将您现有的产品目录无缝集成到Livefyre中，以提高用户在您网站中的参与度和转化率，并提供可购UGC体验。
* 编辑或删除AEM Commerce Product Catalog中的项目，并自动更新Livefyre中的更改。

有关安装的帮助，请参阅 [与Livefyre集成](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html).

### 其他发行信息 {#additional-release-information}

由于更新影响来自Instagram非业务用户帐户的内容汇总，我们无法再代表您发布评论或自动检查作者的回复。 [单击此处了解更多信息](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre功能包2.0.6不支持AEM Classic UI。

#### 新功能或改进 {#new-feature-or-improvement}

* 添加了在Livefyre中设置权限请求社交帐户之前搜索UGC的功能。 您必须设置社交帐户以请求权限，或者在您拥有内容时覆盖权限请求。
* Instagram和Twitter [UGC权限请求工作流](https://experienceleague.adobe.com/docs/experience-manager-64/administering/integration/livefyre.html) 已更新以符合最新的API。
* 权限状态和相应的操作现在显示在权限请求屏幕上。

#### 错误修复 {#bug-fixes}

* 修复了在AEM中加载UGC库时，删除Livefyre Studio中用于权限请求的社交帐户时导致错误的问题。
* 修复了Livefyre Studio中的资产计数与AEM UGC库中的资产计数不匹配的问题。
* 修复了UGC库中在重置过滤器选项后显示过滤结果的问题。
* 修复了AEM Commerce中的一个问题，即行动动员按钮会将用户重定向到错误的URL。
* 修复了AEM Sites中将多个组件拖放到Parsys占位符中导致其消失的问题。
* 修复了在发送权限请求时，可以从中选择禁用的社交帐户的问题。
* 修复了将UGC从资产拖放到站点时出错的问题。
* 修复了将聊天组件和实时博客组件拖放到站点中时，未创建应用程序的问题。
* 修复了用户尝试评论时，评论应用程序出错的问题。
* 修复了将Livefyre Media Wall应用程序添加到站点时在Java内容存储库中创建额外节点的问题。
* 修复了导致Instagram UGC搜索中出现分页和控制台错误的问题。
* 修复了Instagram用户图标在资产中生成API错误的问题。
* 修复了将“审阅”应用程序添加到没有预定义格式的网站的问题。
* 修复了触屏UI功能和内联编辑的问题。
* 修复了导入某些Instagram图像资产时导致错误的问题。
* 修复了AEM中的Livefyre HTTP客户端不支持代理配置的问题。
