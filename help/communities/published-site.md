---
title: 体验已发布的网站
seo-title: Experience the Published Site
description: 浏览到已发布的网站
seo-description: Browse to a published site
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
exl-id: 8f716a59-1116-4855-baeb-3997de71b55f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 1%

---

# 体验已发布的网站 {#experience-the-published-site}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 在发布时浏览到新站点 {#browse-to-new-site-on-publish}

现在，新创建的社区站点已发布，浏览到创建站点时显示的URL，但是在发布服务器上，例如

* 作者URL = http://localhost:4502/content/sites/engage/en.html
* 发布URL = http://localhost:4503/content/sites/engage/en.html

为了最大限度地减少在创作和发布时登录到哪个成员的混淆，建议对每个实例使用不同的浏览器。

首次访问已发布的网站时，网站访客通常尚未登录，且为匿名访客。

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## 匿名网站访客 {#anonymous-site-visitor}

匿名网站访客在UI中看到以下内容：

* 网站的标题。 哪个是入门教程
* 无配置文件链接
* 无消息链接
* 无通知链接
* 搜索字段
* 登录链接
* 品牌横幅
* 引用站点模板中包含的组件的菜单链接

如果选择各种链接，则会发现它们处于只读模式。

## 阻止对JCR的匿名访问 {#prevent-anonymous-access-on-jcr}

尽管如此，已知的限制会通过jcr内容和json向匿名访客公开社区站点内容 **允许匿名访问** 对于网站的内容禁用。 但是，可以使用Sling限制作为解决方法来控制此行为。

要保护您的社区站点内容免遭匿名用户通过jcr内容和json访问，请执行以下步骤：

1. 在AEM创作实例上，转到https://&lt;host>:&lt;port>/editor.html&lt;sitename>.html.

   >[!NOTE]
   >
   >请勿转到本地化的站点。

1. 转到 **[!UICONTROL 页面属性]**.

   ![网站验证](assets/site-authentication.png)

1. 转到 **[!UICONTROL 高级]** 选项卡。

   ![page-properties](assets/page-properties.png)

1. 启用 **[!UICONTROL 身份验证要求]**.
1. 添加登录页面的路径。 例如：`/content/......./GetStarted`。
1. 发布页面。

## 受信任的社区成员 {#trusted-community-member}

