
通常，当您管理云环境的访问权限时，您会前往云服务提供商的控制台，找到名为身份和访问管理（IAM）的模块，或其最接近的变体。在 Google Compute 中，它称为 IAM，您可以在 Figure 15.17 中看到。在 Microsoft Azure 中，您会前往“所有服务”，然后选择“标识”。AWS 有一个名为“身份和访问管理”的功能。从这些地方的任何位置，您都可以创建用户并分配权限。一旦创建了用户，他们可以被分配到您在云环境中创建的资源中。与其他任何身份解决方案一样，请记住角色可能会跨越不同的系统。如果您需要让用户成为某个系统的管理员但不是其他系统，您可能需要创建不同的角色以满足这一需求，而不是仅仅将用户设为管理员。始终要仔细分配给个人用户的权限。

![FIGURE 15.17 Google IAM](img/c15f017.png)

**FIGURE 15.17** Google IAM

在访问控制方面，需要考虑的一个问题是您可以创建密码学钥匙来访问单个资源。这在 AWS 计算实例的情况下是肯定的。如果您创建密钥但未能通过在密钥上使用强密码并不共享密钥和密码来控制对密钥的访问，您就有可能暴露对该密钥所使用的系统的访问权限。如果同一密钥用于多个系统，且该密钥泄露，那么使用该密钥的所有系统都将对拥有密钥和用于解锁密钥的密码的人开放。

保护云资源的一个方法是进行审计和日志记录。您应该记录对资源的访问日志并监控这些访问。攻击者会使用各种技术获取凭据访问资源，这可能包括尝试已知的凭据。如果没有记录访问（包括登录尝试的来源），您将无法知道攻击者是否从不应允许的地理位置登录。与本地系统不同，云资源并不总是有相同的访问限制；在本地系统中，您可能需要实体访问设施才能连接到系统。如果您通过 Internet 连接到云资源，攻击者同样可以以相同的方式进行连接。

### 数据泄露

您在云提供商或任何存储位置维护的最重要资源是数据。最终，您可能不在乎攻击者获得无数据访问权限的独立系统。如果他们利用您的系统发起攻击，您可能会为网络和计算资源支付费用。如果及时发现，则没有持久损害。数据的情况不同。数据可能包含 personally identifiable information（个人可识别信息），如果数据被盗，可能需要向公众通报数据泄露，并且相关数据主体需要投入大量时间和精力进行恢复。在知识产权的情况下，您可能会面临竞争在市场中长期影响的风险。

数据泄露的曝光方式有多种。第一种是通过应用程序暴露，即攻击者 compromise 了应用程序并获得底层数据的访问权限。第二种是数据以非结构化方式存储。例如，在 AWS 中，您可能将数据存储在 S3 桶中。默认情况下，AWS 桶的所有公共访问都被关闭。Figure 15.18 展示了关闭保护后的 S3 桶配置。这要求不仅要关闭设置，还要勾选一个确认框，表明您了解使 S3 桶公开的问题。

这可能正是您想要的。在某些情况下，您希望用户能够访问您在云提供商处存储的数据。然而，问题在于，可能有人不小心在公共云存储实例中存储敏感信息。一旦数据存入云存储，如果允许公共访问，任何人都可以访问。不要假设只要 URL 不为外部所知，数据就无法被访问。隐藏实例且不发布它并不等同于保护它。

您可以通过定期评估资源的权限，确保已正确配置访问控制来帮助防止数据泄露。此外，使用数据防泄漏（DLP）功能，无论是由云提供商还是第三方提供，都可以帮助防止 inadvertent 数据披露。

![FIGURE 15.18 S3 bucket configuration](img/c15f018.png)

**FIGURE 15.18** S3 bucket configuration

### Web 应用程序 compromise

Web 应用程序基本上是数据的程式化接口。虽然可以构建没有可访问数据的 Web 应用，但这很难想象。除非您打算让服务器或客户端处理或存储数据，否则无需程式化访问。问题在于 Web 应用有很多方式可以被破坏。开放式应用安全项目（OWASP）跟踪 Web 应用程序的 Top 10 漏洞列表。其中许多与应用程序代码中对数据的处理不当有关。用户可以向应用程序发送任何数据，如果应用程序未正确处理，应用程序可能会被 compromise，从而导致对后端数据的过度访问。

另一个可能被 compromise 的领域是配置错误。例如，如前所述，启用公共访问 S3 桶会导致配置错误。弱网络限制也是另一种配置错误，可能允许未经授权的人员访问。不了解云提供商提供的控制措施的人可能使用错误的控制措施来实现网络访问限制。虽然云提供商的控制措施与本地保护措施相同，但具体实现可能因环境而异。

