---
title: Assets 网络注意事项
description: 讨论设计 [!DNL Experience Manager] 资产部署。
contentOwner: AG
feature: Developer Tools
role: Architect,Admin
exl-id: f8f9d86f-a5e3-46ac-8d96-c2e44eac9c93
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1035'
ht-degree: 0%

---

# 资产网络注意事项 {#assets-network-considerations}

>[!CAUTION]
>
>AEM 6.4已结束扩展支持，本文档将不再更新。 有关更多详细信息，请参阅 [技术支助期](https://helpx.adobe.com/cn/support/programs/eol-matrix.html). 查找支持的版本 [此处](https://experienceleague.adobe.com/docs/).

了解您的网络与了解Adobe Experience Manager Assets同样重要。 网络可能会影响上传、下载和用户体验。 绘制网络拓扑图有助于确定网络中必须修复的瓶颈点和次优化区域，以提高网络性能和用户体验。

确保在网络图中包含以下内容：

* 从客户端设备（例如，计算机、移动设备和平板电脑）到网络的连接
* 公司网络的拓扑
* 从公司网络和 [!DNL Experience Manager] 环境
* 拓扑 [!DNL Experience Manager] 环境
* 定义 [!DNL Experience Manager] 网络接口
* 定义的工作流 [!DNL Experience Manager] 实例

## 从客户端设备到公司网络的连接 {#connectivity-from-the-client-device-to-the-corporate-network}

首先，绘制单个客户端设备与公司网络之间的连接图。 在此阶段，识别共享资源，如WiFi连接，其中多个用户访问同一点或以太网交换机以上传和下载资产。

![chlimage_1-353](assets/chlimage_1-353.png)

客户端设备以各种方式连接到公司网络，如共享WiFi、以太网到共享交换机和VPN。 识别和了解此网络上的要点对于资产规划和修改网络非常重要。

在图表左上角，3个设备被描述为共享48 Mbps WiFi接入点。 如果所有设备同时上传，则设备之间共享WiFi网络带宽。 与整个系统相比，用户可能会在这个分割的信道上遇到三个客户机的不同的阻塞点。

测量WiFi网络的真实速度是一项挑战，因为速度慢的设备可能会影响接入点上的其他客户端。 如果您计划使用WiFi进行资产交互，请同时从多个客户端执行速度测试以评估吞吐量。

图表左下方显示了通过独立渠道连接到公司网络的两个设备。 因此，每个设备的最低速度为10 Mbps和100 Mbps。

右侧显示的计算机在VPN上的公司网络上游有限，速度为1 Mbps。 1Mbps连接的用户体验与1Gbps连接的用户体验有很大不同。 根据用户与之交互的资产的大小，其VPN上行链路可能不足以完成任务。

## 公司网络的拓扑 {#topology-of-the-corporate-network}

![chlimage_1-354](assets/chlimage_1-354.png)

该图表显示公司网络内的上行链路速度高于通常使用的上行链路速度。 这些管道是共享资源。 如果共享交换机应处理50个客户端，则它可能是一个阻塞点。 在初始图中，只有两台计算机共享该特定连接。

## 从公司网络和 [!DNL Experience Manager] 环境 {#uplink-to-the-internet-from-the-corporate-network-and-aem-environment}

![chlimage_1-355](assets/chlimage_1-355.png)

在Internet和VPC连接中考虑未知因素很重要，因为由于峰值负载或大规模提供商中断，互联网上的带宽可能会受损。 一般来说，互联网连接是可靠的。 然而，有时它会引入一些关键点。

在从企业网络到互联网的上行链路上，可以使用带宽的其他服务。 了解有多少带宽可以专用或按优先级排列，这一点非常重要 [!DNL Assets]. 例如，如果1Gbps链路的利用率已达80%，则您最多只能为 [!DNL Experience Manager] 资产。

企业防火墙和代理还可以通过多种不同的方式来影响带宽。 此类设备可以使用服务质量、每用户带宽限制或每台主机的比特率限制来确定带宽优先级。 这些是需要检查的重要选项，因为它们可能会显着影响Assets用户体验。

在本例中，企业拥有10Gbps上行链路。 它应该足够大，适合多个客户。 此外，防火墙的主机速率限制为10 Mbps。 此限制可能会将到单台主机的流量限制为10 Mbps，即使到互联网的上行链路为10 Gbps。

这是最小的面向客户端的选择点。 但是，您可以评估更改或由负责此防火墙的网络操作组负责的允许列表。

从示例图中，您可以得出六台设备共享概念性的10Mbps通道。 根据杠杆资产的规模，这可能不足以满足用户的预期。

## 拓扑 [!DNL Experience Manager] 环境 {#topology-of-the-aem-environment}

![chlimage_1-356](assets/chlimage_1-356.png)

设计 [!DNL Experience Manager] 环境需要详细了解系统配置以及网络在用户环境中的连接方式。

此示例方案包括一个包含5个服务器的发布场、一个S3二进制存储区和配置了Dynamic Media 。

调度程序与两个实体(外部世界和 [!DNL Experience Manager] 实例。 要同时上传和下载操作，您应该将此数字除以二。 连接的外部存储使用单独的连接。

的 [!DNL Experience Manager] 实例与多个服务共享其1Gbps连接。 从网络拓扑的角度来看，它等同于共享一个与不同服务的单个通道。

从客户端设备审核网络到 [!DNL Experience Manager] 实例中，最小的阻塞点似乎是10Mbit企业防火墙限制。 您可以在 [Assets大小调整指南](assets-sizing-guide.md) 以确定用户体验。

## 定义的工作流 [!DNL Experience Manager] 实例 {#defined-workflows-of-the-aem-instance}

考虑网络性能时，考虑系统中将发生的工作流和发布可能很重要。 此外，您使用的S3或其他网络连接存储和I/O请求会消耗网络带宽。 因此，即使在完全优化的网络中，性能也可能受到磁盘I/O的限制。

要简化有关资产摄取的流程（尤其是在上传大量资产时），请探索资产工作流，并详细了解其配置。

在评估内部工作流拓扑时，应分析以下内容：

* 编写资产的过程
* 修改资产/元数据时触发的工作流/事件
* 读取资产的过程

以下是需要考虑的一些项目：

* XMP元数据读/写
* 自动激活和复制
* 添加水印
* 子资产摄取/页面提取
* 重叠的工作流。

以下是有关资产工作流定义的客户示例。

![chlimage_1-357](assets/chlimage_1-357.png)
