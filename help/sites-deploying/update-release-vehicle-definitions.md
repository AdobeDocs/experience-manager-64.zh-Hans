---
title: 更新发放车辆定义
seo-title: 更新发放车辆定义
description: 本文详细介绍了各种类型的AEM发行版，包括完整发行版、功能包和服务包。
seo-description: 本文详细介绍了各种类型的AEM发行版，包括完整发行版、功能包和服务包。
uuid: 388fb6f5-0249-41e2-a460-1bb4cd0f8494
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 32695db5-d62d-4959-8a24-3d56b4a19904
translation-type: tm+mt
source-git-commit: d9387009bca3ce1ea5993658959c1070e07e11d0
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 3%

---


# AEM更新发布车辆定义 {#update-release-vehicle-definitions}

本文档包括有关Adobe Experience Manager(AEM)各种版本的详细信息，包括Adobe向客户交付的完整版本、功能包和服务包。

## 完整版本 {#full-release}

<table> 
 <tbody>
  <tr>
   <td><strong>定义</strong></td> 
   <td>
    <ul> 
     <li>计划发行</li> 
     <li>支持特定版本的升级路径（发行说明中定义）</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>命名</strong></td> 
   <td>
    <ul> 
     <li>主要版本的版本号根据公式X+1.Y.Z增加。 </li> 
     <li>次要版本的版本号根据公式X.Y+1.Z增加</li> 
    </ul> <p>其中X是主版本号，Y是次版本号，Z是修补程序号。</p> </td> 
  </tr>
  <tr>
   <td><strong>包含</strong></td> 
   <td>
    <ul> 
     <li>新增功能</li> 
     <li>改进</li> 
     <li>错误修复</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>文档</strong></td> 
   <td>
    <ul> 
     <li>发行说明可在文档门户上找到</li> 
     <li>有关功能、改进和错误修复的文档可在文档门户上找到</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Cadence</strong></td> 
   <td>每年</td> 
  </tr>
  <tr>
   <td><strong>可用性和安装</strong></td> 
   <td>
    <ul> 
     <li>以独立产品安装程序形式提供</li> 
     <li>可从授权许可网站和Managed Services授权许可网站获得</li> 
     <li>可能需要迁移内容存储库</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>测试级别</strong></td> 
   <td>由QA完全验证</td> 
  </tr>
 </tbody>
</table>

## Service Pack {#service-pack}

<table> 
 <tbody>
  <tr>
   <td><strong>定义</strong></td> 
   <td>
    <ul> 
     <li>计划发行</li> 
     <li>当前，无法回滚</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>命名</strong></td> 
   <td>
    <ul> 
     <li>修补程序版本号是单位数</li> 
     <li>安装后，将根据公式X.Y.Z.SPx增加已安装的发行版号补丁号码</li> 
     <li>其中X是主版本号，Y是次版本号，Z是修补程序号。 x是服务包编号。</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>包含</strong></td> 
   <td>
    <ul> 
     <li>改进</li> 
     <li>错误修复</li> 
     <li>Common Interest功能包（如果有）</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>文档</strong></td> 
   <td>
    <ul> 
     <li>文档门户上提供的发行说明</li> 
     <li>文档门户上关于功能、改进和错误修复的文档</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>Cadence</strong></td> 
   <td>季度</td> 
  </tr>
  <tr>
   <td><strong>可用性和安装</strong></td> 
   <td>
    <ul> 
     <li>以包形式交付</li> 
     <li>在包共享中可用</li> 
     <li>需要现有功能安装</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>测试级别</strong></td> 
   <td>
    <ul> 
     <li>已验证所有修复QA</li> 
     <li>借助自动化运行，实现整体包完整性</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## 累积修补程序包 {#cumulative-fix-pack-aem}

<table> 
 <tbody>
  <tr>
   <td><strong>定义</strong></td> 
   <td>
    <ul> 
     <li>单投放释放固定</li> 
     <li>包含单个组件的内容包的聚合器内容包</li> 
     <li>CFP是热修复程序的翻转，但其中没有改进。</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>命名</strong></td> 
   <td><p>X.Y.Z.CFPx</p> <p>其中X是主版本号，Y是次版本号，Z是修补程序号。 x是累积服务包编号。</p> </td> 
  </tr>
  <tr>
   <td><strong>包含</strong></td> 
   <td><p>CFP是包含所有组件在指定日期之前的修复的累积修补程序包。 例如，如果客户应用CFP3，则CFP3 = CFP1 + CFP2。</p> </td> 
  </tr>
  <tr>
   <td><strong>文档</strong></td> 
   <td>文档门户上提供的发行说明</td> 
  </tr>
  <tr>
   <td><strong>Cadence</strong></td> 
   <td>每月</td> 
  </tr>
  <tr>
   <td><strong>可用性和安装</strong></td> 
   <td>
    <ul> 
     <li>以包形式交付</li> 
     <li>在包共享中可用</li> 
     <li>取决于发布的最新服务包</li> 
     <li>CFP是自主的。 客户无需担心查找／解析依赖项。 CFP应安装在最新发布的Service Pack上。</li> 
     <li>CFP可以作为单个包进行安装，这可以改善客户体验。</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>测试级别</strong></td> 
   <td>在集成级别和回归测试中验证的QA</td> 
  </tr>
 </tbody>
</table>

## 橡木累积修补程序包 {#oak-cumulative-fix-pack}

