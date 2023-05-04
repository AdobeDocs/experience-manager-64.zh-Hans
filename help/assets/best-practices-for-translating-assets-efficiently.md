---
title: 有效翻译资产的最佳实践
description: 有效管理资产的最佳实践，可同步各种翻译版本并简化翻译工作流程。
contentOwner: AG
feature: Translation
role: User,Admin
exl-id: 15162b80-ddef-4ec0-9db6-36695c93ebb1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 1%

---

# 高效翻译资产的最佳实践 {#best-practices-for-translating-assets-efficiently}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets支持多语言工作流，用于将数字资产的二进制文件、元数据和标记翻译为多个区域设置，并管理已翻译的资产。 有关详细信息，请参阅 [多语言资产](multilingual-assets.md).

为了有效管理资产以确保不同翻译版本保持同步，请创建 [语言副本](preparing-assets-for-translation.md) 资产。

资产或资产组的语言副本是具有相似内容层次结构的同级语言（或同一语言中资产的版本）。

每个语言副本都是一个独立资产。 因此，将资产翻译为多个区域设置可能会大大增加CRX存储库的大小。 例如，将总大小为10 GB的资产转换为两种语言可将存储库大小增加约20 GB（每种语言为10 GB）。

与元数据和标记相比，资产二进制文件占用的存储空间要大得多。 因此，如果转换元数据和标记仅对您有用，请省略来转换二进制文件。 您可以保留存储库中二进制文件的原始副本，以便与翻译为不同区域设置的元数据和标记关联。 维护二进制文件的单个副本（而不是多个已翻译版本）可以最大限度地减少对存储库大小的影响。

文件数据存储和Amazon S3数据存储提供了最适合这些情形的存储基础架构。 这些存储库存储资产二进制文件（包括演绎版）的单个副本，这些二进制文件可在多个区域设置中由元数据和标记共享。 因此，创建资产语言副本以及翻译元数据和标记不会影响存储库大小。

您还可以对几个工作流和翻译集成框架进行一些配置更改，以进一步简化该过程。

1. 执行下列操作之一：

   * [设置文件数据存储](/help/sites-deploying/data-store-config.md)
   * [设置Amazon S3数据存储](/help/sites-deploying/data-store-config.md)

1. 禁用 [DAM元数据写回](/help/sites-administering/workflow-offloader.md#disable-offloading) 工作流

   正如名字所暗示的， *DAM元数据写回* 工作流会将元数据重写到二进制文件。 由于元数据在翻译后会发生更改，因此将其写回二进制文件会为语言副本生成不同的二进制文件。

   >[!NOTE]
   >
   >禁用 *DAM元数据写回* 工作流关闭对资产二进制文件的XMP元数据回写。 因此，将来的元数据更改将不再保存在资产中。 在禁用此工作流之前，评估后果。

1. 启用 *设置上次修改日期* 工作流。

   的 *DAM元数据写回* 工作流为资产配置上次修改日期。 由于您在步骤2中禁用此工作流， [!DNL Experience Manager Assets] 无法再将资产的上次修改日期保持为最新。 因此，请启用 *设置上次修改日期* 工作流，以确保资产的上次修改日期为最新。 具有过期的上次修改日期的资产可能会导致错误。

1. [配置翻译集成框架](/help/sites-administering/tc-tic.md) 停止转换资产二进制文件。 取消选择资产选项卡下的“翻译资产”选项，以停止翻译资产二进制文件。
1. 使用 [多语言资产工作流](multilingual-assets.md).
