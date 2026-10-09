# Article
Quality of Life Prediction on Walking Scenes Using Deep
Neural Networks and Performance Improvement Using
Knowledge Distillation

Thanasit Rithanasophon 1 , Kitsaphon Thitisiriuwech 1 , Pittipol Kantavat 1, *, Boonsorn Kijisirikul 1, Yuji Iwahori 2,
Shinji Fukui 3, Kazuki Nakamura 4 and Yoshitsugu Hayashi 5

+   1 Department of Computer Engineering, Faculty of Engineering, Chulalongkorn University, Pathumwan,
Bangkok 10330, Thailand; 62/0111921@student.chula.ac.th (T.R.); ck.kitsaphon@gmail.com (K.T.);
boonsorn.k@chula.ac.th (B.K.)

2 Department of Computer Science, Chubu University, Kasugai 487-8501, Japan; iwahori@isc.chubu.ac.jp

3 Faculty of Education, Aichi University of Education, Kariya 448-8542, Japan; sfukui@auecc.aichi-edu.ac.jp

4 Department of Civil Engineering, Meijo University, Nagoya 468-8502, Japan; nkaka@meijo-u.ac.jp

5 Center for Sustainable Development and Global Smart City, Chubu University, Kasugai 487-8501, Japan;
y-hayashi@isc.chubu.ac.jp

* Correspondence: pittipol.k@chula.ac.th

Abstract: The well-being of residents is a top priority for megacities, which is why urban design
and sustainable development are crucial topics. Quality of Life (QoL) is used as an effective key
performance index (KPI) to measure the efficiency of a city plan’s quantity and quality factors.
For city dwellers, QoL for pedestrians is also significant. The walkability concept evaluates and
analyzes the QoL in a walking scene. However, the traditional questionnaire survey approach is
costly, time-consuming, and limited in its evaluation area. To overcome these limitations, the paper
proposes using artificial intelligence (AI) technology to evaluate walkability data collected through
a questionnaire survey using virtual reality (VR) tools. The proposed method involves knowledge
extraction using deep convolutional neural networks (DCNNs) for information extraction and deep
learning (DL) models to infer QoL scores. Knowledge distillation (KD) is also applied to reduce
the model size and improve real-time performance. The experiment results demonstrate that the
proposed approach is practical and can be considered an alternative method for acquiring QoL.

Keywords: quality of life; walking scene; walkability; semantic segmentation; object detection; deep
convolutional neural networks; knowledge distillation

# 1. Introduction

Urban design is crucial for sustainable development in megacities. Fast-growing
megacities without good urban planning can cause a lot of significant problems to residents
such as traffic congestion and transportation accidents [1–5]. For this reason, policymakers
need to realize the importance of sustainable development in urban design and plan both
resident-friendly and environment-friendly cities.

Policymakers can use Quality of Life (QoL), one of the key performance indexes (KPI),
to evaluate their urban design performance [6]. The concept of QoL [7] is to assess well-
being, happiness of citizens, and individual needs including social interactions as a part
of the society based on sustainable development [8–10]. According to numerous studies,
people use the Quality-of-Life framework as a policy performance measurement for urban
public transportation of megacities, especially in emerging countries, for example, Bangkok.
The failed urban planning in Bangkok leads to severe transportation congestion that is
caused by the car-oriented policies [1,2,11]. Thus, many researchers use Bangkok as a case
of study for QoL, such as Alonso [12], who predicts land-use public transportation policy
based on the satisfaction of dwellers, and Hayashi et al. [13] and Banister [14] proposed