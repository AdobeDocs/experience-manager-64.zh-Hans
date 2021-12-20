---
title: AEM 6.4 累积修补程序包发行说明
description: 特定于Adobe Experience Manager 6.4累积修补程序包的发行说明。
contentOwner: AK
mini-toc-levels: 1
exl-id: a63e77a3-da48-4072-bc75-c4c41a2f62a3
source-git-commit: 1d5d2ef3840a40df7c3b223c7b5835e41553e9f1
workflow-type: tm+mt
source-wordcount: '4693'
ht-degree: 15%

---

# AEM 6.4 累积修补程序包发行说明 {#aem-cumulative-fix-pack-release-notes}

## 版本信息 {#release-information}

<!-- TBD: Update the SD URL. -->

| 产品 | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| 版本 | 6.4.8.4 |
| 类型 | 累积修补程序包 |
| 日期 | 2021 年 2 月 25 日 |
| 先决条件 | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| 下载 URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) |

## AEM 6.4.8.4 包含哪些内容 {#what-s-included-in-aem}

AEM累积修补程序包6.4.8.4是一个重要更新，它包括自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式发布以来的若干内部修补程序和客户修补程序。

AEM 6.4.8.4是依赖于AEM 6.4 Service Pack 8的累积修补程序包(CFP)。 安装AEM 6.4 Service Pack 8后，再安装CFP。

中引入的主要功能和增强功能 [!DNL Adobe Experience Manager] 6.4.8.4为：

* 能够启用或禁用 [!DNL Experience Manager Forms] 执行PDFG转换时，注册表发生更改。

* 针对表单数据模型中基于SOAP的Web服务，使用基于X-509证书的身份验证。

* 内置存储库 (Apache Jackrabbit Oak) 已更新至版本 1.8.24。

