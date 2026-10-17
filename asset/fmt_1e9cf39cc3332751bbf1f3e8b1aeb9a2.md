
一个导致缺乏正式过程模型的原因是 DF 作为科学学科的相对新近加入，相比传统法医学（Cohen, 2012）而言，其发展时间较短。传统法医学与其基本的生物学学科共同发展了数十年（Beebe and Clark, 2005；Palmer, 2001），而 DF 科学仍在形成之中，因此在计算机科学（CS）这一更成熟的基础学科面前落后很多（Montasari, 2016a；Beebe and Clark, 2005；Carrier and Spafford, 2003）。DF 学科的发展缺乏初始研究，未能提供必要的、全面的科学基础（Valjarevic and Venter, 2015；US-CERT, 2012；Peisert *et al*., 2008；Meyers and Rogers, 2004；Carrier, 2002）。美国计算机应急响应团队（US-CERT, 2012）指出：“由于计算机取证是新兴学科，法院和行业之间缺乏标准化和一致性。” Meyers and Rogers (2004) 则持更强硬观点，警告 DF 被视为“垃圾科学”，原因是缺乏认证、标准或同行评审的方法（Meyers and Rogers, 2004）。同样，Carrier (2002) 强调，由于缺乏普遍认可的标准和程序，DF 作为科学的可行性受到质疑。导致 DIP 缺乏正式模型的另一原因是模型作者采用“临时”方式，未能运用科学方法进行开发（Montasari, 2017a；Montasari, 2016a；Montasari, 2016b；Montasari, 2016c；Montasari *et al*., 2015；Agarwal *et al*., 2011）。

以往的模型通常由从事实践的非科学家开发，这些模型基于个人经验，且是临时性地构建的（Montasari, 2016a；Montasari *et al*., 2015；Valjarevic and Venter, 2015；Agarwal *et al*., 2011；Montasari, 2016c）。正如 Karyda and Mitrou (2007) 所指出的，使用临时方法和工具提取数字证据会削弱其可靠性和可信度。正如同一问题被 Reith *et al*. (2002) 所强调的那样：“这是因为证据必须使用经过验证、能够可靠提取和分析数据且不受偏见或篡改的方法获得。” Beebe and Clark (2005) 进一步指出，只有在 DFIPM 中采用“正式”和“科学”的方法才能实现严谨性，而 Solomon *et al*. (2011) 则认为当前的程序和工具不应被误认为是一致的调查过程。后者指出：“工具和程序是基于执法经验和系统管理员的经验临时开发的，而非来自科学界，传统法医学也从中汲取方法论。” (Solomon *et al*., 2011)。

因此，以临时方式开发以往模型导致了多种过程模型的出现，这些模型在阶段、活动和术语上相互冲突，进而阻碍了法院和调查人员所需的正式流程的建立（Montasari *et al*., 2015；Agarwal *et al*., 2011）。结果是，许多研究者呼吁对 DIP 采用科学方法和正式手段（Cohen, 2012；Carlton and Worthley, 2009；Garfinkel *et al*., 2009；Pollitt, 2009；Leigland and Krings, 2004）。现有模型的另一问题在于它们倾向于专注于 DF 的某一特定领域，忽视了其他环境（Montasari, 2016a；Montasari, 2016b；Montasari *et al*., 2015）。与其他法医实践领域不同，DFPs 活跃于多个领域（Freiling and Schwittay, 2007；Beebe and Clark, 2005；Ciardhuáin, 2004；Carrier and Spafford, 2003）。Carrier and Spafford (2003) 认为，“模型必须抽象，适用于执法调查、商业调查以及事件响应。” 然而，以往的模型往往只聚焦于单一领域，如执法、商业或事件响应（Montasari, 2016a；Montasari, 2016b；Adams, 2012；Pollitt, 2009），未能考虑不同领域的需求，导致无法形成适用于 DF 各个领域的通用模型（Montasari, 2016a；Montasari, 2016b；Montasari *et al*., 2015）。

