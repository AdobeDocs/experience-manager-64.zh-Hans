---
title: 信件PDF预览中的自定义水印
seo-title: Custom watermark in letter PDF preview
description: 了解如何在信件PDF预览中创建自定义水印。
seo-description: Learn how to create custom watermark in letter PDF preview.
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
feature: Correspondence Management
exl-id: 8aeabd95-948d-4a54-b593-1eda8ddd731b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 1%

---

# 信件PDF预览中的自定义水印 {#custom-watermark-in-letter-pdf-preview}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 概述 {#overview}

在“创建通信”UI中，代理用户以最终形式预览通信，在最终形式中，通信被发送到后处理，如用于电子邮件或打印。

为防止未授权使用此数据，组织可以对预览PDF施加水印。 默认水印为“PREVIEW”，该水印会在整个PDF中显示。

要在预览PDF中启用水印，请选择 **[!UICONTROL 应用水印]** 预览期间选项 **[!UICONTROL 通信管理配置]** at `https://[server]:[port]/system/console/configMgr`.

![默认水印](assets/default-watermark.png)

您可以使用以下步骤来自定义水印的文本和外观：

## 在创建通信UI的PDF预览中自定义水印 {#customizewatermark-}

1. 转到 `https://[server]:[port]/[ContextPath]/crx/de` 和以管理员身份登录。
1. 在apps文件夹中，创建一个名为 **[!UICONTROL 预览水印]** 其路径/结构与libs文件夹中的previewwatermark文件夹类似：

   1. 右键单击以下路径中的**预览水印**文件夹，然后选择 **覆盖节点**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. 确保“覆盖节点”对话框具有以下值：

      **路径：** /libs/fd/cm/configFiles/previewwatermark

      **叠加位置：** /apps/

      **匹配节点类型：** 已选中

      >[!NOTE]
      >
      >请勿在/libs分支中进行更改。 您所做的任何更改都可能会丢失，因为当您执行以下操作时，此分支将容易发生更改：
      >
      >* 在实例上升级
      >* 应用热修复程序
      >* 安装功能包


   1. 单击 **确定** 然后单击 **全部保存**. 的 **[!UICONTROL 预览水印]** 文件夹是在指定的路径中创建的。

1. 将dx文件从“/libs/fd/cm/configFiles/previewwatermark”文件夹复制并粘贴到“/apps/fd/cm/configFiles/previewwatermark”文件夹，然后单击 **[!UICONTROL 全部保存]**.
1. 在/apps/fd/cm/configFiles/previewwatermark/下的ddx文件中进行所需的更改。

   ```
   <DDX xmlns="https://ns.adobe.com/DDX/1.0/">
    <PDF result="output.pdf">
     <PDF source="input.pdf"/>
           <Watermark opacity="15%" rotation="45">
            <StyledText>
                     <p font-family="Georgia" font-size="70pt" color="black" font-weight="bold">
                         PREVIEW
                    </p>
            </StyledText>
           </Watermark>
    </PDF>
   </DDX>
   ```

   有关自定义水印外观、文本和对齐方式的信息，请参阅 [汇编程序服务和DDX参考](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) 文档。

   >[!NOTE]
   >
   >在ddx文件中，对结果和源的引用应保持不更改为output.pdf和input.pdf。 文件ddx的名称也不应更改。

1. 单击 **全部保存**.
