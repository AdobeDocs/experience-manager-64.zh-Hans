---
title: 评分和徽章要点
seo-title: 评分和徽章要点
description: 评分和徽章功能概述
seo-description: 评分和徽章功能概述
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
exl-id: 84aa46d5-4ca4-4f6e-b0b9-fc9907be00a5
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 0%

---

# 评分和徽章要点{#scoring-and-badges-essentials}

AEM Communities评分和徽章功能提供了识别和奖励社区成员的功能。

有关设置该功能的详细信息，请参阅

* [社区评分和徽章](implementing-scoring.md)

本页包含其他技术详细信息：

* 如何[将标记](#displaying-badges)显示为图像或文本
* 如何打开广泛的[调试日志记录](#debug-log-for-scoring-and-badging)
* 如何[访问与评分和标记相关的UGC](#ugc-for-scoring-and-badging)

>[!CAUTION]
>
>CRXDE Lite中可见的实施结构可能会发生更改。

## 显示徽章{#displaying-badges}

在HBS模板的客户端上，将控制徽章显示为文本还是图像。

例如，在`/libs/social/forum/components/hbs/topic/list-item.hbs`中搜索`this.isAssigned`:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

如果为true，则isAssigned表示已为角色分配标记，该标记应显示为文本。

如果为false，则为“已分配”表示已为应得分授予徽章，且徽章应显示为图像。

对此行为所做的任何更改都应在自定义脚本中进行（覆盖或叠加）。 请参阅[客户端自定义](client-customize.md)。

## 调试日志以获取评分和标记{#debug-log-for-scoring-and-badging}

为帮助调试评分和标记，可以设置自定义日志文件。 如果该功能遇到问题，可向客户支持提供此日志文件的内容。

有关详细说明，请访问[创建自定义日志文件](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file)。

要快速设置slinglog文件，请执行以下操作：

1. 例如，访问&#x200B;**[!UICONTROL Adobe Experience Manager Web控制台日志支持]**

   * http://localhost:4502/system/console/slinglog

1. 选择&#x200B;**[!UICONTROL 添加新日志记录器]**

   1. 为&#x200B;**[!UICONTROL 日志级别]**&#x200B;选择`DEBUG`
   1. 输入&#x200B;**[!UICONTROL 日志文件]**&#x200B;的名称，例如

      * logs/scoring-debug.log
   1. 输入两个&#x200B;**[!UICONTROL Logger]**（类）条目（使用`+`图标）

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. 选择&#x200B;**[!UICONTROL Save]**



![chlimage_1-248](assets/chlimage_1-248.png)

要查看日志条目：

* 从Web控制台

   * 在&#x200B;**[!UICONTROL 状态]**&#x200B;菜单下
   * 选择&#x200B;**[!UICONTROL 日志文件]**
   * 搜索日志文件名，如`scoring-debug`

* 在服务器的本地磁盘上

   * 日志文件位于&lt;*server-install-dir*>/crx-quickstart/logs/*log-file-name*>.log
   * 例如，`.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## 用于评分和标记的UGC {#ugc-for-scoring-and-badging}

当所选SRP是JSRP或MSRP，但不是ASRP时，可以查看与评分和标记相关的UGC。 （如果不熟悉这些术语，请参阅[社区内容存储](working-with-srp.md)和[存储资源提供程序概述](srp.md)。）

访问评分和标记数据的描述使用JSRP，因为UGC可以使用[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)轻松访问。

**作者JSRP**:在创作环境中进行实验时，会导致生成的UGC仅在创作环境中可见。

**发布时的JSRP**:同样，如果在发布环境中进行测试，则需要使用发布实例的管理权限访问CRXDE Lite。如果发布实例在[生产模式](../../help/sites-administering/production-ready.md)（nosamplecontent运行模式）中运行，则需要[启用CRXDE Lite](../../help/sites-administering/enabling-crxde-lite.md)。

JSRP上UGC的基本位置为`/content/usergenerated/asi/jcr/`。

### 评分和标记API {#scoring-and-badging-apis}

以下API可供使用：

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

已安装[版本](deploy-communities.md#LatestReleases)的最新Javaoc可供Adobe存储库中的开发人员使用。 请参阅[使用Maven for Communities:Javaocs](maven.md#javadocs)。

**UGC在存储库中的位置和格式可能会发生更改，但不会发出警告**。

### 设置示例{#example-setup}

存储库数据的屏幕截图来自在两个不同的AEM网站上为论坛设置评分和标记：

1. 具有唯一ID的AEM网站（使用向导创建的社区网站）：

   * 使用在[快速入门教程](getting-started.md)中创建的快速入门教程（参与）网站
   * 找到论坛页面节点

      * `/content/sites/engage/en/forum/jcr:content`
   * 添加评分和标记属性

      * `scoringRules = [/etc/community/scoring/rules/comments-scoring,`

         `/etc/community/scoring/rules/forums-scoring]`
      * `badgingRules =[/etc/community/badging/rules/comments-scoring,`

         `/etc/community/badging/rules/forums-scoring]`
   * 找到论坛组件节点

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         (`sling:resourceType = social/forum/components/hbs/forum`)
   * 将资产添加到显示徽章

      * `allowBadges = true`
   * 用户登录，创建论坛主题，并获得铜像徽章





1. 没有&#x200B;*唯一ID的AEM站点*:

   * 使用[社区组件指南](components-guide.md)
   * 找到论坛页面节点

      * `/content/community-components/en/forum/jcr:content`
   * 添加评分和标记属性

      ```
      scoringRules = [/etc/community/scoring/rules/comments-scoring,
      /etc/community/scoring/rules/forums-scoring]
      ```

      ```
      badgingRules =[/etc/community/badging/rules/comments-scoring,
      /etc/community/badging/rules/forums-scoring]
      ```

   * 找到论坛组件节点

      * `/content/community-components/en/forum/jcr:content/content/forum`

         (`sling:resourceType = social/forum/components/hbs/forum`)
   * 将资产添加到显示徽章

      * `allowBadges = true`
   * 用户登录，创建论坛主题，并获得铜像徽章




1. 使用cURL为用户分配了审核者标记：

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

由于用户已获得两枚铜牌，并获得了审核者徽章，因此用户在论坛条目中的显示方式如下：

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>此示例未遵循以下最佳实践：
>
>* 评分规则名称应具有全局唯一性；它们不应以相同的名称结尾。\
   >  *not*&#x200B;要执行的操作的示例：\
   >  /etc/community/scoring/rules/site1/forums-scoring\
   >  /etc/community/scoring/rules/site2/forums-scoring
   >
   >
* 为不同的AEM站点创建唯一标记图像

>



### 访问评分UGC {#access-scoring-ugc}

首选使用[API](#scoring-and-badging-apis)。

出于调查目的，以JSRP为例，包含得分的基本文件夹是

* `/content/usergenerated/asi/jcr/scoring`

`scoring`的子节点是评分规则名称。 因此，最佳做法是服务器上的评分规则名称在全局上是唯一的。

对于“Geometrixx参与”网站，用户及其得分所在的路径包含评分规则名称、社区网站的网站ID(`engage-ba81p`)、唯一ID和用户ID:

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

对于社区组件指南网站，用户及其得分所在的路径是使用评分规则名称、默认ID(`default-site`)、唯一ID和用户ID构建的：

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

分数存储在属性`scoreValue_tl`中，该属性可能仅直接包含值或间接引用atomicCounter。

![chlimage_1-251](assets/chlimage_1-251.png)

### 访问标记UGC {#access-badging-ugc}

首选使用[API](#scoring-and-badging-apis)。

为了调查目的，以JSRP为例，将包含已分配或已授予徽章信息的基础文件夹

* /content/usergenerated/asi/jcr

后跟用户配置文件的路径，以徽章文件夹结尾，例如

* /home/users/community/w271Up2Z4DjnOQrviv/profile/badges

#### 奖章{#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### 已分配标记{#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## 附加信息 {#additional-information}

要显示基于点的已排序成员列表，请执行以下操作：

* [用于包](functions.md#leaderboard-function) 含在社区站点或群组模板中的排行榜功能。
* [排行榜组件](enabling-leaderboard.md)，即排行榜功能的特色组件，用于页面创作。
