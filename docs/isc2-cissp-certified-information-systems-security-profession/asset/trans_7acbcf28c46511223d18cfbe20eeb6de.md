
Web 漏洞扫描是组织安全评估和测试程序的重要组成部分。以下情况建议运行扫描：

* 进行首次 Web 漏洞扫描时，先扫描所有应用程序，以检测遗留应用程序的问题。

* 在首次将新应用程序部署到生产环境之前，先对其进行扫描。

* 在将代码变更部署到生产环境之前，先对修改后的应用程序进行扫描。

* 按照固定频率扫描所有应用程序。受限资源可能需要根据应用程序的优先级来调度这些扫描，例如，处理敏感信息的 Web 应用程序的扫描频率可高于不处理敏感信息的应用程序。

在某些情况下，Web 应用漏洞扫描可能是合规性要求的前提。例如，第 4 章“法律、法规和合规”中讨论的支付卡行业数据安全标准 (PCI DSS) 要求组织要么至少每年进行一次 Web 应用漏洞扫描，要么安装专用的 Web 应用防火墙，以在防御 Web 漏洞方面再增加一层保护。

除了 Nessus 外，常用的 Web 应用漏洞扫描工具还包括商业版 Acunetix 扫描仪、开源的 Nikto 和 Wapiti 扫描器以及 Burp Suite 代理工具。

#### 数据库漏洞扫描

数据库包含组织最敏感的信息，是攻击者的有利目标。虽然大多数数据库通过防火墙防止直接的外部访问，但 Web 应用提供了进入这些数据库的入口，攻击者可能利用数据库驱动的 Web 应用发起攻击，包括 SQL 注入攻击。

数据库漏洞扫描工具让安全专业人员能够同时扫描数据库和 Web 应用，发现可能影响数据库安全的漏洞。`sqlmap` 是一款常用的开源数据库漏洞扫描器，它允许安全管理员对 Web 应用进行数据库漏洞探测。[Figure 15.6](#c15.xhtml#figure15-6) 展示了 sqlmap 对 Web 应用的扫描示例。

![FIGURE 15.6 Scanning a database-backed application with sqlmap ](images/c15f006.jpg)

[**FIGURE 15.6**](#c15.xhtml#figureanchor15-6) Scanning a database-backed application with sqlmap 

#### 漏洞管理工作流

采用漏洞管理系统的组织应当制定漏洞管理工作流，其基本步骤应包括：

1. *Detection*（检测）：漏洞的初步识别通常来源于漏洞扫描的结果。

2. *Validation*（验证）：扫描仪检测到漏洞后，管理员应确认该漏洞，以确保它不是误报。

3. *Remediation*（修复）：被验证的漏洞应随后进行修复，这可能包括应用供应商发布的安全补丁、修改设备配置、实施规避漏洞的工作绕道、或安装 Web 应用防火墙或其他控制措施，以阻止漏洞被利用。

工作流的目标是确保漏洞有序发现并得到解决。工作流还应包括依据漏洞严重程度、被利用的可能性以及修复难度对漏洞修复进行优先排序。

### 渗透测试

*渗透测试* 超出了漏洞测试技术，因为它实际尝试利用系统。漏洞扫描仅探测漏洞是否存在，通常不主动进攻目标系统。（不过，某些漏洞扫描技术可能会干扰系统，但这些选项默认是禁用的。）执行渗透测试的安全专业人员则试图突破安全防护，入侵目标系统或应用，以证明其缺陷。

渗透测试需要比漏洞扫描更大程度的专业安全人员关注。在进行渗透测试时，安全专业人员通常会针对单个系统或一组系统，使用多种技术获取访问。整个过程通常包括如下阶段，如[Figure 15.7](#c15.xhtml#figure15-7)所示：

* *Planning*（规划）包括确定测试范围和参与规则。此阶段至关重要，因为它确保测试团队与管理层对测试的性质达成一致，并明确授权。

* *Information gathering and discovery*（信息收集与发现）使用手动和自动化工具收集目标环境信息，包括基础侦察（如访问系统上托管的网站）和网络发现扫描（识别开放端口）。

* *Vulnerability scanning*（漏洞扫描）通过网络漏洞扫描、Web 漏洞扫描和数据库漏洞扫描来探测系统弱点。

* *Exploitation*（利用）使用手动和自动化利用工具尝试绕过系统安全。

* *Reporting*（报告）总结渗透测试结果，并提出改进系统安全的建议。

渗透测试人员常用名为 `Metasploit` 的工具自动执行针对目标系统的利用。`Metasploit` 在[Figure 15.8](#c15.xhtml#figure15-8)中展示，它使用脚本语言实现常见攻击的自动化，从而大幅节省测试人员（以及黑客）的时间，消除许多重复、繁琐的步骤。

![FIGURE 15.7 Penetration testing process ](images/c15f007.jpg)

[**FIGURE 15.7**](#c15.xhtml#figureanchor15-7) Penetration testing process 

![FIGURE 15.8 The Metasploit automated system exploitation tool allows attackers to quickly execute common attacks against target systems. ](images/c15f008.jpg)

[**FIGURE 15.8**](#c15.xhtml#figureanchor15-8) The Metasploit automated system exploitation tool allows attackers to quickly execute common attacks against target systems. 

渗透测试人员可能是公司内部员工，也可能是受雇的外部顾问。测试通常分为三类：

**White Box Penetration Test**（白盒渗透测试）提供攻击者对目标系统的详细信息，跳过常规的侦察步骤，缩短攻击时间并提高发现安全漏洞的可能性。

**Gray Box Penetration Test**（灰盒渗透测试），也称为部分知识测试，常用于在白盒和黑盒测试之间取得平衡。当黑盒结果理想但成本或时间限制要求提供部分知识时，这种测试尤为常见。

**Black Box Penetration Test**（黑盒渗透测试）在攻击前不提供攻击者任何信息，模拟外部攻击者在获取业务和技术环境信息前进行入侵。

