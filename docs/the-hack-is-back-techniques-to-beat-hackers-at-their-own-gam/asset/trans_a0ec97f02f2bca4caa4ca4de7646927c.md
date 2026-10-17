

## 3 Web 应用程序攻击与防御

### 引言

Web 应用程序在互联网上无处不在，在过去十年中，其普及度和功能呈爆炸式增长。任何敏锐的安全观察者都知道，功能永远是安全的天敌——作为黑客，我们可以利用应用程序中发现的这些弱点。我们的主要目标是发现并解释与这些漏洞相关的风险。

许多网站会无意中泄露有害或敏感的文档，使我们能够收集信息，用以生成针对目标的情报。这些信息涵盖范围广泛，从用户电子邮件到编码在客户端 JavaScript 中的 AWS 访问密钥。不要忽视侦察的重要性，因为每一步的枚举是区分优秀黑客与顶尖黑客的关键。侦察是唯一最重要的步骤，必须不断重新审视并持续投入，才能提供最大价值。

许多组织将其 Web 应用程序托管在非军事区（DMZ）或虚拟私有云（VPC）中。这意味着成功攻破一个面向互联网的主机，可能允许攻击者进一步访问受信任环境中的资源。对这些额外系统的访问通常会导致 VPC 的机密性遭到破坏，并有可能对组织内部进行更深层次的访问。

防御 Web 应用程序是一项艰巨的任务，因为 Web 应用程序通常需要可以从互联网访问。这提供了广阔的受攻击面，需要对其进行监控并加固以抵御利用尝试。未能妥善保护这些资产会使组织面临风险，并可能危及机密性、完整性或可用性。

### 方法论

在安全测试期间实施一种方法论，可以确保我们准确识别应用程序中的漏洞。在执行任务期间，很容易忘记应用程序的哪些区域已被访问或未被访问——方法论有助于跟踪关注领域，并保持可重复、一致的测试方法。

针对网站有多种不同类型的方法论，但黄金标准是开放 Web 应用程序安全项目（OWASP）的 Web 安全测试指南（WSTG）。WSTG 汇集了全球数百名研究人员的经验，利用他们针对最常见和最具破坏性攻击的专业知识，这些攻击会危及系统的机密性、完整性和可用性。WSTG 提供了示范性的测试说明和报告，同时为分析人员提供了清晰、简洁的测试说明，为开发人员提供了修复建议。WSTG 可在 https://owasp.org/www-project-web-security-testing-guide/ 获取。

此外，由 Dafydd Stuttard 和 Marcus Pinto 撰写的《Web 应用程序黑客手册：发现与利用安全漏洞》（第 2 版）一书，概述了现代 Web 应用程序的基础及其开发方式。本书将涵盖一些最常见的错误配置以及如何利用它们——如需几乎所有类型 Web 攻击的详细说明，请参考那本书。虽然《Web 应用程序黑客手册》最近一次修订是在 2011 年，但其中涵盖的许多基础概念在今天依然具有重要价值。理解这些关键概念对于学习并将相同步骤应用于最新的库和交互式应用程序至关重要。

```text
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;m4lwhere.org.                    IN      ANY

;; ANSWER SECTION:
m4lwhere.org.            900     IN      NS      ns1.hover.com.
m4lwhere.org.            900     IN      MX      10
mx.hover.com.cust.hostedemail.com.
m4lwhere.org.            900     IN      TXT     "abuseipdb-
verification=ExJNGjL1"
m4lwhere.org.            900     IN      A       34.226.31.104
m4lwhere.org.            900     IN      SOA     ns1.hover.com.
dnsmaster.hover.com. 1577806130 10800 3600 604800 900
m4lwhere.org.            900     IN      NS      ns2.hover.com.

;; Query time: 720 msec
;; SERVER: 8.8.8.8#53(8.8.8.8) (TCP)
;; WHEN: Wed Jul 06 11:52:00 EDT 2022
;; MSG SIZE  rcvd: 238
```

我们看到的是，该网站发布了多条记录。此外，还有一个针对 AbuseIPDB 的 TXT 记录，AbuseIPDB 是一个用于记录互联网上攻击的网站。这是一个看似无害的小信息的示例；然而，我们可能可以利用这些信息。想象一个场景：我们制作一封伪装成 AbuseIPDB 的钓鱼邮件，可以通知目标，他们的蜜罐违反了该平台的新服务条款——这无疑是一封能引起目标好奇心的有趣邮件。始终保持警惕，寻找将信息转化为关于目标的情报的方法。

