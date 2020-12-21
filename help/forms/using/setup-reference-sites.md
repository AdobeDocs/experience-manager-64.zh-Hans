---
title: 设置和配置AEM Forms参考站点
seo-title: 设置和配置AEM Forms参考站点
description: AEM Forms参考站点展示了如何使用AEM Forms在组织中实施端对端工作流程。
seo-description: AEM Forms参考站点展示了如何使用AEM Forms在组织中实施端对端工作流程。
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '2922'
ht-degree: 0%

---


# 设置和配置AEM Forms参考站点{#set-up-and-configure-aem-forms-reference-sites}

AEM Forms公司提供参考站点实施，以展示AEM Forms公司如何帮助金融服务行业和政府组织随时随地通过任何设备将复杂交易转化为简单而引人入胜的数字体验。

We.Finance和We.Gov参考站点利用真实案例与现有和潜在客户互动，从初次接触开始，以个性化和经济有效的方式管理通信和交易。

通过参考站点，您可以探索和展示AEM Forms的以下主要功能。

* 引人入胜的响应式自适应表单和交互式通信的简化创作体验。
* 交互式通信，创建可适应设备设置和布局的交互式、个性化和响应式客户通信。
* 整合数据以连接到不同的数据源，通过表单数据模型预填和提交表单数据。
* Forms工作流程，实现业务流程和工作流的自动化。
* 高级用户数据管理和处理功能。
* 与Adobe Sign集成，安全地签署和提交自适应表单。
* 与Adobe Target集成，提供有针对性的建议并执行A/B测试，从表单中最大化ROI。
* 与Adobe Analytics集成，衡量表单或活动的表现，并作出明智的决策。
* 增强的表单填写体验。

参考站点提供可重复使用的资产，您可以将这些资产用作模板来创建自己的资产。

* 与Adobe Sign集成，安全地签署和提交自适应表单。

* 与Adobe Sign集成，安全地签署和提交自适应表单。

## 设置引用站点{#prerequisites-and-steps-to-set-up-reference-sites}的先决条件和步骤

在设置参考站点之前，请确保您具有以下各项：

