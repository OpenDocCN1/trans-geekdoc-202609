
# 僵尸网络

僵尸网络是受感染处理器的网络，代表了多种恶意程序感染后的结果。僵尸网络是通过多种方法被攻破的机器集合，允许单个 `C&C` 机器或此类控制机器向该感染网络发送命令，命令它们执行选定的任务。通常，受感染机器的所有者/操作者并不知情这一过程正在进行。因此，僵尸网络是类不知情执行恶意计算机命令的分布式计算机集群。此类分布式僵尸网络是实施分布式拒绝服务 (`DDoS`) 攻击的常用方法。此外，黑客还可以将僵尸网络的访问和控制权租给其他黑客组织，让他们执行自己的恶意意图。僵尸网络的强度可以通过几个核心变量来衡量——僵尸网络中的机器数量、总处理能力、连接带宽以及地理分布。这些都是僵尸网络恶意性能成功的关键部分。此外，拥有对潜在机器的访问权限增强了僵尸网络的扩张和再感染能力。

# 病毒与蠕虫

为了感染机器，存在多种媒介或方法来绕过终端用户设置的安全措施。这些类型不是根据代码本身分类的，而是根据感染的方法。在许多情况下，需要多种方法才能高水平感染机器，因此蠕虫和病毒并不互斥。例如，蠕虫不需要宿主程序；它们独立存在，携带某些基础后门组件的负载，并在发现漏洞的机器上自我复制。蠕虫经历四个阶段：

1. 探测 (Probe)
2. 探索 (Explore)

随着计算机和网络速度的提高，蠕虫的传播速度也得到了增强。早期传播最快的蠕虫之一是“红代码蠕虫”（Code Red Worm），但与目前尖端蠕虫传播感染的速度相比，它显得微不足道。第 20 章将讨论 `Stuxnet` 蠕虫与历史蠕虫相比的复杂性和传播性。然而，新涌出的蠕虫数量已开始下降。

增长下降的原因是美国采取了行动，更改了蠕虫所依赖的一些顶层网络设置。当这些设置被更改后，蠕虫想要适应并继续使用历史上有效的技术进行复制变得更加困难。较新的 `Stuxnet` 蠕虫依赖于技术人员通过闪盘携带蠕虫，而不是攻破一系列网络防御软件、扫描器和防御系统。它是通过个人和手动的方式（但在无意中）绕过这些防御措施的。

然而，仍然有蠕虫会攻击互联网上未受保护网站的“低挂果实”，首先感染那些显然未受保护的机器，然后再攻击保护措施稍好的机器。

蠕虫通常包含少量代码，以便在遍历互联网并最终进入企业大型局域网（`LANs`）时保持敏捷。蠕虫文件大小和压缩的一个例子是“Slammer”蠕虫，它在 10 分钟内感染了 7.5 万多台机器。它仅一个通用数据协议（`UDP`）数据包的大小，该协议本质上是无连接的，使其成为蠕虫复制的完美传输协议媒介。该蠕虫的 `UDP` 基础对其增长能力产生了显著影响。

蠕虫是一种极其危险的逻辑武器，可以直接造成物理破坏，就像加拿大逻辑炸弹或伊朗的 `Stuxnet` 蠕虫发生的那样。但它们也可以用于信息间谍、窃取或阻塞收入，以及创建自身形式的拒绝服务。一旦被有效部署，它们可能会在公共互联网上停留一段时间，并偶尔发生跨站感染。为了对抗蠕虫的全球传播，人们设计了“白蠕虫”来感染并清理被利用的机器。然而，这种方法是不可预测的，可能会造成比它们试图缓解的损害更大的伤害。在互联网上以不受控制的方式发布消毒类蠕虫的伦理问题是非常可疑的。以火攻火并非总是解决方案。

# 对恶意软件、病毒、木马和机器人/僵尸网络的更详细检查

