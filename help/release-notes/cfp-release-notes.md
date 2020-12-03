---
title: AEM 6.4 Cumulative Fix Pack发行说明
description: 特定于Adobe Experience Manager6.4累积修复包的发行说明。
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: f74e20c5264dc38dcbe20c8fc6b9beaaee7cc6da
workflow-type: tm+mt
source-wordcount: '4112'
ht-degree: 11%

---


# AEM 6.4 Cumulative Fix Pack发行说明{#aem-cumulative-fix-pack-release-notes}

## 发行信息 {#release-information}

<!-- TBD: Update the SD URL. -->

| 产品 | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| 版本 | 6.4.8.3 |
| 类型 | 累积修补程序包 |
| 日期 | 2020年11月26日 |
| 先决条件 | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| 下载 URL | [软件分发](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip)上的AEM 6.4.8.3 |

## AEM 6.4.8.3 包含哪些内容 {#what-s-included-in-aem}

AEM Cumulative Fix Pack 6.4.8.3是自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式上市以来，包含若干内部和客户修复的重要更新。

AEM 6.4.8.3是依赖于AEM 6.4 Service Pack 8的累积修补程序包(CFP)。 安装AEM 6.4 Service Pack 8后安装CFP。

在AEM 6.4.8.3中，内置存储库(Apache Jackrabbit Oak)已更新至版本1.8.23。

