---
title: 提升启动项
seo-title: Promoting Launches
description: 在发布之前，您需要提升启动页面以将内容移回源（生产）。 提升启动页面时，源页面的对应页面将被替换为提升页面的内容。
seo-description: You need to promote launch pages to move the content back into the source (production) before publishing. When a launch page is promoted, the corresponding page of the source pages is replaced with the content of the promoted page.
uuid: 91f1c6ac-8c4e-4459-aaab-feaa32befc45
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8d38c6f7-8fea-4d27-992d-03b604b9541f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 793c44fa-9dd1-45f2-b1ab-219b436fcb54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 4%

---

# 提升启动项{#promoting-launches}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

在发布之前，您需要提升启动页面以将内容移回源（生产）。 提升启动页面时，源页面的对应页面将被替换为提升页面的内容。 提升启动项页面时，可以使用以下选项：

* 是仅提升当前页面还是提升整个启动项。
* 是否提升当前页面的子页面。
* 是提升完整启动项，还是仅提升已更改的页面。

## 提升启动页面 {#promoting-launch-pages}

要提升页面，请在编辑要提升的启动页面时执行以下步骤：

1. 在 **页面** 选项卡，单击 **提升启动项**.
1. 指定要提升的页面：

   * （默认）要仅提升当前页面，请选择 **将页面更改提升到生产版本**.
   * 要同时提升当前页面的子页面，请选择 **包含子页面**.
   * 要提升启动项中的所有页面，请选择 **将完整启动项提升到生产版本**.

1. 要将生产页面添加到工作流包，请选择 **添加到工作流包** ，然后选择工作流包。
1. 单击 **提升**.

## 使用 AEM 工作流处理提升的页面 {#processing-promoted-pages-using-aem-workflow}

使用工作流模型对提升的启动项页面执行批量处理：

1. 创建工作流包。
1. 作者提升启动页面时，会将其存储在工作流包中。
1. 使用包作为有效负载，启动工作流模型。

要在提升页面时自动启动工作流， [配置工作流启动器](/help/sites-administering/workflows-starting.md#workflows-launchers) 的子域。

例如，当作者提升启动项页面时，您可以自动生成页面激活请求。 配置工作流启动器，以在修改包节点时启动请求激活工作流。

![chlimage_1-136](assets/chlimage_1-136.png)
