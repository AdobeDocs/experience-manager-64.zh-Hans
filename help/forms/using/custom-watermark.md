---
title: 字母PDF预览中的自定义水印
seo-title: 字母PDF预览中的自定义水印
description: 了解如何在字母PDF预览中创建自定义水印。
seo-description: 了解如何在字母PDF预览中创建自定义水印。
uuid: f406de81-af94-40dd-97ec-9ca95620f961
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: a09e2c83-083d-427a-8336-0567e00c5712
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340

---


# 字母PDF预览中的自定义水印 {#custom-watermark-in-letter-pdf-preview}

## 概述 {#overview}

在“创建对应”UI中，代理用户预览最终形状的对应，在该形状中，对应被发送到后期处理，例如用于电子邮件或打印。

为了防止未授权使用此数据，组织可以在预览PDF上加上水印。 默认水印为“PREVIEW”，它显示在PDF中。

要在预览PDF中启用水印，请在“对应管理配 **[!UICONTROL 置”中选择“在预览]** 期间应用水印 **[!UICONTROL ”选项]**`https://[server]:[port]/system/console/configMgr`。

![default-watermark](assets/default-watermark.png)

您可以使用以下步骤自定义水印的文本和外观：

## 在“创建对应UI”的PDF预览中自定义水印 {#customizewatermark-}

1. 转到并 `https://[server]:[port]/[ContextPath]/crx/de` 以管理员身份登录。
1. 在apps文件夹中，创建一个名为 **[!UICONTROL previewwatermark的文件夹]** ，其路径／结构与libs文件夹中的previewwatermark文件夹类似：

   1. 右键单击以下路径的**previewwatermark **文件夹，然后选择“叠 **加节点”**:

      `/libs/fd/cm/configFiles/previewwatermark`

   1. 确保“叠加节点”对话框具有以下值：

      **** 路径：/libs/fd/cm/configFiles/previewwatermark

      **** 叠加位置：/apps/

      **** 匹配节点类型：已选中

      >[!NOTE]
      >
      >请勿在/libs分支中进行更改。 您所做的任何更改都可能会丢失，因为只要您：
      >
      >* 在实例上升级
      >* 应用热修复
      >* 安装功能包


   1. 单击“ **确定** ”，然后单击“ **全部保存”**。 预 **[!UICONTROL 览水印文件]** ，在指定路径中创建。

1. 将ddx文件从“/libs/fd/cm/configFiles/previewwatermark”文件夹复制并粘贴到“/apps/fd/cm/configFiles/previewwatermark”文件夹，然后单击“全 **[!UICONTROL 部保存”]**。
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

   有关自定义水印外观、文本和对齐方式的信息，请参阅在 [Assembler service和DDX Reference文档中添加和删除水印和背景](https://help.adobe.com/en_US/livecycle/11.0/ddxRef.pdf) 。

   >[!NOTE]
   >
   >在ddx文件中，对结果和源的引用应保持不更改为output.pdf和input.pdf。 文件ddx的名称也不应更改。

1. 单击“ **全部保存**”。

