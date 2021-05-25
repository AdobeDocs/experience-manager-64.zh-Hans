---
title: 与Adobe Target集成的先决条件
seo-title: 与Adobe Target集成的先决条件
description: 了解与Adobe Target集成的先决条件。
seo-description: 了解与Adobe Target集成的先决条件。
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
exl-id: f47e5c6a-ed52-4493-83bd-73e5e693d117
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 3%

---

# 与Adobe Target集成的先决条件{#prerequisites-for-integrating-with-adobe-target}

作为AEM与Adobe Target](/help/sites-administering/target.md)集成的一部分，您需要在Adobe Target中注册，配置复制代理，以及在发布节点上保护活动设置的安全。[

## 向Adobe Target注册{#registering-with-adobe-target}

要将AEM与Adobe Target集成，您必须拥有有效的Adobe Target帐户。 此帐户必须至少具有**审批者**级权限。 在Adobe Target注册后，您会收到一个客户端代码。 您需要客户端代码以及Adobe Target登录名和密码才能将AEM连接到Adobe Target。

客户端代码在调用Adobe Target服务器时标识Adobe Target客户帐户。

>[!NOTE]
>
>您的帐户还必须由Target团队启用，才能使用集成。
>
>
>如果不是这种情况，请联系[Adobe Target客户关怀团队](https://docs.adobe.com/content/help/en/target/using/cmp-resources-and-contact-information.html)。

## 启用目标复制代理{#enabling-the-target-replication-agent}

必须在创作实例上启用测试和目标[复制代理](/help/sites-deploying/replication.md)。 请注意，如果您使用[nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent)运行模式安装AEM，则默认情况下不会启用此复制代理。 有关保护生产环境的更多信息，请参阅[安全检查列表](/help/sites-administering/security-checklist.md)。

1. 在AEM主页上，单击或点按&#x200B;**工具** > **部署** > **复制**。
1. 单击或点按&#x200B;**创作代理**。
1. 单击或点按&#x200B;**测试与目标（测试与目标）**&#x200B;复制代理，然后单击或点按&#x200B;**编辑**。
1. 选择启用选项，然后单击或点按&#x200B;**确定**。

   >[!NOTE]
   >
   >配置Test和Target复制代理时，在&#x200B;**Transport**&#x200B;选项卡中，URI默认设置为&#x200B;**tnt:///**。 请勿将此URI替换为&#x200B;**https://admin.testandtarget.omniture.com**。
   >
   >请注意，如果尝试使用&#x200B;**tnt:///**&#x200B;测试连接，将引发错误。 这是预期行为，因为此URI仅供内部使用，不应与&#x200B;**Test Connection**&#x200B;一起使用。

## 保护活动设置节点{#securing-the-activity-settings-node}

您必须保护发布实例上的活动设置节点&#x200B;**cq:ActivitySettings**，以便普通用户无法访问该节点。 该活动设置节点应当只能由负责将活动同步到 Adobe Target 的服务访问。

**cq:ActivitySettings**&#x200B;节点可在CRXDE lite中的`/content/campaigns/*nameofbrand*`* *活动jcr:content节点下；* *例如`/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`下找到。 此节点仅在您定位组件后创建。

活动jcr:content下的&#x200B;**cq:ActivitySettings**&#x200B;节点受以下ACL保护：

* 拒绝所有人
* 允许“target-activity-authors”的jcr:read，rep:write（作者是此组的成员，开箱即用）
* 允许“targetservice”的jcr:read，rep:write

这些设置可确保普通用户无权访问节点属性。 在创作和发布时使用相同的ACL。 有关更多信息，请参阅[用户管理和安全](/help/sites-administering/security.md)。

## 配置AEM外部器{#configuring-the-aem-externalizer}

在Adobe Target中编辑活动时，该URL将指向&#x200B;**localhost**，除非您更改AEM创作节点上的URL。

配置AEM外部器：

1. 导航到位于&#x200B;**https://&lt;server>的OSGi Web控制台：&lt;port>/system/console/configMgr.**
1. 找到&#x200B;**Day CQ Link Externalizer**&#x200B;并输入创作节点的域。

   ![chlimage_1-120](assets/chlimage_1-120.png)
