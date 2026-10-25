# # A label noise filtering and label missing supplement framework based on game theory

Yuwen Liu $^{a}$, Rongju Yao $^{b}$, Song Jia $^{c}$, Fan Wang $^{f}$, Ruili Wang $^{d}$, Rui Ma $^{e}$, Lianyong Qi $^{a,*}$

$^{a}$ College of Computer Science and Technology, China University of Petroleum (East China), Qingdao 266580, China
$^{b}$ Weifang Key Laboratory of Blockchain on Agricultural Vegetables, Weifang University of Science and Technology, Shouguang, China
$^{c}$ China Unicom Tian Branch, China
$^{d}$ School of Natural and Computational Sciences, Massey University, New Zealand
$^{e}$ General Education Department, Shandong First Medical University, Shandong Academy of Medical Sciences, Tai’an, 271 000, China
$^{f}$ College of Computer Science and Technology, Zhejiang University, Hangzhou, China

+   - Label noise
+   - FastText
+   - Cosine similarity
+   - Game theory
+   - LSTM

Labeled data is widely used in various classification tasks. However, there is a huge challenge that labels are often added artificially. Wrong labels added by malicious users will affect the training effect of the model. The unreliability of labeled data has hindered the research. In order to solve the above problems, we propose a framework of Label Noise Filtering and Missing Label Supplement (LNFS). And we take location labels in Location-Based Social Networks (LBSN) as an example to implement our framework. For the problem of label noise filtering, we first use FastText to transform the restaurant's labels into vectors, and then based on the assumption that the label most similar to all other labels in the location is most representative. We use cosine similarity to judge and select the most representative label. For the problem of label missing, we use simple common word similarity to judge the similarity of users' comments, and then use the label of the similar restaurant to supplement the missing labels. To optimize the performance of the model, we introduce game theory into our model to simulate the game between the malicious users and the model to improve the reliability of the model. Finally, a case study is given to illustrate the effectiveness and reliability of LNFS.

# ## 1. Introduction

The Internet of things [1], mobile crowdsourcing [2] and other new technologies have been vastly popularized and applied in various industries, giving birth to massive data. The formation of such data is often inseparable from the participation of people. The hidden value of such data is huge. For many industries, how to use the big data is the key to win the market competition. With the continuous advancement of computer equipment, people have been able to deal with the large-scale data. However, as most of the data come from the network, its authenticity will be reduced by people's malicious behaviors. For example, in machine learning [3], a common work is to use labeled data to train neural networks for classification, regression or other purposes [4]. At this time, the quality of data will directly affect the model performance. The labels are often assigned by humans, and the task of labeling the data is time-consuming, laborious, and expensive. Some malicious marking behaviors will lead to massive label noise. Therefore, the influence of noise labels must be considered in practical application. We need a model that can accurately identify label noise to actively eliminate the impact of noise data.
Currently, people are happy to mark some popular locations to prove that they have been there. At the same time, users will leave their comments and label the restaurants where they have been to show how much they like the restaurants and help others to judge whether the restaurants are in line with their interests. Then other users can find their preferred restaurant by searching for different labels. An app such as Dianping [5] can achieve this function. However, the quality of such labels is uneven as they are labeled by various people. Some malicious users will add invalid labels to the location, making some labels accurate and authentic, some wrong or fuzzy [6]. Therefore, a very huge challenge is how to select a correct label for the location to help other users with real needs to search and filter out the inaccurate noise labels. We propose a label noise