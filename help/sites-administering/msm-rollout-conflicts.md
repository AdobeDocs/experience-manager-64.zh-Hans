---
title: MSM转出冲突
seo-title: MSM转出冲突
description: 了解如何处理多站点管理器转出冲突。
seo-description: 了解如何处理多站点管理器转出冲突。
uuid: 7a640905-aae2-498e-b95c-2c73008fa1cd
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 16db5334-604f-44e2-9993-10d683dee5bb
translation-type: tm+mt
source-git-commit: aac5026a249e1cb09fec66313cc03b58597663f0
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---


# MSM转出冲突{#msm-rollout-conflicts}

如果在Blueprint分支和从属Live Copy分支中创建了具有相同页面名称的新页面，则可能会发生冲突。

此类冲突需要在转出时进行处理和解决。

## 冲突处理 {#conflict-handling}

当存在冲突的页面（在Blueprint和Live Copy分支中）时，MSM允许您定义应如何（甚至是如何）处理它们。

要确保转出未被阻止，可能的定义可以包括：

* 转出过程中，哪个页面（blueprint或live copy）将具有优先级，
* 将重命名哪些页面（以及如何）,
* 这将如何影响任何已发布的内容。

   AEM（现成）的默认行为是发布的内容不会受到影响。 因此，如果在Live Copy分支中手动创建的页面已发布，则该内容在冲突处理和转出后仍将发布。

除了标准功能之外，还可以添加自定义冲突处理程序以实施不同的规则。 这些操作还允许将发布操作作为单个进程执行。

### 示例方案 {#example-scenario}

在以下几节中，我们使用在Blueprint和 `b`Live Copy分支（手动创建）中创建的新页面示例来说明解决冲突的各种方法：

* blueprint: `/b`

   主控页面； 1页，bp-level-1

* live copy: `/b`

   在Live Copy分支中手动创建的页面； 1个子页面 `lc-level-1`。

   * 发布时激活 `/b`为，以及子页面。

**转出前**

<table> 
 <tbody> 
  <tr> 
   <td><strong>bluept在转出前</strong></td> 
   <td><strong>转出前的Live Copy</strong></td> 
   <td><strong>发布前转出</strong></td> 
  </tr> 
  <tr> 
   <td><code>b</code> <br /> （在blueprint分支中创建，准备转出）<br /> </td> 
   <td><code>b</code> <br /> （在Live Copy分支中手动创建）<br /> </td> 
   <td><code>b</code> <br /> （包含在Live Copy分支中手动创建的页面b的内容）</td> 
  </tr> 
  <tr> 
   <td><code> /bp-level-1</code></td> 
   <td><code> /lc-level-1</code> <br /> （在Live Copy分支中手动创建）<br /> </td> 
   <td><code> /lc-level-1</code> <br /> (包含在Live<br /> Copy分支中手动创建的page child-level-1的内容)</td> 
  </tr> 
 </tbody> 
</table>

## 转出管理器和冲突处理 {#rollout-manager-and-conflict-handling}

转出管理器允许您激活或取消激活冲突管理。

这是使用Day [CQ WCM](/help/sites-deploying/configuring-osgi.md) 转 **出管理器的OSGi配置完成的**:

* **处理与手动创建的页面的冲突**:

   ( `rolloutmgr.conflicthandling.enabled`)

   如果转出管理器应处理在Live Copy中创建的页面中的冲突，并且名称在Blueprint中存在，则设置为true。

