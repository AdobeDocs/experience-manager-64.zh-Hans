---
title: 创建已关闭的用户组
seo-title: 创建已关闭的用户组
description: 了解如何创建已关闭的用户组。
seo-description: 了解如何创建已关闭的用户组。
uuid: 03d5fc69-6e4b-41c1-88c9-7454250c29ac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: ba73e267-598d-4c70-a1a8-71bcfcfbf9e5
translation-type: tm+mt
source-git-commit: 1e55d049ad77aeed2fac6275ea2744c2b6551e43
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---


# 创建已关闭的用户组{#creating-a-closed-user-group}

已关闭的用户组(CUG)用于限制对已发布Internet站点内特定页面的访问。 此类页面需要分配的成员登录并提供安全凭据。

要在网站中配置此区域，您需要：

* [创建实际已关闭的用户组并分配成员](#creating-the-user-group-to-be-used)。

* [将此组应用到所需页面](#applying-your-closed-user-group-to-content-pages) ，并选择（或创建）供CUG成员使用的登录页面； 在将CUG应用到内容页面时也指定。

* [创建一个链接（某些表单），指向保护区域内的至少一个页面](#linking-to-the-realm)，否则它将不可见。
* [如果正在使用](#configure-dispatcher-for-cugs) ，请配置Dispatcher。

>[!CAUTION]
>
>应始终在创建封闭用户组(CUG)时注重性能。
>
>尽管CUG中的用户和用户组数量不受限制，但页面上的CUG数量较多可能会降低渲染性能。
>
>执行性能测试时，应始终考虑CUG的影响。

## 创建要使用的用户组 {#creating-the-user-group-to-be-used}

要创建已关闭的用户组，请执行以下操作：

1. 从AEM **主屏幕转到** “工具——安全”。

   >[!NOTE]
   >
   >有关创 [建和配置用户](/help/sites-administering/security.md#managing-users-and-groups) 和用户组的完整信息，请参阅管理用户和用户组。

1. 从下 **一屏** ，选择组卡。

   ![screestop_2018-10-30at145502](assets/screenshot_2018-10-30at145502.png)

1. 按右 **上角** 的“创建”按钮以创建新组。
1. 命名新组； 例如 `cug_access`,

   ![screestop_2018-10-30at151459](assets/screenshot_2018-10-30at151459.png)

1. 转到“成 **员** ”选项卡，将所需用户分配到此组。

   ![screestop_2018-10-30at151808](assets/screenshot_2018-10-30at151808.png)

1. 激活您分配给您的CUG的所有用户； 在这种情况下，所有成员 `cug_access`。
1. 激活已关闭的用户组，使其在发布环境中可用； 在本例中 `cug_access`,

## 将已关闭的用户组应用到内容页面 {#applying-your-closed-user-group-to-content-pages}

要将CUG应用于页面，请执行以下操作：

1. 导航到要分配给CUG的受限部分的根页面。
1. 单击页面的缩略图，然后单击顶 **部面板** 中的属性。

   ![screestop_2018-10-30at162632](assets/screenshot_2018-10-30at162632.png)

1. 在下面的窗口中，转到高级 **选项卡** 。
1. 向下滚动并启用“身份验证要求” **部分中的** “复选框”。

1. 在下面添加配置路径，然后按保存。
1. 然后，转到“权限” **选项卡** ，并按“编 **辑已关闭的用户组** ”按钮。

   ![screestop_2018-10-30at163003](assets/screenshot_2018-10-30at163003.png)

   >[注意!]
   >
   > 请注意，“权限”选项卡中的CUG无法从Blueprint回滚到Live Copy。 请在配置Live Copy时针对此进行规划。
   >
   > 有关详细信息，请参 [阅此页](closed-user-groups.md#aem-livecopy)。

1. 在以下窗口中查找并添加您的CUG —— 在本例中，添加名为 **cug_access的组**。 最后，按“ **保存**”。
1. 单击 **启用** ，以定义此页面（和任何子页面）属于CUG。
1. 指定 **组成员** 将使用的登录页面； 例如：

   `/content/geometrixx/en/toolbar/login.html`

   这是可选的，如果留空，则将使用标准登录页面。

1. 添加已 **承认的组**。 使用+可添加用户组，使用——可删除。 只允许这些组的成员登录并访问页面。
1. 根据需要 **指** 定领域（页面组的名称）。 留空将使用页面标题。
1. Click **OK** to save the specification.

请参 [阅Identity Management](/help/sites-administering/identity-management.md) ，了解有关发布环境中用户档案以及提供登录和注销表单的信息。

## 链接到领域 {#linking-to-the-realm}

由于匿名用户看不到任何指向CUG领域的链接的目标，链接检查器将删除此类链接。

要避免这种情况，建议创建指向CUG领域内页面的未受保护重定向页面。 然后渲染导航条目，而不会导致链接检查器出现任何问题。 仅当实际访问重定向页面时，用户才会在CUG领域内重定向——成功提供其登录凭据后。

## 为CUG配置调度程序 {#configure-dispatcher-for-cugs}

如果您使用的是Dispatcher，则需要定义具有以下属性的Dispatcher群：

* [virtualhosts](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts): 匹配CUG所应用的页面的路径。
* \会话管理： 请参见下文。
* [缓存](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache): 专用于CUG所应用的文件的缓存目录。

### 为CUG配置调度程序会话管理 {#configuring-dispatcher-session-management-for-cugs}

在 [CUG的dispatcher.any文件中配置会话](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) 管理。 请求CUG页面访问时使用的身份验证处理程序决定如何配置会话管理。

```xml
/sessionmanagement
    ...
    /header "Cookie:login-token" 
    ...
```

>[!NOTE]
>
>当调度程序群启用会话管理时，不会缓存该群处理的所有页面。 要缓存CUG外的页面，请在dispatcher.any中创建第二个场\
>处理非CUG页面。

1. 通过 [定义](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) ，配置／会话管 `/directory`理； 例如：

   ```xml
   /sessionmanagement
     {
     /directory "/usr/local/apache/.sessions"
     ...
     }
   ```

1. 将 [/allowAuthorized](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html#caching-when-authentication-is-used) 设置为 `0`。

