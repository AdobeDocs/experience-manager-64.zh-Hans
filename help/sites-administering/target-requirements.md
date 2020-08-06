---
title: 与Adobe Target整合的先决条件
seo-title: 与Adobe Target整合的先决条件
description: 了解与Adobe Target集成的先决条件。
seo-description: 了解与Adobe Target集成的先决条件。
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 3%

---


# 与Adobe Target整合的先决条件{#prerequisites-for-integrating-with-adobe-target}

作为AEM和Adobe Target [集成的一部分](/help/sites-administering/target.md)，您需要向Adobe Target注册，配置复制代理，并在发布节点上安全活动设置。

## 向Adobe Target注册 {#registering-with-adobe-target}

要将AEM与Adobe Target集成，您必须拥有有效的Adobe Target帐户。 此帐户至少必须具有**审批者**级别权限。 当你向Adobe Target注册时，你会收到一个客户代码。 您需要客户端代码和Adobe Target登录名和密码才能将AEM连接到Adobe Target。

客户代码在调用Adobe Target服务器时标识Adobe Target客户帐户。

>[!NOTE]
>
>目标团队还必须启用您的帐户才能使用集成。
>
>
>如果不是这样，请联系 [Adobe Target客户服务](https://docs.adobe.com/content/help/en/target/using/cmp-resources-and-contact-information.html)。

## 启用目标复制代理 {#enabling-the-target-replication-agent}

必须在创作实 [例上启用](/help/sites-deploying/replication.md) “测试和目标”复制代理。 请注意，如果您使用nosamplecontent运行模式安装AEM，则 [默认情况下](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) 不启用此复制代理。 有关保护生产环境的更多信息，请参阅安 [全核对清单](/help/sites-administering/security-checklist.md)。

1. 在AEM主页上，单击或点按 **工具** > **部署** > **复制**。
1. 单击或点按作 **者上的代理**。
1. 单击或点按测 **试和目标(测试和目标)复** 制代理 **，然后单击或点按**&#x200B;编辑。
1. 选择“启用”选项，然后单击或点 **按确定**。

   >[!NOTE]
   >
   >配置测试和目标复制代理时，在“传输 **”选** 项卡中，URI默认设置为 **tnt:///**。 请勿将此URI替换为 **https://admin.testandtarget.omniture.com**。
   >
   >请注意，如果尝试使用tnt:///测试连接 ****，将引发错误。 这是预期行为，因为此URI仅供内部使用，不应与测试连接 **一起使用**。

## 保护活动设置节点 {#securing-the-activity-settings-node}

You must secure the activity settings node **cq:ActivitySettings** on the publish instance so that it is inaccessible to normal users. 该活动设置节点应当只能由负责将活动同步到 Adobe Target 的服务访问。

cq: **ActivitySettings节点** ，在CRXDE lite的jcr:content节点 `/content/campaigns/*nameofbrand*`*下， *活动jcr:content节点下可用；* *例如 `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`。 此节点仅在目标组件后创建。

活动 **的jcr** :content下的cq:ActivitySettings节点受以下ACL的保护：

* 拒绝所有人
* 允许“目标-活动-作者”的jcr:read,rep:write（作者是此组的成员，开箱即用）
* 允许jcr:read,rep:write for &quot;targetservice&quot;

这些设置确保普通用户无权访问节点属性。 在创作和发布时使用相同的ACL。 有关 [详细信息，请参阅](/help/sites-administering/security.md) “用户管理和安全”。

## 配置AEM externalizer {#configuring-the-aem-externalizer}

在Adobe Target编辑活动时，URL将指向 **localhost** ，除非您更改AEM作者节点上的URL。

配置AEM externalizer:

1. 导航到位于https://&lt; **server>:&lt;port>/system/console/configMgr的OSGi Web控制台。**
1. 查 **找Day CQ Link Externalizer** ，然后输入创作节点的域。

   ![chlimage_1-120](assets/chlimage_1-120.png)