第三个重要问题在于以往的模型不够全面，未能覆盖整个 DIP。Beebe and Clark (2005) 认为，需要一个更全面且被普遍接受的框架，以提升科学严谨性，并促进教育、应用和研究。同样，Ciardhuáin (2004) 表示：“完整的网络犯罪调查模型对于标准化术语、定义要求以及支持新技术和工具的研发至关重要。”

#### 9.1.1 Research problem

上述考虑在 Montasari 的 \[3\] 研究中被组织为以下研究问题：

*不存在一套涵盖整个数字取证过程的完整、正式模型，该模型能够帮助法院判断所遵循的取证过程的可靠性，并且该模型具有通用性，可在执法、商业和事件响应等不同领域中应用。*

为解决上述研究问题，Montasari（2016a）开发了一个全面的模型——综合数字取证调查过程模型（CDFIPM），而标准化数字取证调查过程模型（SDFIPM）则构成了该模型的中间部分。CDFIPM 涵盖整个 DIP，其形式化体现在综合、调和和扩展现有模型的同时，也具备通用性，可在法律执法、商业和事件响应等不同领域应用。本研究的重点仅限于 CDFIPM 的中间部分，即拟议的 SDFIPM。为此，我们首先在展示与评估活动之前介绍并讨论 SDFIPM。

#### 9.1.2 Structure of the paper

本文其余部分的结构如下：第 9.2 节 提供对前 DFIPMs 的背景概述。第 9.3 节 讨论研究方法，而 第 9.4 节 则提供拟议模型的概览。第 9.5 节 讨论 Demonstration 活动，即在案例研究中应用 SDFIPM 并对模型进行逐步演示。第 9.6 节 描述 Evaluation Process，通过该过程对 SDFIPM 进行来自法医学、商业和事件响应三大领域的领先专家的外部独立评估。最后，在 第 9.7 节 中，文章得出结论，阐述研究贡献，并讨论未来工作。

### 9.2 Background to the Previous DFIPMs

在设计和开发 SDFIPM 之前，我们对前序模型进行了批判性审查，并依据三套评估标准（Montasari, 2016a）对每个模型进行评估，包括：Daubert Test（Farrell, 1993）的五点要求、Carrier 和 Spafford（2003）的五点要求以及 Beebe 和 Clark（2005）的四点要求。此次批判性分析的目标是深入了解前序模型，并确定哪些模型可为拟议模型提供贡献。由于本研究聚焦于法医学、商业和事件响应三个环境，我们选取在这些领域内最符合评估标准的前序模型，以评估其对新模型的潜在贡献。Adams（2012）采用了类似的方法，即将前 DFIPMs 与 Daubert Test 及 Carrier‑Spafford 五点要求进行评估。

我们对前序 DFIPMs 的评估被认为是重要的（Kohn *et al*., 2013; Cohen, 2012; Cohen, 2010），因为任何通过后续学术讨论和实际使用制度化的模型，都必须考虑其他研究者的观点、方法和“专业术语”。经过对前序模型的批判性审查与评估（Montasari, 2016a; Montasari, 2016c; Montasari, 2016e），我们发现这些模型往往是基于其开发者个人经验、临时性地构建的，且未考虑如何在该领域建立标准化（Valjarevic and Venter, 2015）。此外，这种做法阻碍了法院急需的正式流程的建立（Montasari, 2016a; Montasari *et al*., 2015）。正如 表 9.1（Montasari *et al*., 2015）清楚显示的，前序 DFIPMs 在阶段数量、覆盖范围和针对的具体领域上存在显著差异。因此，这些模型常被批评为过于具体（Carrier and Spafford, 2003; Reith *et al*., 2002）、过于抽象（Beebe and Clark, 2005）、过于宽泛（Rogers *et al*., 2006）、过于技术化（Venter, 2006）以及过于复杂（Selamat *et al*., 2008）。因此，拟议模型旨在解决前序模型的不足。实现本模型可立即为 DFPs（数字取证专家）和法院提供价值。

### 9.3 Research Methodology

