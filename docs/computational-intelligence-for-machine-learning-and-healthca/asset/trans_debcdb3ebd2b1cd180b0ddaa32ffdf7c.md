

每一篇被选中的文章都直接或间接依赖于从非正式社区获得的数据集。我们区分了两种广泛的信息收集方法：（1）使用调查和电子数据收集工具（例如，Facebook 应用程序）直接从参与者处收集数据并获得其同意，以及（2）从公开帖子中提取的总数据。

直接从参与者收集数据的策略因研究目的和目标平台而异。这些方法包括在相关网站上发布项目信息，邀请参与者参与项目（[Tsugawa et al., 2015](#bodymatter-002.xhtml#b_9783110648195-002_ref_050)）以及在公开支持平台上发布任务，请求项目志愿者（[Schwartz et al., 2016](#bodymatter-002.xhtml#b_9783110648195-002_ref_042)）。为了公开支持，研究人员会在诸如 Amazon Mechanical Turk（[Kittur et al., 2008](#bodymatter-002.xhtml#b_9783110648195-002_ref_030)）等平台上发布有关其研究的详细资料，以吸引参与者。作为问卷调查的一部分，参与者通常会被要求提供知情同意，允许收集其社交网络数据。

使用了多种调查来衡量参与者的抑郁程度和生活满意度，包括流行病学研究中心抑郁量表、患者健康问卷-9 和贝克抑郁量表。

## 2.6 结论与未来挑战

现有的 `ML` 技术存在许多挑战，已被讨论过。

现有的倾向性技术通常需要人类专家的输入作为启发式和领域知识，以确保选择合适的特征集，因此包含且对学习和理解至关重要。然而，此类技术受限于专家知识的准确性和可靠性（人类能力），并且还受限于该知识转移到新任务的程度。

一个实用的模型是正则化的 `MTL`，它依赖于正则化泛函的最小化，如 `SVMs`，这些方法在过去已被成功用于单任务学习。正则化的 `MTL` 方法允许以任务耦合参数使用的新颖部分函数来表示任务之间的关系，并在很大程度上超越了使用 `SVMs` 的单任务学习。然而，使用 `SVMs` 的多任务学习本质上受限于它们要求每个类在其自身的权重向量中表达。`MTL` 的一种替代方案是大间隔最近邻算法的扩展。与依赖于分离超平面不同，其决策函数依赖于最近邻规则，该规则本质上扩展到多个类并成为 `MTL` 的自然契合。这种方法超越了最先进的 `MTL` 分类器；然而，在该领域仍有许多开放的研究挑战。

## 2.7 未来工作

本章旨在回顾各种类型的 `ML` 技术、方法、挑战及其在医疗信息学中的未来范围。在回顾了各种类型的 `ML` 算法之后，研究数据的性质以及数据如何与所应用的 `ML` 算法的效率相关变得至关重要。因此，未来的工作是回顾数据性质的关联性以及所应用的 `ML` 算法的效率。此外，从在线网站导入数据以应用 `ML` 算法的伦理和可靠性也变得重要，需要加以考虑。因此，`ML` 技术在健康信息学和数据科学方面的效率及其关联性需要在更广阔的角度下进行回顾。

## Bibliography

American Diabetes Association. Economic consequences of diabetes mellitus in the US in 1997. Diabetes Care, (1998), 21(2), 296–309.

Baxter J. A model of inductive bias learning. Journal of Artificial Intelligence Research, (2000), 12, 149–198.

Braithwaite S.R., Giraud-Carrier C., West J., Barnes M.D., and Hanson C.L. Validating machine learning algorithms for Twitter data against established measures of suicidality. JMIR Mental Health, (2016) May 16, 3(2), e21. [→](#bodymatter-002.xhtml#xref_d69967e3944)

Clifton D.A., Gibbons J., Davies J., and Tarassenko L. (2012) Machine learning and software engineering in health informatics. In: First international workshop on realizing artificial intelligence synergies in software engineering (RAISE), Zurich, Switzerland, 5 June 2012. [→](#bodymatter-002.xhtml#xref_d69967e3774)

Doi K. Current status and future potential of computer-aided diagnosis in medical imaging. The British Journal of Radiology, (2005), 78(1), S3–S19.

Fauci A.S., Braunwald E., Kesper D.L., Hauser S.L., Longo D.L., Jamesonn J.L., and Loscalzo J. Harrison’s Principles of Internal Medicine. 17th. New York: Mc-Graw Hill, (2008).

Fukunaga K. Introduction to Statistical Pattern Recognition. 2nd. San Diego: Academic Press, (1990). [→](#bodymatter-002.xhtml#xref_d69967e3932)

Ghahramani Z. Probabilistic machine learning and artificial intelligence. Nature, (2015), 521, 452–459.

Guyton A.C. and Hall J.E. Textbook of Medical Physiology. 11th. Philadelphia: W. B Saunders Co, (2006). [→](#bodymatter-002.xhtml#xref_d69967e3795)

Hastie T., Tibshirani R., and Friedman J.The Elements of Statistical Learning: Data Mining, Inference, and Prediction. 2nd. New York: Springer, (2009).

Houlsby N., Huszar F., Ghahramani Z., and Hernndez-lobato J.M. Collaborative Gaussian processes for preference learning. In: Pereira F., Burges C., Bottou L., and Weinberger K. (eds.), Advances in Neural Information Processing Systems (NIPS 2012), (2012), 2096–2104.

Hripcsak G. Writing Arden Syntax medical logic modules. Computers in Biology and Medicine, (1994), 5(24), 331–363. [→](#bodymatter-002.xhtml#xref_d69967e4061)

Huppertz B. and Holzinger A. Biobanks a source of large biological data sets: Open problems and future challenges. In: Holzinger A. and Jurisica I. (eds.), Knowledge Dis- covery and Data Mining, (2014), LNCS, Vol. 8401, Springer, Heidelberg, 317–330.

Johnson S.C. et al. Activation of brain regions vulnerable to Alzheimer’s disease: The effect of mild cognitive impairment. Neurobiology of Aging, (2006), 27(11), 1604–1612. [→](#bodymatter-002.xhtml#xref_d69967e4099)

Kandel E.R., Schwartz J.H., Jessell T.M., Siegelbaum S.A., and Hudspeth A. Principles of Neural Science. 5th. ed. New York: McGraw-Hill, (2012), 1760 pages. [→](#bodymatter-002.xhtml#xref_d69967e3947)

Kittur A., Chi E., and Suh B. Crowdsourcing user studies with Mechanical Turk. 2008 Presented at: SIGCHI Conference on Human Factors in Computing Systems – CHI ’08; Apr 5–10, 2008; Florence, Italy p. 453–456. [→](#bodymatter-002.xhtml#xref_d69967e4150)

LeCun Y., Bengio Y., and Hinton G. Deep learning. Nature, (2015), 521, 436–444.

Lostumbo A., Wanamaker C., Tsai J., Suzuki K., and Dachman A.H. Comparison of 2D and 3D views for evaluation of flat lesions in CT colonography. Academic Radiology, (2010), 17(1), 39–47. [a](#bodymatter-002.xhtml#xref_d69967e3924), [b](#bodymatter-002.xhtml#xref_d69967e3950)

Michalski R.S. (2004) Attributional calculus: a logic and representation language for natural induction. Reports of the machine learning and inference laboratory: MLI 04-2 George Mason University, Fairfax. [→](#bodymatter-002.xhtml#xref_d69967e4054)

Park K. Park’s Textbook of Preventive and Social Medicine. 18th. India: Banarsidas Bhanot publishers, (2005).

Rumelhart D.E., Hinton G.E., and Williams R.J. Learning representations by back-propagating errors. Nature, (1986), 323, 533–536. [a](#bodymatter-002.xhtml#xref_d69967e3909), [b](#bodymatter-002.xhtml#xref_d69967e3935)