DNS 记录的输出显示返回了多个不同的 IP 地址。务必牢记，并非所有这些 IP 都可能归目标所有，也可能只是基于 SaaS（软件即服务，可以想想 Office 365 之类的服务）或归第三方所有。直接评估 SaaS 应用提供商的安全性严格来说不在范围内，但允许进行身份验证尝试。在分析环境时，我们必须确保严格遵守范围界定。

从我们作为黑客的角度来看，我们希望尽可能多地枚举主机和主机名。这将与它们解析到的 IP 地址以及开源资源中的潜在信息相关联，以收集更多信息。以下工具用于帮助我们收集尽可能多的潜在主机名和子域，以在后续的侦察链中使用。

### DNS Dumpster

像 DNSDumpster 这样的工具可以快速轻松地查找和分析 DNS 记录。只需将域名放入搜索栏，即可显示有效的 DNS 记录及其解析结果。许多组织并不知道他们的 DNS 记录中有哪些条目，无意中泄露了敏感信息或资产。

那些已从 DNS 中删除或从未打算发布的记录，例如通过证书透明性日志暴露的记录。

```text
$ amass enum -d m4lwhere.org
m4lwhere.org (FQDN) --> ns_record --> ns1.hover.com (FQDN)
m4lwhere.org (FQDN) --> ns_record --> ns2.hover.com (FQDN)
m4lwhere.org (FQDN) --> mx_record --> mx.hover.com.cust.hostedemail.com
(FQDN)
mx.hover.com.cust.hostedemail.com (FQDN) --> a_record --> 216.40.42.4
(IPAddress)
notes.m4lwhere.org (FQDN) --> cname_record --> hosting.gitbook.io (FQDN)
webshell.m4lwhere.org (FQDN) --> a_record --> 164.90.139.235 (IPAddress)
216.40.32.0/20 (Netblock) --> contains --> 216.40.42.4 (IPAddress)
164.90.128.0/18 (Netblock) --> contains --> 164.90.139.235 (IPAddress)
15348 (ASN) --> managed_by --> TUCOWS - Tucows.com Co. (RIROrganization)
15348 (ASN) --> announces --> 216.40.32.0/20 (Netblock)
14061 (ASN) --> managed_by --> DIGITALOCEAN-A-N - DigitalOcean, LLC
(RIROrganization)
14061 (ASN) --> announces --> 164.90.128.0/18 (Netblock)
ns1.hover.com (FQDN) --> a_record --> 216.40.47.26 (IPAddress)
216.40.32.0/20 (Netblock) --> contains --> 216.40.47.26 (IPAddress)
ns2.hover.com (FQDN) --> a_record --> 64.98.148.13 (IPAddress)
64.98.148.0/24 (Netblock) --> contains --> 64.98.148.13 (IPAddress)
32491 (ASN) --> managed_by --> TUCOWS-3 - Tucows.com Co.
(RIROrganization)
32491 (ASN) --> announces --> 64.98.148.0/24 (Netblock)
```

枚举已完成。

运行几分钟后，枚举完成，我们可以看到与该域名关联的一些子域。除此之外，**amass** 工具还提供了关于 ASN（自治系统编号）的大量详细信息，这些信息可以揭示拥有和运营这些 IP 的组织。这可以揭示更多信息，供我们在后续调查中使用。

### Subfinder

**subfinder** 工具是一个基于 Go 的程序，使用被动检测源从 eTLD 枚举有效的子域。该工具速度快，通常能在十秒内完成一组枚举。Subfinder 使用其他数据源（如 VirusTotal 和 Shodan）快速收集已知的子域。该工具可以从 Project Discovery GitHub 的发布版本安装，也可以从源码构建，地址为 https://github.com/projectdiscovery/subfinder。

```text
$ subfinder -d m4lwhere.org

                    __       __
   _________  _____/ /______ / /____  _____
  / ___/ __ \/ ___/ __/ ___// __/ _ \/ ___/
 (__  ) /_/ / /  / /_/ /__/ / /_/  __/ /
/____/\____/_/   \__/\___/_/\__/\___/_/

                         projectdiscovery.io

[INF] Current subfinder version v2.6.0 (outdated)
[INF] Loading provider config from
/home/chris/.config/subfinder/provider-config.yaml
```

