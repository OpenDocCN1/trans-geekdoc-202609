
[Table 13.4](#ch13.xhtml#tab13_4) 显示，在训练数据集上，CNN 模型实现了 83% 的准确率，对应的损失为 0.35。在测试数据集上，模型表现更好，准确率为 88%，损失更低，为 0.25。这表明 CNN 模型能够很好地从训练数据推广到测试数据，证明其在正确分类眼部图像方面的有效性。

模型的性能还通过其曲线在 [Figure 13.9](#ch13.xhtml#fig13_9) 的基础上进行图形化分析。

![Figure 13.9 Learning curves of CNN model](images/fig13_9_C.jpg)

[Figure 13.9 Learning curves of CNN model](#ch13.xhtml#R_fig13_9)

[Table 13.5](#ch13.xhtml#tab13_5) 提供了关于精确率（precision）、召回率（recall）以及 F1 分数（F1 score）的特定模型性能摘要。

[Table 13.5 Performance summary.](#ch13.xhtml#R_tab13_5)

| 模型 || 召回率 || 精确率 || F1 分数 |

| --- | --- | --- | --- |

| CNN || 0.50 || 0.50 || 0.50 |

| --- | --- | --- | --- |

同样，该模型还基于精确率、召回率和 F1 分数在 [Table 13.6](#ch13.xhtml#tab13_6) 中对二元数据集（即健康眼和粉红眼）进行评估。

[Table 13.6 Class-wise performance metrics for eye classification.](#ch13.xhtml#R_tab13_6)

| 类别 || 精确率 || 召回率 || F1 分数 |

| --- | --- | --- | --- |

| 健康眼 || 0.33 || 0.38 || 0.35 |

| --- | --- | --- | --- |

| 粉红眼 || 0.67 || 0.64 || 0.62 |

## V. 讨论

结膜炎是一种有潜力影响所有年龄段人群的状况。然而，观察表明，这一现象在儿童群体和年轻成年人群中更为普遍。这可以归因于儿童和年轻成年人经常聚集在教育机构和工作场所，在那里他们之间保持密切的身体接触和频繁的身体接触。病原体的指数级繁殖是导致本年度（Hashmi, 2022）病例人数近乎翻倍的主要因素。

根据可用资料，结膜炎病例出现了显著增加，病例数量上升了约 50–60%。主要受影响的群体主要是处于儿童发育阶段的个体。根据我们的研究结果，大约每三个孩子中就有一个表现出红眼或结膜炎症状（PTI, 2023）。观察到的数据表明，与以往季节模式相比，结膜炎病例的发生率显著上升，范围在 10% 到 15% 之间。根据专家分析，可能高达 40% 的受影响个体是儿童（Debroy, 2023）。

在本论文中，研究旨在促进结膜炎的早期准确检测，这是一种影响全球数百万人的传染性眼部疾病。所得结果展示了 CNN 模型在准确率、精确率、召回率、F1 分数和损失方面的表现。模型在区分健康眼和受结膜炎影响的眼部方面展示了显著的准确性。

CNN 模型的精确率、召回率和 F1 分数均为 0.50。这些结果表明，模型在正确识别阳性实例（真阳性）的同时，能够将假阴性降到最低。不过，F1 分数为 0.50 表明模型整体性能仍有提升空间，因为通常更倾向于更高的精确率、召回率和 F1 分数以获得更准确可靠的预测。同样，按类别的指标显示健康类和结膜炎类的表现相对均衡。但仍需考虑一些局限性。数据集的规模、多样性和质量会影响模型的表现，过拟合仍是一个主要问题，尤其是在数据集较小或不平衡时。

## VI. 结论

本文强调了拟议的 CNN 模型在利用眼部图像自动检测结膜炎方面的重要性。模型的准确率为 88.80%，能够有效地区分健康眼和受结膜炎影响的眼部，为医务人员提供早期诊断的有力工具。这一自动化检测的进展有望提升眼部健康管理，通过及时干预降低传播率。未来，工作可以通过扩大数据集并开发能够进行多类别结膜炎分类的自动学习模型来进一步扩展。

总体而言，本论文凸显了基于人工智能的诊断工具在提升结膜炎检测和整体眼部健康护理方面的重要作用。

## 参考文献

*   Azari, Amir A., and Amir Arabi. (2020). Conjunctivitis: a systematic review. Journal of ophthalmic & vision research. 15(3): 372–395. doi: [10.18502/jovr.v15i3.7456](http://dx.doi.org/10.18502/jovr.v15i3.7456)

*   Manjumdar, Pulak. (2010). Preliminary phytochemical and wound healing activity of zyziphus oenoplia (l) mill. PhD diss., Rajiv Gandhi University of Health Sciences (India), 1–24.

*   Erdin, Muh. and Patel, L. (2023). Early detection of eye disease using CNN. Int. J. Res. Appl. Sci. Engg. Technol. 11(4), 2683–2690.

*   Melih, G., Goceri, E., and Danisman, T. (2015). Automated detection of adenoviral conjunctivitis disease from facial images using machine learning. 2015 IEEE 14th Int. Conf. Mach. Learn. Appl. (ICMLA), 1204–1209.

*   Jae-Ho, H. (2022). Artificial intelligence in eye disease: Recent developments, applications, and surveys. Diagnostics, 12(8), 1927.

*   Hashmi MF, Gurnani B, Benson S, Price KL. Conjunctivitis (Nursing). (2022). Dec 6. In: StatPearls \[Internet\]. Treasure Island (FL): StatPearls Publishing; 2023 Jan–. PMID: 33760572.

*   [Kaggle](#ch13.xhtml#R_ref13_7). (2020). Eye diseases virus dateset vol 1. October 26.

*   Apeksha, K., Bawa, R. K., and Kumar, Y. (2023). Artificial intelligence techniques to predict the airway disorders illness: A systematic review. Arch. Comput. Method Engg., 30(2), 831–864.

*   Ajitesh, K. (2023). Different types of CNN architectures explained: Examples - Data analytics. Data Analyt., August 23.

*   Yogesh, K., Koul, A., and Mahajan, S. (2022). A deep learning approaches and fastai text classification to predict 25 medical diseases from medical speech utterances, transcription and intent. Soft Comput., 26(17), 8253–8272.

*   [Singh, Jaiteg, and Nandini Modi](#ch13.xhtml#R_ref13_11). (2019). Use of information modelling techniques to understand research trends in eye gaze estimation methods: An automated review. Heliyon, 5(12), 1–12.

*   Debrowski, Adam. (2022). Types of conjunctivitis: Bacterial, viral, allergic and others. Available at https://www.allaboutvision.com/en-in/conditions/conjunctivitistypes/ \[Accessed on Dec 10, 2023\]

*   Prateeti, M., Bhattacharyya, I., Mullick, M., Kumar, R., Roy, N. D., and Mahmud, M. (2021). iConDet: An intelligent portable healthcare app for the detection of conjunctivitis. Int. Conf. Appl. Intel. Informat., 29–42. Cham: Springer International Publishing.

*   Nangia, Aarti. (2023). Cases of conjunctivitis, other eye infection on rise in Delhi: Doctors. Available at [https://economictimes.indiatimes.com/news/india/cases-ofconjunctivitis-other-eye-infection-on-rise-in-delhidoctors/articleshow/102085752.cms](https://economictimes.indiatimes.com/news/india/cases-ofconjunctivitis-other-eye-infection-on-rise-in-delhidoctors/articleshow/102085752.cms) \[Accessed on Dec 9, 2023]
