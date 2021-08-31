---
title: 设置和配置AEM Forms引用站点
seo-title: Set up and configure AEM Forms reference sites
description: AEM Forms参考网站展示了如何使用AEM Forms在组织中实施端到端工作流。
seo-description: AEM Forms reference sites showcase how you can use AEM Forms to implement end-to-end workflow in an organization.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '2911'
ht-degree: 2%

---

# 设置和配置AEM Forms引用站点 {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms提供参考站点实施，以演示AEM Forms如何帮助金融服务行业和政府组织在任何设备上随时随地将其复杂交易转换为简单而引人入胜的数字体验。

We.Finance和We.Gov参考网站利用真实的用例与现有和潜在客户进行互动，从首次接触开始，以个性化且经济高效的方式管理信函和交易。

利用参考网站，可探索和展示AEM Forms的以下主要功能。

* 简化了引人入胜的响应式自适应表单和交互式通信的创作体验。
* 交互式通信，创建可适应设备设置和布局的交互式、个性化和响应式客户通信。
* 数据集成以连接到不同的数据源，通过表单数据模型预填和提交表单数据。
* Forms工作流，可自动执行业务流程和工作流。
* 高级用户数据管理和处理功能。
* 与Adobe Sign集成，以安全地签署和提交自适应表单。
* 与Adobe Target集成，以提供有针对性的推荐并执行A/B测试，从而最大限度地提高表单投资回报率。
* 与Adobe Analytics集成，以衡量表单或营销活动的效果并做出明智的决策。
* 增强表单填写体验。

参考站点提供了可重复使用的资产，您可以将这些资产用作模板来创建自己的资产。

* 与Adobe Sign集成，以安全地签署和提交自适应表单。

* 与Adobe Sign集成，以安全地签署和提交自适应表单。

## 设置引用站点的先决条件和步骤 {#prerequisites-and-steps-to-set-up-reference-sites}

在设置引用站点之前，请确保您具有以下内容：

