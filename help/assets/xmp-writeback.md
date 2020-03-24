---
title: XMP 写回到演绎版
description: 了解XMP写回功能如何将资产的元数据更改传播到资产的所有或特定演绎版。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5ef4c4e42165819191c6e3810c36183110f3f34a

---


# XMP 写回到演绎版 {#xmp-writeback-to-renditions}

Adobe Experience Manager(AEM)资产中的此XMP写回功能可将资产元数据更改复制到资产的演绎版。

当您从AEM资产中更改资产的元数据或在上传资产时，更改最初会存储在Crx-De中的资产节点中。

XMP写回功能将元数据更改传播到资产的所有或特定演绎版。

请考虑将资产标题的 [!UICONTROL 标题] 属性修改为的 `Classic Leather` 场景 `Nylon`。

![元数据](assets/metadata.png)

In this case, the AEM Assets saves the changes to the **[!UICONTROL Title]** property in the `dc:title` parameter for the asset metadata stored in the asset hierarchy.

![metadata_stored](assets/metadata_stored.png)

但是，AEM资产不会自动将任何元数据更改传播到资产的演绎版。

XMP写回功能允许您将元数据更改传播到资产的所有或特定演绎版。 但是，这些更改不会存储在资产层次结构中的元数据节点下。此功能而是会将更改嵌入到演绎版的二进制文件中。

## 启用XMP写回 {#enabling-xmp-writeback}

要在上传元数据更改时将其传播到资产的演绎版，请在配置管理器中修改 **Adobe CQ DAM Rendition Maker** 配置。

1. 从中打开配置管理 `https://[aem_server]:[port]/system/console/configMgr`器。
1. 打开 **[!UICONTROL Adobe CQ DAM Rendition Maker配置]** 。
1. 选择“ **[!UICONTROL 传播XMP]** ”选项，然后保存更改。

   ![chlimage_1-346](assets/chlimage_1-346.png)

## 为特定再现启用XMP写回 {#enabling-xmp-writeback-for-specific-renditions}

要让XMP写回功能将元数据更改传播到选定的演绎版，请将这些演绎版指定到DAM元数据写回工作流的XMP写回流程工作流步骤。 默认情况下，此步骤配置有原始再现。

要使XMP写回功能将元数据传播到再现缩略图140.100.png和319.319.png，请执行这些步骤。

1. 在Experience Manager中，导航到工 **[!UICONTROL 具>工作流>模型]**。
1. 从“模 [!UICONTROL 型] ”页面，打开 **[!UICONTROL DAM元数据写回工作流模型]** 。
1. 在“ **[!UICONTROL DAM元数据写回]** ”属性页中，打开“ **[!UICONTROL XMP写回进程”步骤]** 。
1. 在&#x200B;**[!UICONTROL 步骤属性]**&#x200B;对话框中，点按/单击&#x200B;**[!UICONTROL 流程]**&#x200B;选项卡。
1. 在“参 **[!UICONTROL 数]** ”框中，添加 `rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`。 Tap/click **[!UICONTROL OK]**.

   ![step_properties](assets/step_properties.png)

1. To regenerate the pyramid TIFF renditions for Dynamic Media images with the new attributes, add the **[!UICONTROL Dynamic Media Process Image Assets]** step to the DAM Metadata Writeback workflow.
PTIFF演绎版仅在Dynamic Media Hybrid模式下创建并存储在本地。 保存工作流。

元数据更改将传播到资产的演 `thumbnail.140.100.png` 绎版 `thumbnail.319.319.png` 和演绎版，而不是其他演绎版。

>[!NOTE]
>
>有关64位Linux中的XMP写回问题，请参 [阅如何在64位RedHat Linux上启用XMP写回](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)。
>
>有关支持的平台的详细信息，请参 [阅XMP元数据回写的先决条件](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back)。

## 过滤XMP元数据 {#filtering-xmp-metadata}

AEM资产支持对从资产二进制文件读取的、在摄取资产时存储在JCR中的XMP元数据的属性／节点进行黑名单和白名单过滤。

黑名单过滤允许您导入除为排除而指定的属性外的所有XMP元数据属性。 但是，对于具有大量XMP元数据（例如，1000个节点具有10,000个属性）的资产类型（如INDD文件），要筛选的节点名称并不总是预先知道的。 如果黑名单过滤允许导入大量具有大量XMP元数据的资产，则AEM实例／群集可能会遇到稳定性问题，例如，阻塞的观察队列。

XMP元数据的白名单过滤功能可通过允许您定义要导入的XMP属性来解决此问题。 这样，将忽略其他／未知的XMP属性。 您可以将其中一些属性添加到黑名单过滤器，以实现向后兼容性。

>[!NOTE]
>
>筛选仅适用于从资产二进制文件中的XMP源派生的属性。 对于从非XMP源（如EXIF和IPTC格式）派生的属性，过滤不起作用。 例如，资产创建日期存储在以EXIF TIFF命名的 `CreateDate` 属性中。 AEM在名为的元数据字段中讲述此值 `exif:DateTimeOriginal`。 由于源是非XMP源，因此过滤不适用于此属性。

1. 从中打开配置管理 `https://[aem_server]:[port]/system/console/configMgr`器。
1. 打开 **[!UICONTROL Adobe CQ DAM XmpFilter配置]** 。
1. 要应用白名单过滤，请选择&#x200B;**[!UICONTROL 将白名单应用于 XMP 属性]**，然后在 **[!UICONTROL XMP 过滤的列入白名单的 XML 名称]**&#x200B;框中指定要导入的属性。

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. 要在应用白名单过滤后过滤掉列入黑名单的 XMP 属性，请在 **[!UICONTROL XMP 过滤的列入黑名单的 XML 名称]**&#x200B;框中指定。保存更改。

   >[!NOTE]
   >
   >默认 **[!UICONTROL 情况下，“将黑名单应用到XMP属性]** ”选项处于选中状态。 换句话说，黑名单过滤默认为启用状态。 要禁用黑名单过滤，请取消选 **[!UICONTROL 择“将黑名单应用到XMP属性”]**。
