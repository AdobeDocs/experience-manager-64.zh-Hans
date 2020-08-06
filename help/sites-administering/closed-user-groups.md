---
title: AEM中已关闭的用户组
seo-title: AEM中已关闭的用户组
description: 了解AEM中的已关闭用户组。
seo-description: 了解AEM中的已关闭用户组。
uuid: a65ed163-fdec-45f3-adf9-984d36f4eb73
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: a2bd7045-970f-4245-ad5d-a272a654df0a
translation-type: tm+mt
source-git-commit: 7dc90299b7a0e5166c30702323f1678353fe39b3
workflow-type: tm+mt
source-wordcount: '6889'
ht-degree: 0%

---


# AEM中已关闭的用户组{#closed-user-groups-in-aem}

## 简介 {#introduction}

自AEM 6.3起，新的“已关闭的用户组”实施旨在解决现有实施中存在的性能、可扩展性和安全问题。

>[!NOTE]
>
>为了简单起见，本文档中将使用CUG缩写。

新实施的目标是在需要时涵盖现有功能，同时解决旧版本的问题和设计限制。 结果是具有以下特点的新CUG设计：

* 认证和授权元素的清晰分离，可单独或组合使用；
* 专用的授权模型，在配置的CUG树上反映受限读取访问，不会干扰其他访问控制设置和权限要求；
* 在创作实例时通常需要受限读取权限的访问控制设置与发布时通常只需要的权限评估之间进行分离；
* 编辑受限读取访问，而不提升权限；
* 专用节点类型扩展标记认证要求；
* 与身份验证要求关联的可选登录路径。

### 新的自定义用户组实现 {#the-new-custom-user-group-implementation}

在AEM的上下文中称为CUG的步骤包括：

* 限制对需要保护的树的读取访问，并且仅允许对包含给定CUG实例的承担者进行读取，或者完全从CUG评估中排除。 这称为授 **权** 元素。
* 在给定树上强制进行身份验证，并（可选）为该树指定一个专用登录页，该页随后会被排除。 这称为身份验 **证** 元素。

新的实现设计为在验证和授权元素之间划出一条线。 从AEM 6.3开始，可以在不显式添加身份验证要求的情况下限制读访问。 例如，如果给定实例需要完全身份验证，或者给定树已驻留在需要身份验证的子树中。

