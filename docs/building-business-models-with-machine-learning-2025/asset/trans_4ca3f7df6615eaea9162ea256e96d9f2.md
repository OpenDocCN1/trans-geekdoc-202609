
Ronald, M., Poulouse, A., & Han, D. S. (2021). iSPLInception: An inception-ResNet deep learning architecture for human activity recognition. IEEE Access: Practical Innovations, Open Solutions, 9, 68985-6901. DOI: 10.1109/ACCESS.2021.3078184

Sadowski, Jathan, Yolande Streangers, and Jenny Kennedy. Work for Big Mother: Revaluing care and control in smart homes. Environment and Planning A: Economy and Space, 2021.

Sovacool, B. K., & Dylan, D. (2020). Fursyer Del Rio. Smart home technologies in Europe: A critical review of concepts, benefits, risks, and policies. Renewable & Sustainable Energy Reviews, 120, 109663. DOI: 10.1016/j.rser.2019.109663

Tang, C. L., Perez-Pozuelo, I., Spathis, D., Brage, S., Wareham, N., & Mascolo, C. Selfhar: Improving human activity recognition through self-training with unlabeled data. arXiv preprint:2102.06073, 2021.

Wang, A., Chen, H., Zheng, C., Zhao, L., Liu, J., & Wang, L. Evaluation of random forest for complex human activity recognition using wearable sensors. In 2020 International Conference on Networking and Network Applications (NaA), pp. 310-315. IEEE, 2020. DOI: 10.1109/NaS51721.2020.00060

Wiecek, Alyssa, Fernanda S. Tonin, Andrea Torres-Robles, Shalom I. Benimoj, Fernando Fernandez-Limos, and Victoria Garcia-Cardenas. Temporal effectiveness of interventions to improve medication adherence: In A network meta-analysis, 2019.

Yadav, S. K., Tiwari, K., Pandey, H. M., & Akbar, S. A. (2021). A review of multimodal human activity recognition with special emphasis on classification, applications, challenges and future directions. Knowledge-Based Systems, 223, 106970. DOI: 10.1016/jknys.2021.106970

Yang, X. L., Chu, X., & Zhou, M-T. (2020). Fog-Enabled Smart Home and User Behavior Recognition. In Fog-Enabled Intelligent IoT Systems. Springer. DOI: 10.1007/978-3-030-23185-9_7

Yang, Y., Luo, X., Chu, X., & Zhou, M-T. (2020). Fog-Enabled Smart Home and User Behavior Recognition. In Fog-Enabled Intelligent IoT Systems, pages (pp. 185–210). Springer. DOI: 10.1007/978-3-030-23185-9_7

## 第 12 章
通过数据驱动创新彻底商业模式：Hudi 的案例

Giulia Rita Sala
ESADE, 西班牙

Saverio Barabuff
Scuola Superiore Sant'Anna, 意大利

Giulio Ferrigno
Scuola Superiore Sant'Anna, 意大利

Enrico Marcazzan
Scuola Superiore Sant'Anna, 意大利

### 摘要

本章探讨了数字转型时代大数据变现的演变轮廓，重点关注“人类数据收入”（Hudi）模型。基于关于大数据和创新管理的文献，以及所谓的“数据驱动创新”框架，本章探讨了将个人信息转化为资产过程中固有的挑战。为了为了地理解这些挑战，本章对 Hudi 进行了深度的案例研究分析，并评估了该商业模式对个人、企业和整个社会产生的影响，并对数据变现和价值创造提供了宝贵的见解。基于这些结果，本章有助于对数据经济演变格局中固含的机遇、挑战和后果有更深入的理解，从而塑造该领域未来的讨论和研究方向。

## 引言

在当今数字转型时代，企业日益意识到其海量数据储备中的内在价值（Mcafee et al., 2012）。将这些数据转化为有价值资产的紧迫性已成为旨在获得竞争优势、促进创新和增强决策过程组织的关键任务（Saggi & Jain, 2018; Terauchi & Buzangan, 2019）。

