
-   [Xin, G., Han, J., Yin, T., Zhou, Y., Yang, J., Cheng, X., and Zeng, X.](#ch70.xhtml#R_ref70_16) (2020). VPQC: A domain-specific vector processor for post-quantum cryptography based on RISC-V architecture. IEEE Trans. Cir. Sys. I Reg. Papers, 67(8), 2672–2684.

-   [Aminanto, M. E., Choi, R., Tanuwidjaja, H. C., Yoo, P. D., and Kim, K.](#ch70.xhtml#R_ref70_17) (2017). Deep abstraction and weighted feature selection for Wi-Fi impersonation detection. IEEE Trans. Inform. Foren. Sec., 13(3), 621–636.

-   [Kumar, A., Kumar, S., Kumar, V., Kumari, A., Saini, A., and Gupta, S.](#ch70.xhtml#R_ref70_18) (2023). Edge computing based IDS detect-ing threats using machine learning and PyCaret. 2023 Int. Conf. Comput. Intel. Sustain. Engg. Sol. (CISES), 668–673.

# 71 A federated learning approach to classify depression using audio dataset

Chetna Gupta and Vikas Khullar^([^(72)](#fn72))

Chitkara University Institute of Engineering and Technology, Chitkara University, Punjab, India

DOI: [10.1201/9781003471059-71](https://dx.doi.org/10.1201/9781003471059-71)

## Abstract

**Vocal emotions are basic to expressing and understanding thoughts and the low toned vocal emotion expression is a major deficit in individuals with depression. The primary objective of this paper is to propose a federated learning (FL)-based classification model to identify depression in individuals through audio. The current scenario of artificial intelligence (AI) focuses on collaborative training of deep learning (DL) models without losing data privacy. So, in the methodology of this paper, a collaborative and privacy preserved approach has been developed using FL for training deep learning models. The long-short short-term memory (LSTM) and bidirectional-long-short term memory (B-LSTM)-based deep learning models will be trained on a collected dataset in the federated learning ecosystem. As a result, the implemented models will be comparatively analyzed on base DL structure as well as the FL ecosystem. The purpose of the investigation is to compare the impact of FL architecture implementations on benchmark models. In conclusion, the most effective examined strategy will be considered for future research objectives.**

**Keywords: Depression, artificial intelligence, federated learning, long-short term memory, bidirectional – long-short term memory, audio**

## Introduction

In the present era, depression is one of the biggest problems the world faces, and if it fails to be treated, it can result in both suicidal thoughts and actual attempts ([Statista, 2021](#ch71.xhtml#ref71_16)). Depression affects people and is an unnoticed psychological disorder that can strike anyone, including those who appear to be doing well. Additionally, one of the most prevalent psychological conditions is depression in our society, which is characterized by a rapid reliance on technological advancement ([LeMoult and Gotlib 2019](#ch71.xhtml#ref71_11); [Gupta and Khullar 2022](#ch71.xhtml#ref71_7)). It is crucial to keep in mind that this illness does not yet have a known remedy that can eliminate all of its effects. Determining the fundamental causes of the problem and coming up with an answer is therefore imperative if we want to stop it from becoming more serious in the future. An early depression detection method could save people’s lives from risk.

In this era, depression detection using audio dataset, which depends on voice analysis learning models to support the early detection of depression by patients themselves, has attracted great interest as a result of recent advancements in deep learning techniques. Existing research uses centralized training to classify and predict depression ([Ye et al., 2021](#ch71.xhtml#ref71_21)). Hence, a method that preserves patient privacy while enabling individual patients with health information to provide the construction of a reliable approach is greatly desired ([Cui et al., 2022](#ch71.xhtml#ref71_4); [Suruliraj and Orji, 2022](#ch71.xhtml#ref71_17)).

To achieve this goal, a federated architecture is suggested to achieve privacy-preserving data via voice analysis. With the training data remaining decentralized, this model makes an effort to use federated learning (FL) to enable collaborative training of an audio-based framework through many clients. The proposed architecture can reduce numerous systemic privacy problems that are present in the conventional centralized approaches because personal information is preserved locally in FL.

## Related work

A study by [Orabi et al. (2018](#ch71.xhtml#ref71_13)) used a variety of deep learning (DL) techniques to analyze Twitter data for depression classification. [Cai et al. (2018](#ch71.xhtml#ref71_3)) tested four machine learning algorithms to identify depression via EEG signals, and the K-Nearest Neighbour model achieved substantial accuracy. [Khullar et al. (2022](#ch71.xhtml#ref71_8)) and [Brar et al. (2022](#ch71.xhtml#ref71_10)) developed an ensemble ML model for anxiety detection using physiological signals. Using a ML approach, [Mousavian et al. (2021](#ch71.xhtml#ref71_12)) established the identification of depression on resting-state MRI and structured MRI image data. In a recent study, [Adarsh et al. (2023](#ch71.xhtml#ref71_1)) presented an ensemble mode to solve the problem of the difference between depression and suicidal thoughts through social media. TR et al. (2022) and [Elbeltagi et al. (2020](#ch71.xhtml#ref71_5)) demonstrated ML models for different heart diseases and climate changes. [Sadilek et al. (2021](#ch71.xhtml#ref71_15)) have summa-rized many instances in which FL could be utilized to improve various health research. [Pranto and Al Asad (2021](#ch71.xhtml#ref71_14)) introduced the application of FL in medical studies by comparing centralized and FL approaches across multiple mental diseases. [Khullar and Singh (2022](#ch71.xhtml#ref71_9)) introduced FL trained algorithms for identifying disaster areas in the internet of unmanned aerial vehicles (UAVs) that enhance data sharing. [Fan et al. (2021](#ch71.xhtml#ref71_6)), [Uyulan et al. (2021](#ch71.xhtml#ref71_19)) and [Yasin et al. (2021](#ch71.xhtml#ref71_20)) developed diagnostic systems to detect major depressive disorder using various DL techniques.

## Methodology

In this study, an openly available audio dataset is obtained which are pre-processed and analyzed using deep learning algorithms as a base, CNN, long-short short-term memory (LSTM) and bidirectional-long-short term memory (B-LSTM). Following that, the privacy-preserved FL algorithm is applied to IID users to train a centralized model on the client site and develop an aggregated model on the server site.

The audio files contain 52 individuals’ data from Chinese people (23 depressed and 29 healthy participants) obtained from Lanzhou University’s Second Affiliated Hospital ([Cai et al., 2020](#ch71.xhtml#ref71_2)). Each individual has 29 clips in this dataset, which are categorized as positive, neutral, or negative emotional stimuli. The voice data is collected using high-quality equipment. Participants in both the healthy and depressed groups range in age from 18 to 55 years.

FL clients simply share the outcomes of calculated weights to form an aggregated analysis model. To protect data privacy, no data is transferred between nodes. FL supports N clients (C1, C2, ... CN) with datasets (D1, D2, ... DN). So, FL trains each client’s data independently to establish a decentralized deep learning model ([Figure 71.1](#ch71.xhtml#fig71_1)).

![Figure 71.1 Federated learning model for depression detection using audio data](images/fig71_1_C.jpg)

[Figure 71.1 Federated learning model for depression detection using audio data](#ch71.xhtml#R_fig71_1)

(1)  

$$\\text{f}(\\text{w}) = {\\sum\_{\\text{i} = 1}^{\\text{c}}\\text{f}\_{\\text{i}}}(\\text{w})$$  

## Results and discussion
