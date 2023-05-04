---
title: 创建节点
seo-title: Create Nodes
description: 覆盖评论系统
seo-description: Overlay the comments system
uuid: 802ae28b-9989-4c2c-b466-ab76a724efd3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: cd4f53ee-537b-4f10-a64f-474ba2c44576
exl-id: fc044a4e-0037-405f-8c26-b388c6a98733
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 8%

---

# 创建节点 {#create-nodes}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

通过将所需的最少文件数从/libs复制到/apps中并在/apps中修改它们，以自定义版本覆盖注释系统。

>[!CAUTION]
>
>/libs文件夹的内容从不进行编辑，因为任何重新安装或升级都可能删除或替换/libs文件夹，而/apps文件夹的内容将保持不变。

使用 [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) 在创作实例中，首先在/apps文件夹中创建一个路径，该路径与/libs文件夹中叠加的组件的路径相同。

复制的路径为

* `/libs/social/commons/components/hbs/comments/comment`

路径中的某些节点是文件夹，而某些节点是组件。

1. 浏览到 [http://localhost:4502/crx/de/index.jsp](http://localhost:4502/crx/de/index.jsp)
1. 创建 `/apps/social` （如果它不存在）
   * 选择 `/apps` 节点
   * **[!UICONTROL 创建>文件夹……]**
      * 输入姓名: `social`
1. 选择 `social` 节点
   * **[!UICONTROL 创建>文件夹……]**
      * 输入姓名: `commons`
1. 选择 `commons` 节点
   * **[!UICONTROL 创建>文件夹……]**
      * 输入姓名: `components`
1. 选择 `components` 节点
   * **[!UICONTROL 创建>文件夹……]**.
      * 输入姓名: `hbs`
1. 选择 `hbs` 节点
   * **[!UICONTROL 创建>创建组件……]**
      * 输入标签： `comments`
      * 输入标题： `Comments`
      * 输入描述: `List of comments without showing avatars`
      * 超级类型: `social/commons/components/comments`
      * 输入群组： `Communities`
      * 单击 **[!UICONTROL 下一个]** 直到 **[!UICONTROL 确定]**
1. 选择 `comments` 节点

   * **[!UICONTROL 创建>创建组件……]**

      * 输入标签： `comment`
      * 输入标题： `Comment`
      * 输入描述: `A comment instance without avatars`
      * 超级类型: `social/commons/components/comments/comment`
      * 输入群组： `.hidden`
      * 单击 **[!UICONTROL 下一个]** 直到 **[!UICONTROL 确定]**
   * 选择 **[!UICONTROL 全部保存]**
1. 删除默认 `comments.jsp`
   * 选择节点 `/apps/social/commons/components/hbs/comments/comments.jsp`
   * 选择 **[!UICONTROL 删除]**
1. 删除默认的comment.jsp
   * 选择节点 `/apps/social/commons/components/hbs/comments/comment/comment.jsp`
   * 选择 **[!UICONTROL 删除]**
   * 选择 **[!UICONTROL 全部保存]**

>[!NOTE]
>
>为保留继承链， `Super Type` （属性） `sling:resourceSuperType`)的值与 `Super Type` 覆盖的组件中，在本例中为
>
>* `social/commons/components/comments`
>* `social/commons/components/comments/comment`
>


叠加图本身 `Type`（属性） `sling:resourceType`)必须是相对的自引用，以便在/apps中未找到的任何内容随后都会在/libs中查找。
* 名称: `sling:resourceType`
* 类型: `String`
* 价值: `social/commons/components/hbs/comments`

1. 选择绿色 `[+] Add`
   * 名称: `sling:resourceType`
   * 类型: `String`
   * 价值: `social/commons/components/hbs/comments/comment`
1. 选择绿色 `[+] Add`
   * 选择 **[!UICONTROL 全部保存]**

![chlimage_1-4](assets/chlimage_1-4.png)
