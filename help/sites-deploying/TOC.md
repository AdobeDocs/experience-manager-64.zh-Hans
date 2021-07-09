---
cloud: Experience Cloud
product: adobe experience manager
solution: Experience Manager, Experience Manager Sites, Experience Manager 6.4
audience: end-user
user-guide-title: AEM 6.4 Deploying 指南
breadcrumb-title: Deploying 指南
user-guide-description: 详细了解 Adobe Experience Manager 6.4 的安装、部署和架构，包括我们的 Adobe Managed Services 云部署。
feature: 部署
role: Architect
source-git-commit: 5b0eef590f9a0c709fa21b8dbcf6a2f286a20237
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 17%

---


# AEM 6.4 Deploying用户指南 {#deploying}

+ [Deploying用户指南](home.md)
+ AEM平台{#introduction}简介
   + [AEM平台简介](platform.md)
   + [技术要求](technical-requirements.md)
   + [AEM 6.4中的存储元素](storage-elements-in-aem-6.md)
   + [AEM with MongoDB](aem-with-mongodb.md)
+ 部署 AEM {#deploying}
   + [部署和维护](deploy.md)
   + [推荐的部署](recommended-deploys.md)
   + [应用程序服务器安装](application-server-install.md)
   + [自定义独立安装](custom-standalone-install.md)
   + [命令行启动和停止](command-line-start-and-stop.md)
   + [在AEM 6中配置节点存储和数据存储](data-store-config.md)
   + [修订版清理](revision-cleanup.md)
   + [如何使用TarMK冷备用运行AEM](tarmk-cold-standby.md)
   + [AEM 6.4中的RDBMS支持](rdbms-support-in-aem.md)
   + [Oak查询和索引](queries-and-indexing.md)
   + [通过Oak-run Jar索引](indexing-via-the-oak-run-jar.md)
   + [Oak-run.jar索引用例](oak-run-indexing-usecases.md)
   + [Oak索引疑难解答](troubleshooting-oak-indexes.md)
   + [选择加入汇总使用情况统计信息收集](opt-in-aggregated-usage-statistics.md)
   + [疑难解答](troubleshooting.md)
+ 配置AEM {#configuring}
   + [基本配置概念](configuring.md)
   + [记录](configure-logging.md)
   + [配置OSGi](configuring-osgi.md)
   + [OSGi配置设置](osgi-configuration-settings.md)
   + [运行模式](configure-runmodes.md)
   + [Web 控制台](web-console.md)
   + [复制](replication.md)
   + [使用互相SSL复制](mssl-replication.md)
   + [复制故障诊断](troubleshoot-rep.md)
   + [静态对象的过期](expiration-static-objects.md)
   + [版本清除](version-purging.md)
   + [监控和维护AEM实例](monitoring-and-maintaining.md)
   + [卸载作业](offloading.md)
   + [单点登录](single-sign-on.md)
   + [资源映射](resource-mapping.md)
   + [启用HTTP Over SSL](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/configuring/ssl-by-default.html)
   + [一致性和遍历检查](consistency-check.md)
   + [性能准则](performance-guidelines.md)
   + [性能优化](configuring-performance.md)
   + [Assets性能指南](https://experienceleague.adobe.com/docs/experience-manager-64/assets/administer/performance-tuning-guidelines.html?lang=en)
   + [配置操作方法文章](ht-deploy.md)
   + [删除Geometrixx站点](removing-the-geometrixx-sites.md)
   + [配置Web控制台](configuring-web-console.md)
+ 升级到AEM 6.4 {#upgrading}
   + [升级到AEM 6.4](upgrade.md)
   + [规划升级](upgrade-planning.md)
   + [利用模式检测器评估升级复杂度](pattern-detector.md)
   + [AEM 6.4中的向后兼容性](backward-compatibility.md)
   + [升级过程](upgrade-procedure.md)
   + [使用离线重新索引以减少升级期间的停机时间](upgrade-offline-reindexing.md)
   + [执行就地升级](in-place-upgrade.md)
   + [延迟内容迁移](lazy-content-migration.md)
   + [使用CRX2Oak迁移工具](using-crx2oak.md)
   + [升级前维护任务](pre-upgrade-maintenance-tasks.md)
   + [升级后检查和疑难解答](post-upgrade-checks-and-troubleshooting.md)
   + [升级自定义搜索Forms](upgrading-custom-search-forms.md)
   + [可持续升级](sustainable-upgrades.md)
   + [升级代码和自定义](upgrading-code-and-customizations.md)
   + [应用程序服务器安装的升级步骤](app-server-upgrade.md)
   + [升级后卸载的过时包列表](obsolete-bundles.md)
+ 存储库重组{#restructuring}
   + [AEM 6.4中的存储库重组](repository-restructuring.md)
   + [AEM 6.4中的常用存储库重组](all-repository-restructuring-in-aem-6-4.md)
   + [AEM 6.4中的站点存储库重组](sites-repository-restructuring-in-aem-6-4.md)
   + [AEM 6.4中的资产存储库重组](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html?lang=en)
   + [Dynamic Media 6.4中的存储库重组](dynamicmedia-repository-restructuring-in-aem-6-4.md)
   + [Forms 6.4中的存储库重组](forms-repository-restructuring-in-aem-6-4.md)
   + [AEM 6.4中的电子商务存储库重组](ecommerce-repository-restructuring-in-aem-6-4.md)
   + [6.4中的AEM Communities存储库重组](communities-repository-restructuring-in-aem-6-4.md)
+ 电子商务 {#ecommerce}
   + [电子商务概述](ecommerce.md)
   + [SAPCommerce Cloud](sap-commerce-cloud.md)
   + [SalesforceCommerce Cloud](https://github.com/adobe/commerce-salesforce)
   + [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)
+ 最佳实践 {#practices}
   + [部署最佳实践](best-practices.md)
   + [性能树](performance-tree.md)
   + [性能测试的最佳实践](best-practices-for-performance-testing.md)
   + [有关查询和索引的最佳实践](best-practices-for-queries-and-indexing.md)
   + [面向客户的用户界面Recommendations](ui-recommendations.md)
   + [性能和可扩展性](performance.md)


<!--

To be removed:
[Quickstart for AEM Screens](setting-up-a-basic-project-screens.md)
[Device Control Center](device-control-center.md)
[repository-restructuring-in-aem64](repository-restructuring-in-aem64.md)
[Web Console] (configuring-web-console.md)
[Configuring and Deploying AEM Screens](configuring-screens-introduction.md)
[Kickstart Guide](kickstart-for-aem-screens.md)
/help/sites/deploying/using/performance-lp.md
/help/sites-deploying/do-not-delete-performance-guidelines-pdf.md
/help/sites-deploying/removing-the-geometrixx-sites.md
/help/sites-deploying/consistency-check.md

Redirects:
[(Enabling HTTP Over SSL)](config-ssl.md) redirect to /content/help/en/experience-manager/6-4/sites-administering/ssl-by-default
-->
