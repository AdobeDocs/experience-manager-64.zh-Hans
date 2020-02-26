---
title: 指定XCI配置选项
seo-title: 指定XCI配置选项
description: 了解如何指定XCI配置选项。
seo-description: 了解如何指定XCI配置选项。
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
translation-type: tm+mt
source-git-commit: d04e08e105bba2e6c92d93bcb58839f1b5307bd8

---


# 指定XCI配置选项 {#specifying-xci-configuration-options}

表单允许您指定用于渲染的自定义XCI文件。 (请参阅 [配置表单的位置](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms)。)默认情况下，表单会覆盖在XCI文件中指定的一些选项，包括：

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

您可以选择取消覆盖上述选项的选项，在这种情况下，表单将使用自定义XCI文件中指定的值。

1. 在管理控制台中，单击“服务”>“表单”。
1. 选中或取消选中“使用系统默认XCI选项”复选框。 选择此选项后，Forms将使用其默认值设置包、创建者、producer和compressObjectStream。 取消选择此选项后，Forms将使用自定义XCI文件中指定的值。
1. 单击保存。

