---
title: 批量编辑多个资产和收藏集的元数据
description: 了解如何同时编辑许多资产和收藏集的元数据，以快速传播常见的元数据更改。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 184aa0a7fcd3f89510295ddaff28624b8306b7d2
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 18%

---


# 管理多个资产和收藏集{#managing-multiple-assets-and-collections}

了解如何同时编辑多个资产和收藏集的元数据，以快速传播常见的元数据更改。

Adobe Enterprise Manager(AEM)资产允许您同时编辑多个资产的元数据，以便您可以快速将常见元数据更改批量传播到资产。 您还可以批量编辑多个集合的元数据。

使用“属性”页可以对多个资产或收藏集执行元数据更改：

* 将元数据属性更改为通用值
* 添加或修改标记

要自定义元数据属性页面，包括添加、修改和删除元数据属性，请使用模式编辑器。

>[!NOTE]
>
>批量编辑方法适用于文件夹或收藏集中的可用资产。 对于跨文件夹可用或符合通用标准的资产，可以从资产搜索结果中批量更新元数据。

## 编辑多个资产{#editing-metadata-properties-of-multiple-assets}的元数据属性

1. 在资产用户界面中，导航到要编辑的资产所在的位置。
1. 选择要编辑其通用属性的资产。
1. 在工具栏中，单击&#x200B;**[!UICONTROL 属性]**&#x200B;以打开选定资产的属性页面。
1. 在各种选项卡下修改选定资产的元数据属性。
1. 要视图特定资产的元数据，请在列表中取消选择其余资产。 如果您取消在[!UICONTROL 属性]页面上选择一些资产，则不会更新此类资产的元数据。
1. 要为资产选择其他元数据模式，请单击工具栏中的&#x200B;**[!UICONTROL 设置]**，然后选择模式。 单击&#x200B;**[!UICONTROL 保存并关闭]**。
1. 要将新元数据与现有元数据追加到包含多个值的字段中，请选择&#x200B;**[!UICONTROL 追加模式]**。如果不选中此选项，则新元数据将替换字段中的现有元数据。单击&#x200B;**[!UICONTROL 提交]**。

![元数据模式批量应用于多个资产](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>对于单值字段，即使选择&#x200B;**[!UICONTROL 追加模式]**，新元数据也不会追加到字段中的现有值中。

## 配置元数据批量更新的限制{#configure-limit-for-bulk-metadata-update}

为防止出现类似DOS的情况，AEM限制Sling请求中支持的参数数。 在一次性更新许多资产的元数据时，您可能会达到限制并且不会为更多资产更新元数据。 AEM在日志中生成以下警告：

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

要更改限制，请访问&#x200B;**[!UICONTROL “工具”>“操作”>“Web控制台”]**，并更改[!UICONTROL Apache Sling请求参数处理] OSGi配置中的[!UICONTROL 最大POST参数]值。

>[!MORELIKETHIS]
>
>* [批量编辑多个集合的元数据](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)