恶意软件（Malware）是“malicious software”的缩写。恶意软件被认为是任何对计算机或系统有害的软件或文件。恶意软件包含了病毒、蠕虫、虫、僵尸网络、根内核程序和后门，这些内容很难被发现，一旦被发现，有时难以清除。本节将检查最常见的恶意软件，重点关注各种类型恶意软件的工作原理，以及阻止、检测、避免和删除它们的最佳方法。

## 蠕虫

蠕虫由通过自我传播复制的代码组成，然后通过安排立即执行代码来扩散到各个系统中。执行的蠕虫代码可能包含恶意软件本身，也包含自我传播和扩散技术。它随后利用本地计算机网络在本地进行传播，严重依赖内部安全漏洞来访问目标计算机。然后它寻找访问边缘路由器作为通往公共互联网的网关，从而传播到并感染全球范围内的大量站点。

此外，蠕虫不需要附在现有程序上即可执行感染。蠕虫可以独立行动。当蠕虫在网络中传播时，它往往不会改变其所感染计算机上的系统。蠕虫可以作为可执行恶意软件独立存在，也可以通过将自己放置在现有代码的后端来感染其他软件，并在代码执行时直接影响它，或者覆盖有效代码执行时使用的文件。在从计算机到计算机的传播过程中，蠕虫可能会消耗大量带宽。

蠕虫通常携带少量代码，以便在遍历互联网并最终进入企业大型局域网（`LANs`）时保持敏捷。蠕虫通常携带后门、木马、病毒等任务。蠕虫操作的四个阶段是：探测漏洞、利用这些漏洞进入站点、执行自身的复制以及交付恶意载荷。

## 历史蠕虫攻击示例

### 莫里斯蠕虫（Morris Worm）

莫里斯蠕虫于 1988 年发布，这是通过早期形式在互联网上传播的首批计算机蠕虫之一，它无疑引起了广泛的媒体关注。它是由康奈尔大学的研究生罗伯特·塔潘·莫里斯（Robert Tappan Morris）编写的，根据国家安全局[`NSA`]的说法，该蠕虫的编写并不是为了破坏，而是为了衡量互联网的大小。结果是感染了约 6000 台机器，造成了约 100 万美元的停机损失。

### 红代码 I 和 II 蠕虫（Code Red I and II Worms）

红代码 I 是在 2001 年 7 月 15 日攻击运行微软 `IIS` 的蠕虫。它是莫里斯蠕虫的直接后代，利用了 `IIS` 的缓冲区溢出。它感染了超过 50 万台服务器，造成了 26 亿美元的损失。幸运的是，肯尼·艾希曼（Kenneth D. Eichmann）发现了阻止该蠕虫的方法。红代码 II 是红代码 I 类似的蠕虫，在其后两周发布。与红代码 I 不同，红代码 II 主要关注创建后门而不是攻击。虽然微软已为该漏洞开发了安全补丁，但并非所有人都安装了补丁，导致红代码 II 仍然有效并继续传播。

### Nimda 蠕虫

`Nimda` 蠕虫于 2001 年 9 月 18 日发布。它是一种使用多种传播技术的蠕虫，在初始感染后的 22 分钟内就成为互联网上最广泛的蠕虫。`Nimda` 的名字是“admin”的反写，这表明它试图使用管理员权限。

### SQL Slammer

`SQL Slammer` 是一种导致选定互联网主机出现拒绝服务并减慢互联网流量的蠕虫。它于 2003 年 1 月 25 日传播，在 10 分钟内迅速感染了 7.5 万台计算机。该蠕虫利用了微软的结构化查询语言（`SQL`）服务器，但并未在其感染过程中实际使用 `SQL`。

### Conficker 蠕虫

这种蠕虫也被称为 `Downup`、`Kido` 和 `Downadup`，针对微软 Windows 操作系统，并在管理员密码进行字典攻击以传播自身并随后创建僵尸网络。`Conficker` 于 2008 年 11 月首次被发现，由于采用了多种先进恶意软件技术的组合，因此很难防御。`Conficker` 最终感染了全球 900 万到 1500 万台计算机。`Conficker` 蠕虫利用了多个漏洞：

