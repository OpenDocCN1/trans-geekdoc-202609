
多源域自适应（MSDA）通过引入多个源模型的知识，扩展了标准的无监督域自适应（UDA）设置。隐空间变换方法[`/path.to/xxx`]旨在通过优化差异度量或对抗损失，使不同域的特征对齐。基于差异的方法通过最小化最大均值差异[`/path.to/xxx`]和Rényi-差异[`/path.to/xxx`]等度量来对齐域。对抗方法通过优化GAN损失[`/path.to/xxx`]，使多个域的特征对域判别器不可区分，从而实现域适应。Wasserstein距离[`/path.to/xxx`]和ℋ![si5_e](images/S0169716122000566/si5_e.png)-差异[`/path.to/xxx`]也是对抗方法的一种形式。域生成方法[`/path.to/xxx`]利用某种形式的域翻译，如CycleGAN[`/path.to/xxx`]，在像素级别进行适应。所有这些方法都假设在适应过程中可以访问源数据。

###  2.4: Source-free multisource UDA

这一研究方向非常新，最初在[`/path.to/xxx`]中提出并解决。通过优化合适的源权重，将多个源模型的知识转移到未标注的目标域，是本论文的核心思想，将在下一节中详细讨论。受此工作启发，一些近期工作也 tackled 这个问题。[`/path.to/xxx`]从理论和实证两方面展示了对目标域数据进行选择性伪标记的好处，而[`/path.to/xxx`]则设计了置信锚诱导伪标记生成器，在无源域设置下为目标域挖掘置信伪标记。与这些工作密切相关，我们关注一种新颖的模型聚合方案，该方案通用且可在现有任何方法上使用以提升性能。在本章中，我们仅分析该模型聚合方案对[`/path.to/xxx`]中算法的影响。

##  3: Problem setting

本文解决了在只获得目标域未标注样本的情况下，同时适应在多个域上训练的多个模型的问题。我们将考虑具有K个类别的分类模型，输入空间为𝒳![si6_e](images/S0169716122000566/si6_e.png)。形式上，设有源模型集合{`θ`[*S*][*j*]^(*j* = 1)^(*n*)![si7_e](images/S0169716122000566/si7_e.png}，其中第j^(*th*)个模型`θ`[*S*][*j*]:𝒳→ℝ^(*K*)![si8_e](images/S0169716122000566/si8_e.png)是使用源数据集𝒟[*S*][*j*] = {`x`[*S*][*j*][*i*], `y`[*S*][*j*][*i*]}[*i* = 1]^(*N*[*j*])![si9_e](images/S0169716122000566/si9_e.png)训练得到的分类模型，其中N[*j*]为第j个源的数据点数，`x`[*S*][*j*][*i*]![si10_e](images/S0169716122000566/si10_e.png)和`y`[*S*][*j*][*i*]![si11_e](images/S0169716122000566/si11_e.png)分别表示第i个源图像和对应的标签。现在，给定目标未标注数据集𝒟[*T*] = {`x`[*T*][*i*]}[*i* = 1]^(*N*[*T*])![si12_e](images/S0169716122000566/si12_e.png），问题在于仅利用已学好的源模型，在不访问源数据集的前提下，学习一个分类模型`θ`[*T*]:𝒳→ℝ^(*K*)![si13_e](images/S0169716122000566/si13_e.png）。注意，这与文献中大多数多源域自适应方法不同，后者在学习目标模型`θ`[*T*]时也会利用源数据。

Since our proposed framework is built upon the first work on source-free multisource UDA (DECISION) ([`/path.to/xxx`]), we will first discuss DECISION in detail and then move on to the analysis of the modification we made.

##  4: Practical motivation

To understand the practicality of this specific problem setting, we provide example of some real applications. For example, let's say we want to classify some images in the target which belong to the domain *sketches*. We also have access to the trained source models which are trained on domains like *Art*, *Clipart*, *Product*, *Real*, etc. Images from *Art* domain are mostly visually and semantically similar to *sketches* domain compared to other sources. So, intuitively most images from the target domain should acquire highest adaptation performance from the *Art* domain. However, in practical scenarios these source images are not available and as a result there is no way of computing similarities between source and target images directly, which are crucial for computing weights for the corresponding sources given the target image. In this situation, this problem setting comes into play where the target images are adapted by the source models without accessing the source data. During adaptation, each of the target images should accordingly weight the source models based on just the source model parameters.

##  5: Overall framework of DECISION ([Ahmed et al., 2021](#Ch005_81-105_S0169716122000566.xhtml#bb0015))&#x2014;A review

Each of the source models can be decomposed into two modules: the feature extractor `ϕ`[*S*][*i*]:𝒳→ℝ^(*d*[*i*])![si14_e](images/S0169716122000566/si14_e.png) and the classifier `ψ`[*S*][*i*]:ℝ^(*d*[*i*])→ℝ^(*K*)![si15_e](images/S0169716122000566/si15_e.png). Here, *d*[*i*] refers to the feature dimension of the *i*th model, while *K* refers to the number of categories. The overall aim is to estimate the target model `θ`[*T*] ([Fig. 2](#Ch005_81-105_S0169716122000566.xhtml#f0015)) by combining knowledge only from the given source models in a manner that automatically rejects poor source models, i.e., those which are irrelevant for the target domain.

![Fig. 2 Overall framework of DECISION (Ahmed et al., 2021): Final classification layers of all the sources are frozen and the source feature encoders are jointly optimized along with their corresponding weights to get the target predictor by combining those.](images/S0169716122000566/f05-02-9780443184307.jpg)

[Fig. 2](#Ch005_81-105_S0169716122000566.xhtml#B-f0015) Overall framework of DECISION ([Ahmed et al., 2021](#Ch005_81-105_S0169716122000566.xhtml#bb0015)): Final classification layers of all the sources are frozen and the source feature encoders are jointly optimized along with their corresponding weights to get the target predictor by combining those.
