
DL 算法可用于利用生成模型生成音乐、诗歌、绘画，以及真实人物的声音和图像。模型可以生成合成内容，包括真实人物的虚假视频。目前尚不清楚如何同时保护这些人的个人权利和这些视频制作者的言论自由权。另一个挑战是生成模型的训练数据集可能包含受版权保护的材料，且尚不清楚如何保护原作者的权利。在美国，受版权保护的材料可用于训练搜索算法（使用判别模型而非生成模型）\[Wik20\]。

这些挑战也是扩大公众对 DL 认知度的动机，以便社会能够共同找到更好的应对方式。

## 10.6 结论性说明

DL 系统的采用正在迅速增长并改善了许多技术和服务。本书涵盖了超大规模计算公司在大型 DL 生产系统中使用的算法、硬件和编译器。我们分析了商业应用中使用的计算图或拓扑结构的基本构建块或原语。我们解释了在超大规模计算公司、学术界和规模较小的公司中常见的不同类型的工作负载，并强调了推荐模型的重要性及普遍性。我们提供了训练和调试模型的指南，使其能够泛化到训练数据集之外的数据，推荐使用 `Ranger`、`Adam`、`SGDM` 和 `LARS` 优化器来训练模型，并解释了如何通过反向传播将梯度计算为一系列乘法和加法。我们强调了找到能实现高硬件利用率和低训练时间的批大小的好处。

随着单节点上的训练时间变得 prohibitively 长，且某些模型大小超过节点的内存容量，分布式训练变得必要并在超大规模计算公司中得到使用。我们提供了分布式训练的指南，并建议对大型模型采用混合方法：数据并行在超节点组之间使用，模型并行在每个超节点内部使用，每个超节点包含 4–8 个节点。我们强调了流水线并行作为改进模型并行的有前景的方法，这对于具有大 SRAM 的硬件平台尤其有益，可尝试消除大部分 DRAM 访问。然而，还需要进一步的进展来缓解权重更新停滞并获得广泛采用。

内存带宽是训练和部署模型时的常见瓶颈。我们讨论了各种较小的数值格式以减小模型大小，这缓解了该瓶颈并导致每个管芯面积拥有更多 FPU 单元。我们建议生产训练硬件支持 `bf16`、`fp16` 和 `fp32` 计算，而推理硬件支持 `fp16`、`bf16`、`fp8`、`int8` 以及部分 `fp32` 计算。我们还强调了在各种工作负载中使用 `int8` 时的统计性能损失。基于 Hessian 的方法可以指导可量化层的选择并缓解该损失。

快速的拓扑和算法创新推动了采用灵活平台以支持广泛的工作负载，包括分离的 CPU 与加速器比例、标准外形模块以及用于扩展架构的行业标准互连。我们讨论了用于 DL 的各种硬件设计中性能与易编程性之间的权衡，包括软件管理内存的挑战以及提取高性能的复杂性。

编译器是 DL 系统的核心，可有效将程序降低到目标硬件。我们详细介绍了各种优化传递，并强调了操作融合和循环分块作为减少内存访问并高效使用本地内存的关键优化。我们讨论了流行框架 `TensorFlow` 和 `PyTorch` 的特性，以及编译器 `TVM` 和 `XLA` 等。推进编译器对于促进生态系统的进入和竞争力至关重要。

我们正处于 DL 系统的早期阶段，有令人兴奋的方向可探索，也有挑战需要克服。其中最有前景的机会之一是使用 ML 算法来改进 DL 系统栈。我们回顾了潜在的 ML for DL 用例，并强调了社区需要解决的一些挑战。

我希望本书中你所学的概念能帮助你更好地与数据科学家、硬件工程师以及编译器和性能工程师合作，以应对计算、带宽和内存需求，解决社会性挑战，利用 ML 改进 DL 系统，并为这一令人兴奋的领域做出贡献。感谢你对 DL 系统的兴趣以及投入学习本书的时间。

## Bibliography

