

多个团队和联盟正在致力于量子互联网，其中包括欧盟的量子互联网联盟（`https://twitter.com/eu_qia`）项目。量子互联网联盟正在荷兰启动一个四城示范项目，涵盖阿姆斯特丹、莱顿、海牙和代尔夫特等城市。它包含了创建大型量子宽域网络所需的所有组件，预计将于2020年投入运行。随后他们希望将项目扩展到整个欧盟。

## 其他量子网络

目前，所有现有的量子网络都相当有限且具有实验性，即使每天都在取得更多进展。2018年，基于光纤的量子密钥分发在421公里/261英里处成功演示。大多数可供商业销售的现有QKD系统的最大传输距离为100公里/62英里，因此该实验网络超过了四倍。预计量子QKD系统将不断扩展其传输距离。

中国尤其专注于量子信息科学的网络方面。2016年，中国发射了墨子（`https://www.bbc.com/news/world-asia-china-37091833`），即首颗基于量子的通信卫星。当卫星飞越上空时，它使用QKD将单个密钥安全地发送到北京和维也纳的地面站，两地相距7,500公里/4,700英里。然后它创建了一个第三密钥供各方共享。它用每个地面站先前传输的单个密钥对第三密钥进行加密。每个地面站都可以解密共享的第三密钥，并开始相互加密消息。这是具有里程碑意义的时刻。

墨子只能在视线范围内运行，且不能在阳光下运行；尽管如此，它仍成功演示了一次75分钟的视频会议通话，这对于第一代、首创的量子卫星来说已是相当充分的演示。你可以在这里阅读更多关于墨子的信息：`https://www.wired.com/story/why-this-intercontinental-quantum-encrypted-video-hangout-is-a-big-deal/`、`https://cosmosmagazine.com/technology/the-quantum-internet-is-already-being-built` 和 `https://en.wikipedia.org/wiki/Quantum_Experiments_at_Space:Scale`。中国还在上海和北京之间建设一条2,000公里/1,200英里的基于量子的通信骨干网。它连接4个城市，拥有32个节点。

> **NOTE**  一些量子信息科学家对中国的量子网络声明持怀疑态度，或怀疑其并非100%基于量子。

日本已演示了使用量子中继器的量子网络（`https://qiqb.otri.osaka-u.ac.jp/wp-content/uploads/2019/01/AllPhotonicQR-QIQBen.pdf`）。它使用光学器件作为量子中继器（称为*光子学*），这使其能够在无需经典组件且不使用量子存储器的情况下发送量子信息。

一个美国团队正在构建一条长48公里/30英里的量子网络，使用量子纠缠和量子隐形传态（`https://spectrum.ieee.org/tech-talk/telecom/security/us-national-labs-join-forces-on-a-quantum-network`）。大多数其他长距离量子网络使用QKD，但该由美国国家实验室资助的项目，由芝加哥附近牵头，将是首批使用隐形传态的项目之一。美国能源部提供了数百万美元。国家实验室（阿贡国家实验室和费米国家加速器实验室）与芝加哥大学共同组建了一个正式实体，即芝加哥量子交易所（`https://quantum.uchicago.edu/`）。它涉及超过100名量子信息科学研究人员。

基于量子的网络已在实验阶段投入运行，并在未来几年内将有多个现实世界项目和设备上线。

## 更多信息

Quantum Network, Rodney Van Meter, Wiley, 2017, `https://www.worldcat.org/title/quantum-networking/oclc/879947342`

The Quantum Internet Is Emerging, One Experiment at a Time, Anil Ananthaswamy, Scientific American magazine, June 19, 2019, `https://www.scientificamerican.com/article/the-quantum-internet-is-emerging-one-experiment-at-a-time/`

The Quantum Internet, H. J. Kimble, June 25, 2008, white paper, `https://arxiv.org/pdf/0806.4195.pdf`

A Poisson Model for Entanglement Optimization in the Quantum Internet, Laszlo Gyongyosi and Sandor Imre, Quantum Information Processing, June 5, 2019, `https://link.springer.com/content/pdf/10.1007%2Fs11128-019-2335-1.pdf`

The quantum internet has arrived (and it hasn't), Davide Castelvecchi, Nature Magazine, February 14, 2019, `https://www.nature.com/articles/d41586-018-01835-3`

Internet Research Task Force (IRTF) research group on quantum Internet called QIRG. Qirg mailing list submissions to `qirg@irtf.org`, To subscribe or unsubscribe via the World Wide Web, visit `https://www.irtf.org/mailman/listinfo/qirg`.

## 摘要

量子网络将像量子信息科学的其他部分一样发展和成熟，随着底层技术的进步而时断时续。量子网络将首先使用更多经典组件（如可信中继器）并使用QKD交换安全密钥，然后转向使用真正的量子中继器、量子纠缠、隐形传态和量子交换的完整基于量子的网络栈。有限的、实验性的网络很快将被真实的、运行的量子网络所取代。最终，我们的大部分，如果不是全部，经典互联网都将被量子网络所取代，原因多种多样，其中最不重要的就是量子力学提供的更强固有安全性。

所有前几章都涵盖了量子力学、计算、密码学，以及量子计算机为何可能很快破坏当今的公钥密码学。[Part II](#p02.xhtml)首先介绍了抗量子和基于量子的密码学。本章介绍了量子网络组件、挑战和可能的应用。[Chapter 9](#c09.xhtml)将介绍所有利益相关者应如何为即将到来的量子破解和革命做好准备。

# 9 现在开始准备

即将到来的量子密码学破解将会发生；只是时间问题。当它发生时，它将使世界大部分传统公钥密码学失效，并使其他现有密码学的强度至少减弱50%。而且这是在最佳情况下的情景，不包括任何其他可能使求解对称密码和哈希变得更简单的量子进步。

在前几章中，我们讨论了量子力学、量子计算机、网络以及即将到来的变化，包括可能的密码学破解。本章讨论你和你的组织如何在破解发生之前就开始今天的准备。本章可能是你们许多人购买这本书的原因。首先，我们将介绍任何后量子缓解项目的四个主要阶段，然后我们将重点介绍项目步骤。

## 四个主要后量子缓解阶段

大多数组织的后量子缓解项目将包括以下四个主要阶段：

* Stage 1: Strengthen current solutions.
* Stage 2: Move to quantum-resistant solutions.
* Stage 3: Implement quantum-hybrid solutions.
* Stage 4: Implement fully quantum solutions.

[Figure 9.1](#c09.xhtml#c09-fig-0001) 以图形方式展示了每个阶段。每个项目阶段将在以下章节中更详细地讨论。

### Stage 1: Strengthen Current Solutions

