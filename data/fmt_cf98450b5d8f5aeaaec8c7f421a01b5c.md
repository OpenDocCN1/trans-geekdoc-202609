
例如，Gemma Services 旨在降低儿童出院时的病情严重度，从而降低其出院后第二年内再住院的可能性。利用这种方法，他们识别出精神科医生和临床医生可用于为每个不同青少年亚群体量身定制干预措施的具体服务、治疗和药物组合。

精准护理模型的优势在于，它减少了统计建模相关的问题；统计建模依赖集中趋势度量（即平均值），往往忽略轻度至重度的离群案例、少数群体案例，尤其是正态分布尾部的案例。

随着数据集增长和匹配群体数量增加，模型的精准度和公平性得到提升，使从业者能够生成更准确的建议，增加成功的可能性。此外，这种方法促进了准实验因果分析，并推动了对所有客户的公平治疗。

## 评估与影响

精准护理建模过程为每个区组匹配群体自动生成了准实验评估发现，使 Gemma Services 更好地理解了实现各群体可归因成功所需的细微差别。这使他们能够管理预期，并向付费方提出更有力的论据，以争取更多量身定制和个性化的解决方案。

尽管从业者一直都知道“一刀切”的方法行不通，但精准护理建模提供的证据为 Gemma Services 提供了所需的依据，使其能够主张采取更个性化的干预措施。他们利用这些证据为更精准、更定制化的解决方案争取资金，包括主张缩短标准化的住院时长。评估证据表明，坚持单一程序模式——该模式旨在推动总体平均水平的提升——并不适用于所有人，为了最大化成功率，需要采取针对性的干预措施并设置不同的住院时长。

除了提供更多针对特定群体的发现，说明实现群体特定可归因结果所需的条件外，精准护理建模过程还为所有层级的结果产生了更准确、更精确的评估发现，使员工能够对离群值、逆境突围者等进行更深入的定性调查。机器学习算法为每个儿童评估并生成了准实验因果评估结果，使服务提供方能够将所有获得所需服务并取得成功的儿童计为“可归因成功”。然而，还有其他三类结果：(1) 未获得所需服务但仍然成功的儿童（即所谓的“独立成功”案例）；(2) 获得了所需服务但未成功的儿童（即所谓的“未知需求”案例）；(3) 未获得其群体有效服务且未成功的儿童（即所谓的“未满足需求”案例）。每种结果类型中的儿童现在都可以由临床医生单独或集体地进行评估，以定性研究这些案例成为例外的原因。这包括临床医生之间、临床医生与家庭之间、以及临床医生与儿童之间的会面，以更深入地从定性上了解他们为何获得或未获得其群体的有效服务，以及为何成功或未成功。

通过精准分析建模过程识别出的这四种结果类型，分别代表了真阳性、真阴性、假阳性和假阴性的概念，这些概念是理解预测模型性能的基础（请参阅图 11.3 查看生成结果的屏幕截图）。

![Figure 11.3 Screenshot showing how EquIP identifies nonprofit service providers most proximate to deprived communities, sharing an evaluation of their financial health, determined by applying Precision Analytics.](img/fig11.3.jpg)

*图 11.3* 截图展示了 EquIP 如何识别最靠近弱势社区的非营利服务提供商，并分享其财务健康状况评估，该评估通过应用精准分析确定。

另一方面，假阳性（即未获得所需服务但仍成功的儿童）和假阴性（即获得了所需服务但未成功的儿童）代表了模型中的误差，即模型预测与实际结果不符。这些是从业者遇到现有数据无法充分解答的问题和假设的实例，凸显了当前数据收集过程中的缺口。因此，假阳性和假阴性表明，所收集的数据不够全面，无法完全支持其工作中所需的深度分析和决策制定（图 11.4）。

![Figure 11.4 Screenshot of an evaluation dashboard, presenting precision analytics results for each block-matched comparison group of program recipients, with probabilistic outcome results.](img/fig11.4.jpg)

*图 11.4* 评估仪表板截图，展示了每个区组匹配比较组的项目接受者的精准分析结果，包含概率结果。

因此，挑战不仅在于识别这些额外的数据变量（指标），还在于优化模型以减少这些误差。这就是机器学习算法的因果建模训练发挥作用的地方，它有助于识别具体案例进行评估、假设和得出结论，了解发生了什么、为什么发生以及如何发生。然而，假阳性和假阴性的存在也凸显了预测模型固有的局限性，以及持续针对真实结果进行优化和验证的必要性。

这一认识凸显了精准护理模型中数据需求的演变性质。随着项目主管、管理者和从业者更深入地研究案例，他们遇到了现有数据无法充分解答的问题和假设。这凸显了当前数据收集过程中的缺口，表明所收集的数据并不总是足够全面，无法完全支持其工作中所需的深度分析和决策制定。因此，明确需要进一步优化数据收集过程，纳入能更完整描绘案例全貌的额外数据变量。一旦添加了新的数据变量（指标），便能更稳健地检验假设，并最终做出更明智的决策和干预。

