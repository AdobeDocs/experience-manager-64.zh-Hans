---
title: 在HTML5表单中使用涂写签名
seo-title: 在HTML5表单中使用涂写签名
description: 'HTML5表单在触控设备上的使用越来越多，一个常见要求是支持签名。 在移动设备上对文档进行签名正成为在移动设备上对表单进行签名的公认方式。 '
seo-description: 'HTML5表单在触控设备上的使用越来越多，一个常见要求是支持签名。 在移动设备上对文档进行签名正成为在移动设备上对表单进行签名的公认方式。 '
uuid: afac2d37-ef0d-428b-aed7-64a00d62792d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: designer
discoiquuid: abb5513f-c824-4dc2-8617-29ea47684afe
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '696'
ht-degree: 0%

---


# 在HTML5表单中使用涂写签名 {#using-scribble-signature-in-html-forms}

HTML5表单在触控设备上的使用越来越多，一个常见要求是支持签名。 划片（用手写笔或手指书写）正成为在移动设备上签署表单的一种公认方式。 HTML5表单和Forms设计器现在支持在表单上设置徒手签名字段的选项。 在浏览器中呈现表单时，您可以使用手写笔、鼠标或触摸在这些字段上签名。

## 如何使用“涂写签名”字段设计表单 {#how-to-design-a-form-using-scribble-signature-field}

1. 在Forms设计师中打开表单。
1. 在页面上拖放“签名涂抹”字段。

   ![designer_scribble](assets/designer_scribble.png)

   >[!NOTE]
   >
   >在Forms设计器中选择的字段的Dimension会在渲染该字段时反映出来。 但是，渲染的签名框的尺寸是根据字段的长宽比计算的，而不是根据Forms设计器中指定的尺寸计算的。

1. 配置签名涂写字段。

   默认情况下，“签名涂抹”字段在iPad上的签名过程中将地理位置信息标记为必填（对于其他设备是可选的）。 通过更改属性的值可以覆盖此默认 `geoLocMandatoryOnIpad` 行为。 此属性在“签名涂写”字段中显示为额外内容。 修改它的步骤有：

   1. 在表单上，选择“签名涂写”字段。
   1. 选择“ **XML源** ”选项卡。

      >[!NOTE]
      >
      >要打开“XML源”选项卡，请单击“ **视图** ”> **“XML源”**。

   1. 在标记 `<ui>` 中找到标 `<field>` 记并修改源代码，使其如下所示：

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. 选择“设 **计视图** ”选项卡。 在确认框中，单击“ **是**”。
   1. 保存表单。

1. 在支持的设备／桌面浏览器上渲染表单。

## 与涂写签名连接 {#interfacing-with-the-scribble-signatures}

### 签名 {#signing}

在将签名涂抹字段添加到表单并呈现后，单击或点按该字段会打开一个对话框。 用户可以使用鼠标、手指或手写笔在由虚线矩形指定的绘图区域中涂抹签名。

![地理位置](assets/geolocation.png)

**A.画** 笔 **B.橡皮** 擦 **C.地理** 位 **置D.地** 理位置信息

### 地理标记 {#geo-tagging}

在创建涂鸦时单击地理位置图标会导致地理位置和时间信息嵌入到字段中。

>[!NOTE]
在iPad上，默认情况下，必须嵌入地理位置信息。

在iPad上，默认情况下不显示地理位置图标，并且当您单击“确定”时会自动嵌入地理位 **置信息**。

对于iPad，可通过将参数值修改为字段的 `geoLocManadatoryOnIpad` init参数 `0`中的值来更改此设置。

* 当地理位置信息是强制的时候，向用户呈现减小的绘图区域。 当用户单击其余区域上的“确 **定** ”图标时，将添加地理位置文本。
* 在其他情况下，向用户显示一个完全可绘制区域。 如果用户选择嵌入地理位置信息，则调整该区域的大小以适应地理位置文本。

### 清除签名 {#clearing-a-signature}

使用此功能时，用户可以单击“橡皮 **擦** ”图标以清除字段并开始。 如果添加了地理位置信息，也会清除该信息。

### 保存签名 {#saving-a-signature}

单击“ **确定** ”图标，将涂抹内容保存为字段中的图像。 图像和值可提交到服务器以进一步处理。 用户单击“确 **定**”后，“涂抹”字段被锁定。 无法使用涂写构件再次编辑签名。

点按或单击“涂抹”字段将以只读模式打开对话框。

![3](assets/3.png)

### 选择笔大小 {#selecting-pen-size}

单击“ **画笔** ”图标以显示可用笔大小的列表。 单击或点按笔大小以使用相应的笔。

### 从表单删除签名 {#delete-signatures-from-the-form}

要从表单中删除签名：

* （移动设备）长按签名字段，在确认对话框中点按 **是**。
* （桌面）将鼠标悬停在签名字段上，单击“ **取消** ”图标，在确认对话框上，单 **击“是”**。
