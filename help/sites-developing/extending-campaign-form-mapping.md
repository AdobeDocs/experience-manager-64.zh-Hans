---
title: 创建自定义表单映射
seo-title: Creating Custom Form Mappings
description: 在Adobe Campaign中创建自定义表时，您可能希望在AEM中构建一个映射到该自定义表的表单
seo-description: When you create a custom table in Adobe Campaign, you may want to build a form in AEM that maps to that custom table
uuid: f3bde513-6edb-4eb6-9048-40045ee08c4a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: d5dac1db-2dde-4b75-a31b-e057b447f6e2
exl-id: 3270a279-13ef-4bbf-aafe-539df388c652
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 1%

---

# 创建自定义表单映射{#creating-custom-form-mappings}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在Adobe Campaign中创建自定义表时，您可能希望在AEM中构建一个映射到该自定义表的表单。

本文档介绍如何创建自定义表单映射。 完成本文档中的步骤后，您将为用户提供一个事件页面，用户可在该页面注册即将发生的事件。 然后，通过Adobe Campaign跟踪这些用户。

## 前提条件 {#prerequisites}

您需要安装以下组件：

* Adobe Experience Manager
* Adobe Campaign Classic

请参阅 [将AEM与Adobe Campaign Classic集成](/help/sites-administering/campaignonpremise.md) 以了解更多信息。

## 创建自定义表单映射 {#creating-custom-form-mappings-2}

要创建自定义表单映射，您需要遵循以下高级步骤，有关这些步骤的详细说明，请参阅以下章节：

1. 创建自定义表。
1. 扩展 **种子** 表。
1. 创建自定义映射。
1. 基于自定义映射创建投放。
1. 在AEM中构建表单，该表单将使用创建的投放。
1. 提交表单以进行测试。

### 在Adobe Campaign中创建自定义表 {#creating-the-custom-table-in-adobe-campaign}

首先在Adobe Campaign中创建自定义表。 在本例中，我们使用以下定义来创建事件表：

```xml
<element autopk="true" label="Event" labelSingular="Event" name="event">
 <attribute label="Event Date" name="eventdate" type="date"/>
 <attribute label="Event Name" name="eventname" type="string"/>
 <attribute label="Email" name="email" type="string"/>
 <attribute label="Number of Seats" name="seats" type="long"/>
</element>
```

创建事件表后，运行 **更新数据库结构向导** 创建表。

### 扩展种子表 {#extending-the-seed-table}

在Adobe Campaign中，点按/单击 **添加** 创建的新扩展 **种子地址(nms)** 表。

![chlimage_1-194](assets/chlimage_1-194.png)

现在，使用 **事件** 表以扩展 **种子** 表：

```xml
<element label="Event" name="custom_cus_event">
 <attribute name="eventname" template="cus:event:event/@eventname"/>
 <attribute name="eventdate" template="cus:event:event/@eventdate"/>
 <attribute name="email" template="cus:event:event/@email"/>
 <attribute name="seats" template="cus:event:event/@seats"/>
 </element>
```

之后，运行 **更新数据库向导** 以应用更改。

### 创建自定义目标映射 {#creating-custom-target-mapping}

在 **管理/营销活动管理** t，转到 **目标映射** 并添加新T **目标映射。**

>[!NOTE]
>
>确保为 **内部名称**.

![chlimage_1-195](assets/chlimage_1-195.png)

### 创建自定义投放模板 {#creating-a-custom-delivery-template}

在此步骤中，您将添加一个使用创建的 **目标映射**.

在 **资源/模板**，导航到投放模板并复制现有AEM投放。 单击 **至**，选择创建事件 **目标映射**.

![chlimage_1-196](assets/chlimage_1-196.png)

### 在AEM中构建表单 {#building-the-form-in-aem}

在AEM中，确保已在 **页面属性**.

然后，在 **Adobe Campaign** 选项卡，选择在中创建的投放 [创建自定义投放模板](#creating-a-custom-delivery-template).

![chlimage_1-197](assets/chlimage_1-197.png)

配置字段时，请确保为表单字段指定唯一的元素名称。

配置字段后，您需要手动更改映射。

在CRXDE-lite中，转到 **jcr:content** （页面的）节点，并更改 **acMapping** 的内部名称 **目标映射**.

![chlimage_1-198](assets/chlimage_1-198.png)

在表单的配置中，确保选中复选框以在不存在时创建

![chlimage_1-199](assets/chlimage_1-199.png)

### 提交表单 {#submitting-the-form}

您现在可以提交表单，并在Adobe Campaign端验证值是否已保存。

![chlimage_1-200](assets/chlimage_1-200.png)

## 疑难解答 {#troubleshooting}

**&quot;元素&#39;@eventdate&#39;中值&#39;02/02/2015&#39;的类型无效(类型为&#39;Event&#39;的文档([adb:event])&#39;)&quot;**

提交表单时，此错误将记录在 **error.log** 在AEM中。

这是由于日期字段的格式无效所致。 解决方法是 **yyyy-mm-dd** 作为值。
