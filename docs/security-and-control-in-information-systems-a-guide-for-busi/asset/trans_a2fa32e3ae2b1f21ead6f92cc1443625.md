

内部审计人员长期以来一直被其他员工持怀疑态度，被认为具有“执法”角色，尤其是在查处欺诈方面。然而，一本权威教材（Venables and Impey [1991](#reference.xhtml#ref_r230)）认为他们至少还应承担另外四项责任：

* 防止和发现错误；
* 消除浪费（源于规划和控制不善、资产缺乏维护等原因）；
* 确保管理报告基于准确可靠的信息；
* 检查是否遵守相关法律法规。

内部审计人员不能期望在所有这些领域运作而不侵入他人的职责范围。例如，管理会计师负责生成报告，而大多数经理认为消除浪费是他们的责任，特别是如果他们从事运营管理或质量保证等领域。良好的内部审计建立在各方之间的协作意识之上，只有当事情严重脱轨时，审计人员才会采取更对抗的立场。上述责任清单中的一个有趣特点是，它们都涉及对信息系统完整性和安全性进行核查的要求。因此，`computer` 审计员的角色在这里自然契合。

计算在内部和外部审计中的作用总结于 [Figure 11.1](#ch11.xhtml#fig11_1)。正如 [Figure 11.1](#ch11.xhtml#fig11_1) 所暗示的那样，计算机审计员将成为与外部审计公司 IS 专家联系的有用渠道。她能够协助从系统中提取数据，代表外部审计师运行测试，并查找他们所需的任何技术文档（如程序流程图）。如果组织运行的系统在国际上运作，她还应能够提供网络的协调视图，以及适用于国家边界的任何自动化控制。许多外部审计公司还设有咨询部门，渴望帮助实施新的控制和对策。这会引发微妙的伦理问题，即审计是否被用作咨询业务的“钓鱼之旅”。同样，审计员的专业知识可能有助于判断此类咨询是否有用。

![Figure 11.1 ](images/fig11_1_B.jpg)

[Figure 11.1 ](#ch11.xhtml#R_fig11_1)

## 11.2 系统开发的审计

定制或“量身定制”软件的衰落曾被多次预测，尤其是由打包解决方案供应商提出，但仍有许多情况企业更愿意选择这种方式。例如，政府部门可能必须根据该国独有的规则和立法实施系统，或企业可能为自己设定创造独特服务以超越竞争对手的目标。定制软件通常规模庞大，对组织的一项或多项核心活动至关重要。因此，关于其可审计性以及应设计其中的控制机制的问题，最好在早期阶段就进行讨论。

关于计算机审计员是否应参与这些早期阶段，可以有两种不同的观点。一方面，早期参与应确保所有适当的控制作为基本设计的一部分被纳入，而不必以后作为事后考虑“临时加上”。由于任何增添和更改往往随着软件项目进入后期阶段而变得越来越昂贵，这表明计算机审计员的早期干预应有助于降低开发成本。另一方面，如果审计员与项目过于密切地参与，她可能很难保持独立性和公正性。她可能会发现开发团队的态度影响了她：例如，团队可能非常重视满足截止日期，从而形成一种风险更可能被接受、走捷径的氛围。

对美国一家领先公司内部审计人员的调查表明，让他们在项目中担任“参与性”角色显著提高了他们的工作满意度（Allen [1996](#reference.xhtml#ref_r4)）。这种对“亲手操作”角色的享受同样可能适用于计算机审计员。然而，在积极参与设计和开发的过程中，他们在后期探究系统弱点时失去客观性的真实危险尤其存在，特别是如果内置控制的质量或适用性受到质疑。

无论计算机审计员的参与程度如何，其范围都必须在开始时明确界定，并由所有相关方达成一致。Mitchell（[1995](#reference.xhtml#ref_r174)）建议将项目分为四个等级，其中最低等级表示敏感性低的项目，几乎不需要或不需要审计人员参与，而最高等级则意味着定期且持续的参与。在后一种情况下，应做出决定，计算机审计员应参加哪些会议，应将其列入哪些传阅名单，等等。

还应就开发的哪些方面应纳入计算机审计员的职权范围达成一致。可能的责任领域清单列于 [Table 11.1](#ch11.xhtml#table11_1)。

[Table 11.1 Computer Auditor Responsibilities During System Development Life Cycle (SDLC)](#ch11.xhtml#R_table11_1)

| SDLC stage | | Areas of involvement for computer auditor |
| --- | --- | --- |
| Initiation | | Review security needs, investigate alternatives, and prepare proposals for preferred alternative |
| Requirement specification | | Provide definition of security requirements, determine how quality assurance is to be applied to the development of security features |
| Design | | Specify security features in more detail, and suggest methods for testing their effectiveness |
| Construction | | Assist in developing software features, oversee initial testing, and ensure that features are properly integrated with the rest of the software |
| Implementation and testing | | Carry out final tests on security features in individual modules and in the integrated system. Ensure that all security and control measures are fully documented |

## 11.3 非传统方法：软件包和终端用户计算

对于内部软件开发，计算机审计员至少有参与可能影响安全的设计和编码决策的选择。然而，软件行业最近的发展却合力剥夺了这一选择。相反，计算机审计员不得不从较远的距离进行评估，而且不总是从一个很好的观察点进行。

在极端情况下，存在商业化软件包的“接受或放弃”性质。这些软件包可能声称包含访问控制、备份生成、文件和消息加密等功能。核实这些声明极其困难，因为大多数供应商将产品的最内在细节视为专有。计算机审计员将无法检查源代码，因为产品将以“目标”代码形式交付，可直接在机器上运行。同样，也不会有程序流程图可供参考，除非是为营销目的制作的、非常肤浅的少数图表。

