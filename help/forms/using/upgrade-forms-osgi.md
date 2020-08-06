---
title: 升级到AEM 6.4Forms
seo-title: 升级到AEM 6.4Forms
description: '您可以从AEM 6.1Forms、AEM 6.2Forms和LiveCycleES4 SP1直接升级到6.3Forms。 '
seo-description: '您可以从AEM 6.1Forms、AEM 6.2Forms和LiveCycleES4 SP1直接升级到6.3Forms。 '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 3%

---


# 在OSGi上升级到AEM 6.4Forms {#upgrade-to-aem-forms-osgi}

根据您的环境，使用以下升级路径之一。

## AEM 6.2Forms或AEM 6.3Forms> AEM 6.4Forms {#upgrade-aem-forms-62-63-to-64}

您可以从AEM 6.2Forms或AEM 6.3Forms直接升级到AEM 6.4Forms。 执行以下操作：

1. 将现有AEM实例升级到AEM 6.4。以下步骤列出：

   1. 为AEM 6.2Forms或AEM 6.3Forms安装最新的Service Pack和修补程序。 有关详细信息，请参阅：

      * [AEM 6.2 发行说明](https://helpx.adobe.com/cn/experience-manager/6-2/release-notes.html)
      * [AEM 6.3 发行说明](https://helpx.adobe.com/cn/experience-manager/6-3/release-notes.html)
      * [AEM Susement Hub](https://helpx.adobe.com/cn/experience-manager/aem-releases-updates.html)
   1. 准备源实例以进行升级。 有关详细步骤，请 [参阅升级到AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance)。
   1. 下载 [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software)。
   1. **(仅限基于Unix/Linux的安装** )如果您使用UNIX或Linux作为基础操作系统，请打开终端窗口，导览至包含crx-quickstart的文件夹，然后运行以下命令：

      `chmod -R 755 ../crx-quickstart`

   1. 将AEM实例升级到AEM 6.3。有关分步说明，请参 [阅升级到AEM 6.4](/help/sites-deploying/upgrade.md)。

      在继续执行后续步骤之前，请等待ServiceEvent REGISTERED和ServiceEvent UNREGISTERED消息停止显示在&lt;crx-repository>/error.log文件中。

      >[!NOTE]
      >
      >服务器启动并运行后，一些AEM Forms捆绑包仍处于安装状态。 每个安装的捆绑包数量可能不同。 您可以安全地忽略这些包的状态。 这些包列在 `https://[server]:[port]/system/console/`。


1. 安装AEM Forms加载项包。 这些步骤如下所示：

   1. 开放 [软件分发](https://experience.adobe.com/downloads)。 您需要Adobe ID才能登录软件分发。
   1. 点按 **[!UICONTROL 标题]** 菜单中提供的Adobe Experience Manager。
   1. 在过滤器 **[!UICONTROL 部分]** :
      1. 从“ **[!UICONTROL 解决方]** 案 **[!UICONTROL ”下拉]** 列表中选择Forms。
      1. 选择包的版本和类型。 您还可以使用“搜 **[!UICONTROL 索下载]** ”选项筛选结果。
   1. 点按适用于您的操作系统的包名称，选择“ **[!UICONTROL 接受EULA条款]**”，然后点 **[!UICONTROL 按下载]**。
   1. 打开 [包管理器](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) ，然后单 **[!UICONTROL 击“上传包]** ”以上传包。
   1. Select the package and click **[!UICONTROL Install]**.

      您还可以使用AEM Forms版本文章中列出的直接链接 [下载包](https://helpx.adobe.com/cn/aem-forms/kb/aem-forms-releases.html) 。

      >[!NOTE]
      >
      >安装包后，系统会提示您重新启动AEM实例。 **不要立即停止服务器。** 在停止AEM Forms服务器之前，请等到ServiceEvent REGISTERED和ServiceEvent UNREGISTERED消息停止显示在&lt;crx-repository>/error.log文件中，并且日志是稳定的。 另请注意，一些包可以保持安装状态。 您可以安全地忽略这些包的状态。

   1. 停止AEM实例并删除以下文件：

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. 开始AEM实例。


1. 执行安装后活动。

   * **运行迁移实用程序**

      迁移实用程序使早期版本的自适应表单和对应管理资源与AEM 6.4表单兼容。 您可以从AEM软件分发下载该实用程序。 有关配置和使用迁移实用程序的分步信息，请参阅迁 [移实用程序](/help/forms/using/migration-utility.md)。

      如果您使用示 [例将草稿和提交组件与查询库集成](integrate-draft-submission-database.md) ，并从先前版本升级，则在执行升级后运行以下SQL:

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

   * **(如果仅从AEM 6.2Forms或先前版本升级)重新配置Adobe Sign**

      如果您在AEM Forms的先前版本中配置了Adobe Sign，请从AEM云服务中重新配置Adobe Sign。 有关详细信息，请参阅 [将Adobe Sign与AEM Forms集成](/help/forms/using/adobe-sign-integration-adaptive-forms.md)。

   * **(如果仅从AEM 6.2Forms或先前版本升级)重新配置分析和报告**

      在AEM 6.4Forms，不提供源流量变量和印象成功事件。 因此，从AEM 6.2Forms或先前版本升级后，AEM Forms将停止向Adobe Analytics服务器发送数据，并且不提供自适应表单的分析报告。 此外，AEM 6.4Forms还为表单分析版本引入了流量变量，并为字段所用的时间引入了成功事件。 因此，请重新配置AEM Forms环境的分析和报告。 有关详细步骤，请参 [阅配置分析和报告](/help/forms/using/configure-analytics-forms-documents.md)。

1. 验证服务器是否升级成功，所有数据是否也成功迁移，并且它可以正常运行。

   * **验证捆绑包的状态：** 确保所有捆绑包都处于活动状态。
   * **验证复制和反向复制：** 发布、填写和提交几个迁移的表单。 同时验证提交的数据。
   * **验证对管理员和开发人员用户界面的访问权限：** 从管理员帐户登录AEM实例并验证您是否有权访问以下URL:

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   在AEM 6.4Forms,crx-repository的结构已更改。 升级到AEM 6.4表单后，请使用您重新创建的更改路径进行自定义。 有关更改路径的完整列表，请参 [阅AEM 6.4中的Forms存储库重组](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)。

## AEM 6.0Forms和AEM 6.1Forms> AEM 6.4Forms {#upgrade-aem-forms-60-61-to-64}

不提供从AEM **6.0Forms****和AEM 6.1Forms到AEM** 6.4Forms的直接升级途径。 执行到AEM 6. [2Forms的中](/help/forms/using/upgrade.md) 间升级 [,](/help/forms/using/upgrade.md) 或升级到AEM 6.3Forms，然后从AEM 6.2Forms或AEM 6.3Forms升级到AEM6.4Forms。