\[ABC+16\] M. Abadi, P. Barham, J. Chen, et al. TensorFlow: a system for large-scale machine learning. *OSDI*, 2016. 184

\[ACG+16\] M. Abadi, A. Chu, I. Goodfellow, H. McMahan, I. Mironov, K. Talwar, and L. Zhang. Deep learning with differential privacy. CCS, Oct. 2016. 203

\[AA16\] M. Abadi and D. Andersen. Learning to protect communications with adversarial neural cryptography. Oct. 2016. 203

\[AGM+18\] J. Adebayo, J. Gilmer, M. Muelly, I. Goodfellow, M. Hardt, and B. Kim. Sanity checks for saliency maps. *NeurIPS*, Dec. 2018. 205

\[ARS+20\] D. Abts, J. Ross, J. Sparling, et al. Think fast: a tensor streaming processor (TSP) for accelerating deep learning workloads. *ISCA*, Jun. 2020. 154

\[AMP+19\] A. Agrawal, A. Modi, A. Passos, et al. TensorFlow Eager: a multi-stage, Pythonembedded DSL for machine learning (slides). *MLSys*, Feb. 2019. 186, 187

\[AAB+19\] Z. Ahmed, S. Amizadeh, M. Bilenko, et al. Machine learning at Microsoft with ML .NET. *SIGKDD*, Jul. 2019. 201

\[ALV08\] M. Al-Fares, A. Loukissas, and A. Vahdat. A scalable, commodity data center network architecture. *SIGCOMM*, Oct. 2008. 150

\[Ali20\] Alibaba. Machine Learning Platform for AI. 2020. 201

\[Ala18\] J. Alammar. The illustrated transformer. June 2018. 64

\[AHJ+18\] D. Alistarh, T. Hoefler, M. Johansson, S. Khirirat, N. Konstantinov, and C. Renggli. The convergence of sparsified gradient methods. *NeurIPS*, Dec. 2018. 102

\[AVG+15\] L. Alvarez, L. Vilanova, M. Gonzalez, X. Martorell, N. Navarro, and E. Ayguade. Hardware-software coherence protocol for the coexistence of caches and local memories. TC,Jan. 2015. 134

\[Ama19\] Amazon. EC2 Inf1 Instances. 2019. 153

\[Ama19b\] Amazon. AWS re:Invent 2019: deliver high performance ML inference with AWS Inferentia. Dec. 2019. 153

\[Ama20\] Amazon. SageMaker. 2020. 201

\[Amd67\] G. Amdahl. Validity of the single processor approach to achieving large scale computing capabilities. *AFIPS*, Apr. 1967. 134

\[Amd19\] Amd. EPYC 7742. 2019. 152

\[AAB+15\] D. Amodei, R. Anubhai, E. Battenberg, et al. Deep Speech 2: end–to-end speech recognition in English and Mandarin. *ICML*, Dec. 2015. 66

\[AC16\] D. Amodei and J. Clark. Faulty reward functions in the wild. *OpenAI*, Dec. 2016. 70

\[DH18\] A. Dario and D. Hernandez. AI and compute. *OpenAI*, May 2018. 1, 99

\[AES19\] A. Antoniou, H. Edwards, and A. Storkey. How to train your MAML. *ICLR*, Mar. 2019\. 200

\[AP19\] S. Arik and T. Pfister. ProtoAttend: attention-based prototypical learning. Sep. 2019. 204

\[ABF+19\] N. Arivazhagan, A. Bapna, O. Firat, et al. Massively multilingual neural machine translation in the wild: findings and challenges. July 2019. 61, 62

\[ACB17\] M. Arjovsky, S. Chintala, and L. Bottou. Wasserstein GAN. Jan. 2017. 14

\[ADC11\] T. Ashby, P. Diaz, and M. Cintra. Software-based cache coherence with hardware-assisted selective self-invalidations using Bloom filters. TC, Apr. 2011. 134

\[AFO18\] S. Ashkiani, M. Farach-Colton, and J. Owens. A dynamic hash table for the GPU. *IPDPS*, May 2018. 41
