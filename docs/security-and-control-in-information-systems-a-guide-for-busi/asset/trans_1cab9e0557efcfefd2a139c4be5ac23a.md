

# 术语表

## An early method of establishing a private key
当两个人试图通过不安全的通信链路建立私钥时的一种早期方法。以其发明者 Whitfield Diffie 和 Martin Hellman 的名字命名。

## Digital Signature
任何数字材料都可以使用签名者的私钥通过非对称加密进行“签名”。签名者必须绝对保密该密钥。任何知道签名者*公钥*的人都可以解密该材料。成功解密确认该材料确实来自签名者。

## Disaster Recovery Plan
一份详细计划，规定组织的信息系统遭受严重退化或损坏时应采取的措施。该计划应定期进行测试。

## Discretionary Access Control
允许用户“拥有”某些数据或设施，并决定是否授予其他用户访问权限的系统。这种安排在基于大型机的早期分时系统中被视为相当先进。随着个人计算机的出现，用户控制“其”资源并按自主基础共享这些资源已成为司空见惯的做法。

## EDI (Electronic Data Interchange)
使用标准电子格式交换业务报文。

## EDIFACT (Electronic Data Interchange for Administration, Commerce and Transport)
一种国际采用的 EDI 报文标准。它包含一些用于认证和安全的可选规定。

## Electronic Purse
一种可以存入现金价值的智能卡。持卡人可以在拥有适当读卡设备的零售商处“花费”该现金。

## Electronic Wallet
安装在用户个人计算机上的程序，当通过互联网进行金融交易时接管控制权。

## Electronic Watermark
一种证明电子（数字）材料作者身份或所有权的方法。另请参阅 Steganography。

## Encryption
对一段明文进行编码，以生成（不可理解的）加密报文。有时也称为 enciphering。

## ETSI (European Telecommunications Standards Institute)
一个制定欧洲标准的论坛，拥有数百名成员，主要来自电信行业。

## EU (Expected Utility)
一种量化风险的方法。通过将结果的大小（通常以货币收益或损失衡量）乘以该结果发生的概率来获得。

## Escrow
将电子材料副本存放给独立第三方的安排。可以规定在何种情况下以及向谁发布该材料。通常涉少量高价值材料，例如加密密钥。

## False Negative
用户识别失败的一种，即合法的授权用户被系统错误地拒绝。

## False Positive
用户识别失败的一种，即冒名顶替者（假装成授权用户）被系统错误地接受。

## Feedback Control
一种依赖于在事件发生*后*采取补救措施的控制。（例如，通过检查电话交换机生成的日志来检测未经授权的电话呼叫）。

## Firewall
安装在组织内部数据网络与外部网络（通常是互联网）边界上的保护设备。防火墙将过滤掉某些形式的不需要的流量和发起恶意攻击的尝试。

## Fraud
资产的挪用，或制造财务状况的误导性印象，行为人试图隐瞒任何不当行为的事实。

## General Control
应用于整个系统的任何类型控制的统称。这一概念更容易应用于基于一个或多个中央大型机的系统，因为“系统”几乎完全位于一个机房内。然而，在更复杂的分布式系统中，通用控制仍然是必要的，特别是在提供访问控制的“外部边界”方面。

## Generation Data Sets
一种轮换使用存放备份的介质的技术。通常有三代副本。每当制作新的备份副本时，*最旧*的版本会被覆盖，从而成为最新的一代。

## Groupware
旨在使工作组能够共享文件、程序和传入的电子文档的软件，通常具有供管理者监控和控制的功能。

## GSM (Groupe Spéciale Mondiale)
一种移动电话国际标准，有时被英文化为 Global System for Mobile Communications。用户识别由 SIM (Subscriber Identification Module) 提供。

## Hacker
在报刊用语中，指对信息系统进行恶意攻击的人，特别是跨数据网络的攻击。最初，“hacker”指对计算机内部结构有着痴迷兴趣的任何人。

## Hoax Virus
一种电子邮件，声称警告互联网上流行的病毒或其他危险。收件人被敦促转发该警告。实际上不存在危险，该邮件的目的是制造恐慌和大量不必要的邮件。

## Hot stand-by
一种提供计算机服务的备用设施，可在灾难发生时迅速激活。

## IAB (Internet Architecture Board)
（前身为 Internet Activities Board）一个协调互联网发展并推广技术标准的机构。

## ISACA (Information Systems Audit and Control Association)
一个长期致力于推广 IS 安全领域良好实践和专业标准的机构。总部位于美国，在世界其他地区设有分会。最初名为 EDP Auditors Association。

## IIA (Institute of Internal Auditors)
一个总部位于美国的组织，其成员从事内部审计、计算机审计、治理和内部控制工作。

## IIA-UK (Institute of Internal Auditors – United Kingdom)
与同名的美国机构职能相似，并与其有联系。

## (ISC)² (International Information Systems Security Certification Consortium Inc)
一个为 IS 安全从业者提供认证的非营利性公司。

## ISDN (Integrated Services Digital Network)
一种数字电信线路标准，可以像普通商用或家用电话线一样通过“拨号”按需连接。

## ITAR (International Traffic in Arms Regulations)
美国关于军火出口的法规。“军火”的定义包括加密产品和算法。

## ITSEC (Information Technology Security Evaluation & Certification Scheme)
欧盟委员会推动的一项计划，旨在制定评估 IT 产品和系统安全性的标准。

## KDC (Key Distribution Centre)
一种基于中央计算机存储和分发加密密钥的方法。密钥通常是对称的，用户群是“封闭的”（例如，仅限于一个组织的员工）。

## Kerberos
KDC 功能的扩展，最初在麻省理工学院开发，通过向用户发放电子“票据”，授权他们使用内部网络上的各种设施。Kerberos 经历了多个版本的演进，并已被纳入商业产品中。

## LEAF (Law Enforcement Access Field)
美国政府在 1990 年代初大力推广的“Clipper”加密芯片的一个有争议的特性。LEAF 提供了一种确定加密密钥的“后门”方法，从而解码报文。

## MAC (Mandatory Access Control)

