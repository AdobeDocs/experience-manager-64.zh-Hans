---
title: 升级到 AEM 6.4 Forms
seo-title: Upgrade to AEM 6.4 Forms
description: 您可以从AEM 6.1 Forms、AEM 6.2 Forms和LiveCycleES4 SP1直接升级到AEM 6.3 Forms。
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 9%

---

# 在OSGi上升级到AEM 6.4 Forms {#upgrade-to-aem-forms-osgi}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

根据您的环境，使用以下升级路径之一。

## AEM 6.2 Forms或AEM 6.3 Forms > AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

您可以从AEM 6.2 Forms或AEM 6.3 Forms直接升级到AEM 6.4 Forms。 执行以下操作：

1. 将现有AEM实例升级到AEM 6.4。下面列出了步骤：

   1. 安装AEM 6.2 Forms或AEM 6.3 Forms的最新Service Pack和修补程序。 有关详细信息，请参阅：

      * [AEM 6.2 发行说明](https://helpx.adobe.com/cn/experience-manager/6-2/release-notes.html)
      * [AEM 6.3 发行说明](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html)
      * [AEM维护中心](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)
   1. 为升级准备源实例。 有关详细步骤，请参阅 [升级到AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. 下载 [AEM 6.4快速入门](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **（仅基于Unix/Linux的安装）** 如果您使用UNIX或Linux作为基础操作系统，请打开“终端”窗口，导航到包含crx-quickstart的文件夹，然后运行以下命令：

      `chmod -R 755 ../crx-quickstart`

   1. 将您的AEM实例升级到AEM 6.3。有关分步说明，请参阅 [升级到AEM 6.4](/help/sites-deploying/upgrade.md).

      在继续执行后续步骤之前，请等待ServiceEvent REGISTERED和ServiceEvent UNEXIVERTED消息停止出现在 &lt;crx-repository>/error.log文件。

      >[!NOTE]
      >
      >服务器启动并运行后，一些AEM Forms包仍处于安装状态。 每次安装的包数可能有所不同。 您可以安全地忽略这些包的状态。 这些包列在 `https://[server]:[port]/system/console/`.


1. 安装AEM Forms附加组件包。 下面列出了这些步骤：

   1. 打开 [Software Distribution](https://experience.adobe.com/downloads)。您需要 Adobe ID 才能登录 Software Distribution。
   1. 点按标题菜单中的 **[!UICONTROL Adobe Experience Manager]**。
   1. 在 **[!UICONTROL 过滤器]** 部分：
      1. 选择 **[!UICONTROL Forms]** 从 **[!UICONTROL 解决方案]** 下拉列表。
      1. 选择包的版本和类型。 您还可以使用 **[!UICONTROL 搜索下载]** 选项来筛选结果。
   1. 点按适用于您的操作系统的包名称，选择 **[!UICONTROL 接受EULA条款]**，然后点按 **[!UICONTROL 下载]**.
   1. 打开[包管理器](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)，并单击&#x200B;**[!UICONTROL 上传包]**&#x200B;以上传包。
   1. 选择包并单击 **[!UICONTROL 安装]**.

      您还可以使用 [AEM Forms版本](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) 文章。

      >[!NOTE]
      >
      >安装包后，系统会提示您重新启动AEM实例。 **不要立即停止服务器。** 在停止AEM Forms服务器之前，请等待ServiceEvent REGISTERED和ServiceEvent UNREGISTERED消息停止显示在 &lt;crx-repository>/error.log文件和日志稳定。 另请注意，一些包可以保持已安装状态。 您可以安全地忽略这些包的状态。

   1. 停止AEM实例并删除以下文件：

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. 启动 AEM 实例。


1. 执行安装后活动。

   * **运行迁移实用程序**

      迁移实用程序使早期版本的自适应表单和通信管理资产与AEM 6.4表单兼容。 您可以从AEM Software Distribution下载该实用程序。 有关配置和使用迁移实用程序的分步信息，请参阅 [迁移实用程序](/help/forms/using/migration-utility.md).

      如果您使用 [集成草稿和提交组件的示例](integrate-draft-submission-database.md) 使用数据库并从以前的版本升级，然后在执行升级后运行以下SQL查询：

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(如果仅从AEM 6.2 Forms或以前的版本升级)重新配置Acrobat Sign**

      如果您在以前的AEM Forms版本中配置了Acrobat Sign，请从AEM云服务中重新配置Acrobat Sign。 有关更多详细信息，请参阅 [将Acrobat Sign与AEM Forms集成](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(如果仅从AEM 6.2 Forms或以前的版本升级)重新配置分析和报表**

      在AEM 6.4 Forms中，不提供用于展示的源流量变量和成功事件流量变量。 因此，当您从AEM 6.2 Forms或更早版本升级时，AEM Forms将停止向Adobe Analytics服务器发送数据，并且自适应表单的Analytics报表不可用。 此外，AEM 6.4 Forms还为表单分析版本引入了流量变量，并为字段逗留时间的成功事件引入了流量变量。 因此，请为您的AEM Forms环境重新配置分析和报表。 有关详细步骤，请参阅 [配置分析和报表](/help/forms/using/configure-analytics-forms-documents.md).

1. 验证服务器是否成功升级，所有数据是否也已成功迁移，并且可以正常运行。

   * **验证包的状态：** 确保所有包都处于活动状态。
   * **验证复制和反向复制：** 发布、填写和提交一些迁移的表单。 同时验证提交的数据。
   * **验证对管理员和开发人员用户界面的访问权限：** 从管理员帐户登录AEM实例，并验证您是否有权访问以下URL:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   在AEM 6.4 Forms中，crx-repository的结构已发生更改。 升级到AEM 6.4表单后，请使用更改的路径进行重新创建的自定义。 有关更改路径的完整列表，请参阅 [Forms 6.4中的存储库重组](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms和AEM 6.1 Forms > AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

直接从升级路径 **AEM 6.0 Forms** 和 **AEM 6.1 Forms** 到AEM 6.4 Forms不可用。 执行中间 [升级到AEM 6.2 Forms](/help/forms/using/upgrade.md) 或 [升级到AEM 6.3 Forms](/help/forms/using/upgrade.md) 然后，从AEM 6.2 Forms或AEM 6.3 Forms升级到AEM 6.4 Forms。
