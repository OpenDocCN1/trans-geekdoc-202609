
通过使用最小的计算资源，从而确保安全层不会影响物联网环境的整体性能。为了在低功耗设备上运行，采用CNN和RNN来减少计算负载及其复杂度。[45]。

边缘计算也可以作为将计算任务从物联网设备卸载到其他强大网关的策略之一[46]。通过减轻单个物联网设备的负担，该过程能够在不影响性能的情况下实现实时数据处理和威胁检测。当使用轻量级模型和计算负载分配时，具有强大安全性和实时操作的物联网系统更加资源高效。

## 12.6 挑战与未来方向

### 12.6.1 当前局限性

尽管在可接受性和有效性方面仍有一些问题需要解决，但基于深度学习的入侵检测系统（DL-based IDS）在改善物联网环境安全方面提供了诸多好处。

- a) 深度学习模型的计算开销：物联网系统的主要问题之一是深度学习或必要的处理成本。一般来说，资源密集型任务由不同的深度学习算法（如CNN和RNN）处理，这些算法需要更大的内存、存储和处理能力。许多物联网设备，例如可穿戴设备或使用有限计算资源的低功耗受限设备，使得深度学习模型难以直接部署在设备上[47]。因此，需要付出大量努力来优化这些模型，以减轻边缘层而非设备本身的计算过载。

- b) 缺乏物联网安全标准化框架：物联网系统基本上是异构的，由具有不同处理能力、安全要求和通信协议的各种设备组成。物联网安全中缺乏入侵检测标准化框架，突显了为不同物联网设备开发统一方法来保护物联网环境的必要性。因此，在多样化的物联网系统中实施和维护安全措施非常困难，从而使系统容易被利用。

### 12.6.2 研究机会

- a) 开发节能的深度学习算法：许多物联网设备具有有限的能源资源和计算处理能力；因此，集成节能的深度学习算法至关重要。目前，轻量级模型提供与传统深度学习模型相同的检测精度，但显著减少了计算负担。知识蒸馏、量化和模型剪枝是各种不同的技术，它们降低了模型的复杂度，使其能够在资源受限的物联网设备中高效运行。张量处理单元（TPU）或现场可编程门阵列（FPGA）是用于硬件加速的专用处理器，可以进一步优化物联网环境中深度学习所需的处理能力。见文献[48]。

- b) 扩展数据集以在多样化的物联网应用中实现更好的模型泛化：深度学习模型所需的数据集需要数量多且多样化。然而，许多物联网安全数据集在规模和范围上都很有限，这使得深度学习模型难以在多样化的应用中提供泛化解决方案。为了提升模型性能并确保基于深度学习的IDS能够在不同行业中成功使用，必须扩大和多样化代表物联网环境真实世界多样性的数据集。为了收集用于模型训练的广泛数据，这可能涉及开发公开可用的数据集或政府机构、企业和学术界之间的合作举措。

此外，通过集成自恢复结构，可以显著提高物联网网络的恢复能力，这些结构能够自行检测和响应安全问题。无需人工干预，这些系统可以隔离受损设备、修补漏洞，并在发生入侵时自动重新配置，从而确保在广阔而复杂的物联网生态系统中持续安全。物联网安全的未来可能通过灵活、可扩展且能够在物联网环境变化中保持高水平安全性的结构来塑造，同时强调协作保护和自学习模型。

物联网设备的快速普及彻底改变了技术，促进了连接性和创新，但也带来了重大的网络安全挑战。传统安全机制在应对物联网生态系统的复杂性和规模方面力不从心，需要更先进的解决方案。本章强调了基于深度学习的IDS结构在加强物联网安全方面的变革能力。通过全面评估，本章探讨了深度学习与物联网网络安全的交集，强调了数据收集、特征提取、异常检测和模型训练在开发稳健IDS中的重要性。本章还指出了在优化保护与确保物联网环境运行性能之间保持平衡的重要作用。尽管深度学习前景广阔，但本章也提到了现有挑战，如可扩展性、对抗鲁棒性，以及边缘计算和区块链等互补技术的结合。这些领域代表了未来研究和发展的机会，为能够适应不断变化的威胁环境的弹性安全物联网铺平了道路。

本章为研究人员、从业人员和网络安全爱好者提供了全面指南，帮助他们加深对保护物联网生态系统的理解。通过弥合物联网安全挑战与基于深度学习的IDS等先进解决方案之间的差距，本章为读者提供了基础知识、技术见解、实践相关性和战略视角。预计本章将帮助读者掌握批判性评估物联网安全风险的知识，并利用深度学习开发可扩展、稳健且自适应的解决方案，以保护物联网生态系统。