本文拟的书章节深入探讨了数据价值创造的复杂性，围绕遵循数据驱动创新（DDI）框架的人类数据创新（以下简称 Hudi）这一值得关注的案例（Zillner, 2021; Zollner, 2021b）。尽管由于技术进步、物联网和全球连接，数字格局见证了数据重要性的激增，但仅仅的数据堆积并不能保证价值创造（Cappa et al., 2021; Ferrigno et al., 2024; Gashahemei & Calic, 2020）。Hudi 的创新方法脱颖而出，它赋予个人数据所有权，并让他们积极参与数据市场，从而通过数据共享获得收入并捕捉内在价值。

本章详细介绍了 Hudi 的指导原则、战略倡议和运作机制，这些机制使得个人数据能够转化为有形且价值的资产。此外，还对支持安全透明交易的技术基础设施和平台进行了详细检查，并重点考虑了隐私保护和数据完整性。还深入探讨了围绕数据所有权、同意和使用的法律及伦理考量，解决了有关隐私和安全的担忧。

深度分析将批判性地评估 Hudi 模型对个人、企业和整个社会的潜在影响。本章通过文献综述、案例研究、利益相关者访谈和数据分析等严谨方法，为 Hudi 在数据变现方面的案例提供了宝贵的见解。总体目标是为数据转化为有价值资产的过程提供有意义的见解（Accinari et al., 2023; Cappa et al., 2021），强调了 Hudi 模型在重塑数据经济方面的变革力量。

总之，本章节是对新兴数据变现领域（Johnson et al., 2017; Wixom & Ross, 2017）和价值捕捉领域（Cappa et al., 2021）的探索。

## 文献背景

### 数据作为资产

在当代，企业日益意识到其海量数据储备中的内在价值（Mcafee et al., 2012）。将这些数据转化为有价值资产的紧迫性已成为旨在获得竞争优势、促进创新和增强决策过程组织的关键任务（Saggi & Jain, 2018; Terauchi & Buzangan, 2019）。

本文拟的书章节深入探讨了数据价值创造的复杂性，围绕遵循数据驱动创新（DDI）框架的人类数据创新（以下简称 Hudi）这一值得关注的案例（Zillner, 2021; Zollner  2021b）。尽管由于技术进步、物联网和全球连接，数字格局见证了数据重要性的激增，但仅仅的数据堆积并不能保证价值创造（Cappa et al., 2021; Ferrigno et al., 2024; Gashahemei & Calic, 2020）。Hudi 的创新方法脱颖而出，它赋予个人数据所有权，并让他们积极参与数据市场，从而通过数据共享获得收入并捕捉内在价值。

本章详细介绍了 Hudi 的指导原则、战略倡议和运作机制，这些机制使得个人数据能够转化为有形且价值的资产。此外，还对支持安全透明交易的技术基础设施和平台进行了详细检查，并重点考虑了隐私保护和数据完整性。还深入探讨了围绕数据所有权、同意和使用的法律及伦理考量，解决了有关隐私和安全的担忧。

深度分析将批判性地评估 Hudi 模型对个人、企业和整个社会的潜在影响。本章通过文献综述、案例研究、利益相关者访谈和数据分析等严谨方法，为 Hudi 在数据变现方面的案例提供了宝贵的见解。总体目标是为数据转化为有价值资产的过程提供有意义的见解（Accinari et al., 2023; Cappa et al., 2021），强调了 Hudi 模型在重塑数据经济方面的变革力量。

总之，本章节是对新兴数据变现领域（Johnson et al., 2017; Wixom & Ross, 2017）和价值捕捉领域（Cappa et al., 2021）的探索。

*(注：原文中存在大量重复段落已根据“不要重复输出原文”的原则，在译文中仅保留核心翻译内容)*

