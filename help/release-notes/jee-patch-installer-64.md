---
title: AEM FormsJEE修补程序安装程序
description: 'null'
uuid: e709871b-c04c-43bb-a7d0-45e89fbd3d44
content-type: reference
discoiquuid: 83bace08-1d4f-4192-a634-c7c4879963d8
translation-type: tm+mt
source-git-commit: 610e9a54adad3abdfecb8b2c4da67d677f75175e
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 1%

---


# AEM FormsJEE修补程序安装程序 {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[有关详细信息](https://www.adobe.com/account/sign-in.supportportal.html) ，请与支持部门联系或获取修补程序。

## 关于修补程序安装程序 {#about-the-patch-installer}

AEM 6.4FormsJEE修补程序安装程序包含AEM 6.4FormsJEE所有组件在发布此修补程序之前可用的所有已修复问题。 有关完整的 [修复问题列表](cfp-release-notes.md) ，请参阅最新的累积修复包发行说明。

## 安装修补程序的先决条件 {#prerequisites-to-installing-the-patch}

* AEM 6.4Forms

## 安装和配置修补程序 {#installing-and-configuring-the-patch}

1. 备份&lt;AEM_*forms_root*>/deploy文件夹。 如果您决定卸载快速修复，则此操作是必需的。
1. 停止应用程序服务器。
1. 将修补程序安装程序存档文件解压到硬盘。
1. 在根据您所使用的操作系统命名的目录中：

   * **Windows**&#x200B;导航到硬盘上安装介质或文件夹中的相应目录，并在其中复制了安装程序，然后多次单击 
`aemforms64_cfp_install.exe` 文件。

      * （Windows 32位） `Windows\Disk1\InstData\VM`
      * （Windows 64位） `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux、Solaris、AIX**&#x200B;导航到相应的目录，并从命令提示符中键入 
`./aem64_cfp_install.bin`。

      * (Linux) `Linux/Disk1/InstData/NoVM`
      * (Solaris) `Solaris/Disk1/InstData/NoVM`
      * (AIX)

         ```
         AIX/Disk1/InstData/VM
         ```
   这将启动一个安装向导，指导您完成安装。

1. 在“简介”面板上，单击“ **[!UICONTROL 下一步]**”。
1. 在“选择安装文件夹”屏幕上，验证显示的默认位置是否适用于您的现有安装，或单击“浏 **[!UICONTROL 览]** ”选择安装AEM表单的备用文件夹，然后单击“下 **[!UICONTROL 一步”]**。

1. 阅读“快速修复修补程序摘要”信息，然后单击“ **[!UICONTROL 下一步]**”。
1. 阅读“预安装摘要”信息，然后单击“ **[!UICONTROL 安装]**”。
1. 安装完成后，单击“**下[!UICONTROL 一步]*”，将快速修复更新应用到已安装的文件。
1. [仅Windows] 执行以下步骤之一：

   * 单击“完成”之前，请取消选择“开始配置管理器”选项。 稍后使用中的文件运 `ConfigurationManager.bat` 行Configuration Manager `[aem-forms root]\configurationManager\bin`。 使用 `ConfigurationManager.bat` 可帮助您避免手动更新。lax文件中axis.jar名称的名称
   * 单击“完成”之前，请取消选择“开始配置管理器”选项。 在使用ConfigurationManager.exe或 **ConfigurationManager** _IPv.exe运行ConfigurationManager之前 **，请导航至************ &lt;AORMS_Install_>目录并将Axis.jar更新至\configurationManager\bin轴-1.4.1.1.1，在以下文件中：

      * ConfigurationManager.lax
      * ConfigurationManager_IPv6.lax

1. （仅基于Unix）默认情况下，开始配置管理器复选框处于选中状态。 单击 **[!UICONTROL 完成]** ，以运行Configuration Manager。

   要稍后运行Configuration Manager，请在单击“完成”之前取消选择“开始配置管理器”选项。 您以后可以使用目录中的相应脚本开始Configuration `[AEM_forms_root]/configurationManager/bin` Manager。

1. 根据您的应用程序服务器，选择以下文档之一，然后按照配置和部署AEM表 *单部分中的说明* 。

   * [为JBoss安装和部署AEM表单](http://www.adobe.com/go/learn_aemforms_installJBoss_64)
   * [安装和配置AEM forms for WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_64)
   * [安装和配置AEM forms for WebLogic](http://www.adobe.com/go/learn_aemforms_installWebLogic_64)

1. （仅限JBoss）安装修补程序并配置服务器后，删除JBoss应用程序服务器的tmp和工作目录。

## 部署后配置 {#post-deployment-configurations}

### SAML配置 {#saml-configurations}

如果您已配置SAML身份验证，并且遇到大型IDP元数据的问题，请在安装修补程序后执行以下操作：

1. 在应用程序服务器中设置以下系统属性：\
   `um.saml.enable.large.xml=true`

1. 重新启动服务器。
1. 如SAML设置中所述，删除现有SAML身份验证提供者，然后再次为现有域添加它们。

## 受影响的模块 {#impacted-modules}

* 文档服务
* 文档安全
* Foundation JEE
* PDFG 服务

[联系支持](https://www.adobe.com/account/sign-in.supportportal.html)
