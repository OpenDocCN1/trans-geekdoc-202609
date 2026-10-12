
# 双蜜网系统

本地路由器配置有公开可访问的地址，代表所需服务。连接到其他地址的会被视为不需要的连接，并通过内部路由器重定向到蜜网 1。一旦蜜网 1 被攻破，蠕虫将尝试建立出站连接以攻击另一个网络。内部路由器的实现是为了将双蜜网与局域网 (LAN) 隔离。该路由器拦截来自蜜网 1 的所有出站连接，并将其重定向到蜜网 2，后者执行相同任务，形成一个回路。这种循环机制使我们能够捕获多态蠕虫的不同实例，因为它在每次循环迭代中都会发生变异。

我们在相当长一段时间后停止循环，以收集多态蠕虫。关于收集此类攻击所需时间的更多细节见第 7.4 节。

只有建立出站连接的数据包才被视为多态蠕虫，因此双蜜网系统仅转发建立出站连接的数据包。之所以制定此策略，是因为如果面对不存在的地址，良性用户不会尝试建立出站连接。事实上，我们的系统还会收集其他恶意活动，这些活动不意图自我传播，而是仅攻击目标机器。此类恶意攻击不在我们的工作范围内。

当蜜网 1 和蜜网 2 收集到足够多的蠕虫载荷实例时，它们会被转发给特征码生成组件，该组件使用特定算法自动生成特征码。

## 参考文献