<table> 
 <tbody>
  <tr>
   <td><strong>定义</strong></td> 
   <td>
    <ul> 
     <li>与标准CFP相似，但仅包含与Oak相关的修复</li> 
     <li>COFP是自相关的（无依赖关系）。 客户无需担心查找／解析依赖项。 [1]</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>命名</strong></td> 
   <td>oak &lt;版本&gt;</td> 
  </tr>
  <tr>
   <td><strong>包含</strong></td> 
   <td>COFP是包含针对特定1.x版本的所有Oak组件的修补程序的累积修补程序包。 例如，如果客户应用COHF 1.x.3，则应用COHF 1.x.3。 = COHF 1.x.1 + COHF 1.x.2。</td> 
  </tr>
  <tr>
   <td><strong>文档</strong></td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>Cadence</strong></td> 
   <td><p>根据需要</p> </td> 
  </tr>
  <tr>
   <td><strong>可用性和安装</strong></td> 
   <td>
    <ul> 
     <li>COFP安装过程已得到简化，可改善客户体验。 （客户只需为所有组件安装一个包即可。）</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>测试级别</strong></td> 
   <td><p>已验证QA</p> </td> 
  </tr>
 </tbody>
</table>

## 热修复 {#hot-fix}

<table> 
 <tbody>
  <tr>
   <td><strong>定义</strong></td> 
   <td><p>包含为解决严重降低基本服务或显着影响业务运营的产品缺陷而创建的一个或多个文件。 </p> </td> 
  </tr>
  <tr>
   <td><strong>命名</strong></td> 
   <td>cq-&lt;发行版&gt;-修补程序-&lt;修补程序ID&gt;-&lt;修补程序版本&gt;</td> 
  </tr>
  <tr>
   <td><strong>包含</strong></td> 
   <td>包括针对特定问题的修复</td> 
  </tr>
  <tr>
   <td><strong>文档</strong></td> 
   <td>公共修补程序的发行说明仅根据客户通过AEM支持门户提供的请求提供。</td> 
  </tr>
  <tr>
   <td><strong>Cadence</strong></td> 
   <td>根据需要</td> 
  </tr>
  <tr>
   <td><strong>可用性和安装</strong></td> 
   <td>
    <ul> 
     <li>以包形式交付</li> 
     <li>在包共享中可用</li> 
     <li>取决于发布的最新服务包</li> 
     <li>除非指定，否则大多数热修复都是独立的。 可以按任意顺序安装。 可通过“依赖关系”元素的“包共享详细信息”选项卡进行验证。</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>测试级别</strong></td> 
   <td>
    <ul> 
     <li>由客户关怀部门验证</li> 
     <li>AEM热修复程序与服务包或产品发行版的质量保证级别不同。 因此，应首先在分阶段环境上验证它们，作为质量部署流程的一部分。</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

## 叠加 {#overlay}

<table> 
 <tbody>
  <tr>
   <td><strong>定义</strong></td> 
   <td> </td> 
  </tr>
  <tr>
   <td><strong>命名</strong></td> 
   <td>overlay-&lt;票证ID&gt;</td> 
  </tr>
  <tr>
   <td><strong>包含</strong></td> 
   <td>JS或JSP文件的错误修复</td> 
  </tr>
  <tr>
   <td><strong>文档</strong></td> 
   <td>无</td> 
  </tr>
  <tr>
   <td><strong>Cadence</strong></td> 
   <td>根据需要</td> 
  </tr>
  <tr>
   <td><strong>可用性和安装</strong></td> 
   <td>
    <ul> 
     <li>由AEM客户关怀团队以包裹形式提供</li> 
     <li>未必包含在Service Pack或完整版本中</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>测试级别</strong></td> 
   <td>由客户关怀部门验证</td> 
  </tr>
 </tbody>
</table>

## 功能包 {#feature-pack}

<table> 
 <tbody>
  <tr>
   <td><strong>定义</strong></td> 
   <td>
    <ul> 
     <li>功能包是附加功能，通过Service Pack提供。 如果AEM版本发布了其最后一个服务包，Adobe将来不会为它提供任何功能包。</li> 
     <li>FP包含产品增强功能，计划在随后的产品发布中发布，但根据Adobe产品管理的决定提前发布。</li> 
     <li>功能始终与下一个主要版本合并，然后支持客户所需的AEM版本</li> 
     <li>Common Interest和GA功能包合并到下一个服务包中</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>命名</strong></td> 
   <td>cq-&lt;发行版&gt;-featurepack-&lt;featurepack ID&gt;-&lt;featurepack版本&gt;</td> 
  </tr>
  <tr>
   <td><strong>包含</strong></td> 
   <td>
    <ul> 
     <li>新增功能</li> 
     <li>改进</li> 
     <li>错误修复（增量产品更新）</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>文档</strong></td> 
   <td>有关文档，请访问helpx.adobe.com。</td> 
  </tr>
  <tr>
   <td><strong>Cadence</strong></td> 
   <td>因产品区域而异</td> 
  </tr>
  <tr>
   <td><strong>可用性和安装</strong></td> 
   <td>
    <ul> 
     <li>以包形式交付</li> 
     <li>可用于包共享。 客户通过包共享接受Adobe的条款和条件。</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><strong>测试级别</strong></td> 
   <td>通用可用性功能包已通过QA验证</td> 
  </tr>
 </tbody>
</table>

* [1]: OAK修复不是作为单独的热修复提供的。 但是，它们包含在后续的Cumulative Oak热修复中。 如有必要，可以在最新COFP上提供诊断版本。 前提是客户拥有最新的COFP运行。 诊断构建只提供与热修复相同级别的质量保证。 因此，他们提供的质量保证级别与累积修补程序包、服务包或产品版本不同。 最终修复将随下一个COFP一起提供。

