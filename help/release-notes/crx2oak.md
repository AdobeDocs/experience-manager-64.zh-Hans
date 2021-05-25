---
title: CRX2OAK迁移工具
seo-title: CRX2OAK迁移工具
description: 特定于Adobe Experience Manager 6.4 CRX2OAK迁移工具的发行说明。
seo-description: 特定于Adobe Experience Manager 6.4 CRX2OAK迁移工具的发行说明。
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
exl-id: 441c8ba0-f8b2-4c2c-b7be-cfdad9e1e498
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# CRX2OAK迁移工具{#crx-oak-migration-tool}

## 更改和修复列表{#list-of-changes-and-fixes}

### 1.8.6（2018年6月） {#june}

* OAK-7339修复程序通过引入LoopbackBlobStore，在MissingBlobStore上所有因UnsupportedOperationException而中断
* 使用Oak 1.8.4

### 1.8.4（2018年4月） {#april}

* 使用Oak版本1.8.2
* 从6.3到6.4的GRANITE-18104 Repo迁移错误应该更有意义
* GRANITE-16571取代SHA-1的用法

   * 使用 — version选项时，工具校验和现在为SHA-512

* GRANITE-17601在CRX2Oak中使用oak-blob-cloud嵌入oak — 升级
* GRANITE-18553 crx2oak即使未迁移版本，也会保留节点上的版本属性

### 1.6.8版（2017年3月）{#version-march}

* 已将Oak版本更新至1.6.1
* CQ-61847将crx2oak-quickstart-extension与crx2oak合并（添加了迁移配置文件）
* CQ-97488提升和删除AEM运行模式（通过重写sling.options.file）
* GRANITE-12798/OAK-4260将从Oak区段到Oak区段焦油的级别并排

### 1.4.2版（2016年3月）{#version-march-1}

* 将Oak版本升级到1.4.1
* OAK-3846 / GRANITE-10748如果SNS节点违反节点类型约束，请重命名SNS节点
* OAK-3910 / GRANITE-10730迁移节点从`mix:versionable`继承，但不包含版本历史记录
* OAK-4128 / GRANITE-11757 `RepositorySidegrade`未复制根节点属性

### 版本1.3.4（2016年1月）{#version-january}

* 将Oak版本升级到1.3.16
* OAK-3844 / GRANITE-10730更好地支持不具有版本历史的可转换节点
* OAK-3846如果SNS节点违反节点类型约束，请重命名SNS节点

### 版本1.3.2（2015年12月）{#version-december}

* 将Oak版本升级到1.3.12
* 迁移后不应移动数据存储目录(GRANITE-10447)
* 将crx2oak-quickstart-extension与crx2oak合并(CQ-61847)
* crx2oak在存储库中的重复值上失败(CQ-61906)
* 从CQ 5.x迁移后，AEM会长启动(GRANITE-10309)
* 在crx2oak中支持多个LDAP服务器(GRANITE-9917)
* 强制检查最大节点名称长度(OAK-3111)
* 支持将S3DataSource作为迁移源(OAK-3685)