## 参考文献

1 Nikitha, M., Arulprakash, P., Ayyannan, M., Nithin, M., Pokhariyal, R., and Maranan, R. (2023). Intelligent smart home automation system using internet of things. 7th International Conference I-SMAC (IoT Social, Mobile, Analytics and Cloud), I-SMAC 2023—Proceeding, 11-13 October, Kirtipur, Nepal. pp. 31–36, 10.1109/I-SMAC58438.2023.10290235.

2 Rout, S.K., Sahu, B., Mohapatra, P.K. et al. (2023). IoT and an intelligent cloud-based framework to build a smart city traffic management system BT. In: Enabling Technologies for Effective Planning and Management in Sustainable Smart Cities (ed. M.A. Ahad, G. Casalino, and B. Bhushan), 283–302. Cham: Springer International Publishing. https://doi.org/10.1007/978-3-031-22922-0_11.

3 Prince, N.U., Al Mamun, M.A., Olajide, A.O. et al. (2024). IEEE standards and deep learning techniques for securing Internet of Things (IoT) devices against cyber attacks. Journal of Computational Analysis and Applications 33 (7): 1270–1289.

4 Kumar, C.S. and Anand, R.V. (2024). Security in IOT-enabled smart agriculture systems BT. In: Communication Technologies and Security Challenges in IoT: Present and Future (ed. A. Prasad, T.P. Singh, and S.D. Sharma), 279–300. Singapore: Springer Nature Singapore. https://doi.org/10.1007/978-981-97-0052-3_14.

5. Heidari, A. and Jabraeil Jamali, M.A. (2023). Internet of Things intrusion detection systems: a comprehensive review and future directions. Cluster Computing 26 (6): 3753–3780. https://doi.org/10.1007/s10586-022-03776-z.

6. Ahanger, A.S., Khan, S.M., and Masoodi, F. (2022). Building an intrusion detection system using supervised machine learning classifiers with feature selection. In: Inventive Systems and Control. Proceedings of ICISC 2022 (ed. V. Suma, Z. Baig, S. Kolandapalayam Shanmugam, P. Lorenz), 811–821. Springer Nature Singapore.

7. Pandey, S. and Bhushan, B. (2024). Recent Lightweight cryptography (LWC) based security advances for resource-constrained IoT networks. Wireless Networks 30 (4): 2987–3026. https://doi.org/10.1007/s11276-024-03714-4.

8. Malhotra, P., Singh, Y., Anand, P. et al. (2021). Internet of things: evolution, concerns and security challenges. Sensors 21 (5): 1–35. https://doi.org/10.3390/s21051809.

9. Yadav, U. and Sharma, A.K. (2023). A novel automated depression detection technique using text transcript. International Journal of Imaging Systems and Technology 33 (1): 108–122. https://doi.org/10.1002/ima.22793.

10. Yadav, U. and Sharma, A.K. (2021). Review on automated depression detection from audio visual clue using sentiment analysis. Proceedings—2nd International Conference on Sustainable Communication Systems ICESC 2021, 04-06 August, Coimbatore, India. pp. 1462–1467. https://doi.org/10.1109/ICESC51422.2021.9532751.

11. Bondre, S. and Sharma, A.K. (2021). Review on leaf diseases detection using deep learning. In 2021 Second International Conference on Electronics and Sustainable Communication Systems (ICESC), 04-06 August, Coimbatore, India. pp. 1455–1461. https://doi.org/10.1109/ICESC51422.2021.9532697.

12. Masoodi, F. (2021). Machine learning for classification analysis of intrusion detection on NSL-KDD dataset. Turkish Journal of Computer and Mathematics Education (TURCOMAT) 12 (10): 2286–2293.

13. Yaqoob, T., Abbas, H., and Atifuzzaman, M. (2019). Security vulnerabilities, attacks, countermeasures, and regulations of networked medical devices—a review. IEEE Communication Surveys and Tutorials 21 (4): 3723–3768. https://doi.org/10.1109/COMST.2019.2914094.

14. Purohit, N. and Joshi, S. (2024). Comprehensive analysis on various cryptographic algorithm for constrained devices. In 2024 International Conference on Innovations and Challenges in Emerging Technologies (ICICET), 07-08 June, Nagpur, India. pp. 1–7. https://doi.org/10.1109/ICICET59348.2024.10616265.

15. Abrar, I., Ayub, Z., Masoodi, F., and Bhamdi, A.M. (2020). A machine learning approach for intrusion detection system on NSL-KDD dataset. 2020 International Conference on Smart Electronics and Communication (ICOSEC), IEEE. 10-12 September, Trichy, India.

