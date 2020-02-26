---
title: AEM 6.4中的已知问题
seo-title: AEM 6.4中的已知问题
description: Adobe Experience Manager 6.4中的已知问题
seo-description: Adobe Experience Manager 6.4中的已知问题。
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
translation-type: tm+mt
source-git-commit: 9b6c1efe1f6281892648c7b41820856d2e3fcac1

---


# 已知问题 {#known-issues}

本页列出了Adobe Experience Manager 6.4在2018年4月发布的已知问题。 有关已知问题的更多信息，请与支 [持部门联系](https://helpx.adobe.com/support/experience-manager.html)。

## 混合设备 {#hybrid-devices}

不支持混合设备。 使用此类设备时可能会遇到各种问题。 以下建议的过程有助于解决许多问题：

如果您使用Google Chrome作为浏览器：
* 在地 `chrome://flags/` 址栏中键入，然后按Enter。
* 单击“启用触控事件”>“禁用”。
* 重新启动浏览器（所有选项卡和窗口）。

如果您使用Mozilla Firefox作为浏览器：
* 在地 `about:config` 址栏中键入，然后按Enter。
* 将设置筛选为 `dom.w3c`。
* 确保设置为 `0` 和 `false`。
* 重新启动浏览器。

如果您使用Microsoft edge作为浏览器：

* 在地 `about:flags` 址栏中键入，然后按回车键。
* 滚动到实验功能，然后 **[!UICONTROL 选择Touch]**。
* 单击“ **[!UICONTROL 启用触控事件]**”。
* 选择“ **[!UICONTROL 始终关闭]**”。
* 重新启动浏览器。

## 平台 {#platform}

* **** 操作控制板：当备份文件缺少。zip扩展名时，不显示进度栏。 (GRANITE-10713)
* **** HTL:包声明中带有尾随空白的Java Use对象冻结SightlyJavaCompilerService(GRANITE-20836)
* **** Apache Felix/Sling:即使在configuration.delete()之后，配置文件仍在存储库中存在(GRANITE-20618)
* **** 云设置：在编辑配置容器后，控制台会损坏(GRANITE-20726)
* **** 安全性：IMS与自定义上下文路径的集成失败(GRANITE-20639)
* **** 安全性：改进SSO、外部和默认登录模块的默认JAAS排名(GRANITE-20590)
* **** 工具集- CRX DE Lite:“属性脊”视图不断上升(GRANITE-12040)
* **** 工具集- CRX DE Lite:除非双击“属性名称”(GRANITE-12351)，否则无法保存对“长”值类型所做的更改

* **** 工具集- CRX DE Lite:ctrl+F在打开的文本文件上搜索会在RegExp搜索中卡住(GRANITE-5996)

* **** 工具集- CRX DE Lite:重命名节点后不显示节点属性(GRANITE-7160)
* **** UI:Pulldown &quot;更多……&quot; 在IE和Firefox上的快显元素处打开时不显示所有元素(GRANITE-16326)
* **** UI:当使用固定列布局并排两列时，信息工具提示会隐藏(GRANITE-16869)
* **** UI:模拟为不存在的用户时出现未处理的错误(GRANITE-23228)。 通过实 [施错误处理程序来自定义错误消息](/help/sites-developing/customizing-errorhandler-pages.md) ，可以采取补救方法。

* **** 全搜索：搜索中出现反斜杠原因异常(GRANITE-11769)
* **** 全搜索：在列表视图中打开“视图设置”会导致搜索筛选器发生更改(GRANITE-16524)
* **** 全搜索：从站点搜索资产时显示的列配置列表错误(GRANITE-16527)

* **** 全搜索：左边栏谓词与Omnisearch服务器请求(GRANITE-20524)相符
* **** 全搜索：Omnisearch不支持上下文路径(GRANITE-16044)

## 资产 {#assets}

* **搜索**:如果搜索字符串以空格 [OAK-4786开头，则搜索不返回任何结果](https://issues.apache.org/jira/browse/OAK-4786)

* **搜索**:在经典UI中，标记在搜索中不可见(CQ-4235239)

* **UI**:在复制粘贴和全选后，资产UI变得无响应(CQ-4236142)

* **UI**:延迟加载后无法移动资产(CQ-4236134)

* **报告**:创建资产修改报告时出错(CQ-4239744)

* **报告**:计划的常规资产报表生成失败（某些报表仍在排队）(CQ-4239089)

* **元数据**:在向资产架构中添加多值文本字段时，必填字段层叠规则不起作用(CQ-4239333)

* **BrandPortal**:发布到BrandPortal无法用于集合(CQ-4238731)

* **上传**:在上传文件名中包含特殊字符的资产时，不会为每个资产显示有关不允许的字符的验证错误消息。 虽然仅为第一个资产显示该文件，但该界面会向用户明确指示不允许使用所提供资产的文件名。 (CQ-4256876)

## 社区 {#communities}

* **协调** -无法从批量协调UI中将父帖子作为单个删除操作删除(CQ-4236797)

* **控制台** -“忘记用户名或密码”链接正重定向到登录页面，而不是相应的密码检索表单(CQ-4237682)

## Forms {#forms}

### 安装和部署

* （仅限AEM Forms JEE）当运行配置管理器时引导JBoss应用程序服务器时，返回EJB调用和引导失败错误。 但是，您可以忽略它们。 (Ref# CQ-4229793)

### 交互式通信

* 代理UI需要一段时间才能加载包含图表或图像元素的交互式通信。 (CQ-4236630)
* 打印预览中的数据显示格式为dd-mm-yyyy，而Web预览中的数据显示格式 `dd-mmm-yy` 为(CQ-4237045)
* 交互通信Web渠道仅支持有序和无序列表。 在列表文档片段中，交互式通信的Web通道不支持复合列表和缩进。 (CQ-4233672)
* 当Web渠道与打印渠道同步时，会发现以下问题：

   * 首次从打印渠道切换时，Web渠道需要一段时间才能同步。
   * 如果打印渠道包含未配置的图表组件，则Web渠道不同步。 要解决此问题，请删除图表组件并再次同步。
   * 同步有时会失败，出现“同步Live Copy时出错”错误。 要解决此问题，请刷新页面。
   * 当表中的第一列是打印渠道模板中的标题列时，布局片段中的静态文本将替换为表单元格名称。
   * 无法在Web渠道通信底部以外的任何位置添加组件或资产。 要将其放在其他位置，请在Web渠道底部添加一个面板，然后使用内容树重新排序。
   * 可以将内容移入Web渠道的继承目标区域，而无需删除Live copy继承。

(CQ-4239780)

### 数据集成

* 基于SOAP的Web服务的身份验证配置不可见，因此无法在云服务中配置。 要解决此问题，请执行以下操作：

   1. 在CRXDE lite控制台中，转到以下节点。\
      /libs/fd/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/items/\
      selectAuthentication/items/custom。
   1. 将value属性的值更新为与text属性的值相同的值。
   1. 单击“全部保存”以保存配置。

(CQ-4238462)

### Adobe sign集成

* Adobe sign计划程序间歇性地停止工作，因此表单待处理的签名不会移至提交。 要解决此问题，请从AEM web控制台(位于https:// **server** :[*port*]/system/console/bundles)重新启动&#x200B;[**] Apache Sling Scheduler Support Bundle。

### 自适应表单创作

* 自适应表单中的图表组件占用的空间比通常占用的空间要多。
* 在Forms Manager UI中保存自适应表单、自适应表单片段或交互式通信的属性时，会返回异常。
* 在 Android 6.0 Samsung 设备上不接受为自适应表单文本框指定的最大字符数。(Ref# CQ-4235205)
