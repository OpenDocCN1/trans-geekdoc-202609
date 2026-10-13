

![Figure 11.11 nmapAutomator Performing Full Scan of Asset.](images/c11f011.png)

[**Figure 11.11**](#c11.xhtml#rc11-fig-0011) nmapAutomator 对资产执行全面扫描。

![Figure 11.12 nmapAutomator Results.](images/c11f012.png)

[**Figure 11.12**](#c11.xhtml#rc11-fig-0012) nmapAutomator 结果。

### 11.4.2 Sn1per

由 1N3 创建，Sn1per 是另一款自动化漏洞扫描工具。Sn1per 的免费版本可从 GitHub 下载。不过，也有专业版可用，它支持图形用户界面（GUI）视图和工作区管理。免费版本可以高效利用。按照说明下载并配置工具后，项目经理可以获取一个域名的 URL 并开始对其进行测试。Sn1per 拥有许多模式。不过，一个好的起点是使用 "normal"（普通）模式。

下载后，使用命令即可轻松上手：`sniper -t https://example.com`。

该工具将尝试针对该域名利用各种枚举工具，用于 Web 应用程序和网络渗透测试。请注意：如果未指定，该工具可能会尝试各种利用，这可能会对生产环境造成损害；为此做好准备至关重要。（参见 [Figure 11.13](#c11.xhtml#c11-fig-0013) 和 [11.14](#c11.xhtml#c11-fig-0014)。）

![Figure 11.13 Sn1per Running Metasploit Modules.](images/c11f013.png)

[**Figure 11.13**](#c11.xhtml#rc11-fig-0013) Sn1per 运行 Metasploit 模块。

![Figure 11.14 Sn1per Running Nmap Scripts.](images/c11f014.png)

[**Figure 11.14**](#c11.xhtml#rc11-fig-0014) Sn1per 运行 Nmap 脚本。

### 11.4.3 Owasp Zap

在免费的 DAST（动态应用程序安全测试）工具套件中有 OWASP ZAP。该工具专注于 Web 应用程序测试方面，并将针对各种漏洞评估 URL 或参数。ZAP 随大多数渗透测试工具包预装，包括 Kali Linux 和 Parrot。或者，Burp Suite 专业版也有一个不错的 DAST 扫描器。然而，并非每个项目经理都有资金购买许可证。

扫描相当简单：工具加载后，项目经理可以在 "URL to Attack"（要攻击的 URL）字段中输入一个 URL。此时，只需按下 "Attack"（攻击）即可。然而，在更现实的场景中，或根据企业的需求，可能需要修改配置。有大量开源指南解释了当 ZAP 配置为高级用法时可以执行的许多操作。

在 [Figure 11.15](#c11.xhtml#c11-fig-0015) 所示示例中，我们使用一个故意设置漏洞的域名进行测试。

![Figure 11.15 Setting up an Automated Scan in OWASP ZAP.](images/c11f015.png)

[**Figure 11.15**](#c11.xhtml#rc11-fig-0015) 在 OWASP ZAP 中设置自动扫描。

点击 "attack" 按钮后，它将开始爬取并测试各种载荷以查找漏洞（[Figure 11.16](#c11.xhtml#c11-fig-0016)）。

![Figure 11.16 OWASP ZAP Scan Results.](images/c11f016.png)

[**Figure 11.16**](#c11.xhtml#rc11-fig-0016) OWASP ZAP 扫描结果。

警报字段显示所有可能的攻击向量，在本例中，爬取和载荷测试发现了一个基于 DOM 的 XSS 漏洞（[Figure 11.17](#c11.xhtml#c11-fig-0017)）。在已识别漏洞的右侧，通常会提供载荷和攻击描述。如果我们复制该载荷，如下所示：

![Figure 11.17 OWASP ZAP Potential Vulnerability Result.](images/c11f017.png)

[**Figure 11.17**](#c11.xhtml#rc11-fig-0017) OWASP ZAP 潜在漏洞结果。

`https://xss-game.appspot.com/level1/frame#jaVasCript`:/\*-/\*\`/\*\\\`/\*’/\*”/\*\*/(/\* \*/oN cliCk = alert())//%0D%0A%0d%0a// </stYle/ </titLe/ </teXtarEa/ </scRipt/–! >\\x3csVg/ < sVg/oNloAd = alert()// >\\x3e

当该载荷输入浏览器时，成功执行了 XSS 攻击（[Figure 11.18](#c11.xhtml#c11-fig-0018)）：

![Figure 11.18 XSS Attack Performed.](images/c11f018.png)

[**Figure 11.18**](#c11.xhtml#rc11-fig-0018) 执行 XSS 攻击。

不要被迷惑：OWASP ZAP 并非专用的 XSS 工具。它具备模糊测试、编辑和重发请求以及搜索大量漏洞的能力。项目经理可以花费数小时自定义 ZAP，甚至可以导出漏洞报告。

### 11.4.4 Dalfox

在项目经理用于测试 URL 参数和查找隐藏参数的工具库中，DalFox 是最好的工具之一。由 hahwul 维护，DalFox 可从 GitHub 下载。通过收集 URL 列表，甚至拥有根域名列表，DalFox 已被证明是一款得力工具。文件选项允许测试多个参数，也可以提供单个 URL 进行测试（[Figure 11.19](#c11.xhtml#c11-fig-0019)）。有大量选项可供使用，因此请在使用前阅读手册。

![Figure 11.19 Dalfox Available Command.](images/c11f019.png)

[**Figure 11.19**](#c11.xhtml#rc11-fig-0019) Dalfox 可用命令。

在该具体示例中，将使用我们之前用 ZAP 测试时的一个已知易受攻击的 URL。

`/dalfox url https://xss-game.appspot.com/level1/frame`

运行脚本后很快就通过 query = 参数识别出一个 XSS 实例（[Figure 11.20](#c11.xhtml#c11-fig-0020)）。输出一个最终载荷，带有 `[POC][V]`，意味着该利用已验证可行——或至少被检测为如此（[Figure 11.21](#c11.xhtml#c11-fig-0021)）。

![Figure 11.20 Dalfox Identifying an XSS Instance.](images/c11f020.png)

[**Figure 11.20**](#c11.xhtml#rc11-fig-0020) Dalfox 识别 XSS 实例。

![Figure 11.21 XSS Attack.](images/c11f021.png)

[**Figure 11.21**](#c11.xhtml#rc11-fig-0021) XSS 攻击。

载荷：`https://xss-game.appspot.com/level1/frame?query=%3CScRipt+class%3Ddalf​ox%3Ealert%2845%29%3C%2Fscript%3E`

### 11.4.5 Dirsearch

模糊测试也是内部评估的一个重要方面。黑客喜欢直接跳到利用的核心部分，这导致许多人忘记了，有时少即是多。最好的攻击是黑客了解关于目标的一切。因此，项目经理应努力比参与的安全研究人员多了解两倍的信息。模糊测试的理念是在 Web 应用程序上搜索隐藏文件或目录。Dirsearch 简化了这一过程。与大多数工具一样，开始使用需要从 GitHub 下载，除非它已预装在所选的渗透测试操作系统中。Dirsearch 由 maurosoria 创建。再次强调，阅读手册很重要，因为有大量不同的开关可用于创建和微调相关过程。

几个组合开关似乎对快速测试很有效：`-x` 用于包含要忽略的状态码（以避免误报或无关真阳性过载），`-e` 用于标注需要测试的扩展名，`-f` 用于强制将扩展名追加到从默认字典测试的每个单词上。例如，如果测试一个 URL 且工具在寻找 admin 目录，若使用 `-e php -f` 作为开关选项，`admin.php` 也会被测试。如果使用更匆忙的测试，移除 `-e` 和 `-f` 开关将仅测试目录并包含文件路径。

作为示例，假设有以下命令：

```
python3 dirsearch.py -u http://127.0.0.1:8000 -e php,txt,bak,conf -f -x 300,301,302,303,304,400,401,402,403,404,500,501,502,503,504
```

