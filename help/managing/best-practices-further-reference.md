---
title: 核对清单 — 进一步参考
seo-title: The Checklist - Further Reference
description: 了解详细介绍和/或扩充管理项目 — 最佳实践检查表所涵盖的文档和原则的更多详细信息。
seo-description: Learn about further details that elaborate on and/or augment the documents and principles covered by the Managing Projects - Best Practices Checklist.
uuid: 58a8b4ab-e447-4a12-b9e9-4cd3db11e06a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing-checklist
content-type: reference
discoiquuid: 6fc2751e-f42a-4519-bc8c-695057f21b69
exl-id: d561bb0a-352f-4be2-95ed-32dd1e2b4019
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3777'
ht-degree: 2%

---

# 核对清单 — 进一步参考{#the-checklist-further-reference}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

本页提供了进一步的详细信息，以详细说明和/或补充 [管理项目 — 最佳实践检查列表](/help/managing/best-practices.md).

## AEM — 您将使用什么？ {#aem-what-will-you-be-using}

>[!CAUTION]
>
>本分节中的列表虽不详尽，但旨在作为介绍。

### AEM中的功能 {#features-within-aem}

实施AEM（尤其是首次实施）时，您需要查看 [AEM的功能和工作流](https://www.adobe.com/cn/marketing/experience-manager.html) 以确定您需要/需要哪些区域。

考虑您将使用的AEM的功能及其对设计的影响；例如：

* [商务](/help/sites-administering/ecommerce.md)
* [Screens](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html)
* [Assets](/help/assets/assets.md)
* [标记](/help/sites-administering/tags.md)
* [多站点管理和翻译](/help/sites-administering/msm-and-translation.md)
* [Forms](/help/forms/home.md)
* [社区](/help/communities/deploy-communities.md)
* [Livefyre](https://experienceleague.adobe.com/docs/livefyre/implementation/getting-started/c-getting-started.html)

此外，请检查 [发行说明](/help/release-notes/release-notes.md)，以了解何时添加了任何新功能。

### 集成 {#integrations}

AEM可以与其他Adobe产品和/或第三方服务集成。 这些功能可以增加您所能使用的功能。

请参阅 [解决方案集成](/help/sites-administering/integration.md) 以了解完整信息。

## 迁移或升级？ {#migrate-or-upgrade}

一个主要考虑因素是您是否希望：

* 升级现有安装。
* 将内容从当前系统迁移到新安装。

从以前的版本移动到当前版本时，有两个选项可用：

* 使用 [包管理器](/help/sites-administering/package-manager.md) 将所有内容和应用程序代码从旧系统导出到新系统。
* [升级](/help/sites-deploying/upgrade.md) 旧系统就位。 在大多数情况下，建议使用此选项。

## 基本准则 {#basic-ground-rules}

与任何项目一样，尽快制定基本规则至关重要。 其中包括：

>[!NOTE]
>
>这些点是通用的， [最佳实践检查列表](/help/managing/best-practices.md) 处理与AEM相关的特定信息。

* **角色**

   应明确定义这些内容，并将其告知项目参与者。 此外，建议突出显示：

   * 决策者
   * 联系人

* **责任**

   * 对于每个角色，明确定义与项目相关的责任有助于防止混淆。

* **参与**

   通过尽快让感兴趣的方参与进来，您可以鼓励他们成为 *利益相关者* 从而增加他们对项目成功的承诺。

   * 在客户方面，这包括作者 — 他们必须每天与系统一起工作。
   * 在您自己的项目团队中，这还将包括负责质量保证的人员。 他们越了解客户的要求，就越能规划测试。

* **沟通途径**

   * 虽然这些定义不应过于正式化，但具体定义应确保关键人员始终得到通知，从而保持最新。 应特别注意与外部方的沟通。

* **进程**

   要定义的流程取决于您的单个项目。 再次尝试保持这些简单，同时考虑以下事项：

   * 确定与任何第三方互动的流程（和沟通途径）；例如，设计代理和第三方软件供应商等。
   * 通常，客户将拥有自己的项目管理和报告过程和工具。

* **跟踪工具**

   有许多工具可用于跟踪有关错误、任务和项目其他方面的信息 — 请参阅 [潜在工具概述](#overview-of-potential-tools) 以了解更多详细信息。

   * 这里需要注意的要点是，仅保留一份信息副本并共享该信息（从而访问正在使用的工具）。 这将简化维护并帮助防止出现差异。

* **范围**

   明确界定项目在各个级别应涵盖的内容：

   * 单个版本（如果使用了迭代发布流程，且不论它们是交付给客户还是您的内部测试团队）。
   * AEM项目。
   * 整个项目；包括任何第三方软件、它们对测试的影响、组织问题和许多其他内容。
   * 在某些方面，还可以说明 *not* 在项目范围内。 这有助于防止混淆和错误假设，但应限于基本问题。

* **报表**

   明确定义您将以何种形式、多久向谁报告哪些信息。

* **术语**

   * 定义要使用的任何缩写和/或客户特定术语。

* **假设**

   * 定义所做的任何假设。

这些信息可在《项目手册》中加以定义；使用维基也可帮助确保有效处理持续的更改。 无论这些规则在何处被定义，关键因素都是：

* 信息已定义并维护
* 向有关人员明确传达信息。 尽管标准的项目管理实践，但是不能经常重复，以便清晰的角色定义和良好的沟通能够让项目成为或中断项目。
* 只保留一个版本的被跟踪信息；例如，错误跟踪、问题跟踪等。

## 关键绩效指标和目标量度 {#key-performance-indicators-and-target-metrics}

组织使用关键绩效指标(KPI)来评估其在达到目标方面的成功。 这些指标是可衡量的价值，可用于证明具体目标如何有效实现。

这些指标可以是：

* 商务:

   * 用于衡量关键业务目标。
   * 选择适合您的业务/情景的KPI，并明确定义KPI是什么、如何衡量、如何使用和由谁使用，这一点很重要。

* 性能：

   * 定义如何测量系统的性能。
   * 一些示例包括页面加载时间、服务器响应时间和数据库查询性能。

某些指标（但并非全部）可以基于您识别和定义的目标量度。

### 目标量度 {#target-metrics}

量度用于定义网站质量的定量测量 — 它们基本上是您要实现的性能目标的定义，可用于定义您的 [KPI（关键绩效指标）](#key-performance-indicators-and-target-metrics).

可以定义许多量度，但您定义的量度通常涵盖性能和并发性目标。 特别是难以量化，而且往往容易被 *情感* 评估：

* “我们的网站 *太慢了* 今天” — 何时 *慢慢* 合格？

* “所有” *停了下来* 我的同事登录时” — 系统可支持多少个并行用户？
* “我搜索时，系统 *停了下来* “ — 哪类搜索请求会影响系统？
* “需要 *年龄* 下载文件” — 可接受的下载时间（在正常网络条件下）是多少？

目标量度在项目开始时定义为：

* 指示您将提供的网站的预期维度
* 指示您要达到的最低质量
* 定义这些因素的实际测量方式
* 用作 [关键绩效指标](#key-performance-indicators-and-target-metrics)

定义目标量度时必须始终注意：

* 如果设置过高，则可能完全无法实现
* 如果设置过低波动，则不能突出显示
* 以确保能够反复、一致地测量
* 以平衡所测量的不同因素
* 某些量度将与测试环境相关，但某些量度应反映实际情景，因为它们必须在生产网站上可测量且可重复
* 根据量度对网站的重要性对量度进行优先级排序
* 将量度限制为可实际监控的量度集

在项目开发过程中，可以根据需要对其进行更新和调整。 项目成功实施后，它们可用于帮助您控制安装并监视/维护持续操作所需的服务级别。

正确使用这些量度时，可提供有用的工具；如果不负责任地使用，它们可能会浪费时间分散注意力。 和往常一样，您需要了解您在衡量什么、如何衡量它以及为什么。

>[!NOTE]
>
>本节将讨论要审议的基本原则和问题。 每个安装都不同，因此要测量的实际值会不同。

### 一切取决于您的项目设计 {#everything-rests-on-your-project-design}

所有要测量的量度，在某种程度上都会受到项目设计的影响。 相反，许多问题最好通过设计变更来解决。

因此，您应该定义目标量度 *之前* 决定您的设计。 这样，您就可以根据这些因素优化设计。 项目开发完成后，将很难对基本设计原则进行任何更改。

在为网站创建结构时，请按照建议的AEM网站结构操作。 确保您了解以下问题和/或原则：

* 如何构建网站内容。
* 模板和组件的工作方式。
* 缓存的工作原理。
* 个性化内容的影响。
* 搜索功能的工作原理。
* 如何使用CSS及相关技术创建紧凑的非冗余HTML代码。

如果您认为您的设计不符合准则，或者如果您不确定其中的某些含义，请在开始编程阶段或填写内容之前，阐明这些问题。

### 基础架构 {#infrastructure}

要定义或评估基础结构，将有助于定义目标值，例如：

* 访客/日；平均值和峰值
* 点击/日；平均值和峰值
* 提供的网页数
* web内容量

根据您的情况和网站的战略意义，这将帮助您评估和选择您的基础架构：

* 服务器数量
* AEM实例数（创作和发布）

### 性能 {#performance}

可以评估以下几个性能因素：

* 单个页面的响应时间，并考虑：

   * 创作环境中的响应时间
   * 发布环境的响应时间

* 搜索请求的响应时间

此部分可与 [性能优化](/help/sites-deploying/configuring-performance.md) 扩展了实际测量性能的技术细节。

#### 单个页面的响应时间 {#response-times-for-individual-pages}

一个关键问题是您的网站响应访客请求所花费的时间。

尽管该值会因每个请求而异，但可以定义平均目标值。 一旦证明此值既可实现又可维护，便可用于监控网站的性能并指示潜在问题的发展

创作和发布环境中的不同目标

在创作和发布环境中，您要针对的响应时间将有所不同，反映了目标受众：

* **创作环境**

   作者输入和更新内容时会使用此环境，因此必须：

   * 在更新内容页面和这些页面上的各个元素时，会生成大量请求的少数用户需要满足这些需求
   * 尽可能快地最大限度地提高将内容放到您网站上的工作效率

* **发布环境**

   此环境包含可供用户使用的内容：

   * 速度仍然至关重要，但通常比创作环境慢
   * 通常应用其他性能增强机制：

      * 内容已缓存
      * 应用负载平衡

#### 设置目标响应时间 {#setting-target-response-times}

那么，如何确定可实现（平均）的响应时间？ 这通常是经验问题：

* 网站上的以往体验
* 使用AEM体验
* 识别响应时间高于平均时间的复杂页面（如果可能，应单独优化这些页面）

但是，（在受控情况下）可以应用以下准则：

* 70%的页面请求应在100毫秒内做出响应。
* 25%的页面请求应在100毫秒–300毫秒内做出响应。
* 4%的页面请求应在300毫秒–500毫秒内做出响应。
* 1%的页面请求应在500ms-1000ms内做出响应。
* 任何页面的响应速度都不应低于1秒。

上述数字假定满足以下条件：

* 在发布时测量（无创作环境和/或CFC开销）
* 在服务器上测量（无网络开销）
* 未缓存(无AEM输出缓存，无Dispatcher缓存)
* 仅适用于具有许多依赖项的复杂项目(HTML、JS、PDF、...)
* 系统上没有其他负载

您可以使用以下几种机制来监控响应时间：

* **使用AEM request.log监控响应时间**

   性能分析的一个好起点是请求日志。 除其他信息外，您还可以使用它查看各个请求的响应时间。 请参阅 [性能优化](/help/sites-deploying/configuring-performance.md) 以了解更多详细信息。

* **使用HTML注释监控响应时间**

   `*HTML comments* can be used to include response time information within the source of each page:`

   `</body> </html>v <-- Page took 58 milliseconds to be rendered by the server --> Response times for search requests`

#### 搜索请求 {#search-requests}

在以下两方面，搜索请求可能会对您的网站产生重大影响：

* 实际搜索的响应时间

   * 快速搜索功能是您网站的质量目标

* 对一般性能的影响

   * 由于搜索功能必须扫描（可能较大）内容的部分或特别提取的索引，因此，如果未进行优化，可能会影响整个系统的性能

同样，为搜索请求设置目标是体验问题，具体取决于：

* 体验AEM
* 评估与其他目标相比使用搜索的频率
* 您的持久性管理器
* 搜索索引
* 搜索功能的复杂性；仅允许输入1个搜索词的基本搜索功能比允许用户使用AND/OR/NOT构建复杂搜索语句的高级搜索更快。

这些组件应从您的项目开始就进行计划和集成。 可用于监控的机制包括：

* **使用AEM request.log监控搜索响应时间**

   同样，request.log可用于监视搜索请求的响应时间；请参阅 [性能优化](/help/sites-deploying/configuring-performance.md) 以了解更多详细信息。

* **用于测量搜索响应时间的编程机制**

   要自定义您收集的有关搜索请求的信息及其性能，建议在项目源代码中包含信息收集；请参阅 [性能优化](/help/sites-deploying/configuring-performance.md) 以了解更多详细信息。

### 并发 {#concurrency}

您的网站将在创作和发布环境中提供给许多用户/访客。 测试时，数字通常比您使用的要多，但也会波动，难以预测。 您的网站需要针对平均并发用户/访客数进行设计，而不必注意到对性能造成负面影响。 再次 `request.log` 可用于进行并发测试；请参阅 [性能优化](/help/sites-deploying/configuring-performance.md) 以了解更多详细信息。

并发用户数的目标取决于环境类型：

* **创作环境**

   * 通常可以准确估计并发用户数。 您将知道您总共拥有多少位作者，但（可能）并非所有作者都会同时处于活动状态。

* **发布环境**

   * 这更难预测，因此您必须选择目标值。 同样，这应该基于您当前网站的经验以及对新网站的实际期望。
   * 特殊事件（例如，当您发布新的、非常受欢迎的内容时）可能会超出预期，甚至超出预期（如某些活动的票证可供销售时，媒体有时会报道）。

### 容量和卷 {#capacity-and-volume}

在讨论相关量度之前，请快速定义以下术语：

* **卷**

   * 系统处理和传送的输出量。

* **容量**

   * 系统传送卷的功能。
   * 在每个步骤中，容量和容量的测量方式各不相同，如下表所示。 为获得最佳性能，请确保每个步骤的容量与卷相匹配，并确保在所有步骤之间共享容量和卷。 例如，您可以在客户端计算机上计算导航，或将其放入缓存中，而不是在服务器上计算每个请求的导航。

* **容量和卷**

   | 内容/位置 | 容量 | 卷 |
   |---|---|---|
   | 客户端 | 用户计算机的计算能力。 | 页面布局的复杂性。 |
   | 网络 | 网络带宽。 | 页面大小（代码、图像等）。 |
   | 调度程序缓存 | Web服务器的服务器内存（主内存和硬盘）。 | Web服务器（主内存和硬盘）。 缓存的页数和大小。 |
   | 输出缓存 | AEM服务器的服务器内存（主内存和硬盘）。 | 输出缓存中的页数和大小，每页的依赖项数。 调度程序缓存会降低此卷。 |
   | Web 服务器 | Web服务器的计算能力。 | 请求数量。 缓存会降低此卷。 |
   | 模板 | Web服务器的计算能力。 | 模板的复杂性。 |
   | 存储库 | 存储库的性能。 | 从存储库加载的页数。 |

### 其他量度 {#other-metrics}

前几节详细说明了要定义的主要量度。

根据您的特定要求，单独定义或考虑上述分类时，其他量度可能会有用。

但是，最好使用一组精确且可靠的核心量度，而不是尝试测量和定义网站的每个方面。 您的网站从本质上讲，一旦交给您的用户，就会开始改变和发展。

## 安全性 {#security}

安全至关重要，而且是一个越来越大的挑战。 它 ***必须*** 从项目的最初阶段开始考虑并计划。

的 [安全检查列表](/help/sites-administering/security-checklist.md) 详细介绍您应采取哪些步骤来确保AEM安装在部署后是安全的。 其他安全方面在 [安全性（开发时）](/help/sites-developing/security.md) 和 [用户管理和安全](/help/sites-administering/security.md).

## 并行和迭代任务 {#parallel-and-iterative-tasks}

>[!NOTE]
>
>以下内容：
>
>* 提供与 *第* 实施AEM项目。
>* 旨在作为抽象概述；请参阅 [项目核对清单](/help/managing/best-practices.md) 特定阶段/里程碑/任务。
>* 任何时间尺度都是理论上的。
>


对于标准AEM项目的新实施，您需要考虑以下任务：

* 从销售流程移交。
* 客户应用程序的实施(**开发**)。
* 在客户站点(**基础架构**)。
* 创建（或迁移）内容(**内容**)。
* 切换到操作(**维护/支持**)。
* 后续版本。

![chlimage_1-2](assets/chlimage_1-2.png)

建议在所有方面使用迭代方法：

![chlimage_1-3](assets/chlimage_1-3.png)

>[!NOTE]
>
>将项目启动项拆分为 **软启动** （降低可用性、多次迭代）和 **硬启动** （完全可用 — 实时），允许在生产环境的实际条件下进行调整、优化和用户培训。

>[!NOTE]
>
>请参阅 [项目核对清单](/help/managing/best-practices.md) 有关在项目生命周期中应执行（或评估）的任务示例。

每个类别需要注意的一些方面是：

* **开发**

   * 首先定义基本架构。
   * 使用多个迭代（约束）进行开发：

      * 首次冲刺相当于首个全面开发周期。
      * 首次冲刺会在您的测试环境中首次部署。
      * 每次冲刺都有可跑的结果。
      * 每次冲刺都会获得客户的签名（结构化测试的最小值，并提供反馈）。
   * 计划在项目期间是否更新可用的AEM版本。
   * 规划在短跑期间的测试和优化。
   * 规划稳定化和优化阶段。
   * 创建要计划进行进一步发行的项目日志。
   * 计划合作伙伴的参与和移交。


* **基础架构**

   * 首先定义基本架构：

      * 定义性能要求。
      * 定义绩效目标（即明确定义预期）。
      * 定义硬件和基础架构架构；包括大小调整。
      * 定义部署。
   * 使用多个迭代；为首次冲刺和初始配置准备：

      * 开发环境。
      * 开发过程。
      * 测试环境。
      * 部署过程（包括配置管理）。
   * 规划多个负载测试。
   * 规划在短跑期间的测试和优化。
   * 规划稳定和优化阶段。
   * 尽早部署到生产环境（让运营团队设置系统以获得经验）。
   * 尽早使用指定用户和定义的角色。
   * 规划培训（例如，管理员培训）。
   * 计划移交到行动。



* **内容**

   * 基本架构：
      * 驱动内容层次结构。
      * 帮助定义内容概念。
      * 定义MSM的使用和布局。
      * 定义角色、组、工作流和权限。
   * 考虑脱机页面创建是否有用。
   * 规划以尽早创建首页和内容（用于测试和反馈）。
   * 规划现有内容的迁移。
   * 重构后规划“in-sprint-migration”。
   * 规划“内容燃尽”（上线内容的站点地图）。

## 估算时间和工作量 {#estimating-time-and-effort}

然后，您可以根据生成的任务列表对（高级别）任务定义的时间和工作量进行初步估计。 这些建议应当包括指示由谁（客户或合作伙伴）执行什么操作以及何时执行。

下表显示了标准近似值和所涉及工作量之间的关系，因此也显示了成本：

>[!CAUTION]
>
>这些数字只能用于初步估计。 经验丰富的AEM开发人员必须进行详细分析。

| 阶段 | 工作 |
|---|---|
| 开发 | 每个组件节点粗略估计2 - 4小时，即可满足所有开发要求。 |
| 开发人员测试 | 15%的发展 |
| 随访 | 10%的发展 |
| 文档 | 15%的发展 |
| JavaDoc文档 | 10%的发展 |
| 错误修复 | 15%的发展 |
| 项目管理 | 20%的项目成本用于进行中的项目管理和治理 |

然后，详细规划可将可用或所需资源与截止时间和成本相关联。

## 参考架构 {#reference-architecture}

给出了参考体系结构，为AEM体系结构提供模板解决方案。 该参考体系结构解决了企业系统常见的问题，包括扩展性、可靠性和安全性。

应定义以下网站量度：

| 分类 | 定义 |
|---|---|
| 因特网网站数量 |  |
| 内联网站点数 |  |
| 代码库的数量（例如，如果Internet和Intranet不同） |  |
| 单个页数 |  |
| 网站访问次数/日 |  |
| 页面查看次数/日 |  |
| 数据传输的卷（以GB为单位）/天 |  |
| 并发用户数（已关闭的用户组） |  |
| 并发访客数（发布） |  |
| 并发作者数量 |  |
| 注册作者数量 |  |
| 页面激活次数/工作日 |  |
| 部署期间的页面激活次数 |  |

## 潜在工具概述 {#overview-of-potential-tools}

下面列出了可供使用的工具。 它旨在作为介绍，而不是详尽的推荐列表，并且当然不应阻止您使用您喜欢的任何其他工具。

<table>
 <tbody>
  <tr>
   <td><strong>产品</strong></td>
   <td><strong>描述</strong></td>
  </tr>
  <tr>
   <td>AEM</td>
   <td><p>AEM本身提供了一系列机制来帮助您监视、测试、调查和调试应用程序；包括：</p>
    <ul>
     <li><a href="/help/sites-developing/developer-mode.md">开发人员模式</a></li>
     <li>的 <a href="/help/sites-developing/hobbes.md">测试控制台</a></li>
     <li><a href="/help/sites-administering/operations-dashboard.md">操作仪表板</a></li>
     <li><a href="/help/sites-authoring/content-insights.md">内容分析</a></li>
     <li>的 <a href="/help/sites-authoring/author-environment-tools.md#content-tree">内容树</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>硒</td>
   <td><a href="https://docs.seleniumhq.org/">硒</a> 是一个开源测试工具。 测试直接在浏览器中运行 — 模拟用户的工作方式。</td>
  </tr>
  <tr>
   <td>Microsoft项目</td>
   <td>常用的项目管理工具。</td>
  </tr>
  <tr>
   <td>吉拉</td>
   <td><a href="https://www.atlassian.com/software/jira">吉拉</a> 是一个开源工具，用于跟踪和管理软件错误的详细信息。 工作流可以根据需要强制应用于错误详细信息。</td>
  </tr>
  <tr>
   <td>Git</td>
   <td><a href="https://git-scm.com/">Git</a> 是修订控制软件。</td>
  </tr>
  <tr>
   <td>Eclipse</td>
   <td><p>Eclipse是一个开源IDE，由各种项目组成。 这些重点是构建一个由可扩展框架、工具和运行时组成的开放开发平台，用于在整个生命周期中构建、部署和管理软件。</p> <p>请参阅 <a href="/help/sites-developing/howto-projects-eclipse.md">如何使用Eclipse开发AEM项目</a> 以了解更多信息。</p> </td>
  </tr>
  <tr>
   <td>IntelliJ</td>
   <td><p>专业的（因此可能需要支付许可费用）IDE提供全面的功能。 </p> <p>请参阅 <a href="/help/sites-developing/ht-intellij.md">如何使用IntelliJ IDEA开发AEM项目</a> 以了解更多信息。</p> </td>
  </tr>
  <tr>
   <td>Maven</td>
   <td><a href="https://maven.apache.org/">马文</a> 是一种软件项目管理和理解工具，可以管理项目的构建过程（软件和文档）。</td>
  </tr>
 </tbody>
</table>

## 深入阅读 {#further-reading}

此外，以下各节特别感兴趣：

* [快速入门](/help/sites-deploying/deploy.md#getting-started)
* [技术要求](/help/sites-deploying/technical-requirements.md)
* [监控和维护实例](/help/sites-deploying/monitoring-and-maintaining.md)

### 最佳实践 {#best-practices}

Adobe为所有阶段和受众提供了更多最佳实践：

* [部署](/help/sites-deploying/best-practices.md)
* [创作](/help/sites-authoring/best-practices.md)
* [管理](/help/sites-administering/administer-best-practices.md)
* [开发](/help/sites-developing/best-practices.md)
* [项目管理](/help/managing/best-practices.md)
