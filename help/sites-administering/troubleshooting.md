---
title: 使用日志
seo-title: Working with Logs
description: 了解如何通过使用日志对AEM进行故障诊断。
seo-description: Learn how to troubleshoot AEM by working with logs.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 5%

---

# 使用日志{#working-with-logs}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

此部分包含有关可帮助您进行故障诊断的日志的详细信息。

CRX记录详细日志。 解包并启动快速入门后，您可以在以下位置找到日志：

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## 激活DEBUG日志级别 {#activating-the-debug-log-level}

默认日志级别为“信息”，即不记录DEBUG消息。

要激活“调试”日志级别，请使用CRX资源管理器设置

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

要调试的属性。 请勿将日志保留在DEBUG日志级别，因为该日志会生成大量日志，所以不要将其保留在必要的时间以内。

调试文件中的一行通常以DEBUG开头，然后提供日志级别、安装程序操作和日志消息。 例如：

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

日志级别如下：

| 0 | 致命错误 | 操作失败，安装程序无法继续。 |
|---|---|---|
| 1 | 错误 | 操作失败。 安装将继续进行，但CRX的一部分安装不正确，无法正常工作。 |
| 2 | 警告 | 操作已成功，但遇到问题。 CRX可能正常工作，也可能无法正常工作。 |
| 3 | 信息 | 操作成功。 |

## 用于疑难解答的详细选项 {#verbose-option-used-for-troubleshooting}

启动CRX时，可以向命令行中添加 — v(verbose)选项，如下所示：&quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

使用详细选项进行故障诊断，因为此选项在控制台上显示一些快速启动日志输出。
