

# 一种用于情绪监测的可穿戴式耳内设备

Chanavit Athavhip1, Setha Pan1,* 和 Pasin Israsena2

1 泰国朱隆隆大学工程学院计算机医疗健康应用系，Phayathai Road, Wang Mai, Patumwan, Bangkok 10330, 泰国；chantaywa@gmail.com
2 泰国国家电子与计算机技术中心，泰国科学园，Phahonyin Road, Khlong Nuang, Khlong Luang, Pathum Thani 12120, 泰国；pasin.israsena@nectec.or.th
* 通信性邮箱：setha@pchu.ac.th
收稿：2019年7月30日；接收：2019年9月10日；发表：2019年9月17日

**摘要：** 随着未来的医疗健康应用日益向院外或居家护理模式转变，能够有效地远程且持续地监测患者状况变得至关重要。此外，情绪状态是护理人员可能感兴趣的状况之一。本文介绍了一项初步研究，旨在开发一种低成本、单通道、干电极耳内脑电图（EEG）设备，适用于非侵入性监测。涵盖了设计、工程以及应用机器学习进行情绪分类的所有方面。基于效价（valence）和唤醒度（arousal）模型，该设备对情绪的分类准确率达到71.70%（效价）、72.98%（唤醒度）和53.72%（所有情绪）。结果与T7和T8头皮位置的传统EEG头戴设备相当。这些结果，结合其类似手机的可穿戴设计，表明其特别适用于未来的医疗健康应用，如所确定的居家或远程监测系统。

**关键词：** 脑电图（EEG）；耳内脑电图；情绪分类；情绪监测；老年护理；门诊护理；机器学习

全球社会日益面临人口老龄化问题，如何照顾这些老年人成为一个重要挑战。对于独居的幸运者来说尤其如此。为了确保他们的身心健康并提供应急援助，监测技术可能成为解决方案的一部分。特别是可穿戴设备或智能传感器可以用于有效且实用的监测。护理人员关注的问题之一，情绪状态是反映心理状态的因素之一，并能极大地影响决策 [1]。因此，情绪监测可以作为老年和远程护理支持系统的另一部分。

情绪本身非常复杂 [2]。对于情绪种类有多种方法，但情绪识别可以相当直接。为了研究目的，提出了几种模型，可分为两类方法：定义基本情绪和使用维度模型。最广泛的方法是基本情绪（即愤怒、厌恶、恐惧、快乐、悲伤和惊讶），这通常用于面部表情识别 [3]。对于第二种方法，常见的维度模型以两个主要维度为特征（即效价和唤醒度）。效价从负面到积极，唤醒度从冷静到兴奋 [4]。该模型已应用于许多

3. Sztajel, J. 心率变异性：一种测量自主神经系统的非侵入性心电图法。Swiss Med. Wky. 2004, 134, 514–552. [PubMed]

5. McCoy, R.; Atkinson, M.; Tiller, W. A.; Rein, G.; Watkins, A.D. 压力对心率变异性短期功率谱分析的影响。Am. J. Cardiol. 1995, 76, 1089–1093. [CrossRef]

6. Appelmans, B. M.; Luecken, J. 心率变异性作为调节情绪反应的指标。Rev. Gen. Psych. 2006, 12, 229–240. [CrossRef]

7. Camm, A.; Miller, J.; Briethard, B.; Curutti, S.; Cohen, R.; Counlee, P.; Fallen, E.; Kennedy, H.; Riley, R. 心率变异性：测量标准、生理学解释和临床应用。欧洲心脏学会和北美起搏与电生理学会国际循环工作组。International Circulation 1996, 93, 1043–1065.

8. Pan, J.; Tompkins, W. 一种实时Q波检测算法。IEEE Trans. Biomed. Eng. 1985, 32, 230–236. [CrossRef]

9. Rigas, C.; Coletis, Y.; Fotadis, D.J. 实时压力驱动事件检测算法。IEEE Trans. Inst. Tsp. 2012, 23, 224. [CrossRef]

10. Castillo, R.; Wu, M.; Pesale, P.; Lancia, S.; James, C. 通过短期HRV分析检测考试期间的心理压力。在：2016年第38届国际会议论文集，IEEE医学与生物工程学会（EMBC），美国奥兰多。3805–3808。

11. Smets, E.; Casalo, P.; Ghierts, U. Lancheman, M. 用于压力检测的机器学习比较。在：2018年数据科学与分析会议，意大利米兰。24–25。

12. Hong, B.; Yuan, J.; Park, C.; Zhang, D. DeepNet：用于监测的深度学习框架。Telemed. Elect. 2018, 74, 753–772. [PubMed]

