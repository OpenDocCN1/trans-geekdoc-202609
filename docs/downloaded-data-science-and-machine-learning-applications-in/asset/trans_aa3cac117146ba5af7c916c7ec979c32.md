
分析（LDS）等），模糊辅助混合模型已被证明在许多已评论文献中具有良好的性能。

由于用于训练人工智能算法的各种数据集的空间维度，将数据集从高维空间转换到低维空间同时保持高维结构的需求有助于提高人工神经网络和机器学习算法的预测能力。该降维过程被称为特征提取。随着深度学习算法的发展，特征提取问题已得到解决，因为算法可以从原始数据输入中提取有价值的信息。本文评阅的文献表明，软计算方法的应用与通过试错方法选择参数设置以获得高性能准确性有关。因此，未来的研究必须采用软计算方法的参数自动选择，以避免在寻找最佳参数时浪费大量时间。

近年来，石油行业见证了由先进传感器产生的大量数据（Saikia et al., 2020），这导致了先进建模和估计技术的发展。这种先进建模是应用深度学习算法（例如，CNN）来处理特征选择（Shaheen, 2016）并通过其隐藏神经元从输入数据中提取有用信息（Saikia et al., 2020）。深度学习（DL）的应用在储层表征领域尚未得到充分利用，但在图像和语音识别领域取得了很大成功（Bae et al., 2016; Fujiyoshi et al., 2019; He et al., 2016; Pouyanfar et al., 2018）以及医疗等其他领域（Chen et al., 2018; Fang et al., 2019）。尽管近年来DL已被应用于解决各种学习任务，模型的训练是困难的（Rere et al., 2016），但随着数据可用性的改善，DL模型的性能有所提高。多年来，已实施了诸如随机梯度下降（SGD）、共轭梯度（CG）、无 Hessian 优化（HFO）和 Krylov 子空间下降（KSD）等各种算法来遏制这一缺陷。这些算法显示出一些局限性，例如 SGD 的多种手动调优方案、CG 的缓慢以及 HFO 和 KSD 的更高内存消耗（Rere et al., 2016）。为了解决其中一些算法的问题，将元启发式与 DL 混合将是一个很好的研究方向。元启发式优化技术已成功应用于工程、科学及相关行业的许多优化问题的求解。在储层表征领域，将 DL 与元启发式算法混合的研究很少。尽管如此，其另一个重要方面——关于储层表征的无标签数据学习——也尚未得到充分利用。同样，随着岩心信息与测井数据的可用性，半监督深度学习方法的应用可以带来储层表征的更大成功，并且必须加以利用。

## 250 地下工程中的数据科学和机器学习应用

![](img/80b94770dd572ad559c67fa9921bb887_266_0.png)

因此，未来的工作将致力于研究半监督深度学习方法的应用，以帮助改进储层性质预测和相分析，并研究利用一些元启发式算法改进 DL 模型。图 10.6 显示了所提出的半监督深度学习模型的框架。在半监督学习算法架构（图 10.6）中，少量标记数据用于模型的局部训练（监督学习）。监督训练后，训练好的模型和未标记数据集用于预测输出，从而产生伪标签。由于这些伪结果可能不准确，算法同时将伪标签数据与标记训练数据关联，并将输入标记训练数据与未标记训练数据关联。这些关联数据再次用于训练模型以减少误差并提高模型的准确性。

地球物理和岩石物理测井数据受到噪声和各种处理不确定性的影响，因此需要适当的预处理技术来改善数据的定性和定量分析。Saikia et al. (2020) 强调了噪声、异常值、虚假属性去除以及不同数据源在时间、深度和频率方面的合适相关性作为预处理技术的一些方面。为有效处理这些问题，岩石物理学的应用在地球物理学界获得了广泛关注。这一范式有助于改善测井条件。此外，近年来岩石物理学在石油工业中也受到广泛关注，以帮助校正输入测井数据，从而改善储层表征。（Chi and Han, 2009; Mukerji et al., 2001; Saberi, 2013; Saxena et al., 2018）。为了捕捉岩石的测井响应以及与理论关系相关的不确定性，

![](img/80b94770dd572ad559c67fa9921bb887_267_0.png)

结合岩石物理学的地震引导方法是最好的方法。由于地质位置对所获取的数据（地球物理、岩心数据和岩石物理）有很大影响，地质的特征（弹性模量）可以通过岩石物理模型来解决，并理解此类地质的地球物理数据响应（图 10.7）。在图 10.7 中，岩石物理模型用于校正各种输入测井数据（如密度和声波测井），然后用于更好地增强储层表征（确定性反演、相概率映射等）。该技术的使用有助于理解地质复杂性、改善测井响应，并且可以用较少的数据样本实现相当高的准确度。因此，未来的工作应利用岩石物理模型与人工智能模型相结合来校正用于预测储层性质的各种输入，以获得未来属性建模的更准确、更精确的结果。

