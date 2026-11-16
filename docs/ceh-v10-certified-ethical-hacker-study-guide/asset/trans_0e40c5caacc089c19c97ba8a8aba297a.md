

![](img/421171b17a0c0dfae0aacde15d9831c1_429_0.png)

## 图 11.7 Linux 下的无线配置

## 自带设备 (BYOD)

你很可能至少拥有一台移动设备，无论是智能手机、平板电脑还是笔记本电脑。它也可能是像 Microsoft Surface 这样的混合设备。由于这些设备普及且易于使用，人们随身携带它们，并且几乎随时都带着至少一部智能手机。公司通常希望利用这些计算资源，因此可能会制定政策，规定如何允许人们在企业网络上使用自己的设备。此政策通常被称为自带设备 (BYOD)。公司可能要求设备获得批准或满足某些最低要求。

允许个人设备接入其网络的公司，通常是通过无线网络（因为移动设备通常没有有线连接），可能对任何设备连接持开放态度。这意味着它们可能没有一种网络访问控制 (NAC) 形式来限制哪些设备可以与其无线网络通信。它们可以通过阻塞 MAC 地址来实现此目的，以防止不在白名单上的人甚至无法进行用户级身份验证。如前所述，使用企业身份验证的 WPA2 也通过要求用户进行身份验证来提供保护。

关于通过 Wi-Fi 访问，还需要考虑网络隔离。企业通常将 Wi-Fi 客户端放入一个隔离网络中，该网络表现得就像位于企业之外一样。要访问内部企业资源，Wi-Fi 网络上的任何人（即使在身份验证之后）都必须使用虚拟专用网络连接才能访问业务资产。他们使用 WPA2-Enterprise 身份验证和加密连接到受密码保护的 Wi-Fi 网络，然后必须进一步进行身份验证才能打开通往网络内部的隧道。这意味着即使你访问了员工 Wi-Fi 网络（通常与可能也提供的访客 Wi-Fi 网络分开），你仍然无法轻松访问业务资产。

然而，采用 BYOD 的公司可能使访问其资源变得更加容易。当然，BYOD 不是员工通过 Wi-Fi 访问企业资源的唯一方式，但如果启用了 BYOD，很可能意味着没有关于哪些设备可以连接的限制，这会阻止某人甚至无法提供身份验证凭据以获取访问权限。

## Wi-Fi 攻击

攻击 Wi-Fi 网络有多种方式。首先，与任何类型的攻击一样，你可以从侦察开始。可以使用 Wireshark 和其他工具来完成这一点。在嗅探时，你需要生成流量。实现这一点的一种方法是强制终端对其自身进行身份验证。你可以使用去认证攻击来做到这一点。另一种攻击称为邪恶双胞胎。这是一个流氓接入点，但它模仿合法的接入点。还有一种称为密钥重装攻击的攻击，有时称为 KRACK，可用于强制终端以攻击者可以轻松解密的方式发送消息。

## 嗅探

如前所述，Wireshark 可用于捕获包含无线电头部的网络流量。在尝试收集信息时，无线电头部非常重要。不过，它们不是唯一携带信息的头部。你会希望查看来自接入点的所有信标，以及可能在站点和接入点之间发送的任何身份验证消息。要查看整个协议栈，需要将无线接口设置为监控模式。实现这一点的一种方法是使用 aircrack-ng 软件包中的 airmon-ng 程序。在以下代码清单中，你可以看到使用 airmon-ng 从无线接口创建监控接口。最终，你将获得一个可用于收集无线电和其他流量的新接口。

### 使用 airmon-ng

```
root@quiche:~# airmon-ng start wlan0

Found 3 processes that could cause trouble.
Kill them using 'airmon-ng check kill' before putting
the card in monitor mode, they will interfere by changing channels
and sometimes putting the interface back in managed mode

PID Name
640 wpa_supplicant
30835 NetworkManager
30859 dhclient
```

| PHY | 接口 | 驱动程序 | 芯片组 |
|---|---|---|---|
| phy0 | wlan0 | rt2800usb | Ralink Technology, Corp. RT5372 |

```
(mac80211 monitor mode vif enabled for [phy0]wlan0 on [phy0]wlan0mon)
(mac80211 station mode vif disabled for [phy0]wlan0)
```

开头你会注意到一些警告。这是因为所运行的 Linux 版本管理着网络接口。airmon-ng 需要能够对网络接口进行更改，因此最好不要运行管理接口的进程。虽然此示例在 Linux 下运行，但 aircrack-ng 确实有 Windows 软件包，相同的程序也可在那里使用。创建监控接口后，你可以像使用任何其他网络接口一样使用它。你可以使用 tcpdump 捕获通过监控接口的所有网络流量。在以下清单中，你可以看到使用 tcpdump 和接口 wlan0mon（由 airmon-ng 创建）的示例。

### 将 tcpdump 与监控接口一起使用

