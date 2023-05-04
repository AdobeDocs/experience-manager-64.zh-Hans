---
title: AEM 6.4中的已知问题
seo-title: Known Issues in AEM 6.4
description: Adobe Experience Manager 6.4中的已知问题
seo-description: Known Issues in Adobe Experience Manager 6.4.
uuid: 1733f15e-9c4f-4db3-98ee-25c2ea606f0d
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 266634ab-21d3-4aac-acfa-b799a7485507
exl-id: ba65e853-d69a-4341-93c3-5628c60c403b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 6%

---

# 已知问题 {#known-issues}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本页保留了2018年4月发布的Adobe Experience Manager 6.4已知问题列表。 有关已知问题的更多信息，请 [联系支持](https://helpx.adobe.com/cn/support/experience-manager.html).

## 混合设备 {#hybrid-devices}

不支持混合设备。 使用此类设备时可能会遇到各种问题。 以下建议的过程有助于解决许多问题：

如果您使用Google Chrome作为浏览器：

* 类型 `chrome://flags/` 在地址栏中按Enter。
* 单击启用触屏事件>禁用。
* 重新启动浏览器（所有选项卡和窗口）。

如果您将Mozilla Firefox用作浏览器：

* 类型 `about:config` 在地址栏中按Enter。
* 将设置过滤到 `dom.w3c`.
* 确保设置为 `0` 和 `false`.
* 重新启动浏览器。

如果您使用Microsoft Edge作为浏览器：

* 类型 `about:flags` 在地址栏中，按回车键。
* 然后滚动到实验功能 **[!UICONTROL 触控]**.
* 单击 **[!UICONTROL 启用触屏事件]**.
* 选择 **[!UICONTROL 始终关闭]**.
* 重新启动浏览器。

## Platform {#platform}

* **操作功能板：** 备份文件缺少.zip扩展名时，不显示进度条。 (GRANITE-10713)
* **HTL:** 包声明中带有尾随空格的Java Use对象冻结SightlyJavaCompilerService(GRANITE-20836)
* **Apache Felix/Sling:** 即使在configuration.delete()之后，配置文件仍然存在于存储库中(GRANITE-20618)
* **云设置：** 编辑配置容器后，控制台损坏(GRANITE-20726)
* **安全性：** IMS集成因自定义上下文路径而失败(GRANITE-20639)
* **安全性：** 改进SSO、外部和默认登录模块的默认JAAS排名(GRANITE-20590)
* **工具 — CRX DE Lite:** 属性视图的脊部不断上移(GRANITE-12040)
* **工具 — CRX DE Lite:** 除非双击属性名称，否则无法保存对“长”值类型所做的更改(GRANITE-12351)

* **工具 — CRX DE Lite:** 对打开的文本文件执行ctrl+F搜索时，正则表达式搜索会卡住(GRANITE-5996)

* **工具 — CRX DE Lite:** 重命名节点后，不显示节点属性(GRANITE-7160)
* **UI:** 下拉“更多……” 在IE和Firefox上的弹出窗口元素处打开时，不会显示所有元素(GRANITE-16326)
* **UI:** 当使用带有2个并排列的固定列布局时，信息工具提示会隐藏(GRANITE-16869)
* **UI:** 模拟为不存在的用户时出现未处理的错误(GRANITE-23228)。 解决方法 [实施错误处理程序](/help/sites-developing/customizing-errorhandler-pages.md) 自定义错误消息。

* **Omnisearch:** 使用反斜杠进行搜索时出现异常(GRANITE-11769)
* **Omnisearch:** 在列表视图中打开“视图设置”会导致搜索过滤器发生更改(GRANITE-16524)
* **Omnisearch:** 从站点中搜索资产时，显示错误的列配置列表(GRANITE-16527)

* **Omnisearch:** 左边栏谓词与Omnisearch服务器请求一起获取(GRANITE-20524)
* **Omnisearch:** Omnisearch不支持上下文路径(GRANITE-16044)

## Assets {#assets}

* **搜索**:如果搜索字符串以空格开头，则搜索不返回任何结果 [OAK-4786](https://issues.apache.org/jira/browse/OAK-4786)

* **搜索**:在经典UI中，标记在搜索中不可见(CQ-4235239)

* **UI**:复制粘贴和全选后，资产UI变得无响应(CQ-4236142)

* **UI**:延迟加载后无法移动资产(CQ-4236134)

* **报表**:创建资产修改报表时出错(CQ-4239744)

* **报表**:计划的常规资产报表生成失败，显示不一致（某些报表仍排队）(CQ-4239089)

* **元数据**:向资产架构添加多值文本字段时，必填字段级联规则不起作用(CQ-4239333)

* **BrandPortal**:发布到BrandPortal对收藏集不起作用(CQ-4238731)

* **上传**:在上传文件名中包含特殊字符的资产时，不会为每个资产显示有关不允许使用的字符的验证错误消息。 虽然它仅为第一个资产显示，但界面会明确向用户指示不允许使用提供资产的文件名。 (CQ-4256876)

## 社区 {#communities}

* **审核**  — 无法从批量审核UI中将父帖子作为单次删除操作进行删除(CQ-4236797)

* **控制台**  — 忘记用户名或密码链接正在重定向到登录页面，而不是相应的密码检索表单(CQ-4237682)

## Forms {#forms}

### 安装和部署

* (仅限AEM Forms JEE)运行配置管理器时引导JBoss应用程序服务器时，会返回EJB调用和引导失败错误。 但是，您可以忽略它们。 (Ref# CQ-4229793)
* 启动AEM Forms时， `SAX Security Manager could not be setup` 出现警告。 (CQ-4297403)

### 交互式通信

* 代理UI需要一段时间才能加载包含图表或图像元素的交互式通信。 (CQ-4236630)
* 打印预览中的数据显示格式为dd-mm-yyyy，而Web预览中的数据显示格式为 `dd-mmm-yy` (CQ-4237045)
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

### Acrobat Sign集成

* Acrobat Sign计划程序间歇性停止工作，因此表单待处理符号不会移至提交。 要解决此问题，请重新启动 **Apache Sling调度程序支持** 从AEM web控制台中捆绑到https://[*服务器*]:[*端口*]/system/console/bundles。

### 自适应Forms创作

* 自适应表单中的图表组件占用的空间比通常多。
* 在Forms Manager UI中保存自适应表单、自适应表单片段或交互式通信的属性时，会返回异常。
* Android 6.0 Samsung设备上不接受自适应表单文本框指定的最大字符数。 (Ref# CQ-4235205)
* 在从 Apple iOS 设备提交包含标准 HTML 上传字段的表单时，有时不会发送文件内容，而在另一端会收到一个 0 字节的文件。Apple iOS 15.1 修复了此问题。

