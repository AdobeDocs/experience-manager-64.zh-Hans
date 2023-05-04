---
title: 配置LDAP绑定密码
seo-title: Configure the LDAP bind password
description: 了解如何在将配置文件导入其他系统之前配置绑定密码字段。
seo-description: Learn how to configure the bind password field before you import the configuration file into another system.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
exl-id: eaa2c889-d116-4209-9063-0c0b32dd8849
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 2%

---

# 配置LDAP绑定密码{#configure-the-ldap-bind-password}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

为避免安全风险，未配置导出配置文件(config.xml)中的绑定密码字段。 在将配置文件导入其他系统之前，请确保配置此密码。 此密码将覆盖存储在数据库中的现有密码。 空密码不会覆盖现有的非空密码值。

1. 在管理控制台中，单击设置>用户管理>配置>导入和导出配置文件。
1. 要将当前配置设置导出到文件，请单击“导出”，然后将配置文件保存到其他位置。
1. 在文件中，找到 `Domains` > *[您的域名]* > `DirectoryConfigs` > `LDAPGroupConfig` 节点。 示例如下：

   ```as3
    <node name="LDAPGroupConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="batchSize" value="200" />  
            <entry key="binduser" value="cn=Directory Manager" />  
            <entry key="bindpassword" value="" /> 
        </map>
   ```

   键入的值 `bindpassword` 并保存更改。

1. 在文件中，找到 `Domains` > *[您的域名]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig` 节点。 示例如下：

   ```as3
    <node name="LDAPUserConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="batchSize" value="200" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="bindpassword" value="" /> 
            <entry key="binduser" value="cn=Directory Manager" />  
        </map>
   ```

   键入的值 `bindpassword` 并保存更改。

1. 要导入更新的文件，请在“用户管理”中，单击配置>导入和导出配置文件。
1. 单击“浏览”(Browse)查找文件，单击“导入”(Import)，然后单击“确定”(OK)。
