
user@Headquarters:~$ `ping 172.16.1.10`

```
PING 172.16.1.10 (172.16.1.10) 56(84) bytes of data.
64 bytes from 172.16.1.10: icmp_seq=2 ttl=64 time=2.34 ms
64 bytes from 172.16.1.10: icmp_seq=3 ttl=64 time=2.15 ms
64 bytes from 172.16.1.10: icmp_seq=4 ttl=64 time=2.34 ms
64 bytes from 172.16.1.10: icmp_seq=5 ttl=64 time=2.30 ms
^C
--- 172.16.1.10 ping statistics
5 packets transmitted, 4 received, 20% packet loss, time 4023ms
rtt min/avg/max/mdev = 2.08/2.21/2.34/0.11 ms
```

user@Headquarters:~$

策略部署成功后，你可以使用威胁防御设备的 CLI 来查看配置。如你所知，你可以运行 `show running-config` 命令。带有 `crypto` 参数将显示 VPN 配置，如示例 19-2 所示。

### 示例 19-2 威胁防御上的站点到站点配置

点击此处查看代码图像

```
> show running-config crypto

crypto ipsec ikev2 ipsec-proposal CSM_IP_1
 protocol esp encryption aes-gcm-256 aes-gcm-192
 protocol esp integrity null
crypto ipsec security-association pmtu-aging infinite
crypto map CSM_Outside_Interface_map 1 match address CSM_ACL_1
crypto map CSM_Outside_Interface_map 1 set peer 203.0.113.2
crypto map CSM_Outside_Interface_map 1 set ikev2 ipsec-proposal CSM_IP_1
crypto map CSM_Outside_Interface_map 1 set reverse-route
crypto map CSM_Outside_Interface_map interface OUTSIDE_INTERFACE
crypto ca trustpool policy
crypto ikev2 policy 1
 encryption aes-256
 integrity sha512
 group 21
 prf sha512
 lifetime seconds 86400
crypto ikev2 enable OUTSIDE_INTERFACE
crypto ikev1 am-disable
>
```

图 19-31 显示了 IKEv2 握手的两对包，随后是 ping 测试的四对包。ICMP 请求和响应的数据包被 ESP 头封装。

要查找威胁防御中 VPN 会话的详细统计信息，请运行 `show vpn-sessiondb detail` 命令。要查看 VPN 会话中使用的 IKEv2 和 IPsec 属性的细节，请在命令中添加 `l2l` 参数，如示例 19-3 所示。

### 示例 19-3 VPN 会话详细信息

```
! 要显示 VPN 会话统计信息：
> show vpn-sessiondb detail

-------------------------------------------------------------------
VPN 会话摘要
-------------------------------------------------------------------
                       活动 : 累计 : 峰值并发 : 非活动
                     ----------------------------------------------
站点间 VPN     :      1 :          1 :           1
  IKEv2 IPsec        :      1 :          1 :           1
-------------------------------------------------------------------
总活动与非活动数:  1             总累计 :      1
设备总 VPN 容量: 75
设备负载              : 1%
-------------------------------------------------------------------
-------------------------------------------------------------------
隧道摘要
-------------------------------------------------------------------
                       活动 : 累计 : 峰值并发
                     ----------------------------------------------
IKEv2                :      1 :          1 :               1
IPsec                :      1 :          1 :               1
-------------------------------------------------------------------
总计               :      2 :          2
-------------------------------------------------------------------
>

! 要显示局域网到局域网 VPN 会话信息：
> show vpn-sessiondb detail l2l

会话类型: 局域网到局域网详细
连接   : 203.0.113.2
索引        : 1                      IP 地址      : 203.0.113.2
协议     : IKEv2 IPsec
加密   : IKEv2: (1)AES256  IPsec: (1)AES-GCM-256
哈希      : IKEv2: (1)SHA512  IPsec: (1)none
发送字节     : 3780                   接收字节     : 3780
登录时间   : 22:02:36 UTC Sat Mar 27 2021
持续时间     : 0h:04m:11s
隧道区域  : 0
IKEv2 隧道: 1
IPsec 隧道: 1
IKEv2:
  隧道 ID    : 1.1
  UDP 源端口 : 500                 UDP 目的端口 : 500
  远程认证模式: preSharedKeys
  本地认证模式: preSharedKeys
  加密   : AES256              哈希      : SHA512
  重密钥间隔 (T): 86400 秒       剩余重密钥 (T): 86148 秒
  PRF          : SHA512              D/H 组    : 21
  过滤器名称  :
IPsec:
  隧道 ID    : 1.2
  本地地址   : 192.168.1.0/255.255.255.0/0/0
  远程地址  : 172.16.1.0/255.255.255.0/0/0
  加密   : AES-GCM-256         哈希      : none
  封装: 隧道
  重密钥间隔 (T): 28800 秒       剩余重密钥 (T): 28548 秒
  重密钥间隔 (D): 4608000 K-Bytes     剩余重密钥 (D): 4607997 K-Bytes
  空闲超时: 30 分          剩余空闲时间 : 26 分
  发送字节     : 3780                接收字节     : 3780
  发送包数      : 45                  接收包数      : 45
>
```

