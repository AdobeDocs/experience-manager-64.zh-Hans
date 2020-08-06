---
title: 配置AEM DS设置
seo-title: 配置AEM DS设置
description: 在提交表单之前，您需要指定处理服务器URL。
seo-description: 在提交表单之前，您需要指定处理服务器URL。
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# 配置AEM DS设置 {#configuring-aem-ds-settings}

本文介绍如何配 **置AEM DS Settings Service**。 此设置可用于多种情况，例如：

* 在通信管理中

   * 配置AEM Forms工作流
   * 使用表单门户远程保存草稿／提交时

* 在自适应表单中，当从发布实例提交自适应表单时

以下是配置AEM DS设 **[!UICONTROL 置的步骤]**:

1. 使用URL在发布实例上打开配置管理器：

   *http://localhost:port/system/console/configMgr*。

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. 在“ **[!UICONTROL Adobe Experience ManagerWeb控制台配置]** ”窗口中，找到并 **[!UICONTROL 单击AEM DS设置]** 。

   ![ds_settings](assets/ds_settings.png)

1. AEM **[!UICONTROL DS设置服务]** ( DS Settings Service)窗口显示AEM DS组件的常用配置设置。

   ![ds_settings_1](assets/ds_settings_1.png)

1. 在相应的字段中添加以下信息：

   **[!UICONTROL 正在处理服务器URL]**: 处理服务器是需要触发Forms或AEM工作流的服务器。 这可以与AEM作者实例的URL或其他服务器URL(即http:// localhost:port/)相同。

   **[!UICONTROL 处理服务器用户名]**: 工作流用户的用 [户名（基于正在使用的服务器URL）]

   **[!UICONTROL 正在处理服务器密码]**: 工作流用户密码

   >[!NOTE]
   >
   >* 在使用Forms或AEM工作流时，在从发布服务器提交任何内容之前，必须配置DS设置服务。 否则，表格提交将失败。

