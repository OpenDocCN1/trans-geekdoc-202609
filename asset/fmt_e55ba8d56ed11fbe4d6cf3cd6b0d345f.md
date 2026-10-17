
机器学习日益应用于放射学、心脏病学、肿瘤学和眼科等领域，以提高准确性促进疾病的早期检测。许多研究使用了监督机器学习方法，包括决策树、逻辑回归、支持向量机（SVMs）、梯度提升、最小绝对收缩选择算子（LASSO）和 AdaBoost [45]。

逻辑回归可以视为线性回归的扩展，如图 8.2b 所示。使用线性关系建模的数据允许根据给定的输入进行预测，如图 8.2a 所示。逻辑回归使用称为逻辑函数的非线性函数，该函数根据阈值将预测值转换为二值结果。LASSO 等技术有助于识别与结果最相关的较小预测变量子集，增强敏感性和泛化能力。

在分类任务中，支持向量机（SVMs）是另一种广泛使用的机器学习模型。它创建一个边界（如图 8.2c 所示），将输入数据分为两个不同的类别，然后可以用于分类新的数据点 [44, 45]。

一种关键的监督学习方法是决策树，如图 8.2d 所示。该树有一个根节点，代表基于预测变量的主要决策点。每个分支节点反映与特定输入变量相关的条件，随着更多输入变量的加入，模型的预测能力随之增强。

集成方法通常用于通过多种机器学习方法来提高预测模型的性能。图 8.2e 展示了用于知识挖掘的流行的机器学习进展。

## 8.2 图表

(a) 数据 1 数据 2 数据 3 收集

| 选择 提取 | LR, SVM, DT, KNN, XGBoost, AdaBoost... | 分析学科 预测结果 寻找材料 ... |

| :--- | :--- | :--- |

| 数据 n | 特征工程 模型选择 模型 应用 | |

(b)

![](img/f8941e254c6ef784f42eac13646de555_172_0.png)

(c)

![](img/f8941e254c6ef784f42eac13646de555_172_1.png)

(d)

(e)

![](img/f8941e254c6ef784f42eac13646de555_172_2.png)

图 8.2 机器学习模型插图。8.2a. 线性回归；8.2b. 逻辑回归；8.2c. 支持向量机；8.2d. 分类与回归树 (CART)；8.2e. 集成方法。

集成技术：自助聚合（bagging）和提升（boosting）。在 bagging 中，从原始数据集中随机选择若干个数据子集，每个子集训练一个不同的预测模型。最终预测由所有模型聚合而成。随机森林是结合了 和决策树的集成方法示例。Boosting 涉及结合多个模型以获得更准确的预测，通常通过 AdaBoost 和梯度提升等技术实现 [45]。

## 8.5 评估总结

医院的电子健康记录（EMRs）具有许多优势。它们不仅减少了与手写笔记相关的临床错误，还创建了无纸化环境，促进了医疗提供者之间的无缝数据交换。该系统提供了对患者病史的即时访问，这在专家位置较远的咨询期间可能关关 [46]。

其他益处还包括消除信誉问题、更快的计费流程以及易于检索的高质量数据存储。EMRs 支持护理，使患者和医疗机构受益。这项技术为管理日常运营提供了一个高效平台。

凸显 EMR 系统有效性的关键优势包括增强循证决策能力、改进护理团队之间的沟通、简化慢性病管理、提高患者安全以及及时干预。这些益处结合大量的先前的研究，证明了 EMRs 的有效性以及它们在与健康记录管理（HRM）系统集成时的重大影响。

## 8.6 通过使用 AI 增强电子健康记录

许多人错误地认为，大型集成医疗服务网络中的电子健康记录（EHR）系统是单一、不灵活的、难以使用且实施成本高贵的。这些系统通常由商业供应商提供，实施、支持和优化这些系统的过程需要大量的时间、资金和咨询支持 [45, 46]。

最常用的系统建立在日益过时的技术之上，这损害了它们的可用性 [47]。与医疗提供者首选的护理流程不匹配的情况并不罕见。临床医生（包括像 Atul Gawande 这样的知名人物）经常发现这些系统复杂且难以导航。

