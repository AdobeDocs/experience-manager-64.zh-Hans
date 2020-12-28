---
title: CRX2OAK迁移工具
seo-title: CRX2OAK迁移工具
description: 特定于Adobe Experience Manager6.4 CRX2OAK迁移工具的发行说明。
seo-description: 特定于Adobe Experience Manager6.4 CRX2OAK迁移工具的发行说明。
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---


# CRX2OAK迁移工具{#crx-oak-migration-tool}

## 更改列表和修复{#list-of-changes-and-fixes}

### 1.8.6（2018年6月）{#june}

* OAK-7339通过引入LoopbackBlobStore，修复在MissingBlobStore上所有因UnsupportedOperationException而中断的故障
* 使用Oak 1.8.4

### 1.8.4（2018年4月）{#april}

* 使用Oak版本1.8.2
* GRANITE-18104回购程序从6.3迁移到6.4的错误应该更有意义
* GRANITE-16571取代SHA-1的使用

   * 使用—version选项时，工具校验和现在为SHA-512

* GRANITE-17601将oak-upgrade嵌入CRX2Oak中，使用oak-blob-cloud
* GRANITE-18553 crx2oak在节点上保留版本属性，即使版本未迁移也是如此

### 版本1.6.8（2017年3月）{#version-march}

* 将Oak版本更新为1.6.1
* CQ-61847将crx2oak-quickstart-extension与crx2oak合并(添加了迁移用户档案)
* CQ-97488提升和删除AEM运行模式（通过重写sling.options.file）
* GRANITE-12798/OAK-4260将Oak Segment改为Oak Segment Tar的能力

### 版本1.4.2（2016年3月）{#version-march-1}

* 将Oak版本升级到1.4.1
* OAK-3846 / GRANITE-10748如果SNS节点违反节点类型约束，请重命名这些节点
* OAK-3910 / GRANITE-10730迁移节点从`mix:versionable`继承，无版本历史
* OAK-4128 / GRANITE-11757 `RepositorySidegrade`未复制根节点属性

### 版本1.3.4（2016年1月）{#version-january}

* 将Oak版本升级到1.3.16
* OAK-3844/GRANITE-10730更好地支持不带版本历史记录的可转换节点
* OAK-3846如果SNS节点违反节点类型限制，则重命名SNS节点

### 版本1.3.2（2015年12月）{#version-december}

* 将Oak版本升级到1.3.12
* 迁移后不应移动数据存储目录(GRANITE-10447)
* 将crx2oak-quickstart-extension与crx2oak合并(CQ-61847)
* crx2oak在存储库中的重复值上失败(CQ-61906)
* 从CQ 5.x迁移后的长AEM开始(GRANITE-10309)
* 在crx2oak中支持多个LDAP服务器(GRANITE-9917)
* 强制检查最大节点名称长度(OAK-3111)
* 支持将S3DataSource作为迁移源(OAK-3685)
