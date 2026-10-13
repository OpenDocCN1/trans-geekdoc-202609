
[Figure 9-29](#ch09.xhtml#ch09fig29) 展示了基于本章前面涉及的工作角色的漏洞管理流程摘要。资产所有者将收到漏洞通知，因为他/她最接近系统，也是评估其相关性的最佳人选。资产所有者可以决定是接受风险，还是指定实施其他行动（如风险降低）。安全官将收到通知，以便在整个缓解过程中跟踪漏洞状态。安全官还可以就潜在的风险降低步骤提供意见。IT 团队也将收到通知，以确定漏洞对网络的影响。IT 团队和安全官都可以提供网络或安全工具选项，在不对设备进行更改的情况下降低风险。所有意见将被汇总，并转化为纠正措施或接受风险的豁免。

![FIGURE 9-29 Summarizing Vulnerability Management Process](Images/09fig29.jpg)

**FIGURE 9-29** Summarizing Vulnerability Management Process

## Summary

本章涵盖了漏洞管理计划生命周期的方方面面。您学习了如何识别资产，并评估其价值及对组织其他部门的潜在风险。您了解了可用于漏洞管理计划的不同工具。我介绍了开发和运行漏洞管理服务所需的所有要素。您学习了调整现有扫描实践的不同方法，以及在何种情况下需要特殊例外处理。本章最后探讨了如何以及何时部署漏洞修复，以及潜在风险。

[Chapter 10](#ch10.xhtml#ch10) 将重点关注数据编排，这有助于改进许多 SOC 服务，包括漏洞管理。依我经验，凡是处理大量事件的组织，都在大力投资自动化和编排，这使得 [Chapter 10](#ch10.xhtml#ch10) 成为负责中大型组织的 SOC 专业人员的必读章节。

## References

Joint Task Force. (2020, September). NIST Special Publication 800-53, Revision 5: Security and Privacy Controls for Information Systems and Organizations. NIST. [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)

Nationwide. (n.d.). What Is Cyber Insurance? Nationwide. [https://www.nationwide.com/lc/resources/small-business/articles/what-is-cyber-insurance](https://www.nationwide.com/lc/resources/small-business/articles/what-is-cyber-insurance)

NIST Information Technology Laboratory. (n.d.). Vulnerability Metrics. NIST. [https://nvd.nist.gov/vuln-metrics/cvss](https://nvd.nist.gov/vuln-metrics/cvss)

Rapid7. (n.d.). Working with Scan Templates and Tuning Scan Performance. Rapid7. [https://docs.rapid7.com/nexpose/working-with-scan-templates-and-tuning-scan-performance#section-keep-the-triangle-in-mind-when-you-tune](https://docs.rapid7.com/nexpose/working-with-scan-templates-and-tuning-scan-performance#section-keep-the-triangle-in-mind-when-you-tune)

Risk Based Security. (2017, May 2). CVSSv3: When Every Vulnerability Appears to Be High Priority. Risk Based Security. [https://www.riskbasedsecurity.com/2017/05/02/cvssv3-when-every-vulnerability-appears-to-be-high-priority/](https://www.riskbasedsecurity.com/2017/05/02/cvssv3-when-every-vulnerability-appears-to-be-high-priority/)

Santos, O. (2016, October 31). The Evolution of Scoring Security Vulnerabilities: The Sequel. Cisco Blogs. [https://blogs.cisco.com/security/cvssv3-study](https://blogs.cisco.com/security/cvssv3-study)

Shakeel, I. (2019, July 5). Risk Management Concepts and the CISSP (Part 1). Infosec Resources. [https://resources.infosecinstitute.com/category/certifications-training/cissp/domains/security-and-risk-management/cissp-risk-management-concepts/#gref](https://resources.infosecinstitute.com/category/certifications-training/cissp/domains/security-and-risk-management/cissp-risk-management-concepts/#gref)

Souppaya, M., & Scarfone, K. (2013, July). NIST Special Publication 800-40, Revision 3: Guide to Enterprise Patch Management Technologies. NIST. [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-40r3.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-40r3.pdf)

# Chapter 10

# Data Orchestration

*I always try not to overload my music with orchestration and to use only those instruments that are absolutely necessary.*

—Abel Korzeniowski

术语 `data orchestration` 在许多群体中越来越流行，包括处理大量数据的云和数据中心专家。`data orchestration` 备受青睐，是因为随着数据量和速度的增加而出现了挑战。其中一个挑战是指望分析师能够查看并理解大量数据。即使是安全信息和事件管理 (`SIEM`) 等工具，也会迅速用事件数据淹没分析师，而这些事件数据代表的警报是合并后的事件，需要时间来调查。另一个挑战是在需要考虑许多因素、且过多事件同时发生并需要及时关注的情况下，选择对事件的最佳响应。随着公共云和威胁情报资源引入 `SOC`，调优数据需要付出更多努力，导致基于技术维护的工作增加。这类挑战导致 `SOCs` 生产力下降，应对之策是大力投资 `data orchestration`。

[Chapter 5](#ch05.xhtml#ch05) "[Centralizing Data](#ch05.xhtml#ch05)" 涵盖了 `SOCs` 可利用的各类数据，以及如何集中这些数据以简化跨多工具的可见性。[Chapter 5](#ch05.xhtml#ch05) 未涵盖的是如何基于这些数据采取行动。本章重点介绍如何通过自动化和编排来利用数据。安全行业称之为 `security orchestration, automation, and response (SOAR)`，它整合了 [Chapter 5](#ch05.xhtml#ch05) 涵盖的数据收集概念和 [Chapter 8](#ch08.xhtml#ch08) "[Threat Hunting and Incident Response](#ch08.xhtml#ch08)" 涵盖的事件响应概念，并专注于通过编排实现自动化。本章还涵盖了利用 `SOAR` 技术（如剧本和 `DevOps`）所需的概念和技能。`SOAR` 技术涉及内容繁多，本章将其分解为更易消化的模块。

> **Note**
>
> 本章还将介绍跨层检测与响应 (`XDR`)，它提供了许多与 `SOAR` 技术相同的功能。

## Introduction to Data Orchestration
