

## 用于智能故障诊断的卷积神经网络 71

![](img/f29bba55de4872c43f26af4667e705f2_81_0.png)

图 4.8 基于 t-SNE 的特征可视化。

在高维空间中通过非线性方式，可视化中不同类别之间的任何重叠仍然与表 4.2 中的高准确率保持一致。上述可视化能够定性地说明 CDFL 在故障诊断中的有效性。

## 结论

本章介绍了一种用于感应电机故障诊断的 CDFL 方法。该方法可以直接从原始数据中学习特征，以表征感应电机不同的运行工况。当局部滤波器的权重通过 BPNN 学习时，可以构建快速卷积池化架构，从原始振动数据中提取判别性和不变特征。然后，SVM 成功地对特征进行了感应电机故障诊断的分类。实验研究验证了 CDFL 从故障信号中提取判别性且有效特征的能力。与其它先进方法相比，本章提出的方法对于感应电机故障诊断更加有效且鲁棒。目前正在进行进一步研究，以验证该方法对其他类型机器故障诊断的适用性。

## 参考文献

- Chang, Chih-Chung, and Chih-Jen Lin. 2011. LIBSVM A Library for Support Vector Machines. ACM Transactions on Intelligent Systems and Technology (TIST) 2 (3): 1-27. https://doi.org/10.1145/1961189.1961199.
- Ganz, Zeke, Ricardo Eanao, David Carlos, and Lawrence Carin. 2015. “Learning Deep Sigmoid Networks With Data Augmentation.” Artificial Intelligence and Data Science, PMLR: 38:268-276. http://proceedings.ml/v3/gan15.
- Nce, Serkan Kayilar, Levant Eren, Murat Akar, and Moncef Gabbou. 2016, “Real-Time Motor Fault Detection by 1-D Convolutional Neural Networks.” IEEE Transactions on Industrial Electronics 63 (1): 7067-7075. https://doi.org/10.1109/TIE.2016.258279
- Le Cun, Y., Boser, J. S. Denker, D. R. Edward, W. Hubbard, and L. D. Jackson. 1990. “Handwritten Digit Recognition With a Back-Propagation Network.” Advances in Information Processing Systems 2:396–404.
- Jing, Luyang, Ming Zhao, Pin Li, and Xiaoqiang Xu. 2017. “A Convolutional Neural Network Based Feature Learning and Fault Diagnosis Method for the Condition Monitoring of Gearbox.” Measurement 111: 1–10. https://doi.org/10.1016/j.measurement.2017.07.017.

## 72 深度神经网络-机械系统的智能故障诊断

- Krizhevsky, Alex, Ilya Sutskever, and Geoffrey E. Hinton. 2012. "ImageNet Classification With Deep Convolutional Networks." Advances in Information Processing Systems 25: 1097–1105.
- LeCun, Yann, and Yoshua Bengio. 1995. "Convolutional Networks for Images, Speech, and Time- The Handbook of Brain Theory and Neural Networks 36(161)(10).
- Liao, Bin, Jingjun Xu, Jiantu, and Shilong Zhou. 2015. "An Image Retrieval Method for Binary Images Based on DNN and softmax Classifier." IEEE Technical Review 32 (4):294–303. https://doi.org/10.1105
- Le Cun, Y., Boser, J. S. Denker, D. R. Edward, W. Hubbard, and L. D. Jackson. 1990. "Handwritten Digit Recognition With a Back-Propagation Network." Advances in Information Processing Systems 2:396–404.
- Krizhevsky, Alex, Ilya Sutskever, and Geoffrey E. Hinton. 2012. "ImageNet Classification With Deep Convolutional Networks." Advances in Information Processing Systems 25: 1097–1105.
- LeCun, Yann, and Yoshua Bengio. 1995. "Convolutional Networks for Images, Speech, and Time- The Handbook of Brain Theory and Neural Networks 36(161)(10).
- Liao, Bin, Jingjun Xu, Jiantu, and Shilong Zhou. 2015. "An Image Retrieval Method for Binary Images Based on DNN and softmax Classifier." IEEE Technical Review 32 (4):294–303. https://doi.org/10.1105
- Le Cun, Y., Boser, J. S. Denker, D. R. Edward, W. Hubbard, and L. D. Jackson. 1990. "Handwritten Digit Recognition With a Back-Propagation Network." Advances in Information Processing Systems 2:396–404.
- Jing, Luyang, Ming Zhao, Pin Li, and Xiaoqiang Xu. 2017. "A Convolutional Neural Network Based Feature Learning and Fault Diagnosis Method for the Condition Monitoring of Gearbox." Measurement 111: 1–10. https://doi.org/10.1016/j.measurement.2017.07.017.
- Krizhevsky, Alex, Ilya Sutskever, and Geoffrey E. Hinton. 2012. "ImageNet Classification With Deep Convolutional Networks." Advances in Information Processing Systems 25: 1097–1105.
- LeCun, Yann, and Yoshua Bengio. 1995. "Convolutional Networks for Images, Speech, and Time- The Handbook of Brain Theory and Neural Networks 36(161)(10).
- Liao, Bin, Jingjun Xu, Jiantu, and Shilong Zhou. 2015. "An Image Retrieval Method for Binary Images Based on DNN and softmax Classifier." IEEE Technical Review 32 (4):294–303. https://doi.org/10.1105
- Le Cun, Y., Boser, J. S. Denker, D. R. Edward, W. Hubbard, and L. D. Jackson. 1990. "Handwritten Digit Recognition With a Back-Propagation Network." Advances in Information Processing Systems 2:396–404.
- Jing, Luyang, Ming Zhao, Pin Li, and Xiaoqiang Xu. 2017. "A Convolutional Neural Network Based Feature Learning and Fault Diagnosis Method for the Condition Monitoring of Gearbox." Measurement 111: 1–10. https://doi.org/10.1016/j.measurement.2017.07.017.
*(注：由于提供的文本中参考文献部分存在大量重复，译文按要求保留格式，但在实际工程中通常会进行去重。此处遵循原文结构进行对应处理。)*

## II 深度学习支持的智能故障诊断高级主题

![](img/f29bba55de4872c43f26af4667e705f2_84_0.png)

## 智能故障诊断的数据增强

### 引言

对于基于深度学习的故障诊断，训练数据是影响预测模型性能的重要因素。通常，深度神经网络包含多个隐藏层，需要训练的自由参数数量是巨大的。为了获得准确的预测，深度架构需要良好的训练，并有充分的大数据。然而，在实践中，不同机器状态的训练样本往往是不平衡的。例如，对于运行中的机械系统，它大部分时间都在正常状态下工作，采集到的正样本数据是足够的，而机器发生故障的情况很少，相应的样本也有限。

生成对抗网络（GANs）为解决不平衡数据分类问题提供了一种方法，通过生成少数类的数据。GAN 在生成真实数据方面显示了卓越的能力，并成功应用于图像生成。它可以通过生成与原始数据相似的人工数据来实现数据增强，从而丰富训练数据集。此外，生成架构模拟了数据生成过程，有助于理解原始数据分布。

GAN 最初作为一种生成人工图像的框架被提出，并具有生成令人信信样本的能力。然而，原始 GAN 面临训练不稳定的问题，需要

