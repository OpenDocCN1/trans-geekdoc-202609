
39. Zhou, M.; Ding, Z.; Tang, J.; Yin, D. Micro behaviors: A new perspective in e-commerce recommender systems. In Proceedings of the Eleventh ACM International Conference on Web Search and Data Mining, Los Angeles, CA, USA, 5–9 February 2018; pp. 727–735.
40. Zdziebko, T.; Sulikowski, P. Monitoring Human Website Interactions for Online Stores. In New Contributions in Information Systems and Technologies; Advances in Intelligent Systems and Computing; Springer: Cham, Switzerland, 2015; Volume 354, pp. 375–384.
41. Tian, G.; Wang, J.; He, K.; Sun, C.; Tian, Y. Integrating implicit feedbacks for time-aware web service recommendations. Inf. Syst. Front. 2017, 19, 75–89. [CrossRef]
42. Liversedge, S.P.; Drieghe, D.; Li, X.; Yan, G.; Bai, X.; Hyönä, J. Universality in eye movements and reading: A trilingual investigation. Cognition 2016, 147, 1–20. [CrossRef]
43. Buscher, G.; Dengel, A.; Biedert, R.; Van Elst, L. Attentive documents: Eye tracking as implicit feedback for information retrieval and beyond. ACM Trans. Interact. Intell. Syst. 2012, 1, 1–30. [CrossRef]
44. Xu, S.; Jiang, H.; Lau, F.C. User-oriented document summarization through vision-based eye-tracking. In Proceedings of the 13th International Conference on Intelligent User Interfaces (IUI’09), Sanibel Island, FL, USA, 8–11 February 2009; ACM: New York, NY, USA, 2009; pp. 7–16.
45. Loyola, P.; Brunetti, E.; Martínez, G.; Velásquez, J.D.; Maldonado, P. Leveraging Neurodata to Support Web User Behavior Analysis. In Wisdom Web of Things; Zhong, N., Ma, J., Liu, J., Huang, R., Tao, X., Eds.; Web Information Systems Engineering and Internet Technologies Book Series; Springer: Cham, Switzerland, 2016; pp. 181–207.
46. Sheng, H.; Lockwood, N.S.; Dahal, S. Eyes Don’t Lie: Understanding Users’ First Impressions on Websites Using Eye Tracking. In Human Interface and the Management of Information. Information and Interaction Design, Proceedings of the 15th International Conference, HCI International 2013, Las Vegas, NV, USA, 21–26 July 2013; Lecture Notes in Computer Science; Yamamoto, S., Ed.; Springer: Berlin/Heidelberg, Germany, 2013; Volume 8016, p. 8016.
47. Sharafi, Z.; Shaffer, T.; Sharif, B.; Guéhéneuc, Y.-G. Eye-Tracking Metrics in Software Engineering. In Proceedings of the 2015 Asia-Pacific Software Engineering Conference, New Delhi, India, 1–4 December 2015; IEEE Press: Piscataway, NJ, USA, 2015; pp. 96–103.
48. Lee, J.; Ahn, J.-H.; Park, B. The effect of repetition in internet banner ads and the moderating role of animation. Comput. Hum. Behav. 2015, 46, 202–209. [CrossRef]

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_253_0.png)

