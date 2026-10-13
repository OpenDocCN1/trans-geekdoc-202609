

其他 SIEM 专注于 SEM，这意味着它们提供各种事件管理和事件分析功能。`IBM QRadar` 就是一个拥有大量 SEM 功能的 SIEM 示例。QRadar 事件功能的示例包括开发各种类型仪表板的能力、识别网络上的每个资产，甚至直接从仪表板启动原生或第三方漏洞扫描器。需要明确的是，`Splunk` 具备 SEM 功能，而 `QRadar` 可作为 SIM 用于挖掘数据，但这两个系统在满足这些特定需求时的体验截然不同。[图 2-27](#ch02.xhtml#ch02fig27) 是一个名为 `Pulse` 的 QRadar 应用程序仪表板示例。[第 5 章](#ch05.xhtml#ch05) 将更详细地介绍 SIEM 和数据管理。

![图 2-27 QRadar 仪表板示例](Images/02fig27.jpg)

**图 2-27** QRadar 仪表板示例

一些 SIEM 不提供对事件采取行动的能力。行动的一个示例可以是阻止 SIEM 解决方案识别出的事件。如果无法采取行动，分析师将使用 SIEM 产品进行事件感知，同时使用其他方法采取行动。采取行动的程序可以记录下来并转化为剧本，随后可以实现自动化。这被称为 `orchestration`（编排），这正成为 SIEM 适配或与其他供应商合作以作为组合解决方案提供的一项功能。我们将在 [第 10 章](#ch10.xhtml#ch10) “[数据编排](#ch10.xhtml#ch10)” 中更深入地探讨编排。

SIEM 还可以包含不同的事件跟踪方法。一种流行的方法是工单系统。工单系统可以是 SIEM 或编排平台的一部分，也可以是专门为此目的而设的。`BMC’s Helix ITSM` 和 `ServiceNow Security Operations` 就是可用于此目的的事件跟踪平台示例。优秀的工单工具包含协作功能，例如用于搜索过去发生的类似案例的 Wiki。`Tiki Wiki CMS Groupware` 和 `MediaWiki` 等工具也是此方面的选项。我建议在评估用于管理 SOC 将负责监控和处理的所有数据的解决方案时，考虑所有这些需求。

> **注意**
>
> SOC 拥有自己的 SIEM、SOAR 和/或 XDR 以保护 SOC，而不是共享用于保护组织的系统，这是理想的。如果使用共享系统，则必须在 SOC 网络和组织网络之间对管理权限进行分段。

### 总结

本章重点介绍了如何建立一个新的 SOC 以及如何提高现有 SOC 的成熟度。首先介绍的概念是如何制定使命和范围声明。这些构成了所有 SOC 策略和程序的基石，也是 SOC 存在的基础。接下来介绍的概念是 SOC 策略和程序的重要性，它们构成了 SOC 将提供的服务的基石。随后本章介绍了安全工具概念，这些是 SOC 不仅用于保护其负责的组织，而且用于保护 SOC 自身免受攻击的工具。

本章剩余主题涵盖了在规划和建设安全运营中心时需要解决的具体细节。主题涵盖了从如何定制 SOC 设施到需要何种类型的容量和吞吐量来支持 SOC 服务的所有内容。许多这些规划概念也适用于构建和保护组织，但本章的重点是开发 SOC，其中包括将 SOC 相关数据与组织数据分段并加以保护。

到目前为止，我提供了建设 SOC 的高层概述。在接下来的章节中，我们将更深入地探讨使 SOC 成功的要素。[第 3 章](#ch03.xhtml#ch03) 概述了现代 SOC 提供的各种服务。这包括使用内部资源提供的服务以及外包服务。我强烈建议每个 SOC 至少拥有下一章介绍的每项 SOC 服务的最小版本，或者至少有外包资源可用。最糟糕的情况是组织需要一项 SOC 未提供的安全服务，却不知道去哪里寻找合同支持来弥补这项缺失的服务。

### 参考文献

Bodwell, D. J. (1996, June 23). Team Charter. High Performance Teams. [http://www.highperformanceteams.org/hpt_chtr.htm](http://www.highperformanceteams.org/hpt_chtr.htm)

Cisco. Data Center Power and Cooling White Paper. [https://www.cisco.com/c/en/us/solutions/collateral/data-center-virtualization/unified-computing/white_paper_c11-680202.html](https://www.cisco.com/c/en/us/solutions/collateral/data-center-virtualization/unified-computing/white_paper_c11-680202.html)

Conway, B. (2017, May 12). Office Building. Whole Building Design Guide. [https://www.wbdg.org/building-types/office-building](https://www.wbdg.org/building-types/office-building)

Ferrill, P. (2018, January 8). The Best Mobile Device Management (MDM) Solutions for 2020. *PC Magazine*. [https://www.pcmag.com/article/342695/the-best-mobile-device-management-mdm-software](https://www.pcmag.com/article/342695/the-best-mobile-device-management-mdm-software)

International Organization for Standardization. (2004, May). ISO 17624:2004: Acoustics – Guidelines for noise control in offices and workrooms by means of acoustical screens. ISO. [https://www.iso.org/standard/33148.html](https://www.iso.org/standard/33148.html)

International Organization for Standardization. (2011, March). ISO/IEC 27031:2011: Information technology – Security techniques – Guidelines for information and communication technology readiness for business continuity. ISO. [https://www.iso.org/standard/44374.html](https://www.iso.org/standard/44374.html)

International Organization for Standardization. (2012, November). ISO 22311:2012: Societal security – Video surveillance – Export interoperability. ISO. [https://www.iso.org/standard/53467.html](https://www.iso.org/standard/53467.html)

ISACA. (2019). COBIT 2019 Framework (various publications). ISACA. [https://www.isaca.org/resources/cobit](https://www.isaca.org/resources/cobit)

Jones, C.P. (2017, June 9). Flood Resistance of the Building Envelope. Whole Building Design Guide. [https://www.wbdg.org/resources/flood-resistance-building-envelope](https://www.wbdg.org/resources/flood-resistance-building-envelope)

Key, T.S., & and Martzloff, F. D. (1986, September). A Consensus on Powering and Grounding Sensitive Electronic Equipment. Conference Record, IEEE/IAS Annual Meeting. [https://www.nist.gov/system/files/documents/pml/div684/Consensus.pdf](https://www.nist.gov/system/files/documents/pml/div684/Consensus.pdf)

Kosutic, D. (2015, September 21). Understanding IT Disaster Recovery According to ISO 27031. Advisera. [https://advisera.com/27001academy/blog/2015/09/21/understanding-it-disaster-recovery-according-to-iso-27031/](https://advisera.com/27001academy/blog/2015/09/21/understanding-it-disaster-recovery-according-to-iso-27031/)

McCarthy, K., & Avelar, V. (n.d.). Comparing UPS System Design Configurations. Schneider Electric – Data Center Science Center. Retrieved from [https://www.apc.com/salestools/SADE-5TPL8X/SADE-5TPL8X_R3_EN.pdf](https://www.apc.com/salestools/SADE-5TPL8X/SADE-5TPL8X_R3_EN.pdf)

Mearian, L. (2017, March 23). CW@50: Data Storage Goes from $1M to 2 Cents Per Gigabyte. Computerworld. [https://www.computerworld.com/article/3182207/cw50-data-storage-goes-from-1m-to-2-cents-per-gigabyte.html](https://www.computerworld.com/article/3182207/cw50-data-storage-goes-from-1m-to-2-cents-per-gigabyte.html)