配置错误并非 Web 应用被 compromise 的唯一方式。攻击者的目标也很重要。他们不一定寻找系统的 shell 访问，尽管这可能是一种幻想。最终，shell 访问是手段，目的是数据访问。许多现代攻击者属于高级持续性威胁（APT）类别，他们要么寻找货币化受损系统或企业的方法，要么寻找可以在市场中更成功竞争的知识产权。如果他们能够通过经典的 SQL 注入攻击获取数据，那就是他们首选的方法。通常，花费最少的努力获得最大的结果是首选的策略。

在防止 Web 应用程序 compromise 时，应遵循几条建议。首先，应在设计阶段就将安全性纳入考虑。其次，使用经过漏洞评估的组件，并始终保持最新的修复。Web 应用程序应由第三方进行严格测试，即使该第三方是公司内部的安全测试专家。此时的“第三方”指的是除开发团队或质量保证团队之外的任何人。此外，Web 应用程序应通过使用 Web 应用防火墙（WAF）来进行保护。

传统的暴力破解尝试大多已成过去。如果有暴力破解尝试发生，它们是在离线进行的。包含哈希密码的凭据泄漏可以离线破解，而不会向企业透露攻击者正在尝试入侵。此外，凭据通常在网络上广泛可得，包括通过所谓的暗网，它是基于 Tor（洋葱路由器）的互联网叠加层，用于访问这些信息所在的系统。一旦你拥有一组凭据，就可以尝试全部组合。这可能不会引起他人注意，因为许多企业并不关注对不同用户账户的连续失败尝试。它们更关注同一用户账户的多次失败。Credential stuffing（凭据填充）技术不会重复使用相同的用户名。凭据泄漏更可能只包含单个用户名的实例，但涉及大量不同的用户名。2019 年的一个凭据泄漏包含了超过两十亿条用户名和密码组合。

另一种获取用户名和密码组合的方式是直接询问。网络钓鱼攻击非常常见，这主要是因为它们成功率高，尽管大多数钓鱼邮件会被邮件提供商（包括图 15.19 所示的邮件服务）过滤到垃圾邮件夹中。如果邮件内容足够可信，用户可能会被骗去访问网站，这些网站也可能非常逼真。特别是在工作日繁忙时，用户可能注意力不够，容易被诱导透露凭据。他们习惯于接收接二连三的请求，看到再多的请求时，也会直接响应。

![FIGURE 15.19 Phishing message](img/c15f019.png)

**FIGURE 15.19** Phishing message

防范钓鱼信息的常见做法是让用户接受定期的安全意识培训。与其采取对抗性策略，建立与用户的合作关系同样有效。检测钓鱼信息很困难。如果现有的邮件防护措施不足以捕获所有信息，则不应怪责用户未能识别恶意信息。攻击者会花费大量时间让信息看起来极其真实。

其他防范钓鱼攻击的方法（目标可能是获取凭据，进而访问云端服务）是实施邮件防护措施。可以采用基于威胁情报的解决方案，这些方案能够检测即使是未知的攻击，并将恶意信息重定向到用户收件箱之外的位置。

虽然不完美且依赖于良好实施，多因素认证（MFA）仍是对凭据基础攻击的必要缓解措施。若使用短信作为第二因素或使用推送消息作为第二因素，则 MFA 可能被滥用。推送消息是指认证应用通过手机通知向用户发送请求。用户只需点击批准即可完成验证，无需其他操作。当攻击者不断尝试认证并发送请求给用户，导致用户疲惫并直接批准时，推送消息会被滥用。更好的做法是要求使用由认证应用或设备生成的一次性密码（OTP）。此外，硬件设备也可以用于实现 MFA。

### Insider Threat

有趣的是，许多企业将此视为最大挑战，尽管多年来的证据表明，应对和从外部实体的攻击中恢复的成本已给组织带来数十亿美元的损失，即便仅在过去几年。然而，内部威胁是真实存在的问题，且在部分组织中尤为突出。内部威胁是指拥有访问权限的员工，可能会窃取或损坏业务资源。通常人们认为这是恶意行为，但内部人员更可能因错误导致损害或丢失，而不是实施恶意行为。

任何拥有云提供商环境访问权限的员工都可能造成损害或丢失。应始终有控制措施防止损害。正如所述，将用户的访问权限限制在其完成工作所必需的范围内是良好实践。此外，日志记录和监控访问及操作有助于发现损害和丢失。这并不意味着你要怀疑所有员工。它意味着有时会发生坏事，有时是错误，有时是有意为之的破坏。能够观察行为有助于在行为进行时识别，从而及时响应并采取适当措施。

