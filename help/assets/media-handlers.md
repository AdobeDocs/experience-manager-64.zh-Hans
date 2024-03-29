---
title: 使用媒体处理程序和工作流处理资产
description: 了解各种媒体处理程序，以及如何在工作流中使用它们对资产执行任务。
contentOwner: AG
feature: Workflow,Renditions
role: User
exl-id: 7694c68d-0a17-4052-8fbe-9bf45b229e81
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 4%

---

# 使用媒体处理程序和工作流处理资产 {#processing-assets-using-media-handlers-and-workflows}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

Adobe Experience Manager Assets提供了一组用于处理资产的默认工作流和媒体处理程序。 工作流定义了典型的资产管理和处理任务，然后将特定任务委派给媒体处理程序，例如缩略图生成或元数据提取。

可以定义在将特定类型或格式的资产上传到服务器时自动执行的工作流。 这些处理步骤被定义为一系列Experience ManagerAssets媒体处理程序。 Adobe Experience Manager提供了一些 [内置处理程序，](#default-media-handlers) 而更多可以 [自定义开发](#creating-a-new-media-handler) 或通过将流程委派给 [命令行工具](#command-line-based-media-handler).

媒体处理程序是Experience Manager Assets中对资产执行特定操作的服务。 例如，当MP3音频文件上传到Experience Manager中时，工作流会触发一个MP3处理程序，该处理程序会提取元数据并生成缩略图。 媒体处理程序与工作流一起使用。 Experience Manager中支持最常见的MIME类型。 您可以执行以下任一操作，对资产执行特定任务

* 扩展或创建工作流。
* 扩展或创建媒体处理程序。
* 禁用或启用媒体处理程序。

>[!NOTE]
>
>请参阅 [资产支持的格式](assets-formats.md) 页面，其中介绍了Experience Manager Assets支持的所有格式以及每种格式支持的功能。

## 默认媒体处理程序 {#default-media-handlers}

Experience Manager Assets中提供了以下媒体处理程序，并处理最常见的MIME类型：

| 处理程序名称 | 服务名称（在系统控制台中） | 支持的MIME类型 |
|---|---|---|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>application/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | 音频/mpeg<br><b>重要信息</b>  — 上传MP3文件时， [使用第三方库处理](https://www.zxdr.it/programmi/SistEvolBDD/LibJava/doc/de/vdheide/mp3/MP3File.html). 如果MP3具有可变比特率(VBR)，则库会计算非精确的近似长度。 |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | 图像/图片 |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>application/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | application/epub+zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | 回退，以防找不到其他处理程序从资产中提取数据 |

所有处理程序都会执行以下任务：

* 从资产中提取所有可用元数据。
* 从资产中创建缩略图。

可以查看活动媒体处理程序：

1. 在您的浏览器中，导航到 `http://localhost:4502/system/console/components`.
1. 单击链接 `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. 将显示包含所有活动媒体处理程序的列表。 例如：

![chlimage_1-437](assets/chlimage_1-437.png)

## 在工作流中使用媒体处理程序对资产执行任务 {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

媒体处理程序是与工作流一起使用的服务。

Experience Manager具有一些用于处理资产的默认工作流。 要查看工作流，请打开工作流控制台，然后单击 **[!UICONTROL 模型]** 选项卡：以Experience Manager Assets开头的工作流标题是特定于资产的工作流标题。

可以扩展现有的工作流，也可以创建新的工作流，以根据特定要求处理资产。

以下示例显示如何增强 **[!UICONTROL AEM Assets同步]** 工作流，以便为除PDF文档以外的所有资产生成子资产。

### 禁用/启用媒体处理程序 {#disabling-enabling-a-media-handler}

可以通过Apache Felix Web管理控制台禁用或启用媒体处理程序。 禁用媒体处理程序后，不会对资产执行其任务。

启用/禁用媒体处理程序：

1. 在您的浏览器中，导航到 `https://<host>:<port>/system/console/components`.
1. 单击 **[!UICONTROL 禁用]** 媒体处理程序名称旁边。 例如：`com.day.cq.dam.handler.standard.mp3.Mp3Handler`。
1. 刷新页面：媒体处理程序旁会显示一个图标，指示它已禁用。
1. 要启用媒体处理程序，请单击 **[!UICONTROL 启用]** 媒体处理程序名称旁边。

### 创建媒体处理程序 {#creating-a-new-media-handler}

要支持新媒体类型或对资产执行特定任务，需要创建媒体处理程序。 本节介绍如何继续。

#### 重要类和接口 {#important-classes-and-interfaces}

开始实施的最佳方式是继承提供的抽象实施，该实施会处理大多数事务并提供合理的默认行为：the `com.day.cq.dam.core.AbstractAssetHandler` 类。

此类已提供抽象服务描述符。 因此，如果您从此类继承并使用maven-sling-plugin，请确保将继承标记设置为 `true`.

实施以下方法：

* `extractMetadata()`:提取所有可用的元数据。
* `getThumbnailImage()`:在传递的资产中创建缩略图。
* `getMimeTypes()`:返回资产MIME类型。

以下是一个示例模板：

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

接口和类包括：

* `com.day.cq.dam.api.handler.AssetHandler` 界面：此界面介绍添加对特定MIME类型支持的服务。 添加MIME类型时，需要实施此接口。 界面包含用于导入和导出特定文档、创建缩略图和提取元数据的方法。
* `com.day.cq.dam.core.AbstractAssetHandler` 类：此类用作所有其他资产处理程序实现的基础，并提供常用功能。
* `com.day.cq.dam.core.AbstractSubAssetHandler` class:
   * 该类用作所有其他资产处理程序实现的基础，并为子资产提取提供常用功能以及常用功能。
   * 开始实施的最佳方式是继承提供的抽象实施，该实施会处理大多数事务并提供合理的默认行为：com.day.cq.dam.core.AbstractAssetHandler类。
   * 此类已提供抽象服务描述符。 因此，如果您从此类继承并使用maven-sling-plugin，请确保将继承标记设置为true。

必须实施以下方法：

* `extractMetadata()`:此方法会提取所有可用的元数据。
* `getThumbnailImage()`:此方法会在传递的资产中创建缩略图。
* `getMimeTypes()`:此方法会返回资产MIME类型。

以下是一个示例模板：

package my.own.stuff;/&amp;ast;&amp;ast;&amp;ast;@scr.component inherit=&quot;true&quot; &amp;ast;@scr.service &amp;ast;/公共类MyMediaHandler扩展com.day.cq.dam.core.AbstractAssetHandler { //实现相关部分}

接口和类包括：

* `com.day.cq.dam.api.handler.AssetHandler` 界面：此界面介绍为特定mime类型添加支持的服务。 添加MIME类型时，需要实施此接口。 界面包含用于导入和导出特定文档、创建缩略图和提取元数据的方法。
* `com.day.cq.dam.core.AbstractAssetHandler` 类：此类用作所有其他资产处理程序实现的基础，并提供常用功能。
* `com.day.cq.dam.core.AbstractSubAssetHandler` 类：该类用作所有其他资产处理程序实现的基础，并为子资产提取提供常用功能以及常用功能。

#### 示例：创建特定文本处理程序 {#example-create-a-specific-text-handler}

在此部分中，您将创建一个特定的文本处理程序，该处理程序生成带有水印的缩略图。

请按如下方式继续：

请参阅 [开发工具](../sites-developing/dev-tools.md) 安装和设置使用Maven插件的Eclipse，以及设置Maven项目所需的依赖项。

执行以下过程后，当您将txt文件上传到Experience Manager时，将提取该文件的元数据，并生成两个带水印的缩略图。

1. 在Eclipse中，创建 `myBundle` Maven项目：

   1. 在菜单栏中，单击 **[!UICONTROL 文件>新建>其他]**.
   1. 在对话框中，展开Maven文件夹，选择Maven项目，然后单击 **[!UICONTROL 下一个]**.
   1. 检查 **[!UICONTROL 创建简单的项目]** 框和 **[!UICONTROL 使用默认工作区位置]** 框，然后单击 **[!UICONTROL 下一个]**.
   1. 使用以下值定义Maven项目：

      * 组Id:com.day.cq5.myhandler
      * 项目ID:myBundle
      * 名称：我的Experience Manager包
      * 描述：这是我的Experience Manager包
   1. 单击 **[!UICONTROL 完成]**.


1. 将“Java™编译器”设置为版本1.5:

   1. 右键单击 `myBundle` 项目，选择属性。
   1. 选择“Java™编译器”，并将以下属性设置为1.5:

      * 编译器符合性级别
      * 生成的.class文件兼容性
      * 源兼容性
   1. 单击&#x200B;**[!UICONTROL 确定]**。在对话框窗口中，单击是。


1. 将pom.xml文件中的代码替换为以下代码：

   ```xml
   <project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion> 
    <!-- ====================================================================== --> 
    <!-- P A R E N T P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <parent>
     <groupId>com.day.cq.dam</groupId>
     <artifactId>dam</artifactId>
     <version>5.2.14</version>
     <relativePath>../parent</relativePath>
    </parent> 
    <!-- ====================================================================== --> 
    <!-- P R O J E C T D E S C R I P T I O N --> 
    <!-- ====================================================================== -->
    <groupId>com.day.cq5.myhandler</groupId>
    <artifactId>myBundle</artifactId>
    <name>My CQ5 bundle</name>
    <version>0.0.1-SNAPSHOT</version>
    <description>This is my CQ5 bundle</description>
    <packaging>bundle</packaging> 
    <!-- ====================================================================== --> 
    <!-- B U I L D D E F I N I T I O N --> 
    <!-- ====================================================================== -->
    <build>
     <plugins>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-scr-plugin</artifactId>
      </plugin>
      <plugin>
       <groupId>org.apache.sling</groupId>
       <artifactId>maven-sling-plugin</artifactId>
       <configuration>
        <slingUrlSuffix>/libs/dam/install/</slingUrlSuffix>
       </configuration>
      </plugin>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-bundle-plugin</artifactId>
       <extensions>true</extensions>
       <configuration>
        <instructions>
         <Bundle-Category>cq5</Bundle-Category>
         <Export-Package> com.day.cq5.myhandler </Export-Package>
        </instructions>
       </configuration>
      </plugin>
     </plugins>
    </build> 
    <!-- ====================================================================== --> 
    <!-- D E P E N D E N C I E S --> 
    <!-- ====================================================================== -->
    <dependencies>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-api</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-core</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq</groupId>
      <artifactId>cq-commons</artifactId>
     </dependency>
     <dependency>
      <groupId>javax.jcr</groupId>
      <artifactId>jcr</artifactId>
     </dependency>
     <dependency>
      <groupId>org.apache.felix</groupId>
      <artifactId>org.osgi.compendium</artifactId>
     </dependency>
     <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-lang</groupId>
      <artifactId>commons-lang</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-collections</groupId>
      <artifactId>commons-collections</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-gfx</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-text</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.workflow</groupId>
      <artifactId>cq-workflow-api</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.wcm</groupId>
      <artifactId>cq-wcm-foundation</artifactId>
      <version>5.2.22</version>
     </dependency>
    </dependencies>
   ```

1. 创建资源包 `com.day.cq5.myhandler` 中包含Java™类的 `myBundle/src/main/java`:

   1. 在myBundle下，右键单击 `src/main/java`，选择新建，然后选择包。
   1. 将其命名为 `com.day.cq5.myhandler` 并单击“完成”。

1. 创建Java™类 `MyHandler`:

   1. 在日蚀，在 `myBundle/src/main/java`，右键单击 `com.day.cq5.myhandler` 包中，选择新建，然后选择类。
   1. 在对话框窗口中，将Java™类命名为MyHandler，然后单击“完成”。 Eclipse会创建并打开文件MyHandler.java。
   1. 在 `MyHandler.java` 将现有代码替换为以下内容，然后保存更改：

   ```java
   package com.day.cq5.myhandler; 
   import java.awt.Color; 
   import java.awt.Rectangle; 
   import java.awt.image.BufferedImage; 
   import java.io.IOException; 
   import java.io.InputStream; 
   import java.io.InputStreamReader; 
   import javax.jcr.Node; 
   import javax.jcr.RepositoryException; 
   import javax.jcr.Session; 
   import org.apache.commons.io.IOUtils; 
   import org.slf4j.Logger; 
   import org.slf4j.LoggerFactory; 
   import com.day.cq.dam.api.metadata.ExtractedMetadata; 
   import com.day.cq.dam.core.AbstractAssetHandler; 
   import com.day.image.Font; 
   import com.day.image.Layer; 
   import com.day.cq.wcm.foundation.ImageHelper; 
   
   /** 
    * The <code>MyHandler</code> can extract text files 
    * @scr.component inherit="true" immediate="true" metatype="false" 
    * @scr.service 
    * 
    **/ 
   
   public class MyHandler extends AbstractAssetHandler { 
    /** * Logger instance for this class. */ 
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class); 
    /** * Music icon margin */ 
    private static final int MARGIN = 10; 
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */ 
    public String[] getMimeTypes() {
     return new String[] {"text/plain"}; 
    }
   
    public ExtractedMetadata extractMetadata(Node asset) { 
     ExtractedMetadata extractedMetadata = new ExtractedMetadata(); 
     InputStream data = getInputStream(asset); 
     try { 
      // read text data 
      InputStreamReader reader = new InputStreamReader(data); 
      char[] buffer = new char[4096]; 
      String text = ""; 
      while (reader.read(buffer) != -1) { 
       text += new String(buffer); 
      } 
      reader.close(); 
      long wordCount = this.wordCount(text); 
      extractedMetadata.setProperty("text", text); 
      extractedMetadata.setMetaDataProperty("Word Count",wordCount); 
      setMimetype(extractedMetadata, asset); 
     } catch (Throwable t) { 
      log.error("handling error: " + t.toString(), t); 
     } finally { 
      IOUtils.closeQuietly(data); 
     } 
     return extractedMetadata; } 
    // ----------------------< helpers >---------------------------------------- 
    protected BufferedImage getThumbnailImage(Node node) { 
     ExtractedMetadata metadata = extractMetadata(node); 
     final String text = (String) metadata.getProperty("text"); 
     // create text layer 
     final Layer layer = new Layer(500, 600, Color.WHITE); 
     layer.setPaint(Color.black); 
     Font font = new Font("Arial", 12); 
     String displayText = this.getDisplayText(text, 600, 12); 
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text 
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0); 
     } 
     // create watermark and merge with text layer 
     Layer watermarkLayer; 
     try { 
      final Session session = node.getSession(); 
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png"); 
      watermarkLayer.setX(MARGIN); 
      watermarkLayer.setY(MARGIN); 
      layer.merge(watermarkLayer); 
     } catch (RepositoryException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); 
     } catch (IOException e) { 
      // TODO Auto-generated catch block 
      e.printStackTrace(); } 
     layer.crop(new Rectangle(510, 600)); 
     return layer.getImage(); } 
    // ---------------< private >----------------------------------------------- 
    /** 
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px) 
     * * @return the text which will fit into the box 
     */ 
    private String getDisplayText(String text, int height, int fontheight) { 
     String trimmedText = text.trim(); 
     int numOfLines = height / fontheight; 
     String lines[] = trimmedText.split("\n"); 
     if (lines.length <= numOfLines) { 
      return trimmedText; 
     } else { 
      String cuttetText = ""; 
      for (int i = 0; i < numOfLines; i++) { 
       cuttetText += lines[i] + "\n"; 
      } 
      return cuttetText; 
     } 
    } 
    /**
     * * This method counts the number of words in a string 
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */ 
    private long wordCount(String text) { 
     // We need to keep track of the last character, if we have two whitespace in a row we don't want to double count.
     // The starting of the document is always a whitespace.
     boolean prevWhiteSpace = true; 
     boolean currentWhiteSpace = true; 
     char c; long numwords = 0; 
     int j = text.length(); 
     int i = 0; 
     while (i < j) { 
      c = text.charAt(i++); 
      if (c == 0) { break; } 
      currentWhiteSpace = Character.isWhitespace(c); 
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; } 
      prevWhiteSpace = currentWhiteSpace; 
     } 
     // If we do not end with a whitespace then we need to add one extra word.
     if (!currentWhiteSpace) { numwords++; } 
     return numwords; 
    } 
   }
   ```

1. 编译Java™类并创建包：

   1. 右键单击myBundle项目，选择 **[!UICONTROL 运行方式]**，则 **[!UICONTROL Maven安装]**.
   1. 包 `myBundle-0.0.1-SNAPSHOT.jar` （包含编译的类）在下创建 `myBundle/target`.

1. 在CRX Explorer中，在 `/apps/myApp`. 名称= `install`，类型= `nt:folder`.
1. 复制包 `myBundle-0.0.1-SNAPSHOT.jar` 然后储存在下面 `/apps/myApp/install` （例如，使用WebDAV）。 新文本处理程序现在在Experience Manager中处于活动状态。
1. 在浏览器中，打开Apache Felix Web管理控制台。 选择组件选项卡并禁用默认文本处理程序 `com.day.cq.dam.core.impl.handler.TextHandler`.

## 基于命令行的媒体处理程序 {#command-line-based-media-handler}

Experience Manager允许您在工作流中运行任何命令行工具，以转换资产（如ImageMagick）并将新演绎版添加到资产。 在托管Experience Manager服务器的磁盘上安装命令行工具，并向工作流添加和配置流程步骤。 调用的进程，称为 `CommandLineProcess`，会根据特定MIME类型进行过滤，并根据新演绎版创建多个缩略图。

可以自动在中运行和存储以下转化 [!DNL Experience Manager Assets]:

* EPS和AI转换使用 [ImageMagick](https://www.imagemagick.org/script/index.php) 和 [Ghostscript](https://www.ghostscript.com/)
* 使用FLV视频转码 [FFmpeg](https://ffmpeg.org/)
* MP3编码(使用 [跛脚](https://lame.sourceforge.io)
* 音频处理使用 [SOX](https://sox.sourceforge.io)

>[!NOTE]
>
>在非Windows系统上，FFMpeg工具在为文件名中带单引号(&#39;)的视频资产生成演绎版时返回错误。 如果视频文件的名称包含单引号，请在上传到Experience Manager之前将其删除。

的 `CommandLineProcess` 进程会按照其列出顺序执行以下操作：

* 根据特定的mime类型（如果已指定）筛选文件。
* 在托管Experience Manager服务器的磁盘上创建临时目录。
* 将原始文件流式传输到临时目录。
* 执行由步骤的参数定义的命令。 命令正在临时目录内执行，且用户具有运行Experience Manager的权限。
* 将结果流回Experience Manager服务器的呈现文件夹。
* 删除临时目录。
* 根据这些演绎版创建缩略图（如果已指定）。 缩略图的数量和维度由步骤的参数定义。

### 使用ImageMagick的示例 {#an-example-using-imagemagick}

以下示例显示如何设置命令行流程步骤。 每次将具有MIME类型gif或tiff的资产添加到 `/content/dam` 在Experience Manager服务器上，原始图像的翻转图像会与另外三个缩略图（140x100、48x48和10x250）一起创建。

要执行此流程步骤，请使用ImageMagick。 在托管Experience Manager服务器的磁盘上安装ImageMagick :

1. 安装ImageMagick。 请参阅 [ImageMagick文档](https://www.imagemagick.org/script/download.php) 以了解更多信息。
1. 设置工具以便运行 `convert` 在命令行中。
1. 要查看工具是否安装正确，请运行以下命令 `convert -h` 在命令行中。

   此时会显示一个“帮助”屏幕，其中包含转换工具的所有可能选项。

   >[!NOTE]
   >
   >在Windows®的某些版本(例如Windows® SE)中，转换命令无法运行，因为它与Windows®安装中的本机转换实用程序冲突。 在本例中，请提及用于将图像文件转换为缩略图的ImageMagick实用程序的完整路径。 例如：`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`。

1. 要查看该工具是否运行正确，请向工作目录中添加JPG映像并运行命令 `convert <image-name>.jpg -flip <image-name>-flipped.jpg` 在命令行中。

   翻转的图像会添加到目录中。

然后，将命令行流程步骤添加到 **[!UICONTROL DAM 更新资产]**&#x200B;工作流：

1. 转到 **[!UICONTROL 工作流]** 控制台。
1. 在 **[!UICONTROL 模型]** ，编辑 **[!UICONTROL DAM更新资产]** 模型。
1. 更改 **[!UICONTROL 支持Web的演绎版]** 步骤如下：

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. 保存工作流。

要测试修改后的工作流，请将资产添加到 `/content/dam`.

1. 在文件系统中，获取您选择的TIFF图像。 将其重命名为 `myImage.tiff` 然后复制到 `/content/dam`，例如使用WebDAV。
1. 转到 **[!UICONTROL CQ5 DAM]** 控制台，例如 `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. 打开资产 `myImage.tiff` 并验证已创建翻转的图像和三个缩略图。

#### 配置CommandLineProcess进程步骤 {#configuring-the-commandlineprocess-process-step}

本节介绍如何设置 **[!UICONTROL 的]**&#x200B;进程参数`CommandLineProcess`。将 [!UICONTROL 进程参数] 使用逗号，并且不要以空格开头值。

| 参数格式 | 描述 |
|---|---|
| mime:&lt;mime-type> | 可选参数。 如果资产的MIME类型与其中一个参数的MIME类型相同，则应用该过程。 <br>可以定义多种MIME类型。 |
| tn:&lt;width>:&lt;height> | 可选参数。 该过程会创建一个缩略图，并使用参数中定义的维度。 <br>可以定义多个缩略图。 |
| cmd: &lt;command> | 定义要运行的命令。 语法取决于命令行工具。 只能定义一个命令。 <br>以下变量可用于创建命令：<br>`${filename}`:输入文件的名称，例如original.jpg <br> `${file}`:输入文件的完整路径名，例如/tmp/cqdam0816.tmp/original.jpg <br> `${directory}`:输入文件的目录，例如/tmp/cqdam0816.tmp <br>`${basename}`:不带扩展名的输入文件的名称，例如原始文件 <br>`${extension}`:输入文件的扩展名，例如jpg |

例如，如果ImageMagick安装在托管Experience Manager服务器的磁盘上，并且您使用 **CommandLineProcess** 作为实施，且以下值为 **进程参数**:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

然后，当工作流运行时，该步骤仅适用于具有 `image/gif` 或 `mime:image/tiff` 为mime类型。 它会创建原始的翻转图像，将其转换为.jpg，并创建三个具有尺寸的缩览图：140x100、48x48和10x250。

使用以下方法 [!UICONTROL 进程参数] 要使用ImageMagick创建三个标准缩略图，请执行以下操作：

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

使用以下方法 [!UICONTROL 进程参数] 要使用ImageMagick创建启用web的演绎版，请执行以下操作：

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>的 `CommandLineProcess` 步骤仅适用于资产（类型的节点） `dam:Asset`)或资产的子项。