* **AEM essentials**

   AEM QuickStart、AEM Forms加载项包和参考站点包。 有关附加和参考站点包的详细信息，请参见[AEM Forms版本](https://helpx.adobe.com/cn/aem-forms/kb/aem-forms-releases.html)。

* **SMTP服务**
可以使用任何SMTP服务。

* **Adobe Sign开发人员帐户和Adobe SignAPI应用程序**

   要使用数字签名功能，需要Adobe Sign开发者帐户。 请参阅[Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)。

* 要与AEM Forms集成的Microsoft Dynamics 365的正在运行实例。 要运行引用站点，可将示例数据导入Microsoft Dynamics实例，以预填引用站点中使用的交互式通信。
* 运行的AEM 6.4与Forms加载项包的实例。 有关详细信息，请参阅[安装和配置AEM Forms](installing-configuring-aem-forms-osgi.md)。

按照建议的顺序执行以下步骤来设置和配置引用站点。

<table> 
 <tbody> 
  <tr> 
   <th><strong>步骤</strong></th> 
   <th><strong>配置</strong></th> 
   <th><strong>注释</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">安装和配置AEM Forms</a></td> 
   <td>创作和发布</td> 
   <td>安装和配置AEM Forms作者和发布实例。</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">配置SSL</a></td> 
   <td>作者和发布<br /> </td> 
   <td>启用HTTP over SSL以与Adobe Sign进行安全通信。</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">配置Day CQ链接外部器配置</a></p> </td> 
   <td>作者和发布<br /> </td> 
   <td><p>参考站点使用案例针对不同的交易发送电子邮件。 此设置是通过电子邮件投放新闻稿时必需的。 它确保URL和图像指向发布实例。 </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">配置Day CQ邮件服务</a></td> 
   <td>创作和发布</td> 
   <td>电子邮件通信必需。</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">覆盖默认XSS配置</a></td> 
   <td>发布</td> 
   <td>用于覆盖受xss安全性阻止的$、{和}字符。</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">配置AEM DS设置</a></td> 
   <td>作者</td> 
   <td>配置AEM DS以在发布实例上提交表单，并在创作实例上处理工作流。</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">部署参考站点包</a></td> 
   <td>作者</td> 
   <td>在AEM Forms作者实例上部署参考站点包。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">将示例数据导入Microsoft Dynamics</a></td> 
   <td>创作和发布</td> 
   <td>导入信用卡申请、住房抵押申请和住房保险申请的示例数据演练</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">为Microsoft Dynamics配置OAuth云服务</a></td> 
   <td>创作和发布</td> 
   <td>在AEM Forms配置OAuth云服务，实现AEM Forms与Microsoft Dynamics之间的通信。 </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">配置Adobe Sign调度程序</a></td> 
   <td>作者和发布<br /> </td> 
   <td>更改调度程序配置，每两分钟检查一次状态。</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">配置参考站点Adobe SignCloud Service</a></td> 
   <td>作者和发布<br /> </td> 
   <td>引用站点包附带的配置，需要使用有效凭据进行重新配置。</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">为匿名用户配置Forms通用配置服务</a></td> 
   <td>发布</td> 
   <td>该配置允许匿名用户提交、签署和文档记录生成。</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">修改表单数据模型的Rest Service Swagger文件</a></td> 
   <td>作者和发布<br /> </td> 
   <td>修改环境的服务。</td> 
  </tr> 
 </tbody> 
</table>

## 安装和配置AEM Forms{#install-and-configure-aem-forms}

按照[在OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md)上安装和配置AEM Forms中所述安装和部署AEM Forms。

>[!NOTE]
>
>如果不同计算机上有多个发布实例或作者实例和发布实例，请配置复制和反向复制代理。

## 配置SSL {#ssl}

需要SSL配置才能与Adobe Sign服务器通信。 有关详细步骤，请参阅[启用HTTP Over SSL](/help/sites-administering/ssl-by-default.md)。

>[!CAUTION]
>
>请勿在`/etc/map`文件夹上配置强制SSL。

## 配置Day CQ Link Externalizer配置{#externalizer}

在AEM中，**Externalizer**&#x200B;是一个OSGI服务，它允许您以编程方式转换资源路径(例如，/path/to/my/page)通过预配置DNS来预装路径，从而将其导入外部和绝对URL(例如，https://www.mycompany.com/path/to/my/page)。 请参阅[将URL外部化](/help/sites-developing/externalizer.md)。

>[!CAUTION]
>
>如果使用SSL的自签名证书，请勿外置为HTTPS URL。
>
>此外，对于本地服务器，请使用localhost而不是其主机名。

对创作和发布实例执行以下步骤：

1. 转到位于https://&lt;*hostname>*&#x200B;的OSGi配置：*端口>*/system/console/configMgr。
1. 查找并点按&#x200B;**[!UICONTROL Day CQ Link Externalizer]**&#x200B;配置。

   将打开“Day CQ Link Externalizer”对话框，用于编辑配置。

1. 在Day CQ Link Externalizer对话框中的域字段中：

   * 在创作实例上，指定可从外部系统访问的发布URL。 例如，主机名或发布Web服务器。
   * 在发布实例上，指定作者URL和发布URL。

1. 在作者实例和发布实例上，确保在“域”字段中指定本地服务器URL。
1. 点按&#x200B;**[!UICONTROL 保存]**。等待一段时间，以便所有服务重新启动。

## 配置Day CQ邮件服务{#cqmail}

参考站点实施要求在填写和提交表单时向示例用户发送电子邮件。 通过配置Day CQ邮件服务，您可以提供SMTP服务详细信息，以向客户发送自动电子邮件。 请参阅[配置电子邮件通知](/help/sites-administering/notification.md)。

执行以下步骤以在发布实例上配置邮件服务：

1. 转到位于https://&lt;*hostname>*&#x200B;的OSGi配置：*端口>*/system/console/configMgr。
1. 查找并点按&#x200B;**[!UICONTROL Day CQ Mail Service]**&#x200B;以打开它进行配置。
1. 提供SMTP服务器主机名和端口值。
1. 点按&#x200B;**[!UICONTROL 保存]**。

>[!NOTE]
>
>您可以使用企业SMTP服务或Gmail等公共服务。 有关配置SMTP服务的信息，请参阅SMTP服务文档。

## 覆盖默认的XSS配置{#xss}

We.Finance参考站点的电子邮件模板包含电子邮件中的个性化链接。 这些链接的占位符为`${placeholder}`。 在发送电子邮件之前，这些占位符会被实际值替换。 AEM的默认XSS保护配置不允许HTML内容的URL中出现大括号(**{ }**)。 但是，您可以对发布实例执行以下步骤来覆盖默认配置：

1. 将`/libs/cq/xssprotection/config.xml`复制到`/apps/cq/xssprotection/config.xml`。
1. 打开 `/apps/cq/xssprotection/config.xml`.
1. 在`common-regexps`部分，按如下方式修改`onsiteURL`条目并保存文件。

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>大括号(**{ }**)在HTML内容的URL中包含为可接受的字符。

配置SMTP服务器后，尝试使用Sarah Rose人物填写表单并将其另存为草稿。 另存为草稿时，您可以选择通过电子邮件接收草稿。 点击&#x200B;**“发送电子邮件**”按钮时，如果您收到一封包含指向应用程序草稿的链接的电子邮件，则您的电子邮件配置将成功。 确保使用Sarah的凭据登录以查看草稿。

## 配置AEM DS设置{#aemds}

AEM DS服务设置在参考站点用例中用于电子邮件通信的发布实例上是必需的。 有关在发布实例上配置AEM DS服务设置的详细步骤，请参阅[配置AEM DS设置](/help/forms/using/configuring-the-processing-server-url-.md)。

对于AEM Forms参考站点，在AEM DS设置服务中，指定发布服务器的URL而不是处理服务器的URL。

>[!CAUTION]
>
>如果要为AEM FormsOSGi配置处理服务器URL，请不要将`/lc`放入该URL。

## 部署引用站点包{#refsite}

使用“软件分发”安装以下参考站点包。

* [AEM-FORMS-6.4-FSI-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

要进一步了解如何使用包，请参阅[如何使用包](/help/sites-administering/package-manager.md)。

安装包并启动创作和发布实例后，请在浏览器中访问以下URL:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

如果安装成功，您可以访问We.Gov和We.Finance参考站点登陆页。

## （可选）将示例数据导入Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

家庭抵押申请和汽车保险申请参考站点被配置为使用来自Microsoft Dynamics的记录。 引用站点包会安装自定义实体和示例记录，您可以将它们导入Microsoft Dynamics以运行引用站点。 请执行以下步骤来迁移和设置示例数据：

要导入汽车保险应用程序的自定义实体，请执行以下操作：

1. 从AEM作者实例的`https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip`下载&#x200B;**WeFinanceAutoInsurance_1_0.zip**&#x200B;解决方案包。
1. 在Microsoft Dynamics实例中，转到&#x200B;**[!UICONTROL 设置]**&#x200B;菜单中的&#x200B;**[!UICONTROL 解决方案]**，然后单击&#x200B;**[!UICONTROL 导入]**。 选择并导入包。

要导入汽车保险应用程序的自定义实体，请执行以下操作：

1. 从https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip下载&#x200B;**AEMFormsFSIRefsite_1_0.zip**&#x200B;包。 选择并导入包。

1. 在Microsoft Dynamics实例中，转到&#x200B;**[!UICONTROL 设置]**&#x200B;菜单中的&#x200B;**[!UICONTROL 解决方案]**，然后单击&#x200B;**[!UICONTROL 导入]**。 选择并导入包。

要导入客户和保险单记录，请执行以下操作：

1. 从AEM作者实例上的以下位置下载&#x200B;**We.Finance Customers.csv、We.Finance Auto Insurance Renewals.csv**&#x200B;和&#x200B;**家庭抵押**&#x200B;数据文件：

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. 在Microsoft Dynamics实例中，执行以下操作：

   * 转至&#x200B;**[!UICONTROL 销售> We.Finance客户]**&#x200B;并单击&#x200B;**[!UICONTROL 导入]**。
   * 转至&#x200B;**[!UICONTROL 销售> We.Finance Auto Insurance]**&#x200B;并单击&#x200B;**[!UICONTROL 导入]**。
   * 转至&#x200B;**[!UICONTROL 销售> We.Finance Home Mortgage]**&#x200B;并单击&#x200B;**[!UICONTROL 导入]**。

## 为Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}配置OAuth云服务

在AEM Forms配置OAuth云服务，实现AEM Forms与Microsoft Dynamics之间的通信。 执行以下步骤以在AEM作者和发布实例上配置OAuthCloud Service:

1. 在AEM作者实例上，转至&#x200B;**[!UICONTROL 工具>Cloud Services>数据源>全局]**。 点按&#x200B;**[!UICONTROL Refsite Dynamics Integration]**&#x200B;图标，然后点按&#x200B;**[!UICONTROL 属性]**。
1. 转到Microsoft Azure Active Directory帐户。 在注册应用程序的&#x200B;**[!UICONTROL 回复URL]**&#x200B;设置中添加复制的云服务配置URL。 保存配置。
1. 在“身份验证设置”选项卡中，为Microsoft Dynamics实例指定&#x200B;**[!UICONTROL 服务根]**、**[!UICONTROL 客户端Id]**、**[!UICONTROL 客户端机密]**&#x200B;和&#x200B;**[!UICONTROL 资源URL]**。 单击&#x200B;**[!UICONTROL 连接到重定向到Microsoft Dynamics登录页的OAuth]**。
1. 提供登录凭据。 登录后，您将被重定向到“AEM Forms云服务配置”页。 单击&#x200B;**[!UICONTROL 保存并关闭]**。云服务配置已保存。
1. 转至&#x200B;**[!UICONTROL Forms>数据集成> We.Finance]**。 选择自动保险（动态），然后单击编辑。 Microsoft Dynamics实体列在“数据源”选项卡下。 请等待，直到从Microsoft Dynamics获取所有实体并列在数据源选项卡下。
1. 选择&#x200B;**[!UICONTROL AutoInsuranceRenewal实体]**&#x200B;并单击&#x200B;**[!UICONTROL 测试模型对象]**。 在输入请求部分，将客户ID的值指定为“900001”，然后单击&#x200B;**[!UICONTROL 测试]**。 “输出”部分显示从Microsoft Dynamics为客户ID 900001获取的记录。
1. 在输入请求部分，将客户ID的值指定为“900001”，然后单击&#x200B;**[!UICONTROL 测试]**。 “输出”部分显示从Microsoft Dynamics为客户ID 900001获取的记录。
1. 对发布实例重复步骤1-6。

## 配置Adobe Sign调度程序{#scheduler}

对创作和发布实例执行以下操作：

1. 转到位于`https://[server]:[host]/system/console/configMgr`的AEM Web配置控制台。
1. 查找并点按&#x200B;**[!UICONTROL Adobe Sign配置服务]**&#x200B;以打开它进行配置。
1. 将&#x200B;**[!UICONTROL 状态更新调度程序表达式]**&#x200B;配置为&#x200B;**0 0/2 &amp;ast;&amp;ast;&amp;ast;?**。

   >[!NOTE]
   >
   >上述调度程序配置每两分钟检查一次Adobe Sign服务的状态。

1. 点按&#x200B;**[!UICONTROL 保存]**。

## 配置参考站点Adobe Sign云服务{#sign-service}

对创作和发布实例执行以下操作：

1. 转至&#x200B;**[!UICONTROL 工具>Cloud Services>Adobe Sign>全局]**。 选择&#x200B;**[!UICONTROL AEM Forms参考站点符号]**&#x200B;并点按&#x200B;**[!UICONTROL 属性]**。

   >[!CAUTION]
   >
   >确保将https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html URL添加到Adobe SignAPI应用程序OAuth配置的重定向URL列表。

1. 指定Adobe Sign应用程序OAuth配置的客户端ID和机密。
1. （可选）选择&#x200B;**[!UICONTROL 为附件启用Adobe Sign选项]**，然后点按&#x200B;**[!UICONTROL 连接到Adobe Sign]**。 它将附加到自适应表单的文件附加到发送以供签名的相应Adobe Sign文档。
1. 点按&#x200B;**[!UICONTROL 连接到Adobe Sign]**，然后使用您的Adobe Sign凭据登录。

## 配置Forms通用配置服务{#anonymous}

在发布实例上执行以下操作以允许匿名用户访问：

1. 转到位于`https://[server]:[port]/system/console/configMgr`的AEM Web配置控制台。
1. 查找并点按&#x200B;**[!UICONTROL Forms通用配置服务]**&#x200B;以打开它进行配置。
1. 为&#x200B;**[!UICONTROL 所有用户]**&#x200B;配置&#x200B;**[!UICONTROL 允许]**&#x200B;字段。
1. 点按&#x200B;**[!UICONTROL 保存]**。

## 修改表单数据模型{#fdm}的余料服务

对创作和发布实例执行以下操作：

1. 转到位于`https://[server]:[port]/crx/de/index.jsp`的CRXDE。
1. 导航到&#x200B;**/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile**&#x200B;并打开swagger文件。
1. 根据您的环境更新主机和端口设置。
1. 保存设置。
1. （**仅作者实例**）转至&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL 数据源]** **[!UICONTROL 全局]**。 选择&#x200B;**[!UICONTROL roi-rest]**&#x200B;并点按&#x200B;**[!UICONTROL 属性]**。 点按&#x200B;**[!UICONTROL 身份验证设置]**&#x200B;并将&#x200B;**[!UICONTROL 身份验证类型]**&#x200B;设置为&#x200B;**[!UICONTROL 基本身份验证]**。 指定`admin`/ `admin`作为用户名／口令访问服务。 点按&#x200B;**[!UICONTROL 保存并关闭]**。

## 与Marketing Cloud{#integrate-with-marketing-cloud}集成

你可以把AEM Forms和Adobe Analytics和Adobe Target融为一体。 Adobe Analytics帮助您生成报告并分析自适应表单的性能，而Adobe Target则帮助您提供个性化体验并执行自适应表单的A/B测试。

执行以下操作，在AEM Forms配置Adobe Analytics和Adobe Target。

### 配置Adobe Analytics{#configure-adobe-analytics}

AEM Forms与Adobe Analytics的集成使您能够监控和分析客户如何与您的表单和文档互动。 它有助于您识别和修复问题区域并采取行动增加转化率。

要在参考站点中体验此功能，请按照[配置分析和报告](/help/forms/using/configure-analytics-forms-documents.md)中的说明配置您的Analytics帐户。

要生成报告，种子数据会与引用站点绑定。 在使用种子数据之前，请执行以下操作：

1. 确保AEM云服务中提供We.Finance和We.Gov分析配置。 您可以通过以下方式之一查找云服务：

   * 导航到&#x200B;**[!UICONTROL 工具>Cloud Services>旧Cloud Services]**&#x200B;或浏览到https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html。
   * 在&#x200B;**[!UICONTROL Cloud Services]**&#x200B;页面的&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;部分下，单击`Show Configurations`。 您可以看到We.Finance和We.Gov配置。 单击以打开配置。 在配置页中，单击&#x200B;**[!UICONTROL 编辑]**。 提供有效公司、用户名、共享机密（密码）和数据中心，然后单击&#x200B;**[!UICONTROL 连接到Analytics]**。 连接成功对话框后，单击配置对话框上的&#x200B;**[!UICONTROL 确定]**。 按照[配置分析和报告](/help/forms/using/configure-analytics-forms-documents.md)中的说明，在分析配置下配置框架。

1. 导航到https://&lt;*host*>:*port*/system/console/configMgr并执行以下操作：

   * 在&#x200B;**[!UICONTROL Web控制台配置]**&#x200B;页面中，找到并单击&#x200B;**[!UICONTROL AEM Forms分析配置]**。
   * 在“AEM Forms分析配置”对话框的&#x200B;**[!UICONTROL SiteCatalyst框架]**&#x200B;字段中，选择we-finance(we-finance)或we-gov(we-gov)。
   * 单击&#x200B;**[!UICONTROL 保存]**&#x200B;并让页面刷新。

1. 导航到位于https://&lt;host>:&lt;port>/aem/forms的表单管理器，然后执行以下操作：

   * 打开We.Finance或We.Gov文件夹，选择要查看其报告的表单。
   * 单击操作工具栏中的启用分析。 为表单启用分析后，单击分析报告。 您可以看到生成的空白报告。 生成空白报告后，您必须提供refsite包附带的种子数据，以生成分析报告以用于演示。

   参考站点为分析报告提供信用卡、家庭抵押和儿童支持使用案例的种子数据。 有关种子数据的配置，请参阅[We.Finance参考站点演练](/help/forms/using/finance-reference-site-walkthrough.md)和[We.Gov参考站点演练](/help/forms/using/gov-reference-site-walkthrough.md)。

### 配置目标{#configure-target}

参考站点展示了AEM Forms与Adobe Target的集成，允许您在自适应文档中包含有针对性的个性化内容。 它还支持为自适应表单创建A/B测试。

要体验引用站点中的集成，请执行以下操作以在AEM中配置目标:

1. 使用jvm参数`-Dabtesting.enabled=true`开始作者快速启动，以在服务器上启用A/B测试。

   **注意**:如果AEM实例在JBoss上运行，该实例从Turnkey安装作为服务启动，请在文 `-Dabtesting.enabled=true` 件的以下条目中添加 `jboss\bin\standalone.conf.bat` 参数：

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. 访问https://&lt;*hostname*:*port*/libs/cq/core/content/tools/cloudservices.html。

1. 在&#x200B;**[!UICONTROL Adobe Target]**&#x200B;部分，单击&#x200B;**[!UICONTROL 显示配置]**。 您可以看到可用的We.Finance目标配置。 单击以打开配置。 在配置页中，单击&#x200B;**[!UICONTROL 编辑]**。 此时将打开配置的&#x200B;**[!UICONTROL 编辑组件]**&#x200B;对话框。

1. 指定与您的目标帐户关联的客户代码、电子邮件和密码。 选择API类型作为&#x200B;**[!UICONTROL REST]**。
1. 单击&#x200B;**[!UICONTROL 连接到Adobe目标]**。 成功配置目标帐户后，单击&#x200B;**[!UICONTROL 确定]**。 您可以看到打包配置有一个目标框架。

1. 转至https://&lt;*hostname*:*port*/system/console/configMgr。

1. 单击&#x200B;**[!UICONTROL AEM Forms目标配置]**。
1. 选择目标框架。
1. 在&#x200B;**[!UICONTROL 目标URL]**&#x200B;字段中，指定到AEM Forms的URL。 例如：https://&lt;*hostname*:*port*>。

1. 单击&#x200B;**[!UICONTROL 保存]**。

信用卡应用程序和家庭抵押应用程序使用案例演示了如何执行A/B测试并展示报告以用于演示目的。 有关演练，请参阅[We.Finance参考站点演练](/help/forms/using/finance-reference-site-walkthrough.md)。

## 下一步{#next-step}

现在，您已准备好浏览参考站点。 有关参考站点工作流程和步骤的详细信息，请参阅：

* [We.Finance参考站点演练](/help/forms/using/finance-reference-site-walkthrough.md)
* [We.Gov参考站点演练](/help/forms/using/gov-reference-site-walkthrough.md)

* [员工自助参考站点演练](/help/forms/using/employee-self-service-reference-site.md)