随着医疗网络的扩大，确保全面的 EHR 平台能够真正帮助那些难以有效捕捉其工作流的临床医生正成为一个重大挑战。EHR 通常捕获所有相关的临床医生信息或使其易于访问 [48]。临床医生的角色不仅限于临床专业知识，还包括对护理流程、患者环境和管理方法的了解。此外，美国监管、计费和收入周期的复杂性减少了临床医生与患者接触的时间。

解决 EHR 系统与临床流程之间的不匹配问题面临着若干挑战。一种潜在的解决方案是从零开始开发 EHR 系统，使其更加集成和精简化 [47, 48]。例如，在全美 40 个城市运营的家政式诊疗机构 One Medical 创建了了与其护理和患者关系紧密结合的自己的 EHR 系统。同样，罗氏（Roche）对 Flatiron Health 的收购包含了一个适用于肿瘤护理的 Web 端 EHR，增强了其 OnCloud 平台。

虽然这些定制系统可能更符合临床工作流，但它们的开发是劳动密集型且耗时的（据报道 One Medical 花了十年时间创建其系统），并且其运行范围通常有限。对于较大的医疗网络来说，从头构建系统或对商用系统进行大幅定制以满足特定需求可能并不是一个切行的方案 [49]。

## 机器学习在知识挖掘领域的进展

另一种方法是使用开源的电子健康记录（EHR）系统。然而，许多此类系统是为规模较小的临床诊所设计的，这限制了它们的扩展性，并需要大量的定制。虽然软件可能是免费的，但仍需要大量的编程和数据基础设施工作来适应每个独特的医疗实践。此外，与商用对应产品相比，开源 EHR 在更新和维护方面的优先级较低，这使得它们更容易迅速变得过时。监管标准和报销政策也可能发生快速变化，为依赖开源或内部开发系统的组织带来了合规性和财务层面的挑战 [50]。

一种很有前景的方法是利用人工智能（AI）来增强现有的 EHR 系统，使其更具适应性和智能化。一些医疗服务网络已经开始与 EHR 供应商合作，共同探索 AI 的能力。尽管目前 AI 在 EHR 中的功能仍然有限，但我们可以预计该领域将取得重大进展。

例如：

Google 正在与医疗服务网络合作，利用大数据开发预测模型，以提醒医生注意败血症和心力衰竭等高风险状况。包括 Google 和 Enlitic 在内的初创公司也致力于 AI 驱动的解释算法。Jviron 提供了一种“临床成功机器”，可以识别可能对特定治疗产生积极反应的患者以及高风险的患者。将此类工具与 EHR 集成可以显著增强决策支持能力 [49, 50]。

## 8.7 临床决策辅助

在过去，决策支持系统主要依赖基于规则的方法来为治疗方案提供建议。然而，来自 IBM Watson、Change Healthcare 和 AllScripts 等供应商的机器学习解决方案正在层涌而出，能够根据最新数据提供更个性化的护理 [51]。

虽然人工智能目前正在增强电子健康记录（EHR）系统中的数据检索和提取，但它在改进用户体验方面潜力巨大。由于其复杂性，EHR 通常被视为繁琐的导致医生职业倦怠的因素之一。目前，定制 EHR 以使其更易于使用在很大程度上是一个手动过程，这些系统的负担可能会阻碍改进。人工智能，特别是机器学习，具有帮助 EHR 适应用户偏好的潜力，这可能提高临床结果和医生的生活质量 [52]。

为了让这些进展真正产生效益，电子健康数据的无缝集成至关重要。大多数现有的 AI 解决方案是独立服务，无法提供与集成方案相同的价值。它们要求医生学习新的界面，增加了他们的工作负载。然而，EHR 供应商（如 Epic、Cerner、AllScripts 和 Athena）开始将 AI 能力整合到其系统中。这种集成将促进用户友好的界面、更易访问相关数据以及许多其他益处，尽管实施过程可能需要时间。