图 10.7. 岩石物理学在测井校正中的应用及其对储层表征的贡献。

## 10. 结论

过去几年，石油工业为其资源估算产生了大量数据。然而，在当前经济条件下，大多数现场数据采集受到限制，因此在考虑使用复杂模型的情况下，储层表征依赖于所获取的数据。所有可用数据（岩石物理学、地质学、地球物理学、岩石力学和工程）的整合在实现良好的储层表征中发挥着重要作用。可用数据的整合提供了高

## References

- Al-Anazi, A. and Gates, I.D. 2010. 用于分类岩相和模拟非均质储层渗透率的支持向量机算法。 *Engineering Geology* 114(3–4): 267–277. https://doi.org/10.1016/j.enggeo.2010.05.005.
- Al-Anazi, A.F. and Gates, I.D. 2012. 用于预测孔隙度和渗透率的支持向量回归：样本量的影响。 *Computers and Geosciences* 39: 64–76. https://doi.org/10.1016/j.cageo.2011.06.011.
- Al-Bulushi, N., King, P.R., Blunt, M.J. and Kraaijveld, M. 2009. 用于预测含水饱和度和流体分布的人工神经网络模型开发。 *Journal of Petroleum Science and Engineering* 68(3–4): 197–208. https://doi.org/10.1016/j.petrol.2009.06.017.
- Al-Mudhafer, W.J. 2017a. 通过先进机器学习算法整合测井解释用于岩相分类和渗透率建模。 *Journal of Petroleum Exploration and Production Technology* 7(4): 1023–1033. https://doi.org/10.1007/s13202-017-0360-0.
- Al-Mudhafer, W.J. 2017b. 在伊拉克南鲁迈拉油田祖拜尔组主产层中整合核支持向量机进行高效岩相分类。 *Modeling Earth Systems and Environment* 3: 1–8. https://doi.org/10.1007/s40808-017-0277-0.
- Alzubaidi, F., Mostaghimi, P., Swietojanski, P., Clark, S.R. and Armstrong, R.T. 2021. 使用卷积神经网络从钻孔岩心图像进行自动岩性分类。 *Journal of Petroleum Science and Engineering* 197: 107933. https://doi.org/10.1016/j.petrol.2020.107933.
- Ameur-Zaimeche, O., Zeddouri, A., Heddam, S. and Kechiched, R. 2020. 阿尔及利亚南部伯基内盆地西夫法蒂玛油田非取心井的岩相预测：多层感知器神经网络与基于聚类分析方法比较研究。 *Journal of African Earth Sciences* 166: 103826. https://doi.org/10.1016/j.jafrearsci.2020.103826.
- Amiri, M., Ghiasi-Freez, J., Golkar, B. and Hatampour, A. 2015. 利用帝国主义竞争算法优化的人工神经网络提高致密含泥砂岩储层含水饱和度估计：案例研究。 *Journal of Petroleum Science and Engineering* 127: 347–358. https://doi.org/10.1016/j.petrol.2015.01.013.
- Anifowose, F. and Abdulraheem, A. 2011. 应用于油气储层表征的模糊逻辑驱动和 SVM 驱动混合计算智能模型。 *Journal of Natural Gas Science and Engineering* 3(3): 505–517. https://doi.org/10.1016/j.jngse.2011.05.002.
- Anifowose, F.A., Abdulraheem, A., Al-Shuhail, A. and Schmitt, D.P. 2013. 利用人工智能技术从地震和测井数据改进渗透率预测。 pp. 2190–2196. *In: SPE Middle East Oil and Gas Show and Conference*. March. OnePetro. https://doi.org/10.2118/164465-MS.
- Anifowose, F.A., Labadin, J. and Abdulraheem, A. 2015. 基于非线性特征选择的极限学习机集成模型用于改进天然气储层表征。 *Journal of Natural Gas Science and Engineering* 26: 1561–1572. https://doi.org/10.1016/j.jngse.2015.02.012.
- Anifowose, F.A., Labadin, J. and Abdulraheem, A. 2017. 石油储层表征与建模中的混合智能系统：迄今的历程与未来挑战。 *Journal of Petroleum Exploration and Production Technology* 7: 251–263. https://doi.org/10.1007/s13202-016-0257-3.
- Archie, G.E. 1952. 碳酸盐岩储层岩石分类与岩石物理学考虑。 *Aapg Bulletin* 36(2): 278–298. https://doi.org/10.1306/3D9343F7-16B1-11D7-8645000102C1865D.
