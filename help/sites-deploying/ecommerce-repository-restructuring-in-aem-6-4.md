---
title: AEM 6.4中的电子商务存储库重组
seo-title: E-Commerce Repository Restructuring in AEM 6.4
description: 了解如何进行必要的更改，以便迁移到AEM 6.4 for E-Commerce中的新存储库结构。
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for E-Commerce.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
feature: Upgrading
exl-id: 6adcc1a4-eb0f-4410-8219-dbd7e6bbe469
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 4%

---

# AEM 6.4中的电子商务存储库重组{#e-commerce-repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如父项中所述 [AEM 6.4中的存储库重组](/help/sites-deploying/repository-restructuring.md) 页面，升级到AEM 6.4的客户应使用此页面来评估与影响AEM电子商务解决方案的存储库更改相关的工作量。 某些更改在AEM 6.4升级过程中需要工作，而其他更改可能会推迟到6.5升级。

## 升级6.4版 {#with-upgrade}

### 产品、订单、收藏、分类、装运方法和付款方法数据 {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table> 
 <tbody>
  <tr>
   <td><strong>上一位置</strong></td> 
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>新位置</strong></td> 
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>重组指导</strong></td> 
   <td><p>您可以使用 <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">延迟迁移</a> 迁移电子商务数据的任务。</p> <p>它执行以下步骤：</p> 
    <ul> 
     <li>调整对旧位置的引用以指向新位置</li> 
     <li>将内容从旧位置移动到新位置</li> 
     <li>删除旧位置，以最终激活整个系统中新位置的使用</li> 
    </ul> <p>任务涵盖的位置包括：</p> 
    <ul> 
     <li>/etc/commerce/products</li> 
     <li>/etc/commerce/collections<br /> </li> 
     <li>/etc/commerce/orders<br /> </li> 
     <li>/etc/commerce/payment-methods<br /> </li> 
     <li>/etc/commerce/shipping-methods<br /> </li> 
    </ul> <p>对于较大的目录，建议通过将以下Java系统属性传递到AEM来单独运行商务迁移任务：</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>迁移后，AEM需要重新启动。</p> </td> 
  </tr>
  <tr>
   <td><strong>注释</strong></td> 
   <td>不适用<br /> </td> 
  </tr>
 </tbody>
</table>