本研究采用了信息系统（IS）领域广泛采用的设计科学研究（DSR）方法论（Hevner and Chatterjee, 2010; Peffers *et al*., 2006; Hevner *et al*., 2004; March and Smith, 1995; Walls *et al*., 1992; Nunamaker *et al*., 1990），其核心目标是通过构建并应用设计 artefact（Van Aken, 2005; Hevner *et al*., 2004）来获得或发展对问题域的知识与理解。DSR 包括设计创新 artefact 以及分析其性能或使用情况（Watts *et al*., 2009; Kuechler and Vaishnavi, 2008），而 artefact 的开发与评估是 DSR 的重要组成部分（Hevner *et al*., 2004; March and Storey, 2008）。artefact 包括模型、方法、构造、实例化以及设计理论（March and Storey, 2008; March and Smith, 1995），以及社会创新和技术、社会或信息资源的新颖或未知属性（March and Storey, 2008）。本研究涉及的 artefact 是全新的模型——SDFIPM，它涵盖了更大模型 CDFIPM 的中间部分。研究的组织背景为法医学、商业和事件响应。我们的研究还解决了一个尚未得到解决的问题：目前不存在一套正式的 DFIPM，该模型能够综合、调和并扩展现有模型，并且具备通用性，可在法医学、事件响应和商业领域使用。本文采用 DSR 方法论的原因在于 Adams（2012）最初将其应用于 DF 研究。

相较于 grounded theory（GT）或 requirements engineering（RE）等其他方法论，选择 DSR 是因为其在设计与新过程模型后续评估方面的适用性。本研究的核心任务是设计、开发并评估 SDFIPM，因而 DSR 被视为最合适的选择。与解释性科学研究（ESR）方法相比，DSR 更具实用性，且能够解决尚未有解决方案的问题（Peffers *et al*., 2006; Hevner *et al*., 2004）。因此，作为以问题为导向的研究，DSR 再次被认定为最佳方法论。此外，DSR 同时运用归纳与演绎两种推理过程。我们的原始研究（即本论文来源）旨在通过归纳过程产生新知识与文献，并通过演绎过程检验两项研究假设，故 DSR 再次是最合适的选择。

- 各种研究者（无论是在信息系统领域内还是外）都提供了定义 DSR 的指导，并描述了在其生产中应遵循的目标（Hevner 和 Chatterjee, 2010; Peffers *et al*., 2006; Hevner *et al*., 2004; Vaishnavi 和 Kuechler, 2004; Adams 和 Courtney, 2004; Rossi 和 Sein, 2003; March 和 Smith, 1995; Walls *et al*., 1992; Eekels 和 Roozenburg, 1991; Nunamaker *et al*., 1990; Takeda *et al*., 1990; Archer, 1984）。这些研究者经常提出各种方法、流程或理论框架，以合理化 DSR 研究。然而，本研究选择 Peffers *et al*. (2006) 提出的设计科学研究过程 (DSRP) 模型作为合适的 DSR 方法论。其原因在于该模型提供了概念过程的图形化表示，适用于执行和展示 DSR。这种心理模型有助于促进 DSR 的应用，也能够帮助作者制作并展示高质量、严谨且可发表于数字取证科学领域的 DSR（Montasari, 2018; Montasari, 2016a）。

Peffers *et al*. (2006) 的 DSRP 包含六个组成部分，如图 [Fig. 9.1] 所示。本章节其余部分简要讨论我们如何将这六个组成部分应用于本研究。关于 DSRP 在本研究中的应用细节，请参见 Montasari 的研究（Montasari, 2016a）。

![image](img/fig9.1.jpg)

**Fig. 9.1.** 经 Peffers et al. (2006) 修订的设计科学研究过程 (DSRP) 模型。

#### Activity 1 — 问题识别与动机

通过对以往 DFIPMs 相关文献的详细分析与评估，我们获得了对本研究所针对的问题的深刻理解。基于文献综述得出的结论，我们能够提出本研究旨在解决的研究问题。与其他专家的互动以及我们在数字取证领域的经验，也为阐明所述问题提供了洞见。

#### Activity 2 — 解决方案的目标

研究目标是依据问题定义而制定的。Peffers *et al*. (2006) 指出，目标应理性地从问题规格中推导出来。因此，为了制定所述目标，我们深入了解了问题的现状及其当前解决方案，即先前提出的 DFIPMs 及其有效性。

