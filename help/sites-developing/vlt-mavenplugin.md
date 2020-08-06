---
title: 使用Maven管理包
seo-title: 使用Maven管理包
description: 使用内容包Maven插件将包管理任务集成到Maven项目中
seo-description: 使用内容包Maven插件将包管理任务集成到Maven项目中
uuid: fa73f0d6-8848-4911-9b96-311c875b45be
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 943de371-0149-4307-be3a-b11c590b3451
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939
workflow-type: tm+mt
source-wordcount: '3281'
ht-degree: 3%

---


# 使用Maven管理包{#managing-packages-using-maven}

使用内容包Maven插件将包管理任务集成到Maven项目中。 插件目标和参数使您能够自动执行许多通常使用“包管理器”页或FileVault命令行执行的任务:

* 从文件系统中的文件创建新包。
* 在CRX或CQ服务器上安装和卸载包。
* 生成已在服务器上定义的包。
* 获取安装在服务器上的列表包。
* 从服务器中删除包。

## 将内容包Maven插件添加到POM文件 {#adding-the-content-package-maven-plugin-to-the-pom-file}

要使用内容包管理插件，请在POM文件的构建元素中添加以下插件元素：

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>0.0.24</version>
 <configuration>
       <!-- parameters and values common to all goals, as required --> 
 </configuration>
</plugin>
```

要启用Maven下载插件，请使用本页“获取内容包 [Maven插件”部分中提供的用户档案](#obtaining-the-content-package-maven-plugin) 。

## 内容包Maven插件的目标 {#goals-of-the-content-package-maven-plugin}

“内容包”插件提供的目标和目标参数在后面几节中有介绍。 “常用参数”部分中描述的参数可用于大多数目标。 适用于一个目标的参数在该目标的一节中进行了说明。

**插件前缀**

插件前缀是content-package。 使用此前缀从命令行执行目标，如下例所示：

```shell
mvn content-package:build 
```

**参数前缀**

除非另有说明，否则插件目标和参数使用保管库前缀，如下例所示：

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

**代理**

对CRX或CQ服务器使用代理的目标使用在Maven设置中找到的第一个有效代理配置。 如果未找到代理配置，则不使用代理。 请参阅“常用设置”部分中的useProxy参数。

### 常用参数 {#common-parameters}

下表中的参数对所有目标都是通用的，但“目标”列中注明的除外。

<table> 
 <tbody> 
  <tr> 
   <th>名称</th> 
   <th>类型</th> 
   <th>必填</th> 
   <th>默认值</th> 
   <th>描述</th> 
   <th>目标</th> 
  </tr> 
  <tr> 
   <td>failOnError</td> 
   <td>布尔型</td> 
   <td>否</td> 
   <td>false</td> 
   <td>如果值为 <code>true</code> ，则在出错时生成将失败。 值导致 <code>false</code> 生成忽略错误。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>名称</td> 
   <td>字符串</td> 
   <td>构建： 是安装<br /> : 无<br /> rm: 是</td> 
   <td>构建： 无默认值。<br /> 安装： Maven项目的artifactId属性的值。</td> 
   <td>要操作的包的名称。</td> 
   <td>除ls之外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>密码</td> 
   <td>字符串</td> 
   <td>是</td> 
   <td>管理员</td> 
   <td>用于CRX服务器身份验证的口令。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>serverId</td> 
   <td>字符串</td> 
   <td>否</td> 
   <td></td> 
   <td>要从中检索用户名和密码以进行身份验证的服务器ID。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>targetURL</td> 
   <td>字符串</td> 
   <td>是</td> 
   <td>http://localhost:4502/<br /> crx/packmgr/<br /> service.jsp</td> 
   <td>CRX包管理器的HTTP服务API的URL。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>超时</td> 
   <td>int</td> 
   <td>否</td> 
   <td>5</td> 
   <td>与包管理器服务通信的连接超时（以秒为单位）。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>useProxy</td> 
   <td>布尔型</td> 
   <td>否</td> 
   <td>true</td> 
   <td>确定是否从Maven设置文件使用代理配置。 如果值为 <code>true</code> ，则会使用找到的第一个活动代理配置来向包管理器代理请求。 如果值为false，则不使用代理。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>userId</td> 
   <td>字符串</td> 
   <td>是</td> 
   <td>管理员</td> 
   <td>要与CRX服务器进行身份验证的用户名。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
  <tr> 
   <td>详细</td> 
   <td>布尔型</td> 
   <td>否</td> 
   <td>false</td> 
   <td>启用或禁用详细记录。 值启用详 <code>true</code> 细记录。</td> 
   <td>除包外的所有目标。</td> 
  </tr> 
 </tbody> 
</table>

### build {#build}

构建已在AEM实例上定义的内容包。

>[!NOTE]
>
>无需在Maven项目内执行此目标。

#### 参数 {#parameters}

构建目标的所有参数在“常用参数”部 [分中均有介绍](#common-parameters) 。

#### 示例 {#example}

以下示例构建安装在AEM实例上的workflow-mbean包，其IP地址为10.36.79.223。目标使用以下命令执行：

```shell
mvn content-package:build
```

以下POM文件位于命令行工具的当前目录中。 POM指定包服务的包名称和URL。

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
   <name>workflow-mbean</name>
   <failOnError>true</failOnError>
   <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
     </plugin>
 </plugins>
    </build>
</project>
```

