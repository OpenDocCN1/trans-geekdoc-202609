
除了潜在的安全顾虑外，联邦学习还有若干约束，使其无法成为解决我们所有数据隐私问题的灵丹妙荐。值得注意的是，联邦学习训练模型所需的本地设备算力和内存比传统机器学习技术多得多。然而，许多现代设备性能足以胜任这些任务，且该策略还能大幅减少传输到中心服务器的数据量，从而降低数据使用量。如果设备电量充足，这种权衡对许多用户而言可能是有利的 [11]。

另一个技术难题是带宽。与在数据中心进行的标准机器学习不同，联邦学习通过 WiFi 或 4G 网络进行。这些节点间繁忙节点与服务器使用的带宽速率比 WiFi 或 4G 低几个数量级。随着时间的推移，设备带宽的增长速度远不如设备算力；因此，带宽限制可能导致延迟增加，且学习过程比传统方法更漫长。如果在设备运行时进行算法训练，会降低设备性能。Google 找到了解决方案：仅在设备开启、插电且闲置时进行训练。这解决了问题，但由于训练只能在非高峰时段进行，导致学习过程变慢 [12]。

设备在训练过程中掉线是另一个问题；设备可能被用户使用、关机或遭遇其他干扰。无法使用掉线设备的数据可能导致算法模型精度下降。从联邦学习的构想到落地的过渡并非一帆风顺。包括独立于联邦学习倡导者之外的研究人员在内，都帮助加深了对相关挑战的认识 [8, 11]。

虽然已有研究探讨联邦学习的有效性和准确性，但在我看来，以下列出的安全相关难题更为迫切。

### 推理攻击

保护客户数据的机密性是联邦学习的驱动力。

### 模型投毒

一些学者研究了不守规矩的客户植入后门或发起女巫攻击以投毒全局模型的想法。

随机梯度下降中的定向投毒攻击。红色虚线向量代表女巫节点的贡献，将模型引向投毒者的目标。如图 5 所示，实心绿色向量由忠诚客户提供，致力于达成真实目标。

![图 5. 基于目标的定向投毒。](img/fig9_5_C.jpg)

图 5. 基于目标的定向投毒。

联邦学习是一种相对较新的训练方法，在多种用途上展现出前景。由于该技术仍处于研究的早期阶段，因此需要更多调查，目前无法评估其所有潜在应用，也无法评估其可能面临的所有信任和隐私威胁。在此之前，很难精准预测该策略在未来将被广泛采用的程度。好消息是，Google 的 Gboard 已在现实世界中成功应用 [15]。

尽管如此，鉴于前述一些缺点，联邦学习不太可能在所有情况下完全取代传统学习模式。未来也将取决于我们主要互联网巨头对保护隐私的重视程度。目前我们有充分理由保持怀疑。

## 联邦学习在医疗保健领域面临的挑战

尽管联邦学习有诸多优势，但必须记住，与传统机器学习技术一样，联邦学习仍面临偏见、标准化和数据质量等性能问题。此外，在医疗数据背景下，联邦学习还面临以下挑战 [9, 11, 15]：

*   **数据多样性** — 医疗数据本质上复杂且多样。既有结构化形式，也有非结构化形式。数据采集差异、医疗设备品牌和地区人口统计特征等因素也会影响数据的多样性。整合来自多个来源的数据和信息可能颇具挑战。数据在合作高校之间可能分布不均。

### 保密性与安全性

即使联邦学习提供的隐私保护远强于传统机器学习模型，它仍然存在一些隐私和安全风险。信息泄露给竞争方是一种可能性。在使用联邦学习时，可能需要进行权衡，因为在某些情况下，其性能可能比使用常规机器学习模型时略差。研究人员正在研究差分隐私，以给联邦学习提供额外一层隐私保护。

### 可追溯性与责任归属

医疗 AI 解决方案必须具备可复现性和可解释性。然而，在联邦学习中，我们面对的是在网络、硬件和软件差异巨大的环境下进行的多方计算。因此，研究人员难以检查实际数据，以解释任何异常或意外的结果，或通过预测原型来揭示原因。

### 流程设计

支持访问各机构所存数据和控制权的联邦学习架构，需要考虑数据真实性、编码格式以及各异的计算能力要求。

## 联邦学习在医疗健康领域的未来