1. 免受 `Conficker` 蠕虫感染的计算机：具有强密码、安全的共享文件夹、最新的杀毒软件和安全更新。
2. 未受 `Conficker` 蠕虫感染的计算机：具有弱密码且杀毒软件和安全更新过时的网络计算机。
3. 未受 `Conficker` 蠕虫感染的计算机：离网的具有弱密码且杀毒软件和安全更新过时的计算机。
4. 未受 `Conficker` 蠕虫保护的计算机：具有不安全/开放的共享文件夹，以及过时的杀毒软件和安全更新的计算机。

远程攻击者提交的这些针对 Conficker 蠕虫的漏洞如图 7.1 所示。

## 电子邮件蠕虫

这些病毒以附件的形式随电子邮件传递，由于通过向大量联系人列表发送广播邮件，其传播速度可能非常快。

### 爱蠕虫（Love Bug Worm）

也被称为 ILOVEYOU 蠕虫，爱蠕虫通过主题为“ILOVEYOU”的电子邮件传播，带有一个名为“LOVE-LETTER-FOR-YOU.txt.vbs”的附件。当时，`vbs` 文件在 Windows 计算机上默认是隐藏的。打开附件激活了恶意的 Basic 脚本。蠕虫随后损坏了本地机器，并将自身的副本发送到该机器通讯录中的地址。该蠕虫于 2000 年 5 月 3 日发布。总体而言，该蠕虫造成了 550 万至 1000 万美元的损失。

![图 7.1 Conficker 蠕虫的防护与漏洞](img/fig7_2_B.jpg)

图 7.1 Conficker 蠕虫的防护与漏洞。

### MyDoom 蠕虫

该蠕虫于 2004 年 1 月 26 日发布，在 2004 年它是传播最快的电子邮件蠕虫，超过了爱蠕虫。MyDoom 有两个版本：`mydoom.A` 和 `mydoom.B`。`mydoom.A` 有两个载荷：一个创建一个后门，另一个执行拒绝服务。`mydoom.B` 相同的载荷，但此外还阻止了微软网站和其他热门网站。这种拒绝服务攻击针对的是公司。

### Storm 蠕虫与 Storm 僵尸网络

2007 年 1 月 17 日被发现，该蠕虫的载荷包括创建一个影响操作系统的后门木马。它通过主题为“天气灾害”的电子邮件进行自我传播。到 2007 年 1 月 22 日，Storm 蠕虫占全球恶意软件感染的 8%。到 6 月 30 日，它感染了 170 万台计算机。

## 病毒

病毒是一种自我复制的代码，将自身插入其他计算机程序、硬盘和数据文件中。病毒利用附件方法尝试避免检测，以便能够破坏、自我复制并感染其他系统。所有病毒的一个共同点是，它们在没有用户许可的情况下作为现有程序的附件或独立代码安装自身。它们并不一定包含恶意载荷。此外，病毒是机会主义的，这意味着它们的代码会继续寻找让其最终执行的方法。通常，病毒的执行是由用户操作触发的，例如运行感染的应用程序或重启计算机，以便在重启过程中执行被感染的代码。与蠕虫类似，病毒往往具有恶意载荷和传播机制。

### 病毒传播

当病毒执行时，它还会寻找感染其他系统的机会。例如，病毒可能会寻找插入的 USB 闪盘进行感染，这样当闪盘被插入另一个系统时，病毒就可以传播（类似于蠕虫方法）。病毒传播的另一种方式是用户发送带有病毒附件的电子邮件。病毒可以更改电子邮件附件并植入自身；这通常是通过在原始附件开头放置一段微代码来实现的，执行时会绕过原始代码跳转到放置在末尾的病毒载荷代码。为了避免检测，被感染的附件和原始代码被压缩到原始附件代码的大小。这种病毒方法对于感染附件类型（如 Microsoft Word [宏] 和带有 JavaScript 的 PDF）特别有效，而不是简单的 Word 文档和简单的 PDF。病毒也可以自带附件发送电子邮件。

