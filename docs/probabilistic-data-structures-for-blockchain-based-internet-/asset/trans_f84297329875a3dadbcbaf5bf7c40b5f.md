

# Latency Challenge in IoT

Latency 是 IoT 演进中必须考虑的一大挑战。网络操作延迟会降低 IoT 系统性能和服务质量（QoS）\[[169](#bib.xhtml#ch00-bib-169)\]。由于这些设备的计算能力有限，IoT 数据通常需要发送到云端进行计算处理。然而，IoT 用户希望从世界各地访问这些数据。因此，对于集中式云服务器来说，处理如此多的请求是一项艰巨的任务。此外，由于云服务器位于远处，访问服务的延迟显而易见。此外，还有一些对延迟敏感的应用（军事、医疗、交通）要求立即处理查询。因此，设计支持低延迟和快速响应时间的计算基础设施至关重要。除了高延迟之外，直接与云端通信会导致网络带宽过载。不过，随着包括雾/边缘计算在内的最新进展，通过在计算和存储资源上进行少量投资，延迟问题得到了缓解 \[[126](#bib.xhtml#ch00-bib-126)\]，\[[189](#bib.xhtml#ch00-bib-189)\]。因此，某些信息应在设备附近进行处理，以便在挑战更少的情况下实现 IoT。可以从 [Fig. 3.2](#04chap_03.xhtml#fig3_2) 看出，与边缘/雾计算技术相比，云框架的延迟更大。因此，对于延迟敏感的服务，更倾向于使用雾/边缘计算 \[[184](#bib.xhtml#ch00-bib-184)\]。雾/边缘计算在云端和 IoT 设备之间支持一个智能层，使 IoT 能够实现低延迟、位置感知和地理分布 \[[128](#bib.xhtml#ch00-bib-128)\]，\[[206](#bib.xhtml#ch00-bib-206)\]。显然，云计算支持集中化，而雾计算则催生了去中心化。此外，一种名为触觉互联网的最新技术已被用作最新的互联网网络，可实现超低延迟，同时具备高可用性、可靠性和安全性 \[[57](#bib.xhtml#ch00-bib-57)\]，\[[100](#bib.xhtml#ch00-bib-100)\]，\[[56](#bib.xhtml#ch00-bib-56)\]，\[[115](#bib.xhtml#ch00-bib-115)\]。

![FIGURE 3.2 Comparison of data processing at different computing locations.](images/fig3_2.jpg)

**FIGURE 3.2**  

Comparison of data processing at different computing locations.

## 3.6 Communication Challenge in IoT

IoT 设备通过互联网相互通信，并与外部环境通信。IoT 通信是远程监控、数据分析和信息交换的基础。要完全连接 IoT 设备，需要可靠且双向的信号来收集和传输设备之间的数据。在此背景下，IoT 支持多样化的无线网络。此外，无线通信的最新技术更关注于向目的地传输敏感信息，包括能量、延迟、可靠性和安全性 \[[191](#bib.xhtml#ch00-bib-191)\]。然而，由于传感器网络的无线特性，IoT 网络容易受到安全攻击，例如欺骗、水坑攻击、女巫攻击、蠕虫洞攻击和 DDoS。因此，为了充分发挥 IoT 的潜力，必须解决 IoT 通信面临的一些挑战。

此外，网络移动性和覆盖范围仍然是 IoT 的开放研究挑战，需要考虑以有效开发 IoT 用例，因为大多数 IoT 服务旨在交付给移动用户 \[[175](#bib.xhtml#ch00-bib-175)\]。这是 IoT 的一个重要断言，以确保 IoT 节点随时随地都能连接。智能手机有时会因设备移动性而出现中断。因此，需要一个有效的移动性系统来管理 IoT 中连接设备的增长。现有的蜂窝网络需要部署更多基站，以高效地将网络中的所有设备连接在一起。

除此之外，网络拥塞是 IoT 实施中需要解决的另一大挑战，因为智能设备正在推高网络中的信令负载，与传统的人机（H2H）流量相比。在网络拥塞严重的情况下，IoT 性能和网络的服务质量（QoS）会下降。因此，TCP/IP 协议必须有效处理网络拥塞问题 \[[204](#bib.xhtml#ch00-bib-204)\]。然而，当前的 TCP 实现不适用于 IoT 应用场景，因为 IoT 网络的流量模式与传统网络完全不同。

数百万台连接设备的连接会消耗电力和 CPU。为了解决这个问题，通信技术应强制实施最小电池耗尽和最小功耗。与此同时，带宽消耗是 IoT 连接的另一个问题。此外，最优能源利用是 IoT 中需要关注的重要问题之一 \[[188](#bib.xhtml#ch00-bib-188)\]，\[[200](#bib.xhtml#ch00-bib-200)\]。因此，需要一个轻量级网络来在设备和服务器之间无缝传输数据。

### Conclusion

从上述讨论可以得出结论，集中式云/第三方存在多种局限性。特别是，存储在云上的数据面临隐私问题，因为第三方可能在未经同意的情况下更改用户数据。此外，集中式服务器更容易受到 DDoS 攻击。此外，在负载重的情况下，集中式服务器可能无法为用户查询生成快速响应。最重要的是，集中式服务器可能导致单点故障。

### Activity

#### Multiple Choice Questions

1. IoT 设备和节点天然易受 \_\_\_\_\_\_ 威胁？

    1. Sensors

    2. Security

    3. Connectivity

    4. Heterogeneity

2. IoT 涉及一种在环境中无处不在的架构。

    1. True

    2. False

3. 与 IoT 相关的风险和挑战有哪些？

    1. Scalability

    2. Privacy and security

    3. Energy consumption

    4. All of the above

4. IoT 中的哪一项是关键特征，其中设备具有不同的硬件平台和网络？

    1. Heterogeneity

    2. Sensors

    3. Connectivity

    4. Security

5. 当僵尸军队被部署来向 IoT 设备发送垃圾邮件攻击时，会出现哪个挑战？

    1. Heterogeneity

    2. Sensors

    3. Connectivity

    4. Security

6. 将 IoT 数据存储在远程位置会导致查询处理的高响应时间。

    1. True

    2. False

7. IoT 网络操作延迟影响？

    1. System performance

    2. Security

    3. Privacy

    4. QoS

8. 云框架的延迟低于雾计算。

    1. True

    2. False

9. 集中式第三方在数据管理方面的局限性是什么？

    1. Vulnerable to DoS attack

    2. Single point of failure

    3. Privacy issues

    4. All of the above

10. 以下哪项延迟最低？

     1. Cloud devices

     2. User personal devices

     3. Fog devices

     4. Mist devices

1. b  2. a  3. d  4. a  5. d  6. a  7. a, d  8. b  9. d  10. b

# Part II

# Blockchain Overview

# 4

# Python Basics

## 4.1 Introduction

Python 是一种用于通用编程的高级编程语言，由 Guido Van Rossum 于 1991 年开发。Python 特别设计为高度可读，因为它使用频繁的英语关键字。Python 常用于在服务器上创建软件和 Web 应用程序。Python 的一些重要特性描述如下：

* It supports concepts of object-oriented programming.

