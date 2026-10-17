
本章前面我们讨论了作为账户接管一部分的联合身份认证。联合身份认证采用一个身份提供商，并将其用作环境的认证源。这可能是像 Okta（[`www.okta.com/identity-101/what-is-federated-identity`](https://www.okta.com/identity-101/what-is-federated-identity)）这样的服务，它本身充当认证源，也可能集成到 AWS（[`aws.amazon.com/identity/federation`](https://aws.amazon.com/identity/federation)）、Azure（[`docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-fed`](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-fed)）或 Google Cloud（[`cloud.google.com/architecture/identity/federating-gcp-with-active-directory-introduction`](https://cloud.google.com/architecture/identity/federating-gcp-with-active-directory-introduction)）中。

联合身份认证使用 OAuth（[`oauth.net/2/`](https://oauth.net/2/)）、SAML（[`auth0.com/blog/how-saml-authentication-works/`](https://auth0.com/blog/how-saml-authentication-works/)）或 OpenID（[`openid.net/`](https://openid.net/)）等技术，充当可以在环境外部执行认证的身份提供商，然后返回关于已认证方的数据，以便平台本身可以处理授权。这通常通过共享密钥（如证书）来保护。如果这些密钥泄露，则联合身份认证的安全性也就随之受损（[`www.zdnet.com/article/nsa-warns-of-federated-login-abuse-for-local-to-cloud-attacks/`](https://www.zdnet.com/article/nsa-warns-of-federated-login-abuse-for-local-to-cloud-attacks/)）。因此，保护这些密钥是环境安全的基础。

某些服务允许不止一个联合认证源或多个密钥。审核密钥、联合源或外部认证源的变更将有助于保护环境。作为测试人员，这是你应该寻找但需谨慎处理的内容。修改这些设置意味着要保护你添加的密钥，并确保在完成后进行清理，以免因测试而降低目标环境的安全性。

### 对象存储

对象存储是被滥用最多的云组件之一。频繁发生的存储泄露（如 Amazon S3）通常是由于配置错误。在一起案例中，由于糟糕的 S3 卫生习惯，数百 GB 的市政数据被意外泄露（[`www.securitymagazine.com/articles/95704-us-municipalities-suffer-data-breach-due-to-misconfigured-amazon-s3-buckets`](https://www.securitymagazine.com/articles/95704-us-municipalities-suffer-data-breach-due-to-misconfigured-amazon-s3-buckets)）。作为渗透测试人员，我们通过两种方式之一来处理对象存储。我们可以从未认证的角度识别可访问的存储，也可以从已认证的视角识别可访问的存储。像 CloudCustodian（[`cloudcustodian.io/`](https://cloudcustodian.io/)）这样的工具可用于云治理和发现。

![Images](img/exam.jpg)

**考试提示** CloudCustodian 是一个开源工具，它使用 YAML 策略文件在多个云环境（包括 Azure、AWS 和 Google Cloud Platform）中审核和强制执行云配置策略。

#### CloudCustodian

CloudCustodian 接收 YAML 格式的策略，并针对账户运行它们，以识别错误配置、修复它们，并报告潜在的策略违规。策略包含名称、资源和一系列适用的过滤器。CloudCustodian 为 AWS、Azure 和 Google Cloud 提供了示例配置。这些配置范围涵盖从账户检查和修复到 VPC 检查（[`cloudcustodian.io/docs/aws/examples/index.html`](https://cloudcustodian.io/docs/aws/examples/index.html)）。假设我们要识别未阻止公共访问的存储桶。此示例策略将检查此项。

![Images](img/f0206-01.jpg)

要运行此策略，我们可以使用 `run` 命令和 `--dry-run` 选项来运行 `custodian` 二进制文件。`--dry-run` 选项确保不会发生任何更改。我们还使用 `-s` 标志来提供输出目录。

![Images](img/f0206-02.jpg)

在这种情况下，我们看到两个资源。查看输出目录，我们将看到每个策略都有基于名称的自己的目录，已识别的资源位于 `resources.json` 文件中。

![Images](img/f0206-03.jpg)

我们可以看到 test-web 存储桶有一个公共访问阻止设置，但该设置并未阻止公共访问。该策略对 `*` 允许了 `PublicReadGetObject` 以获取对象。这意味着任何人都可以通过 Web 从该存储桶获取文件。让我们用 `curl` 验证一下。

![Images](img/f0206-04.jpg)

我们看到可以使用为启用 Web 的存储桶命名方案（`<bucket>.s3.amazonaws.com`）来访问该存储桶。如果您知道组织名称，也可能能够使用以下格式：`s3-<region>.amazonaws.com/<Org Name>`。我们还可以使用 CloudScout 对 S3 存储桶的输出进行验证。当我们点击 derp-web 存储桶时，我们会看到与 **图 6-3** 中 JSON 响应相同的信息。

![Images](img/F06-03.jpg)

**图 6-3** S3 存储桶的 CloudScout 结果

如果我们没有访问权限怎么办？有许多工具旨在猜测 S3 存储桶名称。您可以在 Pacu 中使用此命令：

```
Pacu > run s3__bucket_finder -d <doamain>
```

Pacu 的 `s3__bucket_finder` 模块根据域名、子域名、给定的词缀等猜测存储桶名称。还有其他工具基于字典和单词列表操作来猜测存储桶。其中一个工具是 CloudBrute（[`github.com/0xsha/CloudBrute`](https://github.com/0xsha/CloudBrute)）。CloudBrute 支持 AWS、Azure、Google Cloud、Digital Ocean、Vultr、阿里云和 Linode 提供商。它将尝试根据键（由 `-k` 指定）、单词列表（由 `-w` 指定）以及域名或其他关键字来猜测存储桶。让我们尝试搜索 derp.pro。在 **图 6-4** 中，您可以看到输出。

![Images](img/F06-04.jpg)

**图 6-4** `./CloudBrute -d derp.pro -k derp -c amazon -w data/storage_small.txt` 的 CloudBrute 结果

Derp-web 没有显示出来。此目录不可公开列出。只有在您显式请求页面（例如使用 `index.html`）时才会显示。存储具有访问列表和公共设置，这些通常构成了组合访问规则。如果您不熟悉它们，这些规则可能会很复杂。这就是为什么发生了如此多的云存储数据泄露（[`github.com/nagwww/s3-leaks`](https://github.com/nagwww/s3-leaks)）。

![Images](img/exam.jpg)

**考试提示** CloudBrute 是一个多云（Azure、Amazon、Google 等）工具，它利用单词列表、域名和常见的云命名约定来帮助识别目标基础设施、文件和应用程序。

### 容器化技术

我们将在 **第 7 章** 中进一步讨论容器。现在，请理解容器允许您获取一个镜像并在任何地方运行它。许多不同的技术让我们能够运行容器，例如 `containerd`、Windows 容器、`Docker`、`Kubernetes` 以及这些技术的云实现。大多数渗透测试人员都需要了解如何识别、访问和逃逸容器化系统。您如何利用容器资源来进一步访问其他系统或宿主系统，将受到您是否能够从容器内部映射系统上的本地磁盘的影响。例如，如果映射的目录包含 Docker 套接字文件，您可能能够使用该文件向容器发出命令。其他的 Docker 逃逸方法可以在 [`blog.nody.cc/posts/container-breakouts-part1/`](https://blog.nody.cc/posts/container-breakouts-part1/) 找到。

`Docker` 通常仅用于在特定主机上运行少量容器。`Docker Swarm` 用于在拥有少量系统和少量服务的环境中进行编排。`Kubernetes` 更适合需要跨许多节点进行编排的系统，并提供企业级的可扩展性和弹性。`Docker` 和 `Kubernetes` 共享一些常见的攻击模式（例如内核漏洞利用：[`snyk.io/blog/kernel-privilege-escalation/`](https://snyk.io/blog/kernel-privilege-escalation/)），但 `Kubernetes` 基于 kubelet、用户、Pod、Secret 等工作，这些具有独特的攻击向量。Microsoft 已创建了一份潜在的攻击、提权、发现和规避技术列表，作为其 Kubernetes 威胁矩阵的一部分（[`www.microsoft.com/security/blog/2021/03/23/secure-containerized-environments-with-updated-threat-matrix-for-kubernetes/`](https://www.microsoft.com/security/blog/2021/03/23/secure-containerized-environments-with-updated-threat-matrix-for-kubernetes/)）。Inguardians 的 Jay Beale 在他们的博客上撰写了一个演练，介绍了一些可用于 `Kubernetes` 攻击的技术：[`www.inguardians.com/attacking-and-defending-kubernetes-bust-a-kube-episode-1/blog/`](https://www.inguardians.com/attacking-and-defending-kubernetes-bust-a-kube-episode-1/blog/)

### 以云为中心的攻击

某些攻击（如 DoS）在应用于云时具有专门的背景。其他攻击则关注仅在云环境中可用的服务的细微差别，例如针对云资源的恶意软件注入和侧信道攻击。攻击者可能利用这些攻击在云环境中获得进一步访问权限，或将云环境作为攻击工具，以针对其他面向互联网的目标实现目标。

#### 拒绝服务

在 **第 3 章** 中，我们在压力测试应用程序的背景下讨论了 DoS 攻击。我们讨论了不同类型的攻击以及攻击者使用它们的原因。这范围从增加成本、中断服务质量，到给拥有资源或试图使用资源的组织造成不便。动机可能从金钱（勒索）、政治或道德活动、报复，到将其用于掩盖其他攻击。作为渗透测试人员，您可能还会被要求评估云环境是否存在弱点，允许攻击者利用云资源进行 DoS 攻击。

##### 容量型 DDoS

容量型攻击试图耗尽目标的带宽或连接。云资源是放大攻击或掩盖攻击真实来源的有吸引力的方式。反射攻击的放大倍数是发送给中间件的流量与发送给受害者的流量之比。例如，`Memcached` 用于存储可在应用程序之间共享的数据，如 Web 会话数据。一个针对 `Memcached` 的小请求可能会变成巨大的返回流量。但由于互联网上的 `Memcached` 系统比 NTP 或 SNMP 少，它可能作为目标吸引力较小。UDP 反射攻击可以使用 Apple 远程管理服务、Web 服务动态发现 (WS-DD)、受限应用协议 (CoAP)、LDAP 和 `Memcached` 等协议，所有这些都可能由云资源暴露。

##### 直击源站攻击

云基础分布式拒绝服务（DDoS）防护的优势之一在于云前端能够大规模扩展以应对攻击。只有必须传递给后端系统的流量才会落在源服务器上。采用这种缓解措施时，理想情况下应配置防火墙规则，防止云提供商以外的任何人直接与源服务器通信。如果这些规则未能妥善保护源服务器，攻击者可能会发出请求，泄露受保护系统的后端 IP 地址（[`cdn.net/how-to-protect-your-cdn-origin-server/`](https://cdn.net/how-to-protect-your-cdn-origin-server/)）。

如果真实 IP 被泄露，攻击者可绕过防护直接攻击 IP 地址。这就是直接源站攻击。内容分发网络（CDN）旨在承担大部分负载。因此，海量流量可由相对较少的系统处理。直接攻击这些少数系统可迅速使目标过载。CDN 中的缓存内容仍可服务，但动态内容无法生成和分发。这包括登录、搜索等功能（[`www.red-button.net/ddos-glossary/direct-to-origin-ddos-attacks/`](https://www.red-button.net/ddos-glossary/direct-to-origin-ddos-attacks/)）。

我们在第 2 章中讨论过如何对此进行侦察，但让我们再回顾一下。通过名称查找网站以获取其 IP。在 ARIN 中查找 IP 并查看其归属。如果是云提供商，则可能是云前端站点。您也可以向虚假的虚拟主机地址发起请求——例如“doesnotexist.derp.pro”——并查看是否收到来自不同 IP 范围的响应。您甚至可以查找目标组织拥有的 IP 范围并请求域名。例如，在 Burp 中向 IP 地址目标发送此请求（`https://<company owned IP address from ARIN>`）：

![Images](img/f0210-01.jpg)

如果响应作为有效的 Web 响应返回基础页面，则表明您已发起直接请求。您还可以检查 SSL 证书以识别可能正在使用的虚拟主机 IP 地址。一些工具可帮助自动化此过程，但可能不会出现在考试中：

*   [`github.com/jobertabma/virtual-host-discovery`](https://github.com/jobertabma/virtual-host-discovery)
*   [`github.com/gwen001/vhost-brute`](https://github.com/gwen001/vhost-brute)
*   [`github.com/m0rtem/CloudFail`](https://github.com/m0rtem/CloudFail)

![Images](img/tip.jpg)

**TIP** 有关此类攻击研究的进一步阅读，请查看 ZDnet 的文章（[`www.zdnet.com/article/fbi-warns-of-new-ddos-attack-vectors-coap-ws-dd-arms-and-jenkins/`](https://www.zdnet.com/article/fbi-warns-of-new-ddos-attack-vectors-coap-ws-dd-arms-and-jenkins/)）和 Team Cymru 的博客（[`team-cymru.com/blog/2020/05/15/dissecting-ddos-attacks/`](https://team-cymru.com/blog/2020/05/15/dissecting-ddos-attacks/)）。

#### 云恶意软件注入

在第 5 章中，我们讨论了应用注入攻击，以及攻击者如何利用 XSS 和 SQLi 攻击将恶意内容注入合法应用程序提供的服务中。这些攻击在云环境中同样有效。然而，云中的恶意软件注入存在额外的攻击向量。在云中，攻击者可能利用通过其他攻击获得的访问权限，将恶意内容注入服务的镜像或云服务中。

例如，如果攻击者能够操纵合法云托管服务或机器镜像的副本，并说服云提供商提供该副本，他们便可获得对云环境的额外访问权限，甚至拦截发往合法服务的服务请求。在 SaaS 或 PaaS 模型中，这意味着使用某项服务。在 IaaS 模型中，这意味着影响服务的镜像。在这两种情况下，都涉及对云账户的某种程度的特权访问。但这可能是其他攻击的结果。让我们看一个合理的例子。