### install {#install}

在存储库中安装包。 执行此目标不需要Maven项目。 该目标将限于Maven构建生命周期的“安装”阶段。

#### 参数 {#parameters-1}

除以下参数外，请参阅“公用参数”部 [分中的说](#common-parameters) 明。

<table> 
 <tbody> 
  <tr> 
   <th>名称</th> 
   <th>类型</th> 
   <th>必填</th> 
   <th>默认值</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td>伪</td> 
   <td>字符串</td> 
   <td>否</td> 
   <td>Maven项目的artifactId属性的值。</td> 
   <td>表单groupId:artifactId:version[:packaging]的字符串。</td> 
  </tr> 
  <tr> 
   <td>artifactId</td> 
   <td>字符串</td> 
   <td>否</td> 
   <td></td> 
   <td>要安装的对象的ID</td> 
  </tr> 
  <tr> 
   <td>groupId</td> 
   <td>字符串</td> 
   <td>否</td> 
   <td></td> 
   <td>要安装的对象的groupId</td> 
  </tr> 
  <tr> 
   <td>安装</td> 
   <td>布尔型</td> 
   <td>否</td> 
   <td>true</td> 
   <td>确定是否在上传包时自动解包。 值true将解压包，而值false不解压包。</td> 
  </tr> 
  <tr> 
   <td>localRepository</td> 
   <td>org.apache.maven.<br /> 藏物。 存储库。<br /> ArtifactRepository</td> 
   <td>否</td> 
   <td>localRepository系统变量的值。</td> 
   <td>本地Maven存储库。 无法使用插件配置配置此参数。 始终使用系统属性。</td> 
  </tr> 
  <tr> 
   <td>packageFile</td> 
   <td>java.io.File</td> 
   <td>否</td> 
   <td>为Maven项目定义的主对象。</td> 
   <td>要安装的包文件的名称。</td> 
  </tr> 
  <tr> 
   <td>包装</td> 
   <td>字符串</td> 
   <td>否</td> 
   <td>zip</td> 
   <td>要安装的对象的打包类型</td> 
  </tr> 
  <tr> 
   <td>pomRemoteRepositories</td> 
   <td>java.util.List</td> 
   <td>是</td> 
   <td>为Maven项目定义的remoteAtifactRepositories属性的值。</td> 
   <td>无法使用插件配置配置此值。 必须在项目中指定值。 </td> 
  </tr> 
  <tr> 
   <td>项目</td> 
   <td>org.apache.maven.<br /> project.MavenProject</td> 
   <td>是</td> 
   <td>为其配置插件的项目。</td> 
   <td>马文项目。 项目是隐式的，因为项目包含插件配置。</td> 
  </tr> 
  <tr> 
   <td>repositoryId <i>(POM)</i><br /> repoID <i>（命令行）</i></td> 
   <td>字符串</td> 
   <td>否</td> 
   <td>温度</td> 
   <td>从中检索对象的存储库的ID。 在POM中，使用repositoryID。 在命令行中，使用repoID。</td> 
  </tr> 
  <tr> 
   <td>repositoryUrl( <i>POM)</i><br /> 回购 <i>URL（命令行）</i></td> 
   <td>字符串</td> 
   <td>否</td> 
   <td></td> 
   <td>从中检索对象的存储库的URL。 在POM中，使用repositoryURL。 在命令行中，使用repoURL。</td> 
  </tr> 
  <tr> 
   <td>版本</td> 
   <td>字符串</td> 
   <td>否</td> 
   <td></td> 
   <td>要安装的对象的版本。</td> 
  </tr> 
 </tbody> 
</table>

#### 示例 {#example-1}

以下示例创建一个包，其中包含workflow-mbean OSGi捆绑包(请参见构建目 [标的](#build) 示例)，然后安装该包。 由于安装目标绑定到包安装阶段，因此以下命令执行安装目标：

```shell
mvn install
```

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>

  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>package</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
```

### ls {#ls}

列表部署到包管理器的包。

#### 参数 {#parameters-2}

ls目标的所有参数都在“常用参数” [部分中进行](#common-parameters) 说明。

#### 示例 {#example-2}

以下示例列表安装在AEM实例上的包，其IP地址为10.36.79.223。目标使用以下命令执行：

```shell
mvn content-package:ls
```

以下POM文件位于命令行工具的当前目录中。 POM指定包服务的URL。

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
      <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
      </plugin>
   </plugins>
     </build>
</project>
```

### rm {#rm}

从包管理器中删除包。

#### 参数 {#parameters-3}

rm目标的所有参数都在“常用参数” [部分中进行](#common-parameters) 说明。

#### 示例 {#example-3}

以下示例删除了IP地址为10.36.79.223的AEM实例上安装的工作流mbean包。目标使用以下命令执行：

```shell
mvn content-package:rm
```

以下POM文件位于命令行工具的当前目录中。 POM指定包服务的URL和包的名称。

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>example-package</artifactId>
  <version>0.0.1-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
                    <name>workflow-mbean</name>
      <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
      </plugin>
   </plugins>
     </build>
</project>
```

### uninstall {#uninstall}

卸载包。 软件包将保留在已卸载状态的服务器上。

#### 参数 {#parameters-4}

卸载目标的所有参数都在“常用参数” [部分中进行](#common-parameters) 说明。

#### 示例 {#example-4}

以下示例卸载安装在AEM实例上的IP地址为10.36.79.223的workflow-mbean包。目标使用以下命令执行：

```shell
mvn content-package:uninstall
```

以下POM文件位于命令行工具的当前目录中。 POM指定包服务的包名称和URL。

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
  xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
  xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>
    <build>
        <plugins>
     <plugin>
  <groupId>com.day.jcr.vault</groupId>
  <artifactId>content-package-maven-plugin</artifactId>
  <version>0.0.24</version>
  <configuration>
   <name>workflow-mbean</name>
   <failOnError>true</failOnError>
   <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
  </configuration>
     </plugin>
 </plugins>
    </build>
</project>
```

### package {#package}

创建内容包。 包目标的默认配置包括保存已编译文件的目录的内容。 执行包目标需要编译构建阶段已完成。 包目标绑定到Maven构建生命周期的包阶段。

#### 参数 {#parameters-5}

除了以下参数之外，请参阅“公用参 `name` 数”部分中 [的参数说](#common-parameters) 明。

<table> 
 <tbody> 
  <tr> 
   <th>名称</th> 
   <th>类型</th> 
   <th>必填</th> 
   <th>默认值</th> 
   <th>描述</th> 
  </tr> 
  <tr> 
   <td>存档</td> 
   <td>org.apache.maven.<br /> archiver。<br /> MavenArchiveConfiguration</td> 
   <td>否</td> 
   <td></td> 
   <td>要使用的存档配置。 请参 <a href="https://maven.apache.org/shared/maven-archiver/index.html">阅Maven Archiver的文档</a>。</td> 
  </tr> 
  <tr> 
   <td>builtContentDirectory</td> 
   <td>java.io.File</td> 
   <td>是</td> 
   <td>Maven内部版本的输出目录的值。</td> 
   <td>包含要包含在包中的内容的目录。</td> 
  </tr> 
  <tr> 
   <td>依赖</td> 
   <td>java.util.List</td> 
   <td>否</td> 
   <td></td> 
   <td></td> 
  </tr> 
  <tr> 
   <td>embeddedTarget</td> 
   <td>java.lang.String</td> 
   <td>否</td> 
   <td></td> 
   <td></td> 
  </tr> 
  <tr> 
   <td>嵌入式</td> 
   <td>java.util.List</td> 
   <td>否</td> 
   <td></td> 
   <td></td> 
  </tr> 
  <tr> 
   <td>failOnMissingEmbed</td> 
   <td>布尔型</td> 
   <td>是</td> 
   <td>false</td> 
   <td>如果值为true，则在项目依赖关系中找不到嵌入的对象时，生成将失败。 值偏离会导致生成忽略错误。</td> 
  </tr> 
  <tr> 
   <td>filterSource</td> 
   <td>java.io.File</td> 
   <td>否</td> 
   <td></td> 
   <td>一个文件，它指定工作区过滤器的源。 在配置中指定并通过嵌入式或子包注入的过滤器与文件内容合并。</td> 
  </tr> 
  <tr> 
   <td>过滤器</td> 
   <td>com.day.jcr.<br /> vault.maven.pack.impl.<br /> DefaultWorkspaceFilter</td> 
   <td>否</td> 
   <td></td> 
   <td>包含定义包内容的筛选器元素。 执行时，过滤器将包含在filter.xml文件中。 请参阅下面的使用过滤器部分。</td> 
  </tr> 
  <tr> 
   <td>finalName</td> 
   <td>java.lang.String</td> 
   <td>是</td> 
   <td>在Maven项目（构建阶段）中定义的finalName。</td> 
   <td>生成的包ZIP文件的名称，不带。zip文件扩展名。</td> 
  </tr> 
  <tr> 
   <td>组</td> 
   <td>java.lang.String</td> 
   <td>是</td> 
   <td>在Maven项目中定义的groupID。</td> 
   <td>生成的内容包的groupId。 此值是内容包的目标安装路径的一部分。</td> 
  </tr> 
  <tr> 
   <td>outputDirectory</td> 
   <td>java.io.File</td> 
   <td>是</td> 
   <td>Maven项目中定义的生成目录。</td> 
   <td>保存内容包的本地目录。</td> 
  </tr> 
  <tr> 
   <td>前缀</td> 
   <td>java.lang.String</td> 
   <td>否</td> 
   <td></td> 
   <td></td> 
  </tr> 
  <tr> 
   <td>项目</td> 
   <td>org.apache.maven.<br /> project.MavenProject</td> 
   <td>是</td> 
   <td></td> 
   <td>马文项目。</td> 
  </tr> 
  <tr> 
   <td>属性</td> 
   <td>java.util.Map</td> 
   <td>否</td> 
   <td></td> 
   <td>可在properties.xml文件中设置的其他属性。 这些属性不能覆盖以下预定义属性： 
    <ul> 
     <li>组： 使用组参数设置</li> 
     <li>名称： 使用名称参数设置</li> 
     <li>版本： 使用版本参数设置</li> 
     <li>说明： 从项目描述设置</li> 
     <li>groupId: Maven项目描述符的groupId</li> 
     <li>artifactId: maven项目描述符的artifactId</li> 
     <li>依赖关系： 使用依赖关系参数设置</li> 
     <li>createdBy: user.name系统属性的值</li> 
     <li>created: 当前系统时间</li> 
     <li>requiresRoot: 使用requiresRoot参数设置</li> 
     <li>packagePath: 从组和包名称自动生成</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>requiresRoot</td> 
   <td>布尔型</td> 
   <td>是</td> 
   <td>false</td> 
   <td>定义包是否需要根。 这将成为properties.xml文件的&lt;code&gt;requiresRoot&lt;/code&gt;属性。</td> 
  </tr> 
  <tr> 
   <td>子包</td> 
   <td>java.util.List</td> 
   <td>否</td> 
   <td></td> 
   <td></td> 
  </tr> 
  <tr> 
   <td>版本</td> 
   <td>java.lang.String</td> 
   <td>是</td> 
   <td>Maven项目中定义的版本</td> 
   <td>内容包的版本。</td> 
  </tr> 
  <tr> 
   <td>workDirectory</td> 
   <td>java.io.File</td> 
   <td>是</td> 
   <td>在Maven项目（构建阶段）中定义的目录。</td> 
   <td>包含要包含在包中的内容的目录。</td> 
  </tr> 
 </tbody> 
</table>

#### 使用过滤器 {#using-filters}

使用过滤器元素定义包内容。 这些过滤器将添加到包文件中 `META-INF/vault/filter.xml` 的workspaceFilter元素。

以下筛选器示例显示要使用的XML结构：

```xml
<filter>
   <root>/apps/myapp</root>
   <mode>merge</mode> 
       <includes>
              <include>/apps/myapp/install/</include>
              <include>/apps/myapp/components</include>
       </includes>
       <excludes>
              <exclude>/apps/myapp/config/*</exclude>
       </excludes>
</filter>
```

**导入模式**

元 `mode` 素定义导入包时如何影响存储库的内容。 可以使用以下值：

* **合并：** 将添加包中尚未在存储库中的内容。 包和存储库中的内容将保持不变。 不会从存储库中删除任何内容。
* **替换：** 包中不在存储库中的内容将添加到存储库。 存储库中的内容将替换为包中的匹配内容。 当内容在包中不存在时，内容将从存储库中删除。
* **更新：** 包中不在存储库中的内容将添加到存储库。 存储库中的内容将替换为包中的匹配内容。 现有内容会从存储库中删除。

当筛选器不包含 `mode` 任何元素时，将使用 `replace` 默认值。

#### 示例 {#example-5}

以下示例创建一个包，它包含workflow-mbean OSGi捆绑包。 POM文件将jcr_root目录标识为builtContentDirectory属性的值。 jcr_root目录包含镜像存储库的目录结构中的捆绑JAR文件：

`jcr_root/apps/myapp/install/workflow-mbean-0.03-SNAPSHOT.jar`

由于目标绑定到包构建阶段，因此以下命令执行包目标：

`mvn package`

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>

  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
        <executions>
          <execution>
            <goals>
              <goal>package</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
```

您可以将目 `package` 标用作项目元 `executions` 素的值，而 `content-package` 不是在插件部分表 `packaging` 示：

```xml
<project xmlns="https://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" 
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 
    https://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.adobe.example.myapp</groupId>
  <artifactId>workflow-mbean</artifactId>
  <version>0.0.3-SNAPSHOT</version>
  <packaging>content-package</packaging>
  <build>
    <plugins>
      <plugin>
        <groupId>com.day.jcr.vault</groupId>
        <artifactId>content-package-maven-plugin</artifactId>
        <version>0.0.24</version>
        <configuration>
          <builtContentDirectory>jcr_root</builtContentDirectory>
          <targetURL>https://10.36.79.223:4502/crx/packmgr/service.jsp</targetURL>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```

### 帮助 {#help}

#### 参数 {#parameters-6}

| 名称 | 类型 | 必填 | 默认值 | 描述 |
|---|---|---|---|---|
| detail | 布尔型 | 否 | false | 确定是否显示每个目标的所有可设置属性。 如果值为true，则显示所有可设置的属性。 |
| 目标 | 字符串 | 否 |  | 要显示帮助的目标的名称。 如果未指定任何值，则显示所有目标的帮助。 |
| indentSize | int | 否 | 2 | 用于每个级别缩进的空格数。 如果指定值，则该值应为正。 |
| lineLength | int | 否 | 80 | 显示线的最大长度。 如果指定值，则该值应为正。 |

## 获取内容包Maven插件 {#obtaining-the-content-package-maven-plugin}

插件可从公共Adobe库中访问。 要下载该插件，请将以下Maven用户档案添加到Maven设置文件并将其激活。 使用Maven命令时，该插件会根据需要下载到您的本地存储库。

>[!NOTE]
>
>Adobe公共发行版存储库不可浏览，因此使用Web浏览器导航到存储库URL会导致“找不到”错误。 但是，Maven能够访问存储库目录。

```xml
<profile>
    <id>adobe-public</id>
    <activation>
         <activeByDefault>false</activeByDefault>
    </activation>
    <properties>
         <releaseRepository-Id>adobe-public-releases</releaseRepository-Id>
         <releaseRepository-Name>Adobe Public Releases</releaseRepository-Name>
         <releaseRepository-URL>https://repo.adobe.com/nexus/content/groups/public</releaseRepository-URL>
    </properties>
    <repositories>
         <repository>
             <id>adobe-public-releases</id>
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </repository>
     </repositories>
     <pluginRepositories>
         <pluginRepository>
             <id>adobe-public-releases</id>
             <name>Adobe Basel Public Repository</name>
             <url>https://repo.adobe.com/nexus/content/groups/public</url>
             <releases>
                 <enabled>true</enabled>
                 <updatePolicy>never</updatePolicy>
             </releases>
             <snapshots>
                 <enabled>false</enabled>
             </snapshots>
         </pluginRepository>
     </pluginRepositories>
</profile>
```

## 在内容包中嵌入OSGi包 {#embedding-osgi-bundles-in-a-content-package}

使用内容包授权插件将OSGi捆绑包嵌入到内容包中。 要嵌入捆绑包，请实施以下配置：

* 必须将捆绑声明为Maven项目的依赖项。
* 插件配置使用包中捆绑包的所需路径引用捆绑包。

以下示例POM创建包含Apache Sling JCR UserManager包的包。 在包中，捆绑JAR位于以下文 `jcr_root/apps/myapp/install` 件夹：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" 
             xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
             xsi:schemaLocation="https://maven.apache.org/POM/4.0.0
             https://maven.apache.org/maven-v4_0_0.xsd">
 <modelVersion>4.0.0</modelVersion>
   <groupId>com.adobe.example.myapp</groupId>
 <artifactId>embedded-example</artifactId>
 <packaging>content-package</packaging>
 <version>1.0.0-SNAPSHOT</version>

   <build>
 <plugins>
     <plugin>
        <groupId>com.day.jcr.vault</groupId>
      <artifactId>content-package-maven-plugin</artifactId>
      <version>0.0.24</version>
      <extensions>true</extensions>
      <configuration>
   <filters>
       <filter>
    <root>/apps/myapp</root>
       </filter>
    </filters>
    <embeddeds>
       <embedded>
    <groupId>org.apache.sling</groupId>
    <artifactId>org.apache.sling.jcr.jackrabbit.usermanager</artifactId>
    <target>/apps/myproject/install</target>
        </embedded>
    </embeddeds>
       </configuration>
  </plugin> 
    </plugins>
    </build>
    <dependencies>
 <dependency>
      <groupId>org.apache.sling</groupId>
      <artifactId>org.apache.sling.jcr.jackrabbit.usermanager</artifactId>
      <version>2.2.0</version>
 </dependency>
    </dependencies> 
</project>
```

## 在包中包含缩略图或属性文件 {#including-a-thumbnail-image-or-properties-file-in-the-package}

替换默认的包配置文件以自定义包属性。 例如，包含缩略图图像以区分包管理器和包共享中的包。

在包中，FileVault特定文件位于/META-INF/vault文件夹中。 源文件可位于文件系统中的任意位置。 在POM文件中，定义构建资源以将源文件复制到目标/vault-work/META-INF以包含在包中。

以下POM代码将项目源的META-INF文件夹中的文件添加到包中：

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail etc.) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

以下POM代码仅向包添加缩略图图像。 缩略图图像必须命名为thumbnail.png，并且必须位于包的META-INF/vault/definition文件夹中。 在此示例中，源文件位于项目的/src/main/content/META-INF/vault/definition文件夹中：

```xml
<build>
    <resources>
        <!-- thumbnail only -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF/vault/definition</directory>
            <targetPath>../vault-work/META-INF/vault/definition</targetPath>
        </resource>
    </resources>
</build>
```

## 使用原型生成AEM项目 {#using-archetypes-to-generate-aem-projects}

有几种马文原型可用于生成AEM项目。 使用与您的发展目标相对应的原型：

* 为AEM应用程序安装资源的内容包： [简单内容包——原型](#simple-content-package-archetype)
* 包含第三方对象的内容包： [simple-content-package-with-embedded-archetype](#simple-content-package-with-embedded-archetype)。
* 一个多模块应用程序，它适应Java类和单元测试的开发： [多模块——内容——包——原型](#multimodule-content-package-archetype)。

>[!NOTE]
>
>Apache Sling项目还优惠了在AEM开发中有用的原型。 这些内容在https://sling.apache.org/site/maven-archetypes.html [上介绍](https://sling.apache.org/documentation/development/maven-archetypes.html)。

每个原型都生成以下项目：

* 项目文件夹结构。
* POM文件。
* FileVault配置文件。

原型文物可从Adobe公共Maven存储库中获得。 要下载和执行原型，请使用Maven原型：generate命令的参数确定原型和Adobe库：

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId={id_of_archetype} -DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

Maven原型插件在shell或命令提示符下使用交互模式来收集有关您的项目的信息。 您提供的信息用于配置各种项目属性，如文件夹名称和对象ID。

**POM文件**

生成的POM文件包括用于编译代码、创建捆绑包以及将它们部署到包中的AEM的命令。 Maven项 `groupID`目的 `artifactId`、、和 `version`属性会使用您向Maven交互提示提供的值自动 `name``archetype:generate` 填充。

您可能希望更改生成的pom.xml文件中的以下默认值：

* CQ服务器名称或IP地址： 默认值为 `localhost`。 以下 `crx.host` 元素 `project/properties` 包含此值。

* CQ服务器的端口号： 默认值为 `4502`。 以下 `crx.port` 元素 `project/properties` 包含此值。

* 内容包Maven插件的版本： 使用最新版本作为插件 `version` 的元素的内容( `artifactId` 包含 `content-package-maven-plugin`)。 默认值为 `0.0.24`.

**使用原型**

1. 在shell窗口或命令提示符下，输入Maven命 `archetype:generate` 令。 出现提示时，请提供其余参数的值。

   有关每个参数的信息，请参阅您所使用的原型的一节。

1. 使用文本编辑器打开pom.xml文件并根据您的要求编辑默认值。
1. 用资源填充生成的文件夹。
1. 输入命 `mvn clean install` 令。

### 简单内容包——原型 {#simple-content-package-archetype}

创建一个适合为简单的AEM应用程序安装资源的主项目。 文件夹结构是在AEM存储库的 `/apps` 文件夹下使用的。 POM定义了用于打包您放置在文件夹中的资源以及在AEM实例上安装包的命令。

**原型工件属性：**

* 组ID: `com.day.jcr.vault`
* 对象ID: `simple-content-package-archetype`
* 版本: `1.0.2`
* 存储库: `adobe-public-releases`

**Maven命令：**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=simple-content-package-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**原型参数：**

* groupId: Maven生成的内容包的groupId。 该值将自动用在POM文件中。
* artifactId: 内容包的名称。 该值还用作项目文件夹的名称。
* 版本： 内容包的版本。
* 包： 此值不用于simple-content-package-archetype。
* appsFolderName: /apps下的文件夹名称。
* artifactName: 内容包的说明。
* packageGroup: 内容包组的名称。 此值配置内容包管理插件的包目标的组参数。

**文件夹结构：**

```xml
${artifactId}
   |- pom.xml
   |- README.txt
   |- src
      |- main
         |- content
             |- jcr_root
                 |- apps
                     |- ${appsFolderName}
                            |- components 
                               |- .content.xml
                            |- config
                            |- install
             |- META-INF
                 |- vault
                     |- config.xml
                     |- filter.xml
                     |- nodetypes.cnd
                     |- properties.xml
                     |- definition
                        |- .content.xml
```

### 简单内容包——带嵌入式原型 {#simple-content-package-with-embedded-archetype}

执行与简单内容包原型相同的任务，还从公共Maven存储库下载并包含一个对象。

**原型捆绑属性：**

* 组ID: `com.day.jcr.vault`
* 对象ID: `simple-content-package-with-embedded-archetype`
* 版本: `1.0.2`
* 存储库: `adobe-public-releases`

**Maven命令：**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=simple-content-package-with-embedded-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**原型参数：**

* groupId: Maven生成的内容包的groupId。 该值将自动用在POM文件中。
* artifactId: 内容包的名称。 该值还用作项目文件夹的名称。
* 版本： 内容包的版本。
* 包： 此参数不被使用。
* appsFolderName: /apps下的文件夹名称。
* artifactName: 内容包的说明。
* embeddedArtifactId: 要嵌入到内容包中的对象的ID。
* embeddedGroupId: 要嵌入的对象的组ID。
* 嵌入式版本： 要嵌入的对象的版本。
* packageGroup: 内容包组的名称。 此值配置内容包管理插件的包目标的组参数。

**文件夹结构：**

```xml
${artifactId}
   |- pom.xml
   |- README.txt
   |- src
      |- main
         |- content
             |- jcr_root
                 |- apps
                     |- ${appsFolderName}
                            |- components 
                            |- config
                            |- install
             |- META-INF
                 |- vault
                     |- config.xml
                     |- filter.xml
                     |- nodetypes.cnd
                     |- properties.xml
                     |- definition
```

### 多模块内容包——原型 {#multimodule-content-package-archetype}

创建一个主项目，其中包含用于开发AEM应用程序和向服务器安装资源的文件夹结构。

该文 `bundle` 件夹包含存储您开发的Java和JUnit源文件的文件夹结构。 此文件夹中的pom.xml文件创建OSGi捆绑。 POM中的以下值标识伪像和捆绑：

* artifactID: `${artifactID}-bundle`.
* Bundle-SymbolicName: `${groupId}.${artifactId}-bundle`.

`${artifactID}` 和 `${groupId}` 执行原型时为这些参数提供的值。

文 `content` 件夹包含安装到AEM实例的资源。 artifactID的值为 `${artifactID}multimodule-bundle`。

父文件夹包含管理Maven插件和依赖项的父POM。

**原型捆绑属性：**

* 组ID: `com.day.jcr.vault`
* 对象ID: `multimodule-content-package-archetype`
* 版本: `1.0.2`
* 存储库: `adobe-public-releases`

**Maven命令：**

```shell
mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault \
-DarchetypeArtifactId=multimodule-content-package-archetype \
-DarchetypeVersion=1.0.2 \
-DarchetypeRepository=adobe-public-releases
```

**原型参数：**

* groupId: Maven生成的内容包的groupId。 该值将自动用在POM文件中。
* artifactId: 内容包的名称。 该值还用作项目文件夹的名称。
* 版本： 内容包的版本。
* 包： 此值不用于multimodule-content-package-archetype。
* appsFolderName: /apps下的文件夹名称。
* artifactName: 内容包的说明。
* packageGroup: 内容包组的名称。 此值配置内容包管理插件的包目标的组参数。

**文件夹结构：**

```xml
${artifactId}
   |- pom.xml
   |- bundle
      |- pom.xml
      |- src
         |- main
            |- java
               |- ${groupId}
                  |- SimpleDSComponent.java
         |- test
            |- java
               |- ${groupId}
                  |- SimpleUnitTest.java
   |- content
      |- pom.xml
      |- src
         |- main
            |- content
               |- jcr_root
                  |- apps
                     |- ${appsFolderName} 
                            |- config
                            |- install
                  |- META-INF
                      |- vault
                         |- config.xml
                         |- filter.xml
                         |- nodetypes.cnd
                         |- properties.xml
                         |- definition
                            |- .content.xml
```