未来的 EHR 开发还应考虑远程医疗技术的整合。例如，One Medical 的 EHR 整合了血糖仪和血压监测仪等家用设备，这些设备可以自动传输数据。随着医疗成本的增加和对新交付方法的探索，像 Hexokin 监测心血管指标的智能衬衫在临床研究和家庭监测中变得越来越流行。此外，随着医疗保健向以患者为中心的护理和自我管理转变，患者报告结局和个人健康记录越来越多地利用。将这些多样化的来源整合到现有的 EHR 中，对于最大化其效用至关重要 [50, 51, 52]。

大多数医疗服务网络可能会采用混合方法，期望供应商在某些领域提供 AI，同时依靠第三方或内部开发来增强患者护理和提供者的工作流。从零开始是不可能的；过渡到更智能、更有效的 EHR 可能需要几年时间，尽管改进是必要且合理的。

## 8.8 结论

总之，电子健康记录（EHR）代表了医学的未来，实现了高效的数据收集和处理。随着患者日益参与其 EHR 的开发和管理，他们获得了医疗记录的所有权，增强了他们对医疗过程的参与。这种转变带来了一个更健康、更健康的群体。虽然 EHR 系统可能会产生意想不到的后果和不可预见的挑战，但如果有效实施，其收益是巨大的。随着纸质记录过时，医疗机构必须优先考虑 EHR 系统的监管和维护，以符合患者的最大利益。

EHR 简化提高了便利，数据输入变得更加准确安全。作为最具影响力的健康技术之一，EHR 通过提供可靠数据并促进数据访问改善了医疗保健的各个方面。因此，许多患者的满意度增加，因为个人可以积极参与护理并与提供者一起做出知情决策。尽管前景广阔，美国的 EHR 系统尚未实现其全部潜力。实施障碍仍然存在，正如英国国家医疗服务体系（NHS）指出的那样，它在 2002 年启动了国家 IT 项目以创建一个全国性的 EHR 系统。然而，该计划面临了延迟和资金问题，导致其在 2011 年解散。2013 年宣布了对“无纸化 NHS”的新努力，目标是 2018 年完成。同样，荷兰议会于 2011 年出于隐私考虑拒绝了全国化的 EHR 系统，尽管在解决这些问题后，国家数据交换于 2013 年开始运行。最终，尽管面临挑战，英国、荷兰、美国和其他国家的大多数医疗机构都使用了 EHR 系统，反映了它们在现代医疗保健中的重要性。然而，这些系统产生量数据往往包含不准确之处，凸显了 EHR 技术和实施持续改进的性。

## 参考文献

- [1] Graham S, Depp C, Lee EE, Nebecker C, Tu X, Kim HC, Jeste DV. (2019). Artificial intelligence for mental health and mental illnesses: an overview.

- [2] Jviron offers a "clinical success machine" ... etc. (2019). What is machine learning? A primer for the epidemiologist.

- [3] Wiemken TL, Kelly RY. (2006). Guidelines for developing and reporting machine learning models in biomedical research.

- [4] Luo W, Phung D, Tran T, Gupta S, Rana S, Karmarkar C. (2019). Learning in epidemiology and outcomes research.

- [5] Latif J, Xiao C, Tu S, Rehman U, Bilal A. (2020). Implementation and use of disease diagnosis systems based on electronic medical records: complete review.

- [6] Ben Miled Z, Haas K, Black CM, Khandker RK, Chandrasearan V, Lipton R. (2019). Predicting dementia with EHR data.

- [7] Agency for Healthcare Research and Quality. (2008). Statewide Implementation of Electronic Health Records.

- [8] Arkes O, O'Malley A, Tetzloff J, Altman DG. (2009). Preferred reporting items for systematic reviews and meta-analyses: the PRISMA statement.

- [9] Agency for Healthcare Research and Quality. (2006). Practice-Based Research Networks (PBRNs) Fact Sheet.

- [10] Bar-Lev S, Harrison ML. (2006). Negotiating scripts during the implementation of an electronic medical record.

- [11] Belletti D, Sader C, Mullins CD. (2010). Perspectives on electronic medical records adoption: electronic medical records (EMR) in outcomes research.

