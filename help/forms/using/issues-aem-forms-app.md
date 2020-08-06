---
title: 对AEM Forms应用程序进行疑难解答
seo-title: 对AEM Forms应用程序进行疑难解答
description: '了解AEM Forms应用程序的常见问题以及如何解决这些问题。 '
seo-description: '了解AEM Forms应用程序的常见问题以及如何解决这些问题。 '
uuid: a5cc3065-0ebf-48c0-a8fe-f1061632ca90
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-app
discoiquuid: 2f45a965-590b-43b1-95c6-df4b74ad15b9
translation-type: tm+mt
source-git-commit: de440f57091d814a0a7ff48e9a0383c5415a0a5b
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 1%

---


# 对AEM Forms应用程序进行疑难解答 {#troubleshoot-aem-forms-app}

本文介绍构建AEM Forms应用程序时可能显示的错误消息以及解决这些错误的步骤。

本文的章节包括：

* [iOS用户的附件丢失](/help/forms/using/issues-aem-forms-app.md#attachment-loss-for-ios-users)
* [工作区用户提交的HTML5表单草稿在门户上不可见](/help/forms/using/issues-aem-forms-app.md#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal)
* [HTML5表单（未缓存）无法在AEM Forms应用程序中加载](/help/forms/using/issues-aem-forms-app.md#html-forms-not-cached-fail-to-load-in-aem-forms-app)
* [AEM Forms在Windows上不同步](/help/forms/using/issues-aem-forms-app.md#aem-forms-do-not-sync-on-windows)
* [不支持的Gradle版本](/help/forms/using/issues-aem-forms-app.md#unsupported-version-of-gradle)
* [Gradle和Android Gradle插件兼容性问题](/help/forms/using/issues-aem-forms-app.md#gradle-and-android-gradle-plug-in-compatibility-issues)

## iOS用户的附件丢失 {#attachment-loss-for-ios-users}

AEM Forms的iOS应用程序配置为在OSGi上与AEM Forms同步，仅支持字段级附件。 所有附件必须具有唯一的名称。 如果多个附件的名称相同，则仅保留一个附件，而所有其他名称相同的附件将丢失。 请执行以下步骤以防止iOS设备上的用户发生数据丢失：

1. 在连接的服务器上，导航到 **Adobe Experience Manager>工具>操作> Web Console**。
1. 查找并单 **击自适应表单配置服务**。
1. 在自适应表单配置服务对话框中，启 **用使文件名唯一**。

   如果 **禁用“使文件名唯一** ”设置，则用户尝试提交具有多个附件的自适应表单时会丢失数据。

1. 单击&#x200B;**保存**。

## 工作区用户提交的HTML5表单草稿在门户上不可见 {#html-form-drafts-submitted-by-workspace-users-are-not-visible-on-the-portal}

对于在AEM Forms应用程序中启用的HTML5表 **单(“另存为草稿** ”HTML渲染用户档案)，工作区用户看不到保存的草稿。 要视图门户上由工作区用户提交的HTML5表单的已保存草稿，请执行以下步骤：

1. 打开CRXDE并使用管理员凭据登录。

   URL: `https://<server>:<port>/lc/crx/de/index.jsp`

1. 在CRXDE的根路径中，在访问控制列表下的访问控制下，单击 **+**。
1. 在“添 **加新条目** ”对话框中，单击“主体”字段中的组搜索按钮。
1. 在“选择主体”对话框的“名称”字段中，键入并 `PERM_WORKSPACE_USER` 单击“ **搜索”**。
1. 在“ `PERM_WORKSPACE_USER` 选择主体”对话框中选择组，然后单 **击确定**。
1. 在“添加新条目”对话框 `PERM_WORKSPACE_USER` 的“承担者”字段中选择组。

   为用 `jcr:read` 户组启用权限。

1. 单击&#x200B;**确定**。

## HTML5表单（未缓存）无法在AEM Forms应用程序中加载 {#html-forms-not-cached-fail-to-load-in-aem-forms-app}

当AEM Forms应用程序连接到旧版AEM Forms服务器时，未缓存的HTML5表单无法在AEM Forms应用程序中加载。

请执行以下步骤以解决问题：

1. 在创作实例中，导航到 **Adobe Experience Manager>工具>配置Workspace App Offline Service >立即配置**。
1. 在“工 **作区应用程序脱机服务** ”页中，单 **击“手动资源缓存”**。

   URL: https://&lt;server>:&lt;port>/libs/fd/workspace-offline/content/config.html

1. 在“手 **动资源缓存** ”选项卡中， **单击+按** 钮以添加CRX路径。
1. 在添加 **新资源字段中** ，键入： /etc.clientlibs/fd/xfaforms/I18N/en_US.js，然后单击“ **添加**”。
1. 单击&#x200B;**保存**。

## AEM Forms在Windows上不同步 {#aem-forms-do-not-sync-on-windows}

在Windows上的AEM Forms应用程序中，如果表单的路径或其任何资源包含大于或等于256个字符，则表单将不与连接的服务器同步。

修改表单的路径及其资源，将字符数减少到少于256个字符。

## 不支持的Gradle版本 {#unsupported-version-of-gradle}

**错误消息：** 项目使用的Gradle版本不受支持。

在Android Studio中构建AEM Forms应用程序时，将显示错误消息。 由于系统上支持的Gradle版本不受支持，因此出现问题。

**解决方案：** 单 **击“修复Gradle包装器”并重新导入项目** ，以解决此问题。

![gradle_unsupported_version](assets/gradle_unsupported_version.png)

## Gradle和Android Gradle插件兼容性问题 {#gradle-and-android-gradle-plug-in-compatibility-issues}

**错误消息：** Android Gradle插件和Gradle的版本不兼容。

从Android Studio用户界面的“ **构建** ”菜单中选择 **“构建APK** ”选项时，将显示错误消息。

![gradle_plugin_compatibility](assets/gradle_plugin_compatibility.png)

**解决方案：** 打 **开Gradle** Scripts > **gradle-wrapper.properties文件** ，并编辑 **distributionUrl属性** 。

例如，Android Studio控制台建议将Gradle版本降级为3.5。在gradle-wrapper.properties文 **件的** distributionUrl中编&#x200B;**辑该** 版本。

再次 **选择** “构 **建”>“构建APK** ”以解决错误并生成。apk文件。

![gradle_wrapper_properties](assets/gradle_wrapper_properties.png)

