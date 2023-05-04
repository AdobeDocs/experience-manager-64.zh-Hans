---
title: 配置AEM表单以预取域信息
seo-title: Configure AEM forms to prefetchdomain information
description: 如果由于深度嵌套的组而导致响应时间变长，或者您是许多组的成员，请配置AEM表单以预取域信息。
seo-description: Configure AEM forms to prefetch domain information if you experience a slower response time due to deeply nested groups or if you are a member of many groups.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
exl-id: 6b431cbd-2cea-4ae2-ad26-587ba524d2f5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 2%

---

# 配置AEM表单以预取域信息 {#configure-aem-forms-to-prefetchdomain-information}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

如果用户属于多个组（例如，500个或更多组），或者如果这些组深度嵌套（例如，30个级别），则响应时间可能会变慢。 如果您遇到此问题，可以配置AEM表单以从某些域预取信息。

1. 在管理控制台中，单击 **[!UICONTROL 设置>用户管理>配置>导入和导出配置文件]**.
1. 要将当前配置设置导出到文件，请单击 **[!UICONTROL 导出]** 并将配置文件保存到其他位置。
1. 添加以下节点（以粗体标记）：

   ```as3
    <node name="UM"> 
    <map/>  
    <node name="PrincipalCache"> 
        <map> 
            <entry key="principalCacheSize" value="1000"/> 
            <entry key="principalCacheBatchFetchSize" value="10"/> 
            <entry key="rebuildCacheAfterSync" value="true /> 
            <entry key="enableFullPrefetch" value="false"/> 
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/> 
        <map> 
    </node> 
    <node name="APSAuditService">
   ```

   在此示例中，配置了多个用于预取的域。 域名以“/”分隔。 如上例所示， *Domain_Name1*, *Domain_Name2*&#x200B;和 *Domain_Name3*.

1. 要导入更新的文件，请在“用户管理”中，单击 **[!UICONTROL 配置>导入和导出配置文件]**.
1. 单击 **[!UICONTROL 浏览]** 要查找文件，请单击“导入”，然后单击 **[!UICONTROL 确定]**.