因此，基本过程是：当病毒感染程序或文件时，它首先在程序开头放置一个跳转程序，然后在程序末尾放置病毒载荷代码。执行时，入口代码直接跳过原始代码跳转到末尾附加的病毒代码进行执行。合并后的被感染代码随后被压缩回原始代码的大小以避免检测。入口代码触发代码的解压缩以及跳转到末尾病毒代码的动作。图 7.2 展示了这一过程。

![图 7.2 病毒包裹程序后缩小到原始大小](img/fig7_2_B.jpg)

图 7.2 病毒包裹程序后缩小到原始大小。

### 载荷（Payload）

病毒代码可以执行任何所需的操作。它可以弹出消息、删除文件、损坏硬件、执行键盘记录、加密你的文件并以此索要赎金、安装可能在日后爆炸的逻辑炸弹，并执行任何类型的删除或进一步渗透。

### 检测病毒

病毒每年造成价值数十亿美元的损失，因此催生了价值数十亿美元的杀毒软件（AV）行业。杀毒软件运行基于特征的检测。它扫描与注入病毒代码对应的字节。一旦你发现了病毒，就可以通过安装病毒识别器来保护计算机和其他计算机。杀毒公司根据它们所拥有的特征数量进行竞争。

如果你是一个病毒编写者并发现公司正在发现你的病毒并拦截特定的模式，那么理想的方法是更改病毒或其外表。编写新病毒需要花费大量时间，因此一种解决方案是让病毒在传播时自我更改，每次传播时都产生看起来不同的副本。

#### 多态代码

多态代码是使用多态引擎进行变异的代码，同时保持原始算法完好无损。换句话说，代码每次运行时，结构会发生变化，但功能不变。加密是隐藏代码最常用的方法。需要注意的是，单凭加密并不是多态性。要被视为多态，加密和解密必须在每个代码副本中发生变异，在保持功能相同的同时产生不同的版本。当代码运行时，病毒解密自身以获取载荷然后执行它。图 7.3 和 7.4 展示了被病毒感染的字节示例，以及多态代码在加密和解密后的样子。

![图 7.3 病毒感染与解密过程](img/fig7_3_B.jpg)

图 7.3 病毒感染与解密过程。

![图 7.4 病毒传播的不可识别子病毒](img/fig7_4_B.jpg)

图 7.4 病毒传播的不可识别子病毒。

Polymorphic code was the first technique that became a serious threat to virus scanners. One idea to defend against it is to use narrow signatures that target the decryptor for the polymorphic code. There are a few problems with this countermeasure. For one, there is less code to compare, resulting in more false positives (i.e., code that is fine but is scanned as a threat); also, virus writers can spread the decryptor across the existing code, making it hard to find. A different approach is to analyze code to see if it decrypts. The problem with this strategy is that not all code that has decryption is malicious or unwanted. The other issue is that you have to let the malware decrypt in order to find it, but how long do you allow the malware to run before you stop it? As is the case most of the time, virus writers are two steps ahead of antivirus companies. To combat against these new tactics, virus writers came up with a new solution.

#### Metamorphic Code

Each time the virus propagates, it generates semantically different versions of itself. In other words, the virus rewrites itself completely each time it infects a new component of the system. When it runs, it produces a logically equivalent version of its own code with various interpretations. This child virus will perform the same task as the parent, but the binary representation will be different. Some ways of doing this include renumbering registers, changing the order of conditional code, reordering operations not dependent on one another, replacing one low-level algorithm with another, or removing some do-nothing padding and replacing it with different do-nothing padding. A metamorphic is extremely large and complex code.

When looking for metamorphic code, the virus scanner looks for its behavior rather than its structure. In other words, what is the outcome of this code? Is it malicious? There are two stages in searching for a virus:

1. Antivirus company analyzes new virus to find behavior signature.
2. Antivirus company software on the end system analyzes suspect code to test for signature match.

As usual, virus writers are two steps ahead. A virus writer can delay the analysis. One major weakness of this type of scan is that it has to find the behavior to find the virus, so if the virus writer can stall the program to not function during a scan, it can avoid being detected. Antivirus companies look for these tactics and skip over them. It is the ever ongoing battle in security.