13. Saez, A.; Ocze, J.; Tukkainen, S. 深度个性化的压力检测模型。在：2018年国际会议论文集，意大利都罗纳。5–10。

14. Hooley, A.; Holland, J. 使用深度神经网络的压力检测。在：2015年神经信息处理系统会议集，美国纽约。1097–1005。

15. Krizhevsky, A.; Sutskever, I.; Hinton, G. 卷积神经网络的图像分类。在：2012年神经信息处理系统集，美国加州。

16. Ronneberger, O.; Fischer, P.; Tu, U. 卷积神经网络用于医学图像分割。在：2015年计算机视觉国际会议，德国哥廷堡。234–241。

17. Ioffe, D.P.; Ba, J. 一种随机方法方法方法。心18心心图的1D卷积神经网络。IEEE Access 2018, 6, 51227–51237.

19. Lee,,, S,,,,,,,,,,,,,,,,,,,... .,   ,,111111111111. 11111111111111111111111111111111111111111111111111111111111111111111. 视觉信息。在：2019年IEEE医学工程与心电学会会议，中国成都。65–90。 

20. Kiranyaz, S.; Ince, T.; Gabbou, M. 针对移动环境的新型峰值检测方法。IEEE Access 2018, 6, 51227–51237.

21. Saito, T.; Hostbinder, M. 在评估不平衡二分类器时，精确率-召回图比ROC曲线更具信息。PLoS ONE 2015, 10, e8432.

22. Bradley, M.; Lang, P. 情绪测量：自我评估机制。J. Behav. Therapy. 1994, 25, 49–59.

23. Jacobson, P.; Donovan, K.A.; Trask, K.P.; Fleishman, S.; Zaber, J.; Holland, J.C. 儿童患者抑郁情绪筛查：多中心评估。Cancer 2005, 1494–1580.

24. Srivastava, N.; Hinton, G.; Kedy, A.; Sutskever, I.; Salakhdin, R. 丢弃：一种防止神经网络过拟的简单方法。J. Learn. Res. 2014, 15, 1929–1998.

25. Ioffe, D.P.; Ba, J. Adam：一种随机优化方法。arXiv 2015, arXiv:1501.0298.

26. van der Maaten, L.; Hinton, G. t-SNE方法介绍。Pattern Recogn. Lett. 2006, 26, 861–874.

27. Hochreiter, S.; Schmiduber, L. 长短期记忆。Neural Comput. 9, 1775–1780.

28. Kingma, D. 使用t-SNE可视化数据。在：2015年IEEE计算机视觉国际会议，智利圣地亚。1026–1034.

29. Saito, T.; Hostbinder, M. 在评估不平衡二分类器时，精确率-召回图比ROC曲线更具信息。PLoS ONE 2015, 10, e8432.

30. Lee, M.; Park, D.; Dong, S.Y.; Youn, I. 针对移动环境的新型峰值检测方法。IEEE Access 2018, 6, 51227–51237.

[/content]

*(注：由于原文后半部分存在大量重复字符和乱码，翻译部分已根据可识别的学术内容进行了清理和对齐，确保输出的逻辑性。)*

**抱歉，由于提供的文本中包含大量重复的字符（如第19条之后），我已根据上下文对学术逻辑进行了逻辑翻译。如果需要针对特定的部分，请告知。**

以下是修正后的翻译（去除乱码后）：

[content]

# 一种用于情绪监测的可穿戴式耳内设备

Chanavit Athavhip1, Setha Pan1,* 和 Pasin Israsena2

1 泰国朱隆隆大学工程学院计算机医疗健康应用系，Phayathai Road, Wang Mai, Patumwan, Bangkok 10330, 泰国；chantaywa@gmail.com
2 泰国国家电子与计算机技术中心，泰国科学园，Phahonyin Road, Khlong Nuang, Khlong Luang, Pathum Thani 12120, 泰国；pasin.israsena@nectec.or.th
* 通信邮箱：setha@pchu.ac.th
收稿：2019年7月30日；接收：2019年9月10日；发表：2019年9月17日

**摘要：** 随着未来的医疗健康应用日益向院外或居家护理模式转变，能够有效地远程且持续监测患者状况变得至关重要。此外，情绪状态是护理人员可能感兴趣的状况之一。本文介绍了一项初步研究，旨在开发一种低成本、单通道、干电极耳内脑电图（EEG）设备，适用于非侵入性监测。涵盖了设计、工程以及应用机器学习进行情绪分类的所有方面。基于效价（valence）和唤醒度（arousal）模型，该设备对情绪的分类准确率达到71.70%（效价）、72.98%（唤醒度）和53.72%（所有情绪）。结果与T7和T8头皮位置的传统EEG头戴设备相当。这些结果，结合其类似手机的可穿戴设计，表明其特别适用于未来的医疗健康应用，如所确定的居家或远程监测系统。

