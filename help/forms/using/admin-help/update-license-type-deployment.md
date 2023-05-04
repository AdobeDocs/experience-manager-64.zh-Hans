---
title: 更新部署的许可证类型
seo-title: Update the license type for the deployment
description: 使用管理控制台中的“更改许可证”页面更新部署的许可证类型。
seo-description: Update the license type for the deployment by using the Change License page in administration console.
uuid: 0152635e-2c00-4944-b9b6-64b368589a91
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e4f31377-ccc9-4986-a3bf-ef2e83d12448
exl-id: 07671470-59dd-4290-be9a-465fcd89ac2d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 1%

---

# 更新部署的许可证类型 {#update-the-license-type-for-the-deployment}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在AEM表单安装过程中，您使用配置管理器配置和部署所需的AEM表单模块。 默认情况下，这些模块配置了60天的评估许可证。 使用管理控制台中的“更改许可证”页面可更改部署的许可证类型。 当前部署的模块显示在“更改许可证”页面上。

“更改许可证”页面显示有关您的许可证的信息：

* 当前许可证类型
* 上次更新许可证的日期和时间
* 执行上次更新的人员
* 许可证的当前状态
* 安装AEM Forms的日期
* 当前许可证的过期日期

>[!NOTE]
>
>许可证更改适用于所有已部署的模块。 在更改许可证类型之前，请取消部署任何未获得许可的模块。 如果已部署模块列表包含的模块不是您从Adobe购买的模块，请勿选择生产许可证类型。

## 更新许可证类型 {#update-the-license-type}

1. 在管理控制台中，单击许可。
1. 阅读AEM表单最终用户许可协议，选择“I Accept i forms（我接受）”（如果您同意协议条款），然后单击“Next（下一步）”。
1. 在“更改许可证”页面上，选择许可证类型：

   * **EVAL:** 60天评估许可证
   * **开发：** 永久开发许可证
   * **NFR:** 2年评估许可
   * **视频：** 1年订购Adobe Developer计划
   * **生产：** 永久许可证

1. 选择“是”，许可证更改对所有已部署模块都有效。
1. 单击确认许可证更改。 出现一条消息，表明许可证已成功更新。
