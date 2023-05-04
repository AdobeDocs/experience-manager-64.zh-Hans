---
title: 基于XDP的自适应表单中的XFA支持
seo-title: XFA support in XDP-based adaptive forms
description: 列出自适应表单中支持的XFA事件、属性、脚本和验证。
seo-description: Lists supported XFA events, properties, scripts, and validation in adaptive forms.
uuid: 2f976de3-2cdf-4bbb-acd1-048a498930f0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: eaf60421-097e-4feb-b661-433a512470ab
feature: Adaptive Forms
exl-id: 86596819-8108-409e-af14-4634e8a1959d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 5%

---

# 基于XDP的自适应表单中的XFA支持 {#xfa-support-in-xdp-based-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

## 简介 {#introduction}

自适应表单支持在XDP文件中定义的各种XFA事件、属性、脚本和验证，包括：

* 执行在XDP文件中的事件上定义的脚本。
* 捕获XDP文件中字段的默认值和行为属性。
* 执行XDP文件中定义的验证脚本。

基于XDP文件创建自适应表单后，表单创作UI中会自动填充属性、事件和验证。 但是，表单作者可以覆盖其中一些元素以创建替代体验。

本文列出了自适应表单中受支持的XFA事件、属性和验证，并说明如何在自适应表单中覆盖它们。

## 自适应表单中支持的XFA元素及其映射 {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### 字段 {#fields}

使用XDP文件创建自适应表单后，可以将XFA字段拖放到自适应表单上。 下表列出了XFA字段如何映射到自适应表单字段。

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA字段或容器</strong></p> </td> 
   <td><p><strong>相应的自适应表单组件</strong></p> </td> 
  </tr>
  <tr>
   <td><p>按钮 </p> </td> 
   <td><p>按钮</p> </td> 
  </tr>
  <tr>
   <td><p>复选框 </p> </td> 
   <td><p>复选框</p> </td> 
  </tr>
  <tr>
   <td><p>列表框 </p> </td> 
   <td><p>下拉列表</p> </td> 
  </tr>
  <tr>
   <td><p>日期/时间字段 </p> </td> 
   <td><p>日期选取器</p> </td> 
  </tr>
  <tr>
   <td><p>签名涂写</p> </td> 
   <td><p>潦草签名</p> </td> 
  </tr>
  <tr>
   <td><p>数值字段 </p> </td> 
   <td><p>数值框</p> </td> 
  </tr>
  <tr>
   <td><p>小数字段</p> </td> 
   <td><p>数值框</p> </td> 
  </tr>
  <tr>
   <td><p>文本字段 </p> </td> 
   <td><p>文本框</p> </td> 
  </tr>
  <tr>
   <td><p>密码字段 </p> </td> 
   <td><p>密码框</p> </td> 
  </tr>
  <tr>
   <td><p>图像</p> </td> 
   <td><p>图像</p> </td> 
  </tr>
  <tr>
   <td><p>文本</p> </td> 
   <td><p>文本</p> </td> 
  </tr>
  <tr>
   <td><p>子表单 </p> </td> 
   <td><p>面板</p> </td> 
  </tr>
  <tr>
   <td><p>区域（组）</p> </td> 
   <td><p>面板</p> </td> 
  </tr>
  <tr>
   <td><p>子表单集 </p> </td> 
   <td><p>面板</p> </td> 
  </tr>
 </tbody>
</table>

### 属性 {#properties}

