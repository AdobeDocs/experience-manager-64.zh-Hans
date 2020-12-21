---
title: 社区分析配置功能
seo-title: 社区分析配置功能
description: 为社区配置分析
seo-description: 为社区配置分析
uuid: 625a253f-b198-40e8-b34c-dff337fb0eff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 36ea97a4-4e13-4e89-866b-495f3c30cb94
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '2787'
ht-degree: 3%

---


# 社区分析配置功能{#analytics-configuration-for-communities-features}

## 概述 {#overview}

Adobe Analytics和Adobe Experience Manager(AEM)都是Adobe Marketing Cloud的解决方案。

Adobe Analytics可以为AEM Communities配置，这样，当成员与支持的社区功能交互时，事件会发送到生成报告的Adobe Analytics。

例如，当启用社区站点的成员视图分配给他们的视频资源时，资源播放器会将事件发送到Analytics，包括视频心跳数据。 在社区站点中，管理员可以查看有关视频播放的各种报告。

此外，对于以下情况，分析是必需的：

* 在发布环境中：

   * 社区[趋势](trends.md)报告
   * 允许网站访客按“查看次数最多”、“最活跃”、“最喜欢”进行排序
   * 视图计入UGC列表

* 在作者环境中：

   * 在[成员管理控制台](members.md)中显示参与数据(视图、帖子、关注、喜欢)
   * 启用资源[报告](reports.md)的趋势摘要、视频心跳和视频设备

支持的社区功能包括：

* [支持资源](resources.md)
* [论坛](forum.md)
* [问题与解答](working-with-qna.md)
* [博客](blog-feature.md)
* [文件库](file-library.md)
* [日历](calendar.md)

本文档的本节介绍如何将Analytics报表包与社区功能相连。 基本步骤为：

