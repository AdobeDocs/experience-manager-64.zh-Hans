---
title: 配置帐户锁定设置
seo-title: Configure account-locking settings
description: 使用“启用帐户锁定”选项可在指定数量的连续身份验证失败后锁定用户帐户。
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: e407c643-5753-447e-ad4e-deb7b9eb2b55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 6%

---

# 配置帐户锁定设置 {#configure-account-locking-settings}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

添加域时，请指定是否启用帐户锁定。 选中启用帐户锁定选项后，在指定数量的连续身份验证失败后，用户帐户将被锁定。 在指定的时长后，用户可以尝试再次进行身份验证。 此功能可阻止用户尝试各种凭据组合来访问系统。

使用“域管理”页上的设置，指定身份验证失败的最大次数和帐户被锁定的时长。 这些设置适用于已启用帐户锁定的所有域。

1. 在管理控制台中，单击 **[!UICONTROL 设置>用户管理>域管理]**.
1. 在“最大连续身份验证失败次数”框中，输入用户在帐户被锁定之前尝试登录失败的连续次数。 默认值为 20。
1. 在“在以后解锁帐户（分钟）”框中，输入用户帐户被锁定的分钟数。 在指定的分钟数后，用户可以尝试再次登录。 默认值为 30。
1. 单击“**[!UICONTROL 保存]**”。
