

# 4.8 致命网络攻击场景

我们将再次回到致命网络攻击可能产生的影响，以此作为本章的总结。让我们回顾一下我们正在探讨的一个挑衅性问题：网络攻击能否致死？这个问题之前已经提出过，但给出的答案只是暗示性的。

这一次，我们将直接回答这个问题：是的，一个人可能会被网络攻击杀死。以下是一个场景。

## 4.8.1 具有致命后果的网络攻击场景——此类逻辑炸弹能否被检测？

正如我们已经提到的，存在这些潜在可能性。接管医疗诊断系统，例如给患者施以过高剂量的辐射，可能是可行的。也可能以这样的方式接管植入物，即通过识别 `a specific` 植入物（甚至特定个人或群体，例如通过检查硬件序列号），恶意软件会被激活并发送恶意指令。

另一个假设场景甚至可能是一次非常大规模的网络攻击。让我们设想一次大规模网络行动的执行。

让我们考虑一个假设场景，即发生此类植入物的大规模感染。此类植入物就是计算机。计算机，正如已经清楚的那样，有时钟。因此，理论上可以设计此类植入物中的恶意软件，使其在特定选定的某一天、某个特定时间激活自身。如果我们有数千名患者用户，并且在所有植入物中同时启动恶意程序会怎样？在极端情况下，这可能导致数千名受害者。这将是一次极其卑鄙和恶毒的网络攻击，其有效性不幸地潜在很高。这种情况将比此类死亡以无协调方式、接二连三地发生严重得多。因为如果我们面对的是孤立病例，有人可能会开始调查它们，问题最终会被识别，原因会被发现，并有机会补救问题。然而，如果我们有数千次攻击同时执行，就没有快速响应的可能性，调查将需要时间。

事实上，我们在这里考虑的是将 `logic bomb` 嵌入此类植入物的用法。逻辑炸弹，即在特定情况下（如特定时间）激活的恶意软件。之前解释过，此类攻击是否可被检测尚不清楚。然而，如果我们在大致相同的时间发生数千次故障，这将是一个非常有力的迹象，表明这并非巧合。具有这种协调效应、这种规模的简单故障，在统计上是不可能的。

## 4.8.2 医疗植入物协同电池耗尽？一个场景

现在让我们考虑一个假设的破坏性场景，假设（为可视化做的数值假设）因网络攻击导致 10,000 名患者的植入物被感染——并且它们的电池（人为导致）在特定一天耗尽，例如 1 月 31 日。能否在一天内完成如此多的非计划、或许是救命的设备更换手术？这当然取决于我们考虑的是哪个国家（有些国家应对得会比其他国家好），但这里存在许多合理的疑虑，因此为求简化，我们将说：当然不可能。

同时，这不仅仅是医疗服务的瘫痪。这里存在极高的致命风险。幸运的是，到目前为止，这个场景纯属假设。让我们希望这种情况不会改变。另一点是，该场景中描述的行为必须是蓄意的，绝对不是为了牟利：这样的人或人群会想要杀人。我们目前不知道有任何具有此类动机的网络犯罪分子或国家团体。那将是一种非常特定的意图。非常危险，有可能破坏政治和安全局势（更多内容见 [第 6 章](#ch6.xhtml) 和 [第 7 章](#ch7.xhtml)）。

然而，医疗设备网络安全不是开玩笑的话题。2017 年，FDA（食品药品监督管理局）宣布必须撤回 465,000 个起搏器，因为发现了一个严重的安全问题，可能允许恶意行为者耗尽电池（比预期更早）甚至强制起搏器产生某些副作用。

远程无线配置此类设备的能力对患者很有用，因为如果我们需要更新操作模式，不需要进行手术——我们可以远程完成。所以它很有用，尽管代价是增加了一些风险（正如前面提到的迪克·切尼的故事所示，对某些患者而言，这种风险是不可接受的）。

我们将以这些“乐观”的场景结束本章。我们将在关于关键基础设施和网络战的章节中重新探讨致命效应问题。

## 注释

1.  [见](#ch4.xhtml#R_en4_1)。[https://www.oxfordlearnersdictionaries.com/definition/english/infrastructure?q=infrastructure](https://www.oxfordlearnersdictionaries.com/definition/english/infrastructure?q=infrastructure)

2.  [欧洲议会和理事会关于协调公平获取和使用数据规则的法规提案（数据法案）第 15 条（“使用数据的特殊需求”）](#ch4.xhtml#R_en4_2)，[https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:52022PC0068&from=EN](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:52022PC0068&from=EN)

3.  [同上](#ch4.xhtml#R_en4_3)，第 15(a) 条。

4.  [英国卫生和社会护理部](#ch4.xhtml#R_en4_4)，《确保医疗和护理领域的网络韧性。2018 年 10 月进展更新》，[https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/747464/securing-cyber-resilience-in-health-and-care-september-2018-update.pdf](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/747464/securing-cyber-resilience-in-health-and-care-september-2018-update.pdf)

5.  [普华永道](#ch4.xhtml#R_en4_5)，《针对 HSE 的 Conti 网络攻击。独立事后事件审查》，2021.12.3，[https://www.hse.ie/eng/services/publications/conti-cyber-attack-on-the-hse-full-report.pdf](https://www.hse.ie/eng/services/publications/conti-cyber-attack-on-the-hse-full-report.pdf)

6.  [A. Vittorio](#ch4.xhtml#R_en4_6)，《默克公司 14 亿美元保险赔偿胜诉将网络风险与“战争行为”区分开来》，2022.01.19，[news.bloomberglaw.com/privacy-and-data-security/mercks-1-4-billion-insurance-win-splits-cyber-from-act-of-war](http://news.bloomberglaw.com/privacy-and-data-security/mercks-1-4-billion-insurance-win-splits-cyber-from-act-of-war)

7.  [L. Gisel](#ch4.xhtml#R_en4_7)，L. Olejnik，《网络行动潜在的人员伤亡代价》，日内瓦红十字国际委员会报告，2018。

8.  [Patel](#ch4.xhtml#R_en4_8)，Z.，Velankar，Y.，Trivedi，C.，& Oza，P. (2023)。无线植入式医疗设备安全与隐私：综述。载于《智慧能源与电力技术进展》（第 69–87 页）。Springer，新加坡。

9.  [Gasson](#ch4.xhtml#R_en4_9)，M. N. (2010, June)。人类增强：你会感染计算机病毒吗？载于 2010 年 *IEEE 国际技术与社会研讨会*（第 61–68 页）。IEEE。

10.  [Rieback](#ch4.xhtml#R_en4_10)，M. R.，Crispo，B.，& Tanenbaum，A. S. (2006, March)。你的猫感染计算机病毒了吗？载于*第四届 IEEE 国际普适计算与通信会议 (PERCOM’06)*（第 10-pp 页）。IEEE。

11.  [赛门铁克](#ch4.xhtml#R_en4_11)，《新的 Orangeworm 攻击组织针对美国、欧洲和亚洲的医疗保健行业》，2018 年 4 月 23 日，[https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/orangeworm-targets-healthcare-us-europe-asia](https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/orangeworm-targets-healthcare-us-europe-asia)

12.  [P.A](#ch4.xhtml#R_en4_12)。Williams，A.J. Woodward，《医疗设备中的网络安全漏洞：一个复杂的环境和多方面的问题》，“Medical Devices (Auckland, NZ)” 2015，第 8 卷，第 305 页；欧洲放射学会 (ESR)，《放射设备更新》，《Insights into Imaging》2014，第 5 卷，第 543–546 页。