AEM在 [取消激活冲突管理时具有预定义的行为](#behavior-when-conflict-handling-deactivated)。

## 冲突处理程序 {#conflict-handlers}

AEM使用冲突处理程序解决将内容从蓝图转出到Live Copy时存在的任何页面冲突。 重命名页面是解决此类冲突的一种（通常）方法。 可以操作多个冲突处理程序以允许选择不同的行为。

AEM提供：

* 默认 [冲突处理程序](#default-conflict-handler):

   * `ResourceNameRolloutConflictHandler`

* 实现自定义处理 [程序的可能](#customized-handlers)。
* 允许您设置每个处理程序的优先级的服务分级机制。 使用排名最高的服务。

### 默认冲突处理程序 {#default-conflict-handler}

默认冲突处理程序：

* 调用 `ResourceNameRolloutConflictHandler`

* 使用此处理函数，将优先处理蓝图页面。
* 此处理函数的服务等级设置为低(即 属性的默认值 `service.ranking` )，因为假定自定义处理程序需要更高的级别。 但是，排名并不是确保必要时灵活性的绝对最小值。

此冲突处理程序优先于Blueprint。 Live Copy页面 `/b` 将移动（在Live Copy分支中）到 `/b_msm_moved`。

* live copy: `/b`

   移动到（在Live Copy中） `/b_msm_moved`。 这充当备份，并确保不丢失任何内容。

   * `lc-level-1` 不移动。

* blueprint: `/b`

   转出到Live Copy页面 `/b`。

   * `bp-level-1` 转出到Live Copy。

**转出后**

<table> 
 <tbody> 
  <tr> 
   <td><strong>plueprint for rollout</strong></td> 
   <td><strong>转出后的Live Copy</strong><br /> </td> 
   <td></td>
   <td><strong>转出后的Live Copy</strong><br /> <br /> <br /> </td> 
   <td><strong>转出后发布</strong><br /> <br /> </td> 
  </tr> 
  <tr> 
   <td><code>b</code></td> 
   <td><code>b</code> <br /> （包含已转出的蓝图页面b的内容）<br /> </td> 
   <td></td>
   <td><code>b_msm_moved</code> <br /> （包含在Live Copy分支中手动创建的页面b的内容）</td> 
   <td><code>b</code> <br /> （无变动） 包含在Live Copy分支中手动创建的原始页面b的内容，现在称为b_msm_moved)<br /> </td> 
  </tr> 
  <tr> 
   <td><code> /bp-level-1</code></td> 
   <td><code class="code"> /bp-level-1</code></td> 
   <td><code> /lc-level-1</code> <br /> （无更改）</td> 
   <td><code> </code></td> 
   <td><code> /lc-level-1</code> <br /> （无更改）</td> 
  </tr> 
 </tbody> 
</table>

### 自定义处理程序 {#customized-handlers}

自定义冲突处理程序允许您实施自己的规则。 使用服务排名机制，您还可以定义它们与其他处理程序的交互方式。

自定义冲突处理程序可以：

* 根据您的要求命名。 ``
* 根据您的要求进行开发／配置； 例如，您可以开发一个处理程序，以使Live Copy页面优先。
* 可设计为使用OSGi配置 [进行配置](/help/sites-deploying/configuring-osgi.md); 特别是：

   * **服务等级**:

      定义与其他冲突处理程序()相关 `service.ranking`的顺序。

      默认值为 0。

### 冲突处理被取消激活时的行为 {#behavior-when-conflict-handling-deactivated}

如果手动取 [消激活冲突处理](#rollout-manager-and-conflict-handling) ,AEM不会对任何冲突页面执行任何操作（非冲突页面会按预期方式转出）。

>[!CAUTION]
>
>AEM不表示冲突被忽略，因为必须显式配置此行为，因此假定它是必需行为。

在这种情况下，Live Copy会优先有效。 Blueprint页面 `/b` 不会复制，Live Copy页面 `/b` 将保持不变。

* blueprint: `/b`

   完全不复制，但忽略。

* live copy: `/b`

   保持不变。

<table> 
 <caption>
   转出后 
 </caption> 
 <tbody> 
  <tr> 
   <td><strong>plueprint for rollout</strong></td> 
   <td><strong>转出后的Live Copy</strong><br /> <br /> <br /> </td> 
   <td><strong>转出后发布</strong><br /> <br /> </td> 
  </tr> 
  <tr> 
   <td><code>b</code></td> 
   <td><code>b</code> <br /> （无变动） 包含在Live Copy分支中手动创建的页面b的内容)</td> 
   <td><code>b</code> <br /> （无变动） 包含在Live Copy分支中手动创建的页面b的内容)<br /> </td> 
  </tr> 
  <tr> 
   <td><code> /bp-level-1</code> </td> 
   <td><code> /lc-level-1</code> <br /> （无更改）</td> 
   <td><code> /lc-level-1</code> <br /> （无更改）</td> 
  </tr> 
 </tbody> 
</table>

### 服务排名 {#service-rankings}

OSGi [服务](https://www.osgi.org/) 排序可用于定义单个冲突处理程序的优先级。
