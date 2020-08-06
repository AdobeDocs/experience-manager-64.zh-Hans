---
title: AEM Communities用户与UGC管理服务
seo-title: AEM Communities用户与UGC管理服务
description: '使用API批量删除和批量导出用户生成的内容，并禁用用户帐户。 '
seo-description: '使用API批量删除和批量导出用户生成的内容，并禁用用户帐户。 '
uuid: f4663825-eac8-4ef5-8253-46875e0cd71d
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
discoiquuid: f564759f-fb56-4f70-a7b1-286a223755c6
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# AEM Communities用户与UGC管理服务 {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>GDPR在以下各节中用作示例，但涵盖的详细信息适用于所有数据保护和隐私法规； 例如GDPR、CCPA等。

AEM Communities公开现成的API，用于管理用户用户档案和批量管理用户生成的内容(UGC)。 启用后，UserUgcManagement **服务允许特权用户** （社区管理员和版主）禁用用户用户档案，并批量删除或批量导出特定用户的UGC。 这些API还使客户数据的控制者和处理器能够遵守欧洲合并的一般数据保护规定(GDPR)和其他受GDPR启发的隐私规定。

有关详细信息，请 [参阅Adobe隐私中心的GDPR页面](https://www.adobe.com/privacy/general-data-protection-regulation.html)。

>[!NOTE]
>
>如果您在 [AEM Communities站点中配置](analytics.md) “Adobe Analytics”，则捕获的用户数据将发送到Adobe Analytics服务器。 Adobe Analytics提供的API允许您访问、导出和删除用户数据并遵守GDPR。 有关详细信息，请参 [阅提交访问和删除请求](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html)。

要使用这些API，您需要通过激 `/services/social/ugcmanagement` 活UserUgcManagement服务来启用端点。 要激活此服务，请安 [装GitHub](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) .com上 [提供的示例servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet)。 然后，使用http请求，在社区站点的发布实例上使用适当的参数点击端点，如下所示：

`http://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation<getUgc>`

但是，您也可以构建UI（用户界面）来管理系统中的用户用户档案和用户生成的内容。

这些API支持执行以下功能。

## 检索用户的UGC {#retrieve-the-ugc-of-a-user}

`getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)` 帮助从系统中导出用户的所有UGC。

* **用户**: 用户的可授权ID。
* **outputStream**: 结果将作为输出流返回，该输出流是包含用户生成的内容（作为json文件）和附件（包括用户上传的图像或视频）的zip文件。

例如，要导出名为Weston McCall的用户的UGC(他使用weston.mccall@dodgit.com作为可授权的ID登录到社区站点)，可以发送与以下内容类似的httpGET请求：

`http://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## 删除用户的UGC {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)帮助** 从系统中删除用户的所有UGC。

* **用户**: 用户的可授权ID。

例如，要通过http-POST请求删除具有可授权ID weston.mccall@dodgit.com的用户的UGC，请使用以下参数：

* 用户= weston.mccall@dodgit.com
* operation= deleteUgc

### 从Adobe Analytics删除UGC {#delete-ugc-from-analytics}

要从Adobe Analytics删除用户数据，请遵循GDPR分析工作流程； 因为API不会从Adobe Analytics删除用户数据。

有关AEM Communities使用的Adobe Analytics变量映射，请参阅下图：

![AEM社区变量映射Adobe Analytics](assets/Analytics-Communities-Mapping.png)

## 禁用用户帐户 {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)帮助禁用** 用户帐户。

* **用户**: 用户的可授权ID。

>[!NOTE]
>
>禁用用户将删除用户在服务器上拥有的所有用户生成的内容。

例如，要通过http-用户档案请求删除具有可授权ID weston.mccall@dodgit.com的用户的POST，请使用以下参数：

* 用户= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>deleteUserAccount()API仅禁用系统中的用户用户档案并删除UGC。 但是，要从系统中删除用户用户档案，请导航到 **CRXDE Lite**: [https://&lt;server>/crx/de](http://localhost:4502/crx/de)，找到用户节点并将其删除。