© 2020 by the authors. Licensee MDPI, Basel, Switzerland. This article is an open access article distributed under the terms and conditions of the Creative Commons Attribution (CC BY) license (http://creativecommons.org/licenses/by/4.0/).

## Article

## Generative Adversarial Network-Based Neural Audio Caption Model for Oral Evaluation

Liu Zhang, Chao Shu, Jin Guo, Hanyi Zhang, Cheng Xie * and Qing Liu

School of Software, Yunnan University, Kunming 650504, China; zhangliu@mail.ynu.edu.cn (L.Z.); shuchao_shanty@126.com (C.S.); jingguo@mail.ynu.edu.cn (J.G.); miukkazhang@outlook.com (H.Z.); liuqing@ynu.edu.cn (Q.L.)

* Correspondence: xiecheng@ynu.edu.cn

Received: 1 February 2020; Accepted: 2 March 2020; Published: 3 March 2020

## Abstract:

Oral evaluation is one of the most critical processes in children’s language learning. Traditionally, the Scoring Rubric is widely used in oral evaluation for providing a ranking score by assessing word accuracy, phoneme accuracy, fluency, and accent position of a tester. In recent years, by the emerging demands of the market, oral evaluation requires not only providing a single score from pronunciation but also in-depth, meaning comments based on content, context, logic, and understanding. However, the Scoring Rubric requires massive human work (oral evaluation experts) to provide such deep meaning comments. It is considered uneconomical and inefficient in the current market. Therefore, this paper proposes an automated expert comment generation approach for oral evaluation. The approach first extracts the oral features from the children’s audio as well as the text features from the corresponding expert comments. Then, a Gated Recurrent Unit (GRU) is applied to encode the oral features into the model. Afterwards, a Long Short-Term Memory (LSTM) model is applied to train the mappings between oral features and text features and generate expert comments for the new coming oral audio. Finally, a Generative Adversarial Network (GAN) is combined to improve the quality of the generated comments. It generates pseudo-comments to train the discriminator to recognize the human-like comments. The proposed approach is evaluated in a real-world audio dataset (children oral audio) collected by our collaborative company. The proposed approach is also integrated into a commercial application to generate expert comments for children’s oral evaluation. The experimental results and the lessons learned from real-world applications show that the proposed approach is effective for providing meaningful comments for oral evaluation.

## Keywords:

oral evaluation; generative adversarial network; neural audio caption; gated recurrent unit; long short-term memory

## 1. Introduction

Oral evaluation is a language-testing process, which includes pronunciation accuracy, fluency, integrity, logical ability, understanding ability and so on. Among them, the evaluation of logical ability and understanding ability generally requires more personalized expert comments, rather than a single score. Oral evaluation plays an important role in the process of language learning. Now there are some products and standards available in the market for oral evaluation [1–3]. However, most of these approaches are based on the Scoring Rubric [4] that only focuses on the pronunciation characteristics but ignoring the semantic characteristics, such as context, content, logic, or understanding, of the oral expression. It leads to current oral evaluation that can only provide a single ranking score [2]. It cannot provide meaningful comments for the oral evaluation. In order to improve the quality of the oral evaluation, some companies thus hire massive experts to generate comments for the evaluation manually. However, it is expensive and inefficient that not all companies could bear it. Therefore, automated comment generation in oral evaluation becomes the emerging demand that markets are chasing. The emerging demand requires machines to imitate expert to generate expert comments for the oral expressions. It is a comprehensive problem that combines speech recognition [5], natural language generation [6], and deep learning [7]. This new interdisciplinary study is challenging. It not only requires the machine to recognize the audio features from oral speech but also requires the machine to understand the relationships between audio features and corresponding comments. There is still no mature product/method in the market that can automatically generate expert comments for oral evaluation.

With the rapid development of artificial intelligence technology [8–10], a new possible solution for automated oral evaluation emerges gradually. Our previous work had tried to apply the caption generation model to generate expert comment for the oral evaluation [11]. In this work, we optimize the previous model. In detail, a Neural Audio Caption Model (NACM) is proposed to generate expert comments from the oral audio. In NACM, based on Gate Recurrent Unit [12], an elaborate encoder-decoder structure is designed for the mapping learning between audio features and text features. Afterwards, a recurrent structure is designed by combing Generative Adversarial Network (GAN) [13] with NACM. The new model is called Generative Adversarial Network-based Neural Audio Caption Model (GNACM). Compared with the previous work, GNACM can produce more accurate and complete expert comment for the oral evaluation. Figure 1 shows the overall framework of the proposed approach.

As shown in Figure 1, the input of the model is the oral audio to be evaluated. Section 3.1 will introduce the detail of audio feature extraction. The output of the model is the generated comments according to the input oral audio. The mappings between oral audio and comments are trained in NACM. Section 3.2 will provide the structure of NACM. The generated comments are further trained through the Discriminator to improve the quality of the comments. Section 3.3 will explain the detail of GNACM. In summary, the work has the following contributions:

- We propose a model called NACM that can generate expert comment for the oral audio.
- Based on NACM, we propose an improved model called GNACM that can generate more accurate and complete expert comment for the oral audio.
- Beyond the Scoring Rubric approach, the work is the early try to generate expert comments for the oral evaluation.

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_255_0.png)

Figure 1. The overview of the proposed approach for the oral evaluation.
