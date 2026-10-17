
Sometimes, an innocent (or ignorant) insider whose intent isn’t malicious still causes security problems by moving, deleting, or corrupting sensitive information. Even an innocent fat finger on the keyboard can have dire consequences in the business world. Think about all the ransomware infections affecting businesses around the world. All it takes is one click by a careless user for your entire network to be affected.

Malicious users are often the worst enemies of IT and information security professionals because they know exactly where to go to get the goods and don’t need to be computer-savvy to compromise sensitive information. These users have the access they need, and management trusts them — often without question.

What about that Edward Snowden guy — the former National Security Agency employee who ratted out his own employer? That subject is a complicated one. (I talk about hacker motivations in Chapter 2.) Regardless of what you think of Snowden, he abused his authority and violated the terms of his nondisclosure agreement. The same can be said of others who, for whatever reason, are placed on a pedestal because of their notoriety.

## Recognizing How Malicious Attackers Beget Ethical Hackers

You need protection from hacker shenanigans; you have to become as savvy as the guys who are trying to attack your systems. A true security assessment professional possesses the skills, mindset, and tools of a hacker but is trustworthy. He or she performs hacks as security tests against systems based on how hackers think and work.

![remember](img/remember.png)`Ethical hacking` (otherwise known as vulnerability and penetration testing) involves the same tools, tricks, and techniques that criminal hackers use, with one major difference: It’s performed with the target’s permission in a professional setting. The intent of this testing is to discover vulnerabilities from a malicious attacker’s viewpoint to better secure systems. Vulnerability and penetration testing is part of an overall information risk management program that allows for ongoing security improvements. This security testing can also ensure that vendors’ claims about the security of their products are legitimate.

### Vulnerability and penetration testing versus auditing

Many people confuse security testing via vulnerability and penetration testing with security auditing, but `big` differences exist in the objectives. Security auditing involves comparing a company’s security policies (or compliance requirements) with what’s actually taking place. The intent of security auditing is to validate that security controls exist, typically by using a risk-based approach. Auditing often involves reviewing business processes and in some cases isn’t very technical. Security audits, in fact, can be as basic as security checklists that simply serve to meet a specific compliance requirement.

![remember](img/remember.png)`Not all audits` are high-level, but many of the ones I’ve seen — especially those involving compliance with the Payment Card Industry Data Security Standard (PCI DSS) and the Health Insurance Portability and Accountability Act (HIPAA) — are quite simplistic. Often, these audits are performed by people who have no technical computer, network, or application experience — or, worse, work outside IT altogether!

Conversely, security assessments based on ethical hacking focus on vulnerabilities that can be exploited. This testing approach validates that security controls `don’t` exist or are ineffectual. This formal vulnerability and penetration testing can be both highly technical and nontechnical, and although it involves the use of formal methodology, it tends to be a bit less structured than formal auditing. Where auditing is required (such as for SSAE 16 SOC 1/2/3 audits and the ISO 27001 certification) in your organization, you might consider integrating the vulnerability and penetration testing techniques I outline in this book into your IT/security audit program. Auditing and vulnerability and penetration testing complement one another really well.

### Policy considerations

If you choose to make vulnerability and penetration testing an important part of your business’s information risk management program, you really need to have a documented security testing policy. Such a policy outlines who’s doing the testing, the general type of testing that’s performed, and how often the testing takes place. Specific procedures for carrying out your security tests could outline the methodologies I cover in this book. You might also consider creating a security standards document that outlines the specific security testing tools used and the specific people performing the testing. You could establish standard testing dates, such as once per quarter for external systems and biannual tests for internal systems — whatever works for your business.

### Compliance and regulatory concerns

Your own internal policies may dictate how management views security testing, but you also need to consider the state, federal, and international laws and regulations that affect your business. In particular, the Digital Millennium Copyright Act (DMCA) sends chills down the spines of legitimate researchers. See [`www.eff.org/issues/dmca`](http://www.eff.org/issues/dmca) for everything that the DMCA has to offer.

Many federal laws and regulations in the United States — such as HIPAA and the associated Health Information Technology for Economic and Clinical Health (HITECH) Act, Gramm-Leach-Bliley Act (GLBA), North American Electric Reliability Corporation (NERC) Critical Infrastructure Protection (CIP) requirements, and PCI DSS — require strong security controls and consistent security evaluations. Related international laws —such as the Canadian Personal Information Protection and Electronic Documents Act (PIPEDA), the European Union’s General Data Protection Regulation (GDPR), and Japan’s Personal Information Protection Act (JPIPA) — are no different. Incorporating your security tests into these compliance requirements is a great way to meet state and federal regulations and to beef up your overall information security and privacy program.

## Understanding the Need to Hack Your Own Systems

To catch a thief, you must think like a thief. That adage is the basis of vulnerability and penetration testing. Knowing your enemy is critical. The law of averages works against security. With the increased number of hackers and their expanding knowledge, and the growing number of system vulnerabilities and other unknowns, all computer systems and applications will eventually be hacked or compromised in some way. Protecting your systems from the bad guys — not just addressing general security best practices — is critical. When you know hacker tricks, you find out how vulnerable your systems really are.

黑客利用弱密码实践和未披露的漏洞进行攻击。越来越多的研究，例如年度《Verizon 数据泄露调查报告》([`www.verizonenterprise.com/verizon-insights-lab/dbir`](http://www.verizonenterprise.com/verizon-insights-lab/dbir))，显示长期存在的、已知的漏洞也在被攻击。防火墙、加密和其他花哨（且昂贵）的安全技术常常会产生一种虚假的安全感。这些安全系统通常关注高级别漏洞，例如访问控制和保护传输中的信息，而不影响攻击者的作战方式。主动测试自己的系统以发现漏洞——特别是那些会让许多人陷入麻烦的低悬挂果实——有助于提升系统安全性。漏洞和渗透测试是经过验证的方法，可极大加固系统免受攻击。如果不发现弱点，那么被利用的漏洞只是时间问题。

随着黑客知识的扩展，你也应该如此。你必须像他们一样思考，像他们一样行动，以保护系统免受他们的侵害。作为伦理黑客，你必须了解不法黑客所进行的活动，以及如何阻止他们的努力。知道要寻找什么以及如何利用这些信息，能够帮助你阻碍黑客的行动。

![tip](img/tip.png)你不必保护系统免受`一切`威胁。你无法做到。唯一能防止一切的办法是拔掉计算机系统并将其锁在仓库中，让任何人都无法触碰——包括你自己。但这种做法并非最佳的安全措施，也绝对不利于业务！重要的是保护系统免受已知漏洞和常见攻击的侵害——即那 20% 的问题导致 80% 的风险，这些问题恰恰是大多数组织中被忽视的最薄弱环节。

预测系统和业务流程中所有可能的漏洞是不可能的。你当然无法规划所有类型的攻击——尤其是未知的攻击。但你尝试的组合越多，越频繁地测试整个系统而非单个组件，你发现影响整个信息系统的漏洞的机会就越大。

不过，切勿将安全测试做得过于极端；对不太可能（甚至`更不可能`）的攻击进行加固意义不大。

![remember](img/remember.png)你的安全测试总体目标是：

*   将系统优先级排序，以便集中精力于最重要的部分。

*   在不破坏系统的方式下进行测试。

*   列举漏洞，必要时向管理层证明业务风险的存在。

*   将结果用于解决漏洞，进一步加固系统。

## 理解系统所面临的危险

仅仅知道全球黑客和内部恶意用户对系统发起攻击是一回事，另一回事是理解针对系统的具体潜在攻击。本节讨论一些知名攻击，但并非 exhaustive（全面）的列表。