1. [复制加密密](#replicate-the-crypto-key) 钥以确保在所有AEM实例上正确进行加密／解密
1. 准备Adobe Analytics[报告套件](#adobe-analytics-report-suite-for-video-reporting)
1. 创建AEM Analytics [云服务](#aem-analytics-cloud-service-configuration)和[框架](#aem-analytics-framework-configuration)
1. [为社](#enable-analytics-for-a-community-site) 区站点启用分析
1. [验证](#verify-analytics-to-aem-variable-mapping) 分析到AEM变量映射
1. 识别[主发布者](#primary-publisher)
1. [发](#publish-community-site-and-analytics-cloud-service) 布社区站点
1. 将报告数据[从Adobe Analytics导入到社区站点](#obtaining-reports-from-analytics)

## 前提条件 {#prerequisites}

要配置Analytics for Communities功能，必须与您的帐户代表合作设置Adobe Analytics帐户和[报表包](#adobe-analytics-report-suite-for-video-reporting)。 建立后，应提供以下信息：

* 公司名称

   与Adobe Analytics帐户关联的公司
* 用户名

   已授权管理Analytics帐户的用户的登录用户名

   （应包括Web服务访问权限）

* 密码

   授权用户的登录密码

* Analytics数据中心

   帐户的Analytics数据中心的URL

* 报表包

   要使用的Analytics报表包的名称

## Adobe Analytics视频报告报告套件{#adobe-analytics-report-suite-for-video-reporting}

使用Adobe Marketing Cloud的[报表包管理器](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html)，可以配置分析报表包，以便允许社区站点提供社区功能的报表。

通过使用[公司名和用户名](analytics.md#prerequisites)登录到[Adobe Marketing Cloud](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/home.html)，可以配置新的或现有的报表包：

* [11转换变量](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) (evar)

   * **`evar1`** 通过启 **`evar11`** 用
   * 可以重用（重命名）现有evar或创建新evar以用于社区功能

* [7成功事件](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/success-events/success-event.html) (事件)

   * **`event1`** 通过启 **`event7`** 用
   * 类型 **`Counter`**

      * 否 **`Counter (no subrelations)`**
   * 可以重用（重命名）现有事件或创建新的社区功能


* [视频管理](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)

   * 视频报告控制台

      * 启用 `Video Core`
      * 选择保存
   * 视频核心测量控制台

      * 选择 `Use Solution Variables`
      * 选择保存


如果使用&#x200B;**新的报表包**，请注意，新报表包可能只有4个evar和6个事件变量，而社区需要11个evar和7个事件变量。

如果使用&#x200B;**现有报表包**，则可能需要[在为社区站点激活Analytics框架之前修改变量映射](#modifying-analytics-variable-mapping)。 有关专用于社区的变量的任何疑虑，请与您的客户代表联系。

>[!CAUTION]
>
>**如果使用的现有报表包已经在**
>
>* **`evar1`** 至 **`evar11`**
>* **`event1`** 至 **`event7`**

>
>
**然后，在发布社区站点** 之前，务必通过移动AEM变量来恢复先前存在的映射，当为社区站点启用分析时，这些变量会自动映射到Analytics变量。
>
>要恢复先前存在的映射并将AEM变量移动到其他Analytics变量，请参阅[修改分析变量映射](#modifying-analytics-variable-mapping)一节。
>
>否则可能导致无法恢复的数据丢失。

### 视频心跳分析{#video-heartbeat-analytics}

获得视频心跳分析许可后，将分配`Marketing Cloud Org Id`。

要在[配置视频报告的分析报告包](#adobe-analytics-report-suite-for-video-reporting)后启用视频心跳报告:

* 创建[Analytics云服务](#aem-analytics-cloud-service-configuration)
* 为社区站点](#enable-analytics-for-a-community-site)启用[分析
* 将`Marketing Cloud Org Id`与社区站点关联

`Marketing Cloud Org Id`可在[社区站点创建](sites-console.md#enablement)或更高时通过[修改](sites-console.md#modifying-site-properties)社区站点属性输入。[](#aem-analytics-cloud-service-configuration)

![chlimage_1-264](assets/chlimage_1-264.png)

启用视频心跳分析后，视频播放器的Javascript(JS)代码会实例化视频心跳库代码（也包含JS），该代码每10秒（不可配置）处理向Analytics视频跟踪服务器发送视频状态更新的所有逻辑，并最终将视频会话的累积报告发送到主Analytics服务器。

如果未启用，则视频心跳代码从不被实例化，只有视频进度和恢复位置跟踪被保留到SRP以进行报告。

## AEMAnalytics Cloud服务配置{#aem-analytics-cloud-service-configuration}

要创建新的Analytics集成，它使用创作实例上的标准UI将Adobe Analytics与AEM社区站点集成：

* 从全局导航：**[!UICONTROL 工具>部署>Cloud Services]**
* 向下滚动至&#x200B;**[!UICONTROL Adobe Analytics]**
* 选择&#x200B;**[!UICONTROL Configure Now]**&#x200B;或&#x200B;**[!UICONTROL Show Configurations]**

![chlimage_1-265](assets/chlimage_1-265.png)

### 创建配置对话框{#create-configuration-dialog}

* 选择&#x200B;**[!UICONTROL 可用配置]**&#x200B;旁边的`[+]`图标以创建新配置

在“创建配置”对话框中，要输入的值标识配置。

![chlimage_1-266](assets/chlimage_1-266.png)

* **[!UICONTROL 标题]**

   （必需）配置的显示标题。

   例如，输入&#x200B;*Enablement Community Analytics*

* **[!UICONTROL 名称]**

   （可选）如果未指定，则名称将默认为从标题派生的有效节点名称。

   例如，输入&#x200B;*communities*


* **[!UICONTROL 模板]**

   选择 `Adobe Analytics Configuration`

* 选择&#x200B;**[!UICONTROL 创建]**
   * 启动配置页并打开`Analytics Settings`对话框

### 分析设置对话框{#analytics-settings-dialog}

初始创建新的Analytics配置会显示配置，并显示新对话框以输入Analytics设置。 此对话框要求从帐户代表处获取[必备帐户信息](#prerequisites)。

![chlimage_1-267](assets/chlimage_1-267.png)

* **[!UICONTROL 公司]**

   与Adobe Analytics帐户关联的公司

* **[!UICONTROL 用户名]**

   已授权管理Analytics帐户的用户的登录用户名

* **[!UICONTROL 密码]**

   授权用户的登录密码

* **[!UICONTROL 数据中心]**

   选择承载报告包的Analytics数据中心

* **[!UICONTROL 不将跟踪标记添加到页面]**

   保留为默认值（未选中）

* **[!UICONTROL 使用 AppMeasurement]**

   保留为默认值（未选中）

* **[!UICONTROL 夜间不导入页面展示（创作）]**

   保留为默认值（未选中）

* **[!UICONTROL 夜间不导入页面展示（发布）]**

   保留为默认值（选中）

保存设置：


* 选择&#x200B;**[!UICONTROL 连接到Analytics]**

   * 如果不成功，

      * 验证条目不包含前导空格
      * 尝试其他数据中心
      * 联系您的客户代表

* 选择&#x200B;**[!UICONTROL 确定]**


![chlimage_1-268](assets/chlimage_1-268.png)

### 创建框架 {#create-framework}

成功配置与Adobe Analytics的基本连接后，必须为社区站点创建或编辑框架。 该框架的用途是将社区功能(AEM)变量映射到Analytics（报表包）变量。

* 选择&#x200B;**[!UICONTROL 可用框架]**&#x200B;旁边的`[+]`图标以创建新框架

![chlimage_1-269](assets/chlimage_1-269.png)

* **[!UICONTROL 标题]**

   （必需）框架的显示标题

   例如，输入&#x200B;*Enablement Community Framework*

* **[!UICONTROL 名称]**

   （可选）如果未指定，则名称将默认为从标题派生的有效节点名称。

   例如，输入&#x200B;*communities*

* **[!UICONTROL 模板]**

   选择 `Adobe Analytics Framework`

* 选择&#x200B;**[!UICONTROL 创建]**

创建Analytics Framework会打开要配置的框架。

## AEM Analytics Framework配置{#aem-analytics-framework-configuration}

该框架的用途是将AEM变量映射到Analytics变量(evar和事件)。 可用于映射的Analytics变量在报表包](#adobe-analytics-report-suite-for-video-reporting)中定义为[。

![chlimage_1-270](assets/chlimage_1-270.png)

### 选择报表包{#select-report-suite}

选择已设置用于视频报告的报表包。

如果尚未创建或未正确设置报表包，请参阅上一节：\
[Adobe Analytics视频报告套件报告](#adobe-analytics-report-suite-for-video-reporting)

Sidekick不需要，并且可以最小化，以便它不会妨碍对报告包设置的访问。

#### 选择“添加项目”{#report-suites-dialog-before-and-after-selecting-add-item}前后的“报表包”对话框

![chlimage_1-271](assets/chlimage_1-271.png)

1. 选择&#x200B;**[!UICONTROL 添加项目+]**&#x200B;将出现两个下拉框
1. 选择`Report suite`与公司帐户关联的报表包应可供选择
1. 在打开的对话框中选择&#x200B;**[!UICONTROL 是]**:```Load default server settings? Do you want to load the default server settings and overwrite current values in the Server section?```
1. 选择`Run Mode`\
   选择&#x200B;**[!UICONTROL publish]**

![chlimage_1-272](assets/chlimage_1-272.png)

Analytic Cloud服务和框架现已完成。 在启用此Analytics服务的情况下创建社区站点后，将定义映射。

## 为社区站点{#enable-analytics-for-a-community-site}启用分析

### 为新社区站点{#enable-for-new-community-site}启用

在[创建新社区站点](sites-console.md)时添加Analytics云服务：


* 步骤3
* 在[ANALYTICS选项卡](sites-console.md#analytics)下：

   * 选中&#x200B;**[!UICONTROL 启用Analytics]**&#x200B;复选框
   * 从下拉框中选择框架

* （可选）返回到Analytics框架配置以调整变量映射。

### 为现有社区站点{#enable-for-existing-community-site}启用

要将Analytics云服务添加到[现有社区站点](sites-console.md#modifying-site-properties)，请执行以下操作：


* 导航到&#x200B;**[!UICONTROL 社区>站点]**&#x200B;控制台
* 选择社区站点的“编辑站点”图标
* 选择设置
* 在“分析”部分：

   * 选中&#x200B;**[!UICONTROL 启用Analytics]**&#x200B;复选框
   * 从下拉框中选择框架


* （可选）返回到Analytics框架配置以调整变量映射。

### 启用自定义站点{#enable-for-customized-sites}

要使Analytics跟踪和导入能够对社区站点正常工作，必须存在具有`scf-js-site-title`类和href属性的页面元素。 页面上只应存在一个此类元素，如社区站点未修改的`sitepage.hbs`脚本中的元素。 提取`siteUrl`的值并作为&#x200B;*站点路径*&#x200B;发送到Adobe Analytics。

```xml
# present in default sitepage.hbs
# only one scf-js-site-title class should be included
# this example sets it to be hidden as it serves no visual purpose
<div
    class="navbar-brand scf-js-site-title"
    href="{{siteUrl}}.html"
    style="visibility: hidden;"
>
</div>
```

对于叠加`sitepage.hbs`脚本的&#x200B;**自定义社区站点**，请确保元素存在。 当`siteUrl`变量呈现在服务器上后，才会设置到客户端。

对于&#x200B;**通用AEM站点**，它包含Communities组件，但不是使用[站点创建向导](sites-console.md)创建的，必须添加元素。 href值应为站点的路径。 例如，如果站点路径为`/content/my/company/en`，则使用：

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## 社区分析功能{#analytics-for-communities-features}

Analytics可自动用于多个Communities功能。

作者环境的[OSGi配置](../../help/sites-deploying/configuring-osgi.md)、`AEM Communities Analytics Component Configuration`提供了已用于Analytics的组件列表。 变量的自动映射由列出的组件决定。

如果创建了用于Analytics的新自定义组件，则应将这些组件添加到已配置组件的此列表。

### 组件配置{#component-configuration}

![chlimage_1-273](assets/chlimage_1-273.png)

注意：`journal`组件用于实现博客功能。

### 将分析映射到AEM变量{#mapped-analytics-to-aem-variables}

在启用Analytics并选择云配置框架的情况下保存社区站点后，AEM变量将自动映射到分别从evar1和事件1开始的Analytics evar和事件，并增加1。

如果使用现有的报表包将evar1至evar11中的任何变量以及事件1至事件7中的任何变量进行映射，则必须[重新映射AEM变量](#modifying-analytics-variable-mapping)并恢复原始映射。

以下是[入门教程](getting-started-enablement.md)之后默认映射的示例：

![chlimage_1-274](assets/chlimage_1-274.png)

#### 与每个事件{#map-of-evars-sent-with-each-event}一起发送的eVar映射

|  | Enablement Resource Type | 站点标题 | 函数类型 | 组标题 | 组路径 | UGC类型 | UGC标题 | 用户（会员） | UGC路径 | 站点路径 |
|------------------------|------------------------|-----------|--------------|------------|-----------|---------|----------|--------------|---------|----------|
|  | **eVar1** | **eVar2** | **eVar3** | **eVar4** | **eVar5** | **eVar6** | **eVar7** | **eVar8** | **eVar9** | **eVar10** |
| 事件1资源播放 | (某个) | - | - | - | - | - | - | - | (i) | - |
| 事件2SCFView | (某个) | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| 事件3SCFCreate（发布） | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| 事件4SCFFollow | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| 事件5SCFVoteUp | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| 事件6SCFVoteDown | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| 事件7SCFRate | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |

**eVar值示例：**

* [MIME类型](https://www.iana.org/assignments/media-types):video/mp4
* [社区站点标题](sites-console.md#step13asitetemplate):Geometrixx社区
* [社区功能名称](functions.md):论坛
* [社区组名称](creating-groups.md#creating-a-new-group):远足
* 社区组内容的路径：/content/sites/communities/cn/groups/hiking
* [UGC组件资源类型](essentials.md):social/forum/components/hbs/topic
* UGC组件标题：远足主题
* 登录（可授权的Id）:aaron.mcdonald@mailinator.com
* UGC的SRP路径：/content/usergenerated/asi/.../forum/jmtz-topic3或&#x200B;*组件要遵循的路径*:/content/sites/communities/cn/jcr:content/content/primary/forum
* 社区站点内容的路径：/content/sites/community/cn

### 修改分析变量映射{#modifying-analytics-variable-mapping}

在为社区站点启用Analytics后，可以从框架配置中看到Analytics evar和事件到AEM变量的映射。

启用Analytics后，在发布社区站点之前，可以通过将所需的Analyticsevar或事件从左边栏拖放到映射表中的相关行，在框架中更改映射。

要避免重复映射，请务必将替换的Analyticsevar或事件从行中删除，方法是将指针悬停在该行上，然后选择显示在Analytics变量元素右侧的“X”。

如果Communitiesevar和事件覆盖了报表包中先前存在的映射，则为避免数据丢失，请将Communities功能的AEM变量分配给其他Analytics evar和／或事件，并恢复原始映射。

>[!CAUTION]
>
>在启用Analytics的社区站点[已发布](#publishing-the-community-site)之前重新映射很重要，否则存在数据丢失的风险。

#### 示例步骤1:将Analytics evar14拖入映射表{#example-step-dragging-analytics-evar-into-mapping-table}

![chlimage_1-275](assets/chlimage_1-275.png)

#### 示例步骤2:选择“x”以删除已替换的evar11 {#example-step-selecting-x-to-remove-replaced-evar}

![chlimage_1-276](assets/chlimage_1-276.png)

#### 示例步骤3:AEM var eventdata.siteId重新映射到Analytics evar14 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![chlimage_1-277](assets/chlimage_1-277.png)

## 发布社区站点{#publishing-the-community-site}

### 验证分析到AEM变量映射{#verify-analytics-to-aem-variable-mapping}

在发布社区站点之前验证变量映射是明智的，该站点也会发布Analytics云服务和框架。

请参阅以下部分：

* [将分析映射到AEM变量](#mapped-analytics-to-aem-variables)
* [修改分析变量映射](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**如果使用的现有报表包已经在**
>
>* **`evar1`** 至 **`evar11`**
>* **`event1`** 至 **`event7`**

>
>
**然后，在发布社区站点** 之前，务必恢复先前存在的映射并将自动映射的社区AEM变量（在为社区站点启用Analytics时）移动到其他Analytics变量。此重新映射应在所有社区组件之间保持一致。
>
>否则可能导致无法恢复的数据丢失。

### 主发布者{#primary-publisher}

当选择的部署是[发布场](topologies.md#tarmk-publish-farm)时，必须将一个AEM发布实例标识为轮询Adobe Analytics以将报告数据写入[SRP](working-with-srp.md)的主发布者。

默认情况下，`AEM Communities Publisher Configuration` OSGi配置将其发布实例标识为主发布者，这样发布场中的所有发布实例都将自标识为主发布者。

因此，必须编辑所有辅助发布实例上的配置以取消选中&#x200B;**主发布者**&#x200B;复选框。

有关具体说明，请参阅[部署社区](deploy-communities.md#primary-publisher)的主要发布者部分。

>[!CAUTION]
>
>配置主发布者以阻止多个发布实例进行轮询很重要。

### 复制加密密钥{#replicate-the-crypto-key}

Adobe Analytics的凭据已加密。 为了方便作者和发布者之间复制或传输加密的分析凭据，所有AEM实例必须共享相同的主加密密钥。

为此，请按照[复制加密密钥](deploy-communities.md#replicate-the-crypto-key)中的说明操作。

### 发布社区站点和Analytics Cloud服务{#publish-community-site-and-analytics-cloud-service}

为社区站点启用Analytics云服务后，如果需要，[将Analytics映射到AEM变量的映射已调整](#mapped-analytics-to-aem-variables)，则必须通过[(re)发布社区站点](sites-console.md#publishing-the-site)将配置复制到发布环境。

## 从Analytics {#obtaining-reports-from-analytics}获取报告

### 报告管理{#report-management}

作者和主发行商的[OSGi配置](../../help/sites-deploying/configuring-osgi.md)`AEM Communities Analytics Report Management`用于查询分析。

作者可以查询实时报告。

在主发布者上，查询用于提供准备报表导入程序的分析数据导入的信息。

查询间隔默认为10秒。

### 报表导入程序{#report-importer}

一旦发布了启用分析的社区站点，主发布者的[OSGi配置](../../help/sites-deploying/configuring-osgi.md)、`AEM Communities Analytics Report Importer`可以配置为那些未在CRXDE中单独配置的配置设置默认轮询间隔。

轮询间隔控制向Adobe Analytics请求数据的频率，以将数据提取并保存到[SRP](working-with-srp.md)中。

当数据可能被归类为“大数据”时，更频繁的民意测验可能会给社区站点带来很大负担。

默认轮询&#x200B;**导入间隔**&#x200B;设置为12小时。

![chlimage_1-278](assets/chlimage_1-278.png)

### 组件报告自定义{#component-report-customization}

目前，为了自定义要跟踪的度量，在存储库中创建节点，该节点定义要为该度量生成报告的时间段。

论坛主题目前是此自定义的唯一示例：

* 在主发布者上
* 以管理权限登录
* 导航到[CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   * 例如，[http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* 在语言根的`jcr:content`节点下

   * 例如，`/content/sites/engage/en/jcr:content`

* 导航到为Analytics报告配置的组件

   * 例如，`analytics/reportConfigs/social_forum_components_hbs_topic`

* 注意创建的时段

   * `last30Days`
   * `last90Days`
   * `thisYear`

* 注意`total`节点

   * 修改`interval`属性将覆盖报表导入程序间隔
   * 该值以秒为单位，并设置为4小时（14400秒）

![chlimage_1-279](assets/chlimage_1-279.png)

## 在Analytics {#manage-user-data-in-analytics}中管理用户数据

Adobe Analytics提供的API允许您访问、导出和删除用户数据。 有关详细信息，请参阅[提交访问和删除请求](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html)。

## 资源 {#resources}

* Adobe Marketing Cloud:[分析帮助和参考](https://docs.adobe.com/content/help/en/analytics/landing/home.html)
* AEM:[与Adobe Analytics集成](../../help/sites-administering/adobeanalytics.md)
* AEM:[具有外部提供者的分析](../../help/sites-administering/external-providers.md)