- [12] Beale T, Chen R, Leslie L, Frankel H, Gader S, Sundvall E, van der Linde H H. (2007). Implementing EHR: Open Informatics.

- [13] Fredericks M, Lyons L, Kondellas B, Ross MW, Hang L, Fredericks J. (2009). Chiropractic physicians: an analysis of select issues for the use of electronic medical records and the patient-practitioner relationship within the society-culture-personality model.

# 人工智能与机器学习技术

- [16] Berko C. (2002). 更好的文档，更好的报销。今日的脊柱医学, 31(6), 56–58。

- [17] 加拿大健康信息中心与普华道。 (2013). 电子病历在社区区域的新兴益处。

- [18] Carayon P, Smith S, Smith-Huditra A, Kurichittame V, Li Q. (2019). 在小型诊所实施电子健康记录系统：诊所工作人员的观点。行为与信息, 28(1), 5–20。

- [19] 医疗保险和保健服务中心 医疗保险保健计划：医生服务收费表内的基于绩效的激励支付系统 (MIPS) 和替代支付模型 (APM) 激励，以及以医生为重点的支付模型标准，

- [20] Chaudhary B, Wang J, Wu S, Maglone M, Mojica W, Roth R, Morton SC, Shekelle PG. (2006). 系统综述：健康信息技术对医疗护理质量、效率和成本的影响。内科学杂志, 144(10), 742–752。

- [21] Chen R. (2009). 迈向基于原型方法的可互操作和基于知识的电子健康记录。Linkoping：林格雪平大学生物医学工程系。

- [22] Choi W, Park I, Shin H, Yoo Y, Kim J, E, et al. (2006). 医嘱系统与电子病历之间直接与间接护理时间的比较。以人为中心的计算机支持系统, 288–293。

- [23] Christensen C, Grossman J, Wang J. (2009). 创新者处方：医疗保健的颠覆性解决方案。纽约：麦格·希尔专业版。

- [24] Cresswell K, Sheikh A. (2014). 对健康信息进行社会技术评估。初级护理, 21(2), 78–83。

- [25] Dxton BE. (2007). 电子健康应用的路线图。电子服务杂志, 5(3), 13–24。

- [26] Donati A, Gabrielli V, Pantassati S, Carletti P, Marini B, et al. (2008). 临床信息系统对监护室的影响。监测与计算杂志, 22, 31–36。

- [27] 安大略省健康局。 (2015). 安大略省健康连接策略版本 1.0。

- [28] Jua A, Desros C, Campbell E, Rao S, Ferris T, et al. (2009). 电子健康记录的使用。新英格兰医学杂志, 360(16), 1628。

- [29] 安大略省健康局。 (2015). 进展报告。

- [30] Fickensen K. (2009). 临床转型：将修辞变为现实。印度健康管理 21。

- [31] Fraser HS, Blaya J. (2010). 在发展中国家实施医疗信息系统，哪些有效，哪些无效。AMIA 年度会议, 232–236。

- [32] Ayatollah H, Bath P, Goad S. (2009). 急诊室的纸质与计算机记录：员工的偏好、期望和担忧。健康信息学, 15(3), 199–211。

- [33] Goetz D, Kuzel A, Feng L, DeShajo J, Lov LE. (2012). 初级护理中的 EHR：益处、挑战和成功策略。美国管理护理杂志, 18(2), e48–e54。

- [34] Grams R. (2009). “新的”电子病历 (EMR) —— 幻想还是现实？医学科学杂志, 33, 327–328。

- [35] Hauck K, Zhao X. (2021). 医院的一天有多危险？患者不良事件和住院时间模型。澳大利亚墨尔本：帝国学院、伦敦和蒙纳什大学。

# 机器学习在知识挖掘中的进展

- [36] Hillestad R, Bigelow J, Bower A, Girosi F, Meili R, Taylor, R. (2005). 电子病历能改变医疗保健吗？潜在的健康益处、节省和成本。健康事务, 24(5), 1103–1117。
