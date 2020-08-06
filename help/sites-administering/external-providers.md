---
title: 外部提供商的分析
seo-title: 外部提供商的分析
description: 了解外部提供商的Analytics。
seo-description: 了解外部提供商的Analytics。
uuid: bea8ec38-a190-46f9-a5fa-8d65321fdf20
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: bf8fd156-4be9-43f8-8948-cf7f91c25f1b
translation-type: tm+mt
source-git-commit: f1a5e4c5c8411e10887efab517115fee0fd1890a
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 3%

---


# 外部提供商的分析{#analytics-with-external-providers}

Analytics可为您提供有关网站使用情况的重要而有趣的信息。

各种开箱即用配置可用于与相应的服务集成，例如：

* [Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* [Adobe Target](/help/sites-administering/target.md)

您还可以配置自己的通用分析 **代码片段实例** ，以定义新的服务配置。

然后，通过添加到网页的少量代码片段来收集信息。 例如：

>[!CAUTION]
>
>脚本不能包含在标 `script` 记中。

```
var _gaq = _gaq || [];
_gaq.push(['_setAccount', 'UA-XXXXX-X']);
_gaq.push(['_trackPageview']);

(function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
})();
```

这样的代码片段能够收集数据并生成报告。 收集的实际数据取决于提供程序和使用的实际代码片断。 统计数据示例包括：

* 一段时间内有多少访客
* 访问页数
* 使用的搜索词
* 登陆页

>[!CAUTION]
>
>Geometrixx-Outdoors演示站点已配置，因此页面属性中提供的属性将附加到相应脚本中的html源代码(就在 `</html>` 结束标记的上方) `js` 中。
>
>
>如果您自 `/apps` 己不继承默认的页面组件( `/libs/foundation/components/page`)，您（或您的开发人员）必须确保包括相应的脚本，例如，包括或 `js``cq/cloudserviceconfigs/components/servicescomponents`使用类似机制。
>
>
>如果没有此选项，则任何服务(通用、分析、目标等)都无法正常工作。

## 使用通用代码片断创建新服务 {#creating-a-new-service-with-a-generic-snippet}

对于基本配置：

1. Open the **Tools** console.

1. 从左窗格展开 **Cloud Services配置**。

1. 多次-单击“ **通用分析代码** ”(Generic Analytics Snippet)以打开页面：

   ![analytics_generic概述](assets/analytics_genericoverview.png)

1. 单击+，使用对话框添加新配置； 至少分配一个名称，例如google analytics:

   ![analytics_addconfig](assets/analytics_addconfig.png)

1. 单击 **创建**，将立即打开片段对话框——将相应的javascript片段粘贴到字段中：

   ![analytics_snippet](assets/analytics_snippet.png)

1. 单击&#x200B;**确定**&#x200B;进行保存。

## 在页面上使用新服务 {#using-your-new-service-on-pages}

创建服务配置后，您现在需要配置所需的页面才能使用它：

1. 导航到页面。

1. 从Sidekick中 **打开页面** 属性，然后打开 **Cloud Services** 选项卡。

1. 单击 **添加服务**，然后选择所需的服务； 例如，通 **用分析代码段**:

   ![analytics_selectservice](assets/analytics_selectservice.png)

1. 单击&#x200B;**确定**&#x200B;进行保存。

1. 您将返回到“Cloud Services” **选项卡** 。 现 **在，通用分析片段** 随消息一起列出 `Configuration reference missing`。 使用下拉列表选择您的特定服务实例； 例如google-analytics:

   ![analytics_selectspecificservice](assets/analytics_selectspecificservice.png)

1. 单击&#x200B;**确定**&#x200B;进行保存。

   现在，如果您视图页面的页面源，就可以看到该片段。

   经过适当的时间段后，您将能够视图已收集的统计信息。

   >[!NOTE]
   >
   >如果配置附加到具有子页面的页面，则服务也由子页面继承。

