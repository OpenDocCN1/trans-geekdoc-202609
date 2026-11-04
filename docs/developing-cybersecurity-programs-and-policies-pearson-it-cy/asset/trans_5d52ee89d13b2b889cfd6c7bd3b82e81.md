
### [25](#app02.xhtml#ch15qu-25).
根据 PCI 标准所规定的最佳实践，网络安全政策应多久审查、更新和授权一次？
**A.** 一次
**B.** 每半年
**C.** 每年
**D.** 每两年

### [26](#app02.xhtml#ch15qu-26).
以下哪项关于 PCI 要求是正确的？
**A.** PCI 标准补充但不取代保护个人身份信息（PII）或其他数据元素的立法或监管要求。
**B.** PCI 标准取代保护个人身份信息（PII）或其他数据元素的立法或监管要求。
**C.** PCI 要求使监管要求无效。
**D.** 以上都不是。

### [27](#app02.xhtml#ch15qu-27).
以下哪项关于一级商户与二级至四级商户是正确的？
**A.** 一级商户每年处理超过六百万笔支付卡交易。
**B.** 一级商户必须支付超过 600 万美元的费用。
**C.** 一级商户必须进行每两年一次的外部渗透测试。
**D.** 一级商户必须完成自我评估问卷或支付超过 100,000 美元的罚款。

### [28](#app02.xhtml#ch15qu-28).
PCI DSS 版本 3.2 主要将 DESV 作为附录纳入，以合并要求并加强这些要求在建立和维护持续网络安全流程方面的重要性。DESV 是一份资源和标准清单，旨在帮助服务提供商和商户在努力保护支付并保持合规的同时解决关键运营挑战。以下哪项不包含在 DESV 中？
**A.** 合规计划监督
**B.** 环境的适当范围界定
**C.** 确保使用适当的机制来检测和警报关键安全控制的故障
**D.** 公共安全漏洞披露政策的创建

### [29](#app02.xhtml#ch15qu-29).
以下哪项陈述最能描述为何需要不同版本的 SAQ？
**A.** 问题数量因支付卡渠道和环境范围而异。
**B.** 问题数量因地理位置而异。
**C.** 问题数量因卡品牌而异。
**D.** 问题数量因交易金额而异。

### [30](#app02.xhtml#ch15qu-30).
以下哪些 SAQ 不适用于电子商务商户？
**A.** SAQ-C
**B.** SAQ-B
**C.** SAQ C-VT
**D.** 以上全部

## Exercises

### Exercise 15.1: Understanding PCI DSS Obligations
练习 15.1：理解 PCI DSS 义务
1. 符合 PCI DSS 是一项合同义务。解释它与监管义务有何不同。
2. 哪一项优先——监管要求还是合同义务？解释你的答案。
3. 谁执行 PCI 合规？如何执行？

### Exercise 15.2: Understanding Cardholder Liabilities
练习 15.2：理解持卡人责任
1. 如果消费者弄丢了借记卡，他或她应该怎么做？为什么？
2. 登录你的银行网站。它是否发布了如何报告丢失或被盗借记卡或信用卡的说明？如果是，总结其说明。如果没有，请致电银行要求将信息发送给你。 （如果你没有银行账户，请选择一家当地金融机构。）
3. 解释《公平信用计费法》（FCBA）与《电子资金转账法》（EFTA）之间的区别。

### Exercise 15.3: Choosing an Authorized Scanning Vendor
练习 15.3：选择授权扫描供应商
1. 所有具有面向互联网 IP 地址的商户和服务提供商都需要进行 PCI 安全扫描。网上查找三家提供季度 PCI 安全扫描的 PCI 委员会授权扫描供应商（ASV）。
2. 阅读他们的服务说明。有哪些相似之处和不同之处？
3. 推荐其中一家 ASV。解释你的理由。

### Exercise 15.4: Understanding PIN and Chip Technologies
练习 15.4：理解 PIN 和芯片技术
1. 美国发行的支付卡将敏感身份验证信息存储在磁条中。这种配置存在哪些问题？
2. 欧洲发行的支付卡将敏感身份验证信息存储在嵌入式微芯片中。这种配置的优势是什么？
3. 某些美国金融机构应要求提供嵌入芯片的卡。确定至少一家会这样做的发卡机构。它会额外收费吗？

### Exercise 15.5: Identifying Merchant Compliance Validation Requirements
练习 15.5：确定商户合规验证要求
完成下表：
| **商户级别** || **标准** || **验证要求** |
| --- | --- | --- |
|  || 每年处理不足 20,000 笔电子商务交易 ||  |
| --- | --- | --- |
| Level 2 ||  ||  |
|  ||  || 需要现场年度审计 |

## Projects

### Project 15.1: Applying Encryption Standards
项目 15.1：应用加密标准
加密在 PCI DSS 标准中被多次提及。对于下面列出的每个 PCI 要求：
1. 解释该要求的理由。
2. 确定可用于满足该要求的加密技术。
3. 确定可用于满足该要求的商业应用。
* **PCI DSS V3.2. 3.4.1:** 如果使用磁盘加密（而不是文件或列级数据库加密），则必须单独且独立于原生操作系统身份验证和访问控制机制来管理逻辑访问（例如，不要使用本地用户账户数据库或通用网络登录凭据）。解密密钥不得与用户账户关联。
* **PCI DSS V3.2. 4.1.1:** 确保传输持卡人数据或连接到持卡人数据环境的无线网络使用强大的加密协议进行身份验证和传输，并使用行业最佳实践实施强大的身份验证和传输加密。
* **PCI DSS V3.2 6.1:** 建立一个流程来识别安全漏洞，使用可靠的外部来源获取安全漏洞信息，并为新发现的安全漏洞分配风险等级（例如，“高”、“中”或“低”）。

### Project 15.2: Completing an SAQ
项目 15.2：完成 SAQ
所有主要信用卡公司都有专门的在线门户来解释他们如何让卡会员信息安全可靠。以下是几家主要信用卡公司的安全门户链接：
* 美国运通：[https://merchant-channel.americanexpress.com//merchant/en_US/data-security](https://merchant-channel.americanexpress.com//merchant/en_US/data-security)
* Discover Card：[https://www.discovernetwork.com/en-us/business-resources/fraud-security/pci-rules-regulations/](https://www.discovernetwork.com/en-us/business-resources/fraud-security/pci-rules-regulations/)
* JCB Card：[www.global.jcb/en/products/security/pci-dss/](http://www.global.jcb/en/products/security/pci-dss/)
* MasterCard：[https://www.mastercard.us/en-us/merchants/safety-security/security-recommendations/site-data-protection-PCI.html](https://www.mastercard.us/en-us/merchants/safety-security/security-recommendations/site-data-protection-PCI.html)
* VISA：[https://usa.visa.com/support/small-business/security-compliance.html](https://usa.visa.com/support/small-business/security-compliance.html)
1. 这些信用卡公司提供的信息有何异同？描述他们如何记录和解决 PCI DSS 合规性。
2. 解释他们如何记录适用于商户和服务提供商的<|message|>要求。
3. 每家公司是否都清楚列出任何人如何报告安全事件？

### Project 15.3: Reporting an Incident
项目 15.3：报告事件
假设你是一家二级商户，你的组织怀疑发生了 Visa 持卡人信息泄露。
