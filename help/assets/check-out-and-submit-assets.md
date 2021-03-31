---
title: 登记和注销您的数字资产，以便进行编辑
description: 了解如何签出资产进行编辑，并在更改完成后重新签入。
contentOwner: AG
feature: 资产管理
role: 商务从业人员
translation-type: tm+mt
source-git-commit: 4acf159ae1b9923a9c93fa15faa38c7f4bc9f759
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 4%

---


# 资产{#check-in-and-check-out-files-in-assets}中的签入和签出文件

Adobe Experience Manager(AEM)资产可让您在完成更改后签出资产进行编辑并重新签入。 在签出资产后，只有您才能编辑、批注、发布、移动或删除资产。 签出资产会锁定资产。 在您将资产签回AEM Assets之前，其他用户无法对资产执行任何这些操作。 但是，他们仍然可以更改锁定资产的元数据。

要能够签出或签入资产，您需要对它们具有写入权限。

此功能有助于防止其他用户覆盖作者所做的更改，在作者中，多个用户跨团队协作编辑工作流。

## 签出资源{#checking-out-assets}

1. 从资产用户界面中，选择您要签出的资产。 您还可以选择要签出的多个资产。

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. 在工具栏中，单击/点按&#x200B;**[!UICONTROL 结帐]**&#x200B;图标。

   ![chlimage_1-469](assets/chlimage_1-469.png)

   请注意，**[!UICONTROL Checkout]**&#x200B;图标在锁定打开时切换为&#x200B;**[!UICONTROL Checkin]**&#x200B;图标。

   ![chlimage_1-470](assets/chlimage_1-470.png)

   要验证其他用户是否可以编辑您注销的资产，请以其他用户身份登录。 您签出的资产的缩略图上会显示一个锁定图标。

   ![chlimage_1-471](assets/chlimage_1-471.png)

   选择资产。 请注意，工具栏不会显示任何允许您编辑、注释、发布或删除资产的选项。

   ![chlimage_1-472](assets/chlimage_1-472.png)

   但是，您可以单击/点按&#x200B;**[!UICONTROL 视图属性]**&#x200B;图标，以编辑已锁定资产的元数据。

1. 单击/点按编辑图标以在编辑模式下打开资产。

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. 编辑资产并保存更改。 例如，裁剪图像并保存。

   ![chlimage_1-474](assets/chlimage_1-474.png)

   您还可以选择对资产添加注释或发布。

1. 从 Assets UI 中选择已编辑资产，然后单击/点按工具栏中的&#x200B;**[!UICONTROL 签入]**&#x200B;图标。

   ![chlimage_1-475](assets/chlimage_1-475.png)

   修改后的资产会签入AEM Assets，可供其他用户编辑。

## 强制签入{#forced-check-in}

管理员可以签入其他用户签出的资产。

1. 以管理员身份登录AEM Assets。
1. 在资产用户界面中，选择一个或多个已由其他用户签出的资产。

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. 在工具栏中，单击/点按&#x200B;**[!UICONTROL 释放锁定]**&#x200B;图标。 资产会签回并可供其他用户编辑。

   ![chlimage_1-477](assets/chlimage_1-477.png)