因此，要克服的挑战在于识别这些额外的数据点，并以有意义且实用的方式将其整合到现有的数据收集和分析框架中。如果没有机器学习算法的因果建模训练帮助识别这些具体案例以进行评估、假设和得出结论（了解发生了什么、为什么发生以及如何发生），这是不可能实现的。Gemma Services 利用项目管理和案例评估数据实施了精准护理模型，构建了因果、预测、处方和评估模型。这种方法生成了自动化的基于证据的（即因果）评估发现和准确的建议，从而提高了儿童亚群体成功的可能性。他们的系统已运行近三年。Gemma 分析了实施精准护理模型前后的住院时长和出院锐度数据。他们发现，每个儿童的住院时长减少了 30 天：住院护理费用为每月每名儿童 10,000 美元。

此外，Gemma 发现儿童的出院锐度下降了 40%；重要的是，Gemma 追踪每个儿童的纵向出院后数据，其分析证明出院锐度与儿童出院后在社区停留 12 个月高度相关。值得注意的是，这些精准护理模型实施前后的对比结果并不反映实验性评估发现，但它们确实作为从业者逐案使用精准护理模型获益的早期迹象（图 11.5）。

![Figure 11.5 Screenshot of up-to-date case-specific recommendations, determined through precision analytics, presenting practitioners with counterfactual evidence (i.e., “Success When Green” contrasted with “Success When Red”) for goals (attributes) that need to be addressed to improve the likelihood of the desired outcome (i.e., exit acuity less than 1.5). Note that names are fictional.](img/fig11.5.jpg)

*图 11.5* 通过精准分析确定的最新案例特定建议截图，向从业者展示了反事实证据（即，“绿色时成功”与“红色时成功”的对比），针对的是为提高期望结果（即出院敏锐度低于 1.5）的可能性而需要解决的目标（属性）。请注意姓名为虚构。

### 利用精准分析应用结构因果建模面临的挑战

尽管 Gemma Services 在实施精准护理模型方面取得了显著进展，但其应用引发了一个关键挑战：需要让受益人作为工具的使用者参与进来。目前，精准分析工具主要由从业者代表受益人使用。这意味着直接受益人——儿童及其家庭——尚未完全参与其中。Gemma Services 已认识到这一差距，并设定了让受益人直接参与使用精准学习工具的目标。其目的是使受益人能够积极参与解读输出结果，并规划优先事项以提高其成功的可能性 (York, 2021)。

然而，实现这一目标本身也面临一系列挑战。这不仅要求使工具对受益人易于获取且用户友好，还要求为他们提供必要的培训和支持，以有效使用这些工具。

此外，还涉及解决潜在的参与障碍，如缺乏技术访问条件、数字素养低或不愿接触数字工具。克服这些挑战对于充分实现精准护理模型的潜力至关重要，因为受益人自身最能从模型生成的洞察和建议中获益。

## 讨论

结构因果建模（SCM）与精准分析（PA）在社会影响项目评估中的融合，正如 Gemma Services 和公民企业援助计划（PACE）的案例研究所例证的那样，代表了项目评估领域的一项重大进展。这种融合有效应对了从大数据中得出有效因果推断的长期挑战，而大数据的特征往往是复杂的非实验性设置。

PACE 案例研究揭示了资源和支持向非营利组织的分配情况，特别是那些服务有色人种社区的组织。应用 SCM 和 PA 揭示了资源分配中的差异，提供了一种数据驱动的方法来理解和解决这些不公平现象。

在 Gemma Services 的背景下，精准护理模型使人们能够细致地理解治疗对不同儿童亚群体的效应。在此背景下使用 SCM 使得治疗方法更加个性化，考虑了每个亚群体的独特特征和需求。这种方法展示了从“一刀切”解决方案的转变，承认了治疗需求的复杂性和个体性。

尽管取得了这些进展，仍必须承认一些局限性。一个显著的局限是依赖可用数据，这些数据可能并不总是全面或具有代表性。这一局限凸显了持续改进数据收集方法的必要性，以确保数据充分捕捉所研究社会现象的复杂性。另一个局限是潜在的算法偏见。虽然 SCM 和 PA 提供了强大的分析工具，且这些方法控制了选择偏差，但它们并不免疫于数据固有的偏见。这引发了应对这些模型可能延续现有不公平现象的潜在风险的必要性，特别是在社会项目评估的背景下使用时。

未来的研究应侧重于解决这些局限性，特别是通过开发更稳健的数据收集方法和探索减轻算法偏见的途径。此外，还需要更多将 SCM 和 PA 应用于不同背景下的研究，以进一步验证和完善这些方法。

也就是说，SCM 和 PA 的融合代表了项目评估领域的一项重大贡献。它提供了一种更严谨、更细致的方法来理解社会项目中的因果关系，从而为项目改进提供更准确、更可操作的洞察。这种方法对政策制定也有影响，因为它为决策提供了更稳健的证据基础。通过阐明项目结果背后的因果机制，SCM 和 PA 使政策制定者和从业者能够设计更有效、更公平的干预措施。

虽然 SCM 和 PA 在项目评估中的融合标志着一个重要的进步，但继续探索和应对已识别的挑战至关重要。这将确保这些方法被负责任且有效地使用，以改进社会影响项目，并为建设一个更公平的社会做出贡献。

