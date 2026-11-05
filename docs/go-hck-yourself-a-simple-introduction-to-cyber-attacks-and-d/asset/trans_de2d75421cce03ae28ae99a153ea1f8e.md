
```
359878442cf617606802105e2f439dbc Wow!
63191e4ece37523c9fe6bb62a5e64d45 Great
9dddd5ce1b1375bc497feeb871842d4b job
4d1f35512954cb227b25bbd92e15bc7b cracking
e6071c75ea19bef227b49e5e304eb2f1 passwords!
```
清单 7-2：来自 [清单 7-1](#c07.xhtml#listing7-1) 的破解密码

# 8 网络入侵

![](image_fi/book_art/chapterart.png)

入侵一台个人电脑可能只会得到几组用户名、密码和其他数据。但入侵一台 Web 服务器可能会让攻击者获得 *数百万* 的用户名和密码，用来在银行网站、电子邮件服务器等地方进行测试。

2019 年，Quest Diagnostics 通过其 Web 支付页面的漏洞遭到攻击，导致 1200 万患者的记录泄露。2017 年，信用机构 Equifax 未能保护 1.5 亿人的信用信息，包括出生日期、社会安全号码和地址。2018 年对 Marriott 的攻击导致 5 亿旅行者的数据泄露，包括信用卡号码和护照数据。迄今为止最大的数据泄露——2013 年对网络搜索引擎和电子邮件平台 Yahoo! 的攻击——泄露了全部 3 *亿* 用户的账户，包括电子邮件地址和密码。

在本章中，你将看到恶意黑客如何仅凭一个 Web 浏览器和几行代码攻击 Web 应用程序。你还将了解安全专业人员防御 Web 攻击的常见方法，从而保护数百万（也许是数十亿！）人的数据免受网络罪犯的侵害。

## Metasploitable 虚拟机

我们希望安全、合乎道德地练习 Web 入侵，因此我们将在虚拟黑客实验室中设置一台 Web 服务器。Metasploit 的创建者还创建了一个故意存在漏洞的 Web 服务器，名为 Metasploitable，用于培训目的。我们将使用我为你定制的该服务器的一个版本。让我们将其添加到你的虚拟黑客实验室中：
1. 转到 [`https://www.nostarch.com/go-hck-yourself/`](https://www.nostarch.com/go-hck-yourself/) 并点击链接下载 `Metasploitable2-gohack.ova` 文件到你的主机电脑。
2. 双击下载的文件在 VirtualBox 中打开它。导入虚拟设备窗口将打开，如 [图 8-1](#c08.xhtml#figure8-1) 所示。点击 **导入**。
    ![图 8-1：向 VirtualBox 导入 Metasploitable2-gohack.ova 文件](image_fi/502000c08/f08001.png)
    图 8-1：导入 `Metasploitable2-gohack.ova` 文件到 VirtualBox
3. 在 VirtualBox VM 管理器中选择 Metasploitable2 VM 并点击 **设置**。
4. 转到 **网络** 选项卡并确保启用网络适配器框已勾选，并且显示附加到：`NAT Network` 和名称：`PublicNAT`，与我们的其他虚拟机一样。正确的设置显示在 [图 8-2](#c08.xhtml#figure8-2) 中。
    ![图 8-2：确保 Metasploitable VM 已连接到 PublicNAT 网络](image_fi/502000c08/f08002.png)
    图 8-2：确保 Metasploitable VM 已连接到 `PublicNAT` 网络
5. 点击 **确定** 保存这些网络设置。你的新 Metasploitable VM 现在已准备好运行！
6. 在 VirtualBox 管理器中选择 Metasploitable 并点击 **启动**。由于 Metasploitable 是一台 Web 服务器，而不是台式电脑，因此它使用基于文本的界面而不是图形用户界面。如果界面太小而无法阅读，请转到 VM 的菜单栏并选择 **查看**▶**虚拟屏幕 1**▶**缩放至 200%**（或适合你屏幕的其他值）。
7. 输入用户名 `msfadmin` 和密码 `msfadmin`。在 Metasploitable 的终端窗口中输入时密码不会显示，但如果输入正确，提示符将从登录变为如下所示的 shell 提示符：
```
msfadmin@metasploitable:~$
```
8. 输入此命令：
```
msfadmin@metasploitable:~$ ip a
```
Metasploitable 将回复其 IP 地址（在我这里是 `10.0.9.8`）：
```
--snip--
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000 link/ether 08:00:27:11:23:67 brd ff:ff:ff:ff:ff:ff inet 1 10.0.9.8/24 brd 10.0.9.255 scope global eth0 --snip--
```
请注意 IP 地址。你需要它从其他虚拟机浏览到 Metasploitable VM 的 Web 服务器。

## 从浏览器进行 Web 入侵

Web 入侵非常常见，因为它对攻击者来说回报丰厚（记住，对 Web 服务器的成功攻击一次可获得 *数百万* 用户的信息），Web 服务器始终在线并连接到互联网，而且攻击者只需一个 Web 浏览器即可操作。为了演示其工作原理，我们将从 Windows 10 VM 中的 Edge 浏览器入侵 Metasploitable 服务器。

在 VirtualBox 管理器中启动你的 Windows 10 VM。使用凭据 `IEUser` 和 `Passw0rd!` 登录。打开 Edge 浏览器（任务栏上的蓝色 *e* 旋涡图标）并在地址栏中输入你的 Metasploitable VM 的 IP 地址。你将看到 [图 8-3](#c08.xhtml#figure8-3) 所示的 Metasploitable 2 主页。
![图 8-3：从你的 Windows 10 VM 输入你的 Metasploitable VM 的 IP 地址以查看此主页。](image_fi/502000c08/f08003.png)
图 8-3：从你的 Windows 10 VM 输入你的 Metasploitable VM 的 IP 地址以查看此主页。

Metasploitable 2 包含五个存在漏洞的 Web 应用程序，但我们将只关注其中一个：`DVWA`，即 Darn Vulnerable Web App。这个故意存在漏洞的开源 Web 应用程序旨在帮助 Web 开发人员和安全专业人员学习基本攻击，以及如何保护 Web 应用程序免受攻击。`DVWA` 具有不同的漏洞等级，以便用户可以尝试攻击具有不同安全程度的应用程序。我们将安全等级设置为低，以模拟没有额外安全性的 Web 应用程序。
1. 点击 Metasploitable 2 主页上的 **DVWA** 链接。你将看到应用程序的登录屏幕，如 [图 8-4](#c08.xhtml#figure8-4) 所示。
2. 输入 `admin` 作为用户名和 `password` 作为密码以访问 `DVWA`。
    ![图 8-4：带有我们凭据的 DVWA 登录屏幕](image_fi/502000c08/f08004.png)
    图 8-4：`DVWA` 登录屏幕，显示我们的凭据
3. 在左侧点击 **DVWA 安全**。
4. 在脚本安全部分下，将安全等级设置为 **低** 并点击 **提交**，如 [图 8-5](#c08.xhtml#figure8-5) 所示。
    ![图 8-5：设置 DVWA 脚本安全等级为低](image_fi/502000c08/f08005.png)
    图 8-5：设置 `DVWA` 脚本安全等级为低

现在我们准备在 `DVWA` 上尝试两种 Web 攻击：跨站脚本攻击和 SQL 注入攻击。

### 启动跨站脚本攻击

在 *跨站脚本 (XSS) 攻击* 中，黑客通过用于常规文本输入的字段（如登录表单或搜索字段）将恶意代码输入到 Web 页面中。XSS 攻击也称为 *代码注入* 攻击，因为黑客能够输入或 *注入* 自己的代码到 Web 应用程序中。我们将使用两种 Web 语言——JavaScript 和超文本标记语言 (HTML)——向 `DVWA` 注入脚本。

要测试 Web 应用程序是否存在 XSS 漏洞，你只需要一个 JavaScript 命令：
```
alert("You've been hacked!");
```
该命令会弹出一个警告框，显示“你已被入侵！”为了将其注入到 Web 页面中，我们用适当的 HTML 标签 `<script>` 和 `</script>` 包裹 JavaScript 代码，如下所示：
```
<script>alert("You've been hacked!");</script>
```
HTML `<script>` 标签告诉 Web 页面一个 *脚本*（一段简短的代码），通常是 JavaScript，开始了。`</script>` 标签称为闭合标签，它让 Web 页面知道脚本代码已结束。

#### 反射型跨站脚本

