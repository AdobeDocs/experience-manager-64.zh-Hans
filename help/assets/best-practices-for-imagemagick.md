---
title: 安装和配置ImageMagick以与AEM Assets一起使用
description: 了解ImageMagick软件、如何安装它、设置命令行处理步骤以及使用它编辑、合成和从图像生成缩览图。
contentOwner: AG
feature: Renditions,Developer Tools
role: Administrator
translation-type: tm+mt
source-git-commit: 29e3cd92d6c7a4917d7ee2aa8d9963aa16581633
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---


# 安装并配置ImageMagick以与AEM Assets {#install-and-configure-imagemagick-to-work-with-aem-assets}一起使用

ImageMagick是用于创建、编辑、合成或转换位图图像的软件插件。 它可以读写各种格式（超过200种）的图像，包括PNG、JPEG、JPEG-2000、GIF、TIFF、DPX、EXR、WebP、Postscript、PDF和SVG。 使用ImageMagick调整图像大小、翻转、镜像、旋转、扭曲、剪切和变换图像。 您还可以使用ImageMagick调整图像颜色、应用各种特殊效果或绘制文本、直线、多边形、椭圆和曲线。

使用命令行中的Adobe Experience Manager(AEM)媒体处理函数通过ImageMagick处理图像。 要使用ImageMagick处理各种文件格式，请参阅[资产文件格式最佳实践](assets-file-format-best-practices.md)。 要了解所有支持的文件格式，请参阅[资产支持的格式](assets-formats.md)。

要使用ImageMagick处理大型文件，请考虑内存要求高于常规要求、IM策略需要的潜在更改以及对性能的总体影响。 内存要求取决于各种因素，如分辨率、位深度、颜色用户档案和文件格式。 如果您打算使用ImageMagick处理超大文件，请正确对AEM服务器进行基准测试。 最后提供了一些有用的资源。

>[!NOTE]
>
>如果您在Adobe Managed Services(AMS)上使用AEM，则如果您计划处理大量大型PSD或PSB文件，请联系Adobe客户服务中心。 Experience Manager可能无法处理超30000 x 23000像素的高分辨率PSB文件。

## 安装ImageMagick {#installing-imagemagick}

ImageMagic安装文件的多个版本可用于各种操作系统。 为您的操作系统使用适当的版本。

1. 下载适合您的操作系统的[ImageMagick安装文件](https://www.imagemagick.org/script/download.php)。
1. 要在承载AEM服务器的磁盘上安装ImageMagick，请启动安装文件。

1. 将路径环境变量设置为ImageMagic安装目录。
1. 要检查安装是否成功，请执行`identify -version`命令。

## 设置命令行进程步骤{#set-up-the-command-line-process-step}

您可以为您的特定用例设置命令行进程步骤。 每次在AEM服务器上向`/content/dam`添加JPEG图像文件时，请执行以下步骤以生成翻转的图像和缩览图（140x100、48x48、319x319和1280x1280）：

1. 在AEM服务器上，转到工作流控制台(`https://[aem_server]:[Port]/workflow`)并打开&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;工作流模型。
1. 从&#x200B;**[!UICONTROL DAM更新资产]**&#x200B;工作流模型中，打开&#x200B;**[!UICONTROL EPS缩略图（由ImageMagick提供）]**&#x200B;步骤。
1. 在&#x200B;**[!UICONTROL 参数选项卡]**&#x200B;中，将`image/jpeg`添加到&#x200B;**[!UICONTROL Mime类型]**&#x200B;列表。

   ![mime_types_jpeg](assets/mime_types_jpeg.png)

1. 在&#x200B;**[!UICONTROL 命令]**&#x200B;框中，输入以下命令：

   `convert ./${filename} -flip ./${basename}.flipped.jpg`

1. 选择&#x200B;**[!UICONTROL 删除生成的演绎版]**&#x200B;和&#x200B;**[!UICONTROL 生成Web演绎版]**&#x200B;标志。

   ![select_flags](assets/select_flags.png)

1. 在&#x200B;**[!UICONTROL “启用Web的图像”]**&#x200B;选项卡中，指定尺寸为1280x1280像素的再现的详细信息。 此外，在&#x200B;**[!UICONTROL Mimetype]**&#x200B;框中指定i *mage/jpeg*。

   ![web_enabled_image](assets/web_enabled_image.png)

1. 点按/单击&#x200B;**[!UICONTROL 确定]**&#x200B;以保存更改。

   >[!NOTE]
   >
   >`convert`命令可能无法与某些Windows版本（例如Windows SE）一起运行，因为它与作为Windows安装一部分的本机`convert`实用程序冲突。 在这种情况下，请提及ImageMagick实用程序的完整路径。 例如，指定
   >
   >`"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ./${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`

1. 打开&#x200B;**[!UICONTROL 处理缩略图]**&#x200B;步骤，并在&#x200B;**[!UICONTROL 跳过MIME类型]**&#x200B;下添加MIME类型`image/jpeg`。

   ![skip_mime_types](assets/skip_mime_types.png)

1. 在&#x200B;**[!UICONTROL 启用Web的图像]**&#x200B;选项卡中，在&#x200B;**[!UICONTROL 跳过列表]**&#x200B;下添加MIME类型`image/jpeg`。 点按/单击&#x200B;**[!UICONTROL 确定]**&#x200B;以保存更改。

   ![web_enabled](assets/web_enabled.png)

1. 保存工作流。
1. 要检查ImageMagic是否能够正确处理图像，请将JPG图像上传到AEM Assets。 验证是否已翻转的图像及其演绎版已生成。

## 缓解安全漏洞{#mitigating-security-vulnerabilities}

存在多个与使用ImageMagick处理图像相关的安全漏洞。 例如，处理用户提交的图像涉及远程代码执行(RCE)的风险。

此外，各种图像处理插件都依赖于ImageMagick库，包括但不限于PHP的图像快速、Ruby的快照和平装剪辑以及Node.js的图像快速。

如果您使用ImageMagick或受影响的库，Adobe建议您通过执行以下至少一种任务（但最好同时执行两种操作）来减轻已知的漏洞：

1. 在将所有图像文件发送到ImageMagick进行处理之前，请先验证所有图像文件是否以与您支持的图像文件类型对应的预期[&quot;magic bytes&quot;](https://en.wikipedia.org/wiki/List_of_file_signatures)开头。
1. 使用策略文件禁用易受攻击的ImageMagick编码器。 `/etc/ImageMagick`中可找到ImageMagick的全局策略。

>[!MORELIKETHIS]
>
>* [使用AEM Assets处理各种文件格式的最佳实践](assets-file-format-best-practices.md)
>* [ImageMagick的命令行选项](https://www.imagemagick.org/script/command-line-options.php)
>* [ImageMagick使用的基本和高级示例](https://www.imagemagick.org/Usage/)
>* [针对ImageMagick的资产性能调整](performance-tuning-guidelines.md)
>* [完整列表AEM Assets支持的文件格式](assets-formats.md)
>* [了解文件格式和图像的内存开销](https://www.scantips.com/basics1d.html)

