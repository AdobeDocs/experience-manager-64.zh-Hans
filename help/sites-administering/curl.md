---
title: 将cURL与AEM结合使用
seo-title: Using cURL with AEM
description: 了解如何将cURL与AEM结合使用。
seo-description: Learn how to use cURL with AEM.
uuid: 771b9acc-ff3a-41c9-9fee-7e5d2183f311
contentOwner: Silviu Raiman
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: d4ceb82e-2889-4507-af22-b051af83be38
exl-id: 97120959-0a45-46b8-a10d-68522ad6f81a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 2%

---

# 将cURL与AEM结合使用{#using-curl-with-aem}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

管理员通常需要自动执行或简化任何系统中的常见任务。 例如，在AEM中，管理用户、安装包和管理OSGi包都是通常必须完成的任务。

由于构建AEM的Sling框架具有RESTful性质，因此大多数任务都可以通过URL调用完成。 cURL可用于执行此类URL调用，并且对于AEM管理员而言，它也是一个有用的工具。

## 什么是cURL {#what-is-curl}

cURL是用于执行URL操作的开源命令行工具。 它支持多种互联网协议，包括HTTP、HTTPS、FTP、FTPS、SCP、SFTP、TFTP、LDAP、DAP、DICT、TELNET、FILE、IMAP、POP3、SMTP和RTSP。

cURL是一款使用URL语法获取或发送数据的成熟且广泛使用的工具，最初于1997年发布。 名称cURL最初意为“see URL”。