*   2 K. Scarfone, and P. Mell, *Guide to Intrusion Detection and Prevention Systems (IDPS)*, National Institute of Standards and Technology Special Publication 800-94, 127 pages, February 2007, [csrc.nist.gov/publications/nistpubs/800-94/SP800-94.pdf](http://csrc.nist.gov/publications/nistpubs/800-94/SP800-94.pdf), last accessed August 11, 2012.
*   3 A. Abduvaliyev, A.-S.K. Pathan, J. Zhou, R. Roman, and W.-C. Wong, *Intrusion detection and prevention in wireless sensor networks*, Wireless Sensor Networks: Current Status and Future Trends, Eds., Shafiullah Khan, Al-Sakib Khan Pathan, and Nabil Ali Alrajeh, CRC Press, Boca Raton, FL, 2012.
*   4 J.R. Vacca, *Managing Information Security*, 1st edition, Syngress, Elsevier, Waltham, MA, March 29, 2010.
*   5 K.K. Frederick, *Network Intrusion Detection Signatures, Part Three*, Security Focus, 2002, [`www.symantec.com/connect/articles/network-intrusion-detection-signatures-part-three`](http://www.symantec.com/connect/articles/network-intrusion-detection-signatures-part-three), last accessed August 11, 2012.
*   6 R. Bace, *Intrusion Detection*, New Riders, Indianapolis, IN, 2000.
*   7 K.K. Frederick, *Network Intrusion Detection Signatures, Part Five*, SecurityFocus, 2002, [`www.symantec.com/connect/articles/network-intrusion-detection-signatures-part-five`](http://www.symantec.com/connect/articles/network-intrusion-detection-signatures-part-five), last accessed August 11, 2012.
*   8 A.-S.K. Pathan, M.M. Monowar, and Z.M. Fadlullah, *Building Next-Generation Converged Networks: Theory and Practice*, CRC Press, Boca Raton, FL, 2013.
*   9 D.J. Marchette, *Computer Intrusion Detection and Network Monitoring: A Statistical Viewpoint (Information Science and Statistics)*, 1st edition, Springer, New York, June 26, 2001.
*   10 M. Rash, A.D. Orebaugh, G. Clark, B. Pinkard, and J. Babbin, *Intrusion Prevention and Active Response: Deploying Network and Host IPS*, 1st edition, Syngress, Elsevier, Waltham, MA, April 26, 2005.
*   11 S. Northcutt, L. Zeltser, S. Winters, K. Kent, and R.W. Ritchey, *Inside Network Perimeter Security*, 2nd edition, Sams, Sams Indianapolis, IN, March 14, 2005.
*   12 M.M.Z.E. Mohammed and A.-S. K. Pathan. *Automatic Defense against Zero-day Polymorphic Worms in Communication Networks*, ISBN 9781466557277, CRC Press, Taylor & Francis Group, Boca Raton, FL, 2013.

例如在图 7.1 中，如果本地路由器怀疑数据包 1（`P[1]`）、数据包 2（`P[2]`）和数据包 3（`P[3]`）是恶意的，它会通过内部路由器将它们重定向到蜜网 1。在这三个数据包中，`P[1]` 和 `P[2]` 发起出站连接，内部路由器将这些出站连接重定向到蜜网 2。在蜜网 2 中，`P[1]` 和 `P[2]` 改变其载荷并分别变为 `P[1]’` 和 `P[2]’`（即 `P[1]’` 和 `P[2]’` 是 `P[1]` 和 `P[2]` 的实例）。因此，在这种情况下，`P[1]’` 和 `P[2]’` 发起出站连接，内部路由器将这些连接重定向到蜜网 1。在蜜网 1 中，`P[1]’` 和 `P[2]’` 改变其载荷并分别变为 `P[1]”` 和 `P[2]”`（即 `P[1]”` 和 `P[2]”` 也是 `P[1]` 和 `P[2]` 的其他实例）。现在，由于出站连接，`P[1]` 和 `P[2]` 被判定为恶意。因此，蜜网 1 将 `P[1]`、`P[1]”`、`P[2]`、`P[2]”` 转发给签名生成器进行签名生成过程。同样，蜜网 2 将 `P[1]’` 和 `P[2]’` 转发给签名生成器进行签名生成过程。

在此场景中，`P[3]` 到达蜜网 1 时未发起任何出站连接。因此，`P[3]` 不被视为恶意。

## 7.3 软件

下面介绍双蜜网系统中使用的软件工具。

### 7.3.1 Honeywall Roo CDROM

Honeywall Roo CDROM 1.4 版从蜜网项目与研究联盟下载。它提供数据捕获、控制和分析功能。

### 7.3.2 Sebek

Sebek 是一种数据捕获工具，主要记录击键，也记录所有其他类型的 `sys_read` 数据。

捕获数据后，客户端将其发送给服务器，服务器将其保存在数据库中或仅记录日志。在蜜网的情况下，服务器通常位于蜜墙机器上，它从所有蜜罐收集数据并将其汇总以供分析。

为防止入侵者检测，Sebek 采用了一些混淆方法。在客户端，它对用户完全隐藏，因此也对系统上的入侵者隐藏。然而，这还不够，因为捕获的数据必须发送给服务器，从而暴露自身。Sebek 使用隐蔽信道与服务器通信。它生成要在 Sebek 内部发送的数据包，而不使用 TCP/IP 协议栈，数据包直接发送给驱动程序，绕过原始套接字接口。这些数据包随后对用户不可见，Sebek 修改内核以防止用户阻塞数据包的传输。图 7.2 显示了 Sebek 部署。

![图 7.2 Sebek 部署。（数据来源：*Know Your Enemy: Sebek—A Kernel Based Data Capture Tool*，[`old.honeynet.org/papers/sebek.pdf`](http://old.honeynet.org/papers/sebek.pdf)，2012。）](images/pg169_1.jpg)

**图 7.2** Sebek 部署。（数据来源：*Know Your Enemy: Sebek—A Kernel Based Data Capture Tool*，[`old.honeynet.org/papers/sebek.pdf`](http://old.honeynet.org/papers/sebek.pdf)，2012。）

在多客户端的情况下，存在客户端互相看到对方数据包的风险。Sebek 在客户端上配置其自己的原始套接字接口以忽略所有传入的 Sebek 数据包。只有服务器可以接收 Sebek 数据包。由于其全面的日志记录能力，它可用作取证数据收集工具。它有一个 Web 界面，可执行数据分析。

### 7.3.3 Snort_inline

`Snort_inline` 是 Snort 的修改版。它是一种开发的入侵防御系统（IPS），利用现有入侵检测系统（IDS）的签名来对遍历 `snort_inline` 的数据包做出决策。决策通常为丢弃、拒绝、修改或允许。

## 7.4 双蜜网系统配置

本节讨论使用 VMware 的双蜜网系统架构和配置。

### 7.4.1 双蜜网架构的实现

图 7.3 显示了使用 VMware Workstation 7 版在一台配备 Intel Pentium 4、3.19-GHz CPU、8GB 内存、运行 Windows XP 64 位的个人电脑上实现的双蜜网系统架构。该个人电脑的操作系统在图 7.3 中称为*宿主操作系统*。宿主机连接到我们的家用路由器，并通过它访问互联网。

由于资源不足且为保持建立成本低廉，我们使用虚拟机部署双蜜网系统。使用了一台个人电脑，并在其上安装了 VMware Workstation。VMware Workstation 是一个软件包，让用户有机会创建虚拟机，这些虚拟机构成相互互联的虚拟网络。因此，我们创建了双蜜网系统作为一个虚拟网络，从外部世界来看是一个独立的网络。攻击者可定位蜜罐并对其发起攻击。蜜罐通过蜜墙透明地连接到互联网，蜜墙拦截所有出站和入站流量。因此，针对蜜罐的恶意流量（入站）或被攻陷蜜罐产生的恶意流量（出站）均可从蜜墙获取，以供进一步分析和调查。正如我们在第 7.2 节中提到的，蜜网 1 和蜜网 2 配置为允许无限制的出站连接。*内部路由器*用于通过将蜜网 1 的所有出站连接重定向到蜜网 2，反之亦然，来保护我们的本地网络。

![图 7.3 双蜜网架构。](img/pg171_1.jpg)

**图 7.3** 双蜜网架构。

### 7.4.2 双蜜网配置

我们的双蜜网系统包含六个组件：本地路由器、内部路由器、局域网、蜜网 1、蜜网 2 和签名生成器。每个子网（无论是本地路由器、内部路由器、局域网、蜜网 1、蜜网 2 还是签名生成器）的子网掩码因此均为 255.255.255.0。第 7.4.2.1 节至第 7.4.2.6 节讨论每个组件的配置。

#### 本地路由器配置

正如我们在第 7.2 节中提到的，本地路由器的功能是通过内部路由器将不需要的流量传递给蜜网 1。例如，如果我们的局域网 IP 地址空间为 212.0.50.0/24，且有一台公共 Web 服务器，该服务器的 IP 地址为 212.0.50.19。如果网络外部的攻击者针对 212.0.50.0/24 发起蠕虫攻击，蠕虫将扫描受害者的 IP 地址空间。极有可能会先尝试未使用的 IP 地址（例如 212.0.50.10），然后才是 212.0.50.19。因此，本地路由器将通过内部路由器将数据包重定向到蜜网 1。蠕虫攻陷蜜网 1 后，将尝试发起出站连接以危害其他网络。我们配置内部路由器以保护局域网免受蠕虫出站连接的侵害。内部路由器拦截来自蜜网 1 的所有出站连接并将其重定向到蜜网 2，后者执行与蜜网 1 相同的任务，形成环路连接。以下是本地路由器机器属性和 IP 表配置的详细信息。

##### 机器属性

*   **操作系统：** Ubuntu Linux 9.10
*   **网卡数量：** 三块网卡（`Eth0`、`Eth1` 和 `Eth2`）
    *   `Eth0` 和 `Eth2` 为桥接局域网端口
    *   `Eth1` 的功能是通过内部路由器将本地路由器与蜜网 1 连接
*   **IP 地址：**
    *   `Eth1`：192.168.50.20

##### 网络配置详解

在进行 IP-tables 设置之前，我们在本地路由器中启用了 IP 转发。

编辑 `/etc/sysctl.conf` 文件如下：

```
net.ipv4.ip_forward = 1
```

##### IP-tables 配置

使用 IP-tables 进行内核网络地址转换器的设置如下：

**不转换发往真实公共服务器的数据包：**

```bash
# iptables -t nat -A PREROUTING -m physdev --physdev-in eth0 -d 212.0.50.19 -j RETURN
```

**将发往公共 LAN 的所有其他数据包转换至内部路由器：**

```bash
# iptables -t nat -A PREROUTING -m physdev --physdev-in eth0 -d 212.0.50.0/24 -j DNAT --to 192.168.50.22
```

#### 内部路由器配置

正如第 7.2 节所述，内部路由器的功能是保护 LAN 免受蠕虫出站连接的侵害，并将 Honeynet 1 的出站连接重定向到 Honeynet 2，反之亦然。以下将详细探讨内部路由器的机器属性和 IP-tables 配置。

##### 机器属性

*   **操作系统：** Ubuntu Linux 9.10
*   **网卡数量：** 四张网卡（`Eth0`、`Eth1`、`Eth2` 和 `Eth3`）
    *   `Eth0`：连接内部路由器至 Honeynet 1 客户端
    *   `Eth1`：连接内部路由器与本地路由器
    *   `Eth2`：连接内部路由器至 Honeynet 2 客户端
    *   `Eth3`：连接内部路由器与签名生成器
*   **IP 地址：**
    *   `Eth0`：192.168.51.20
    *   `Eth1`：192.168.50.22
    *   `Eth2`：192.168.58.20
    *   `Eth3`：192.168.55.20

在设置 IP-tables 规则之前，我们在内部路由器中启用 IP 转发：

编辑 `/etc/sysctl.conf` 文件如下：

```
net.ipv4.ip_forward = 1
```

##### IP-tables 配置

使用 IP-tables 进行内核网络地址转换器的设置如下：

*   **转换来自 `Eth1` 进入 Honeynet 1 的数据包：**

    ```bash
    # iptables -t nat -A PREROUTING -i eth1 -j DNAT --to 192.168.51.22
    ```

*   **来自 Honeynet 1，不转换发往签名生成器的数据包：**

    ```bash
    # iptables -t nat -A PREROUTING -i eth0 -s 192.168.51.22 -d 192.168.55.22 -j RETURN
    ```

*   **来自 Honeynet 1，转换所有其他数据包至 Honeynet 2：**

    ```bash
    # iptables -t nat -A PREROUTING -i eth0 -j DNAT --to 192.168.58.22
    ```

*   **来自 Honeynet 2，不转换发往签名生成器的数据包：**

    ```bash
    # iptables -t nat -A PREROUTING -i eth0 -s 192.168.58.22 -d 192.168.55.22 -j RETURN
    ```

*   **来自 Honeynet 2，转换所有其他数据包至 Honeynet 1：**

    ```bash
    # iptables -t nat -A PREROUTING -i eth0 -j DNAT --to 192.168.51.22
    ```

#### LAN 配置

正如第 7.4.2.1 小节所述，我们的 LAN 中有一台公共 Web 服务器，其 IP 地址为：212.0.50.19。

以下是公共 Web 服务器的机器属性详情。

##### 机器属性

*   **操作系统：** Ubuntu Linux 9.10
*   **网卡数量：** 一张网卡：`Eth0`
