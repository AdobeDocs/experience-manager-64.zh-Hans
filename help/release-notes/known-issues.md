---
title: AEM 6.4中的已知问题
seo-title: AEM 6.4中的已知问题
description: Adobe Experience Manager6.4中的已知问题
seo-description: Adobe Experience Manager6.4中的已知问题。
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 4%

---


# 已知问题 {#known-issues}

本页保留Adobe Experience Manager6.4在2018年4月发布的一列表已知问题。 有关已知问题的详细信息，请[联系支持部门](https://helpx.adobe.com/cn/support/experience-manager.html)。

## 混合设备{#hybrid-devices}

不支持混合设备。 使用此类设备时可能会遇到各种问题。 以下建议的过程有助于解决许多问题：

如果您使用Google Chrome作为浏览器：

* 在地址栏中键入`chrome://flags/` ，然后按Enter。
* 单击“启用触控事件”>“禁用”。
* 重新启动浏览器（所有选项卡和窗口）。

如果您将Mozilla Firefox用作浏览器：

* 在地址栏中键入`about:config` ，然后按Enter。
* 将设置筛选为`dom.w3c`。
* 确保设置为`0`和`false`。
* 重新启动浏览器。

如果您使用Microsoft Edge作为浏览器：

* 在地址栏中键入`about:flags` ，然后按回车键。
* 滚动到实验功能，然后&#x200B;**[!UICONTROL 触控]**。
* 单击&#x200B;**[!UICONTROL 启用触控事件]**。
* 选择&#x200B;**[!UICONTROL 始终关闭]**。
* 重新启动浏览器。

## 平台 {#platform}

* **操作仪表板** 符：当备份文件缺少。zip扩展名时，不显示进度栏。(GRANITE-10713)
* **HTL：包** 声明中带有尾随空格的Java Use对象冻结SightlyJavaCompilerService(GRANITE-20836)
* **Apache Felix/Sling:Config文** 件仍在存储库中，即使在configuration.delete()(GRANITE-20618)后也是如此
* **云设置：编** 辑配置容器后，控制台将断开(GRANITE-20726)
* **安全性：** IMS集成与自定义上下文路径失败(GRANITE-20639)
* **安全性：** 改进SSO、外部和默认登录模块的默认JAAS排名(GRANITE-20590)
* **工具- CRX DE Lite:** 属性脊视图不断上升(GRANITE-12040)
* **工具- CRX DE Lite:** 除非多次单击属性名称(GRANITE-12351)，否则无法保存对“长”值类型所做的更改

* **工具- CRX DE Lite:** 在打开的文本文件上搜索ctrl+F会在RegExp搜索中卡住(GRANITE-5996)

* **工具- CRX DE Lite：重** 命名节点后不显示节点属性(GRANITE-7160)
* **UI：下** 拉“更多……” 在IE和Firefox上的跨距元素处打开时不显示所有元素(GRANITE-16326)
* **UI：当** 使用固定列布局和2个并排列时，信息工具提示会隐藏(GRANITE-16869)
* **UI：模** 拟为不存在的用户时出现未处理的错误(GRANITE-23228)。[实现错误处理程序](/help/sites-developing/customizing-errorhandler-pages.md)以自定义错误消息的补救方法。

* **Omnisearch:** 搜索中出现反斜杠原因异常(GRANITE-11769)
* **Omnisearch：在** 列表视图中打开“视图设置”会导致搜索筛选器发生更改(GRANITE-16524)
* **Omnisearch：从** 站点进行资产搜索时显示列配置列表错误(GRANITE-16527)

* **Omnisearch:** 左边栏谓词与Omnisearch服务器请求(GRANITE-20524)一起使用
* **Omnisearch:** Omnisearch不支持上下文路径(GRANITE-16044)

## 资产 {#assets}

* **搜索**:如果搜索字符串开始有空格OAK-4786，则搜索不 [会返回任何结果](https://issues.apache.org/jira/browse/OAK-4786)

* **搜索**:在经典UI中，标记在搜索中不可见(CQ-4235239)

* **UI**:在复制粘贴和全选后，资产UI变得不响应(CQ-4236142)

* **UI**:延迟加载后无法移动资产(CQ-4236134)

* **报告**:创建资产修改报告时出错(CQ-4239744)

* **报告**:计划的常规资产报表生成失败不一致（某些报表仍在排队）(CQ-4239089)

* **元数据**:在向资产模式添加多值文本字段时，必填字段级联规则不起作用(CQ-4239333)

* **BrandPortal**:发布到BrandPortal无法用于集合(CQ-4238731)

* **上传**:上传文件名中包含特殊字符的资产时，不会为每个资产显示有关不允许的字符的验证错误消息。虽然仅为第一个资产显示该资产，但该界面会明确向用户指示不允许使用提供的资产的文件名。 (CQ-4256876)

## 社区 {#communities}

* **协调** -无法从批量协调UI中将父帖子作为单个删除操作删除(CQ-4236797)

* **控制台** -忘记用户名或密码链接正在重定向到登录页面，而不是相应的密码检索表单(CQ-4237682)

## 表单 {#forms}

### 安装和部署

* (仅限AEM FormsJEE)当运行配置管理器时引导JBoss应用程序服务器时，返回EJB调用和引导失败错误。 但是，您可以忽略它们。 (Ref# CQ-4229793)
* 启动AEM Forms时，将显示`SAX Security Manager could not be setup`警告。 (CQ-4297403)

### 交互式通信

* 代理UI需要一段时间来加载包含图表或图像元素的交互式通信。 (CQ-4236630)
* 打印预览中的数据显示格式为dd-mm-yyyy，而Web预览中的数据显示格式为`dd-mmm-yy`(CQ-4237045)
* 交互通信Web渠道仅支持有序和无序列表。 在列表文档片段中，交互通信的Web渠道不支持复合列表和缩进。 (CQ-4233672)
* 当Web渠道与打印渠道同步时，会发现以下问题：

   * 首次从打印渠道切换时，Web渠道需要一段时间才能同步。
   * 如果打印渠道包含未配置的图表组件，则Web渠道不会同步。 要解决此问题，请删除图表组件并再次同步。
   * 同步有时会失败，出现“同步Live Copy时出错”错误。 要解决此问题，请刷新页面。
   * 当表中的第一列是打印渠道模板中的标题列时，布局片段中的静态文本将替换为表单元格名称。
   * 无法在Web渠道通信底部以外的任何位置添加组件或资源。 要将其放在其他位置，请在Web渠道底部添加一个面板，然后使用内容树重新排序。
   * 可以将内容移入Web目标的继承渠道区域，而不删除Live Copy继承。

(CQ-4239780)

### 数据集成

* 基于SOAP的Web服务的身份验证配置不可见，因此无法在云服务中配置。 要解决此问题，请执行以下操作：

   1. 在CRXDE Lite控制台中，转到以下节点。\
      /libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices/\
      wsdlauthenticationsettings/items/fixedcolumns/items/容器/items/wsdl/items/\
      selectAuthentication/items/custom。
   1. 将value属性的值更新为与text属性的值相同的值。
   1. 单击“全部保存”以保存配置。

(CQ-4238462)

### Adobe Sign整合

* Adobe Sign调度程序间歇性地停止工作，因此待签名的表单不会移至提交。 要解决此问题，请从AEM web控制台(https://[*server*]:[*port*]/system/console/bundles)重新启动&#x200B;**Apache Sling调度程序支持**&#x200B;捆绑包。

### 自适应Forms创作

* 自适应表单中的图表组件占用的空间比通常占用的空间要多。
* 在Forms管理器UI中保存自适应表单、自适应表单片段或交互式通信的属性时，会返回异常。
* 在 Android 6.0 Samsung 设备上不接受为自适应表单文本框指定的最大字符数。(Ref# CQ-4235205)