在 IPsec 隧道成功建立后，你可以从 CLI 查看安全关联（SA）的详细统计信息。运行 `show crypto ikev2 sa detail` 命令（参见示例 19-4）查看 IKEv2 安全关联，并运行 `show crypto ipsec sa detail` 命令查看 IPsec 安全关联（参见示例 19-5）。

### 示例 19-4 IKEv2 安全关联详情

点击此处查看代码图片

```
> show crypto ikev2 sa detail

IKEv2 SAs:
会话 ID:1, 状态:UP, IKE 计数:1, 子通道计数:1
隧道 ID   本地             远程            角色
1906247   203.0.113.1/500   203.0.113.2/500   准备     发起者
      加密: AES-CBC, 密钥长度: 256, 哈希: SHA512, DH 组:21, 认证: PSK
      生存/活动时间: 86400/21 秒
      会话 ID: 1
      状态: 协商完成
      本地 spi: 1B8980EB3784BB      远程 spi: 91154FB2E310F0
      本地 ID: 203.0.113.1
      远程 ID: 203.0.113.2
      本地请求 ID: 18           远程请求 ID: 0
      本地队列: 18           远程队列: 0
      本地窗口: 18                  远程窗口: 1
      DPD 配置为 10 秒，重试: 2
      检测到 NAT-T
      IKEv2 MTU: 576 字节，开销: 28 字节，有效 MTU: 548 字节
      父 SA:
      正在删除
      已标记为删除
      子 SA: 192.168.1.0/0 - 192.168.1.255/6535
      远程选择器: 172.16.1.0/0 - 172.16.1.255/6535
      ESP spi/出: 0xe62a8d7b/0bc47fd
      AH spi/出: 0/0
      加密: AES-GCM, 密钥长度: 256, esp_hmac: N/A
      ah_hmac: 无，压缩: 隧道
```

### 示例 19-5 IPsec 安全关联详情

点击此处查看代码图片