近年来，我们都已熟悉发展中技术对我们生活诸多方面的重要性及影响。技术在我们生活中扮演着重要角色，无论是迎合我们偏好的智能手机应用程序，还是利用 AI 协助临床医生进行诊断。在机器学习 (ML) 和深度学习 (DL) 中，为了从病理学、遗传学、放射学、癌症等产生的医疗数据 [[20]](#ch9.xhtml#ref9_20) 中获取洞见，我们在医疗健康领域实现了人工智能创新的跨越式发展。

为了从放射学、病理学等收集的医疗数据中获取洞见，我们在医疗健康领域实现了人工智能创新的跨越式发展，特别是在机器学习 (ML) 和深度学习 (DL) 方面。近年来，我们都已熟悉发展中技术对我们生活诸多方面的重要性及影响。技术在我们生活中扮演着重要角色，无论是发掘我们偏好的智能手机程序，还是利用人工智能帮助医生诊断 [[17]](#ch9.xhtml#ref9_17)。

然而，医疗行业的数据不仅组织混乱且极其敏感。此外，为了维护数据安全、数据访问权和隐私权，必须充分尊重特定国家的监管问题，如 NMPA (中国)、FDA (美国)、CDSCO (印度)、GDPR (欧洲) 等。除了数据量巨大外，数据还包含大量非结构化内容和敏感患者信息，地理分布广泛，且缺乏跨各种设备和制造商的兼容性。

例如，AI 已显示出协助放射科医生进行计算机辅助分析和诊断的能力。然而，鉴于收集、整理和保存具有多样化人群的高质量数据的困难，仅凭小数据集创建无偏见的有效模型仍然很难。这也耗费大量时间、金钱和精力。医疗和生命科学专业人员可利用联邦学习 (FL) 的优势，通过联合开发算法来处理隐私、数据完整性和治理问题，数据保留在医院防火墙后，仅共享模型 [[18]](#ch9.xhtml#ref9_18)。

近期研究表明，FL 训练的模型性能可优于在中心托管数据集上训练的原型，以及仅见过孤立单机构数据的模型。联邦学习跨多个人口统计学特征检查患者，收集更广泛的数据变异性。例如，在获得电子健康信息的前提下，FL 可协助识别临床上可比的受影响人群，并预测因心脏事件、死亡及 ICU 住留时长导致的住院情况。FL 最初是为包括门诊和边缘设备用例在内的多个领域而创建，但最近在医疗健康应用中获得了流行 [[19]](#ch9.xhtml#ref9_19)。

FL 可协助开发用于 X 光、超声、计算机断层扫描、磁共振成像和正电子发射成像中器官分割的模型，以及针对疾病特异性成像技术的肿瘤表征。通过提供获取更多数据变异性和跨不同人口统计学特征评估患者的机会，FL 未来可实现革命性改进。

研究表明，FL 生成的原型性能更好，且比在特定机构数据上训练的模型具有更强的泛化能力。作为 Health Chain 项目的一部分，一个 FL 框架将在法国四家机构中创建并实施。利用此技术，黑色素瘤和乳腺癌患者可预估其治疗效果。这也能帮助肿瘤科医生根据患者的皮肤镜检查或显微解剖图像，确定每位患者的最佳治疗方案。FL 还可用于增强学术研究。例如，2020 年，美国放射学会、Diagnostics da America、Partners HealthCare、俄亥俄州立大学和斯坦福医学院利用联邦学习创建了更准确的预测模型，用于确定乳腺 X 光检查中的乳腺组织密度。

此外，遵循“FAIR”原则——可查找、可访问、可互操作、可复用——编译数据，使得可能来自复杂自主算法的数据在很大程度上变得清晰可懂。例如，以统一资源标识符 (URI) 和公开可访问的本体等广泛认可的词汇表显示数据，可能助力许多该领域研究者克服从国际医疗机构检索的临床数据中的语言障碍。通过将 FL 与 FAIR 原则相结合，可从大规模数据集中获得全球适用的临床洞见。

包括医生、患者、医院、AI 研究人员和医疗服务提供者在内的众多利益相关者，可能会受到联邦学习的重大影响。尽管 FL 优势明显，研究人员和 AI 开发者仍必须仔细考虑研究设计、临床流程选择、数据分类和数据价值，以减少模型偏见。联邦学习是保障可靠、安全、无偏见数据模型的一个潜在思路。FL 通过允许多方在无需交换或整合数据集的情况下协同训练，克服了与敏感医疗数据相关的挑战。联邦学习将极大地影响精准医疗，也有潜力在全球范围内改善患者护理。

### 7. 结论

正如机器学习展望声明所述，联邦学习具有变革性能力，可将 AI 现代化引入医疗路线图。修订地区隐私法、建立充分的标准化代码共享程序和 IT 基础设施，或为合作伙伴制定公平的薪酬计划，这些仅是联邦学习中仅能通过协作解决的部分跨学科难题。联邦学习合作必须持续进化，才能在未来复杂的医疗环境中取得成功。借助此方法，信息共享取得了重大进展，医院在机器学习方面的协作变得更加高效。通过利用前沿机器学习和深度学习技术，它规避并克服了处理高度敏感医疗数据的挑战。

### 参考文献

## 第 10 章 医疗系统中的协作联邦学习

*Bini M Issac*^(¹⁰)

邮箱：binimissac@amaljyothi.ac.in

### 参考文献

1.  网站： [`owkin.com/publications-and-news/blogs/federated-learning-in-healthcare-the-future-of-collaborative-clinical-and-biomedical-research`](https://owkin.com)。

2.  网站： [`www.comparitech.com/blog/information-security/federated-learning/`](https://www.comparitech.com)。

3.  网站： [`www.sundeepteki.org/blog/federated-machine-learning-for-healthcare`](https://www.sundeepteki.org)。

4.  网站： [`bluesteens.medium.com/federated-learning-in-healthcare-7a380ffc01f9`](https://bluesteens.medium.com)。

5.  Thomas, G.A.S. and Robinson, Y.H. 2020. IoT, Big Data, Blockchain and Machine Learning Besides Its Transmutation with Modern Technological Applications. Springer 书籍章节——物联网与大数据应用（智能系统参考丛书 ISRL，第 180 卷），2020 年 2 月 25 日，第 47–63 页，ISSN: 978-3-030-39118-8。

6.  [`medium.datadriveninvestor.com/an-overview-of-federated-learning-8a1a62b0600d`](https://medium.datadriveninvestor.com)。

7.  Thomas, G.A.S. and Robinson, Y.H. 2020. Real-Time Health System (RTHS) Centered Internet of Things (IoT) in Healthcare Industry: Benefits, Use Cases and Advancements in 2020. Springer’s Multimedia Technologies in the Internet of Things Environment (Scopus Indexed), 2020 年 9 月 29 日，ISSN: 978-981-15-7965-3。

8.  网站： [`medium.datadriveninvestor.com/an-overview-of-federated-learning-8a1a62b0600d`](https://medium.datadriveninvestor.com)。

9.  网站： [`medium.com/mlearning-ai/whats-federated-learning-and-why-it-s-key-to-the-future-of-medical-ai-e53c6869a849`](https://medium.com)。

10.  Rieke, N. and Hancox, J. 2020. The future of digital health with federated learning. npj Digital Medicine, volume 3, Article number: 119。

11.  Li, T., Sahu, A.K., Talwalkar, A. and Smith, V. 2020. Federated learning: Challenges, methods, and future directions. IEEE 2020: Signal Processing Magazine, 37: 50–60。

12.  Yang, Q., Liu, Y., Chen, T. and Tong, Y. 2019. Federated machine learning: Concept and applications. ACM Trans. Intell. Syst. Technol. (TIST), 10: 12。

13.  Kairouz, P., Sen Zhao and Zheng Xu. 2019. Advances and open problems in federated learning. arXiv preprint arXiv:1912.04977。

14.  Lee, J., Li Xiong and Dawn Song. 2018. Privacy-preserving patient similarity learning in a federated environment: Development and analysis. JMIR Med. Inform., 6: e20。

15.  Brisimi, T.S. and Chaoyang He. 2018. Federated learning of predictive models from federated electronic health records. Int. J. Med. Inform., 112: 59–67。

16.  网站： [`blogs.nvidia.com/blog/2021/09/15/federated-learning-nature-medicine/`](https://blogs.nvidia.com)。

17.  网站： [`www.expresshealthcare.in/blogs/guest-blogs-healthcare/the-future-of-federated-learning-in- healthcare/430940/`](https://www.expresshealthcare.in)。

18.  Rieke, N., Hang Qi and Ziteng Sun. 2020. The future of digital health with federated learning. Nature Partner Journal Digital Medicine, 3: 119. [`doi.org/10.1038/s41746-020-00323-1`](https://doi.org/10.1038/s41746-020-00323-1)。

19.  Kalendralis, P., Hang Qi and Zheng Xu. 2020. FAIR-compliant clinical, radiomics and DICOM metadata of RIDER, interobserver, Lung1 and head-Neck1 TCIA collections, 47(11): November 2020, Medical Physics。

20.  Li, X. and Weikang Song. 2020. Multi-site fMRI analysis using privacy-preserving federated learning and domain adaptation: ABIDE results. Medical Image Analysis, 101765。

21.  Vaid, A. and Sanmi Koyejo. 2020. Federated learning of electronic health records improves mortality prediction in patients hospitalized with COVID-19. medRxiv。

22.  Chen, S. and Daniel Ramage. 2020. FL-QSAR: A Federated Learning-based QSAR prototype for collaborative drug discovery. Bioinformatics, 5492–5498。

### 1. 简介

过去几年里，机器学习算法一直被用于执行疾病预测或检测等复杂任务。然而，机器学习算法的准确性取决于用于创建模型的数据。此外，使用这些算法时数据隐私是一个关注点，因为如果存储这些数据的服务器遭到攻击，数据可能会泄露。在标准的机器学习场景中，客户端将其数据发送到中央服务器，服务器将来自不同客户端的数据合并并用于训练模型。但这带来了严重的安全风险，特别是在医疗领域，因为数据在客户端和服务器之间传输时可能会泄露。医疗领域的研究涉及大量健康信息的收集、存储和传输，如果安全性受到威胁，这些健康信息可能会被不当访问。如果患者的错误信息泄露，可能会给患者带来诸多问题，如社会或心理问题、失业、失去医疗保险等。
