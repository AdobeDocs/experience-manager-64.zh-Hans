---
title: 配置AEM DS设置
seo-title: Configuring AEM DS settings
description: 在提交表单之前，您需要指定处理服务器URL。
seo-description: You need to specify the processing server URL before you submit a form.
uuid: 2b415c99-275b-4b67-bb8e-35329514ecbb
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: fbb9044a-a737-45f6-8062-0ef5424a92f8
role: Admin
exl-id: f60beaae-4082-4165-8a37-9d9c94e360b2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 1%

---

# 配置AEM DS设置 {#configuring-aem-ds-settings}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本文介绍了如何配置 **AEM DS设置服务**. 此设置可用于多种情况，例如：

* 在通信管理中

   * 用于配置AEM Forms工作流
   * 使用Forms门户远程保存草稿/提交时

* 在自适应表单中，当从发布实例提交自适应表单时

以下是配置 **[!UICONTROL AEM DS设置]**:

1. 使用URL在发布实例上打开配置管理器：

   *http://localhost:port/system/console/configMgr*.

   ![aem_web_configuration_console](assets/aem_web_configuration_console.png)

1. 在 **[!UICONTROL Adobe Experience Manager Web控制台配置]** 窗口，找到并单击 **[!UICONTROL AEM DS设置]** 选项。

   ![ds_settings](assets/ds_settings.png)

1. 的 **[!UICONTROL AEM DS设置服务]** 窗口显示AEM DS组件的常用配置设置。

   ![ds_settings_1](assets/ds_settings_1.png)

1. 在相应的字段中添加以下信息：

   **[!UICONTROL 处理服务器URL]**:处理服务器是需要触发Forms或AEM工作流的服务器。 这可以与AEM创作实例的URL或其他服务器URL(即http:// localhost:port/)相同。

   **[!UICONTROL 处理服务器用户名]**:工作流用户的用户名 [基于所使用的服务器URL]

   **[!UICONTROL 处理服务器密码]**:工作流用户的密码

   >[!NOTE]
   >
   >* 使用Forms或AEM工作流时，在从发布服务器提交任何内容之前，必须配置DS设置服务。 否则，《表》报送失败。