#### Activity 3 — 设计与开发

在设计和开发 SDFIPM 之前，我们对所有先前的 DFIPMs 进行了批判性审查，并依据三组评估标准对其进行评估，以确定哪些可以为新模型提供贡献。本研究聚焦于执法、商业和事件响应三个环境。因此，我们考虑了这三个领域内的先前模型，以评估其可能对新模型的贡献。一旦确定了最可靠的模型，我们就确定了其具体的关键贡献，以便将其纳入新模型。随后，我们从这些关键贡献中识别出构建新模型所必需的基本组件，这些组件构成了 SDFIPM 的基础结构。我们在此基础上，通过构建一套面向特定领域的新组件，对现有模型进行扩展。前面的模型中识别出的组件促成了新模型的发展，同时新构建的组件也发挥了作用。SDFIPM 以 UML 活动图的形式进行了图形化表示。

我们已经将 DSRP 的前三个组成部分应用于本研究（Montasari, 2016a），本章节聚焦于剩余的三个组成部分，即演示、评估和沟通活动。下面的章节描述了我们如何将这些要素应用于本研究。

#### Activity 4 — 演示

在完成 SDFIPM 的设计与开发后，需要依据 DSRP 的演示活动，在适当的环境中展示其实施情况。Peffers *et al*. (2006) 建议使用案例研究作为合适的演示环境。该领域的其他研究者（Valjarevic 和 Venter, 2015; Casey, 2011; Beebe 和 Clark, 2005; Carrier 和 Spafford, 2003; Ciardhuáin, 2004）也使用案例研究作为模型适用性的合适环境。我们选择了涵盖执法、商业和事件响应三个领域的案例研究，作为测试拟议模型的合适环境。因此，我们将在 第 9.5 节 中将 SDFIPM 应用于所选案例，以展示其在上述三个领域中的应用和有效性。我们认为此活动很重要，因为它能够在向外部独立专家提交模型进行正式评估之前，发现模型的不足之处。同时，这也能避免占用外部审稿人的时间。演示活动的结果将决定是否需要在设计与开发阶段重复，以便进行相应的修改。

#### Activity 5 — 评估

根据 DSRP 的要求，SDFIPM 还需要进行评估，以判断其如何支持对所述问题的解决。本研究的评估活动将比较 SDFIPM 的应用和效果与研究问题中设定的特征。评估活动在 第 9.6 节 中进行，涉及将 SDFIPM 提交给本研究重点领域的三个 DFPs（即执法、商业和事件响应），以及提交给法官、律师和学术界的研究人员。此类做法旨在获取权威外部审稿人对 SDFIPM 有效性的深入且可靠的反馈。与演示阶段类似，评估完成后，我们将判断是否需要重复设计与开发阶段以进行改进。任何此类修改随后都将纳入 SDFIPM 的设计与开发阶段。

#### Activity 6 — 沟通

再次遵循 DSRP 的要求，本研究所针对的问题、其重要性、解决方案（SDFIPM）、实用性和创新性、设计与实现的严谨性以及效果，都必须向目标用户社区进行沟通。本研究的沟通活动已通过在知名同行评审期刊和会议上发表论文、以及参加各类会议、数字取证展览和网络安全峰会来实现。此外，我们计划继续发表论文，并主动与广泛的专家群体（包括 DFPs、法律实践者和学术界专家）进行直接交流，以传达我们所提议模型的重要性。

### 9.4 Overview of the SDFIPM

SDFIPM 采用自上而下的方法设计，以便 DFPs 能更好地洞察其组成部分，即 Processes、Phases 和 Sub-Phases。模型包含七个 Processes，每个 Process 包含不同数量的 Phases。每个 Process 提供额外的更低层次细节，即 Phases 和 Sub-Phases。Figures 9.2 和 9.3 代表了 SDFIPM 形式化表示的首次实例，即 UML 活动图，它们的组合构成了整个模型。由于模型的设计与开发阶段已在 Montasari (2016a) 中详细阐述，以下小节仅提供模型的简要概述。

![image](img/fig9.2.jpg)

**Fig. 9.2.** 检查、分析、解释、事件重构和报告过程。
