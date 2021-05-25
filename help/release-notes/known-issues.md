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
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 4%

---

# 已知问题 {#known-issues}

本页保留了2018年4月发布的Adobe Experience Manager 6.4已知问题列表。 有关已知问题的更多信息，请[联系支持人员](https://helpx.adobe.com/cn/support/experience-manager.html)。

## 混合设备{#hybrid-devices}

不支持混合设备。 使用此类设备时可能会遇到各种问题。 以下建议的过程有助于解决许多问题：

如果您使用Google Chrome作为浏览器：

* 在地址栏中键入`chrome://flags/`，然后按Enter。
* 单击启用触屏事件>禁用。
* 重新启动浏览器（所有选项卡和窗口）。

如果您将Mozilla Firefox用作浏览器：

* 在地址栏中键入`about:config`，然后按Enter。
* 将设置筛选为`dom.w3c`。
* 确保设置为`0`和`false`。
* 重新启动浏览器。

如果您使用Microsoft Edge作为浏览器：

* 在地址栏中键入`about:flags`，然后按返回。
* 滚动到实验功能，然后&#x200B;**[!UICONTROL Touch]**。
* 单击&#x200B;**[!UICONTROL 启用触屏事件]**。
* 选择&#x200B;**[!UICONTROL 始终关闭]**。
* 重新启动浏览器。

## 平台 {#platform}

* **操作功能板：** 当备份文件缺少.zip扩展名时，不显示进度条。(GRANITE-10713)
* **HTL:** 包声明中带有尾随空格的Java Use对象将冻结SightlyJavaCompilerService(GRANITE-20836)
* **Apache Felix/Sling:** 即使在configuration.delete()之后，配置文件仍然存在于存储库中(GRANITE-20618)
* **云设置：** 编辑配置容器后控制台损坏(GRANITE-20726)
* **安全：** IMS集成因自定义上下文路径而失败(GRANITE-20639)
* **安全性：** 改进SSO、外部和默认登录模块的默认JAAS排名(GRANITE-20590)
* **工具 — CRX DE Lite:** 属性脊图视图保持上移(GRANITE-12040)
* **工具 — CRX DE Lite:** 除非双击属性名称，否则无法保存对“长”值类型所做的更改(GRANITE-12351)

* **工具 — CRX DE Lite:** 对打开的文本文件执行ctrl+F搜索时，正则表达式搜索卡住(GRANITE-5996)

* **工具 — CRX DE Lite:** 重命名节点后不显示节点属性(GRANITE-7160)
* **UI:** 下拉菜单“更多……” 在IE和Firefox上的弹出窗口元素处打开时，不会显示所有元素(GRANITE-16326)
* **UI:** 当使用带有2个并排列的固定列布局时，信息工具提示会隐藏(GRANITE-16869)
* **UI:** 模拟为不存在的用户时出现未处理的错误(GRANITE-23228)。[实施错误处理程序](/help/sites-developing/customizing-errorhandler-pages.md)以自定义错误消息的解决方法。

* **Omnisearch:** 搜索反斜线原因异常(GRANITE-11769)
* **Omnisearch:** 在列表视图中打开“视图设置”会导致搜索筛选器发生更改(GRANITE-16524)
* **Omnisearch:** 从站点中搜索资产时显示的列配置列表错误(GRANITE-16527)

* **Omnisearch:** 左边栏谓词与Omnisearch服务器请求一起获取(GRANITE-20524)
* **Omnisearch:** Omnisearch不支持上下文路径(GRANITE-16044)

## 资产 {#assets}

* **搜索**:如果搜索字符串以空格OAK-4786开头，则搜索不会返 [回任何结果](https://issues.apache.org/jira/browse/OAK-4786)

* **搜索**:在经典UI中，标记在搜索中不可见(CQ-4235239)

* **UI**:复制粘贴和全选后，资产UI变得无响应(CQ-4236142)

* **UI**:延迟加载后无法移动资产(CQ-4236134)

* **报表**:创建资产修改报表时出错(CQ-4239744)

* **报表**:计划的常规资产报表生成失败，显示不一致（某些报表仍排队）(CQ-4239089)

* **元数据**:向资产架构添加多值文本字段时，必填字段级联规则不起作用(CQ-4239333)

* **BrandPortal**:发布到BrandPortal对收藏集不起作用(CQ-4238731)

* **上传**:在上传文件名中包含特殊字符的资产时，不会为每个资产显示有关不允许使用的字符的验证错误消息。虽然它仅为第一个资产显示，但界面会明确向用户指示不允许使用提供资产的文件名。 (CQ-4256876)

## 社区 {#communities}

* **审核**  — 无法从批量审核UI中将父帖子作为单次删除操作进行删除(CQ-4236797)

* **控制台**  — 忘记用户名或密码链接正在重定向到登录页面，而不是相应的密码检索表单(CQ-4237682)

## 表单 {#forms}

### 安装和部署

* (仅限AEM Forms JEE)运行配置管理器时引导JBoss应用程序服务器时，会返回EJB调用和引导失败错误。 但是，您可以忽略它们。 (Ref# CQ-4229793)
* 启动AEM Forms时，会显示`SAX Security Manager could not be setup`警告。 (CQ-4297403)

### 交互式通信

* 代理UI需要一段时间才能加载包含图表或图像元素的交互式通信。 (CQ-4236630)
* 打印预览中的数据显示格式为dd-mm-yyyy，而Web预览中的数据显示格式为`dd-mmm-yy`(CQ-4237045)
* 交互式通信Web渠道仅支持已排序和未排序的列表。 在列表文档片段中，交互式通信的Web渠道不支持复合列表和缩进。 (CQ-4233672)
* 当Web渠道与打印渠道同步时，会发现以下问题：

   * 首次从打印渠道切换时，Web渠道需要一段时间才能同步。
   * 如果打印渠道包含未配置的图表组件，则Web渠道不会同步。 要解决此问题，请删除图表组件并再次同步。
   * 同步有时会失败，并出现“同步Live Copy时出错”错误。 要解决此问题，请刷新页面。
   * 当表中的第一列是打印渠道模板中的标题列时，布局片段中的静态文本将替换为表单元格名称。
   * 无法在Web渠道通信底部以外的任何位置添加组件或资产。 要将其放置到其他位置，请在Web渠道的底部添加一个面板，然后使用内容树重新排序。
   * 可以将内容移动到Web渠道的继承目标区域，而无需删除Live Copy继承。

(CQ-4239780)

### 数据集成

* 基于SOAP的Web服务的身份验证配置不可见，因此无法在云服务中配置。 要解决此问题，请执行以下操作：

   1. 在CRXDE Lite控制台中，转到以下节点。\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/container/items/wsdl/items/\
      选择Authentication/items/custom。
   1. 将value属性的值更新为与text属性的值相同。
   1. 单击全部保存以保存配置。

(CQ-4238462)

### Adobe Sign集成

* Adobe Sign计划程序间歇性停止工作，因此表单待处理符号不会移至提交。 要解决此问题，请从AEM Web控制台中重新启动&#x200B;**Apache Sling调度程序支持**&#x200B;包，网址为： https://[*server*]:[*port*]/system/console/bundles。

### 自适应Forms创作

* 自适应表单中的图表组件占用的空间比通常多。
* 在Forms Manager UI中保存自适应表单、自适应表单片段或交互式通信的属性时，会返回异常。
* 在 Android 6.0 Samsung 设备上不接受为自适应表单文本框指定的最大字符数。(Ref# CQ-4235205)
