---
title: XMP写回到演绎版
description: 了解XMP写回功能如何将资产的元数据更改传播到资产的所有或特定演绎版。
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 456f8c91-aacf-4db5-a329-2d1650ff0f2f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '811'
ht-degree: 4%

---

# XMP写回到演绎版 {#xmp-writeback-to-renditions}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

此XMP写回功能位于 [!DNL Adobe Experience Manager Assets] 会将元数据更改复制到原始资产的演绎版。 当您从资产内更改资产的元数据或在上传资产时，所做的更改最初存储在资产层次结构的元数据节点中。

XMP写回功能允许您将元数据更改传播到资产的所有演绎版或特定演绎版。 该功能仅会回写那些使用 `jcr` namespace，即名为的属性 `dc:title` 被写回，但名为 `mytitle` 不是。

假设您在 [!UICONTROL 标题] 资产的属性 `Classic Leather` to `Nylon`.

![元数据](assets/metadata.png)

在本例中， [!DNL Experience Manager] 资产会将所做的更改保存到 **[!UICONTROL 标题]** 属性 `dc:title` 资产层次结构中存储的资产元数据的参数。

![metadata_stored](assets/metadata_stored.png)

但是， [!DNL Experience Manager Assets] 不会自动将任何元数据更改传播到资产的演绎版。 请参阅 [如何启用XMP写回](#enabling-xmp-writeback).

## 启用XMP写回 {#enabling-xmp-writeback}

要在上传资产时，允许将元数据更改传播到资产的演绎版，请修改 **Adobe CQ DAM演绎版制作器** 配置。

1. 从中打开配置管理器 `https://[aem_server]:[port]/system/console/configMgr`.
1. 打开 **[!UICONTROL Adobe CQ DAM演绎版制作器]** 配置。
1. 选择 **[!UICONTROL 传播XMP]** ，然后保存更改。

   ![chlimage_1-346](assets/chlimage_1-346.png)

## 为特定呈现版本启用XMP写回 {#enabling-xmp-writeback-for-specific-renditions}

要让XMP写回功能将元数据更改传播到选定的演绎版，请将这些演绎版指定到DAM元数据写回工作流的XMP写回流程工作流步骤。 默认情况下，此步骤配置为原始演绎版。

要使XMP写回功能将元数据传播到演绎版缩略图140.100.png和319.319.png，请执行这些步骤。

1. 在Experience Manager中，导航到 **[!UICONTROL 工具>工作流>模型]**.
1. 从 [!UICONTROL 模型] 页面，打开 **[!UICONTROL DAM元数据写回]** 工作流模型。
1. 在“ **[!UICONTROL DAM元数据写回]** ”属性页中，打开“ **[!UICONTROL XMP写回进程”步骤]** 。
1. 在&#x200B;**[!UICONTROL 步骤属性]**&#x200B;对话框中，点按/单击&#x200B;**[!UICONTROL 流程]**&#x200B;选项卡。
1. 在 **[!UICONTROL 参数]** 框，添加 `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`. 点按/单击 **[!UICONTROL 确定]**.

   ![step_properties](assets/step_properties.png)

1. 要使用新属性为Dynamic Media图像重新生成金字塔TIFF呈现，请将 **[!UICONTROL Dynamic Media处理图像资产]** 步骤到DAM元数据写回工作流。
PTIFF呈现仅在Dynamic Media混合模式下本地创建和存储。 保存工作流。

元数据更改会传播到演绎版 `thumbnail.140.100.png` 和 `thumbnail.319.319.png` 而不是其他资产。

>[!NOTE]
>
>有关64位Linux中的XMP写回问题，请参阅 [如何在64位RedHat Linux上启用XMP回写](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).
>
>有关受支持平台的更多信息，请参阅 [XMP元数据回写先决条件](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back).

## 过滤XMP元数据 {#filtering-xmp-metadata}

[!DNL Experience Manager Assets] 支持对XMP元数据的属性/节点进行阻止列表和允许列表筛选，这些属性/节点从资产二进制文件中读取，并在摄取资产时存储在JCR中。

通过使用阻止列表进行筛选，您可以导入所有XMP元数据属性，但指定用于排除的属性除外。 但是，对于具有大量XMP元数据的资产类型（例如，1000个节点，其属性为10,000），要筛选的节点名称并不总是预先知道。 如果使用阻止列表进行筛选时允许导入大量具有大量XMP元数据的资产，则 [!DNL Experience Manager] 实例或群集可能会遇到稳定性问题，例如观察队列阻塞。

通过允许列表过滤XMP元数据可通过允许您定义要导入的XMP属性来解决此问题。 这样，任何其他或未知的XMP属性都将被忽略。 为了向后兼容，您可以将其中某些属性添加到使用阻止列表的过滤器中。

>[!NOTE]
>
>筛选仅适用于资产二进制文件中从XMP源派生的属性。 对于从非XMP源（如EXIF和IPTC格式）派生的属性，筛选不起作用。 例如，资产创建日期存储在名为的属性中 `CreateDate` 在EXIFTIFF中。 [!DNL Experience Manager] 将此值存储在名为 `exif:DateTimeOriginal`. 由于源是非XMP源，因此无法对此属性进行筛选。

1. 从中打开配置管理器 `https://[aem_server]:[port]/system/console/configMgr`.
1. 打开 **[!UICONTROL Adobe CQ DAM XmpFilter]** 配置。
1. 要通过允许列表应用过滤，请选择 **[!UICONTROL 将“允许列表”应用于XMP属性]**，并指定要在 **[!UICONTROL 允许的XML名称以进行XMP筛选]** 框中。

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. 要在通过允许列表应用过滤后过滤掉阻止的XMP属性，请在 **[!UICONTROL 用于XMP筛选的阻止的XML名称]** 框中。 保存更改。

   >[!NOTE]
   >
   >的 **[!UICONTROL 将“阻止列表”应用于XMP属性]** 选项。 换言之，默认情况下会启用使用阻止列表进行过滤。 要禁用此类过滤，请取消选择 **[!UICONTROL 将“阻止列表”应用于XMP属性]** 选项。
