---
title: XMP 写回到演绎版
description: 了解XMP写回功能如何将资产的元数据更改传播到资产的所有或特定演绎版。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 31d652ee04fe75e96f96c9ddc5a6f2c3c64bd630
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 7%

---


# XMP 写回到演绎版 {#xmp-writeback-to-renditions}

Adobe Experience Manager(AEM)资产中的此XMP写回功能可将资产元数据更改复制到资产的演绎版。

当您从AEM Assets内更改资产的元数据或在上传资产时，更改最初存储在Crx-De的资产节点内。

XMP写回功能将元数据更改传播到资产的所有或特定演绎版。

请考虑将标题为`Classic Leather`的资产的[!UICONTROL Title]属性修改为`Nylon`的情况。

![元数据](assets/metadata.png)

在这种情况下，AEM Assets会为资产层次结构中存储的资产元数据在`dc:title`参数中保存对&#x200B;**[!UICONTROL Title]**&#x200B;属性所做的更改。

![metadata_stored](assets/metadata_stored.png)

但是，AEM Assets不会自动将任何元数据更改传播到资产的演绎版。

XMP写回功能允许您将元数据更改传播到资产的所有或特定演绎版。 但是，这些更改不会存储在资产层次结构中的元数据节点下。此功能而是会将更改嵌入到演绎版的二进制文件中。

## 启用XMP写回{#enabling-xmp-writeback}

要在上传元数据更改时将其传播到资产的演绎版，请修改Configuration Manager中的&#x200B;**Adobe CQDAM演绎版制作器**&#x200B;配置。

1. 从`https://[aem_server]:[port]/system/console/configMgr`打开Configuration Manager。
1. 打开&#x200B;**[!UICONTROL Adobe CQDAM再现制造商]**&#x200B;配置。
1. 选择&#x200B;**[!UICONTROL 传播XMP]**&#x200B;选项，然后保存更改。

   ![chlimage_1-346](assets/chlimage_1-346.png)

## 为特定再现{#enabling-xmp-writeback-for-specific-renditions}启用XMP写回

要让XMP写回功能将元数据更改传播到选定的演绎版，请指定这些演绎版到DAM元数据回写工作流的XMP写回流程工作流步骤。 默认情况下，此步骤配置为原始再现。

要使XMP写回功能将元数据传播到再现缩略图140.100.png和319.319.png，请执行这些步骤。

1. 在Experience Manager中，导航到&#x200B;**[!UICONTROL 工具>工作流>模型]**。
1. 从[!UICONTROL 模型]页面，打开&#x200B;**[!UICONTROL DAM元数据写回]**&#x200B;工作流模型。
1. 在“ **[!UICONTROL DAM元数据写回]** ”属性页中，打开“ **[!UICONTROL XMP写回进程”步骤]** 。
1. 在&#x200B;**[!UICONTROL 步骤属性]**&#x200B;对话框中，点按/单击&#x200B;**[!UICONTROL 流程]**&#x200B;选项卡。
1. 在&#x200B;**[!UICONTROL 参数]**&#x200B;框中，添加`rendition:cq5dam.thumbnail.140.100.png,rendition:cq5dam.thumbnail.319.319.png`。 点按／单击&#x200B;**[!UICONTROL 确定]**。

   ![step_properties](assets/step_properties.png)

1. 要使用新属性为Dynamic Media图像重新生成金字塔TIFF演绎版，请将&#x200B;**[!UICONTROL Dynamic Media处理图像资产]**步骤添加到DAM元数据写回工作流。
PTIFF演绎版仅在Dynamic Media混合模式下创建并存储在本地。 保存工作流。

元数据更改将传播到资产的演绎版`thumbnail.140.100.png`和`thumbnail.319.319.png`，而不是其他演绎版。

>[!NOTE]
>
>有关64位Linux中的XMP写回问题，请参阅[如何在64位RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html)上启用XMP写回。
>
>有关支持的平台的详细信息，请参阅[XMP元数据回写先决条件](/help/sites-deploying/technical-requirements.md#requirements-for-aem-assets-xmp-metadata-write-back)。

## 筛选XMP元数据{#filtering-xmp-metadata}

[!DNL Experience Manager Assets] 支持XMP元数据的属性／节点的阻止列表和允许列表过滤，该元数据从资产二进制文件读取并在摄取资产时存储在JCR中。

使用阻止列表进行筛选后，您可以导入除为排除指定的属性外的所有XMP元数据属性。 但是，对于具有大量XMP元数据（例如，1000个节点具有10,000个属性）的资产类型（如INDD文件），要筛选的节点名称并不总是预先知道的。 如果使用阻止列表进行筛选允许导入大量具有大量XMP元数据的资产，AEM实例或群集可能会遇到稳定性问题，例如阻塞观察队列。

通过允许列表筛选XMP元数据可通过允许您定义要导入的XMP属性来解决此问题。 这样，将忽略任何其他或未知的XMP属性。 为了向后兼容，您可以向使用阻止列表的筛选器中添加一些这些属性。

>[!NOTE]
>
>筛选仅适用于资产二进制文件中从XMP源派生的属性。 对于从非XMP源（如EXIF和IPTC格式）派生的属性，过滤不起作用。 例如，资产创建日期存储在EXIF TIFF中名为`CreateDate`的属性中。 AEM将此值存储在名为`exif:DateTimeOriginal`的元数据字段中。 由于源是非XMP源，因此过滤不适用于此属性。

1. 从`https://[aem_server]:[port]/system/console/configMgr`打开Configuration Manager。
1. 打开&#x200B;**[!UICONTROL Adobe CQDAM XmpFilter]**&#x200B;配置。
1. 要通过允许列表应用过滤，请选允许列表择&#x200B;**[!UICONTROL 将应用到XMP属性]**，并在&#x200B;**[!UICONTROL 允许的XML名称中指定要导入的属性以进行XMP过滤]**。

   ![chlimage_1-347](assets/chlimage_1-347.png)

1. 要在通过允许列表应用过滤后过滤掉已阻止的XMP属性，请在&#x200B;**[!UICONTROL 用于XMP过滤的XML名称被阻止]**&#x200B;框中指定这些属性。 保存更改。

   >[!NOTE]
   >
   >默认情况下，将选阻止列表择&#x200B;**[!UICONTROL 应用到XMP属性]**&#x200B;选项。 换言之，默认情况下启用使用阻止列表进行筛选。 要禁用此类过滤，请取消选择&#x200B;**[!UICONTROL 应阻止列表用到XMP属性]**&#x200B;选项。