此体验假定为 [亚伦·麦当诺](tutorials.md#demo-users) 已分配 [社区经理和主持人](create-site.md#roles). 如果没有，请返回创作环境以 [修改站点设置](sites-console.md#modifying-site-properties) 并选择Aaron McDonald作为社区经理和主持人。

在右上角，选择 `Log in`，并使用用户名“aaron.mcdonald@mailinator.com”和密码“password”进行签名。 请注意使用Twitter或Facebook凭据登录的功能。

![chlimage_1-312](assets/chlimage_1-312.png)

登录后，请注意有一个新的菜单项， `Administration`，因为会员被授予主持人角色。 现在，选择各种链接会更有趣。

![chlimage_1-313](assets/chlimage_1-313.png)

请注意，日历页面是主页，因为所选的引用站点模板首先包含日历函数，然后是活动流函数、论坛函数等。 此结构在 [网站模板](sites.md#edit-site-template) 控制台或在创作环境中修改站点属性时：

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>有关社区组件和功能的更多信息，请访问
>
>* [社区组件](author-communities.md) （对于作者）
>* [组件、函数和功能要点](essentials.md) （对于开发人员）
>


## 论坛链接 {#forum-link}

通过选择“论坛”链接，查看基本论坛功能。

成员可以发布新主题或关注主题。

网站访客能够查看帖子并以各种方式对其进行排序。

![chlimage_1-315](assets/chlimage_1-315.png)

## 群组链接 {#groups-link}

由于Aaron是群组管理员，因此选择群组链接将允许Aaron通过选择群组模板、图像（无论群组是开放还是保密）并邀请成员来创建新的社区群组。

例如，会在发布环境中创建群组。

也可以在创作环境中创建组，并在创作环境( [社区组控制台](groups.md))。 体验 [创建创作组](nested-groups.md) 下一个教程中。

![chlimage_1-316](assets/chlimage_1-316.png)

创建引用组：

1. 选择 **[!UICONTROL 新建组]**
1. **[!UICONTROL “设置”选项卡]**
   * 组名称: `Sports`
   * 描述: `A parent group for various sporting groups`
   * 组 URL 名称: `sports`
   * 选择 `Open Group` （允许任何社区成员通过加入参与）
1. **[!UICONTROL “模板”选项卡]**
   * 选择 `Reference Group` （在其结构中包含允许嵌套组的组函数）
1. 选择 **[!UICONTROL 创建群组]**

![chlimage_1-317](assets/chlimage_1-317.png)

创建新群组后， **选择新的体育组** 以在其中创建两个组（嵌套）。 由于网站结构不能以组功能开头，因此在打开“体育”组后，需要选择“组”链接：

![chlimage_1-318](assets/chlimage_1-318.png)

第二组链接，以 `Blog`，则属于当前选定的群组， `Sports`群组。 选择“体育” `Groups` 链接时，可以在“体育”组中嵌套两个组。

例如，添加两个n `ew groups.`

* 一个已确认 `Baseball`
   * 将其设置为 `Open Group` （必需的会员资格）
   * 在“模板”选项卡上，选择 `Conversational Group`
* 一个已确认 `Gymnastics`
   * 将其设置更改为 `Member Only Group` （会员资格受限）
   * 在“模板”选项卡上，选择 `Conversational Group`

**通知**:

* 在显示两个组之前，可能需要刷新页面
* 此模板*不*包含组函数，因此无法再进一步嵌套组
* 在作者中， [“组”控制台](groups.md) 提供了第三种选择 — a `Public Group` （可选会员资格）

创建两个组后，选择打开的组“棒球组”，并注意其链接： `Discussions` `What's New` `Members`
群组的链接显示在主网站链接的下方，并会显示以下内容：

![chlimage_1-319](assets/chlimage_1-319.png)

在创作时 — 具有管理权限，导航到 [“社区组”控制台](members.md) 把韦斯顿·麦考尔加到 `Community Engage Gymnastics <uid> Members` 群组。

继续发布内容，以Aaron McDonald身份登录，并以匿名网站访客的身份查看体育组中的群组：

* 从主页
* 选择 `Groups`链接
* 选择 `Sports`链接
* 选择体育 `Groups`链接

只有棒球组可见。

以Weston McCall(weston.mccall@dodgit.com /密码)的身份登录，然后导航到同一位置。 注意，韦斯顿能 `Join` 打开 `Baseball` 群组及 `enter or Leave` 私人 `Gymnastics`群组。

![chlimage_1-320](assets/chlimage_1-320.png)

## 网页链接 {#web-page-link}

通过选择网页链接查看网站中包含的基本网页。 标准AEM创作工具可用于在创作环境中向此页面添加内容。

例如，转到 **作者** 实例，打开 `engage` 文件夹 [社区站点控制台](sites-console.md)，选择 **打开网站** 图标以进入创作编辑模式。 然后选择预览模式以选择 `Web Page`链接，然后选择编辑模式以添加标题和文本组件。 最后，只重新发布页面或整个网站。

![chlimage_1-321](assets/chlimage_1-321.png)

## 管理链接 {#administration-link}

当社区成员具有审核权限时，将显示“管理”链接，选择该链接后，将显示已发布的社区内容并允许其发布 [已审核](moderate-ugc.md) 与 [审核控制台](moderation.md) 在创作环境中。

使用浏览器的“返回”按钮返回到已发布的网站。 大多数控制台无法在发布环境中通过全局导航访问。

![chlimage_1-322](assets/chlimage_1-322.png)

## 自注册 {#self-registration}

注销后，可以创建新用户注册。

* 选择 `Log In`
* 选择 `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

默认情况下，电子邮件地址为登录ID。 如果未选中，则访客可以输入自己的登录ID（用户名）。 在发布环境中，用户名必须唯一。

指定用户名、电子邮件和密码后，选择 `Sign Up`将创建用户并允许他们进行签名。

登录后，显示的第一个页面是 `Profile`页面，用户可以对其进行个性化。

![chlimage_1-325](assets/chlimage_1-325.png)

如果成员忘记了其登录ID，则可以使用其电子邮件地址进行恢复。

![chlimage_1-326](assets/chlimage_1-326.png)
