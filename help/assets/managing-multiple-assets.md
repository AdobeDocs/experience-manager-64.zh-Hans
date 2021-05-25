---
title: 批量编辑多个资产和收藏集的元数据
description: 了解如何同时编辑多个资产和收藏集的元数据，以快速传播常见的元数据更改。
contentOwner: AG
feature: 资产管理，元数据，收藏集
role: Business Practitioner
exl-id: 3541b50a-f226-4a6a-9c2a-03a5f47f1c23
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 18%

---

# 管理多个资产和收藏集{#managing-multiple-assets-and-collections}

了解如何同时编辑多个资产和收藏集的元数据，以快速传播常见的元数据更改。

AdobeEnterprise Manager(AEM)Assets允许您同时编辑多个资产的元数据，以便您能够快速将常见的元数据更改批量传播到资产。 您还可以批量编辑多个收藏集的元数据。

使用属性页面对多个资产或收藏集执行元数据更改：

* 将元数据属性更改为通用值
* 添加或修改标记

要自定义元数据属性页面（包括添加、修改、删除元数据属性），请使用架构编辑器。

>[!NOTE]
>
>批量编辑方法适用于文件夹或收藏集中的可用资产。 对于跨文件夹提供的资产或符合通用标准的资产，可以从资产搜索结果中批量更新元数据。

## 编辑多个资产的元数据属性{#editing-metadata-properties-of-multiple-assets}

1. 在Assets用户界面中，导航到要编辑的资产所在的位置。
1. 选择要编辑其通用属性的资产。
1. 在工具栏中，单击&#x200B;**[!UICONTROL 属性]** ，以打开选定资产的属性页面。
1. 在各种选项卡下修改选定资产的元数据属性。
1. 要查看特定资产的元数据，请取消在列表中选择的其余资产。 如果您在[!UICONTROL 属性]页面上取消选择一些资产，则不会更新此类资产的元数据。
1. 要为资产选择其他元数据架构，请单击工具栏中的&#x200B;**[!UICONTROL 设置]** ，然后选择一个架构。 单击&#x200B;**[!UICONTROL 保存并关闭]**。
1. 要将新元数据与现有元数据追加到包含多个值的字段中，请选择&#x200B;**[!UICONTROL 追加模式]**。如果不选中此选项，则新元数据将替换字段中的现有元数据。单击&#x200B;**[!UICONTROL Submit]**。

![元数据架构批量应用于多个资产](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>对于单值字段，即使选择&#x200B;**[!UICONTROL 追加模式]**，新元数据也不会追加到字段中的现有值中。

## 配置批量元数据更新限制{#configure-limit-for-bulk-metadata-update}

为防止出现类似DOS的情况，AEM会限制Sling请求中支持的参数数量。 一次更新多个资产的元数据时，您可能会达到限制，并且不会为更多资产更新元数据。 AEM在日志中生成以下警告：

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

要更改限制，请访问&#x200B;**[!UICONTROL 工具>操作> Web Console]**，并更改[!UICONTROL Apache Sling请求参数处理] OSGi配置中的[!UICONTROL 最大POST参数]值。

>[!MORELIKETHIS]
>
>* [批量编辑多个收藏集的元数据](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

