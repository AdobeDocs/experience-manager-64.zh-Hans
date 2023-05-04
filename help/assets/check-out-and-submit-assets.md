---
title: 签入和签出数字资产以进行编辑
description: 了解如何签出要编辑的资产，并在更改完成后重新签入它们。
contentOwner: AG
feature: Asset Management
role: User
exl-id: 0c79ed42-0acd-426e-8e14-412bb4117585
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 5%

---

# Assets中的签入和签出文件 {#check-in-and-check-out-files-in-assets}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets允许您签出资产以进行编辑，并在完成更改后重新签入。 签出资产后，只有您才能编辑、注释、发布、移动或删除资产。 签出资产会锁定资产。 在您将资产签回到 [!DNL Experience Manager] 资产。 但是，他们仍可以更改锁定资产的元数据。

要签出或签入资产，您需要对它们具有写入权限。

此功能有助于防止其他用户覆盖作者所做的更改，在作者所做的更改中，多个用户会跨团队协作进行编辑工作流。

## 结帐资产 {#checking-out-assets}

1. 从资产UI中，选择要签出的资产。 您还可以选择多个要签出的资产。

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. 在工具栏中，单击/点按 **[!UICONTROL 结帐]** 图标。

   ![chlimage_1-469](assets/chlimage_1-469.png)

   请注意 **[!UICONTROL 结帐]** 图标切换 **[!UICONTROL 签入]** 图标。

   ![chlimage_1-470](assets/chlimage_1-470.png)

   要验证其他用户是否可以编辑您签出的资产，请以其他用户身份登录。 签出的资产的缩略图上会显示锁图标。

   ![chlimage_1-471](assets/chlimage_1-471.png)

   选择资产。 请注意，工具栏不显示任何选项，允许您编辑、注释、发布或删除资产。

   ![chlimage_1-472](assets/chlimage_1-472.png)

   但是，您可以单击/点按 **[!UICONTROL 查看属性]** 图标，以编辑锁定资产的元数据。

1. 单击/点按编辑图标，以在编辑模式下打开资产。

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. 编辑资产并保存更改。 例如，裁剪图像并保存。

   ![chlimage_1-474](assets/chlimage_1-474.png)

   您还可以选择在资产中添加批注或发布资产。

1. 从 Assets UI 中选择已编辑资产，然后单击/点按工具栏中的&#x200B;**[!UICONTROL 签入]**&#x200B;图标。

   ![chlimage_1-475](assets/chlimage_1-475.png)

   已修改的资产将签入到 [!DNL Assets] 和可供其他用户编辑。

## 强制签入 {#forced-check-in}

管理员可以签入其他用户签出的资产。

1. 登录到 [!DNL Assets] 作为管理员。
1. 从资产UI中，选择一个或多个已由其他用户签出的资产。

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. 在工具栏中，单击/点按 **[!UICONTROL 释放锁]** 图标。 资产会签回，以供其他用户编辑。

   ![chlimage_1-477](assets/chlimage_1-477.png)