同样，给定的树可以用身份验证要求进行标记，而无需更改有效权限设置。 组合和结果列在组合CUG策 [略和身份验证要求部分](/help/sites-administering/closed-user-groups.md#combining-cug-policies-and-the-authentication-requirement) 。

## 概述 {#overview}

### 授权： 限制读取访问 {#authorization-restricting-read-access}

CUG的主要功能是限制内容存储库中给定树上除选定承担者之外的所有人的读取访问权限。 新的实现采用的方法不是即时处理默认访问控制内容，而是定义表示CUG的专用访问控制策略类型。

#### CUG的访问控制政策 {#access-control-policy-for-cug}

此新型策略具有以下特点：

* 访问控制org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy（由Apache Jackrabbit API定义）类型的策略；
* PrincipalSetPolicy授予可修改的主体集的权限；
* 授予的权限和策略的范围是实施详细信息。

用于表示CUG的PrincipalSetPolicy的实施还定义了：

* CUG策略仅授予对常规JCR项目的读取权限(例如，访问控制内容被排除);
* 范围由包含CUG策略的访问控制节点定义；
* CUG策略可以嵌套，嵌套的CUG将新CUG开始，而不继承“父”CUG的主体集；
* 如果启用了评估，则策略的效果将继承到整个子树，下一个嵌套CUG。

这些CUG策略通过名为oak-authorization-cug的单独授权模块部署到AEM实例。 本模块附带有自己的访问控制管理和权限评估。 换言之，默认的AEM设置提供一个Oak内容存储库配置，该配置结合了多个授权机制。 有关详细信息，请 [参阅Apache Oak文档中的此页](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html)。

在此复合设置中，新的CUG不会替换附加到访问控制节点的现有目标内容，而是设计为补充，以后也可以删除它而不影响原始访问控制，在AEM中默认情况下，它将是访问控制列表。

与前一实施相比，新的CUG政策始终被承认并视为访问控制内容。 这意味着它们是使用JCR访问控制管理API创建和编辑的。 有关详细信息，请参 [阅管理CUG策略](#managing-cug-policies) 。

#### CUG策略的权限评估 {#permission-evaluation-of-cug-policies}

除了CUG的专用访问控制管理，新授权模型还允许有条件地启用其策略的权限评估。 这允许在分阶段环境中设置CUG策略，并且只允许在复制到生产环境后评估有效权限。

CUG策略的权限评估以及与默认或任何附加授权模型的交互遵循Apache Jackrabbit Oak中为多个授权机制设计的模式： 如果且仅当所有模型授予访问权限时，才授予给定权限集。 有关 [更多详细信息](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html) ，请参阅此页。

与用于处理和评估CUG策略的授权模型相关的权限评估适用以下特性：

* 它只处理常规节点和属性的读取权限，而不处理读取访问控制内容
* 它不处理对受保护JCR内容(访问控制、节点类型信息、版本控制、锁定或用户管理等)进行修改所需的写入权限或任何类型的权限； 这些权限不受CUG策略影响，并且不会由关联的授权模型评估。 是否授予这些权限取决于在安全设置中配置的其他模型。

单个CUG策略对权限评估的影响可概括如下：

* 除策略中列出的包含被排除的承担者或承担者的主体外，所有人均拒绝读取权限；
* 该策略对包含该策略及其属性的访问控制节点生效；
* 此效果还会在层次结构中继承——即由访问控制节点定义的项目树；
* 但是，它既不影响访问控制节点的同级，也不影响访问控制节点的祖先；
* 给定CUG的继承在嵌套CUG处停止。

#### 最佳实践 {#best-practices}

在通过CUG定义受限读取访问权限时，应考虑以下最佳实践：

* 有意识地决定您对CUG的需求是限制读取访问还是验证要求。 如果是后者，或者如果两者都需要，请查阅最佳实践部分，以了解有关身份验证要求的详细信息
* 为需要保护的数据或内容创建威胁模型，以识别威胁边界并清晰了解数据的敏感性以及与授权访问相关的角色
* 为存储库内容和CUG建立模型，同时要考虑到与一般授权相关的方面和最佳做法：

   * 请记住，仅当给定的CUG和设置授权中部署的其他模块的评估允许给定主体读取给定存储库项目时，才会授予读取权限
   * 避免创建冗余CUG，因为其他授权模块已限制读取访问
   * 对嵌套CUG的过度需求可能会突出内容设计中的问题
   * 对CUG的过度需求（例如，在每个页面上）可能表明需要一个可能更适合满足应用程序和手头内容的特定安全需求的自定义授权模型。

* 将CUG策略支持的路径限制为存储库中的几个树，以便获得优化的性能。 例如，仅允许作为自AEM 6.3以来的默认值发运的/content节点下的CUG。
* CUG策略旨在授予对一小组主体的读取权限。 需要大量原则可能会突出内容或应用程序设计中的问题，并应重新考虑。

### 身份验证： 定义身份验证要求 {#authentication-defining-the-auth-requirement}

CUG功能的身份验证相关部分允许标记需要身份验证的树，并可选地指定专用登录页。 根据先前版本，新实现允许在内容存储库中标记需要验证的树，并有条件地启用与负责最终强 `Sling org.apache.sling.api.auth.Authenticator`制该要求和重定向到登录资源的同步。

通过提供注册属性的OSGi服务，向验证者注册这些 `sling.auth.requirements` 要求。 然后，这些属性用于动态扩展身份验证要求。 有关更多详细信息，请参 [阅Sling文档](https://sling.apache.org/apidocs/sling7/org/apache/sling/auth/core/AuthConstants.html#AUTH_REQUIREMENTS)。

#### 使用专用混音类型定义身份验证要求 {#defining-the-authentication-requirement-with-a-dedicated-mixin-type}

出于安全原因，新实现将剩余JCR属性的使用替换为名为的专用混音类型 `granite:AuthenticationRequired`，该类型为登录路径定义STRING类型的单个可选属性 `granite:loginPath`。 只有与此混合类型相关的内容更改才能更新向Apache Sling Authenticator注册的要求。 在保持任何临时修改时跟踪该修改，因此需要 `javax.jcr.Session.save()` 呼叫才能生效。

这同样适用于该 `granite:loginPath` 属性。 只有通过身份验证相关的混音类型定义，才会尊重它。 在非结构化JCR节点上添加具有此名称的剩余属性将不显示所需效果，负责更新OSGi注册的处理程序将忽略该属性。

>[!NOTE]
>
>设置登录路径属性是可选的，并且仅当需要身份验证的树无法返回到默认登录页面或以其他方式继承的登录页面时才需要。 请参阅下 [面的登录路径评估](/help/sites-administering/closed-user-groups.md#evaluation-of-login-path) 。

#### 向Sling Authenticator注册身份验证要求和登录路径 {#registering-the-authentication-requirement-and-login-path-with-the-sling-authenticator}

由于此类型的身份验证要求应限于某些运行模式以及内容存储库中的一小部分树，因此跟踪要求混合类型和登录路径属性是有条件的，并绑定到定义受支持路径的相应配置（请参阅下面的配置选项）。 因此，只有这些受支持路径范围内的更改才会触发OSGi注册的更新，其他位置将忽略mixin类型和属性。

默认的AEM安装程序现在允许在作者运行模式下设置混音，但只有在复制到发布实例后才会生效，从而利用此配置。 有关 [Sling如何实施](https://sling.apache.org/documentation/the-sling-engine/authentication/authenticationframework.html) 身份验证要求的详细信息，请参阅本页。

在已配 `granite:AuthenticationRequired` 置的支持路径中添加混音类型将导致更新负责处理程序的OSGi注册，该注册包含带有该属性的新的附加条 `sling.auth.requirements` 目。 如果给定的身份验证要求指定 `granite:loginPath` 了可选属性，则该值将附加地注册到验证器中，并带有“-”前缀，以便从身份验证要求中排除。

#### 认证要求的评价与继承 {#evaluation-and-inheritance-of-the-authentication-requirement}

Apache Sling身份验证要求应通过页面或节点层次结构进行继承。 继承和验证要求评估的详细信息（如顺序和优先级）被视为一个实施详细信息，本文中不予记录。

#### 登录路径评估 {#evaluation-of-login-path}

验证时对登录路径的评估并重定向到相应的资源当前是AdobeGranite登录选择器身份验证处理程序()的实现详细信息，该处理程序是默认配置为AEM的Apache Sling AuthenticationHandler。 `com.day.cq.auth.impl.LoginSelectorHandler`

调用此 `AuthenticationHandler.requestCredentials` 处理函数时，会尝试确定将用户重定向到的映射登录页面。 这包括以下步骤：

* 区分过期密码和需要定期登录作为重定向的原因；
* 如果是定期登录，则测试是否可以按以下顺序获得登录路径：

   * LoginPathProvider中的 `com.adobe.granite.auth.requirement.impl.RequirementService`,
   * 从旧的、已弃用的CUG实现，
   * 从登录页面映射(如 `LoginSelectorHandler`,
   * 最后，回退到默认登录页面，如中所定义 `LoginSelectorHandler`。

* 一旦通过上述呼叫获得了有效的登录路径，用户的请求将被重定向到该页面。

本文档的目标是评估内部界面所显示的登录路径 `LoginPathProvider` 。 自AEM 6.3起发运的实施如下所示：

* 登录路径的注册取决于对过期密码的区别，以及是否需要定期登录作为重定向的原因
* 如果是定期登录，则测试是否可以按以下顺序获得登录路径：

   * 从 `LoginPathProvider``com.adobe.granite.auth.requirement.impl.RequirementService`新的，
   * 从旧的、已弃用的CUG实现，
   * 从“登录页面映射”(定义 `LoginSelectorHandler`)
   * 最后，回退到使用定义的默认登录页面 `LoginSelectorHandler`。

* 一旦通过上述呼叫获得了有效的登录路径，用户的请求将被重定向到该页面。

由Granite `LoginPathProvider` 中新的身份验证要求支持实现的登录路径由属性定义，而属性 `granite:loginPath` 又由上述的混合类型定义。 保存登录路径和属性值本身的资源路径的映射将保留在内存中，并将被评估为为层次结构中的其他节点找到合适的登录路径。

>[!NOTE]
>
>仅对与配置的支持路径中的资源关联的请求执行评估。 对于任何其他请求，将评估确定登录路径的替代方法。

#### 最佳实践 {#best-practices-1}

在定义身份验证要求时，应考虑以下最佳实践：

* 避免嵌套身份验证要求： 在树的开始上放置单个身份验证要求标记应足够，并且继承到由目标节点定义的整个子树。 该树中的其他身份验证要求应被视为冗余，在评估Apache Sling中的身份验证要求时，可能会导致性能问题。 通过将授权和认证相关的CUG区域分开，可以通过CUG或其他类型的策略限制读访问，同时强制对整个树的认证。
* 建模存储库内容，使身份验证要求适用于整个树，无需再次从要求中排除嵌套子树。
* 要避免指定并随后注册冗余登录路径，请执行以下操作：

   * 依赖继承并避免定义嵌套登录路径，
   * 不要将可选登录路径设置为与默认值或继承值对应的值，
   * 应用程序开发人员应确定在与关联的全局登录路径配置（默认和映射）中应配置哪些登录路径 `LoginSelectorHandler`。

## 存储库中的表示法 {#representation-in-the-repository}

### 存储库中的CUG策略表示 {#cug-policy-representation-in-the-repository}

Oak文档涵盖新CUG策略在存储库内容中的反映方式。 有关详细信息，请 [参阅本页](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#Representation_in_the_Repository)。

### 存储库中的身份验证要求 {#authentication-requirement-in-the-repository}

在存储库内容中反映了对单独身份验证要求的需要，该内容中放置了位于目标节点的专用混合节点类型。 混合类型定义一个可选属性，用于为目标节点定义的树指定专用登录页。

与登录路径关联的页面可能位于该树的内部或外部。 它将被排除在身份验证要求之外。

```java
[granite:AuthenticationRequired]
      mixin
      - granite:loginPath (STRING)
```

## 管理CUG策略和身份验证要求 {#managing-cug-policies-and-authentication-requirement}

### 管理CUG策略 {#managing-cug-policies}

用于限制CUG读访问的新类型访问控制策略是使用JCR访问控制管理API管理的，并遵循JCR 2.0规 [范中描述的机制](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html)。

#### 设置新的CUG策略 {#set-a-new-cug-policy}

在以前没有CUG集的节点应用新CUG策略的代码。 请注意， `getApplicablePolicies` 将仅返回以前尚未设置的新策略。 最后，策略需要写回，并且更改需要保留。

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

AccessControlPolicyIterator it = acMgr.getApplicablePolicies(path);
while (it.hasNext()) {
        AccessControlPolicy policy = it.nextAccessControlPolicy();
        if (policy instanceof PrincipalSetPolicy) {
           cugPolicy = (PrincipalSetPolicy) policy;
           break;
        }
}

if (cugPolicy == null) {
   log.debug("no applicable policy"); // path not supported or no applicable policy (e.g.
                                                   // the policy was set before)
   return;
}

cugPolicy.addPrincipals(toAdd1, toAdd2);
cugPolicy.removePrincipals(toRemove));

acMgr.setPolicy(path, cugPolicy); // as of this step the policy can be edited/removed
session.save();
```

#### 编辑现有CUG策略 {#edit-an-existing-cug-policy}

编辑现有CUG策略需要以下步骤。 请注意，修改后的策略需要回写，并且更改需要使用保留 `javax.jcr.Session.save()`。

```java
String path = [...] // needs to be a supported, absolute path

Principal toAdd1 = [...]
Principal toAdd2 = [...]
Principal toRemove = [...]

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
     if (policy instanceof PrincipalSetPolicy) {
        cugPolicy = (PrincipalSetPolicy) policy;
        break;
     }
}

if (cugPolicy == null) {
   log.debug("no policy to edit"); // path not supported or policy not set before
   return;
}

if (cugPolicy.addPrincipals(toAdd1, toAdd2) || cugPolicy.removePrincipals(toRemove)) {
   acMgr.setPolicy(path, cugPolicy);
   session.save();
} else {
     log.debug("cug policy not modified");
}
```

### 检索有效的CUG策略 {#retrieve-effective-cug-policies}

JCR访问控制管理定义了一种检索在给定路径上生效的策略的最佳方法。 由于CUG策略的评估是有条件的，并且取决于要启用的相应配置，调用是验证给定CUG策 `getEffectivePolicies` 略是否在给定安装中生效的一种简便方法。

>[!NOTE]
>
>请注意在层次结 `getEffectivePolicies` 构中向上遍历的后续代码示例之间的差异，以查找给定路径是否已经属于现有CUG的一部分。

```java
String path = [...] // needs to be a supported, absolute path

AccessControlManager acMgr = session.getAccessControlManager();
PrincipalSetPolicy cugPolicy = null;

// log an debug message of all CUG policies that take effect at the given path
// there could be zero, one or many (creating nested CUGs is possible)
for (AccessControlPolicy policy : acMgr.getEffectivePolicies(path) {
     if (policy instanceof PrincipalSetPolicy) {
        String policyPath = "-";
        if (policy instanceof JackrabbitAccessControlPolicy) {
           policyPath = ((JackrabbitAccessControlPolicy) policy).getPath();
        }
        log.debug("Found effective CUG for path '{}' at '{}', path, policyPath);
     }
}
```

#### 检索继承的CUG策略 {#retrieve-inherited-cug-policies}

查找在给定路径中定义的所有嵌套CUG，而不管它们是否生效。 有关详细信息，请参 [阅配置选项](/help/sites-administering/closed-user-groups.md#configuration-options) 。

```java
String path = [...]

List<AccessControlPolicy> cugPolicies = new ArrayList<AccessControlPolicy>();
while (isSupportedPath(path)) {
     for (AccessControlPolicy policy : acMgr.getPolicies(path)) {
         if (policy instanceof PrincipalSetPolicy) {
            cugPolicies.add(policy);
         }
      }
      path = (PathUtils.denotesRoot(path)) ? null : PathUtils.getAncestorPath(path, 1);
}
```

#### 按Pincipal管理CUG策略 {#managing-cug-policies-by-pincipal}

CUG访问控制管理中 `JackrabbitAccessControlManager` 未实现允许按主体编辑访问控制策略的扩展，因为定义中，CUG策略始终会影响所有主体： 将授予与目标节 `PrincipalSetPolicy` 点一起列出的内容读取访问权限，同时将阻止所有其他主体读取由读取节点定义的树中的内容。

相应的方法始终返回空策略数组，但不会引发异常。

### 管理身份验证要求 {#managing-the-authentication-requirement}

通过改变目标节点的有效节点类型来实现新认证要求的创建、修改或移除。 然后，可以使用常规JCR API编写可选的登录路径属性。

>[!NOTE]
>
>如果已配置目标，且目标包含在受支持路径定义的树中，则上述对给定节点的修改 `RequirementHandler` 仅会反映在Apache Sling Authenticator上（请参阅配置选项一节）。
>
>有关详细信息，请参 [阅指定混合节点类型](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.10.3指定混合节点类型)和 [添加节点和设置属性](https://docs.adobe.com/docs/en/spec/jcr/2.0/10_Writing.html#10.4添加节点和设置属性)

#### 添加新的身份验证要求 {#adding-a-new-auth-requirement}

创建新身份验证要求的步骤详见下文。 请注意，仅当为包含目标节点的树配置了 `RequirementHandler` 该要求时，才会向Apache Sling Authenticator注册。

```java
Node targetNode = [...]

targetNode.addMixin("granite:AuthenticationRequired");
session.save();
```

#### 使用登录路径添加新的身份验证要求 {#add-a-new-auth-requirement-with-login-path}

创建新身份验证要求的步骤，包括登录路径。 请注意，只有为包含目标节点的树配置了Apache Sling Authenticator，才会向 `RequirementHandler` Apache Sling Authenticator注册登录路径的要求和排除。

```java
Node targetNode = [...]
String loginPath = [...] // STRING property

Node targetNode = session.getNode(path);
targetNode.addMixin("granite:AuthenticationRequired");

targetNode.setProperty("granite:loginPath", loginPath);
session.save();
```

#### 修改现有登录路径 {#modify-an-existing-login-path}

更改现有登录路径的步骤详见下文。 只有为包含目标节点的树配置了 `RequirementHandler` 修改后，才会向Apache Sling Authenticator注册。 之前的登录路径值将从注册中删除。 与目标节点关联的身份验证要求不受此修改的影响。

```java
Node targetNode = [...]
String newLoginPath = [...] // STRING property

if (targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", newLoginPath);
   session.save();
} else {
     log.debug("cannot modify login path property; mixin type missing");
}
```

#### 删除现有登录路径 {#remove-an-existing-login-path}

删除现有登录路径的步骤。 如果已为包含目标节点的树配置登录路径， `RequirementHandler` 则登录路径条目将仅从Apache Sling Authenticator注册。 与目标节点关联的身份验证要求不受影响。

```java
Node targetNode = [...]

if (targetNode.hasProperty("granite:loginPath") &&
   targetNode.isNodeType("granite:AuthenticationRequired")) {
   targetNode.setProperty("granite:loginPath", null);
   session.save();
} else {
     log.debug("cannot remove login path property; mixin type missing");
}
```

或者，您可以使用下面的方法来实现相同的目的：

```java
String path = [...] // absolute path to target node

String propertyPath = PathUtils.concat(path, "granite:loginPath");
if (session.propertyExists(propertyPath)) {
    session.getProperty(propertyPath).remove();
    // or: session.removeItem(propertyPath);
    session.save();
}
```

#### 删除身份验证要求 {#remove-an-auth-requirement}

删除现有身份验证要求的步骤。 如果为包含目标节点的树配置了， `RequirementHandler` 则只能从Apache Sling Authenticator中取消注册此要求。

```java
Node targetNode = [...]
targetNode.removeMixin("granite:AuthenticationRequired");

session.save();
```

#### 检索有效的身份验证要求 {#retrieve-effective-auth-requirements}

没有专用的公共API来读取向Apache Sling Authenticator注册的所有有效身份验证要求。 但是，列表会在系统控制台的“身份验 `https://<serveraddress>:<serverport>/system/console/slingauth` 证要求配&#x200B;**置”部分下公开**。

下图显示了包含演示内容的AEM发布实例的身份验证要求。 社区页的突出显示路径说明了本文档中所述实施所添加的要求如何反映在Apache Sling Authenticator中。

>[!NOTE]
>
>在此示例中，未设置可选登录路径属性。 因此，没有向验证器注册第二项。

![chlimage_1-62](assets/chlimage_1-62.jpeg)

#### 检索有效登录路径 {#retrieve-the-effective-login-path}

当前没有公共API可检索登录路径，该路径将在匿名访问需要身份验证的资源时生效。 有关如何检索登录路径的实现详细信息，请参阅登录路径评估部分。

但是，请注意，除了使用此功能定义的登录路径之外，还有其他方法可指定重定向到登录，在设计内容模型和给定AEM安装的身份验证要求时，应考虑这些方法。

#### 检索继承的身份验证要求 {#retrieve-the-inherited-auth-requirement}

与登录路径一样，没有公共API可检索内容中定义的继承身份验证要求。 以下示例说明如何列表已使用给定层次结构定义的所有身份验证要求，无论这些要求是否生效。 有关详细信息，请参阅 [配置选项](/help/sites-administering/closed-user-groups.md#configuration-options)。

>[!NOTE]
>
>建议使用继承机制满足身份验证要求和登录路径，并避免创建嵌套身份验证要求。
>
>有关详细信息， [请参阅验证要求的评估](#evaluation-and-inheritance-of-the-authentication-requirement)[和继承、登录路径的评](#evaluation-of-login-path) 估和最 [佳实践](#best-practices)。

```java
String path = [...]
Node node = session.getNode(path);

Map<String, String> authRequirements = new ArrayList<String, String>();
while (isSupported(node)) {
     if (node.isNodeType("granite:AuthenticationRequired")) {
         String loginPath = (node.hasProperty("granite:loginPath") ?
                                     node.getProperty("granite:loginPath").getString() :
                                     "";
        authRequirements.put(node.getPath(), loginPath);
        node = node.getParent();
     }
}
```

### 结合CUG策略和身份验证要求 {#combining-cug-policies-and-the-authentication-requirement}

下表列表了AEM实例中CUG策略的有效组合和身份验证要求，该实例通过配置同时启用了这两个模块。

| **需要身份验证** | **登录路径** | **受限读取访问** | **预期效果** |
|---|---|---|---|
| 是 | 是 | 是 | 如果有效权限评估授予访问权限，则给定用户只能视图用CUG策略标记的子树。 未通过身份验证的用户将被重定向到指定的登录页面。 |
| 是 | 否 | 是 | 如果有效权限评估授予访问权限，则给定用户只能视图用CUG策略标记的子树。 未通过身份验证的用户将被重定向到继承的默认登录页面。 |
| 是 | 是 | 否 | 未通过身份验证的用户将被重定向到指定的登录页面。 是否允许它视图标记有身份验证要求的树取决于该子树中包含的各个项目的有效权限。 没有专用CUG限制读取访问。 |
| 是 | 否 | 否 | 未通过身份验证的用户将被重定向到继承的默认登录页面。 是否允许它视图带有身份验证要求的树取决于该子树中包含的各个项目的有效权限。 没有专用CUG限制读取访问。 |
| 否 | 否 | 是 | 如果有效的权限评估授予访问权限，则给定的已验证或未验证的用户只能视图用CUG策略标记的子树。 未经身份验证的用户将得到同等对待，不会被重定向到登录。 |

>[!NOTE]
>
>上面未列出“身份验证要求”=“否”和“登录路径”=“是”的组合，因为“登录路径”是与身份验证要求关联的可选属性。 指定不添加定义混音类型而使用该名称的JCR属性将不起作用，并且相应的处理函数将忽略该属性。

## OSGi组件和配置 {#osgi-components-and-configuration}

本节概述了OSGi组件以及新CUG实现中引入的各个配置选项。

另请参阅CUG映射文档，以全面映射旧实施和新实施之间的配置选项。

### 授权： 设置和配置 {#authorization-setup-and-configuration}

新的授权相关部件包含在 **Oak CUG授权包** ( `org.apache.jackrabbit.oak-authorization-cug`)中，它是AEM默认安装的一部分。 该绑定定义了一个分离的授权模型，该模型旨在作为管理读访问的一种附加方式进行部署。

#### 设置CUG授权 {#setting-up-cug-authorization}

相关Apache文档中详细介绍了设置CUG [授权的过程](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability)。 默认情况下，AEM在所有运行模式下都部署了CUG授权。 该分步指令还可用于在那些需要不同授权设置的安装中禁用CUG授权。

#### 配置推荐人筛选器 {#configuring-the-referrer-filter}

您还需要配置Sling [推荐人筛选器](/help/sites-administering/security-checklist.md#the-sling-referrer-filter) ，以及可能用于访问AEM的所有主机名； 例如，通过CDN、负载平衡器等进行。

如果未配置推荐人过滤器，则当用户尝试登录CUG站点时，将看到与以下内容类似的错误：

```shell
31.01.2017 13:49:42.321 *INFO* [qtp1263731568-346] org.apache.sling.security.impl.ReferrerFilter Rejected referrer header for POST request to /libs/granite/core/content/login.html/j_security_check : https://hostname/libs/granite/core/content/login.html?resource=%2Fcontent%2Fgeometrixx%2Fen%2Ftest-site%2Ftest-page.html&$$login$$=%24%24login%24%24&j_reason=unknown&j_reason_code=unknown
```

#### OSGi组件的特性 {#characteristics-of-osgi-components}

已引入以下两个OSGi组件来定义身份验证要求和指定专用登录路径：

* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration`
* `org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl`

**org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugConfiguration**

<table> 
 <tbody> 
  <tr> 
   <td>标签</td> 
   <td>Apache Jackrabbit Oak CUG配置</td> 
  </tr> 
  <tr> 
   <td>描述</td> 
   <td>专用于设置和评估CUG权限的授权配置。</td> 
  </tr> 
  <tr> 
   <td>配置属性</td> 
   <td> 
    <ul> 
     <li><code>cugSupportedPaths</code></li> 
     <li><code>cugEnabled</code></li> 
     <li><code>configurationRanking</code></li> 
    </ul> <p>另请参阅下 <a href="/help/sites-administering/closed-user-groups.md#configuration-options" target="_blank">面的配置</a> 选项。</p> </td> 
  </tr> 
  <tr> 
   <td>配置策略</td> 
   <td><code>ConfigurationPolicy.REQUIRE</code></td> 
  </tr> 
  <tr> 
   <td>引用</td> 
   <td><code>CugExclude (ReferenceCardinality.OPTIONAL_UNARY)</code></td> 
  </tr> 
 </tbody> 
</table>

**org.apache.jackrabbit.oak.spi.security.authorization.cug.impl.CugExcludeImpl**

<table> 
 <tbody> 
  <tr> 
   <td>标签</td> 
   <td>Apache Jackrabbit Oak CUG排除列表</td> 
  </tr> 
  <tr> 
   <td>描述</td> 
   <td>允许从CUG评估中排除配置名称的主体。</td> 
  </tr> 
  <tr> 
   <td>配置属性</td> 
   <td> 
    <ul> 
     <li><code>principalNames</code></li> 
    </ul> <p>另请参阅下面的配置选项一节。</p> </td> 
  </tr> 
  <tr> 
   <td>配置策略</td> 
   <td><code>ConfigurationPolicy.REQUIRE</code></td> 
  </tr> 
  <tr> 
   <td>引用</td> 
   <td>NA</td> 
  </tr> 
 </tbody> 
</table>

#### Configuration Options {#configuration-options}

主要配置选项有：

* `cugSupportedPaths`: 指定可能包含CUG的子树。 未设置默认值
* `cugEnabled`: 配置选项，以启用对当前CUG策略的权限评估。

Apache Oak Documentation中列出了与CUG授权模块相关的可用配置选项，并对其进 [行了详细说明](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#configuration)。

#### 从CUG评估中排除承担者 {#excluding-principals-from-cug-evaluation}

在前一个实施中，个人负责人免于进行CUG评估。 新的CUG授权通过一个名为CugExclude的专用接口覆盖此权限。 Apache Jackrabbit Oak 1.4附带默认实现，该实现不包括固定的主体集以及允许配置单个主体名称的扩展实现。 后者是在AEM发布实例中配置的。

自AEM 6.3以来的默认值可防止以下承担者受到CUG策略的影响：

* 管理主体（管理员用户、管理员组）
* 服务用户主体
* 存储库内部系统主体

有关详细信息，请参阅下面“自AEM 6.3 [以来的默认配置”部分](#default-configuration-since-aem) 中的表。

在Apache Jackrabbit Oak CUG排除列表的配置部分的系统控制台中，可以更改或扩 **展“管理员”组的排除**。

或者，可以提供和部署CugExclude接口的自定义实现，以根据特殊需要调整被排除的承担者集。 有关详细信息 [和示例实](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) 施，请参阅CUG可插件相关文档。

### 身份验证： 设置和配置 {#authentication-setup-and-configuration}

新的与身份验证相关的部件包含在 **AdobeGranite Authentication** Handler包 `com.adobe.granite.auth.authhandler` 中（版本5.6.48）。 此捆绑包是AEM默认安装的一部分。

为了为已弃用的CUG支持设置身份验证要求替换，在给定的AEM安装中，必须存在某些OSGi组件并且它们处于活动状态。 有关详细信息，请 **参阅以下OSGi组件的** 特性。

>[!NOTE]
>
>由于RequirementHandler的强制配置选项，仅当通过指定一组受支持的路径启用了该功能时，验证相关部分才会处于活动状态。 在标准AEM安装中，该功能在作者运行模式下处于禁用状态，在发布运行模式下处于/content启用状态。

**OSGi组件的特性**

已引入以下2个OSGi组件来定义身份验证要求并指定专用登录路径：

* `com.adobe.granite.auth.requirement.impl.RequirementService`
* `com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler`

**com.adobe.granite.auth.requirement.impl.RequirementService**

<table> 
 <tbody> 
  <tr> 
   <td>标签</td> 
   <td>-</td> 
  </tr> 
  <tr> 
   <td>描述</td> 
   <td>用于验证要求的专用OSGi服务，该服务将观察器注册到影响验证要求的内容更改(通过混 <code>granite:AuthenticationRequirement</code> 合类型)和登录路径暴露给该 <code>LoginSelectorHandler</code>服务。 </td> 
  </tr> 
  <tr> 
   <td>配置属性</td> 
   <td>-</td> 
  </tr> 
  <tr> 
   <td>配置策略</td> 
   <td><code>ConfigurationPolicy.OPTIONAL</code></td> 
  </tr> 
  <tr> 
   <td>引用</td> 
   <td> 
    <ul> 
     <li><code>RequirementHandler (ReferenceCardinality.MANDATORY_UNARY)</code></li> 
     <li><code>Executor (ReferenceCardinality.MANDATORY_UNARY)</code></li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**com.adobe.granite.auth.requirement.impl.DefaultRequirementHandler**

| 标签 | AdobeGranite身份验证要求和登录路径处理程序 |
|---|---|
| 描述 | `RequirementHandler` 更新Apache Sling身份验证要求以及相关登录路径的相应排除的实现。 |
| 配置属性 | `supportedPaths` |
| 配置策略 | `ConfigurationPolicy.REQUIRE` |
| 引用 | NA |

#### Configuration Options {#configuration-options-1}

CUG重写的身份验证相关部分只附带与AdobeGranite身份验证要求和登录路径处理程序关联的单个配置选项：

**&quot;身份验证要求和登录路径处理程序&quot;**

<table> 
 <tbody> 
  <tr> 
   <td>属性</td> 
   <td>类型</td> 
   <td>默认值</td> 
   <td>描述</td> 
  </tr> 
  <tr> 
   <td><p>标签=支持的路径</p> <p>名称= 'supportedPaths'</p> </td> 
   <td>Set&lt;String&gt;</td> 
   <td>-</td> 
   <td>此处理程序将遵守身份验证要求的路径。 如果要将混合类型添加到节点而不强制 <code>granite:AuthenticationRequirement</code> 执行这些类型（例如，在创作实例上），请取消设置此配置。 如果缺失，则禁用该功能。 </td> 
  </tr> 
 </tbody> 
</table>

## AEM 6.3之后的默认配置 {#default-configuration-since-aem}

默认情况下，新安装的AEM将使用新的实现来进行CUG功能的授权和身份验证相关部分。 旧实现“AdobeGranite已关闭的用户组(CUG)支持”已弃用，默认情况下将在所有AEM安装中禁用。 新实施将改为启用，如下所示：

### 作者实例 {#author-instances}

| **&quot;Apache Jackrabbit Oak CUG配置&quot;** | **说明** |
|---|---|
| 支持的路径 `/content` | 已启用CUGpolicies的访问控制管理。 |
| 启用CUG评估为FALSE | 权限评估已禁用。 CUG策略无效。 |
| 等级 | 200 | 请参阅Oak文档。 |

>[!NOTE]
>
>默认创作 **实例中不存在Apache Jackrabbit Oak CUG Exclude列表****和AdobeGranite身份验证要求和登录路径处理** 程序的配置。

### 发布实例 {#publish-instances}

| **&quot;Apache Jackrabbit Oak CUG配置&quot;** | **说明** |
|---|---|
| 支持的路径 `/content` | CUG策略的访问控制管理在配置路径下启用。 |
| 启用CUG评估 | 在配置的路径下启用权限评估。 CUG策略生效 `Session.save()`。 |
| 等级 | 200 | 请参阅Oak文档。 |

| **&quot;Apache Jackrabbit Oak CUG排除列表&quot;** | **说明** |
|---|---|
| 主体名称管理员 | 从CUG评估中不包括管理员主体。 |

| **“AdobeGranite身份验证要求和登录路径处理程序”** | **说明** |
|---|---|
| 支持的路径  `/content` | 通过混合类型在存储库中定义的身份验证 `granite:AuthenticationRequired` 要求将在以下时 `/content` 生效 `Session.save()`。 Sling Authenticator将更新。 将忽略在支持的路径之外添加混音类型。 |

## 禁用CUG授权和身份验证要求 {#disabling-cug-authorization-and-authentication-requirement}

当给定安装不使用CUG或使用不同的方法进行身份验证和授权时，可以完全禁用新实现。

### 禁用CUG授权 {#disable-cug-authorization}

有关如何 [从复合授权设置](https://jackrabbit.apache.org/oak/docs/security/authorization/cug.html#pluggability) 中删除CUG授权模型的详细信息，请查阅CUG可插件文档。

### 禁用身份验证要求 {#disable-the-authentication-requirement}

为了禁用对模块提供的身份验证要求的支 `granite.auth.authhandler` 持，完全可以删除与AdobeGranite身份验证要求和登录路径 **处理程序相关的配置**。

>[!NOTE]
>
>但是，请注意，删除配置不会取消注册混合类型，该类型仍适用于节点，但不会生效。

## 与其他模块的交互 {#interaction-with-other-modules}

### Apache Jackrabbit API {#apache-jackrabbit-api}

为了反映CUG授权模型使用的新型访问控制策略，扩展了Apache Jackrabbit定义的API。 由于模块的版本2.11.0定义 `jackrabbit-api` 了一个名为的新接口， `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy`该接口从扩展 `javax.jcr.security.AccessControlPolicy`。

### Apache Jackrabbit FileVault {#apache-jackrabbit-filevault}

Apache Jackrabbit FileVault的导入机制已调整为处理类型的访问控制策略 `PrincipalSetPolicy`。

### Apache Sling内容分发 {#apache-sling-content-distribution}

请参阅上 [面的Apache Jackrabbit FileVault](/help/sites-administering/closed-user-groups.md#apache-jackrabbit-filevault) 部分。

### AdobeGranite复制 {#adobe-granite-replication}

为了能够在不同AEM实例之间复制CUG策略，复制模块稍作调整：

* `DurboImportConfiguration.isImportAcl()` 是字面解释的，只会影响访问控制政策的实施 `javax.jcr.security.AccessControlList`

* `DurboImportTransformer` 将仅对真正的ACL遵守此配置
* 其他策略( `org.apache.jackrabbit.api.security.authorization.PrincipalSetPolicy` 如由CUG授权模型创建的实例)将始终被复制，并且 `DurboImportConfiguration.isImportAcl`将忽略配置选项()。

复制CUG策略存在一个限制。 如果在删除相应的混合节点类型的情况下删除了给定的CUG策 `rep:CugMixin,` 略，则复制时不会反映删除。 已通过始终在删除策略时删除混音来解决此问题。 但是，如果手动添加混音类型，则可能会显示该限制。

### AdobeGranite身份验证处理程序 {#adobe-granite-authentication-handler}

捆绑包附带 **的AdobeGranite HTTP Header Authentication** Handler的验证处理 `com.adobe.granite.auth.authhandler` 函数保留对由同一模块定义 `CugSupport` 的接口的引用。 它用于在某些情况下计算“领域”，并返回到使用处理函数配置的领域。

已调整此参数，以使引用为可选 `CugSupport` 的，以确保在给定设置决定重新启用已弃用的实现时最大的向后兼容性。 使用该实现的安装将不再获取从CUG实现提取的领域，但将始终显示使用 **AdobeGranite HTTP Header Authentication Handler定义的领域**。

>[!NOTE]
>
>默认情况下， **AdobeGranite HTTP Header Authentication** Handler仅在启用“禁用登录页”()选项的发布运行模式 `auth.http.nologin`下配置。

### AEM LiveCopy {#aem-livecopy}

通过添加一个额外节点和一个额外属性来表示与LiveCopy相结合的CUG，如下所示：

* `/content/we-retail/us/en/blueprint/rep:cugPolicy`
* `/content/we-retail/us/en/LiveCopy@granite:loginPath`

这两个元素都在下面创建 `cq:Page`。 在当前设计中，MSM仅处理位于()节点下的节 `cq:PageContent` 点和`jcr:content`属性。

因此，CUG组无法从Blueprint回滚到Live Copy。 在设置Live Copy时，请相应地计划。

## 新CUG实施中的更改 {#changes-with-the-new-cug-implementation}

本节旨在概述对CUG功能所做的更改，以及新旧实施之间的比较。 它列表影响CUG支持配置方式的更改，并描述如何在存储库内容中管理CUG以及由谁管理CUG。

### CUG设置和配置的差异 {#diferences-in-cug-setup-and-configuration}

已弃用的OSGi **组件AdobeGranite Closed User Group** (CUG)Support `com.day.cq.auth.impl.cug.CugSupportImpl`()已被新组件所取代，以便能够单独处理以前CUG功能的授权和身份验证相关部分。

## 在管理存储库内容中的CUG方面的差异 {#differences-in-managing-cugs-in-the-repository-content}

以下各节从实施和安全性角度介绍了新旧实施之间的差异。 虽然新实现旨在提供相同的功能，但在使用新CUG时，需要了解一些细微的更改。

### 授权方面的差异 {#diferences-with-regards-to-authorization}

授权方面的主要差异在以下列表中总结：

**CUG专用访问控制内容**

在旧的实现中，默认授权模型用于在发布时操作访问控制列表策略，由CUG授权的设置替换任何现有ACE。 这是由编写常规的、剩余的JCR属性触发的，这些属性在发布时进行解释。

在新的实施中，默认授权模型的访问控制设置不会受到创建、修改或删除的任何CUG的影响。 而是将名为的新类型的策 `PrincipalSetPolicy` 略作为附加访问控制内容应用于目标节点。 此附加策略将作为目标节点的子项，并且如果存在，将作为默认策略节点的同级。

**在访问控制管理中编辑CUG策略**

从剩余的JCR属性移动到专用访问控制策略会影响创建或修改CUG功能授权部分所需的权限。 由于这被视为对访问控制内容的修改，因此它 `jcr:readAccessControl` 需要 `jcr:modifyAccessControl` 和权限才能写入存储库。 因此，只有有权修改页面访问控制内容的内容作者才能设置或修改此内容。 这与以前的实施形成鲜明对比，当时编写常规JCR属性的能力已足够，从而导致权限提升。

**目标节点由策略定义**

应在JCR节点创建CUG策略，该节点定义要受受限读取访问的子树。 这可能是AEM页面，以防CUG影响整个树。

请注意，将CUG策略仅放在位于给定页面下方的jcr:content节点将仅限于访问给定页面的内容，但不会对任何同级或子页面生效。 这可能是一个有效的用例，并且可以通过允许应用细粒度访问内容的存储库编辑器来实现。 但是，它对比了前一个实现，即在jcr:content节点上放置cq:cugEnabled属性是在内部重新映射到页面节点的。 不再执行此映射。

**使用CUG策略的权限评估**

从旧的CUG支持转向其他授权模型，改变评估有效读取权限的方式。 如Jackrabbit文档中 [所述](https://jackrabbit.apache.org/oak/docs/security/authorization/composite.html)，只有在Oak存储库中配置的所有型号的权限评估授予读访问权限 `CUGcontent` 时，才会授予允许视图该模型的给定主体读取权限。

换言之，在评估有效权限时，将同时考虑 `CUGPolicy` 访问控制条目和默认的访问条目，并且仅在两种策略都授予CUG内容读取权限时，才授予对CUG内容的读取权限。 在默认的AEM发布安装中，每个人都 `/content` 有权读取完整树，CUG策略的效果将与旧实施的效果相同。

**按需评估**

CUG授权模型允许单独开启访问控制管理和权限评估：

* 如果模块具有一个或多个可创建CUG的支持路径，则启用访问控制管理
* 仅当另外选中“启用CUG评估 **”选项时** ，才启用权限评估。

在新的AEM默认设置CUG策略评估中，它仅启用“发布”运行模式。 有关更多详细信 [息，请参阅AEM 6.3后默认配置](#default-configuration-since-aem) 的详细信息。 这可以通过比较给定路径的有效策略与存储在内容中的策略来验证。 只有启用CUG的权限评估后，才会显示有效策略。

如上所述，CUG访问控制策略现在始终存储在内容中，但仅当在Apache Jackrabbit Oak CUG配置的系统控制台中打开“启用 **CUG评估** ”时，才会强制执行对这些策略产生的有效权 **限的评估。** 默认情况下，它仅启用“发布”运行模式。

### 身份验证方面的差异 {#differences-with-regards-to-authentication}

与身份验证相关的差异如下所述。

#### 用于验证要求的专用混合类型 {#dedicated-mixin-type-for-authentication-requirement}

在前一个实现中，CUG的授权和验证方面都由单个JCR属性( `cq:cugEnabled`)触发。 就身份验证而言，这会导致与Apache Sling Authenticator实现一起存储的身份验证要求的更新列表。 在新的实现中，通过用专用混合类型()标记目标节点来实现相同的 `granite:AuthenticationRequired`结果。

#### 排除登录路径的属性 {#property-for-excluding-login-path}

mixin类型定义一个名为的可选属性， `granite:loginPath`该属性基本上与该属性 `cq:cugLoginPage` 对应。 与以前的实现不同，只有在其声明节点类型为所述混音时，登录路径属性才会受到尊重。 在不设置混音类型的情况下添加具有该名称的属性将不起作用，不会向验证器报告对登录路径的新要求或排除。

#### 身份验证要求的权限 {#privilege-for-authentication-requirement}

添加或删除混音类型需要 `jcr:nodeTypeManagement` 授予权限。 在前一个实现中， `jcr:modifyProperties` 权限用于编辑剩余属性。

就属性而 `granite:loginPath` 言，添加、修改或删除属性时需要相同的权限。

#### 目标节点由混合类型定义 {#target-node-defined-by-mixin-type}

身份验证要求应在JCR节点创建，该节点定义要受强制登录的子树。 如果CUG预计会影响整个树，则这可能是AEM页面，而新实现的UI将随后在页面节点上添加身份验证要求混合类型。

将CUG策略仅放置在给定页面下方的jcr:content节点上将仅限访问内容，但不会影响页面节点本身或任何子页面。

这可能是有效的方案，并且可以使用允许将混音放置到任何节点的存储库编辑器。 但是，该行为与前一个实现形成了对比，在前一个实现中，将cq:cugEnabled或cq:cugLoginPage属性放置到jcr:content节点上会在内部重新映射到页面节点。 不再执行此映射。

#### 已配置的支持路径 {#configured-supported-paths}

mixin类 `granite:AuthenticationRequired` 型和granite:loginPath属性将仅在AdobeGranite身份验证要求和登录路径处理程序提供的 **受支持路径** 配置选项集定义的 **范围内得到尊重**。 如果未指定路径，则完全禁用身份验证要求功能。 在这种情况下，在添加或设置给定JCR节点时，混合类型或属性将生效。

### JCR内容、OSGi服务和配置的映射 {#mapping-of-jcr-content-osgi-services-and-configurations}

以下文档提供了旧实施和新实施之间OSGi服务、配置和存储库内容的全面映射。

自AEM 6.3以来的CUG映射

[获取文件](assets/cug-mapping.pdf)

## 升级CUG {#upgrade-cug}

### 使用已弃用的CUG的现有安装 {#existing-installations-using-the-deprecated-cug}

旧的CUG支持实施已弃用，将在将来的版本中删除。 从AEM 6.3以前的版本升级时，建议转到新的实现。

对于升级的AEM安装，确保只启用一个CUG实施非常重要。 新的和已弃用的旧CUG支持的组合未经过测试，可能会导致不期望的行为：

* Sling Authenticator中与身份验证要求的冲突
* 当与旧CUG关联的ACL设置与新CUG策略冲突时，拒绝读取访问。

### 迁移现有CUG内容 {#migrating-existing-cug-content}

Adobe为迁移到新CUG实施提供了工具。 要使用它，请执行以下步骤：

1. 转到 `https://<serveraddress>:<serverport>/system/console/cug-migration` 访问该工具。
1. 输入要检查CUG的根路径，然后按“Perform **dry run** （执行练习）”按钮。 这将扫描所选位置中符合转换条件的CUG。
1. 查看结果后，按“Perform migration **** （执行迁移）”按钮迁移到新实现。

>[!NOTE]
>
>如果遇到问题，可以在DEBUG级别设置特 **定记录** 器 `com.day.cq.auth.impl.cug` ，以获得迁移工具的输出。 有关 [如何执](/help/sites-deploying/configure-logging.md) 行此操作的详细信息，请参阅日志记录。