### Internet of Things

数十年来，计算设备一直在不断变小。我们从占据整间房的设备开始，发展到可以放在桌面上、放在膝盖上、甚至放在手掌里的电脑，今天你可能甚至在家里看不见的地方散布着许多计算设备。例如，图 15.20 展示了一台内置小型计算设备的灯光开关，使用户可以通过应用或语音（在安装了合适的控制器后）进行控制。这些设备并非通用计算设备，无法运行任意程序，通常具备有限的存储和计算能力，因为它们并不需要承担繁重任务。灯光开关只需决定是否允许电流通过，或阻止电流通过。所有这些设备的集合被称为物联网（IoT）。

当前，智能家居推动了大量具备计算智能和网络连接的设备使用。你可能拥有灯光开关、家电、恒温器、医疗设备或其他需要一定智能和网络能力的设备。也可能有仅负责在家庭网络中传输信息的传感器，或控制家中设备（如灯光开关）的设备。这些设备具备网络能力，意味着你可以与它们交互，它们在你的网络中可被检测到，有时甚至能被广泛看到。

首先，有几个网站可用于搜索 IoT 设备。你可以使用 Censys.io，它允许你根据长长的特征列表在其数据库中搜索设备。另一个是 Shodan，网址为 `shodan.io`。Shodan 维护一个 IoT 设备的数据库，拥有账户的用户可以搜索这些设备。图 15.21 展示了在 Shodan 上可以执行的一些快速搜索。选择其中一个搜索会显示设备的详细信息。例如，搜索“Cams”会返回通过这些设备发出的 HTTP 请求的头部信息。每个响应都是一组 HTTP 头部，包含请求的日期时间以及服务器信息，进而揭示使用的软件。

![FIGURE 15.20 Internet‑enabled light switch](img/c15f020.png)

**FIGURE 15.20** Internet‑enabled light switch

- [费曼学习法](https://wiki.example.org/feynmans_learning_method)的灵感源于诺贝尔物理奖获得者`理查德·费曼`。

1. 运用费曼技巧，你只需花上`20 min`就能深入理解知识点，而且记忆深刻，`难以遗忘`。

```
if (condVar > someVal) {console.log("xxx")}
```

Typically, you wouldn't spend a lot of time on these sites, since finding all of the web‑cams in the world, or at least the world according to Shodan, won't be a task you would perform as an ethical hacker. You would be more apt to identify IoT devices through something like a `network scan`. Using `nmap`, we can turn up all the devices on a network, including IoT devices. One example, shown next, is how that light switch shown earlier appears on the network. You can see `nmap` isn't sure what to make of the operating system. According to `nmap`, this is a smartphone of some sort. However, the real clue isn't what `nmap` believes. It's in the media access control (MAC) address. According to the organizationally unique identifier (OUI), the network interface was manufactured by a company called iDevices.

![FIGURE 15.21 Shodan website](img/c15f021.png)

**FIGURE 15.21** Shodan website

**Nmap Results**

```
Nmap scan report for 192.168.4.25
Host is up (0.026s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
80/tcp open  http
MAC Address: D4:81:CA:5B:8E:CA (iDevices)
Device type: phone|VoIP phone|media device|general purpose
Running (JUST GUESSING): Sony Ericsson Symbian OS 9.X (86%), Palmmicro embedded (85%), Acer embedded (85%), Microsoft Windows XP (85%)
OS CPE: cpe:/h:sonyericsson:p1i cpe:/o:sonyericsson:symbian_os:9.1 cpe:/o:microsoft:windows_xp::sp3
Aggressive OS guesses: Sony Ericsson P1i mobile phone (Symbian OS 9.1) (86%), Palmmicro AR1688 VoIP module (85%), Acer S5200 projector (85%), Microsoft Windows XP SP3 (85%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop
```

The company iDevices doesn't make smartphones. It makes smart home devices. One of these (and the only type of iDevices device on this network) is a smart light switch. Where tools are uncertain, as in this case, sometimes you have to resort to another way to obtain the information. What we can see, in addition to the type of device this is, by way of the manufacturer, is there is a port that's open. There appears to be a web server running in this device, which is common for embedded devices (small, single‑purpose computing devices where the “program” running is embedded into the firmware). We can do a little probing. The following example shows a connection to this device over port 80 using `netcat` to manage the connection:

```
nc 192.168.4.25 80
GET / HTTP/1.1
Host: 192.168.4.25
 
HTTP/1.1 404 Not Found
Content-Length: 0
```
