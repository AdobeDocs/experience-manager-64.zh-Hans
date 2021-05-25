---
title: 'HTML5表单与PDF forms之间的功能区别 '
seo-title: 'HTML5表单与PDF forms之间的功能区别 '
description: HTML5表单和PDF forms中支持的功能
seo-description: HTML5表单和PDF forms中支持的功能
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
feature: 移动设备表单
exl-id: 2b82e68c-ec11-417d-a8e2-769da9b35140
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 2%

---

# HTML5表单与PDF forms的功能区别{#feature-differentiation-between-html-forms-and-pdf-forms}

下表指定了为HTML5表单和PDF forms提供的功能支持：

<table> 
 <tbody>
  <tr>
   <th>功能</th> 
   <th>HTML5 表单</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>条形码<br /> </td> 
   <td>在用户界面级别不可用。 </td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>签名字段<br /> </td> 
   <td><strong>不支</strong> 持数字签名，但为纸质 <strong>签</strong> 名（如签名）添加了新的Scribble Signaturefield。可以使用<strong>Scribble Signature</strong>字段在表单上涂写其签名。 签名在表单上另存为图像。 您可以在<strong>Scribble Signature</strong>字段中保存地理位置信息。</td> 
   <td>可用于<strong>数字签名</strong>的签名字段。</td> 
  </tr>
  <tr>
   <td>数据合并</td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
  <tr>
   <td>图像</td> 
   <td>数据URI方案用于显示图像。 所有新版浏览器都支持此方案，但每个浏览器支持的图像格式范围存在差异。<br /> </td> 
   <td>支持.gif、.png、.jpeg、.bmp和.tiff格式。</td> 
  </tr>
  <tr>
   <td>分页<br /> </td> 
   <td><p>HTML5表单分为多个面板和框，外观与PDF forms类似。 页面大小是动态计算的。 如果删除或隐藏HTML5表单中某个页面的所有内容，则会隐藏空白页面，并且空白页面上方和下方的页面之间不显示空白空间（空白空间）。</p> <p>如果数据合并或脚本向页面添加内容，则会扩展页面长度以容纳新添加的内容。 表单中不会添加任何新页面以容纳新添加的内容。 </p> <p><strong>注意：</strong> 删除或隐藏HTML5表单中某个页面的所有内容后，空白页面（空白）在第1页和第2页之间保持可见，但在任何其他页面之间不可见。</p> </td> 
   <td>PDF中的分页取决于合并的数据内容或用户内容，并且页面计数会据此进行增加/减少。</td> 
  </tr>
  <tr>
   <td>页眉/页脚 </td> 
   <td>支持。<br /> <br /> 由于HTML5移动表单不支持分页，因此页眉和页脚仅显示一次。但是，您可以在布局中将它们设置为在移动设备表单预览的多个位置显示。<br /> </td> 
   <td>支持。</td> 
  </tr>
  <tr>
   <td>自定义小组件</td> 
   <td>您可以自定义小组件以增强移动设备上的用户体验。<br /> </td> 
   <td>所有小组件都已锁定，无法插入自定义小组件。<br /> </td> 
  </tr>
  <tr>
   <td>XFA脚本API</td> 
   <td>支持最常用的XFA脚本结构。 有关支持的结构的详细列表，请参阅<a href="/help/forms/using/scripting-support.md">脚本支持</a>。</td> 
   <td>支持所有XFA脚本结构。</td> 
  </tr>
  <tr>
   <td>Acrobat Script API </td> 
   <td>HTML5表单支持最常用的API。 有关详细信息，请参阅<a href="/help/forms/using/scripting-support.md">脚本支持</a>。</td> 
   <td>如果PDF文件在Acrobat或Reader中打开，则它也支持Acrobat提供的所有脚本API。</td> 
  </tr>
  <tr>
   <td>支持从右到左的语言 </td> 
   <td>支持</td> 
   <td>支持</td> 
  </tr>
 </tbody>
</table>

按照最佳实践为HTML5呈现启用表单模板，并确保HTML5表单和基于XFA的PDF的行为和外观保持一致。 有关最佳实践的详细列表，请参阅[设计HTML5表单的最佳实践。](/help/forms/using/best-practices-for-html5-forms.md)
