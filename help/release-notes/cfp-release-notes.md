---
title: AEM 6.4 Cumulative Fix Pack发行说明
description: 特定于Adobe Experience Manager6.4累积修复包的发行说明。
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2158'
ht-degree: 20%

---


# AEM 6.4 Cumulative Fix Pack发行说明 {#aem-cumulative-fix-pack-release-notes}

## 发行信息 {#release-information}

| 产品 | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| 版本 | 6.4.8.1 |
| 类型 | 累积修补程序包 |
| 日期 | 2020年6月4日 |
| 先决条件 | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| 下载 URL | AEM 6.4.8.1软件分 [发](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fcumulativefixpack%2Faem-6.4.8-cfp-1.0.zip) |

## AEM 6.4.8.1 包含哪些内容 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.1是自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式上市以来，包含若干内部和客户修复的重要更新。

AEM Cumulative Fix Pack 6.4.8.1取决于AEM 6.4 Service Pack 8。 因此，在安装AEM 6.4 Service Pack 8之后，必须安装AEM Cumulative Fix Pack 6.4.8.1包。

AEM 6.4.8.1的一些主要亮点是：

* 删除了与Adobe Experience Manager的包共享集成。
* 内置存储库 (Apache Jackrabbit Oak) 已更新至版本 1.8.21。

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

## 更改列表 {#list-of-changes}

Adobe Experience Manager6.4.8.1修复了以下问题。

### 站点 {#sites-6481}

* 当LiveCopy中的本地组件名称与蓝图中的组件名称相同，并且从蓝图中转出该组件时，术语_msm_moved不会添加到本地组件的名称(NPR-33207)。
* 附加到原始请求的参数不包括在重定向URL中(NPR-33174)。
* 当Coral.Select选项设置emptyOption=true或包含值为“”的默认项时，dropdownshowhide.js文件会遇到错误：未捕获的TypeError:component.getValue不是函数(NPR-33163)。
* 当组件包含另一个组件作为容器资源时，父组件占位符将替换为内部组件占位符(NPR-33119)。
* 当您将内容片段基于模式并且它包含强制文本区域或路径字段时，内容片段无法保存(NPR-33007)
* 当您使用现成的体验片段组件创建自定义组件并在AEM Sites页面中使用它时，AEM不显示自定义组件的引用（用法）(NPR-32852)。
* 当AEM Sites页面是包含多个Live Copy的大型内容集的一部分时，无法加载页面版本历史预览(NPR-32772)。
* 提升启动项时，会向启动项中添加的每个组件添加“cq:LiveRelation”混合。 它影响所有启动项，无论是否在创建启动项时选择——继承源页面实时数据——选项(NPR-32664)。
* 分页开始时，体验片段选取器不加载所有项目(NPR-32605)。
* 无法为AEM Sites页面创建启动项。 启动项创建会导致错误(NPR-32544)。
* 管理发布在激活工作流请求中不包括引用的资产(NPR-32463)。
* 调度程序运行状况 `Invalid cookie header` 检查在日志文件中显示警告消息(NPR-33630)。
* Salesforce集成易受SSRF(NPR-32671)的影响。
* PreferencesServlet中反射的XSS(NPR-33439)。

### 资产 {#assets-6481}

* 资产计数不会因列表视图中选择的更改而发生更改(NPR-33285)。

* 在选择父节点（其中显示单个子文件夹），然后选择子文件夹时，未启用“下一步”按钮(NPR-33284)。

* 在启用DMS7或混合模式时，触屏UI无法为无权在存储库根上访问读取的用户呈现（出现错误）(NPR-33175)。

* 文件夹和资源名称中出现的GB18030字符在下载的zip文件中更改为空白(NPR-33150)。

* 在智能裁剪父级文件夹内的资产时会创建额外的文件夹，其名称 `.` 中带有点字符(NPR-32755)。

* 延迟加载不会触发，选择从通知收件箱中查看任务时不会显示100个以下的资源(NPR-32749)。

* 由于coral-info中的更改(NPR-32510)，用于共享集合的链接页面被中断。

* 批量上传时的资产处理会卡住(CQ-4293916)。

* Experience Manager中的SSRF漏洞(NPR-33437)。

### 平台 {#platform-6481}

* 如果 [!DNL Sling] 在(NPR-33308) `sling:match` 下创建映射条目， `/etc/maps` 则不调用该过滤器。
* 取消激活页面时将触发所有刷新代理(NPR-32941)。
* 当您使用 `ScriptProcessor` API缩小JavaScript库时，日志文件显示一条错误消息，指示JavaScript代码不符合严格模式。 API不提供启用或禁用严格模式的选项。 (NPR-32746).
* 当SQL查询运行时间较长（例如7小时）时，AEM停止响应(NPR-33043)。

### 用户界面 {#ui-6481}

