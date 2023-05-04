---
title: 创建和分配启用资源
seo-title: Create and Assign Enablement Resources
description: 添加启用资源
seo-description: Add enablement resources
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
exl-id: 9f447a54-4512-41ab-b8d3-327e751eda58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 2%

---

# 创建和分配启用资源 {#create-and-assign-enablement-resources}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 添加启用资源 {#add-an-enablement-resource}

要向新社区站点添加支持资源，请执行以下操作：

* 在创作实例上
   * 例如， [http://localhost:4502/](http://localhost:4503/)
* 以系统管理员身份登录
* 从全局导航中，选择 **社区> [资源](resources.md)**

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* 选择要向其添加支持资源的社区站点
   * 选择 `Enablement Tutorial`
* 从菜单中，选择 ` Create`
* 选择 **[!UICONTROL 资源]**

![chlimage_1-201](assets/chlimage_1-201.png)

### 基本信息 {#basic-info}

填写资源的基本信息：

* **[!UICONTROL 网站名称]**:设置为选定社区站点的名称：启用教程
* **[!UICONTROL 资源名称(&amp;A);]**:滑雪课程1
* **[!UICONTROL 标记]**:教程：体育/滑雪
* **[!UICONTROL 在目录中显示]**:开
* **[!UICONTROL 描述]**:初学者在雪上滑动
* **[!UICONTROL 添加图像]**:向其“分配”视图中的成员添加表示资源的图像
   ![chlimage_1-202](assets/chlimage_1-202.png)
* 选择 **[!UICONTROL 下一个]**

### 添加内容 {#add-content}

虽然它看起来好像可以选择多个资源，但只允许一个资源。

选择 `'+' icon`，以通过标识源来开始选择资源的过程。

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

上传资源。 如果视频资源，请上传自定义图像以在视频开始播放之前显示，或者允许从视频生成缩略图（可能需要几分钟 — 无需等待）。

![chlimage_1-205](assets/chlimage_1-205.png)

* 选择 **[!UICONTROL 下一个]**

### 设置 {#settings}

* **[!UICONTROL 社交设置]**
保留默认设置，以便学习者对支持资源的体验进行评论和评级。
* **[!UICONTROL 到期日期]**

   *（可选）* 可以选择应完成分配的日期。
* **[!UICONTROL 资源作者]**

   *（可选）* 留空。
* **[!UICONTROL 资源联系人(&amp;A);]**

   *（必需）* 使用下拉菜单选择成员 `Quinn Harper`.
* **[!UICONTROL 资源专家]**

   *（可选）* 留空。
   **注意**:如果用户或组不可见，请检查是否已将其添加到 `Community Enable Members` 本集团及 *已保存* 在发布实例上。
   ![chlimage_1-206](assets/chlimage_1-206.png)
* 选择 **[!UICONTROL 下一个]**

### 指定任务 {#assignments}

* **[!UICONTROL 添加受分配人]**
保持未设置状态，因为此启用资源将添加到学习路径中。 如果将学习者分配到单个启用资源以及包含启用资源的学习路径，则会将学习者分配到启用资源两次。

![chlimage_1-207](assets/chlimage_1-207.png)

* 选择 **[!UICONTROL 创建]**

![chlimage_1-208](assets/chlimage_1-208.png)

成功创建资源会返回到资源控制台，并选择新创建的资源。 在此控制台中，可以发布、添加学习者并更改其他设置。

要上传启用资源的新版本，建议创建新资源，然后从旧版本中取消注册成员，并将他们注册到新版本中。

### 发布资源 {#publish-the-resource}

在登记者能够查看分配的资源之前，必须先发布该资源：

* 选择世界 `Publish`图标

成功消息确认激活：

![chlimage_1-209](assets/chlimage_1-209.png)

## 添加第二个启用资源 {#add-a-second-enablement-resource}

重复上述步骤以创建并发布第二个相关的支持资源，以从中创建学习路径。

![chlimage_1-210](assets/chlimage_1-210.png)

**发布** 第二个资源。

返回其资源的启用教程列表。

*提示：如果两个资源都不可见，请刷新页面。*

![chlimage_1-211](assets/chlimage_1-211.png)

## 添加学习路径 {#add-a-learning-path}

学习路径是构成课程的支持资源的逻辑分组。

* 从资源控制台中，选择 `+ Create`
* 选择 **[!UICONTROL 学习路径]**

![chlimage_1-212](assets/chlimage_1-212.png)

添加 **[!UICONTROL 基本信息]**:

* **[!UICONTROL 学习路径名称]**:滑雪课
* **[!UICONTROL 标记]**:教程：滑雪
* **[!UICONTROL 在目录中显示]**:未选中
* **[!UICONTROL 上传图像]** 在“资源”控制台中表示学习路径

![chlimage_1-213](assets/chlimage_1-213.png)

* 选择 **[!UICONTROL 下一个]**

跳过下一个面板，因为没有要添加的先决学习路径。

* 选择 **[!UICONTROL 下一个]**

在“添加资源”面板上

* 选择 `+ Add Resources` 选择要添加到学习路径中的2个滑雪课程资源

   注意：仅 **发布** 资源将可供选择。

>[!NOTE]
>
>您只能选择与学习路径处于同一级别的可用资源。 例如，对于在组中创建的学习路径，只有组级别资源可用；对于在社区站点中创建的学习路径，该站点中的资源可用于添加到学习路径中。

* 选择 **[!UICONTROL 提交]**.

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* 选择 **[!UICONTROL 下一个]**

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL 添加受分配人]**
使用下拉菜单选择 
`Community Ski Class` 组，其中应包括成员 `Riley Taylor` 和 `Sidney Croft.`

* **[!UICONTROL 学习路径联系方式(&amp;A);]**

   *（必需）* 使用下拉菜单选择成员 `Quinn Harper`.

* 选择 **[!UICONTROL 创建]**

![chlimage_1-217](assets/chlimage_1-217.png)

成功创建学习路径会返回到“资源”控制台，并选择新创建的学习路径。 在此控制台中，可以发布、添加学习者并更改其他设置。

**发布** 学习之路。
