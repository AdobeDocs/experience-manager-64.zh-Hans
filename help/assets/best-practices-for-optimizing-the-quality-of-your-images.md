---
title: 优化图像质量的最佳实践
description: 了解在Dynamic Media中优化图像质量的最佳实践
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 2e90bea1-eaac-457b-8588-b18d3a6e8d91
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1497'
ht-degree: 6%

---

# 优化图像质量的最佳实践 {#best-practices-for-optimizing-the-quality-of-your-images}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

优化图像质量可能是一个非常耗时的过程，因为渲染可接受的结果会涉及到许多因素。 结果在一定程度上是主观的，因为个人对图像质量的看法不同。 结构化实验是关键。

AEM包含100多个dynamic media图像交付命令，用于调整和优化图像以及渲染结果。 以下准则可帮助您使用一些基本的命令和最佳实践来简化流程并快速获得良好结果。

## 图像格式的最佳实践(&amp;fmt=) {#best-practices-for-image-format-fmt}

* JPG或PNG是交付高质量且具有可管理大小和重量的图像的最佳选择。
* 如果URL中未提供format命令，则Dynamic Media图像交付默认为交付JPG。
* JPG的压缩比率为10:1，通常生成的图像文件较小。 PNG的压缩比率约为2:1，但有些情况除外，例如当图像包含白色背景时。 但是，通常PNG文件大于JPG文件。
* JPG使用有损压缩，这意味着在压缩期间图像元素（像素）会被丢弃。 PNG则使用无损压缩。
* JPG通常压缩照片图像，其保真度优于具有锐边和对比度的合成图像。
* 如果图像包含透明度，请使用PNG，因为JPG不支持透明度。

作为图像格式的最佳实践，请首先从最常见的设置开始 `&fmt=JPG`.

## 图像大小的最佳实践 {#best-practices-for-image-size}

动态减小图像大小是最常见的任务之一。 它涉及指定大小，（可选）指定用于缩小图像的缩减采样模式。

* 对于图像大小调整，最好且最直接的方法是使用 `&wid=<value>` 和 `&hei=<value>,`或 `&hei=<value>`. 这些参数会根据宽高比自动设置图像宽度。
* `&resMode=<value>`控制用于缩减采样的算法。 开始于 `&resMode=sharp2`. 此值可提供最佳图像质量。 使用缩减采样 `value =bilin` 速度更快，通常会导致出现锯齿伪像。

作为图像大小调整的最佳实践，请使用 `&wid=<value>&hei=<value>&resMode=sharp2` 或 `&hei=<value>&resMode=sharp2`

## 图像锐化的最佳实践 {#best-practices-for-image-sharpening}

在控制网站上的图像时，图像锐化是最复杂的方面，而且会导致许多错误。 请参阅 [Adobe Dynamic Media Classic图像质量和锐化最佳实践](/help/assets/assets/sharpening_images.pdf) 指南。