有关CFP和其他类型版本的信息，请参见[AEM更新版本车辆定义](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager6.4.8.3修复了以下问题。

### 站点 {#sites-6483}

* 更新内容片段的变体文本时，将更新主控内容片段的内容，而不是变体(NPR-35080)。

* 当您为组件的字符串类型标签属性设置一个数字值，删除该组件，然后使用撤消选项将其重新启用时，标签属性的类型将自动从字符串更改为长(NPR-34738)。

* 将文件上传组件添加到多字段时，图像路径会存储在组件节点中，而不是多字段节点(NPR-34423)。

* 在“移动页面”向导中，即使未选择目标，下一个按钮仍处于启用状态(NPR-34460)。

* 当父组件包含`cq:isContainer`属性时，继承的组件不会自动包含该属性(CQ-4308409)。

* 使用`calc()`函数使用CSS微型化时，将删除`+`符号周围的空白(NPR-34991)。

* 开始AEM实例时，`com.adobe.granite.maintenance.impl.MaintenanceTaskManagerImpl`和`com.adobe.granite.maintenance.impl.TaskScheduler`组件不以`Active`状态显示(NPR-34952)。

### [!DNL Assets] {#assets-6483}

* 在创建现有资产的某个版本时，如果将元数据用户档案应用到该文件夹，则用户对元数据的更新不会持续存在(NPR-34833)。
* 将[!DNL Adobe Asset Link]与[!DNL Adobe InDesign]一起使用时，搜索结果不包含文件夹和集合，但仅包含资产(NPR-34700)。
* 在文件夹上拖动资产以移动资产时，用户界面还显示选项[!UICONTROL 放入Lightbox]和[!UICONTROL 放入收藏集]。 即使取消移动操作，用户界面仍继续显示后两个选项(NPR-34525)。
* 打开“管理发布”界面时，发布选项不可用，选择取消发布选项后，范围页面为空(CQ-4302509)。

#### [!DNL Dynamic Media] {#dynamic-media}

* 在“图像预设”设置中，当]中取消选择“启用JPG色度缩减采样”[!UICONTROL 选项时，所做的更改不会与[!DNL Experience Manager]同步(NPR-34284)。[!DNL Dynamic Media]
* 在[!UICONTROL 查看器预设编辑器]中，编辑[!UICONTROL PanoramicImage/PanoramicImage_VR]预设时，在`PanoramicView`组件中，`PANORAMICVIEW_AUTOROTATE`修饰符标签不可用(CQ-4302043)。
* 从[!DNL Experience Manager]取消发布视频不会取消发布配置的Scene7上的自适应视频集。 (CQ-4304405).

### 平台 {#platform-6483}

* 将`emitUseStrict`标志添加到Google Closure Compiler(GCC)处理器函数`com.adobe.granite.ui.clientlibs.impl.HtmlLibraryManagerImpl`。 该标志禁止`use strict`指令的输出(NPR-34830)。
* 在开始每日或每周维护任务时返回`NullPointerException`(NPR-34702)。
* [!DNL Apache Sling Health Check]工具已弃用。 而应使用[图案检测器](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/upgrading/pattern-detector.html)检测内容违规(NPR-33929)。

### 集成 {#integrations-6483}

* 从文件夹导航到[!UICONTROL Audiences]页面时，[!UICONTROL 创建]按钮会显示在[!UICONTROL Audiences]页面上(NPR-35152)。

### 用户界面 {#ui-6483}

* [!UICONTROL Omnisearch]用户界面上的[!UICONTROL Filters]搜索面板也会返回除搜索运行位置之外的位置的结果(NPR-34877)。
* 在关闭[!UICONTROL Omnisearch]用户界面上的[!UICONTROL 滤镜]面板时，左边栏不会重置为[!UICONTROL 内容]选择，这将阻止重新打开[!UICONTROL 滤镜]面板(NPR-34483)。
* 访问页面属性时返回`NullPointerException`(NPR-34509)。

### 社区 {#communities-6483}

<!-- Following fixes of 6483 are documented on Nov 11 20202 by Vishabh. 
-->

* 产品中所有不公平术语的实例都被接受的等价物取代(NPR-34506)。

### 商务 {#commerce-6483}

* 当一个集合中有15种以上的产品时，该集合仅显示前15种产品(NPR-34494)。

### 表单 {#forms-6483}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 在计划的Cumulative Fix Pack发布日期后一周 [!DNL Experience Manager] 内发布附加包。

**自适应表单**

* 在应用[!DNL Experience Manager]累积修复包(NPR-35127)后，无法使用经典UI编辑自适应表单。

* 由于缓存失效，片段以自适应形式加载需要较长的时间(NPR-34655)。

* 辅助工具：Tab键导航不适用于自适应格式的屏幕阅读器(NPR-34550)。

**通信管理**

* 从ES3迁移资源时，资源包括两个不可编辑的默认条件(NPR-34971)。

**Foundation JEE**

* 将[!DNL AEM Forms]用户从Flash迁移到HTML(CQ-4304075)。

有关安全更新的信息，请参阅[Experience Manager安全公告页](https://helpx.adobe.com/security/products/experience-manager.html)。

## 以前的累积修补程序包中包含的修补程序和功能包 {#hotfixes-and-feature-packs-included-in-previous-cumulative-fix-packs}

### Adobe Experience Manager 6.4.8.2 {#experience-manager-6482}

AEM Cumulative Fix Pack 6.4.8.2是自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式上市以来，包含若干内部和客户修复的重要更新。

AEM 6.4.8.2是依赖于AEM 6.4 Service Pack 8的累积修复包(CFP)。 在安装AEM 6.4 Service Pack 8后安装CFP。

在AEM 6.4.8.2中，内置存储库(Apache Jackrabbit Oak)已更新至版本1.8.22。

有关CFP和其他类型版本的信息，请参见[AEM更新版本车辆定义](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager6.4.8.2修复了以下问题。

#### 站点 {#sites-6482}

* 如果`RolloutConfigManagerFactoryImpl`无法加载转出配置，则它不会尝试加载缺失的配置。 它返回缓存的配置(NPR-34091)。
* 在Text核心组件中，使用源HTML编辑选项后，将删除`em`标签中的类(NPR-34080)。
* 从Experience Manager6.2升级到Experience Manager6.5时，静态模板的Parsys组件无法正确显示。 Parsys组件的高度设置为0，并且其中的组件不可见(NPR-34044)。
* 模板编辑器中允许的组件的标签信息不显示(NPR-33908)。

   ![布局容器中缺少标签](assets/33908_missing_labels.png)

* 用户无法在第四级嵌套组件(NPR-33873)之后向parsys添加或编辑组件。
* 如果更改了可编辑模板的初始内容，然后发布了模板，则使用此模板创建的任何新页面都会显示模板的“已发布日期”，即使这些页面未发布(NPR-33822)。
* 复制和粘贴操作期间将删除副本上`cq:acLinks`和`cq:acUUID`的属性(NPR-33793)。[!DNL Adobe Campaign]
* 在[!UICONTROL “实时用法”]选项卡中，只显示49个结果。 它不显示组件的所有用法(NPR-33710)。
* 在创作时，URL中具有`/`字符的网页会变得无响应。 在创作时添加组件时，CPU使用量会增加，浏览器会停止响应(NPR-33625)。
* 在[!DNL RTE]的内联编辑模式下，拖动图像不适用于Text组件(NPR-33579)。
* 可以在蓝图页面中创建与页面名称同名的组件。 在转出期间，此类组件通过后缀`_msm_moved`重命名。 但是，该组件将移至[!UICONTROL 段落系统]的末尾(NPR-33534)。
* 如果未在第一个内容根目录上检查[!UICONTROL 包含子页]属性，启动促销不会发布页面(NPR-33533)。
* 使用锚点重定向到[!DNL Experience Manager]页对Author实例无效，因为`PageRedirectServlets`将查询字符串放在URL片段或锚点之后(NPR-34287)。
* `PageRedirectServlet` 导致 `.html` 链路故障的Sling映射后追加(NPR-34271)。
* 可以暂停页面的[!DNL Live Copy]，继承在中断开，如在“编辑器”模式中所示。 但是，在“页面”属性中，表示继承的图标错误地指示继承存在且未断开(NPR-34096)。
* 在“编辑模板”页中显示允许的组件时出现问题(CQ-4297295)。
* 升级Chrome和Firefox后，弹出菜单无法按预期工作。 加载页面属性时，当其中包含数据时，它不显示面板(CQ-4292995)。

#### 资产 {#assets-6482}

* 上传的PDF文件的文本提取不起作用，PDF文件中某些单词的全文搜索无法获取该PDF文件(NPR-34165)。

   >[!NOTE]
   >要使此修复正常工作，请在安装Service Pack 6.4.8.2后重新启动Adobe Experience Manager实例。

* 在搜索资源的建议中，在特殊字符之前添加反斜杠，资源名称中包含特殊字符(NPR-33833)。

* 另存为智能收藏夹的自定义滤镜未正确应用于资源，因此搜索结果不准确   (NPR-33725)。

* 重新排序的文件夹内资源的时间轴描述该资源已移动(NPR-33580)。

* 从[!DNL Brand Portal]批量取消发布资源会导致`Request-URI Too Long`错误(NPR-34158)。

* 在列视图中，如果用户在选择一组资源后选择[!UICONTROL Filter]选项（资源将被取消选择），然后选择另一组资源进行移动，则先前选择的资源也将移动到新位置(NPR-34018)。

* 即使页面中有大量资源可容纳，滚动条在列表视图中也不可见(NPR-34156)。

* 资源的[!UICONTROL 管理出版物]页面已断开，其中的选项无效(CQ-4302509)。

**Dynamic Media**

* 将图像配置文件添加到具有多个长宽比（例如，11）的文件夹时，智能裁剪功能会失败，并出现错误(NPR-34083)。

* 对[!UICONTROL Adobe Experience Manager]中的图像预设所做的更改不会同步到Scene7出版系统(NPR-34284、CQ-4299713)。

* [!UICONTROL 查看器预设编辑器]页面(CQ-4302043)中的“行为”标签[!UICONTROL “行为”]中缺少[!UICONTROL PANORAMICVIEW_AUTOTATE]修饰符标签。

#### 平台 {#platform-6482}

* 未指定Default Agent（发布）配置的&#x200B;**[!UICONTROL Connect Timeout]**&#x200B;和&#x200B;**[!UICONTROL Socket Timeout]**&#x200B;设置的默认值(NPR-33708)。
* 维护任务调度程序启动和停止维护任务的频率超过配置(NPR-33520)。
* 无法使用诊断工具在升级的Experience Manager实例上下载日志(NPR-34419)。

#### 集成 {#integrations-6482}

* 为从[!DNL Adobe Dynamic Tag Management]迁移的库生成[!DNL Adobe Launch]库URL时，不考虑`library_path`的值。 此外，迁移的库使用的前缀与[!DNL Adobe Launch]库不同。 (NPR-34238).
* 更新页面属性时，从云服务继承的属性不会保留(NPR-33865)。

#### 用户界面 {#ui-6482}

* 在搜索页面上显示的选定资源计数不正确(NPR-33540)。

#### 社区 {#communities-6482}

* 通过admin console添加的社区组的现有用户将从社区组控制台中任何修改的用户列表中删除(NPR-34312)。

#### 表单 {#forms-6482}

>[!NOTE]
>
>[!DNL Experience Manager] 累积修复包不包含修复 [!DNL Experience Manager Forms]。它们使用单独的[!DNL Forms]加载项包交付。 此外，还发布了一个累积安装程序，其中包含对JEE上的[!DNL Experience Manager Forms]的修复。 有关详细信息，请参阅[安装AEM Forms加载项包](#install-aem-forms-add-on-package)和[安装AEM FormsJEE安装程序](#install-aem-forms-jee-installer)。

**自适应表单**

* 当缺少自适应表单片段时，自适应表单无法渲染(NPR-34303)。

* 自适应表单域的帮助内容描述显示段落HTML标签(NPR-34117)。

* 在[!DNL Experience Manager Sites]页面上添加Forms容器时，该页显示以下错误消息，不允许您添加任何新组件(NPR-33858):

   `DevTools failed to load SourceMap: Could not load content for <Link>. HTTP error: status code 404, net::ERR_HTTP_RESPONSE_CODE_FAILURE`

* 选择&#x200B;**[!UICONTROL 在Server]**&#x200B;上重新验证属性并上传多个附件时，自适应表单无法提交(NPR-33701)。

* 选择&#x200B;**[!UICONTROL 使用页面语言]**&#x200B;和&#x200B;**[!UICONTROL 表单覆盖[!DNL Experience Manager Sites]页面上[!DNL Experience Manager Forms]组件中的Page]**&#x200B;选项的整个宽度时，该页面无法翻译(NPR-33641)。

* 当您提交嵌入[!DNL Experience Manager Sites]页面的启用分析的自适应表单时，分析无法正确工作(NPR-31359)。

* 删除了对[!DNL Lodash]和[!DNL backbone]库的依赖项(NPR-33458)。

* **[!UICONTROL 提交到REST端点]**&#x200B;提交操作不适用于自适应表单(NPR-34513)。

* 辅助工具：当您尝试提交自适应表单而不上传必填字段的附件时，焦点不会自动转到附件字段(NPR-34511)。

**工作流**

* [!DNL Experience Manager] “工作流清理”操作失败并显示以下错误消息(NPR-33576):

   `java.lang.UnsupportedOperationException: The query read more than 500000 nodes in memory`

* 安装[!DNL Experience Manager] 6.4.8.1时，项目的[!UICONTROL To Do]列表不显示为链接。 [!UICONTROL To Do]项的文本包括HTML标签(NPR-34318)。

**后端集成**

* 无法在AWS托管[!DNL Experience Manager Forms Linux]环境中配置表单数据模型(NPR-33617)。

**设计人员**

* 在[!DNL Experience Manager]Forms服务器上安装[!DNL Acrobat DC]时，**[!UICONTROL 分发表单]**&#x200B;选项在[!DNL Experience Manager Designer] 6.x版中不可用(NPR-34325)。

**文档安全**

* 在安装[!DNL Experience Manager] 6.4.8.0后，无法在PDF文件中使用基于HSM的证书执行Sign操作(NPR-34309)。

**升级**

* 在[!DNL Linux]环境中，使用“文档安全性”将[!DNL JBoss]版本升级到[!DNL Experience Manager Forms]的7.0.9时，会导致错误(CQ-4300546)。

有关安全更新的信息，请参阅[Experience Manager安全公告页](https://helpx.adobe.com/security/products/experience-manager.html)。

### Adobe Experience Manager 6.4.8.1 {#experience-manager-6481}

AEM Cumulative Fix Pack 6.4.8.1是自2020年3月AEM 6.4 Service Pack 8(6.4.8.0)正式上市以来，包含若干内部和客户修复的重要更新。

AEM Cumulative Fix Pack 6.4.8.1取决于AEM 6.4 Service Pack 8。 因此，在安装AEM 6.4 Service Pack 8之后，必须安装AEM Cumulative Fix Pack 6.4.8.1包。

AEM 6.4.8.1的一些主要亮点是：

* 不允许匿名访问CRXDE Lite以增强安全性。 而是将用户定向到登录屏幕。 请参阅[使用CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md)开发。
* 删除了与Adobe Experience Manager的包共享集成。
* 内置存储库 (Apache Jackrabbit Oak) 已更新至版本 1.8.21。

有关CFP和其他类型版本的信息，请参见[AEM更新版本车辆定义](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/deploying/update-release-vehicle-definitions.html)

Adobe Experience Manager6.4.8.1修复了以下问题。

#### 站点 {#sites-6481}

* 匿名用户可以访问CRX DE Lite功能(NPR-33522)。
* 当LiveCopy中某个本地组件的名称与蓝图中某个组件的名称相同且该组件从蓝图中推出时，术语_msm_moved不会添加到本地组件的名称(NPR-33207)。
* 附加到原始请求的参数不包括在重定向URL中(NPR-33174)。
* 当Coral.Select选项设置emptyOption=true或包含值为“”的默认项时，dropdownshowhide.js文件会遇到错误：未捕获的TypeError:component.getValue不是函数(NPR-33163)。
* 当组件将另一个组件作为数据机密资源包含时，父容器组件占位符将替换为内部组件占位符(NPR-33119)。
* 如果内容片段基于架构并且包含必填文本区域或路径字段，则内容片段无法保存(NPR-33007)
* 当您使用开箱即用的体验片段组件创建自定义组件并在AEM Sites页中使用它时，AEM不显示自定义组件的引用（用法）(NPR-32852)。
* 如果AEM Sites页面是包含多个实时副本的大型内容集的一部分，则无法加载页面版本历史记录预览(NPR-32772)。
* 升级启动时，它会将“cq:LiveRelationship”混音添加到启动中添加的每个组件。 无论是否在创建启动时选择— Inherit source page live data —选项(NPR-32664)，它都会影响所有启动。
* 当分页开始时，Experience Fragments拾色器不会加载所有项目(NPR-32605)。
* 无法为AEM Sites页创建启动。 启动创建会导致错误(NPR-32544)。
* “管理出版物”不在激活工作流程请求中包含引用的资源(NPR-32463)。
* 调度程序运行状况检查在日志文件中显示`Invalid cookie header`警告消息(NPR-33630)。
* Salesforce集成易受SSRF(NPR-32671)的影响。
* PreferencesServlet中反映的XSS(NPR-33439)。

#### 资产 {#assets-6481}

* 资源计数不会因“列表视图”中所选内容的更改而更改(NPR-33285)。

* 在选择父节点（其中显示单个子文件夹），然后选择子文件夹时，不启用“下一步”按钮(NPR-33284)。

* 启用DMS7或混合模式时，如果用户没有存储库根目录的读访问权限，则触摸UI无法呈现（出现错误）(NPR-33175)。

* 文件夹和资源名称中出现的GB18030字符在下载的zip文件中更改为空白(NPR-33150)。

* 在智能裁剪父文件夹中的资源时，会创建额外的文件夹，其名称中带有点`.`字符(NPR-32755)。

* 不触发延迟加载，在选择查看通知收件箱中的任务时，将显示不超过100个资源(NPR-32749)。

* 由于coral-info中的更改，共享集合的链接页面被断开(NPR-32510)。

* 批量上传时的资产处理会卡住(CQ-4293916)。

* Experience Manager中的SSRF漏洞(NPR-33437)。

#### 平台 {#platform-6481}

* 如果在`/etc/maps`下创建`sling:match`映射条目，则不调用[!DNL Sling]过滤器(NPR-33308)。
* 在停用页面时触发所有刷新代理(NPR-32941)。
* 使用`ScriptProcessor` API缩小JavaScript库时，日志文件会显示一条错误消息，指示JavaScript代码不符合严格模式。 API不提供启用或禁用严格模式的选项。 (NPR-32746).
* 当SQL查询运行较长时间（例如7小时）时，AEM停止响应(NPR-33043)。

#### 用户界面 {#ui-6481}

* 使用选择对话框搜索或浏览路径时，选择对话框将显示所选JCR节点的所有内容，而不是仅显示图像(NPR-32712)。

#### 翻译项目 {#tranlation-6481}

* 在运行转换作业的日志中出现`NullPointerException`错误(NPR-32220)。

#### 集成 {#integrations-6481}

* JSON的跨站点脚本(NPR-32745)。

#### 社区 {#communities-6481}

* 创建新组后，作者不会重定向到[!DNL Internet Explorer] 11上的[!UICONTROL 社区组]部分(NPR-33202)。
* 访问[!UICONTROL 活动流]页时出错(NPR-33152)。
* 编辑[!DNL Communities]组并更改缩览图图像不会更新组缩览图图像(NPR-32603)。
* 创建用户生成内容(UGC)的通知和订阅版本时，会存储源页面的不正确ID(CQ-4289703)。
* 跨站点脚本问题(NPR-33212)。

#### 工作流 {#workflow-6481}

* 当用户完成包含[!UICONTROL “对话参与者”步骤]的工作流时，弹出的对话框中不显示某些组件(NPR-32989)。

* 左侧边栏中的[!UICONTROL 时间轴]选项加载所花的时间比预期要多(NPR-32850)。

#### 表单 {#forms-6481}

>[!NOTE]
>
>AEM累积修复包不包含针对AEM Forms的修复。 它们是通过单独的 Forms 附加组件包交付的。此外，还发布了包含针对AEM Forms的JEE修复的累积安装程序。 有关详细信息，请参阅[安装AEM Forms加载项包](#install-aem-forms-add-on-package)和[安装AEM FormsJEE安装程序](#install-aem-forms-jee-installer)。

* 通信管理：当用户粘贴[!DNL Word]文档中的内容时，文本文档片段不保留格式(NPR-33213)。
* 适应性Forms:自适应表单词典中字符串的新行将`&#xa;`字符添加到词典(NPR-33265)。
* 适应性Forms:用户无法保存包含多个附件的自适应表单(NPR-33214)。
* 适应性Forms:Instance Manager类的`AddInstance`和`RemoveInstance`方法不会在[!DNL Internet Explorer 11]上为惰性加载片段添加动态数目的实例(NPR-33201)。
* 适应性Forms:在[!DNL Sites]页面中嵌入的自适应表单上启用的分析不会记录“提交”和“放弃”事件的数据(NPR-31359)。
* 适应性Forms:当用户将[!DNL Word]文档中的内容粘贴到自适应表单并提交它时，提交的自适应表单包含Unicode字符。 此外，PDF到PDF/A的转换由于Unicode字符而失败(NPR-33348)。
* 后端集成：由于不正确的非活动状态，刷新令牌过期时表单数据模型请求失败(NPR-33168)。
* 文档服务：由于[!DNL Linux]服务器上[!DNL WebLogic]的Gibson Jar缺少(NPR-33515、CQ-4292239),“转换PDF”服务无法将PDF文档转换为PostScript。
* 文档服务：当用户将文本文件转换为PDF时，日文字符无法正确渲染(NPR-33239)。
* 使用GuideSOMProviderServlet存储XSS(NPR-32701)。

## 安装6.4.8.3 {#install}

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
>对于安装在AEM 6.4上的Feature Pack的客户。Adobe提供的可选功能包依赖于发行版和服务包。 如果您安装了任何功能包，请与AEM客户关怀团队联系，以验证这些功能包与AEM 6.4的此累积修复包的兼容性。

* AEM 6.4.8.3需要AEM 6.4.8.0。请访问[升级文档](../sites-deploying/upgrade.md)以获取详细说明。
* 在具有 MongoDB 和多个实例的部署中，使用包管理器在其中一个 Author 实例上安装 AEM 6.4.8.3。
* 在安装累积修复包之前，请确保拥有AEM实例的快照或新鲜备份。
* 安装之前请重新启动该实例。尽管仅当实例仍处于更新模式时（这种情况下是从早期版本更新实例时）才需要此设置，但通常建议实例在较长的时间内运行。

>[!NOTE]
>
>Adobe 建议不要移除或卸载 AEM 6.4.8.3 包。

### 安装Cumulative Fix Pack {#install-cumulative-fix-pack}

执行以下步骤以在现有 AEM 6.4.8.0 实例上安装累积修补程序包：

1. 单击[软件分发](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-3.0.zip)链接以下载包。

1. 打开[包管理器](http://localhost:4502/crx/packmgr/index.jsp)，然后单击&#x200B;**[!UICONTROL 上传包]**&#x200B;以上传包。

1. 选择包名称，然后单击&#x200B;**[!UICONTROL 安装]**。

>[!NOTE]
>
>**包管理器 UI 中的对话框有时会在 AEM 6.4.8.3 的安装过程中退出**
>
>因此，建议在访问该实例之前先等待错误日志稳定下来。用户必须等待与卸载更新程序包相关的特定日志，才能确保安装成功。 这通常出现在 Safari 中，但也可能会间歇性发生在任何浏览器中。

### 自动安装  {#auto-installation}

可通过两种方法将 AEM 6.4.8.3 自动安装到正在运行的实例上：

答：将包放入……*/crx-quickstart/install* 文件夹中。包会自动进行安装。

B.使用包管理器](https://helpx.adobe.com/cn/experience-manager/aem-previous-versions.html)中的[ HTTP API —— 确保使用`cmd=install&recursive=true` —— 以便安装嵌套的包。

>[!NOTE]
>
>AEM 6.4.8.3 不支持 Bootstrap 安装。

### 验证安装 {#validate-install}

1. “产品信息”页面(*/system/console/productinfo*)现在应在“已安装产品”下显示更新的版本字符串“Adobe Experience Manager, 6.4.8.3版”。
1. 所有 OSGi 包在 OSGi 控制台中均为“活动”或“片段”（使用 Web 控制台：/system/console/bundles）。
1. OSGI捆绑包org.apache.jackrabbit.oak-core在版本1.8.17或更高版本上(使用Web控制台：/system/console/bundles)。

要确定与此版本的AEM Sites和资产一起运行的认证平台，请参阅[技术要求](../sites-deploying/technical-requirements.md)。

>[!NOTE]
>成功安装包时，将显示一条信息性消息，指示内容包已成功安装，如&#x200B;**&quot;成功安装内容包AEM-6.4-Service-Pack-8。&quot;**

### 更新动态媒体查看器(5.10.1){#update-dynamic-media-viewers}

AEM 6.4.8.3包含新版Dynamic Media查看器(5.10.1)，可在“图像预设”页面上检查重复的名称。 建议Dynamic Media客户运行以下命令，将盒式查看器预设调出为最新状态。

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

将新的查看器预设复制到/conf位置。

### 安装 AEM Forms 附加组件包 {#install-aem-forms-add-on-package}

>[!NOTE]
>
>[!DNL Experience Manager Forms] 在计划的Cumulative Fix Pack发布日期后一周 [!DNL Experience Manager] 内发布附加包。

>[!NOTE]
>
>如果您未使用 AEM Forms，请跳过。AEM Forms 中的修复通过单独的附加包来交付。

1. 确保已安装AEM Cumulative Fix Pack。
1. 下载操作系统[AEM Forms版本](https://helpx.adobe.com/cn/aem-forms/kb/aem-forms-releases.html)中列出的相应表单加载项包。
1. 按照[安装AEM forms add-on包](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package)中的说明安装表单加载项包。

### 安装AEM FormsJEE安装程序{#install-aem-forms-jee-installer}

>[!NOTE]
>
>如果您未在 JEE 上使用 AEM Forms，请跳过。AEM Forms JEE 中的修复通过单独的安装程序来交付。

有关安装AEM FormsJEE的累积安装程序和部署后配置的信息，请参阅[AEM FormsJEE修补程序安装程序](jee-patch-installer-64.md)。

### Uber Jar {#uber-jar}

用于AEM 6.4.8.3的Uber Jar位于[ Maven Central存储库](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.4.8.3/)中。

要在Maven项目中使用Uber Jar，请参阅文章[如何使用Uber jar](../sites-developing/ht-projects-maven.md)，并在您的项目POM中包含以下依赖项：

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.3</version>
      <scope>provided</scope>  
</dependency>
```

>[!NOTE]
>
>UberJar和其他相关对象可在Maven Central Repository上使用，而不是AdobePublic Maven存储库(repo.adobe.com)。 主UberJar文件被重命名为`uber-jar-<version>.jar`。 因此，`dependency`标签没有`classifier`（值为`apis`）。

## 已移除/已弃用功能 {#removed-deprecated-features}

此部分列出了 AEM 6.4 中已移除或已弃用的功能和特性。

| 区域 | 功能 | 替换 | 版本 |
|---|---|---|---|
| 资产 | 管理子资产的标签操作 | 无替换项 | AEM 6.4.2.0 |
| 资产和 Creative Cloud 集成 | [AEM到Creative Cloud文件](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) 夹共享在AEM 6.2中引入，以便让创意用户能够访问AEM中的资产。在 Creative Cloud 应用程序中发布的新功能“Adobe 资产链接”提供了更佳的用户体验，能够直接从 Photoshop、InDesign 和 Illustrator 中轻松访问 AEM 资产。Adobe 不会再进一步增强文件夹共享功能。尽管AEM中包含该功能，但会强烈建议客户使用该替换。 | Adobe资产链接或桌面应用程序。 有关更多信息，请参阅 [AEM Creative Cloud 集成](/help/assets/aem-cc-integration-best-practices.md)一文。 | AEM 6.4.4.0 |

## 已知问题 {#known-issues}

* 如果从[!DNL Experience Manager] 6.4升级到[!DNL Experience Manager] 6.5，则某些包可能不显示其状态为`Active`。 安装最新的[!DNL Experience Manager] 6.5 Service Pack以解决此问题。

有关AEM 6.4.8.0 Service Pack已知问题的信息，请参阅《Service Pack发行说明》[ &lt;a0/>AEM 6.4.8.0 &lt;版本>](sp-release-notes.md)。

## 包含的 OSGi 包和内容包 {#osgi-bundles-and-content-packages-included}

以下文本文档列出了 AEM 6.4.8.3 中包含的 OSGi 包和内容包.

AEM 6.4.8.3 中包含的 OSGi 包列表

[获取文件](assets/6.4.8.3_osgi_bundles.txt)

AEM 6.4.8.3 中包含的内容包列表

[获取文件](assets/6.4.8.3_content_packages.txt)

## 有用资源 {#helpful-resources}

* [AEM 6.4 发行说明](../release-notes/release-notes.md)
* [AEM 产品页面](https://www.adobe.com/solutions/web-experience-management.html)
* [AEM 6.4 文档](https://helpx.adobe.com/cn/support/experience-manager/6-4.html)
* 订阅[Adobe优先级产品更新](https://www.adobe.com/subscription/priority-product-update.html)

## 受限的网站 {#restricted-sites-new}

这些网站仅适用于客户。如果您是客户并且需要访问，请联系您的 Adobe 客户经理。

* [产品下载：licensing.adobe.com](https://licensing.adobe.com/)
* [联系客户支持](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
