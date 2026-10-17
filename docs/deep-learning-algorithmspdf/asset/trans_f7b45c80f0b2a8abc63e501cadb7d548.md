
-   [回顾性研究了深度学习在宫颈癌近曲疗法中的应用，并梳理了发展现状。](#)

# Method

## 方法

This survey reviewed the application of machine learning and deep learning in brachytherapy for cervical cancer in the past 10 years. The survey **Citation**: Hu, H., Shao, Y. and Hu, S. (2020), A Review of the Application of Deep Learning in Brachytherapy. Open Access Library Journal, 7, 1-9. doi: 10.4236/oalib.1106589.

Copyright
licensed under the Creative Commons Attribution International License (CC BY). http://creativecommons.org/licenses/by/4.0

本书版权归Arcler所有

![Image 1056](index-244_1.png)

![Image 1057](index-244_2.png)

![Image 1058](index-244_3.png)

## Deep Learning Algorithms

## 深度学习算法

218

retrieved and reviewed electronic journal articles in scientific databases such as Google Scholar and IEEE. The three sets of keywords used 1) deep learning, brachytherapy, 2) machine learning, brachytherapy, 3) automation, brachytherapy.

retrieved and reviewed electronic journal articles in scientific databases such as Google Scholar and IEEE. The three sets of keywords used 1) 深度学习, 近曲疗法, 2) 机器学习, 近曲疗法, 3) 自动化, 近曲疗法.

## Results

## 结果

Through research on the application of deep learning in brachytherapy, it is found that the U-net model is basically based on convolutional neural networks or some attention mechanisms are added to it, and it is applied to brachytherapy of prostate or cervical cancer. The automatic segmentation and reconstruction of the mid-source applicator (interpolation needle), target area delineation, optimization in the treatment planning system and dose calculation have achieved good results, proving that deep learning can be applied to the clinical treatment of brachytherapy.

通过对深度学习在近曲疗法中的应用研究，发现 U-net 模型基本基于卷积神经网络，或者在其上加入了一些注意力机制，并应用于前列腺癌或宫颈癌的近曲疗法中。自动分割和重建中源应用器（插入针），目标区域划定，治疗计划系统中的优化以及剂量计算已取得良好结果，证明深度学习可以应用于近曲疗法的临床治疗。

## Conclusion

## 结论

The research on the application of deep learning in brachytherapy confirmed that deep learning can effectively promote the development of brachytherapy.

关于深度学习在近曲疗法中的应用研究确认了深度学习可以有效促进近曲疗法的发展。

**Keywords:** Deep Learning, Brachytherapy, Machine Learning, Automation

**关键词:** 深度学习, 近曲疗法, 机器学习, 自动化

## INTRODUCTION

## 引言

Brachytherapy technology is a method of placing a radioactive source into the tumor area through an applicator or directly implanting it into the tumor tissue for radiotherapy. Because of its inherent physical and biological characteristics, brachytherapy can give a high absorbed dose to the focused irradiation of the tumor, and the dose around the source drops rapidly, which can effectively increase the local irradiation of the tumor and protect the normal tissue around the tumor. The local control rate and survival rate have significantly reduced the complications associated with brachytherapy.

近曲疗法技术是一种通过应用器将放射性源置入肿瘤区域，或直接植入肿瘤组织进行放射治疗的技术。由于其固有的物理和生物学特征，近曲疗法可以向肿瘤部位输送高剂量，而源周围的剂量迅速下降，这可以有效提高肿瘤的局部照射剂量，并保护肿瘤周围的正常组织。局部控制率和生存率显著降低了近曲疗法相关的并发症。

When the patient moves or the tumor moves in the body, the relative position of the radiation source and the tumor can remain unchanged, and the tumor obtains high dose conformity. These advantages make brachytherapy widely used in clinical applications, often used in the cervix and uterus. The treatment of tumors in the body, vagina, nasopharynx, esophagus, rectum, breast, prostate, skin and other parts is also applicable to the treatment of tumors in many other parts \[1\] \[2\] \[3\].

当患者活动或肿瘤在体内移动时，辐射源与肿瘤的相对位置可以保持不变，肿瘤获得高剂量一致性。这些优势使近曲疗法在临床应用中被广泛使用，常用于宫颈和子宫。体内、阴道、鼻咽、食管、直肠、乳腺、前列腺、皮肤等部位的肿瘤治疗也同样适用于其他部位的肿瘤治疗 \[1\] \[2\] \[3\].

本书版权归Arcler所有

![Image 1059](index-245_1.jpg)

![Image 1060](index-245_2.png)

![Image 1061](index-245_3.png)

![Image 1062](index-245_4.png)

## A Review of The Application of Deep Learning in Brachytherapy 219

## 近曲疗法中的深度学习应用综述 219

The basic procedures of brachytherapy include: target area delineation, applicator reconstruction, dose calculation and dose optimization \[4\]. The specific process is shown in Figure 1. This review revolves around the brachytherapy process.

近曲疗法的基本程序包括：目标区域划定、应用器重建、剂量计算和剂量优化 \[4\]。具体流程如图 1 所示。本综述围绕近曲疗法的过程展开。

In recent years, with the development of computer hardware, the rapid calculation and innovation of large amounts of data and neural network algorithms brought by social digitization, deep learning technology has developed rapidly, and deep learning has also gradually emerged in the applicator reconstruction, dose calculation and treatment planning system \[6\] \[7\] \[8\]. How to closely integrate emerging deep learning with traditional brachytherapy technology to promote the development of three-dimensional brachytherapy technology is the problem considered in this article, but

