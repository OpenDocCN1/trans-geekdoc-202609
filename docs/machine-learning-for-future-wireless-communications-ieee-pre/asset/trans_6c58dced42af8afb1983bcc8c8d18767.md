
一般而言，本章考虑由一组 ![images](images/c01-i0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="script">N</mi><mo>=</mo><mfenced open="{" close="}" separators=""><mrow><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>.</mo><mo>.</mo><mo>.</mo><mo>,</mo><mi>N</mi></mrow></mfenced></mrow></math> 的用户和一组 ![images](images/c01-i0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="script">K</mi><mo>=</mo><mfenced open="{" close="}" separators=""><mrow><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mo>.</mo><mo>.</mo><mo>.</mo><mo>,</mo><mi>K</mi></mrow></mfenced></mrow></math> 的共享正交信道组成的无线网络（例如正交频分多址 [`OFDMA`]）。在每个时隙开始时，每个用户选择一个信道并使用传输接入协议（例如 Aloha 型，或载波侦听多址 [`CSMA`] 型窄带传输）传输其数据。在信道 ![images](images/c01-i0003.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>k</mi></mrow></math> 上的传输如果在给定时隙内只有单个用户在信道 ![images](images/c01-i0004.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>k</mi></mrow></math> 上传输则成功。否则，会发生碰撞。本章中的算法适用于 `DSA` 的两种主要模型（Zhao and Sadler，[2007](#c01.xhtml#c01-bib-0094)）：一种分层模型，允许次级（未授权）认知用户在不干扰主级（授权）用户时使用频谱；另一种是用户之间的开放共享模型，它作为管理频谱区域的基础，其中通常不假设网络中存在主用户和次用户（例如工业、科学和医疗无线电 [`ISM`] 频段）。因此，在分层模型中，只有次级用户实现 `ML` 算法来学习环境以改善频谱利用率，而主用户则被建模为外部过程。这种情况在 [图 1.1](#c01.xhtml#c01-fig-0001) 中进行了说明。在开放共享模型中，所有用户都是认知用户，并应用 `ML` 算法来学习系统动态。

本章其余部分分为三个部分。[第 1.2 节](#c01.xhtml#c01-sec-0002) 重点介绍为 `DSA` 开发的在线学习算法，其中认知用户旨在在外部用户存在的情况下学习频谱占用情况以改善频谱利用率。因此，重点在于认知用户学习外部过程的速度，而非认知用户之间的交互。[第 1.3 节](#c01.xhtml#c01-sec-0012) 重点介绍更一般的模型，其中多个认知用户共享频谱，目标是以分布式方式有效地为认知用户分配信道以最大化某个全局目标。我们首先概述模型依赖的解决方案，然后重点介绍基于深度学习的用于 `DSA` 的人工智能 (`AI`) 算法的最新发展，这些算法能够有效地自适应复杂的现实世界环境。[第 1.4 节](#c01.xhtml#c01-sec-0022) 将提供进一步的讨论和结论。

![图 1.1 分层模型的说明，该模型允许次级（未授权）认知用户在不干扰主级（授权）用户时使用频谱。次级用户实现 ML 算法来学习环境以通过利用频谱空洞改善频谱利用率，而主用户则被建模为外部过程（即图中的占用频谱）。](images/c01f001.jpg)

[图 1.1](#c01.xhtml#R_c01-fig-0001) 分层模型的说明，该模型允许次级（未授权）认知用户在不干扰主级（授权）用户时使用频谱。次级用户实现 `ML` 算法来学习环境以通过利用频谱空洞改善频谱利用率，而主用户则被建模为外部过程（即图中的占用频谱）。

## 1.2 用于机会主义频谱接入的在线学习算法

### 1.2.1 网络模型
