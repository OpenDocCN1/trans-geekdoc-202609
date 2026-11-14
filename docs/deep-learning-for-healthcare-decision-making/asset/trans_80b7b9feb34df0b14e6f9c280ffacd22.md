
另一项艰巨的任务是根据症状分配医疗代码，这需要医生或护士的支持。这种深度 EHR 分析是研究人员和医务人员之间的协作，旨在改进诊断和预测，从而更好地为患者服务。因此，应鼓励医院与研究人员共享数据，反过来，研究人员不应向公众泄露患者详细信息。不同格式的临床数据（如文本、医疗代码、图像、扫描报告等）带来了严重问题，仔细融合所有这些数据并以通用格式表示它们以进行适当分析至关重要。由于数据来自不同来源且缺乏通用表示，数据本质上更加异构。这在归一化过程中确实构成了一个棘手的问题。

由于上述原因，将深度学习研究成果应用于实时医院环境仍存在巨大犹豫，这使得该领域需要进一步研究以实现实际部署。对于临床决策支持系统而言，当务之急是一个能够以良好的准确性非常快速地分析数据的稳健高效模型。因此，医务人员和研究人员是时候共同努力，提供这样一个在实时环境下表现良好的优秀 EHR 数据分析模型了。

## 6.7 改进建议

使用深度学习技术很难解释生成的模型。因此，这些技术被称为“黑箱”。由于这一困境，在表现力与透明度之间产生了权衡。预测和猜测可能影响了医学界正确的诊断和治疗。

这就是为什么线性模型（如逻辑回归）被认为在临床领域是最好的。我们将回顾尝试，使这种深度学习技术更加清晰。在 [[27](#ch6.xhtml#ref6_27)]、[[48](#ch6.xhtml#ref6_48)] 和 [[55](#ch6.xhtml#ref6_55)、[56](#ch6.xhtml#ref6_56) 和 [57](#ch6.xhtml#ref6_57)] 中，主要局限性是缺乏可解释性。表 V 展示了可解释性技术的总结。

### 6.7.1 调整激活函数

有必要清楚地研究输入类型，因为这将影响隐藏单元和输出单元的激活。这种研究肯定会增强学习过程。应识别每个特征的重要性，以设计完美的深度学习模型 [[38](#ch6.xhtml#ref6_38)]、[[42](#ch6.xhtml#ref6_42)]、[[47](#ch6.xhtml#ref6_47)]、[[58](#ch6.xhtml#ref6_58)]。

### 6.7.2 约束

许多研究人员已经研究了训练限制，以提高深度模型的可解释性。因此，像轮数、输入数量和隐藏层数量这样的训练参数应被精确设置。同样，权重调整应适当聚焦 [[40](#ch6.xhtml#ref6_40)]，因为生成的权重稀疏性揭示了激活稀疏神经元的输入类型。所有这些权重限制都应纳入用于调整深度学习神经网络架构的目标函数中。[[59](#ch6.xhtml#ref6_59)] 中针对时间序列数据的表型发现方法通过施加不规则性和稀疏性要求，提高了学习模型权重的可解释性。

### 6.7.3 定性聚类

可以使用可视化方法（如 `t-SNE`）来实现 EHR 概念中向量表示的自然聚类。这实际上是高维数据点之间成对相似性的二维表示 [[55](#ch6.xhtml#ref6_55)]。为了使深度学习表现良好，有必要对表型组成进行彻底检查。在相似诊断和患者亚组的情况下，医疗事件和患者向量的二维分布式表示 [[32](#ch6.xhtml#ref6_32)] 能够实现最佳性能。

### 6.7.4 MIMIC 学习

在其可解释的 `MIMIC` 学习框架 [[59](#ch6.xhtml#ref6_59)]–[[60](#ch6.xhtml#ref6_60)] 中，应充分解决深度模型透明度问题。可解释的线性模型可用于加权原始输入特征，从而显著增强深度网络的能力。在创建深度架构的同时保持所需的特征透明度是另一个关键考虑因素。

## 结论

本章对与 EHR 分析相关的当前深度学习研究进行了综述。在过去两年中，关于这一新兴主题的大量出版物已发表。当我们回顾深度学习所实现的图像和自然语言处理领域的突破时，我们看到了与当代 EHR 驱动的深度学习研究领域惊人的相似之处。本综述中的大多数研究展示了定义过去十年收集的大量原始患者数据的最准确技术。基本图像处理技术关注日益复杂和分层的图像表示。同样，自然语言处理至关重要，因为大多数 EHR 数据由医生笔记组成，必须正确理解。未来的研究应集中在描述患者健康数据及其独特医疗代码的方法上，以便不同的数据源不会在 EHR 数据分析中造成瓶颈。本章讨论了临床记录分析过程、迄今为止部署的深度学习网络、研究空白，并以一些未来深度学习研究改进建议作为结尾。

## 参考文献

1. [Benjamin Shickel, Patrick James Tighe, Azra Bihorac, and Parisa Rashidi](#ch6.xhtml#R_ref6_1), “深度 EHR：电子健康记录（EHR）分析深度学习技术最新进展综述”, IEEE Journal of Biomedical And Health Informatics, vol. 22, No. 5, pp 1589-1604, September 2018

2. [A. Subasi and M. I. Gursoy](#ch6.xhtml#R_ref6_2), 使用 PCA、ICA、LDA 和支持向量机进行 EEG 信号分类, Expert Syst. Appl., vol. 37, no. 12, pp. 8659–8666, 2010.

3. [M. Pechenizkiy, A. Tsymbal, and S. Puuronen](#ch6.xhtml#R_ref6_3), 基于 PCA 的用于分类的特征变换：医学诊断中的问题, in Proc. 17th IEEE Symp. Computer-Based Medical Systems, Bethesda, MD, USA, 2004, pp. 535–540.

4. [L. V. Lita, S. P. Yu, S. Niculescu, and J. B. Bi](#ch6.xhtml#R_ref6_4), 医疗患者记录的大规模诊断代码分类, in Proc. 3rd Int. Joint Conf. Natural Language Processing, Hyderabad, India, 2008, pp. 877–882.

5. [B. Koopman, G. Zuccon, A. Nguyen, A. Bergheim, and N. Grayson](#ch6.xhtml#R_ref6_5), 从自由文本死亡证明中自动进行癌症 ICD-10 分类, Int. J. Med. Inform., vol. 84, no. 11, pp. 956–965, 2015.

6. [D. X. Wang, X. Liu, and M. D. Wang](#ch6.xhtml#R_ref6_6), 一种用于大数据股票期货预测的 DT-SVM 策略, in Proc. 16th Int. Conf. Computational Science and Engineering, Sydney, Australia, 2013, pp. 1005–1012.

7. [J. M. Sun and C. K. Reddy](#ch6.xhtml#R_ref6_7), 医疗保健大数据分析, in Proc. 19th ACM SIGKDD Int. Conf. Knowledge Discovery and Data Mining, Chicago, IL, USA, 2013, p. 1525.

8. [Ying Yu, Min Li, Liangliang Liu, Yaohang Li, and Jianxin Wang](#ch6.xhtml#R_ref6_8), “临床大数据与深度学习：应用、挑战与未来展望”, Big Data Mining And Analytics, Vol.2, No.4, pp288–305, December 2019.

9. [A. Perotte, R. Pivovarov, K. Natarajan, N. Weiskopf, F. Wood, and N. Elhadad](#ch6.xhtml#R_ref6_9), 诊断代码分配：模型与评估指标, J. Am. Med. Inform. Assoc., vol. 21, no. 2, pp. 231–237, 2014.
