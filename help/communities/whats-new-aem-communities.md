---
title: AEM 6.4 Communities的新增功能
description: AEM Communities为企业提供了一个框架，以便在合作伙伴、客户和员工之间进行协作。
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
source-git-commit: 1a7ecec2f3c2618bb6d0280a8f9a66754cd8a1a3
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 0%

---

# AEM 6.4 Communities {#what-s-new-in-aem-communities}的新增功能

AEM Communities为企业提供了一个框架，以便在合作伙伴、客户和员工之间进行协作。 它将社交能力引入网站结构，并帮助企业与利益相关方接触并传授知识，以提升其品牌价值。

AEM 6.4 Communities引入了一些功能，用于增强社区用户的体验，并简化社区管理员、审核者和管理者的日常任务。

进一步阅读，快速了解新增功能和增强功能。 另请参阅AEM 6.4 Communities [发行说明](../release-notes/communities-release-notes.md)。 有关AEM 6.4 Communities文档，请访问[AEM 6.4 Communities用户指南](home.md)。

## 管理子社区或社区组{#managing-sub-communities-or-community-groups}

AEM Communities允许社区管理员在创作环境中使用预定义的模板在社区站点内创建组和子组。 这些组用作子社区，可以继承许多配置，如父站点的主题和样式。 但是，这些组可能与父站点不同，例如具有不同的组审核者集合，或者在安全级别上可能有所不同。 这些群体作为独立、成熟的小型社区发挥作用，通过以下改进进一步增强了这些社区的能力。

### 在单步{#create-multi-locale-groups-in-single-step}中创建多区域设置组

作为社区站点的一部分，可以通过单次操作创建多语言组。 **[!UICONTROL “社区组模板”页面中]** 的其他可 **[!UICONTROL 用]** 社区组语言字段(在社区站点内创建新社 [区](groups.md) 组时可用)使此功能可行。

![多语言组–1](assets/multilingualgroup-1.png)

要创建此类群组，用户只需从站点控制台导航到所需社区站点的群组集合即可。 创建群组，并在&#x200B;**[!UICONTROL 社区组模板]**&#x200B;页面的&#x200B;**[!UICONTROL 其他可用社区组语言]**&#x200B;字段中指定所需的语言。

### 从组控制台{#delete-community-groups-from-groups-console}中删除社区组

AEM 6.4 Communities在社区站点控制台的社区组收藏集中，为现有社区组提供了“删除组”图标。 这样一来，[组删除](groups.md#deleting-the-group)，并删除与组关联的所有项目（如内容和用户成员关系）。

![deletegrp](assets/deletegrp.png)

### 在{#create-and-assign-enablement-resources-within-groups}组内创建和分配启用资源

现在，可以为一组特定的定向社区成员创建、管理和发布学习内容。 由于社区组（不仅是整个社区站点）的目录和分配功能可用，支持管理人员可以[将支持资源](resource.md)和学习路径分配给一小群人。

![分配目录](assets/assignmentcatalog.png)

## 审核用户生成的内容{#moderating-user-generated-content}

AEM 6.4 Communities对审核功能的改进很少，这有助于简化社区审核者的日常生活。

### 自动垃圾邮件检测{#automatic-spam-detection}

新的垃圾邮件检测引擎有助于过滤掉社区站点或群组上不需要且未经请求的用户生成的内容。 启用此功能后，可根据预先定义的一组垃圾信息词语，将用户生成的内容标记为“垃圾信息”或“非垃圾信息”。 审核者可以进一步对内容采取行动以拒绝内容，或者允许内容显示在发布实例上。 这些审核操作可以在内联执行，也可以通过批量审核控制台执行。

![spamdetection-1](assets/spamdetection-1.png)

[垃圾邮](moderate-ugc.md#spam-detection) 件检测器查找并标记给定的一段用户生成的内容，其准确度为90%。但是，默认情况下未启用此功能。 要启用此功能，社区管理员需要导航到系统/控制台上的configMgr并添加垃圾邮件进程。

![spamprocess-1](assets/spamprocess-1.png)

### QnA {#new-answered-unanswered-filters-for-qna}的新（已应答/未应答）过滤器

AEM 6.4向批量审核控制台中添加了两个[新筛选器（针对QnA问题，命名为“已回答”和“未回答”）。 ](moderation.md#filter-rail)这些过滤器位于“过滤器边栏”中的状态下。

![状态](assets/statuses.png)

选择“已回答”状态时，内容区域中的审阅人可以看到所有已回答的问题。 但是，如果只选择了“未回答”状态，则主持人将看到除已回答问题之外的所有内容（适用于所有内容类型），因为对于未回答的问题以及论坛主题、博客文章或评论等其他内容，不存在负责“已回答问题”的属性。

### 将审核过滤器{#bookmark-moderation-filters}加入书签

AEM Communities提供在审核控制台上为预定义的审核过滤器](moderation.md#filter-rail)添加书签的功能。 [以后可以重新查看这些保存的书签并与其他用户共享。

用户只需从审核控制台的过滤器边栏中选择所需的过滤器，即可查看过滤的UGC，并在其浏览器中为过滤器添加书签即可。 这些过滤器会附加到URL字符串的末尾，因此可以共享、重复使用，稍后再次查看。

## 管理社区站点{#managing-community-sites}

AEM 6.4 Communities提供了站点管理增强功能，可确保站点管理员轻松创建、管理和删除大量使用不同语言的社区站点。

### 在一个步骤{#create-multi-locale-community-sites-in-one-step}中创建多区域设置社区站点

AEM Communities允许在单次操作中创建[多语言社区站点](create-site.md)。 这可能是因为在从站点控制台创建新的社区站点时，在&#x200B;**[!UICONTROL 站点模板]**&#x200B;页面的&#x200B;**[!UICONTROL 社区站点基本语言]**&#x200B;字段中提供了多种语言可供选择。

![多本地化](assets/multilocalesite.png)

用户可以同时为所有这些站点选择配置文件夹、品牌和许多其他配置。

### 从站点控制台{#delete-community-sites-from-sites-console}中删除社区站点

AEM 6.4 Communities在社区站点控制台中，在现有社区站点上提供了“删除站点”图标。 这样一来，就可以[删除站点](create-site.md)和关联的项目。

![站点操作](assets/siteactions.png)

## 管理UGC和用户配置文件{#managing-ugc-and-user-profiles}

AEM Communities将用户数据保护置于社区体验的核心，它公开了[现成API](user-ugc-management-service.md)和[示例servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet)。 这些API有助于批量管理（批量删除和批量导出）用户生成的内容和删除用户配置文件，并且有助于处理欧盟GDPR合规请求。

## 更改了哪些内容{#what-s-changed}

* 创建新社区站点时，AEM 6.4 Communities中不再提供现成的验证码验证。 但是，可以自定义社区网站以包含[Google组件reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html)，以提高安全性。
* 从社区站点和组主题中删除了上传自定义CSS的选项。
* 已在批量审核UI的过滤器边栏中添加“仅限内容”和“搜索”图标。
* 已在批量审核UI的“过滤器边栏”中添加了内容路径过滤器。
* 已从批量审核UI中删除了切换到批量模式和退出批量模式的选项。 要进入多选模式，请单击帖子上的选择(![selecticon](assets/selecticon.png))图标，当将鼠标悬停在帖子上时（桌面）会显示该图标，或者按住手指在帖子上（移动设备）时会显示该图标。
