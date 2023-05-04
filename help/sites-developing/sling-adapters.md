---
title: 使用 Sling 适配器
seo-title: Using Sling Adapters
description: Sling提供了适配器模式，可方便地转换实施可适应界面的对象
seo-description: Sling offers an Adapter pattern to conveniently translate objects that implement the Adaptable interface
uuid: 07f66a33-072d-49e1-8e67-8b80a6a9072a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: c081b242-67e4-4820-9bd3-7e4495df459e
exl-id: 7780d04d-418e-494c-85c3-76bef5f35690
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1753'
ht-degree: 14%

---

# 使用 Sling 适配器{#using-sling-adapters}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

[Sling](https://sling.apache.org) 选件 [适配器模式](https://sling.apache.org/site/adapters.html) 方便地转换实现 [适应性](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 界面。 此界面提供一个通用 [adaptTo()](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) 将对象转换为作为参数传递的类类型的方法。

例如，要将资源对象转换为相应的Node对象，您只需执行以下操作：

```java
Node node = resource.adaptTo(Node.class);
```

## 用例 {#use-cases}

有以下用例：

* 获取特定于实施的对象。

   例如，基于JCR的通用 [`Resource`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) 界面提供对基础JCR的访问 [`Node`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html).

* 要求传递内部上下文对象的对象的快捷方式创建。

   例如，基于JCR的 [`ResourceResolver`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) 包含对请求的引用 [`JCR Session`](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html)，而基于该请求会话工作的许多对象(如 [`PageManager`](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) 或 [`UserManager`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html).

* 服务的快捷方式。

   罕见的案例。 `sling.getService()` 也很简单。

### Null返回值 {#null-return-value}

`adaptTo()` 可返回null。

原因有多种，包括：

* 实施不支持目标类型
* 处理此案例的适配器工厂不活动(例如 由于缺少服务引用)
* 内部条件失败
* 服务不可用

请务必优雅地处理空值大小写。 对于jsp渲染，如果jsp失败将导致内容为空，则可能可以接受。

### 缓存 {#caching}

为了提高性能，实施可以免费缓存从 `obj.adaptTo()` 呼叫。 如果 `obj` 相同，则返回的对象相同。

此缓存针对所有 `AdapterFactory` 基于案例。

但是，没有一般规则 — 对象可以是新实例或现有实例。 这意味着您不能依赖任一行为。 因此，它很重要，特别是内部 `AdapterFactory`，则对象在此方案中可重复使用。

### 工作原理 {#how-it-works}

有多种方法 `Adaptable.adaptTo()` 可以实施：

* 对象本身；实现方法本身，并映射到特定对象。
* 按 [`AdapterFactory`](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html)，可映射任意对象。

   对象仍必须实现 `Adaptable` 界面和必须 [`SlingAdaptable`](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/adapter/SlingAdaptable.html) (通过 `adaptTo` 调用中央适配器管理器)。

   这允许将挂接到 `adaptTo` 现有类的机制，例如 `Resource`.

* 两者兼有。

对于第一种情况，javaoc可以说明 `adaptTo-targets` 是可能的。 但是，对于特定子类（如基于JCR的资源），通常不可能执行此操作。 在后一种情况下，实施 `AdapterFactory` 通常是包的私有类的一部分，因此不会在客户端API中公开，也不会在javaoc中列出。 理论上，可以访问所有 `AdapterFactory` 实施 [OSGi](/help/sites-deploying/configuring-osgi.md) 服务运行时并查看其“适配器”（源和目标）配置，但不要将它们相互映射。 最后，这取决于必须记录的内部逻辑。 因此，该参考。

## 引用 {#reference}

### Sling {#sling}

[**资源**](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) 调整为：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">节点</a></td> 
   <td>如果这是基于JCR的资源或引用节点的JCR属性。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Property.html">属性</a></td> 
   <td>如果这是基于JCR属性的资源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Item.html">项目</a></td> 
   <td>如果这是基于JCR的资源（节点或属性）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api//java/util/Map.html">地图</a></td> 
   <td>返回属性的映射(如果这是基于JCR节点的资源（或其他支持值的资源映射）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td> 
   <td>如果这是基于JCR节点的资源（或其他资源支持值映射），则返回属性的方便使用映射。 也可以（更简单）使用<br /> <code><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceUtil.html#getvaluemap%28org.apache.sling.api.resource.resource%29">ResourceUtil.getValueMap(Resource)</a></code> （处理空大小写等）</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">继承值映射</a></td> 
   <td>扩展 <a href="https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a> 这允许在查找属性时考虑资源的层次结构。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/PersistableValueMap.html">PersistableValueMap</a></td> 
   <td>如果这是基于JCR节点的资源，并且用户有权修改该节点上的属性。<br /> 注意：多个可持续映射不共享其值。</td> 
  </tr> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td> 
   <td>返回“文件”的二进制内容<code>nt:resource</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>AuthorizableResourceProvider</code><code>org.apache.sling.jackrabbit.usermanager</code><code>/system/userManager</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Page</code><code>cq:PseudoPage</code></td></tr><tr><td></td><td><code>cq:Component</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td><code>cq:Template</code></td></tr><tr><td></td><td><code>cq:Page</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:Tag</code></td></tr><tr><td></td><td><code>cq:Preferences</code></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr><tr><td></td><td><code>cq:ContentSyncConfig</code></td></tr></tbody></table>

[**ResourceResolver**](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/ResourceResolver.html) 调整为：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Session.html">会话</a></td> 
   <td>请求的JCR会话(如果这是基于JCR的资源解析程序（默认）)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">组件管理器</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td> 
   <td>基于JCR会话，如果这是基于JCR的资源解析程序。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td> 
   <td>基于JCR会话，如果这是基于JCR的资源解析程序。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td> 
   <td>基于JCR会话，如果这是基于JCR的资源解析程序，并且用户有权访问UserManager。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">可授权</a> </td> 
   <td>当前用户。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/jackrabbit/api/security/user/User.html">用户</a><br /> </td> 
   <td>当前用户。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/privileges/PrivilegeManager.html">权限管理器</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/Preferences.html">首选项</a></td> 
   <td>当前用户的首选项（如果这是基于JCR的资源解析程序，则基于JCR会话）。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/preferences/PreferencesService.html">首选项服务</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/auth/pin/PinManager.html">PinManager</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/Externalizer.html">外部器</a></td> 
   <td>用于外部化绝对URL，即使使用外部请求对象也是如此。<br /> </td> 
  </tr> 
 </tbody> 
</table>

[**SlingHttpServletRequest**](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) 调整为：

尚无目标，但实施了“适应性”，可在自定义AdapterFactory中用作源。

[**SlingHttpServletResponse**](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) 调整为：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://java.sun.com/j2se/1.5.0/docs/api/org/xml/sax/ContentHandler.html">ContentHandler</a><br /> (XML)</td> 
   <td>如果这是Sling重写器响应。</td> 
  </tr> 
 </tbody> 
</table>

#### WCM {#wcm}

[**页面**](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Page.html) 调整为：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><br /> </td> 
   <td>页面的资源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>标记的资源(==此)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">节点</a></td> 
   <td>页面的节点。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>页面资源可以调整的所有内容。</td> 
  </tr> 
 </tbody> 
</table>

[**组件**](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/components/Component.html) 调整为：

| [Resource](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 组件的资源。 |
|---|---|
| [LakedResource](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html) | 标记的资源(==此)。 |
| [节点](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 组件的节点。 |
| ... | 组件资源可以适应的所有内容。 |

[**模板**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/Template.html) 调整为：

<table> 
 <tbody> 
  <tr> 
   <td><a href="https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html">Resource</a><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td> 
   <td>模板的资源。</td> 
  </tr> 
  <tr> 
   <td><a href="https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/commons/LabeledResource.html">LakedResource</a></td> 
   <td>标记的资源(==此)。</td> 
  </tr> 
  <tr> 
   <td><a href="https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html">节点</a></td> 
   <td>此模板的节点。</td> 
  </tr> 
  <tr> 
   <td>...</td> 
   <td>模板资源可以适应的所有内容。</td> 
  </tr> 
 </tbody> 
</table>

#### 安全性 {#security}

[**可授权**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Authorizable.html), [**用户**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/User.html) 和 [**组**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/security/Group.html) 适应：

| [节点](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 返回用户/组主节点。 |
|---|---|
| [复制状态](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/ReplicationStatus.html) | 返回用户/组主节点的复制状态。 |

#### DAM {#dam}

[**资产**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/dam/api/Asset.html) 调整为：

| [Resource](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 资产的资源。 |
|---|---|
| [节点](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 资产的节点。 |
| ... | 资产资源可以调整的所有内容。 |

#### 标记 {#tagging}

[**标记**](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/tagging/Tag.html) 调整为：

| [Resource](https://helpx.adobe.com/cn/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/org/apache/sling/api/resource/Resource.html) | 标记的资源。 |
|---|---|
| [节点](https://www.adobe.io/experience-manager/reference-materials/spec/jsr170/javadocs/jcr-2.0/javax/jcr/Node.html) | 标记的节点。 |
| ... | 标记资源可以调整的所有内容。 |

#### 其他 {#other}

此外，Sling / JCR / OCM还提供 ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` ([对象内容映射](https://jackrabbit.apache.org/object-content-mapping.html))对象。