由于构建AEM的Sling框架具有RESTful性质，因此大多数任务都可简化为URL调用，该调用可以使用cURL执行。 [内容处理任务](/help/sites-administering/curl.md#common-content-manipulation-aem-curl-commands) 例如激活页面、启动工作流以及 [操作任务](/help/sites-administering/curl.md#common-operational-aem-curl-commands) 使用cURL可以自动执行包管理和管理用户等操作。 此外，您还可以 [创建您自己的cURL](/help/sites-administering/curl.md#building-a-curl-ready-aem-command) 中的大多数任务。

>[!NOTE]
>
>任何通过cURL执行的AEM命令都必须像任何用户一样获得AEM的授权。 使用cURL执行AEM命令时，将遵守所有ACL和访问权限。

## 下载cURL {#downloading-curl}

cURL是macOS和某些Linux Distros的标准部分。 但是，它适用于大多数操作系统。 最新下载可在 [https://curl.haxx.se/download.html](https://curl.haxx.se/download.html).

cURL的源存储库也可以在GitHub上找到。

## 构建cURL就绪AEM命令 {#building-a-curl-ready-aem-command}

可以为AEM中的大多数操作（如触发工作流、检查OSGi配置、触发JMX命令、创建复制代理等）构建cURL命令。

要查找特定操作所需的确切命令，您需要使用浏览器中的开发人员工具，在执行AEM命令时捕获对服务器的POST调用。

以下步骤描述如何以在Chrome浏览器中创建新页面为例执行此操作。

1. 准备要在AEM中调用的操作。 在本例中，我们已进入 **创建页面** 向导，但尚未单击 **创建**.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. 启动开发人员工具并选择 **网络** 选项卡。 单击 **保留日志** 选项。

   ![chlimage_1-67](assets/chlimage_1-67.png)

1. 单击 **创建** 在 **创建页面** 向导来实际创建工作流。
1. 右键单击生成的POST操作，然后选择 **复制** -> **复制为cURL**.

   ![chlimage_1-68](assets/chlimage_1-68.png)

1. 将cURL命令复制到文本编辑器，并从命令中删除所有标题（以开头） `-H` （在下图中以蓝色突出显示），并添加正确的身份验证参数，例如 `-u <user>:<password>`.

   ![chlimage_1-69](assets/chlimage_1-69.png)

1. 通过命令行执行cURL命令并查看响应。

   ![chlimage_1-70](assets/chlimage_1-70.png)

## 常见操作AEM cURL命令 {#common-operational-aem-curl-commands}

以下是常见管理和操作任务的AEM cURL命令列表。

>[!NOTE]
>
>以下示例假定AEM在 `localhost` 端口 `4502` 和使用用户 `admin` 密码 `admin`. 其他命令占位符在尖括号中设置。

### 包管理 {#package-management}

#### 列出所有已安装的包

```shell
curl -u <user>:<password> http://<host>:<port>/crx/packmgr/service.jsp?cmd=ls
```

#### 创建资源包 {#create-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=create -d packageName=<name> -d groupName=<name>
```

#### 预览包 {#preview-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=preview
```

#### 列出包内容 {#list-package-content}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/console.html/etc/packages/mycontent.zip?cmd=contents
```

#### 构建包 {#build-a-package}

```shell
curl -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=build
```

#### 重新包装包 {#rewrap-a-package}

```shell
curl -u <user>:<password> -X POST http://localhost:4502/crx/packmgr/service/.json/etc/packages/mycontent.zip?cmd=rewrap
```

#### 重命名包 {#rename-a-package}

```shell
curl -u <user>:<password> -X POST -Fname=<New Name> http://localhost:4502/etc/packages/<Group Name>/<Package Name>.zip/jcr:content/vlt:definition
```

#### 上传包 {#upload-a-package}

```shell
curl -u <user>:<password> -F cmd=upload -F force=true -F package=@test.zip http://localhost:4502/crx/packmgr/service/.json
```

#### 安装包 {#install-a-package}

```shell
curl -u <user>:<password> -F cmd=install http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### 卸载包 {#uninstall-a-package}

```shell
curl -u <user>:<password> -F cmd=uninstall http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### 删除资源包 {#delete-a-package}

```shell
curl -u <user>:<password> -F cmd=delete http://localhost:4502/crx/packmgr/service/.json/etc/packages/my_packages/test.zip
```

#### 下载包 {#download-a-package}

```shell
curl -u <user>:<password> http://localhost:4502/etc/packages/my_packages/test.zip
```

### 用户管理 {#user-management}

#### 创建新用户 {#create-a-new-user}

```shell
curl -u <user>:<password> -FcreateUser= -FauthorizableId=hashim -Frep:password=hashim http://localhost:4502/libs/granite/security/post/authorizables
```

#### 创建新群组 {#create-a-new-group}

```shell
curl -u <user>:<password> -FcreateGroup=group1 -FauthorizableId=testGroup1 http://localhost:4502/libs/granite/security/post/authorizables
```

#### 向现有用户添加属性 {#add-a-property-to-an-existing-user}

```shell
curl -u <user>:<password> -Fprofile/age=25 http://localhost:4502/home/users/h/hashim.rw.html
```

#### 使用配置文件创建用户 {#create-a-user-with-a-profile}

```shell
curl -u <user>:<password> -FcreateUser=testuser -FauthorizableId=hashimkhan -Frep:password=hashimkhan -Fprofile/gender=male http://localhost:4502/libs/granite/security/post/authorizables
```

#### 将新用户创建为组的成员 {#create-a-new-user-as-a-member-of-a-group}

```shell
curl -u <user>:<password> -FcreateUser=testuser -FauthorizableId=testuser -Frep:password=abc123 -Fmembership=contributor http://localhost:4502/libs/granite/security/post/authorizables
```

#### 将用户添加到群组 {#add-a-user-to-a-group}

```shell
curl -u <user>:<password> -FaddMembers=testuser1 http://localhost:4502/home/groups/t/testGroup.rw.html
```

#### 从群组中删除用户 {#remove-a-user-from-a-group}

```shell
curl -u <user>:<password> -FremoveMembers=testuser1 http://localhost:4502/home/groups/t/testGroup.rw.html
```

#### 设置用户的群组成员资格 {#set-a-user-s-group-membership}

```shell
curl -u <user>:<password> -Fmembership=contributor -Fmembership=testgroup http://localhost:4502/home/users/t/testuser.rw.html
```

#### 删除用户 {#delete-a-user}

```shell
curl -u <user>:<password> -FdeleteAuthorizable= http://localhost:4502/home/users/t/testuser
```

#### 删除群组 {#delete-a-group}

```shell
curl -u <user>:<password> -FdeleteAuthorizable= http://localhost:4502/home/groups/t/testGroup
```

### 备份 {#backup}

请参阅 [备份和恢复](/help/sites-administering/backup-and-restore.md#automating-aem-online-backup) 以了解详细信息。

### OSGi {#osgi}

#### 启动包 {#starting-a-bundle}

```shell
curl -u <user>:<password> -Faction=start http://localhost:4502/system/console/bundles/<bundle-name>
```

#### 停止捆绑包 {#stopping-a-bundle}

```shell
curl -u <user>:<password> -Faction=stop http://localhost:4502/system/console/bundles/<bundle-name>
```

### Dispatcher {#dispatcher}

#### 使缓存失效 {#invalidate-the-cache}

```shell
curl -H "CQ-Action: Activate" -H "CQ-Handle: /content/test-site/" -H "CQ-Path: /content/test-site/" -H "Content-Length: 0" -H "Content-Type: application/octet-stream" http://localhost:4502/dispatcher/invalidate.cache
```

#### 逐出缓存 {#evict-the-cache}

```shell
curl -H "CQ-Action: Deactivate" -H "CQ-Handle: /content/test-site/" -H "CQ-Path: /content/test-site/" -H "Content-Length: 0" -H "Content-Type: application/octet-stream" http://localhost:4502/dispatcher/invalidate.cache
```

### 复制代理 {#replication-agent}

#### 检查代理的状态 {#check-the-status-of-an-agent}

```shell
curl -u <user>:<password> "http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json?agent=publish"
http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json?agent=publish
```

#### 删除代理 {#delete-an-agent}

```shell
curl -X DELETE http://localhost:4502/etc/replication/agents.author/replication99 -u <user>:<password>
```

#### 创建代理 {#create-an-agent}

```shell
curl -u <user>:<password> -F "jcr:primaryType=cq:Page" -F "jcr:content/jcr:title=new-replication" -F "jcr:content/sling:resourceType=/libs/cq/replication/components/agent" -F "jcr:content/template=/libs/cq/replication/templates/agent" -F "jcr:content/transportUri=http://localhost:4503/bin/receive?sling:authRequestLogin=1" -F "jcr:content/transportUser=admin" -F "jcr:content/transportPassword={DES}8aadb625ced91ac483390ebc10640cdf"http://localhost:4502/etc/replication/agents.author/replication99
```

#### 暂停代理 {#pause-an-agent}

```shell
curl -u <user>:<password> -F "cmd=pause" -F "name=publish"  http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json
```

#### 清除代理队列 {#clear-an-agent-queue}

```shell
curl -u <user>:<password> -F "cmd=clear" -F "name=publish"  http://localhost:4502/etc/replication/agents.author/publish/jcr:content.queue.json
```

### 社区 {#communities}

#### 分配和撤销徽章 {#assign-and-revoke-badges}

请参阅 [社区评分和徽章](/help/communities/implementing-scoring.md#assign-and-revoke-badges) 以了解详细信息。

请参阅 [评分和徽章要点](/help/communities/configure-scoring.md#example-setup) 以了解详细信息。

#### MSRP重新索引 {#msrp-reindexing}

请参阅 [MSRP - MongoDB存储资源提供程序](/help/communities/msrp.md#running-msrp-reindex-tool-using-curl-command) 以了解详细信息。

### 安全性 {#security}

#### 启用和禁用CRX DE Lite {#enabling-and-disabling-crx-de-lite}

请参阅 [在AEM中启用CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md) 以了解详细信息。

### 数据存储垃圾收集 {#data-store-garbage-collection}

请参阅 [数据存储垃圾收集](/help/sites-administering/data-store-garbage-collection.md#automating-data-store-garbage-collection) 以了解详细信息。

### Analytics与Target集成 {#analytics-and-target-integration}

请参阅 [选择加入Adobe Analytics和Adobe Target](/help/sites-administering/opt-in.md#configuring-the-setup-and-provisioning-via-script) 以了解详细信息。

### 单点登录 {#single-sign-on}

#### 发送测试标题 {#send-test-header}

请参阅 [单点登录](/help/sites-deploying/single-sign-on.md) 以了解详细信息。

## 常见内容处理AEM cURL命令 {#common-content-manipulation-aem-curl-commands}

以下是用于内容处理的AEM cURL命令列表。

>[!NOTE]
>
>以下示例假定AEM在 `localhost` 端口 `4502` 和使用用户 `admin` 密码 `admin`. 其他命令占位符在尖括号中设置。

### 页面管理 {#page-management}

#### 页面激活 {#page-activation}

```shell
curl -u <user>:<password> -X POST -F path="/content/path/to/page" -F cmd="activate" http://localhost:4502/bin/replicate.json
```

#### 页面停用 {#page-deactivation}

```shell
curl -u <user>:<password> -X POST -F path="/content/path/to/page" -F cmd="deactivate" http://localhost:4502/bin/replicate.json
```

#### 树激活 {#tree-activation}

```shell
curl -u <user>:<password> -F cmd=activate -F ignoredeactivated=true -F onlymodified=true -F path=/content/geometrixx http://localhost:4502/etc/replication/treeactivation.html
```

#### 锁定页面 {#lock-page}

```shell
curl -u <user>:<password> -X POST -F cmd="lockPage" -F path="/content/path/to/page" -F "_charset_"="utf-8" http://localhost:4502/bin/wcmcommand
```

#### 解锁页面 {#unlock-page}

```shell
curl -u <user>:<password> -X POST -F cmd="unlockPage" -F path="/content/path/to/page" -F "_charset_"="utf-8" http://localhost:4502/bin/wcmcommand
```

#### 复制页面 {#copy-page}

```shell
curl -u <user>:<password> -F cmd=copyPage -F destParentPath=/path/to/destination/parent -F srcPath=/path/to/source/location http://localhost:4502/bin/wcmcommand
```

### 工作流 {#workflows}

请参阅 [以编程方式与工作流交互](/help/sites-developing/workflows-program-interaction.md) 以了解详细信息。

### Sling内容 {#sling-content}

#### 创建文件夹 {#create-a-folder}

```shell
curl -u <user>:<password> -F jcr:primaryType=sling:Folder http://localhost:4502/etc/test
```

#### 删除节点 {#delete-a-node}

```shell
curl -u <user>:<password> -F :operation=delete http://localhost:4502/etc/test/test.properties
```

#### 移动节点 {#move-a-node}

```shell
curl -u <user>:<password> -F":operation=move" -F":applyTo=/sourceurl"  -F":dest=/target/parenturl/" https://localhost:4502/content
```

#### 复制节点 {#copy-a-node}

```shell
curl -u <user>:<password> -F":operation=copy" -F":applyTo=/sourceurl"  -F":dest=/target/parenturl/" https://localhost:4502/content
```

#### 使用Sling PostServlet上传文件 {#upload-files-using-sling-postservlet}

```shell
curl -u <user>:<password> -F"*=@test.properties"  http://localhost:4502/etc/test
```

#### 使用Sling PostServlet上传文件并指定节点名称 {#upload-files-using-sling-postservlet-and-specifying-node-name}

```shell
curl -u <user>:<password> -F"test2.properties=@test.properties"  http://localhost:4502/etc/test
```

#### 上传指定内容类型的文件 {#upload-files-specifying-a-content-type}

```shell
curl -u <user>:<password> -F "*=@test.properties;type=text/plain" http://localhost:4502/etc/test
```

### 资产处理 {#asset-manipulation}

请参阅 [资产HTTP API](/help/assets/mac-api-assets.md) 以了解详细信息。