近年来，随着计算机硬件的发展，社会数字化带来的大量数据和神经网络算法的快速计算与创新，深度学习技术迅速发展，并逐渐在应用器重建、剂量计算和治疗计划系统中出现 \[6\] \[7\] \[8\]。如何将新兴的深度学习技术与传统近曲疗法技术紧密结合，以促进三维近曲疗法技术的发展，是本文所考虑的问题，但

This article reviews the application of deep learning in the brachytherapy automation process \[9\], which is reported as follows.

本文综述了近曲疗法自动化过程中的深度学习应用 \[9\]，具体内容如下。

## ORGAN DISSECTION AND SEGMENTATION

## 器官解剖与分割

In brachytherapy, organ delineation and segmentation undoubtedly play an important role in the treatment plan. The patient performs layer-by-layer scanning through CT or MRI to obtain multiple medical images \[10\]. The doctor sketches the primary target area, the medium-risk target area and the organs at risk according to the patient’s condition. In clinical practice, manual sketching is still the main method. However, there are hundreds of CT images of a single patient, which is a lot of work for doctors. The automatic segmentation of the target area of medical images also plays an increasingly important role in helping doctors delineate tumor areas and endanger organs. Many segmentation methods have been developed, and the effects are different according to the type of application and the image studied. Now some of them have mature segmentation methods integrated in commercial treatment planning system \[6\].

在近曲疗法中，器官的轮廓划定和分割无疑在治疗计划中扮演着重要角色。患者通过 CT 或 MRI 分层扫描获得多张医学影像 \[10\]。医生根据患者的情况，绘制主要靶区、中危靶区以及危及器官。在临床实践中，手动绘制仍是主要方法。然而，单个患者可能有数百张 CT 图像，这对医生而言工作量巨大。医学影像目标区域的自动分割在帮助医生划定肿瘤区域和危及器官方面发挥日益重要的作用。已开发出许多分割方法，其效果因应用类型和所研究的图像而异。目前，部分成熟的分割方法已集成在商业治疗计划系统中 \[6\]。

**Figure 1**. The basic procedures of brachytherapy.

**图 1**. 近曲疗法的基本程序。

本书版权归Arcler所有

![Image 1063](index-246_1.png)

![Image 1064](index-246_2.png)

![Image 1065](index-246_3.png)

## Deep Learning Algorithms

## 深度学习算法

220

Derek Allman \[11\] et al. used convolutional neural networks in 2018 to locate and classify the sources and artifacts in the K-wave simulation formation data. The experimental results show that, unlike geometry-based beamforming, the use of convolutional neural networks can be effective to eliminate metal artifacts in the image. In 2018, Xia Huang \[12\] et al. constructed a convolutional neural network and combined residual learning to eliminate metal artifacts on CT images. The final signal-to-noise ratio on the test set was 38.09. In 2019, Davood Karimi \[13\] et al. used Convolutional Neural Networks (CNN) to develop an automated accurate and stable segmentation method for the clinical target volume of transrectal ultrasound imaging of the prostate in brachytherapy, and proposed two different strategies to Improving the accuracy of image segmentation, research shows that this method can significantly improve the performance of medical image segmentation. Yang Lei \[14\] et al. built the supervised learning model V-net in 2019 to complete the segmentation of the prostate in the ultrasound image, and marked the prostate tissue through deep supervised learning. Finally, the segmented prostate volume is reconstructed and refined through contours.

Derek Allman 等人于 2018 年使用卷积神经网络对 K-wave 仿真数据中的源和伪影进行定位和分类。实验结果表明，与基于几何的束形成不同，使用卷积神经网络可以有效消除图像中的金属伪影。2018 年，Xia Huang 等人构建了卷积神经网络并结合残差学习，消除 CT 图像中的金属伪影。测试集的最终信噪比为 38.09。2019 年，Davood Karimi 等人利用卷积神经网络（CNN）开发出一种用于近曲疗法经直肠超声检查前列腺临床靶区的自动化、准确且稳定的分割方法，并提出了两种提高图像分割精度的不同策略，研究表明该方法可显著提升医学图像分割的性能。Yang Lei 等人于 2019 年构建了监督学习模型 V-net，用于完成超声图像中前列腺的分割，并通过深度监督学习标记前列腺组织。最后，通过轮廓重建和精细，对分割的前列腺体积进行修正。

实验证明，所提方法可用于前列腺的诊断和治疗。结果表明，前列腺分割的 Dice 相似系数、Hausdorff 距离和平均表面距离分别为 0.92、3.94 和 0.60。Nathan Orlando 等人于 2020 年通过构建 U-net 和 V-net 网络，完成了超声引导前列腺癌的前列腺自动分割，证明所构建的模型取得了良好的分割效果，评估参数表明分割效果良好。Qin Nannan 等人于 2020 年通过构建 U-net 网络，完成了宫颈癌近曲疗法中靶区和危及器官的自动划定。自动划定靶区的平均 Dess 相似系数为 0.898，Hausdorff 距离的平均值在 5.3 mm 以内，这证明其可用于临床，并能大幅提高医生的工作效率。

## SEGMENTATION AND RECONSTRUCTION OF THE APPLICATOR (INTERSTITIAL NEEDLES)

## 分割与重建应用器（间质针）

The applicators serve as a bridge between the radiation source and the patient in brachytherapy, and are extremely important in brachytherapy.

近曲疗法中的应用器是辐射源与患者之间的桥梁，在近曲疗法中具有至关重要的作用。