* 当您使用选择对话框搜索或浏览路径时，选择对话框显示所选JCR节点的所有内容，而不是只显示图像(NPR-32712)。

### 翻译项目 {#tranlation-6481}

* 运 `NullPointerException` 行转换作业的日志中显示错误(NPR-32220)。

### 集成 {#integrations-6481}

* JSON的跨站点脚本(NPR-32745)。

### 社区 {#communities-6481}

* 创建新组后，作者不会被重定向到 [!UICONTROL 第11号] “社区 [!DNL Internet Explorer] 组”部分(NPR-33202)。
* 访问活动流页 [!UICONTROL 面时出错] (NPR-33152)。
* 编辑 [!DNL Communities] 组和更改缩略图图像不会更新组缩略图图像(NPR-32603)。
* 在创建通知版本和用户生成内容订阅(UGC)时，会存储源页面的错误ID(CQ-4289703)。
* 跨站点脚本问题(NPR-33212)。

### 工作流 {#workflow-6481}

* 当用户完成包含“对话框参与者”步骤的工作流时，某些组件不会显示在弹出 [!UICONTROL 的对话框中] (NPR-32989)。

* 加 [!UICONTROL 载左边栏] 中的“时间轴”选项比预期花费的时间要多(NPR-32850)。

### 表单 {#forms-6481}

>[!NOTE]
>
>AEM累积修复包不包含针对AEM Forms的修复。 它们是通过单独的 Forms 附加组件包交付的。此外，还发布了包含针对AEM Forms的JEE修复的累积安装程序。 For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* 通信管理：当用户粘贴来自文档的 [!DNL Word] 内容时，文本文档片段不保留格式(NPR-33213)。
* 适应性Forms:自适应表单词典中字符串的新行将字 `&#xa;` 符添加到词典(NPR-33265)。
* 适应性Forms:用户无法保存具有多个附件的自适应表单(NPR-33214)。
* 适应性Forms: `AddInstance` 和 `RemoveInstance` 实例管理器类的方法不会为上的延迟加载片段添加动态 [!DNL Internet Explorer 11] 实例数(NPR-33201)。
* 适应性Forms:对嵌入到页面中的自适应表单启 [!DNL Sites] 用的分析不会记录提交和放弃事件的数据(NPR-31359)。
* 适应性Forms:当用户将文档中的内容粘贴 [!DNL Word] 到自适应表单并提交时，提交的自适应表单包含Unicode字符。 此外，PDF到PDF/A的转换由于Unicode字符而失败(NPR-33348)。
* 后端集成：表单数据模型请求失败，因为由于不正确的非活动状态，刷新令牌过期(NPR-33168)。
* 文档服务：由于服务器上缺少Gibson Jar，转换PDF服务 [!DNL WebLogic] 无法 [!DNL Linux] 将PDF文档转换为PostScript(NPR-33515、CQ-4292239)。
* 文档服务：当用户将文本文件转换为PDF时，日文字符无法正确呈现(NPR-33239)。
* 使用GuideSOMProviderServlet存储XSS(NPR-32701)。


## Install 6.4.8.1 {#install}

### 设置要求 {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>对于安装在AEM 6.4上的功能包的客户。Adobe提供的可选功能包与发行版和服务包有依赖关系。 如果您安装了任何功能包，请与AEM客户关怀团队联系，以验证这些功能包与AEM 6.4的此累积修复包的兼容性。

* AEM 6.4.8.1 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* 在具有 MongoDB 和多个实例的部署中，使用包管理器在其中一个 Author 实例上安装 AEM 6.4.8.1。
* 在安装累积修复包之前，请确保拥有AEM实例的快照或新鲜备份。
* 安装之前请重新启动该实例。尽管仅当实例仍处于更新模式时（这种情况下是从早期版本更新实例时）才需要此设置，但通常建议实例在较长的时间内运行。

>[!NOTE]
>
>Adobe 建议不要移除或卸载 AEM 6.4.8.1 包。

### 安装累积修复包 {#install-cumulative-fix-pack}

执行以下步骤以在现有 AEM 6.4.8.0 实例上安装累积修补程序包：

1. 单击“ [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-1.0.zip) （软件分发）”链接以下载包。

