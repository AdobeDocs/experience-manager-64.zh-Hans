---
title: 体验已发布的站点
seo-title: 体验已发布的站点
description: 浏览到已发布的站点
seo-description: 浏览到已发布的站点
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7

---


# 体验已发布的站点 {#experience-the-published-site}

## 浏览到发布时的新站点 {#browse-to-new-site-on-publish}

新创建的社区站点已发布，现在浏览至创建站点时显示的URL，但在发布服务器上，例如

* 作者URL = http://localhost:4502/content/sites/engage/en.html
* 发布URL = http://localhost:4503/content/sites/engage/en.html

为最大限度地减少在创作和发布时登录到哪个成员的混淆，建议为每个实例使用不同的浏览器。

首次到达已发布的站点时，站点访客通常尚未登录，且为匿名访客。

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## 匿名网站访客 {#anonymous-site-visitor}

匿名网站访客在UI中可看到以下内容：

* 站点的标题。 哪个入门教程
* 无配置文件链接
* 无消息链接
* 无通知链接
* 沙奇场
* 登录链接
* 品牌横幅
* 引用站点模板中包含的组件的菜单链接

如果选择各种链接，您会发现它们处于只读模式。

## 防止对JCR进行匿名访问 {#prevent-anonymous-access-on-jcr}

已知限制通过jcr内容和json向匿名访客公开社区站点内容，但 **对于站点内容** ，允许匿名访问是禁用的。 但是，可以使用Sling Restrictions作为解决方法来控制此行为。

要保护您的社区站点的内容免受匿名用户通过jcr内容和json访问，请执行以下步骤：

1. 在AEM作者实例中，转到https://&lt;host>:&lt;port>/editor.html/content/site/&lt;sitename>.html。

   >[!NOTE]
   >
   >请勿转到本地化的站点。

1. 转至页 **[!UICONTROL 面属性]**。

   ![站点身份验证](assets/site-authentication.png)

1. 转到“高 **[!UICONTROL 级]** ”选项卡。

   ![page-properties](assets/page-properties.png)

1. Enable **[!UICONTROL Authentication Requirement]**.
1. 添加登录页面的路径。 For example, `/content/......./GetStarted`.
1. 发布页面。

## 受信任的社区会员 {#trusted-community-member}

