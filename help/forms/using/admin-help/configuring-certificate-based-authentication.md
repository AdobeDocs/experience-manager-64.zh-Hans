---
title: 配置基于证书的身份验证
seo-title: Configuring certificate-based authentication
description: 将证书颁发机构(CA)证书导入信任存储，并创建证书映射以进行基于证书的身份验证。
seo-description: Import a Certificate Authority (CA) certificate into the Trust Store and create a certificate mapping for certificate-based authentication.
uuid: 9802a969-6d29-4b80-a4ed-06eb6e66e046
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d958ae65-3008-4d68-9e11-4346e149827f
exl-id: 88932b5b-2acc-4f21-8ce3-b819a990ad30
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# 配置基于证书的身份验证 {#configuring-certificate-based-authentication}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

用户管理通常使用用户名和密码来执行身份验证。 用户管理还支持基于证书的身份验证，您可以使用该身份验证通过Acrobat对用户进行身份验证或以编程方式对用户进行身份验证。 有关以编程方式对用户进行身份验证的详细信息，请参阅 [使用AEM表单进行编程](https://www.adobe.com/go/learn_aemforms_programming_63).

要使用基于证书的身份验证，请将您信任的证书颁发机构(CA)证书导入信任存储区，然后创建证书映射。

## 导入CA证书 {#import-the-ca-certificate}

在导入证书时，选择Trust for Certificate Authentication和Trust for Identity选项，以及您需要的任何其他选项。 有关导入证书的详细信息，请参阅 [管理证书](/help/forms/using/admin-help/certificates.md#managing-certificates).

## 配置证书映射 {#configuring-certificate-mapping}

要为用户启用基于证书的身份验证，请创建证书映射。 A *证书映射* 定义证书属性与域中用户属性之间的映射。 您可以将多个证书映射到同一域。

在您测试证书时，用户管理会上传证书检查，以确保证书符合以下要求：

* 证书有效。
* 您指定的颁发者可以验证证书。
* 证书包含映射所需的属性。
* 您指定的映射将证书仅映射到AEM Forms数据库中的一个用户。 会检查当前用户和已过时（已删除）的用户，以确定他们是否符合映射条件。 因此，如果多个用户（包括过时的用户）考虑属性值，则证书测试会失败。

>[!NOTE]
>
>您无法编辑现有证书映射。

**添加证书映射**

1. 在管理控制台中，单击设置>用户管理>配置>证书映射。
1. 单击新建证书映射，然后在对颁发者列表中，选择信任存储管理中配置的证书别名。
1. 将证书的一个属性映射到用户的属性。 例如，您可以将证书的通用名称映射到用户的登录ID。

   如果证书中属性的内容与用户管理数据库中用户属性的内容不同，则可以使用Java正则表达式（正则表达式）来匹配这两个属性。 例如，如果证书的通用名称为 *Alex Pink（身份验证）* 和 *Alex Pink（签名）* 和用户管理数据库中的通用名称为 *阿历克斯·平克*，则使用正则表达式提取证书属性的必需部分(在本例中为 *阿历克斯·平克*.) 您指定的正则表达式必须符合Java正则表达式规范。

   您可以通过在“自定义顺序”框中指定组的顺序来转换表达式。 自定义顺序将与 `java.util.regex.Matcher.replaceAll()` 方法。 所看到的行为将与该方法的行为相对应，并且必须相应地指定输入字符串（自定义顺序）。

   要测试正则表达式，请在“测试参数”框中输入值，然后单击“测试”。

   您可以在正则表达式中使用以下字符：

   * 。（任意字符）
   * &amp;ast;（发生0次或更多次）
   * ()（在括号中指定组）
   * \（用于将正则表达式字符转义为常规字符）
   * $n（用于指第n组）

   正则表达式示例：

   * 从“Alex Pink（身份验证）”中提取“Alex Pink”

      **Regex:** (.&amp;ast;)\(Authentication\)

   * 从“Alex(Authentication)Pink”中提取“Alex Pink”

      **Regex:** (.&amp;ast;)\（身份验证\）(.&amp;ast;)

   * 从“Alex(Authentication)Pink”中提取“Pink Alex”

      **Regex:** (.&amp;ast;)\（身份验证\）(.&amp;ast;)

      自定义顺序：$2 $1（返回第二组，连接到第一组，由空格字符捕获）

   * 从“smtp:apink@sampleorg.com”中提取“apink@sampleorg.com”

      **Regex:** smtp:(.&amp;ast;)
   有关使用正则表达式的详细信息，请参阅 [关于正则表达式的Java教程](https://java.sun.com/docs/books/tutorial/essential/regex/).

1. 在“对于域”列表中，选择用户的域。
1. 要测试此配置，请单击浏览以上传示例用户证书，单击测试证书，如果配置正确，请单击确定。

**编辑现有证书映射**

1. 在管理控制台中，单击设置>用户管理>配置。
1. 单击证书映射。
1. 选择证书映射以编辑和编辑其配置。 您可以更新正则表达式和自定义顺序。
1. 要测试您所做的更改，请单击浏览以上传示例证书，单击测试证书，然后单击确定。

**删除证书映射**

1. 在管理控制台中，单击设置>用户管理>配置>证书映射。
1. 选中要删除的证书映射复选框，单击删除，然后单击确定。