```
root@quiche:~# tcpdump -i wlan0mon
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0mon, link-type IEEE802_11_RADIO (802.11 plus radiotap header), capture size 262144 bytes
20:49:20.747433 1.0 Mb/s 2457 MHz 11b -19dBm signal antenna 1 Data IV:8cae Pad 20 KeyID 2
20:49:21.190521 1.0 Mb/s 2457 MHz 11b -43dBm signal antenna 1 Clear-To-Send
RA:64:1c:b0:94:ba:57 (oui Unknown)
20:49:21.387878 1.0 Mb/s 2457 MHz 11b -67dBm signal antenna 1 Probe Request
(WifiMyqGdo) [1.0 2.0 5.5 11.0 Mbit]
20:49:21.403289 1.0 Mb/s 2457 MHz 11b -67dBm signal antenna 1 Probe Request
(WifiMyqGdo) [1.0 2.0 5.5 11.0 Mbit]
20:49:21.537165 1.0 Mb/s 2457 MHz 11b -47dBm signal antenna 1 Probe Request
(ZoeyWasHere) [1.0 2.0 5.5 11.0 Mbit]
20:49:21.589809 1.0 Mb/s 2457 MHz 11b -19dBm signal antenna 1 Acknowledgment
RA:64:1c:b0:94:ba:57 (oui Unknown)
20:49:21.689230 1.0 Mb/s 2457 MHz 11b -43dBm signal antenna 1 Clear-To-Send
RA:64:1c:b0:94:ba:57 (oui Unknown)
20:49:23.247016 1.0 Mb/s 2457 MHz 11b -67dBm signal antenna 1 Acknowledgment
RA:ec:aa:a0:4d:31:a8 (oui Unknown)
20:49:23.250814 1.0 Mb/s 2457 MHz 11b -65dBm signal antenna 1 Acknowledgment
RA:f6:aa:a0:4d:31:a8 (oui Unknown)
20:49:23.594399 1.0 Mb/s 2457 MHz 11b -19dBm signal antenna 1 Acknowledgment
RA:64:1c:b0:94:ba:57 (oui Unknown)
```

### 将 tcpdump 与监控接口一起使用（续）

```
20:49:23.602831 1.0 Mb/s 2457 MHz 11b -21dBm signal antenna 1 Beacon (CasaChien) [1.0* 2.0* 5.5* 11.0* 6.0 9.0 12.0 18.0 Mbit] ESS CH: 11, PRIVACY
20:49:24.258485 1.0 Mb/s 2457 MHz 11b -43dBm signal antenna 1 Clear-To-Send
RA:64:1c:b0:94:ba:57 (oui Unknown)
20:49:24.635482 1.0 Mb/s 2457 MHz 11b -57dBm signal antenna 1 Probe Request
(CasaChien) [1.0 2.0 5.5 11.0 6.0 9.0 12.0 18.0 63.5 Mbit]
20:49:24.656324 1.0 Mb/s 2457 MHz 11b -51dBm signal antenna 1 Acknowledgment
RA:18:d6:c7:7d:ee:11 (oui Unknown)
20:49:24.658753 1.0 Mb/s 2457 MHz 11b -51dBm signal antenna 1 Acknowledgment
RA:70:3a:cb:52:ab:fc (oui Unknown)
```

从 tcpdump 输出中，你可以看到所有无线电流量，包括信号信息。你可以看到通信所使用的频率，所有消息中均为 2457 MHz。你也可以看到信号强度。它以分贝为单位，相对于毫瓦，表示为 dBm。分贝是使用对数尺度的两个值的比率。
不过，dBm 不是一个比率。它是一个绝对值，因为它使用毫瓦作为参考点。这是衡量无线网络信号强度的标准方法。你能获得的最佳信号是 –10 dBm。你可以看到 –19 dBm 到 –67 dBm 的值。这些仍然是可用的信号。在无线网络中，你能获得的最低值是 –100。超过这个值的信号无法使用。

从 tcpdump 输出中，你可以看到针对网络的探测请求。这些探测请求来自曾经连接过这些网络的设备。例如，有一个带有无线功能的车库门开启器正在尝试查找网络 WiFiMyqGdo。这是设备出厂时配置的网络。如果你尝试进行邪恶双胞胎攻击，这些信息可能很有用。不过，你可能希望从数据包捕获中查看其他信息。你可以做的就是导出数据包捕获。在以下清单中，你可以看到从 tcpdump 导出数据包捕获的示例。因为我们使用的是监控接口，所以仍然会接收所有无线电消息。

### 从监控接口写入捕获

```
root@quiche:~# tcpdump -w radio.pcap -i wlan0mon
tcpdump: listening on wlan0mon, link-type IEEE802_11_RADIO (802.11 plus radiotap header), capture size 262144 bytes
^C125 packets captured
126 packets received by filter
0 packets dropped by kernel
```

有了保存的数据包捕获后，你可以在类似 Wireshark 的程序中打开它。图 11.8 更详细地显示了先前提到的同一探测请求。在这里，你不仅可以看到 SSID，还可以看到站点请求的某些功能。你还将看到请求的信道和设备的供应商 ID。