此体验假定 [Aaron mcDonald](tutorials.md#demo-users) 被分配为社区经 [理和主持人的角色](create-site.md#roles)。 如果没有，则返回创作环境以修 [改站点设置](sites-console.md#modifying-site-properties) ，并选择Aaron mcDonald作为社区经理和版主。

在右上角，选择并 `Log in`使用用户名“aaron.mcdonald@mailinator.com”和密码“password”进行签名。 注意使用Twitter或Facebook凭据登录的能力。

![chlimage_1-312](assets/chlimage_1-312.png)

登录后，请注意，会出现一个新的菜单项， `Administration`该菜单项显示是因为该成员被授予了审查方的角色。 现在，选择各种链接会更有趣。

![chlimage_1-313](assets/chlimage_1-313.png)

请注意，“日历”页面是主页，因为所选的“参考站点模板”首先包含“日历”功能，然后是“活动流”功能、“论坛”功能等。 此结构可在“站点模板”控 [制台中或在创作环境中](sites.md#edit-site-template) ，修改站点属性时显示：

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>有关Communities组件和功能的更多信息，请访问
>
>* [社区组件](author-communities.md) （针对作者）
>* [组件、功能和功能基本工具](essentials.md) （针对开发人员）
>



## 论坛链接 {#forum-link}

通过选择“论坛”链接查看基本论坛功能。

会员可以发布新主题或关注主题。

站点访问者可以查看帖子并以各种方式对其进行排序。

![chlimage_1-315](assets/chlimage_1-315.png)

## 用户组链接 {#groups-link}

由于Aaron是组管理员，选择“组”链接将允许Aaron通过选择组模板、图像、组是打开还是秘密以及邀请成员来创建新的社区组。

这是在发布环境中创建组的示例。

用户组也可以在创作环境中创建，并在创作环境（“社区组”控制台）的社区站 [点中进行管理](groups.md)。 本教程的下 [一步是创建作者组](nested-groups.md) 。

![chlimage_1-316](assets/chlimage_1-316.png)

创建引用组：

1. 选择 **[!UICONTROL 新组]**
1. **[!UICONTROL 设置选项卡]**
   * 组名称: `Sports`
   * 描述: `A parent group for various sporting groups`
   * 组 URL 名称: `sports`
   * 选择 `Open Group` （允许任何社区成员通过加入来参加）
1. **[!UICONTROL 模板选项卡]**
   * 选择 `Reference Group` （在其结构中包含组函数以允许嵌套组）
1. 选择 **[!UICONTROL 创建组]**

![chlimage_1-317](assets/chlimage_1-317.png)

创建新组后，选择 **新的“体育组** ”，以便在其中创建两个组（嵌套）。 由于站点结构不能从组功能开始，打开运动组后，必须选择组链接：

![chlimage_1-318](assets/chlimage_1-318.png)

第二组链接(从开始 `Blog`)属于当前选定的组，即 `Sports`组。 通过选择“体育” `Groups` 链接，可以将两个组嵌套在“体育”组中。

例如，添加两个 `ew groups.`

* 一个 `Baseball`
   * 将其设置为 `Open Group` （必需会员资格）
   * 在“模板”选项卡上，选择 `Conversational Group`
* 一个 `Gymnastics`
   * 将其设置更改为 `Member Only Group` （受限会员资格）
   * 在“模板”选项卡上，选择 `Conversational Group`

**通知**:

* 在显示两个组之前，可能需要刷新页面
* 此模板不*包含组功能，因此不可能再嵌套组
* 在创作时，“组 [”控制台提供第](groups.md) 三个选择- `Public Group` （可选会员资格）

创建两个组后，选择“棒球”组（打开的组），并注意其链接：组 `Discussions` 的链 `What's New``Members`接显示在主站点的链接下方，并会显示以下内容：

![chlimage_1-319](assets/chlimage_1-319.png)

在创作时——具有管理权限，导航到“社 [区组”控制台](members.md) ，并将Weston mcCall添加到 `Community Engage Gymnastics <uid> Members` 组。

继续发布，以Aaron mcDonald身份登录，以匿名网站访问者身份查看体育组中的组：

* 从主页
* 选择链 `Groups`接
* 选择链 `Sports`接
* 选择体育链 `Groups`接

只有“棒球”组可见。

以Weston mcCall(weston.mccall@dodgit.com /密码)的身份登录，然后导航到同一位置。 注意，Weston能够访问打开 `Join` 的组 `Baseball` 和私有 `enter or Leave` 组之 `Gymnastics`一。

![chlimage_1-320](assets/chlimage_1-320.png)

## 网页链接 {#web-page-link}

通过选择网页链接查看包含在站点中的基本网页。 标准AEM创作工具可用于在创作环境中向此页面添加内容。

例如，转到作 **者实例** ，在“社区站点”控制台 `engage` 中打开文件夹 [，选择“打开站点](sites-console.md)**** ”图标以进入作者编辑模式。 然后选择预览模式以选择链 `Web Page`接，然后选择编辑模式以添加标题和文本组件。 最后，只发布页面或整个站点。

![chlimage_1-321](assets/chlimage_1-321.png)

## 管理链接 {#administration-link}

当社区成员具有审核权限时，将显示“管理”链接，选择该链接后，将显示发布的社区内容并允许以类似于创作环境中的审核控制台的方式 [进行审核](moderate-ugc.md)[](moderation.md) 。

使用浏览器的返回按钮返回已发布的站点。 大多数控制台都无法通过发布环境中的全局导航访问。

![chlimage_1-322](assets/chlimage_1-322.png)

## 自助注册 {#self-registration}

注销后，可以创建新用户注册。

* 选择 `Log In`
* 选择 `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

默认情况下，电子邮件地址为登录ID。 如果未选中，访客可以输入自己的登录ID（用户名）。 用户名在发布环境中必须是唯一的。

指定用户名、电子邮件和密码后，选择该 `Sign Up`选项将创建用户并允许其签名。

登录后，显示的第一页即为其页 `Profile`面，用户可以对其进行个性化设置。

![chlimage_1-325](assets/chlimage_1-325.png)

如果成员忘记了其登录ID，则可以使用其电子邮件地址进行恢复。

![chlimage_1-326](assets/chlimage_1-326.png)