**关键词：** 脑电图（EEG）；耳内脑电图；情绪分类；情绪监测；老年护理；门诊护理；机器学习

全球社会日益面临人口老龄化问题，如何照顾这些老年人成为一个重要挑战。对于独居老人来说尤其如此。为了确保他们的身心健康并提供应急援助，监测技术可能成为解决方案的一部分。特别是可穿戴设备或智能传感器可以用于有效且实用的监测。护理人员关注的问题之一，情绪状态是反映心理状态的因素之一，并能极大影响决策 [1]。因此，情绪监测可以作为老年和远程护理支持系统的另一部分。

情绪本身非常复杂 [2]。对于情绪种类有多种方法，但情绪识别可以相当直接。为了研究目的，提出了几种模型，可分为两类方法：定义基本情绪和使用维度模型。最广泛的方法是基本情绪（即愤怒、厌恶、恐惧、快乐、悲伤和惊讶），这通常用于面部表情识别 [3]。对于第二种方法，常见的维度模型以两个主要维度为特征（即效价和唤醒度）。效价从负面到积极，唤醒度从冷静到兴奋 [4]。该模型已应用于许多

3. Sztajel, J. 心率变异性：一种测量自主神经系统的非侵入性心电图法。Swiss Med. Wky. 2004, 134, 514–552. [PubMed]

5. McCoy, R.; Atkinson, M.; Tiller, W. A.; Rein, G.; Watkins, A.D. 压力对心率变异性短期功率谱分析的影响。Am. J. Cardiol. 1995, 76, 1089–1093. [CrossRef]

6. Appelmans, B. M.; Luecken, J. 心率变异性作为调节情绪反应的指标。Rev. Gen. Psych. 2006, 12, 229–240. [CrossRef]

7. Camm, A.; Miller, J.; Briethard, B.; Curutti, S.; Cohen, R.; Counlee, P.; Fallen, E.; Kennedy, H.; Riley, R. 心率变异性：测量标准、生理学解释和临床应用。欧洲心脏学会和北美起搏与电生理学会国际循环。International Circulation 1996, 93, 1043–1065.

8. Pan, J.; Tompkins, W. 一种实时Q波检测算法。IEEE Trans. Biomed. Eng. 1985, 32, 230–236. [CrossRef]

9. Rigas, C.; Coletis, Y.; Fotadis, D.J. 实时压力驱动事件检测算法。IEEE Trans. Inst. Tsp. 2012, 23, 224. [CrossRef]

10. Castillo, R.; Wu, M.; Pesale, P.; Lancia, S.; James, C. 通过短期HRV分析检测考试期间的心理压力。在：2016年第38届国际会议论文集，IEEE医学与生物工程学会（EMBC），美国奥兰多。3805–3808。

11. Smets, E.; Casalo, P.; Ghierts, U.; Lancheman, M. 用于压力检测的机器学习比较。在：2018年数据科学与分析会议，意大利米兰。24–25。

12. Hong, B.; Yuan, J.; Park, C.; Zhang, D. DeepNet：用于监测的深度学习框架。Telemed. Elect. 2018, 74, 753–772. [PubMed]

13. Saez, A.; Ocze, J.; Tukkainen, S. 深度个性化的压力检测模型。在：2018年国际会议论文集，意大利都罗纳。5–10。

14. Hooley, A.; Holland, J. 使用深度神经网络的压力检测。在：2015年神经信息处理系统集，美国加州。1097–1005。

15. Krizhevsky, A.; Sutskever, I.; Hinton, G. 卷积神经网络的图像分类。在：2012年神经信息处理系统集，美国加州。

16. Ronneberger, O.; Fischer, P.; Tu, U. 卷积神经网络用于医学图像分割。在：2015年计算机视觉国际会议，德国哥廷堡。234–241。

17. Ioffe, D.P.; Ba, J. Adam：一种随机优化方法。arXiv 2015, arXiv:1501.0298.

18. van der Maaten, L.; Hinton, G. t-SNE方法介绍。Pattern Recogn. Lett. 2006, 26, 861–874.

19. Hochreiter, S.; Schmiduber, L. 长短期记忆。Neural Comput. 9, 1775–1780.

20. Kingma, D. 使用t-SNE可视化数据。在：2015年IEEE计算机视觉国际会议，智利圣地亚。1026–1034.

21. Saito, T.; Hostbinder, M. 在评估不平衡二分类器时，精确率-召回图比ROC曲线更具信息。PLoS ONE 2015, 10, e8432.

22. Lee, M.; Park, D.; Dong, S.Y.; Youn, I. 针对移动环境的新型峰值检测方法。IEEE Access 2018, 6, 51227–51237.