下表捕获了XDP文件中定义的各种XFA脚本在自适应表单中的行为方式。

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA组件属性</strong></p> </td> 
   <td><p><strong>自适应表单中的相应行为</strong></p> </td> 
  </tr>
  <tr>
   <td><p>somExpression </p> </td> 
   <td><p>以自适应形式映射到绑定引用(bindRef)属性。</p> </td> 
  </tr>
  <tr>
   <td><p>存在 </p> </td> 
   <td><p>在自适应表单中映射到可见属性。 您可以使用可见性表达式覆盖它。</p> </td> 
  </tr>
  <tr>
   <td><p>访问 </p> </td> 
   <td><p>在自适应表单中映射到enabled属性。 您可以使用访问表达式覆盖它。</p> </td> 
  </tr>
  <tr>
   <td><p>辅助功能：角色 </p> </td> 
   <td><p>在自适应表单中映射到角色属性。</p> </td> 
  </tr>
  <tr>
   <td><p>辅助功能：seakPriority </p> </td> 
   <td><p>以自适应形式映射到skePriority属性。</p> </td> 
  </tr>
  <tr>
   <td><p>辅助功能：seakText</p> </td> 
   <td><p>在自适应表单中映射到自定义辅助功能文本。</p> </td> 
  </tr>
  <tr>
   <td><p>辅助功能：toolTip </p> </td> 
   <td><p>在自适应表单中映射到简短描述属性。</p> </td> 
  </tr>
  <tr>
   <td><p>字幕<em> （所有字段类型）</em></p> </td> 
   <td><p>在自适应表单中映射到标题属性。</p> </td> 
  </tr>
  <tr>
   <td><p>displayFormat<em> （所有字段类型）</em></p> </td> 
   <td><p>在自适应表单中映射到显示模式。</p> </td> 
  </tr>
  <tr>
   <td><p>rawValue<em> （所有字段类型）</em></p> </td> 
   <td><p>映射到自适应表单中的值属性。</p> </td> 
  </tr>
  <tr>
   <td><p>项目<em> （列表框、复选框）</em></p> </td> 
   <td><p>在自适应表单中映射到options属性。 您可以使用“选项”表达式覆盖它。</p> </td> 
  </tr>
  <tr>
   <td><p>maxChar<em> （文本字段）</em></p> </td> 
   <td><p>在自适应表单中映射到允许的最大字符数属性。</p> </td> 
  </tr>
  <tr>
   <td><p>多线<em> （文本字段）</em></p> </td> 
   <td><p>在自适应表单中映射到允许多行属性。</p> </td> 
  </tr>
  <tr>
   <td><p>fracDigit<em> （数字字段、小数字段）</em></p> </td> 
   <td><p>在自适应表单中映射到Frac digits属性。</p> </td> 
  </tr>
  <tr>
   <td><p>leadDigit<em> （数字字段、小数字段）</em></p> </td> 
   <td><p>在自适应表单中映射到潜在客户位数属性。</p> </td> 
  </tr>
  <tr>
   <td><p>multiSelect<em> （列表框）</em></p> </td> 
   <td><p>映射到自适应表单中允许多个选择属性。</p> </td> 
  </tr>
 </tbody>
</table>

### 脚本 {#scripts}

下表捕获了XDP文件中定义的各种XFA脚本在自适应表单中的行为方式。

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA脚本事件</strong></p> </td> 
   <td><p><strong>自适应表单中的相应行为</strong></p> </td> 
  </tr>
  <tr>
   <td><p>初始化 </p> </td> 
   <td><p>此脚本在运行时执行，不能在自适应表单中覆盖。</p> </td> 
  </tr>
  <tr>
   <td><p>计算</p> </td> 
   <td><p>映射到自适应表单中的计算表达式。</p> </td> 
  </tr>
  <tr>
   <td><p>验证 </p> </td> 
   <td><p>在自适应表单中映射到验证表达式。</p> </td> 
  </tr>
  <tr>
   <td><p>validationState </p> </td> 
   <td><p>此脚本在运行时执行，不能在自适应表单中覆盖。<br /> </p> </td> 
  </tr>
  <tr>
   <td><p>退出 </p> </td> 
   <td><p>此脚本在运行时执行，不能在自适应表单中覆盖。</p> </td> 
  </tr>
  <tr>
   <td><p>单击（按钮字段）</p> </td> 
   <td><p>已映射到按钮的点击表达式。</p> </td> 
  </tr>
  <tr>
   <td><p>支持服务器端脚本</p> </td> 
   <td><p>此脚本在运行时执行，不能在自适应表单中覆盖。</p> </td> 
  </tr>
  <tr>
   <td><p>支持Web服务</p> </td> 
   <td><p>此脚本在运行时执行，不能在自适应表单中覆盖。</p> </td> 
  </tr>
  <tr>
   <td><p>更改（涂写字段、单选按钮、复选框）</p> </td> 
   <td><p>此脚本在运行时执行，不能在自适应表单中覆盖。</p> </td> 
  </tr>
 </tbody>
</table>

### 验证 {#validations}

下表捕获了XFA验证如何映射到自适应表单中的验证。

<table> 
 <tbody>
  <tr>
   <td><p><strong>XFA验证</strong></p> </td> 
   <td><p><strong>自适应表单中的相应验证</strong></p> </td> 
  </tr>
  <tr>
   <td><p>验证模式(formatTest)</p> </td> 
   <td><p>validatePictureClause</p> </td> 
  </tr>
  <tr>
   <td><p>验证模式消息(formatTestMessage)</p> </td> 
   <td><p>validatePictureMessage</p> </td> 
  </tr>
  <tr>
   <td><p>必需(nullTest)</p> </td> 
   <td><p>强制 </p> </td> 
  </tr>
  <tr>
   <td><p>空消息(nullTestMessage) </p> </td> 
   <td><p>mandatoryMessage</p> </td> 
  </tr>
  <tr>
   <td><p>验证脚本(scriptTest)</p> </td> 
   <td><p>validateExp</p> </td> 
  </tr>
  <tr>
   <td><p>验证脚本消息(scriptTestMessage)</p> </td> 
   <td><p>validateMessage</p> </td> 
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>您无法覆盖自适应表单单选按钮和绑定到XFA复选框按钮的复选框组的必填属性。