```
> show crypto ipsec sa detail

接口: OUTSIDE_INTERFACE
    加密映射: CSM_Outside_Interface_map, 序列: 1, 地址: 203.0.113.1
      访问列表: CSM_IPSEC_ACL permit 192.168.1.0 255.255.255.0 172.16.1.0 255.255.255.0
      本地 ID (地址/掩码/端口): (192.168.1.0/255.255.255.0/0/0)
      远程 ID (地址/掩码/端口): (172.16.1.0/255.255.255.0/0/0)
      当前对端: 203.0.113.2
      封装: 45, 加密: 45, 摘要: 45
      解包: 45, 解密: 45, 验证: 45
      压缩: 0, 解压缩: 0
      未压缩: 45, 压缩失败: 0, 失败: 0
      预分片成功: 0, 预分片失败: 0, 创建碎片: 0
      发送 PMTU: 0, 接收 PMTU: 0, 需要重组的解碎片: 0
      TFC 接收: 0, TFC 发送: 0
      ICMP 错误接收: 0, 无效 ICMP 错误: 0
      无 SA (发送): 0, 无效 SA (接收): 0
      封装失败 (发送): 0, 解包失败 (接收): 0
      无效协议 (接收): 0, 验证失败: 0
      无效身份 (接收): 0, 无效长度 (接收): 139624912
      无效填充 (接收): 0
      无效版本 (发送): 0, 无效版本 (接收): 0
      无效长度 (发送): 0, 无效长度 (接收): 0
      无效上下文 (发送): 0, 无效上下文 (接收): 0
      无效接口 (发送): 0, 无效接口 (接收): 0
      失败 (发送): 0, 失败 (接收): 0
      重放翻滚 (发送): 0, 重放翻滚 (接收): 0
      重放失败 (接收): 0
      最小 MTU 分片失败 (发送): 0, 错误碎片偏移 (接收): 0
      内部错误 (发送): 0, 内部错误 (接收): 0

      本地加密端: 203.0.113.1/500, 远程加密端: 203.0.113.2/500
      路径 MTU: 1500, ipsec 开销: 55(36), 链路 MTU: 1500
      PMTU 剩余时间 (秒): 0, DF 策略: 复制 DF
      ICMP 错误验证: 禁用，TFC 数据包: 禁用
      当前出站 spi: BC4877FD
      当前入站 spi : E62A8D7B

    入站 esp sa:
      spi: 0xE62A8D7B (3861548411)
          SA 状态: 活动
          变换: esp-gcm-256 esp-null-hmac
          使用中设置: {L2L, 隧道, IKEv2}
          槽: 0, 连接 ID: 1, 加密映射: CSM_Outside_Interface_map
          SA 计时: 剩余密钥寿命 (kB/sec): 4101116/28719
          IV  own: 8 字节
          重放支持: Y
          重放位图:
          0x00003FFF 0xFFFFFFFF
    出站 esp sa:
      spi: 0xBC4877FD (3158865917)
```

如果在 VPN 网关上启用了 NAT 豁免以排除内部 IP 地址的转换，你可以通过查看 `show running-config nat` 命令的输出来确认身份 NAT 规则的部署（参见示例 19-6）。此外，`show xlate detail` 命令确认由身份规则执行的地址转换豁免。

### 示例 19-6 NAT 豁免实现

点击此处查看代码图像

```
> show running-config nat
nat (INSIDE_INTERFACE,OUTSIDE_INTERFACE) source static HQ_LAN HQ_LAN destination
static Branch_LAN Branch_LAN no-proxy-arp route-lookup
!
object network HQ_LAN
 nat (INSIDE_INTERFACE,OUTSIDE_INTERFACE) dynamic interface
>
> show xlate detail
2 in use, 2 most used
Flags: D - DNS, e - extended, I - identity, i - dynamic, r - portmap,
       s - static, T - twice, N - net-to-net
NAT from INSIDE_INTERFACE:192.168.1.0/24 to OUTSIDE_INTERFACE:192.168.1.0/24
    flags sIT idle 0:00:00 timeout 0:00:00 refcnt 0 xlate id 0x2b8047a7a3c0
NAT from OUTSIDE_INTERFACE:172.16.1.0/24 to INSIDE_INTERFACE:172.16.1.0/24
    flags sIT idle 0:00:00 timeout 0:00:00 refcnt 0 xlate id 0x2b8047a7a1c0
>
```

## 远程访问 VPN 部署

以下章节将阐述如何使用 Secure Firewall 实现远程访问 VPN。

### 先决条件

在开始配置远程访问 VPN 服务之前，请满足以下先决条件：

*   通过管理中心注册威胁防御设备，该设备将在总部提供远程访问 VPN 服务。在路由模式下配置威胁防御设备的入入接口和出口接口，并设置必要的 IP 地址。如果总部的威胁防御接口已配置为站点到站点 VPN 实验的一部分（如图 19-19 所示），你现在可以重复使用。请注意，与站点到站点 VPN 实验不同，远程访问 VPN 实验只需要一个威胁防御设备，它作为终端（参见图 19-32）。

    ![图 19-32 实现远程访问 VPN 服务的实验拓扑](img/19fig32.jpg)

    **图 19-32** 实现远程访问 VPN 服务的实验拓扑