## 结论

总之，本文全面探讨了利用精准分析（PA）应用结构因果建模（SCM）的情况，特别关注了两个案例研究：Gemma Services 和公民企业援助计划（PACE）。利用 PA 的 SCM 展示了其彻底改变社会影响项目评估的潜力，提供实时、按需和个性化的洞察，可指导决策过程并改善结果。

Gemma Services 实施的精准护理模型利用项目管理和案例评估数据构建因果、预测、处方和评估模型，展示了该方法生成自动化、循证评估发现和准确建议的潜力。这反过来又提高了儿童亚群体成功的可能性。

公民企业援助计划（PACE）研究提供了几项关键收益。首先，它为非营利组织之间资源和支持的分配提供了关键洞察，特别是那些服务有色人种社区的组织。通过应用结构因果建模（SCM）和精准分析（PA），该研究为当地资助者揭示了资源分配中的差异，突出了可通过更有针对性的外展和拨款来改善公平性的领域。这种方法使人们能够以更数据驱动的方式理解这些不公平现象，指导更有效、更公平的政策决策。

然而，案例研究也凸显了若干挑战，包括需要额外的数据点来检验当前数据无法回答的假设，以及需要加强受益人使用精准学习工具的参与度。克服这些挑战对于充分实现精准护理模型的潜力至关重要。这些案例研究的发现凸显了 SCM 和 PA 改变社会影响项目评估的潜力。然而，它们也突显了持续完善这些模型的必要性以及应对已识别挑战的重要性。随着我们不断前进，继续探索和应对这些挑战对于充分利用基于大数据驱动的 SCM 评估的力量至关重要。

## 参考文献

1. Fan, J., Han, F., & Liu, H. (2014). Challenges of Big Data Analysis. *National Science Review*, *1*(2), 293–314. [`doi.org/10.1093/nsr/nwt03`](https://doi.org/10.1093/nsr/nwt03)

2. Gay, K. E., & York, P. (2018, February). A New Way to Use Data: Precision Care for Better Outcomes in Psychiatric Residential Treatment for Children. Retrieved from Scattergood Foundation: [`www.scattergoodfoundation.org/wp-content/uploads/2018/02/A-New-Way-to-Use-Data.pdf`](https://www.scattergoodfoundation.org/wp-content/uploads/2018/02/A-New-Way-to-Use-Data.pdf)

3. Knighton, A. J., Savitz, L., Belnap, T., Stephenson, B., & VanDerslice, J. (2016). Introduction of an Area Deprivation Index Measuring Patient Socioeconomic Status in an Integrated Health System: Implications for Population Health. *The Journal for Electronic Health Data and Methods*. [`doi.org/10.13063/2327-9214.1238`](https://doi.org/10.13063/2327-9214.1238)

4. Madhanagopal, B., Amrhein, J., & McDougall Scientific Ltd. (2019). Analyzing Structural Causal Models Using the CALIS Procedure. Retrieved from SAS: [`support.sas.com/resources/papers/proceedings19/3240-2019.pdf`](https://support.sas.com/resources/papers/proceedings19/3240-2019.pdf)

5. Pearl, J. (2010). Causal Inference. *Proceedings of Workshop on Causality: Objectives and Assessment at NIPS 2008*, (pp. 39–58).

6. Program to Aid Citizen Enterprise. (2021). The Health of the Nonprofit Sector in Western Pennsylvania. Retrieved from Pittsburgh Black Media Federation: [`pbmf.org/wp-content/uploads/2021/01/PACENonprofitEffectivenessstudyFINAL12.9.20-1.pdf`](https://pbmf.org/wp-content/uploads/2021/01/PACENonprofitEffectivenessstudyFINAL12.9.20-1.pdf)

7. Spitzer, S., & Weber, D. (2019). Reporting biases in self-assessed physical and cognitive health status of older Europeans. *PloS One*, *14*(10), e0223526. [`doi.org/10.1371/journal.pone.0223526`](https://doi.org/10.1371/journal.pone.0223526)

8. York, P. (2021, July). Unlocking Real-Time Evidence for Practitioners: How Evaluation and Data Analytics Are Generating *On-Demand,* *Actionable Evidence for Front-Line Practitioners at First Place for Youth and Gemma Services.* Retrieved from Project Evident: [`projectevident.org/wp-content/uploads/2022/09/FPFY-GemmaActionableEvidenceCaseStudyJuly21.pdf`](https://projectevident.org/wp-content/uploads/2022/09/FPFY-GemmaActionableEvidenceCaseStudyJuly21.pdf)

# 12 政策与社会的算法化：对实在论评估方法的需求

Frans L. Leeuw

DOI: [`10.4324/9781003512493-12`](https://doi.org/10.4324/9781003512493-12)

本章已根据 CC-BY-NC-ND 4.0 许可提供。

## 引言

纵观本书各章的贡献，呈现出这样一幅图景：人工智能（AI）不仅在各个专业研究领域站稳了脚跟，也已渗透到组织中，在这些组织中进行着决策制定、政策、项目、干预、法规、疗法、药物及法律安排的开发与实施。
