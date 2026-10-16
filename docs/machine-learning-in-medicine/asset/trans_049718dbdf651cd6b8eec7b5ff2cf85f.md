
19. [19.](#C16_chapter9.xhtml#rref9_19) O. Ronneberger, P. Fischer, and T. Brox, “U-net: Convolutional networks for biomedical image segmentation,” in `International Conference on Medical Image Computing and Computer-Assisted Intervention`. Springer, 2015.

20. [20.](#C16_chapter9.xhtml#rref9_20) O. Oktay et al., “Attention U-net: Learning where to look for the pancreas,” `arXiv preprint arXiv:`1804.03999, 2018.

21. [21.](#C16_chapter9.xhtml#rref9_21) K. C. Wong et al., “3D segmentation with exponential logarithmic loss for highly unbalanced object sizes,” in `International Conference on Medical Image Computing and Computer-Assisted Intervention`. Springer, 2018.

22. [22.](#C16_chapter9.xhtml#rref9_22) M. H. Yap et al., “Automated breast ultrasound lesions detection using convolutional neural networks,” `IEEE Journal of Biomedical and Health Informatics`, vol. 22, no. 4, pp. 1218–1226, 2018.

23. [23.](#C16_chapter9.xhtml#rref9_23) C. Leibig, V. Allken, M. S. Ayhan, P. Berens, and S. Wahl, “Leveraging uncertainty information from deep neural networks for disease detection,” `Scientific Reports`, vol. 7, no. 1, pp. 1–14, 2017.

24. [24.](#C16_chapter9.xhtml#rref9_24) A. Krizhevsky, I. Sutskever, and G. E. Hinton, “Imagenet classification with deep convolutional neural networks,” in `Advances in Neural Information Processing Systems`, 2012, pp. 1097–1105.

25. [25.](#C16_chapter9.xhtml#rref9_25) K. He, X. Zhang, S. Ren, and J. Sun, “Deep residual learning for image recognition,” in `Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition`, 2016, pp. 770–778.

26. [26.](#C16_chapter9.xhtml#rref9_26) M. D. Hoffman, D. M. Blei, C. Wang, and J. Paisley, “Stochastic variational inference,” `The Journal of Machine Learning Research`, vol. 14, no. 1, pp. 1303–1347, 2013.

27. [27.](#C16_chapter9.xhtml#rref9_27) K. Clark, et al., “The cancer imaging archive (TCIA): Maintaining and operating a public information repository,” `Journal of` `Digital Imaging`, vol. 26, no. 6, pp. 1045–1057, 2013.

# [CHAPTER 10](#C02a_toc.xhtml#rc10)

[Detection of Abnormal Activities Stemming from Cognitive Decline Using Deep Learning](#C02a_toc.xhtml#rc10)

Damla Arifoglu

University College London

London, United Kingdom

Abdelhamid Bouchachia

Bournemouth University

Poole, United Kingdom

## Contents

[10.1 Introduction](#C17_chapter10.xhtml#secc010_1)

[10.2 Indicators of Dementia](#C17_chapter10.xhtml#secc010_2)

[10.3 Literature Overview](#C17_chapter10.xhtml#secc010_3)

[10.3.1 Cognitive Status Assessment](#C17_chapter10.xhtml#secc010_3_1)

[10.3.2 Deep Learning](#C17_chapter10.xhtml#secc010_3_2)

[10.4 Datasets and Data Generation](#C17_chapter10.xhtml#secc010_4)

[10.4.1 Datasets](#C17_chapter10.xhtml#secc010_4_1)

[10.4.2 Data Generation](#C17_chapter10.xhtml#secc010_4_2)

[10.4.2.1 Activity-Related Abnormal Behavior](#C17_chapter10.xhtml#secc010_4_2_1)

[10.4.2.2 Sub-Activity–Related Abnormal Behavior](#C17_chapter10.xhtml#secc010_4_2_2)

[10.5 Spatio-Temporal Activity Recognition and Abnormal Behavior Detection](#C17_chapter10.xhtml#secc010_5)

[10.5.1 Sensor Data Representation](#C17_chapter10.xhtml#secc010_5_1)

[10.5.2 Abnormal Behavior Detection](#C17_chapter10.xhtml#secc010_5_2)

[10.5.3 Experiments](#C17_chapter10.xhtml#secc010_5_3)

[10.5.4 Results with Recurrent Neural Networks](#C17_chapter10.xhtml#secc010_5_4)

[10.5.5 Results with Convolutional Neural Networks](#C17_chapter10.xhtml#secc010_5_5)

[10.6 Conclusions and Future Work](#C17_chapter10.xhtml#secc010_6)

[10.6.1 Conclusion](#C17_chapter10.xhtml#secc010_6_1)

[10.6.2 Future Work](#C17_chapter10.xhtml#secc010_6_2)

[Bibliography](#C17_chapter10.xhtml#bibliography-1)

## [10.1 Introduction](#C17_chapter10.xhtml#rsecc010_1)

In recent years, diseases related to cognitive impairment in ageing persons are treated as a major public health concern all over the world. Alzheimer’s Disease International estimated the number of people suffering from dementia worldwide in 2018 to be 50 million and it will increase to 82 million by 2030 \[[1](#C17_chapter10.xhtml#ref10_1)\]. These numbers underline a situation that presents a certain level of criticality.

Ageing persons with cognitive impairment have problems with activities that require memory and cognition \[[2](#C17_chapter10.xhtml#ref10_2)\]. They also have difficulties with speaking, writing, distinguishing objects and executing daily life activities such as cleaning, cooking and so on \[[3](#C17_chapter10.xhtml#ref10_3)\]. Elderly people need special care and help from their caregivers leading to a social, psychological, physical and economic challenge to family members, caregivers and the society as a whole.

Most elderly people prefer to lead an independent life. Studies show that it is better for the health of these people to stay in a self-determined private home environment while ageing \[[7](#C17_chapter10.xhtml#ref10_7),[8](#C17_chapter10.xhtml#ref10_8)\].

Changes in daily life activity (preparing food, showering, walking, sleeping, watching television, going to the toilet, having dinner/lunch/breakfast, cleaning the house and so on) patterns and their occurrence time and frequency are key indicators in determining the cognitive status of elderly people. Assessing the cognitive status of elderly people by tracking their daily life activities in a specially designed smart-home would be very useful for caregivers, medical doctors and clinicians so that early treatment would be possible.

Unfortunately, there exists no data assessing the cognitive abilities of ageing persons. Thus, in this study, we tackle the scarcity of the data demonstrating the abnormal behavior of elderly people by generating data. Moreover, we aim to recognise daily life activities by taking their neighbourhood information into account. The spatio-temporal information of activities and their ordering and frequency are important for understanding the cognitive abilities of elderly people. Thus, we emulate activity recognition and abnormal behavior detection problems as a sequence labelling problem. In the present study, we first model activities as a sequence and then detect the abnormal behavior. The rest of the chapter is presented as follows. [Section 10.2](#C17_chapter10.xhtml#secc010_2) provides an overview of dementia indicators. [Section 10.3](#C17_chapter10.xhtml#secc010_3) summarises the literature work, while [Section 10.4](#C17_chapter10.xhtml#secc010_4) describes the datasets used. [Section 10.5](#C17_chapter10.xhtml#secc010_5) describes the methods used and presents the experiments. Lastly, [Section 10.6](#C17_chapter10.xhtml#secc010_6) concludes the chapter.

## [10.2 Indicators of Dementia](#C17_chapter10.xhtml#rsecc010_2)