1. 打开 [包管理器](http://localhost:4502/crx/packmgr/index.jsp) ，然后单 **[!UICONTROL 击“上传包]** ”以上传包。

1. 选择包名称，然后单击“ **[!UICONTROL 安装]**”。

>[!NOTE]
>
>**包管理器 UI 中的对话框有时会在 AEM 6.4.8.1 的安装过程中退出**
>
>因此，建议在访问该实例之前先等待错误日志稳定下来。用户必须等待与卸载更新程序包相关的特定日志，才能确保安装成功。 这通常出现在 Safari 中，但也可能会间歇性发生在任何浏览器中。

### 自动安装 {#auto-installation}

可通过两种方法将 AEM 6.4.8.1 自动安装到正在运行的实例上：

答：将包放入……*/crx-quickstart/install* 文件夹中。包会自动进行安装。

B. Use the [HTTP API from Package Manager](https://helpx.adobe.com/cn/experience-manager/aem-previous-versions.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.1 不支持 Bootstrap 安装。

### 验证安装 {#validate-install}

1. “产品信息”页&#x200B;*面(/system/console*/productinfo)现在应在“已安装产品”下显示更新的版本字符串“Adobe Experience Manager，版本6.4.8.1”。
1. 所有 OSGi 包在 OSGi 控制台中均为“活动”或“片段”（使用 Web 控制台：/system/console/bundles）。
1. OSGI捆绑包org.apache.jackrabbit.oak-core在版本1.8.17或更高版本上(使用Web控制台：/system/console/bundles)。

要确定与此版本的AEM Sites和资产一起运行的认证平台，请参 [阅技术要求](../sites-deploying/technical-requirements.md)。

>[!NOTE]
>On successful installation of the package, an informational message appears indicating that the content package has installed successfully, such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### 更新Dynamic Media查看器(5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.1包含新版Dynamic Media查看器(5.10.1)，该查看器支持在“图像预设”页面上检查重复名称。 建议Dynamic Media客户运行以下命令，将包装盒查看器预设调出为最新状态。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

将新查看器预设复制到/conf位置。

### 安装 AEM Forms 附加组件包 {#install-aem-forms-add-on-package}

>[!NOTE]
>
>如果您未使用 AEM Forms，请跳过。AEM Forms 中的修复通过单独的附加包来交付。

1. 确保已安装AEM Cumulative Fix Pack。
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/cn/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Install AEM Forms JEE installer {#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果您未在 JEE 上使用 AEM Forms，请跳过。AEM Forms JEE 中的修复通过单独的安装程序来交付。

For information about installing the cumulative installer for AEM Forms JEE and post-deployment configuration, see [AEM Forms JEE Patch Installer 0016](https://helpx.adobe.com/cn/aem-forms/quick-fixes/6-4/jee-patch-0016.html).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.1 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8.1/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.1</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## 已移除/已弃用功能 {#removed-deprecated-features}

此部分列出了 AEM 6.4 中已移除或已弃用的功能和特性。

| 区域 | 功能 | 替换 | 版本 |
|---|---|---|---|
| 资产 | 管理子资产的标记操作 | 无替换项 | AEM 6.4.2.0 |
| 资产和 Creative Cloud 集成 | [AEM到Creative Cloud文件夹共享](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) ，在AEM 6.2中引入了，作为一种让创意用户能够访问AEM中的资产的方式。 在 Creative Cloud 应用程序中发布的新功能“Adobe 资产链接”提供了更佳的用户体验，能够直接从 Photoshop、InDesign 和 Illustrator 中轻松访问 AEM 资产。Adobe 不会再进一步增强文件夹共享功能。尽管AEM中包含该功能，但会强烈建议客户使用该替换。 | Adobe资产链接或桌面应用程序。 有关更多信息，请参阅 [AEM Creative Cloud 集成](/help/assets/aem-cc-integration-best-practices.md)一文。 | AEM 6.4.4.0 |

## 已知问题 {#known-issues}

* 安装AEM 6.4.8.1时，更新版 [!DNL Chrome] 本83会导致构建包时出现问题。 使用其他可用的浏览器(如 [!DNL Internet Explorer] 和 [!DNL Firefox]或其他AEM标准包安装选项)来解决问题。 安装AEM 6.4.8.1后，问题就得到解决。

* 无法使用AEM默认邮件发送器向远程SMTP服务器发送电子邮件，因为它仅允许使用TLS v1.2进行通信。请从中删除捆绑包 `javax.mail:mail:1.5.0-b01` , `system/console` 并刷新捆绑包以解决此问题。

有关AEM 6.4.8.0 Service Pack已知问题的信息，请参 [阅《AEM 6.4.8.0 Service Pack发行说明》](sp-release-notes.md)。

## 包含的 OSGi 包和内容包 {#osgi-bundles-and-content-packages-included}

以下文本文档列出了 AEM 6.4.8.1 中包含的 OSGi 包和内容包.

AEM 6.4.8.1 中包含的 OSGi 包列表

[获取文件](assets/6.4.8.1_osgi_bundles.txt)

AEM 6.4.8.1 中包含的内容包列表

[获取文件](assets/6.4.8.1_content_packages.txt)

## 有用资源 {#helpful-resources}

* [AEM 6.4 发行说明](../release-notes/release-notes.md)
* [AEM 产品页面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 文档](https://helpx.adobe.com/cn/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## 受限的网站 {#restricted-sites-new}

这些网站仅适用于客户。如果您是客户并且需要访问，请联系您的 Adobe 客户经理。

* [产品下载：licensing.adobe.com](https://licensing.adobe.com/)
* [联系客户支持](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
