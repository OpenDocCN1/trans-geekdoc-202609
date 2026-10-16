
金融顾问的网络具有内容过滤功能，会监控 incoming emails 的关键词和文件附件。不幸的是，金融公司的网络管理员正在查看内容过滤系统，看看有什么来了。

5. 这位rogue 网络管理员发现了带有机密附件的邮件，保存了附件，并意识到它是受密码保护的。

6. 网络管理员记得一个非常好的密码破解工具——Advanced Archive Password Recovery（[`www.elcomsoft.com/archpr.html`](http://www.elcomsoft.com/archpr.html)），他于是使用它来破解密码。

破解受密码保护的文件就这么简单！现在，这位rogue 网络管理员只需将机密表格转发给他的伙伴或公司的竞争对手即可。

![tip](images/tip.png)如果你在 Advanced Archive Password Recovery 中仔细选择正确的选项，你可以大幅缩短测试时间。例如，如果你知道密码少于五个字符，或者全是小写字母，你可以将破解时间减半。

我建议在使用内容过滤或网络分析工具捕获的文件上进行这些文件密码破解测试。这种方法是确定用户是否遵守政策并使用足够强的密码来保护他们传输的敏感信息的好方法。

#### Countermeasures

对抗弱文件密码保护的最佳防御是要求用户使用更强的文件保护方式，例如 Pretty Good Privacy (PGP) 或 WinZip 内置的 Advanced Encryption Standard (AES) 加密（必要时）。理想情况下，你不想依赖用户决定如何保护敏感信息，但依赖他们比什么都不做要好。强调文件加密机制（如受密码保护的 zip 文件）只有在用户保持密码机密，且 never 将其在不安全的明文（如单独的电子邮件）中传输或存储时才是安全的。

如果你担心不安全的电子邮件传输，可以考虑使用内容过滤系统或数据防泄漏系统，阻止所有在电子邮件服务器上未受保护的出站邮件附件。

### 了解其他破解密码的方法

多年来，我在技术和社会工程方面发现了其他破解（或捕获）密码的方法。

#### 键盘记录

一种最佳的捕获密码的技术是远程 *键盘记录*——使用软件或硬件记录键盘输入。

![warning](images/warning.png)请小心使用键盘记录。即使出于良好意图，如果操作不当，监控员工也会带来各种法律问题。与你的法律顾问讨论你将要做的事情，请求她的指导，并获得上级管理层的批准。

#### LOGGING TOOLS

使用键盘记录工具，你可以检查受监控的应用程序的日志，看看人们使用的密码：

* 键盘记录应用程序可以安装在被监控的计算机上。我推荐 Spector 360（SpectorSoft）[`www.spector360.com`](http://www.spector360.com)。网络上有大量这类工具。

* 硬件键盘记录工具，如 KeyGhost（[`www.keyghost.com`](http://www.keyghost.com)），插在键盘和计算机之间或直接替代键盘。

![warning](images/warning.png)在共享计算机上安装键盘记录工具可以捕获所有登录该计算机的用户的密码。

![warning](images/warning.png)黑客安装键盘记录软件的潜在风险是另一个确保用户不下载和安装随意的分享软件或打开未请求邮件附件的原因。可以通过在 Windows 本地或组策略中设置适当的用户权限来锁定工作站，或者使用商业锁定程序，如 Fortres 101（[`www.fortresgrand.com`](http://www.fortresgrand.com)）或 Deep Freeze Enterprise（[`www.faronics.com/products/deep-freeze/enterprise`](http://www.faronics.com/products/deep-freeze/enterprise)），适用于 Windows、Linux 和 macOS X。另一种仍属于此类技术的是 Carbon Black 的“正向安全”白名单应用——Cb Protection（[`https://www.carbonblack.com/products/cb-protection`](https://www.carbonblack.com/products/cb-protection)），它允许你配置在任何系统上可以运行的可执行文件。它用于对抗高级恶意软件，但也可以用于此类情况。

#### 弱密码存储

许多老旧和独立应用程序——如电子邮件、�ialk 网络连接和会计软件——会本地存储密码，这使它们容易受到密码破解的攻击。通过基本的文本搜索，我发现这些机器的本地硬盘上存储了明文密码。你可以使用 FileLocator Pro（[`https://www.mythicsoft.com`](https://www.mythicsoft.com)）进一步自动化此过程。我在第 16 章（[Chapter 16](#c16.xhtml)）中介绍了文件和相关存储的弱点。

#### SEARCHING

你可以使用你喜欢的文本搜索工具——如 Windows 搜索功能、`findstr` 或 `grep`——在计算机的驱动器上搜索 *password* 或 *passwd*。你可能会惊讶于系统上存储的内容。有些程序甚至会将密码写入磁盘或保留在内存中。

![remember](images/remember.png)弱密码存储是黑客的梦想。如果能防止它就更好。但我并不是说你应该马上跑去使用云端密码管理器——正如我们所看到的，那些系统也会被黑客入侵！

#### COUNTERMEASURES

消除弱密码存储的唯一可靠方法是只使用能够安全存储密码的应用程序。虽然这在实际操作中可能不切实际，但它是确保密码安全的唯一保证。另一种做法是指示用户在被询问时不要存储密码。

在升级应用程序之前，联系软件供应商查看它如何管理密码，或寻找第三方解决方案。

#### 网络分析仪

网络分析仪会嗅探网络中传输的数据包，这正是攻击者在获得控制某台计算机、接入无线网络或获得物理网络访问权限后会做的事。如果他们获得物理访问，可以在墙上寻找网络插口并直接插入。

#### TESTING

[Figure 8-4](#c08.xhtml#c08-fig-0004) 展示了网络分析仪视角下清晰可见的密码。Cain & Abel（[`www.oxid.it/cain.html`](http://www.oxid.it/cain.html)）可以在几小时内窃取数千个网络中的密码。左侧窗格显示，这些明文密码弱点可适用于 FTP、Web、Telnet 等多种协议。（实际的用户名和密码已模糊处理，以保护隐私。）

![ FIGURE 8-4:  使用 Cain & Abel 捕获网络中传输的密码。](images/9781119485476-fg0804.png)

[FIGURE 8-4:](#c08.xhtml#rc08-fig-0004) 使用 Cain & Abel 捕获网络中传输的密码。

![remember](images/remember.png)如果流量没有通过某种加密链路（如虚拟私网、Secure Shell 或 Secure Sockets Layer）进行隧道化，则容易受到攻击。

