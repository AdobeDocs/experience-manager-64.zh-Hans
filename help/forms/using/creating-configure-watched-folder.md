---
title: 创建或配置监视文件夹
seo-title: Create or Configure a watched folder
description: 了解如何创建或删除已监视文件夹，或修改现有已监视文件夹的属性。
seo-description: Learn how to create or delete a watched folder, or modify the properties of an existing watched folder.
uuid: 659d4d8c-99b8-40dd-b884-bfee4d476fe1
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: 0ce7b338-6686-49b3-b58b-e7ab6b670708
exl-id: 7e2706e2-092f-4780-be8f-2bf444613d70
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1860'
ht-degree: 0%

---

# 创建或配置监视文件夹 {#create-or-configure-a-watched-folder}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

管理员可以配置网络文件夹(称为 *监视文件夹*，以便当用户将文件(如PDF文件)放置到监视的文件夹时，会启动预配置的操作并处理该文件。 执行指定操作后，操作会将修改后的文件保存在指定的输出文件夹中。 有关管理已监视文件夹的详细信息，请参阅 [管理帮助](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md).

您可以使用监视文件夹用户界面执行以下操作：

* 创建监视文件夹
* 修改现有监视文件夹的属性
* 删除监视的文件夹

## 创建监视文件夹 {#create-a-watched-folder}

在配置监视文件夹之前，请确保：

* 监视文件夹是AEM表单的一项高级功能。 它需要AEM Forms附加组件包才能正常工作。 确保安装和配置了相应的AEM Forms附加组件包。
* 您可以在共享或本地存储中创建已监视的文件夹。 确保配置为运行已监视文件夹的AEM Forms用户对已监视文件夹具有读写权限。
* 您可以使用服务、工作流或脚本自动执行监视文件夹的操作。 确保创建了相应的服务、工作流或脚本，并准备运行。 有关创建服务、工作流和脚本的信息，请参阅 [各种文件处理方法](/help/forms/using/watched-folder-in-aem-forms.md#various-methods-for-processing-files).
* 已监视文件夹具有各种属性，请参阅 [监视的文件夹属性](/help/forms/using/watched-folder-in-aem-forms.md#watchedfolderproperties).

执行以下步骤以创建监视文件夹：

1. 点按 **Adobe Experience Manager** 图标。
1. 点按 **工具** > **Forms** > **配置监视文件夹。** 将显示已配置的监视文件夹列表。
1. 点按 **新建**. 此时将显示创建监视文件夹所需的字段列表：

   * **名称**:标识监视的文件夹。 名称只能使用字母数字字符。
   * **路径**:指定监视的文件夹位置。 在群集环境中，此设置必须指向一个共享网络文件夹，该文件夹可供在群集的不同节点上运行AEM的每个用户访问。
   * **处理文件使用**:要启动的进程的类型。 您可以指定工作流、脚本或服务。
   * **服务名称/脚本路径/工作流路径**:字段的行为基于为 **处理文件使用** 字段。 您可以指定以下值：

      * 对于工作流，指定要执行的工作流模型。 例如， /etc/workflow/models/&lt;workflow_name>/jcr:content/model
      * 对于脚本，指定要执行的脚本的JCR路径。 例如， /etc/watchfolder/test/testScript.ecma
      * 对于服务，指定用于查找OSGi服务的过滤器。 该服务将注册为com.adobe.aemfd.watchfolder.service.api.ContentProcessor Interface的实现。 例如，以下代码是ContentProcessor界面的自定义实现，该界面具有自定义(foo=bar)属性。

   >[!NOTE]
   >
   >如果已选择 **服务** 对于 **处理文件使用** 字段中，“服务名称(inputProcessorType)”字段的值必须括在括号中。 例如，(foo=bar)。

   ```java
   @Component(metatype = true, immediate = true, label = "WF Test Service", description = "WF Test Service")
   @Service(value = {OutputWriter.class, ContentProcessor.class})
   @Property(name = "foo", value = "bar")
   public class OutputWriter implements ContentProcessor {
   ```

   * **输出文件模式**:指定分号(;)分隔的模式列表，已监视文件夹使用该列表来确定输出文件和文件夹的名称和位置。 有关文件模式的更多信息，请参阅 [关于文件模式](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).


1. 点按 **高级**. 高级选项卡包含更多字段。 这些字段中的大多数都包含默认值。

   * **负载映射器过滤器：** 创建监视文件夹时，它会在监视的文件夹中创建文件夹结构。 文件夹结构具有暂存、结果、保留、输入和失败文件夹。 文件夹结构可用作工作流的输入有效负荷，并接受来自工作流的输出。 它还可以列出故障点（如果有）。 有效负载的结构与监视文件夹的结构不同。 您可以编写自定义脚本，将已监视文件夹的结构映射到有效负载。 这种脚本称为负载映射器过滤器。 提供了两个现成的有效负载映射器实施。 如果您没有 [自定义实施](/help/forms/using/watched-folder-in-aem-forms.md#creating-a-custom-payload-mapper-filter)，使用一个现成的实施：

      * **默认映射器：** 使用默认有效负载映射器将已监视文件夹的输入和输出内容保留在有效负载中单独的输入和输出文件夹中。
      * **简单的基于文件的有效负载映射器：** 使用基于简单文件的有效负载映射器将输入和输出内容直接保留在有效负载文件夹中。 它不会创建任何额外的层次结构，如默认映射器。
   * **运行模式**:指定用于工作流执行的允许运行模式的逗号分隔列表。
   * **在以下情况下超时暂存文件**:指定在输入文件/文件夹（已被拾取以进行处理）被视为已超时并标记为失败之前等待的秒数。 仅当此属性的值为正数时，才会激活超时机制。
   * **在限制时删除超时暂存文件**:如果启用，则 **在以下情况下超时暂存文件** 仅当为监视文件夹打开限制时，才会激活机制。
   * **每次扫描后扫描输入文件夹：** 指定扫描监视文件夹以获取输入的时间间隔（以秒为单位）。 除非启用“限制”设置，否则轮询间隔应大于处理平均作业的时间；否则，系统可能会过载。 间隔的值必须大于或等于1。
   * **排除文件模式**:指定分号(;)分隔的模式列表，已监视文件夹使用该列表来确定要扫描和选取的文件和文件夹。 不会扫描任何具有指定模式的文件或文件夹以进行处理。 有关文件模式的更多信息，请参阅 [关于文件模式](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **包含文件模式**:指定分号(;)分隔的模式列表，已监视文件夹使用这些模式确定要扫描和选取的文件夹和文件。 例如，如果“Include File Pattern（包含文件模式）”为input&amp;ast;，则所有与input&amp;ast（输入和发送）匹配的文件和文件夹；被接走。 默认值为&amp;ast;和指示所有文件和文件夹。 有关文件模式的更多信息，请参阅 [关于文件模式](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **等待时间：** 指定在文件夹或文件创建后扫描之前等待的时间（以毫秒为单位）。 例如，如果等待时间为3,600,000毫秒（一小时），而文件是在一分钟前创建的，则此文件将在59分钟或更久之后被提取。 默认值为 0。

      此设置有助于确保将文件或文件夹的所有内容复制到输入文件夹。 例如，如果要处理大文件，并且文件需要10分钟才能下载，请将等待时间设置为10&amp;ast;60 &amp;ast;1000毫秒。 此间隔会阻止已监视文件夹扫描文件（如果该文件没有10分钟）。

   * **删除早于以下时间的结果：** 指定在删除早于指定值的文件和文件夹之前等待的时间（以天为单位）。 此设置有助于确保结果文件夹不会变满。 值为–1天表示从不删除结果文件夹。 默认值为–1。
   * **结果文件夹名称：** 指定用于存储结果的文件夹的名称。 如果结果未显示在此文件夹中，请检查失败文件夹。 只读文件不会处理，而是保存在失败文件夹中。 您可以对以下文件模式使用绝对路径或相对路径：

      * %F =文件名前缀
      * %E =文件扩展名
      * %Y =年（满）
      * %y =年（最后两位）
      * %M =月
      * %D =每月的某天
      * %d =每年的某天
      * %H =小时（24小时制）
      * %h =小时（12小时制）
      * %m =分钟
      * %s =秒
      * %l =毫秒
      * %R =随机数（介于0和9之间）
      * %P =进程ID或作业ID
      * 例如，如果在2009年7月17日晚上8点，并且您指定了C:/Test/WF0/failure/%Y/%M/%D/%H/，则结果文件夹为C:/Test/WF0/failure/2009/07/17/20。
      * 如果路径不是绝对路径，而是相对路径，则文件夹将在监视的文件夹内创建。 默认值为result/%Y/%M/%D/，这是监视文件夹内的Result文件夹。 有关文件模式的更多信息，请参阅 [关于文件模式](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).
   * **失败文件夹名称：** 指定保存失败文件的文件夹。 此位置始终与监视文件夹相对。 可以使用文件模式，如“结果文件夹”中所述。
   * **保留文件夹名称：** 指定在成功扫描和提取后存储文件的文件夹。 路径可以是绝对目录、相对目录或空目录。 可以使用文件模式，如“结果文件夹”中所述。 默认值为preserve/%Y/%M/%D/。
   * **批量：** 指定每次扫描要选取的文件或文件夹数。 它防止了系统过载；一次扫描过多文件可能会导致崩溃。 默认值为 2。

      如果扫描间隔较小，则线程会经常扫描输入文件夹。 如果文件经常被放入监视文件夹，则扫描间隔应保持较小。 如果文件不常被删除，请使用较大的扫描间隔，以便其他服务可以使用线程。

   * **开关：** 启用此选项后，它将限制AEM表单在任何给定时间处理的已监视文件夹作业的数量。 “批量大小”值确定作业的最大数量。 有关更多信息，请参阅 [限制](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-throttling)
   * **使用相似名称覆盖现有文件**:设置为True时，将覆盖结果文件夹和保留文件夹中的文件。 当设置为False时，名称将使用带数字索引后缀的文件和文件夹。 默认值为False。
   * **失败时保留文件：** 当设置为True时，在失败时保留输入文件。 默认值为true。
   * **包含模式为的文件：** 指定分号(;)分隔的模式列表，已监视文件夹使用这些模式确定要扫描和选取的文件夹和文件。 例如，如果“Include File Pattern（包含文件模式）”为input&amp;ast;，则所有与input&amp;ast（输入和发送）匹配的文件和文件夹；被接走。 有关更多信息，请参阅 [管理帮助](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md)
   * **异步调用监视文件夹：** 将调用类型标识为异步或同步。 默认值为异步。 建议对于长生命周期进程使用异步，而对于临时或短生命周期进程，建议使用同步。
   * **启用监视文件夹：** 启用此选项后，将启用监视文件夹。 默认值为True。



## 修改现有监视文件夹的属性 {#modify-properties-of-an-existing-watched-folder}

除了更改已监视文件夹的名称之外，您还可以修改现有已监视文件夹的所有属性。 执行以下步骤以修改现有监视文件夹的属性：

1. 点按 **Adobe Experience Manager** 图标。
1. 点按 **工具** > **Forms** > **配置监视文件夹。** 将显示已配置的监视文件夹列表。
1. 在“监视文件夹”屏幕的左侧，选择监视文件夹并点按 **编辑。** 此时将显示创建监视文件夹所需的字段列表。 中列出的字段 **基本** 选项卡是必填项。 高级选项卡包含更多字段。 这些字段中的大多数都包含默认值。 您可以根据自己的要求修改这些资产。
1. 修改属性后，点按 **更新**. 将保存修改的属性。
