---
title: 有效翻译资产的最佳实践
description: 有效管理资产的最佳实践，可同步各种翻译版本并简化翻译工作流。
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# 有效翻译资产的最佳实践 {#best-practices-for-translating-assets-efficiently}

Adobe Experience Manager(AEM)资产支持多语言工作流，将数字资产的二进制文件、元数据和标记翻译为多个区域设置并管理已翻译的资产。 有关详细信息，请参 [阅多语言资产](multilingual-assets.md)。

为了有效管理资产以确保不同的翻译版本保持同步，请在运行 [翻译工作流](preparing-assets-for-translation.md) 之前创建资产的语言副本。

资产或资产组的语言副本是具有相似内容层次结构的语言同级（或同一语言中资产的版本）。

每个语言副本都是独立资产。 因此，将资源翻译为多个区域设置可大幅增加CRX存储库的大小。 例如，将总大小为10 GB的资产翻译为两种语言可将存储库大小增加约20 GB（每种语言为10 GB）。

与元数据和标记相比，资源二进制文件占用的存储空间要大得多。 因此，如果转换元数据和标记只能满足您的目的，请忽略转换二进制文件。 您可以在存储库中保留二进制文件的原始副本，以便与翻译为不同区域设置的元数据和标记关联。 维护一个二进制副本（而不是多个译文版本）可最大限度地减少对存储库大小的影响。

文件数据存储和AmazonS3数据存储提供最适合这些情形的存储基础结构。 这些存储存储库存储资产二进制文件（包括演绎版）的单一副本，这些二进制文件可以在多个区域设置中由元数据和标记共享。 因此，创建资产语言副本以及翻译元数据和标记不会影响存储库大小。

您还可以对两个工作流和翻译集成框架进行一些配置更改以进一步简化该过程。

1. 执行下列操作之一：

   * [设置文件数据存储](/help/sites-deploying/data-store-config.md)
   * [设置AmazonS3数据存储](/help/sites-deploying/data-store-config.md)

1. 禁用DAM元数 [据写回工作流](/help/sites-administering/workflow-offloader.md#disable-offloading) 。

   如名称所示，DAM元数 *据写回工作流* 会将元数据重写到二进制文件。 由于元数据在翻译后会发生更改，因此将其写回二进制文件会为语言副本生成不同的二进制文件。

   >[!NOTE]
   >
   >禁用DAM MetaData *写回工作流* ，将关闭资产二进制文件的XMP元数据写回。 因此，将来的元数据更改不再保存在资产中。 在禁用此工作流之前，评估后果。

1. 启用“设 *置上次修改日期* ”工作流。

   DAM MetaData *写回工作流* ，配置资产的上次修改日期。 由于您在步骤2中禁用了此工作流，AEM Assets无法再让资产的上次修改日期保持最新。 因此，请启 *用“设置上次修改日期* ”工作流，以确保资产的上次修改日期为最新日期。 具有过期的上次修改日期的资产可能会导致错误。

1. [配置转换集成框架](/help/sites-administering/tc-tic.md) ，以停止转换资产二进制文件。 取消选择“资产”选项卡下的“转换资产”选项，以停止转换资产二进制文件。
1. 使用多语言资产工作流转 [译资产元数据／标记](multilingual-assets.md)。