另请参阅 [使用钝化蒙版锐化图像](https://helpx.adobe.com/photoshop/using/adjusting-image-sharpness-blur.html).

通过AEM，您可以在摄取、交付或两者时锐化图像。 但是，在大多数情况下，您应该只使用一种方法或另一种方法锐化图像，而不是同时使用这两种方法。 通常，在交付时通过URL锐化图像可获得最佳效果。

可以使用两种图像锐化方法：

* 简单锐化( `&op_sharpen`) — 与Photoshop中使用的锐化滤镜类似，简单锐化会在动态调整大小后对图像的最终视图应用基本锐化。 但是，用户无法配置此方法。 最佳做法是，除非有需要，否则不使用&amp;op_sharpen。
* 钝化蒙版( `&op_USM`)- USM锐化是行业标准的锐化滤镜。 最佳实践是按照以下准则使用USM锐化来锐化图像。 USM锐化允许您控制以下三个参数：

   * `&op_sharpen=`数量，半径，阈值

      * **[!UICONTROL 金额]** （0-5，效果的强度。）
      * **[!UICONTROL 半径]** (0-250，在锐化对象周围绘制的“锐化线”宽度（以像素为单位）。

             请记住，半径和量参数彼此相对工作。 减少半径可通过增加量来补偿。 半径允许进行更精细的控制，因为较低值仅锐化边缘像素，而较高值锐化较宽范围的像素。
         
      * **[!UICONTROL 阈值]** （0-255，效果的敏感性。）

             此参数确定锐化的像素与周围区域必须有多大的不同，才会被视为边缘像素，而滤镜会锐化这些像素。 **[!UICONTROL threshold]**参数有助于避免过度锐化颜色相似的区域，如肤色。 例如，阈值为12时，会忽略肤色亮度的细微变化，以避免添加“杂色”，同时仍会为高对比度区域添加边缘对比度，如睫毛与皮肤相遇的地方。
         
         有关如何设置这三个参数的更多信息（包括与过滤器一起使用的最佳实践），请参阅 [Adobe Dynamic Media Classic图像质量和锐化最佳实践](/help/assets/assets/sharpening_images.pdf) 指南(也适用于AEM上的Dynamic Media)。
   * AEM还允许您控制第四个参数：单色(0,1)。 此参数确定是否使用值0分别将USM锐化应用于每个颜色组件，或者使用值1将USM锐化应用于图像亮度/强度。


作为最佳实践，请首先使用USM锐化radius参数。 可以开始使用的半径设置如下：

* **[!UICONTROL 网站]**:0.2-0.3像素
* **[!UICONTROL 照片打印(250-300 ppi)]**:0.3-0.5像素
* **[!UICONTROL 胶印(266-300 ppi)]**:0.7-1.0像素
* **[!UICONTROL 画布打印(150 ppi)]**:1.5-2.0像素

将金额从1.75逐步增加到4。 如果锐化仍不是您所需的方式，请将半径增加一个小数点，然后再次运行从1.75到4的数量。 根据需要重复。

将monochrome参数设置保留为0。

### JPEG压缩的最佳实践(&amp;qlt=) {#best-practices-for-compression-qlt}

* 此参数可控制JPG编码质量。 值越大，表示图像质量越高，但文件也越大；或者，值越低，表示图像质量越低，但文件越小。 此参数的范围为0-100。
* 要优化质量，请勿将参数值设置为100。 设置为90或95与设置为100几乎没有区别，但设置为100会不必要地增加图像文件的大小。 因此，要优化质量，同时避免图像文件过大，请设置 `qlt=<value>` 90或95。
* 要优化较小的图像文件大小，但将图像质量保持在可接受的级别，请将 `qlt=<value>` 80。 低于70到75的值会导致图像质量显着下降。
* 作为最佳实践，若要停留在中间，请设置 `qlt=<value>` 到85岁，在中间。
* 在中使用色度标志 `qlt=`

   * 的 `qlt=` 参数具有第二个设置，允许您使用值打开RGB色度缩减采样 `,1` 或使用值 `,0`.
   * 要保持简单，请首先关闭RGB色度缩减采样(`,0`)。 此设置通常可以提高图像质量，特别是对于具有大量锐边和对比度的合成图像。

作为JPG压缩使用的最佳实践 `&qlt=85,0`.

## JPEG大小调整的最佳实践(&amp;jpegSize=) {#best-practices-for-jpeg-sizing-jpegsize}

jpegSize是一个有用的参数，可确保在将图像传送到内存有限的设备时，该图像不会超过某个大小。

* 此参数以千字节(`jpegSize=<size_in_kilobytes>`)。 它定义了图像交付所允许的最大大小。
* `&jpegSize=` 与JPG压缩参数交互 `&qlt=`. 如果JPG响应具有指定的JPG压缩参数(`&qlt=`)未超过jpegSize值，则返回图像时将使用 `&qlt=` 定义。 否则， `&qlt=` 会逐渐减小，直到图像符合允许的最大大小，或直到系统确定图像不适合并返回错误为止。

作为最佳实践，请设置 `&jpegSize=` 并添加参数 `&qlt=` 如果您将JPG图像传送到内存有限的设备。

## 最佳实践摘要 {#best-practices-summary}

最佳做法是，要实现高图像质量和小文件大小，请首先结合以下参数：

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

在大多数情况下，这种设置组合会产生出色的效果。

如果图像需要进一步优化，请从将半径设置为0.2或0.3开始，逐渐微调锐化（USM锐化）参数。然后，将锐化量从1.75逐渐增加到最大4(相当于Photoshop的400%)。 检查是否达到了所需的结果。

如果锐化结果仍不令人满意，请按小数点增加半径。 对于每次递增的小数点，重新将金额从1.75开始，并逐渐将其增加到4。 重复此过程，直到达到所需结果。 尽管上述值是创意工作室已经验证的一种方法，但请记住，您可以从其他值开始，并遵循其他策略。 结果是否令您满意是一个主观问题，因此结构化实验是关键。

在您进行实验时，您可能还会发现以下常规建议有助于优化工作流：

* 直接在URL上实时尝试并测试不同的参数。
* 作为最佳实践，请记住，可以将Dynamic Media图像提供命令分组到图像预设中。 图像预设基本上就是具有自定义预设名称(如 `$thumb_low$` 和 `&product_high$`. URL路径中的自定义预设名称会调用这些预设。 此类功能可帮助您管理网站上不同图像使用模式的命令和质量设置，并缩短URL的整体长度。
* AEM还提供了更高级的图像质量调整方法，例如在摄取时应用锐化图像。 对于高级用例，如果可能需要进一步调整和优化渲染结果， [Adobe Professional Services](https://www.adobe.com/cn/experience-cloud/consulting-services.html) 可帮助您了解自定义的见解和最佳实践。