有关CFP和其他发行版类型的信息，请参阅 [AEM更新版本发行方式定义](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.4提供了以下问题的修复。

### 站点 {#sites-6484}

* 安装Experience ManagerService Pack 6.4.8.2后，用户无法编辑内容片段模型，并会体验到以下错误：

   `Uncaught TypeError: Cannot read property 'debounce' of undefined` (NPR-35312)
* 当用户单击注销按钮时，用户不会从包管理器中注销。 (NPR-35161)
* 从Experience Manager6.4.x升级到Experience Manager6.4.8.3后，用户无法通过“管理发布”发布页面。 (CQ-4312511)
* 将Blueprint子页面移回原始位置时，不会从Live Copy子页面中删除cq:liveSyncConfig配置。 (NPR-35900)
* 当您前后移动具有Live Copy的Blueprint时，只有第一次移动可正常工作，然后该移动会失败，并且不显示错误消息。 (NPR-35899)


### [!DNL Assets] {#assets-6484}

* `IndexWriter.merge` 原因 `OutOfMemoryError` 智能标记功能会创建大量错误 `/oak:index/lucene` 和 `/oak:index/ntBaseLucene` 索引(NPR-35650)。
* 用户在中编辑资产后无法签入资产 [!DNL Adobe InDesign] 和收到有关缺少权限的错误(NPR-35340)。
* 解决命名冲突后创建现有资产的新版本时，会覆盖原始资产的元数据(NPR-35939)。
* 删除文件夹或使用更新文件夹时，不会维护和删除自动生成的专用文件夹组 [!UICONTROL 删除专用文件夹限制] 选项集(NPR-35625)。

#### [!DNL Dynamic Media] {#dynamic-media}

* 间歇性ImageServer错误导致403响应，并导致 [!DNL Experience Manager]. (CQ-4308565)

### 集成 {#integrations-6484}

* 升级到Experience Manager6.4.8.3后打开页面属性时，控制台中会开始显示JavaScript错误(NPR-35649)。

### 表单 {#forms-6484}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 在计划的 [!DNL Experience Manager] 累积修补程序包发行日期后一周发布附加组件包。

**通信管理**

* 编辑信件时，包含条件的模块需要较长时间才能加载(NPR-35326)。

* 编辑信件时，内容和数据绑定不显示在用户界面(CQ-4312905)上。

**文档服务**

* 升级后无法组合PDF [!DNL JAVA] to [!DNL JDK1.8.0_261] (NPR-35761、NPR-35848)。

**Foundation JEE**

* 在 [!DNL Forms] 工作流中，您无法保存它(CQ-4315055)。

**AEMForms-6.4.0-0027中已修复的问题**

* （仅限JEE）针对Apache Log4j2报告的关键安全漏洞(CVE-2021-44228和CVE-2021-45046)。

有关安全更新的信息，请参阅 [Experience Manager安全公告页](https://helpx.adobe.com/security/products/experience-manager.html).

## 以前的累积修补程序包中包含的修补程序和功能包 {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.3 {#experience-manager-6483}

AEM累积修补程序包6.4.8.3是一个重要更新，它包括自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式发布以来的若干内部修补程序和客户修补程序。

AEM 6.4.8.3是依赖于AEM 6.4 Service Pack 8的累积修补程序包(CFP)。 安装AEM 6.4 Service Pack 8后，再安装CFP。

在AEM 6.4.8.3中，内置存储库(Apache Jackrabbit Oak)已更新至版本1.8.23。

有关CFP和其他发行版类型的信息，请参阅 [AEM更新版本发行方式定义](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.3提供了以下问题的修复。

#### 站点 {#sites-6483}

* 更新内容片段变体的文本时，将更新主控内容片段的内容，而不是变体的内容(NPR-35080)。

* 当您为组件的字符串类型标签属性设置数字值，删除该组件，然后使用撤消选项将其重新打开时，标签属性的类型会自动从字符串更改为长(NPR-34738)。

* 将文件上传组件添加到多字段时，图像路径会存储在组件节点中，而不是多字段节点中(NPR-34423)。

* 在“移动页面”向导中，即使未选择任何目标，下一个按钮仍会保持启用状态(NPR-34460)。

* 当父组件包含 `cq:isContainer` 属性中，继承的组件不会自动包含该属性(CQ-4308409)。

* 当您使用 `calc()` 函数中的空白 `+` 删除了符号(NPR-34991)。

* 启动AEM实例时， `com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl` 和 `com.adobe.granite.maintenance.impl.TaskScheduler` 组件不显示在 `Active` 状态(NPR-34952)。

#### [!DNL Assets] {#assets-6483}

* 创建现有资产的版本时，如果将元数据配置文件应用到文件夹，则用户对元数据的更新不会持久保留(NPR-34833)。
* 使用 [!DNL Adobe Asset Link] with [!DNL Adobe InDesign]，则搜索结果中不包含文件夹和收藏集，但只包含资产(NPR-34700)。
* 在文件夹上拖动资产以移动资产时，用户界面还会显示 [!UICONTROL 放入灯箱] 和 [!UICONTROL 放入收藏集]. 即使取消移动操作，用户界面仍会继续显示后两个选项(NPR-34525)。
* 打开“管理发布”界面时，发布选项不可用，选择取消发布选项后，范围页面将为空(CQ-4302509)。

##### [!DNL Dynamic Media] {#dynamic-media-6483}

* 在“图像预设”设置中，当 [!UICONTROL 启用JPG色度缩减采样] 在 [!DNL Experience Manager]，则所做的更改不会与同步 [!DNL Dynamic Media] (NPR-34284)。
* 在 [!UICONTROL 查看器预设编辑器]，编辑时 [!UICONTROL 全景图像/全景图像_VR] 预设，在 `PanoramicView` 组件， `PANORAMICVIEW_AUTOROTATE` 修饰符标签不可用(CQ-4302043)。
* 取消发布来自 [!DNL Experience Manager] 不会取消发布已配置的自适应视频集Dynamic Media Classic。 (CQ-4304405).

#### 平台 {#platform-6483}

* 的 `emitUseStrict` 标记已添加到Google关闭编译器(GCC)处理器函数中 `com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`. 标记禁止输出 `use strict` 说明(NPR-34830)。
* A `NullPointerException` 在启动每日或每周维护任务时返回(NPR-34702)。
* 的 [!DNL Apache Sling Health Check] 工具已弃用。 请改为使用 [图案检测器](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html) 以检测内容违规(NPR-33929)。

#### 集成 {#integrations-6483}

* 的 [!UICONTROL 创建] 按钮 [!UICONTROL 受众] 页面 [!UICONTROL 受众] 页面(NPR-35152)。

#### 用户界面 {#ui-6483}

* 的 [!UICONTROL 过滤器] 搜索面板 [!UICONTROL Omnisearch] 用户界面还会从运行搜索的位置以外的位置返回结果(NPR-34877)。
* 关闭 [!UICONTROL 过滤器] 面板 [!UICONTROL Omnisearch] 用户界面中，左边栏不会重置为 [!UICONTROL 内容] 选择，用于阻止重新打开 [!UICONTROL 过滤器] 面板(NPR-34483)。
* A `NullPointerException` 在访问页面属性时返回(NPR-34509)。

#### 社区 {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* 产品中所有不公平术语的实例都被接受的对等术语替换(NPR-34506)。

#### 商务 {#commerce-6483}

* 当收藏集中的产品超过15个时，该收藏集仅显示前15个产品(NPR-34494)。

#### 表单 {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 在计划的 [!DNL Experience Manager] 累积修补程序包发行日期后一周发布附加组件包。

>[!NOTE]
>
>[!DNL Experience Manager] 累积修补程序包不包含 [!DNL Experience Manager Forms]. 它们使用单独的 [!DNL Forms] 附加组件包。 此外，还发布了累积安装程序，其中包含针对 [!DNL Experience Manager Forms] 在JEE上。 有关更多信息，请参阅 [安装AEM Forms附加组件包](#install-aem-forms-add-on-package) 和 [安装AEM Forms JEE安装程序](#install-aem-forms-jee-installer).

**自适应表单**

* 应用 [!DNL Experience Manager] 累积修补程序包(NPR-35127)。

* 由于缓存失效，以自适应形式加载片段需要较长时间(NPR-34655)。

* 辅助功能：自适应表单中的屏幕阅读器无法正常使用选项卡导航(NPR-34550)。

**通信管理**

* 从ES3迁移资产时，这些资产包含两个不可编辑的默认条件(NPR-34971)。

**Foundation JEE**

* 迁移 [!DNL AEM Forms] 从Flash到HTML的用户(CQ-4304075)。

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM累积修补程序包6.4.8.2是一个重要更新，它包括自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式发布以来的若干内部修补程序和客户修补程序。

AEM 6.4.8.2是依赖于AEM 6.4 Service Pack 8的累积修补程序包(CFP)。 安装AEM 6.4 Service Pack 8后，再安装CFP。

在AEM 6.4.8.2中，内置存储库(Apache Jackrabbit Oak)已更新至版本1.8.22。

有关CFP和其他发行版类型的信息，请参阅 [AEM更新版本发行方式定义](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.2提供了以下问题的修复。

#### 站点 {#sites-6482}

* 如果 `RolloutConfigManagerFactoryImpl` 无法加载转出配置，它不会尝试加载缺少的配置。 它会返回缓存的配置(NPR-34091)。
* 在文本核心组件中，使用源HTML编辑选项后， `em` 标记已删除(NPR-34080)。
* 从Experience Manager6.2升级到Experience Manager6.5时，静态模板的Parsys组件无法正确显示。 Parsys组件的高度设置为0，且其中的组件不可见(NPR-34044)。
* 在模板编辑器中，不会显示允许的组件的标签信息(NPR-33908)。

   ![布局容器中缺少标签](assets/33908_missing_labels.png)

* 在第四级嵌套组件之后，用户无法向Parsys添加或编辑组件(NPR-33873)。
* 如果更改了可编辑模板的初始内容，然后发布了模板，则使用此模板创建的任何新页面都会显示模板的发布日期，即使页面未发布也是如此(NPR-33822)。
* 的 `cq:acLinks` 和 `cq:acUUID` 属性 [!DNL Adobe Campaign] 在复制并粘贴操作期间，会删除复制上的(NPR-33793)。
* 在 [!UICONTROL 实时使用情况] 选项卡，则只显示49个结果。 它不显示组件的所有用法(NPR-33710)。
* 网页 `/` 创作时，URL中的字符会变得无响应。 在创作时添加组件时，CPU使用率会增加，浏览器停止响应(NPR-33625)。
* 在内联编辑模式下， [!DNL RTE]，则对于文本组件无法拖动图像(NPR-33579)。
* 可以在Blueprint页面中使用与页面名称相同的名称创建组件。 在转出过程中，此类组件会通过在 `_msm_moved`. 但是，该组件会移动到 [!UICONTROL 段落系统] (NPR-33534)。
* 在 [!UICONTROL 包含子页面] 未在第一个内容根目录上检查属性(NPR-33533)。
* 重定向到 [!DNL Experience Manager] 具有锚点的页面在创作实例上无法作为 `PageRedirectServlets` 在URL片段或锚点之后放置查询字符串(NPR-34287)。
* `PageRedirectServlet` 附加 `.html` 后，Sling映射会导致链接失败(NPR-34271)。
* 您可以暂停 [!DNL Live Copy] 中的页面和继承会断开，如在编辑器模式中所示。 但是，在“页面”属性中，表示继承的图标错误地指示继承存在且未中断(NPR-34096)。
* 在“编辑模板”页面中显示允许的组件时出现问题(CQ-4297295)。
* 升级Chrome和Firefox后，弹出菜单无法按预期工作。 加载页面属性时，当其中包含数据时，它不会显示面板(CQ-4292995)。
* 中的多个跨站点脚本实例 [!DNL Experience Manager Sites] 组件(NPR-33926)。
* 向客户端发送信息时，不会针对各种组件对用户输入进行适当的编码(NPR-33696)。
* 以 `childrenlist.html` 显示HTML页面，而不是404响应。 此类URL容易遭受跨站点脚本攻击(NPR-33441)。

#### 资产 {#assets-6482}

* 上传的PDF文件的文本提取不起作用，且对PDF文件中某些词语的全文搜索无法获取该PDF文件(NPR-34165)。

   >[!NOTE]
   >要使此修复正常工作，请在安装Service Pack 6.4.8.2后重新启动Adobe Experience Manager实例。

* 在资产的搜索建议中，会在特殊字符之前添加反斜杠，这些字符的名称中带有特殊字符(NPR-33833)。

* 另存为智能收藏集的自定义过滤器未正确应用于资产，因此搜索结果不准确(NPR-33725)。

* 重新排序的文件夹中资产的时间轴表示资产已移动(NPR-33580)。

* 从批量取消发布资产 [!DNL Brand Portal] 导致 `Request-URI Too Long` 错误(NPR-34158)。

* 在列视图中，如果用户选择 [!UICONTROL 过滤器] 选项（取消选择资产），然后选择另一组要移动的资产，之前选择的资产也会移到新位置(NPR-34018)。

* 即使页面中有大量资产可容纳，滚动条在列表视图中也不可见(NPR-34156)。

* 的 [!UICONTROL 管理发布] 资产的页面已损坏，且其中的选项不起作用(CQ-4302509)。

**Dynamic Media**

* 将图像配置文件添加到具有多个（例如11）宽高比的文件夹后，智能裁剪功能会失败，并出现错误(NPR-34083)。

* 对 [!UICONTROL Adobe Experience Manager] 请勿同步到Dynamic Media Classic(NPR-34284、CQ-4299713)。

* 的 [!UICONTROL 全景图_自动切换] 中缺少修饰符标签 [!UICONTROL 行为] 选项卡 [!UICONTROL 查看器预设编辑器] 页面(CQ-4302043)。

#### 平台 {#platform-6482}

* 的默认值 **[!UICONTROL 连接超时]** 和 **[!UICONTROL 套接字超时]** 未指定默认代理（发布）配置的设置(NPR-33708)。
* 维护任务计划程序启动和停止维护任务的频率超过配置(NPR-33520)。
* 无法在已升级的Experience Manager实例上使用诊断工具下载日志(NPR-34419)。

#### 集成 {#integrations-6482}

* 的值 `library_path` 在生成时不考虑 [!DNL Adobe Launch] 库的库URL(从 [!DNL Adobe Dynamic Tag Management]. 此外，迁移的库使用的前缀与 [!DNL Adobe Launch] 库。 (NPR-34238).
* 更新页面属性时，从云服务继承的属性不会持久保留(NPR-33865)。

#### 用户界面 {#ui-6482}

* 搜索页面上显示的选定资产计数不正确(NPR-33540)。

#### 社区 {#communities-6482}

* 通过管理控制台添加的社区组的现有用户将从社区组控制台中的任何修改的用户列表中删除(NPR-34312)。

#### 表单 {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] 累积修补程序包不包含 [!DNL Experience Manager Forms]. 它们使用单独的 [!DNL Forms] 附加组件包。 此外，还发布了累积安装程序，其中包含针对 [!DNL Experience Manager Forms] 在JEE上。 有关更多信息，请参阅 [安装AEM Forms附加组件包](#install-aem-forms-add-on-package) 和 [安装AEM Forms JEE安装程序](#install-aem-forms-jee-installer).

**自适应表单**

* 当缺少自适应表单片段时，自适应表单无法呈现(NPR-34303)。

* 自适应表单字段的帮助内容描述显示段落HTML标记(NPR-34117)。

* 在 [!DNL Experience Manager Sites] 页面上，该页面会显示以下错误消息，并且不允许您添加任何新组件(NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* 当您选择 **[!UICONTROL 在服务器上重新验证]** 属性并上传多个附件后，自适应表单提交失败(NPR-33701)。

* 当您选择 **[!UICONTROL 使用页面语言]** 和 **[!UICONTROL 表单覆盖页面的整个宽度]** 选项 [!DNL Experience Manager Forms] 组件 [!DNL Experience Manager Sites] 页面，页面翻译失败(NPR-33641)。

* 提交在 [!DNL Experience Manager Sites] 页面上，analytics无法正常工作(NPR-31359)。

* 删除了 [!DNL Lodash] 和 [!DNL backbone] 库(NPR-33458)。

* 的 **[!UICONTROL 提交到REST端点]** 提交操作不适用于自适应表单(NPR-34513)。

* 辅助功能：当您尝试在未上载必填字段的附件的情况下提交自适应表单时，焦点不会自动转移到附件字段(NPR-34511)。

* 用户输入未针对 [!DNL Forms] 组件(NPR-33611)。

**工作流**

* [!DNL Experience Manager] 工作流清除操作失败，并显示以下错误消息(NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* 安装时 [!DNL Experience Manager] 6.4.8.1, [!UICONTROL 待办事项] 项目列表不显示为链接。 的文本 [!UICONTROL 待办事项] 项目包括HTML标记(NPR-34318)。

**后端集成**

* 无法在托管的AWS中配置表单数据模型 [!DNL Experience Manager Forms Linux] 环境(NPR-33617)。

**Designer**

* When [!DNL Acrobat DC] 安装在 [!DNL Experience Manager] Forms服务器， **[!UICONTROL 分发表单]** 选项在 [!DNL Experience Manager Designer] 版本6.x(NPR-34325)。

**文档安全**

* 安装后，无法在PDF文件中使用基于HSM的证书执行Sign操作 [!DNL Experience Manager] 6.4.8.0(NPR-34309)。

**升级**

* 升级 [!DNL JBoss] 版本至7.0.9( [!DNL Experience Manager Forms] 在 [!DNL Linux] 环境中，会导致错误(CQ-4300546)。

有关安全更新的信息，请参阅 [Experience Manager安全公告页](https://helpx.adobe.com/security/products/experience-manager.html).

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM累积修补程序包6.4.8.1是一个重要更新，它包括自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式发布以来的若干内部修补程序和客户修补程序。

AEM 累积修补程序包 6.4.8.1 依赖于 AEM 6.4 Service Pack 8。因此，您必须在安装AEM 6.4 Service Pack 8之后安装AEM累积修补程序包6.4.8.1。

AEM 6.4.8.1的一些主要功能亮点包括：

* 不允许匿名访问CRXDE Lite以增强安全性。 而是会将用户定向到登录屏幕。 请参阅 [使用CRXDE Lite进行开发](/help/sites-developing/developing-with-crxde-lite.md).
* 删除了与Adobe Experience Manager的包共享集成。
* 内置存储库 (Apache Jackrabbit Oak) 已更新至版本 1.8.21。

有关CFP和其他发行版类型的信息，请参阅 [AEM更新版本发行方式定义](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager 6.4.8.1提供了对以下问题的修复。

#### 站点 {#sites-6481}

* 匿名用户可以访问CRX DE Lite功能(NPR-33522)。
* 如果LiveCopy中本地组件的名称与Blueprint中组件的名称相同，并且从Blueprint中转出该组件，则不会将术语_msm_moved添加到本地组件的名称中(NPR-33207)。
* 重定向URL中不包含附加到原始请求的参数(NPR-33174)。
* 当Coral.Select选项设置emptyOption=true或包含值为“”的默认项时，dropdownshowhide.js文件会遇到错误：未捕获的类型错误：component.getValue不是函数(NPR-33163)。
* 当组件包含其他组件作为数据密钥资源时，父容器组件占位符将被替换为内部组件占位符(NPR-33119)。
* 如果内容片段基于架构并且包含必填文本区域或路径字段，则内容片段无法保存(NPR-33007)
* 使用现成的体验片段组件创建自定义组件并在AEM Sites页面中使用该组件时，AEM不会显示自定义组件的引用（用法）(NPR-32852)。
* 当AEM Sites页面包含在具有多个Live Copy的大型内容集中时，页面版本历史记录预览无法加载(NPR-32772)。
* 在提升启动项时，它会将“cq:LiveRelationship”混合添加到启动项中添加的每个组件。 无论是否在创建启动项时选择 — 继承源页面实时数据 — 选项，它都会影响所有启动项(NPR-32664)。
* 开始分页时，体验片段选取器不会加载所有项目(NPR-32605)。
* 无法为AEM Sites页面创建启动项。 创建启动项时会导致错误(NPR-32544)。
* 管理发布在激活请求工作流中不包含引用的资产(NPR-32463)。
* 显示调度程序运行状况检查 `Invalid cookie header` 日志文件中出现警告消息(NPR-33630)。
* Salesforce集成容易受到SSRF的攻击(NPR-32671)。
* PreferencesServlet中已反映XSS(NPR-33439)。

#### 资产 {#assets-6481}

* 资产计数不会因列表视图中选择内容的更改而发生更改(NPR-33285)。

* 选择父节点（其中显示单个子文件夹），然后选择子文件夹时，未启用“下一步”按钮(NPR-33284)。

* 启用DMS7或混合模式后，对于在存储库根目录上没有读取访问权限的用户，触屏UI无法呈现（出现错误）(NPR-33175)。

* 文件夹和资产名称中出现的GB18030字符在下载的zip文件中会更改为空白(NPR-33150)。

* 对于位于父文件夹中且带圆点的资产，在智能裁剪时会创建额外的文件夹 `.` 名称中的字符(NPR-32755)。

* 选择从通知收件箱中查看任务时，不会触发延迟加载，并且显示的资产不超过100个(NPR-32749)。

* 由于coral-info中的更改，指向共享收藏集的链接页面断开(NPR-32510)。

* 批量上传时的资产处理卡住(CQ-4293916)。

* Experience Manager中的SSRF漏洞(NPR-33437)。

#### 平台 {#platform-6481}

* 的 [!DNL Sling] 如果 `sling:match` 在下创建映射条目 `/etc/maps` (NPR-33308)。
* 取消激活页面时会触发所有刷新代理(NPR-32941)。
* 当您使用 `ScriptProcessor` 为缩小JavaScript库，日志文件会显示一条错误消息，指示JavaScript代码不符合严格模式。 API不提供启用或禁用严格模式的选项。 (NPR-32746).
* 当SQL查询运行较长时间（例如7小时）时，AEM停止响应(NPR-33043)。

#### 用户界面 {#ui-6481}

* 使用选择对话框搜索或浏览路径时，选择对话框会显示所选JCR节点的所有内容，而不是仅显示图像(NPR-32712)。

#### 翻译项目 {#tranlation-6481}

* A `NullPointerException` 运行翻译作业时在日志中显示错误(NPR-32220)。

#### 集成 {#integrations-6481}

* JSON跨站点脚本(NPR-32745)。

#### 社区 {#communities-6481}

* 创建新组后，作者不会被重定向到 [!UICONTROL 社区组] 部分 [!DNL Internet Explorer] 11(NPR-33202)。
* 访问 [!UICONTROL 活动流] 页面(NPR-33152)。
* 编辑 [!DNL Communities] 组和更改缩略图图像不会更新组缩略图图像(NPR-32603)。
* 在创建用户生成内容(UGC)的通知和订阅版本时，会存储不正确的源页面ID(CQ-4289703)。
* 跨站点脚本问题(NPR-33212)。

#### 工作流 {#workflow-6481}

* 当用户完成包含 [!UICONTROL 对话框参与者步骤] (NPR-32989)。

* 的 [!UICONTROL 时间轴] 左边栏中的选项加载所花费的时间比预期要长(NPR-32850)。

#### 表单 {#forms-6481}

>[!NOTE]
>
>AEM累积修补程序包不包括适用于AEM Forms的修补程序。 它们是通过单独的 Forms 附加组件包交付的。此外，发布了一个累计安装程序，其中包含 JEE 上对 AEM Forms 的修复。有关更多信息，请参阅 [安装AEM Forms附加组件包](#install-aem-forms-add-on-package) 和 [安装AEM Forms JEE安装程序](#install-aem-forms-jee-installer).

* 通信管理：当用户粘贴 [!DNL Word] 文档，文本文档片段不保留格式(NPR-33213)。
* 自适应Forms:自适应表单词典中的字符串新行会添加 `&#xa;` 字符到词典(NPR-33265)。
* 自适应Forms:用户无法保存包含多个附件的自适应表单(NPR-33214)。
* 自适应Forms: `AddInstance` 和 `RemoveInstance` 实例管理器类的方法不会在上为延迟加载片段添加动态实例数 [!DNL Internet Explorer 11] (NPR-33201)。
* 自适应Forms:对嵌入在 [!DNL Sites] 页面不会记录提交和放弃事件的数据(NPR-31359)。
* 自适应Forms:当用户粘贴 [!DNL Word] 文档到自适应表单并提交它，提交的自适应表单包含unicode字符。 此外，PDF到PDF/A的转换因Unicode字符而失败(NPR-33348)。
* 后端集成：表单数据模型请求因不正确的非活动状态而失败，因为刷新令牌过期(NPR-33168)。
* 文档服务：由于缺少Gibson Jar，转换PDF服务无法将PDF文档转换为PostScript [!DNL WebLogic] 在 [!DNL Linux] 服务器(NPR-33515、CQ-4292239)。
* 文档服务：当用户将文本文件转换为PDF时，日语字符无法正确呈现(NPR-33239)。
* 将XSS与GuideSOMProviderServlet一起存储(NPR-32701)。

## 安装 6.4.8.4 {#install}

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
>对于在AEM 6.4上安装了功能包的客户。由Adobe提供的可选功能包依赖于发行版本和Service Pack。 如果您已安装功能包，请联系AEM客户关怀团队以验证这些功能包与AEM 6.4的累积修补程序包的兼容性。

* AEM 6.4.8.4需要AEM 6.4.8.0。请访问 [升级文档](../sites-deploying/upgrade.md) 以了解详细说明。
* 在具有 MongoDB 和多个实例的部署中，使用包管理器在其中一个 Author 实例上安装 AEM 6.4.8.4。
* 在安装累积修补程序包之前，请确保拥有AEM实例的快照或新备份。
* 安装之前请重新启动该实例。尽管仅当实例仍处于更新模式时才需要执行此操作（这种情况下实例刚从早期版本更新），但通常建议当实例运行较长时间时执行此操作。

>[!NOTE]
>
>Adobe 建议不要移除或卸载 AEM 6.4.8.4 包。

### 安装累积修补程序包 {#install-cumulative-fix-pack}

执行以下步骤以在现有 AEM 6.4.8.0 实例上安装累积修补程序包：

1. 单击 [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-4.0.zip) 链接以下载包。

1. 打开[包管理器](http://localhost:4502/crx/packmgr/index.jsp)，并单击&#x200B;**[!UICONTROL 上传包]**&#x200B;以上传包。

1. 选择包名称，然后单击&#x200B;**[!UICONTROL 安装]**。

>[!NOTE]
>
>**包管理器 UI 中的对话框有时会在 AEM 6.4.8.4 的安装过程中退出**
>
>因此，建议在访问该实例之前先等待错误日志稳定下来。在确保安装成功之前，用户必须等待与卸载更新程序包相关的特定日志。 这通常出现在 Safari 中，但也可能会间歇性发生在任何浏览器中。

### 自动安装 {#auto-installation}

可通过两种方法将 AEM 6.4.8.4 自动安装到正在运行的实例上：

A.将包放入……*/crx-quickstart/install* 文件夹中。包会自动进行安装。

B.使用 [包管理器中的HTTP API](https://helpx.adobe.com/cn/experience-manager/aem-previous-versions.html)  — 确保使用 `cmd=install&recursive=true`  — 以便安装嵌套包。

>[!NOTE]
>
>AEM 6.4.8.4 不支持 Bootstrap 安装。

### 验证安装 {#validate-install}

1. 现在，产品信息页面 (*/system/console/productinfo*) 应该在“已安装的产品”下显示更新的版本字符串“Adobe Experience Manager，版本 6.4.8.4”。
1. 所有 OSGi 包在 OSGi 控制台中均为“活动”或“片段”（使用 Web 控制台：/system/console/bundles）。
1. OSGi包org.apache.jackrabbit.oak-core的版本为1.8.17或更高版本(使用Web控制台：/system/console/bundles)。

要确定要随此版本的AEM Sites和Assets一起运行的经认证的平台，请参阅 [技术要求](../sites-deploying/technical-requirements.md).

>[!NOTE]
>成功安装包后，会显示一条信息性消息，指示内容包已成功安装，例如 **&quot;已成功安装内容包AEM-6.4-Service-Pack-8。&quot;**

### 更新Dynamic Media查看器(5.10.1) {#update-dynamic-media-viewers}

AEM 6.4.8.4包含新版Dynamic Media查看器(5.10.1)，该查看器支持在“图像预设”页面上检查重复名称。 建议Dynamic Media客户运行以下命令，以将现成的查看器预设调至最新状态。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

将新查看器预设复制到/conf位置。

### 安装 AEM Forms 附加组件包 {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 在计划的 [!DNL Experience Manager] 累积修补程序包发行日期后一周发布附加组件包。

>[!NOTE]
>
>如果您未使用 AEM Forms，请跳过。AEM Forms 中的修复通过单独的附加包来交付。

1. 确保已安装AEM累积修补程序包。
1. 下载列于的相应Forms附加组件包 [AEM Forms版本](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) 操作系统。
1. 按照 [安装AEM Forms附加组件包](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### 安装AEM Forms JEE安装程序 {#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果您未在 JEE 上使用 AEM Forms，请跳过。AEM Forms JEE 中的修复通过单独的安装程序来交付。

有关安装AEM Forms JEE的累积安装程序和部署后配置的信息，请参阅 [AEM Forms JEE补丁安装程序](jee-patch-installer-64.md).

>[!NOTE]
>
>在JEE上安装Experience Manager Forms的累积安装程序后，安装最新的Forms附加组件包，并从 `crx-repository\install` 文件夹，然后重新启动服务器。

### Uber Jar {#uber-jar}

适用于AEM 6.4.8.4的Uber Jar可在 [Maven中央存储库](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.4/).

要在 Maven 项目中使用 Uber Jar，请参阅[如何使用 Uber Jar](../sites-developing/ht-projects-maven.md) 一文，并在项目 POM 中包含以下依赖项：

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.4</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar和其他相关对象可在Maven中央存储库中使用，而不是Adobe公共Maven存储库(repo.adobe.com)。 主UberJar文件将重命名为 `uber-jar-<version>.jar`. 因此，没有 `classifier`，使用 `apis` 作为值，对于 `dependency` 标记。

## 已移除/已弃用功能 {#removed-deprecated-features}

此部分列出了 AEM 6.4 中已移除或已弃用的功能和特性。

| 区域 | 功能 | 替换 | 版本号 |
|---|---|---|---|
| 资产 | 管理子资产的标记操作 | 无替换项 | AEM 6.4.2.0 |
| 资产和 Creative Cloud 集成 | AEM 6.2 中引入了 [AEM 到 Creative Cloud 的文件夹共享](https://docs.adobe.com/content/help/zh-Hans/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html)功能，以便创意用户可以从 AEM 访问资产。在 Creative Cloud 应用程序中发布的新功能“Adobe 资产链接”提供了更佳的用户体验，能够直接从 Photoshop、InDesign 和 Illustrator 中轻松访问 AEM Assets。Adobe 不会再进一步增强文件夹共享功能。虽然AEM中包含该功能，但强烈建议客户使用替换。 | Adobe资产链接或桌面应用程序。 有关更多信息，请参阅 [AEM Creative Cloud 集成](/help/assets/aem-cc-integration-best-practices.md)一文。 | AEM 6.4.4.0 |

## 已知问题 {#known-issues}

* 如果您从 [!DNL Experience Manager] 6.4至 [!DNL Experience Manager] 6.5，某些包可能无法将其状态显示为 `Active`. 安装最新 [!DNL Experience Manager] 6.5 Service Pack以解决此问题。

有关AEM 6.4.8.0 Service Pack已知问题的信息，请参阅 [AEM 6.4.8.0 Service Pack发行说明](sp-release-notes.md).

## 包含的 OSGi 包和内容包 {#osgi-bundles-and-content-packages-included}

以下文本文档列出了 AEM 6.4.8.4 中包含的 OSGi 包和内容包.

AEM 6.4.8.4 中包含的 OSGi 包列表

[获取文件](assets/6.4.8.4_osgi_bundles.txt)

AEM 6.4.8.4 中包含的内容包列表

[获取文件](assets/6.4.8.4_content_packages.txt)

## 有用资源 {#helpful-resources}

* [AEM 6.4 发行说明](../release-notes/release-notes.md)
* [AEM 产品页面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 文档](https://helpx.adobe.com/cn/support/experience-manager/6-4.html)
* 订阅 [Adobe 产品更新早知道](https://www.adobe.com/cn/subscription/priority-product-update.html)

## 受限的网站 {#restricted-sites-new}

这些网站仅适用于客户。如果您是客户并且需要访问，请联系您的 Adobe 客户经理。

* [产品下载：licensing.adobe.com](https://licensing.adobe.com/)
* [联系客户支持](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
