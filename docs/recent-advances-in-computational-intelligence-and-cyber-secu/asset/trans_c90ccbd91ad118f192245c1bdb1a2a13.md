

*信任与透明性：* 区块链网络提供高度的信任和透明性，是智能合约的操作系统。由于交易和合约执行记录在公共账本上，因此可审计且防篡改。

*去中心化：* 为最大限度减少对中心化权威的需求，智能合约通常部署在去中心化区块链上。这种去中心化增强了合约的安全性和不可变性。

*不可变：* 一旦智能合约部署，其代码和执行逻辑即不可变。这确保部署后任何一方都无法更改合约条款。

*以太坊：* 提供功能强大、图灵完备的智能合约，但由于 gas 费用可能更慢且成本更高。

*Hyperledger fabric：* 为智能合约提供模块化且可扩展的方法，适用于复杂的医疗工作流程和应用（[Table 2.4](#ch2.xhtml#tab2_4)）。

[Table 2.4: Comparative analysis of various methods in public and private blockchain](#ch2.xhtml#R_tab2_4)

| Feature || Public blockchains || Private blockchains |
| --- | --- | --- |
| Transparency || High transparency and decentralization || Permissioned, limited transparency |
| --- | --- | --- |
| Consensus mechanism || Typically PoW (slower, resource-intensive) || Often PoS (more energy-efficient) |
| Smart contracts || Ethereum (robust, slower, higher cost) || Hyperledger fabric (modular, scalable) |
| Data interoperability || Promotes interoperability through standardized data formats and APIs || Promotes interoperability through multi chain architecture |
| Privacy and security || Less private; privacy-preserving technologies needed || Enhanced privacy and access control |
| Scalability || Can be a challenge; need solutions like sharding, sidechains || More control over scalability |
| Regulatory compliance || Compliance can be complex; adapt to regulations like HIPAA, GDPR || Easier compliance with tailored rules |
| Tokenization || Can be used to incentivize data sharing || Incentives can be managed with more control |
| Costs and energy efficiency || Higher costs and energy consumption || More cost-effective and efficient |
| User experience || User-friendly interfaces and workflows || Tailored to the needs of participants |

## 6. Existing applications of blockchain in the healthcare domain

区块链技术在医疗保健领域日益发挥作用，因其能够改善数据安全、互操作性和透明度。区块链在医疗保健中的若干现有应用如下：

### 6.1. Estonia's e-health system

爱沙尼亚在数字治理方面的突出地位体现于其先进的电子健康系统。该综合且安全的数字健康基础设施以患者为中心，包括电子健康记录以及一系列医疗管理电子服务。显著的特性和实施情况如[Table 2.5](#ch2.xhtml#tab2_5)所示。

[Table 2.5: Features of Estonia's e-health system](#ch2.xhtml#R_tab2_5)

| Aspect || Description |
| --- | --- |
| a. Electronic health records (EHRs) || 爱沙尼亚公民可访问一个安全且集中的电子健康记录系统，由安全的数字身份保护。这些 EHR 全面包含患者的完整病史、处方、检验结果和其他健康相关数据。患者和医疗提供者均可安全地访问和更新此信息 |
| --- | --- |
| b. Digital ID || 爱沙尼亚人使用数字身份证访问其健康记录和其他电子政务服务。该卡确保安全认证和数据保护 |
| c. Data interoperability || 电子健康系统优先考虑数据互操作性，使医疗专业人员能够跨不同提供者访问患者信息，从而促进协调一致的患者护理 |
| d. E-prescriptions || 爱沙尼亚的电子健康系统优化了电子处方的开具。患者以数字方式接收处方，并可从任何药房方便地领取药物，有效减少文书工作并最大限度降低处方错误 |
| e. Telemedicine || 爱沙尼亚已采用远程医疗，使患者能够与医疗专业人员进行远程咨询，这在农村地区尤其有价值 |
| f. Patient access || 患者能够在线访问和查看其健康记录、检验结果和处方历史。此外，他们在必要时可向医疗提供者授予临时访问权限 |
| g. Blockchain in healthcare || 爱沙尼亚已开始在医疗保健中应用区块链技术，以确保健康数据的最大安全性和完整性 |

*MedRec by MIT:* MedRec 是由麻省理工学院开发的创新型基于区块链技术的电子健康记录系统。其主要目标是赋予患者对其健康数据的更大控制权，同时确保隐私和安全 \[[28](#ch2.xhtml#ref2_28), [29](#ch2.xhtml#ref2_29) and [30](#ch2.xhtml#ref2_30)\]。该系统的关键特性如[Table 2.6](#ch2.xhtml#tab2_6)所示。

[Table 2.6: Features of MedRec](#ch2.xhtml#R_tab2_6)

| Aspect || Description |
| --- | --- |
| a*.* Patient control || MedRec 赋予患者对其健康记录的控制权，使其能够决定谁可以访问其数据以及出于何种特定目的可以访问 |
| --- | --- |
| b. Blockchain technology || MedRec 利用区块链技术保护健康数据，确保透明性和不可变性。这种强大的安全机制不仅保护数据完整性，还降低了未经授权访问的风险 |
| c. Privacy preserving smart contracts || MedRec 采用智能合约高效管理数据访问权限和数据共享。这些智能合约提供精细控制，允许患者指定谁可以访问特定健康数据以及出于何种目的 |
| d. Research opportunities || MedRec 通过允许研究人员请求访问汇总和匿名化的健康数据，积极促进医学研究。这种方法在保护个人隐私的同时促进研究机会 |

### 6.2. Medicalchain

Medchain 是一个基于区块链技术的开创性医疗保健平台，专门设计用于改善医疗记录的管理和安全性。该系统的关键特性包括以下内容 \[[31](#ch2.xhtml#ref2_31), [32](#ch2.xhtml#ref2_32)\]：

*Patient-driven access:* Medicalchain 通过让患者完全控制其健康数据并按需授予医疗提供者访问权限，从而赋予患者权力。

*Telemedicine:* 该平台无缝集成远程医疗，使患者能够与医疗专业人员进行远程咨询。

*Secure and immutable records:* Medicalchain 通过将健康记录存储在区块链上确保其安全性和不可变性。这保证了存储数据的完整性。

*Health passport:* Medicalchain 引入了独特的“健康护照”功能，使患者能够汇编其完整的病史。该病史可方便地与全球医疗提供者共享，从而简化患者护理（[Table 2.7](#ch2.xhtml#tab2_7)）。

[Table 2.7: Blockchain in healthcare domain](#ch2.xhtml#R_tab2_7)

| Feature || Description |
| --- | --- |