* **AEM essentials**

   AEM快速入门、AEM Forms附加组件包和引用站点包。 有关附加组件和引用站点包的详细信息，请参阅[AEM Forms版本](https://helpx.adobe.com/cn/aem-forms/kb/aem-forms-releases.html)。

* **SMTP服务**
您可以使用任何SMTP服务。

* **Adobe Sign开发人员帐户和Adobe Sign API应用程序**

   要使用数字签名功能，需要Adobe Sign开发人员帐户。 请参阅[Adobe Sign](https://acrobat.adobe.com/us/en/why-adobe/developer-form.html)。

* 要与AEM Forms集成的Microsoft Dynamics 365运行实例。 要运行引用站点，请将示例数据导入Microsoft Dynamics实例，以预填充引用站点中使用的交互式通信。
* 包含Forms附加组件包的AEM 6.4运行实例。 有关更多信息，请参阅[安装和配置AEM Forms](installing-configuring-aem-forms-osgi.md)。

按照建议的顺序执行以下步骤以设置和配置引用站点。

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
   <td>安装和配置AEM Forms创作和发布实例。</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">配置SSL</a></td> 
   <td>创作和发布<br /> </td> 
   <td>启用HTTP over SSL以与Adobe Sign进行安全通信。</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">配置Day CQ Link Externalizer配置</a></p> </td> 
   <td>创作和发布<br /> </td> 
   <td><p>参考网站用例为不同交易发送电子邮件。 通过电子邮件发送新闻稿时需要此设置。 它可确保URL和图像指向发布实例。 </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">配置Day CQ Mail Service</a></td> 
   <td>创作和发布</td> 
   <td>电子邮件通信需要。</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">覆盖默认的XSS配置</a></td> 
   <td>发布</td> 
   <td>用于覆盖xss安全性阻止的$、{和}字符。</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">配置AEM DS设置</a></td> 
   <td>作者</td> 
   <td>配置AEM DS以在发布实例上提交表单，并在创作实例上处理工作流。</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">部署引用站点包</a></td> 
   <td>作者</td> 
   <td>在AEM Forms创作实例上部署引用站点包。</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">将示例数据导入Microsoft Dynamics</a></td> 
   <td>创作和发布</td> 
   <td>为信用卡申请、住房抵押申请和住房保险申请过程导入样本数据</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">为Microsoft Dynamics配置OAuth云服务</a></td> 
   <td>创作和发布</td> 
   <td>在AEM Forms中配置OAuth云服务，以启用AEM Forms与Microsoft Dynamics之间的通信。 </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">配置Adobe Sign调度程序</a></td> 
   <td>创作和发布<br /> </td> 
   <td>更改调度程序的配置，每两分钟检查一次状态。</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">配置参考站点Adobe SignCloud Service</a></td> 
   <td>创作和发布<br /> </td> 
   <td>引用站点附带的配置包，需要使用有效凭据重新配置。</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">为匿名用户配置Forms通用配置服务</a></td> 
   <td>发布</td> 
   <td>该配置允许为匿名用户提交、签署和生成记录文档。</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">修改表单数据模型的Rest服务Swagger文件</a></td> 
   <td>创作和发布<br /> </td> 
   <td>修改环境的服务。</td> 
  </tr> 
 </tbody> 
</table>

## 安装和配置AEM Forms {#install-and-configure-aem-forms}

按照[在OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md)上安装和配置AEM Forms中所述，安装和部署AEM Forms。

>[!NOTE]
>
>如果多个发布实例或创作和发布实例位于不同的计算机上，则配置复制和反向复制代理。

## 配置SSL {#ssl}

需要SSL配置才能与Adobe Sign服务器通信。 有关详细步骤，请参阅[启用HTTP Over SSL](/help/sites-administering/ssl-by-default.md)。

>[!CAUTION]
>
>请勿在`/etc/map`文件夹上配置强制SSL。

## 配置Day CQ Link Externalizer配置 {#externalizer}

在AEM中， **Externalizer**&#x200B;是一项OSGI服务，它允许您通过预配置的DNS来预定路径，以编程方式将资源路径（例如/path/to/my/page）转换为外部和绝对URL(例如https://www.mycompany.com/path/to/my/page)。 请参阅[外部化URL](/help/sites-developing/externalizer.md)。

>[!CAUTION]
>
>如果您对SSL使用自签名证书，请勿将其外部化为HTTPS URL。
>
>此外，对于本地服务器，请使用localhost而不是其主机名。

对创作实例和发布实例执行以下步骤：

1. 转到位于https://的OSGi配置：*hostname>*:*port>*/system/console/configMgr。
1. 查找并点按&#x200B;**[!UICONTROL Day CQ Link Externalizer]**&#x200B;配置。

   将打开Day CQ Link Externalizer对话框，用于编辑配置。

1. 在Day CQ Link Externalizer（日CQ链接外部器）对话框的Domains（域）字段中：

   * 在创作实例上，指定可从外部系统访问的发布URL。 例如，主机名或发布Web服务器。
   * 在发布实例上，指定创作URL和发布URL。

1. 在创作实例和发布实例上，确保在“域”字段中指定本地服务器URL。
1. 点按&#x200B;**[!UICONTROL 保存]**。等待一段时间，以便所有服务都重新启动。

## 配置Day CQ Mail Service {#cqmail}

引用网站实施要求在填写和提交表单时向示例用户发送电子邮件。 配置Day CQ Mail Service允许您提供SMTP服务详细信息，以向客户发送自动电子邮件。 请参阅[配置电子邮件通知](/help/sites-administering/notification.md)。

执行以下步骤以在发布实例上配置邮件服务：

1. 转到位于https://的OSGi配置：*hostname>*:*port>*/system/console/configMgr。
1. 查找并点按&#x200B;**[!UICONTROL Day CQ Mail Service]**&#x200B;以将其打开进行配置。
1. 提供SMTP服务器主机名和端口值。
1. 点按&#x200B;**[!UICONTROL 保存]**。

>[!NOTE]
>
>您可以使用企业SMTP服务或Gmail等公共服务。 有关配置SMTP服务的信息，请参阅SMTP服务文档。

## 覆盖默认的XSS配置 {#xss}

We.Finance参考网站的电子邮件模板在电子邮件中包含个性化链接。 这些链接的占位符为`${placeholder}`。 在发送电子邮件之前，这些占位符会被替换为实际值。 AEM的默认XSS保护配置不允许在HTML内容的URL中使用大括号(**{ }**)。 但是，您可以对发布实例执行以下步骤来覆盖默认配置：

1. 将`/libs/cq/xssprotection/config.xml`复制到`/apps/cq/xssprotection/config.xml`。
1. 打开 `/apps/cq/xssprotection/config.xml`.
1. 在`common-regexps`部分中，按如下方式修改`onsiteURL`条目并保存文件。

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>大括号(**{ }**)在HTML内容的URL中包含为可接受的字符。

配置SMTP服务器后，尝试使用Sarah Rose角色填写表单，并将其另存为草稿。 另存为草稿时，您可以选择通过电子邮件接收草稿。 点按&#x200B;**发送电子邮件**&#x200B;按钮时，如果您收到一封包含应用程序草稿链接的电子邮件，则您的电子邮件配置会成功。 确保您使用Sarah的凭据登录以查看草稿。

## 配置AEM DS设置 {#aemds}

AEM DS服务设置是引用站点用例中用于电子邮件通信的发布实例中的必需设置。 有关在Publish实例上配置AEM DS服务设置的详细步骤，请参阅[配置AEM DS设置](/help/forms/using/configuring-the-processing-server-url-.md)。

对于AEM Forms引用站点，在AEM DS设置服务中，指定发布服务器的URL，而不是处理服务器的URL。

>[!CAUTION]
>
>如果要为AEM Forms OSGi配置处理服务器URL，请勿将`/lc`置于该URL中。

## 部署引用站点包 {#refsite}

使用Software Distribution安装以下引用站点包。

* [AEM-FORMS.-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS.-6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

要了解有关如何使用包的更多信息，请参阅[如何使用包](/help/sites-administering/package-manager.md)。

安装包并启动创作和发布实例后，请在浏览器中访问以下URL:

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

如果安装成功，您可以访问We.Gov和We.Finance引用网站登陆页面。

## （可选）将示例数据导入Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

住房抵押申请和汽车保险申请参考站点被配置为使用来自Microsoft Dynamics的记录。 引用站点包会安装自定义实体和示例记录，您可以将其导入Microsoft Dynamics以运行引用站点。 执行以下步骤以迁移和设置示例数据：

要导入汽车保险申请的自定义实体，请执行以下操作：

1. 从AEM创作实例的`https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip`下载&#x200B;**WeFinanceAutoInsurance_1_0.zip**&#x200B;解决方案包。
1. 在Microsoft Dynamics实例中，转到&#x200B;**[!UICONTROL Settings]**&#x200B;菜单中的&#x200B;**[!UICONTROL Solutions]**，然后单击&#x200B;**[!UICONTROL Import]**。 选择并导入资源包。

要导入汽车保险申请的自定义实体，请执行以下操作：

1. 从https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip下载&#x200B;**AEMFormsFSIRefsite_1_0.zip**&#x200B;包。 选择并导入资源包。

1. 在Microsoft Dynamics实例中，转到&#x200B;**[!UICONTROL Settings]**&#x200B;菜单中的&#x200B;**[!UICONTROL Solutions]**，然后单击&#x200B;**[!UICONTROL Import]**。 选择并导入资源包。

要导入客户和保险单记录，请执行以下操作：

1. 在您的AEM创作实例上，从以下位置下载&#x200B;**We.Finance Customers.csv、We.Finance Auto Insurance Renuvars.csv**&#x200B;和&#x200B;**home mortgage**&#x200B;数据文件：

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. 在Microsoft Dynamics实例中，执行以下操作：

   * 转到&#x200B;**[!UICONTROL Sales > We.Finance Customers]**&#x200B;并单击&#x200B;**[!UICONTROL Import]**。
   * 转到&#x200B;**[!UICONTROL Sales > We.Finance Auto Insurance]**，然后单击&#x200B;**[!UICONTROL Import]**。
   * 转到&#x200B;**[!UICONTROL Sales > We.Finance Home Mortgage]**&#x200B;并单击&#x200B;**[!UICONTROL Import]**。

## 为Microsoft Dynamics配置OAuth云服务 {#configure-oauth-cloud-service-for-microsoft-dynamics}

在AEM Forms中配置OAuth云服务，以启用AEM Forms与Microsoft Dynamics之间的通信。 执行以下步骤以在AEM创作和发布实例上配置OAuthCloud Service:

1. 在AEM创作实例中，转到&#x200B;**[!UICONTROL 工具>Cloud Services>数据源>全局]**。 点按&#x200B;**[!UICONTROL 刷新Dynamics集成]**&#x200B;图标，然后点按&#x200B;**[!UICONTROL 属性]**。
1. 转到Microsoft Azure Active Directory帐户。 将复制的云服务配置URL添加到注册应用程序的&#x200B;**[!UICONTROL 回复URL]**&#x200B;设置中。 保存配置。
1. 在“身份验证设置”选项卡中，为Microsoft Dynamics实例指定&#x200B;**[!UICONTROL 服务根]**、**[!UICONTROL 客户端Id]**、**[!UICONTROL 客户端密钥]**&#x200B;和&#x200B;**[!UICONTROL 资源URL]**。 单击重定向到Microsoft Dynamics登录页面的&#x200B;**[!UICONTROL 连接到OAuth]**。
1. 提供您的登录凭据。 登录后，您将被重定向到AEM Forms云服务配置页面。 单击&#x200B;**[!UICONTROL 保存并关闭]**。云服务配置已保存。
1. 转到&#x200B;**[!UICONTROL Forms >数据集成> We.Finance]**。 选择“自动保险（动态）”，然后单击“编辑”。 Microsoft Dynamics实体列在数据源选项卡下。 等待直到从Microsoft Dynamics获取所有实体并列在数据源选项卡下。
1. 选择&#x200B;**[!UICONTROL AutoInsuranceRenewal实体]**&#x200B;并单击&#x200B;**[!UICONTROL 测试模型对象]**。 在输入请求部分中，将客户ID的值指定为“900001”，然后单击&#x200B;**[!UICONTROL Test]**。 “输出”部分显示从Microsoft Dynamics获取的客户ID 900001的记录。
1. 在输入请求部分中，将客户ID的值指定为“900001”，然后单击&#x200B;**[!UICONTROL Test]**。 “输出”部分显示从Microsoft Dynamics获取的客户ID 900001的记录。
1. 对发布实例重复步骤1-6。

## 配置Adobe Sign调度程序 {#scheduler}

在创作实例和发布实例上执行以下操作：

1. 转到位于`https://[server]:[host]/system/console/configMgr`的AEM Web配置控制台。
1. 找到并点按&#x200B;**[!UICONTROL Adobe Sign配置服务]**&#x200B;以将其打开进行配置。
1. 将&#x200B;**[!UICONTROL 状态更新调度程序表达式]**&#x200B;配置为&#x200B;**0 0/2 &amp;ast;&amp;ast;&amp;ast;?**。

   >[!NOTE]
   >
   >上述调度程序配置每两分钟检查一次Adobe Sign服务的状态。

1. 点按&#x200B;**[!UICONTROL 保存]**。

## 配置参考站点Adobe Sign云服务 {#sign-service}

在创作实例和发布实例上执行以下操作：

1. 转到&#x200B;**[!UICONTROL 工具>Cloud Services> Adobe Sign >全局]**。 选择&#x200B;**[!UICONTROL AEM Forms引用站点符号]**&#x200B;并点按&#x200B;**[!UICONTROL 属性]**。

   >[!CAUTION]
   >
   >确保将https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html URL添加到Adobe Sign API应用程序OAuth配置的重定向URL列表中。

1. 指定Adobe Sign应用程序OAuth配置的客户端ID和密钥。
1. （可选）选择&#x200B;**[!UICONTROL 为附件启用Adobe Sign也]**&#x200B;选项，然后点按&#x200B;**[!UICONTROL 连接到Adobe Sign]**。 它会将附加到自适应表单的文件附加到发送进行签名的相应Adobe Sign文档。
1. 点按&#x200B;**[!UICONTROL 连接到Adobe Sign]** ，然后使用您的Adobe Sign凭据登录。

## 配置Forms Common Configuration Service {#anonymous}

在发布实例上执行以下操作，以允许匿名用户访问：

1. 转到位于`https://[server]:[port]/system/console/configMgr`的AEM Web配置控制台。
1. 找到并点按&#x200B;**[!UICONTROL Forms Common Configuration Service]**&#x200B;以将其打开进行配置。
1. 为&#x200B;**[!UICONTROL 所有用户]**&#x200B;配置&#x200B;**[!UICONTROL Allow]**&#x200B;字段。
1. 点按&#x200B;**[!UICONTROL 保存]**。

## 修改表单数据模型的Rest服务 {#fdm}

在创作实例和发布实例上执行以下操作：

1. 转到位于`https://[server]:[port]/crx/de/index.jsp`的CRXDE。
1. 导航到&#x200B;**/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile**&#x200B;并打开swagger文件。
1. 根据您的环境更新主机和端口设置。
1. 保存设置。
1. （**仅创作实例**）转到&#x200B;**[!UICONTROL 工具]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL 数据源]** > **[!UICONTROL 全局]**。 选择&#x200B;**[!UICONTROL roi-rest]**&#x200B;并点按&#x200B;**[!UICONTROL 属性]**。 点按&#x200B;**[!UICONTROL 身份验证设置]**，并将&#x200B;**[!UICONTROL 身份验证类型]**&#x200B;设置为&#x200B;**[!UICONTROL 基本身份验证]**。 指定`admin`/ `admin`作为访问服务的用户名/密码。 点按&#x200B;**[!UICONTROL 保存并关闭]**。

## 与Marketing Cloud集成 {#integrate-with-marketing-cloud}

您可以将AEM Forms与Adobe Analytics和Adobe Target集成。 虽然Adobe Analytics可以帮助您生成报表并分析自适应表单的性能，但Adobe Target可以帮助您提供个性化体验并执行自适应表单的A/B测试。

执行以下操作以在AEM Forms中配置Adobe Analytics和Adobe Target。

### 配置Adobe Analytics {#configure-adobe-analytics}

AEM Forms与Adobe Analytics集成允许您监控和分析客户与表单和文档的交互方式。 它有助于您识别和修复问题区域，并采取措施提高转化率。

要在参考站点中体验此功能，请按照[配置分析和报表](/help/forms/using/configure-analytics-forms-documents.md)中所述配置您的Analytics帐户。

要生成报表，种子数据会与引用站点捆绑在一起。 在使用种子数据之前，请执行以下操作：

1. 确保AEM云服务中提供We.Finance和We.Gov分析配置。 您可以通过以下方式之一找到云服务：

   * 导航到&#x200B;**[!UICONTROL 工具>Cloud Services>旧版Cloud Services]**&#x200B;或浏览到https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html。
   * 在&#x200B;**[!UICONTROL Cloud Services]**&#x200B;页面的&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;部分下，单击`Show Configurations`。 您可以看到We.Finance和We.Gov的可用配置。 单击以打开配置。 在配置页中，单击&#x200B;**[!UICONTROL 编辑]**。 提供有效的公司、用户名、共享密钥（密码）和数据中心，然后单击&#x200B;**[!UICONTROL 连接到Analytics]**。 连接成功对话框后，在配置对话框中单击&#x200B;**[!UICONTROL 确定]**。 在Analytics配置下配置框架，如[配置Analytics和报表](/help/forms/using/configure-analytics-forms-documents.md)中所述。

1. 导航到https://*host*>:*port*>/system/console/configMgr并执行以下操作：

   * 在&#x200B;**[!UICONTROL Web控制台配置]**&#x200B;页面中，找到并单击&#x200B;**[!UICONTROL AEM Forms Analytics配置]**。
   * 在AEM Forms Analytics配置对话框的&#x200B;**[!UICONTROL SiteCatalyst框架]**&#x200B;字段中，选择we-finance(we-finance)或we-gov(we-gov)。
   * 单击&#x200B;**[!UICONTROL Save]**&#x200B;并让页面刷新。

1. 导航到https://&lt;host>:&lt;port>/aem/forms中的表单管理器，然后执行以下操作：

   * 打开We.Finance或We.Gov文件夹，然后选择要查看其报表的表单。
   * 在“操作”工具栏中单击启用Analytics 。 为表单启用分析后，单击“分析报表”。 您可以看到生成的空白报表。 生成空白报表后，您必须提供推荐包随附的种子数据，才能生成用于演示目的的分析报表。

   参考网站提供分析报告，其中包含信用卡、住房抵押和儿童支持用例的种子数据。 有关种子数据的配置，请参阅[We.Finance引用站点演练](/help/forms/using/finance-reference-site-walkthrough.md)和[We.Gov引用站点演练](/help/forms/using/gov-reference-site-walkthrough.md)。

### 配置Target {#configure-target}

参考网站展示了AEM Forms与Adobe Target的集成，允许您在自适应文档中包含有针对性的个性化内容。 它还支持为自适应表单创建A/B测试。

要在参考站点中体验集成，请执行以下操作以在AEM中配置Target:

1. 使用jvm参数`-Dabtesting.enabled=true`启动创作快速启动，以在服务器上启用A/B测试。

   **注意**:如果AEM实例在JBoss（从Turnkey安装以服务形式启动）上运行，请在文件的 `-Dabtesting.enabled=true` 以下条目中添加 `jboss\bin\standalone.conf.bat` 参数：

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. 访问https://&lt;*hostname*>:*port*>/libs/cq/core/content/tools/cloudservices.html。

1. 在&#x200B;**[!UICONTROL Adobe Target]**&#x200B;部分中，单击&#x200B;**[!UICONTROL 显示配置]**。 您可以看到We.Finance Target配置的可用。 单击以打开配置。 在配置页中，单击&#x200B;**[!UICONTROL 编辑]**。 此时将打开配置的&#x200B;**[!UICONTROL 编辑组件]**&#x200B;对话框。

1. 指定与Target帐户关联的客户端代码、电子邮件和密码。 选择API类型作为&#x200B;**[!UICONTROL REST]**。
1. 单击&#x200B;**[!UICONTROL 连接到Adobe目标]**。 成功配置Target帐户后，单击&#x200B;**[!UICONTROL 确定]**。 您可以看到打包的配置具有Target框架。

1. 转到https://*hostname*>:*port*>/system/console/configMgr。

1. 单击&#x200B;**[!UICONTROL AEM Forms Target配置]**。
1. 选择Target框架。
1. 在&#x200B;**[!UICONTROL 目标URL]**&#x200B;字段中，指定到AEM Forms的URL。 例如：https://&lt;*hostname*>:*port*>。

1. 单击&#x200B;**[!UICONTROL 保存]**。

信用卡应用程序和住房抵押贷款应用程序用例演示了如何执行A/B测试并展示用于演示目的的报告。 有关演练，请参阅[We.Finance引用站点演练](/help/forms/using/finance-reference-site-walkthrough.md)。

## 下一步 {#next-step}

现在，您都可以浏览参考站点。 有关参考站点工作流和步骤的更多信息，请参阅：

* [We.Finance参考站点演练](/help/forms/using/finance-reference-site-walkthrough.md)
* [We.Gov引用站点演练](/help/forms/using/gov-reference-site-walkthrough.md)

* [员工自助参考站点演练](/help/forms/using/employee-self-service-reference-site.md)
