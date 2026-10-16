
```
Z = f(We · x + be)
where z is the latent representation, We is the weight matrix of the encoder, x is the input data, and b is the bias.
```

![](img/a13b588839130d750aecd8a32b6143d9_258_0.png)

图10.8 自动编码器架构。来源：参考文献[21] / 经Springer Nature许可使用。

- **解码器：** 网络的这一组件从潜空间中的缩减表示重构主要输入数据。它通常由一系列层组成，这些层逐渐扩展数据量，直到达到原始输入大小，如图10.8所示。

$x' = g(Wd \cdot z + bd)$

其中 $x'$ 是重构后的数据，$Wd$ 是解码器的权重矩阵，$bd$ 是偏置。

- **潜空间：** 它充当瓶颈，促使网络学习相关特征。这是自动编码器的瓶颈。它是输入数据的低维表示，捕获最重要的特征和模式。潜空间的维度通常远低于输入数据的维度。

使用自动编码器来增强无线网络的安全性具有重要意义，例如在异常检测中，自动编码器可在典型网络流量上进行训练。当它们遇到新型流量时，会尝试重构它。显著的重构误差则表明可能存在异常，例如入侵、DDoS攻击或恶意软件感染。自动编码器可以获取网络流量数据的紧凑可视化，借助特征提取来提取关键特征和模式[2]。这些获取的表示可以被输入到其他机器学习模型中，包括分类器或异常检测器。此外，自动编码器可用于去除网络流量数据中的噪声和异常，这些噪声和异常可能掩盖恶意活动的存在。

## 10.6 基于深度学习的MANETs和WSNs入侵检测挑战解决方案

移动自组网（MANETs）和无线传感器网络（WSNs）由于其分散式结构、资源稀缺、动态拓扑以及对各种威胁的敏感性，带来了重大的入侵检测问题。深度学习（DL）提供了成功解决这些问题的改进方法。下面详细描述这些问题及基于深度学习的解决方案，随后附有汇总表。

### 10.6.1 自动编码器在资源受限无线网络中的用例

近年来，自动编码器迅速变得流行，尤其是在研究和实践中。在无线网络中，自动编码器可以为入侵检测提供有效且高效的基础。实现这一目标的一种方式是使用自动编码器进行异常检测[14]。自动编码器甚至可以在供应商修补软件以缓解此类攻击之前，在早期阶段捕获零日漏洞利用。借助自动编码器，我们能够以更强的估计能力，将入侵检测中输入数据的预期误差编成表格。自动编码器是一种可以压缩输入数据并学习如何重构数据的神经网络。它学习数据的压缩形式，在需要时用于重构原始数据。数据中的异常，如噪声和缺失值，可能导致自动编码器无法生成误差分数。通过纳入降维策略，我们可以利用自动编码器实现SMART IDS，该自动编码器使用隐藏节点值作为特征向量来捕获传入的威胁数据，同时在本地区域之外的节点上添加更多传感器。

该方法利用自动编码器的强大功能来创建有效的数据可视化，有助于减轻资源受限设备上的计算负载[3]。通过专注于发现异常活动而非复杂分类，自动编码器可以用更少的能量和计算资源识别有害行为[17]。这对于在物联网和基于传感器的系统等资源有限的领域构建更好的安全协议至关重要。剪枝、量化和压缩模型可以进一步提升自动编码器的性能。这些技术减小了模型的大小和计算的复杂度，使其适用于资源受限的设备。凭借自动编码器的天然优势和这些优化方法，我们可以在不严重影响有限资源的情况下增强资源受限无线网络的安全性[15]。类似地，有人提出了无监督自动编码器框架，以缓解物联网网络中的DDoS和零日攻击[16]。要检测移动设备上的异常数据模式，网络中，还提出了一种自适应时序卷积网络自编码器（`ATCN-AE`）[14]。

### 10.6.2 CNNs 用于 DDoS 检测的用例

CNNs 通过分析网络流量数据在多个维度上的特征来识别 DDoS 攻击，例如时间序列或数据包头部数据。数据包大小、源/目的 IP 地址和流量量被编码为矩阵并送入 CNN 层。CNNs 使用卷积和池化方法提取区分合法数据与恶意数据的分层特征。在实时系统中，这些模型能够在无线网络中准确地将传入流量分类为良性或恶意[18]。此外，CNNs 快速的推理速度使其能够大规模运行，使其非常适合延迟至关重要的实时应用。使用 CNNs 进行 DDoS 检测的主要优势在于其能够泛化并适应各种攻击模式，包括零日攻击[5]。其自主学习特性使其能够随着新攻击技术的出现而演进，相较于传统的基于规则的系统具有显著优势。此外，将 CNNs 集成到实际系统中的实现需要严格的优化，以在保持高吞吐量的同时实现低计算成本。

CNNs 通过将网络流量数据作为多维输入来检测 DDoS 攻击，例如数据包头部信息或时间序列。数据包长度、源/目的 IP 地址和流量量被转换为矩阵并提供给 CNN 层。CNNs 通过应用卷积和池化层学习分层特征，重点在于区分良性流量与恶意流量。在实时系统中，这些模型可以扫描传入的流量流并准确评估其是否为良性或恶意[6]。此外，带模糊逻辑的 CNNs 增强了推理速度，使其能够扩展并检测恶意节点；它们可用于延迟是问题的实时应用中[19]。

1. Gyamfi, E. 和 Jurcut, A. (2022). 物联网系统中的入侵检测：利用多接入边缘计算、机器学习和数据集的设计方法综述。Sensors 22 (10): 3744.
2. Song, Y., Hyun, S., 和 Cheong, Y.G. (2021). 网络入侵检测中自编码器的分析。Sensors 21 (13): 4294.
3. Rassam, M.A. (2024). 无线体域网异常检测的基于自编码器的神经网络模型。IoT 5 (4): 852–870.
4. Ahmed, K.T., Godder, T.K., 和 Al Mahmud, T.H. (2024). 评估 MANET 路由协议：使用 NS3 的主动与反应式方法的比较分析。Indonesian Journal of Electrical Engineering and Informatics (IJEEI) 12 (4): 780–801.
5. Al-Fuqaha, A., Guizani, M., Mohammadi, M. 等 (2015). 物联网：使能技术、协议和应用综述。IEEE Communications Surveys & Tutorials 17 (4): 2347–2376.
6. Sbai, O. 和 Elboukhari, M. (2022). 针对洪泛攻击的移动自组织网络深度学习入侵检测系统。International Journal of Artificial Intelligence 2252 (8938): 878.
7. Thapa, K.N.K. 和 Duraipandian, N. (2021). 使用长短期记忆（LSTM）模型进行恶意流量分类。Wireless Personal Communications 119 (3): 2707–2724.
8. Sowah, R.A., Ofori-Amanfo, K.B., Mills, G.A., 和 Koumadi, K.M. (2019). 使用人工神经网络（ANN）预测技术在 MANET 中检测和防止中间人欺骗攻击。Journal of Computer Networks and Communications 2019 (1): 4683982.
9. Diro, A. 和 Chilamkurti, N. (2018). 利用 LSTM 网络进行雾到物通信中的攻击检测。IEEE Communications Magazine 56 (9): 124–130.
10. Arshad, S., Ashraf, W., Ashraf, S., Hassan, I., 和 Masoodi, F.S. (2023). CICIDS-2017 数据集上入侵检测机器学习技术的比较研究。2023 年第 10 届可持续全球发展计算国际会议（INDIACom），IEEE。Bharati Vidyapeeth's Institute of Computer Applications & Management (BVICAM)，New Delhi, India，March 15–17, 2023.
11. Zhang, G., Kou, L., Zhang, L. 等 (2017). 物联网感知层数据完整性保护的一种新的数字水印方法。Security and Communication Networks 2017 (1): 3126010.
12. Abrar, I., Ayub, Z., Masoodi, F.S., 和 Bamhdi, A.M. (2020). NSL-KDD 数据集上入侵检测系统的机器学习方法。2020 International Conference on Smart Electronics and Communication (ICOSEC)，IEEE。Kalasalingam Academy of Research and Education (KARE)，Tamil Nadu, India，September 10–12, 2020.
13. Laqtib, S., Yassini, K.E., 和 Hasnaoui, M.L. (2019). 基于机器学习的 MANET 入侵检测系统的深度学习方法。载于第 4 届智慧城市应用国际会议论文集，Moulay Ismail University，Meknes, Morocco，October 2019，pp. 1–8.
14. Masoodi, F.S., Abrar, I., 和 Bamhdi, A.M. (October 27, 2021). 使用同质集成技术的有效入侵检测系统。International Journal of Information Security and Privacy (IJISP) 16 (1).
15. Aloul, F., Zualkernan, I., Abdalgawad, N., Hussain, L., 和 Sakhnini, D. (2021). 使用对抗自编码器在物联网边缘进行网络入侵检测。载于 2021 International Conference on Information Technology (ICIT)，pp. 120–125，IEEE。Amman, Jordan，July 14–15, 2021.
16. Yang, K., Zhang, J., Xu, Y., 和 Chao, J. (2020). 使用自编码器检测 DDoS 攻击。载于 NOMS 2020–2020 IEEE/IFIP Network Operations and Management Symposium，pp. 1–9，IEEE。Budapest, Hungary (virtual)，April 20–24, 2020.
17. Ahanger, A.S., Khan, S.M., Masoodi, F. 等 (2025). 使用图注意力网络进行物联网高级入侵检测。Scientific Reports 15: 9831.
18. Singh, V.K., Sivashankar, D., Kundan, K., 和 Kumari, S. (2024). 使用 SS-LSACNN 和 TCSLR 的 WSN 中 DDoS 攻击高效入侵检测与防御系统。Journal of Cyber Security and Mobility 135–160.
19. Shanmathi, M., Sonker, A., Hussain, Z. 等 (2024). 使用 CNN-FL 和 NGO 优化增强无线传感器网络安全性和效率。Measurement: Sensors 32: 101057.
20. Hinds, A., Ngulube, M., Zhu, S.Y., 和 Al-Aqrabi, H. (2013). 移动自组织网络（MANET）路由协议综述。International Journal of Information and Education Technology 3 (1): 101–105.
21. Hammi, S., Hammami, S.M., 和 Belguith, L.H. (2023). 利用结合深度学习模型 CNN 和 bi-RNN 与机器学习模型 SVM 的新架构推进基于方面的情感分析。Social Network Analysis and Mining 13 (1): 117.
22. Ahanger, A.S., Khan, S.M., 和 Masoodi, F.S. (2021). 使用监督机器学习技术的有效入侵检测系统。2021 5th International Conference on Computing Methodologies and Communication (ICCMC)，IEEE。Erode, Tamil Nadu, India，Apr. 8–10, 2021，pp. 1639–1644.
23. Thakkar, A. 和 Lohiya, R. (2023). 深度神经网络入侵检测系统中特征选择的统计重要性融合。Information Fusion 90: 353–363.
24. Zhang, Y., Zhang, H., 和 Zhang, B. (2022). 网络入侵检测的有效集成自动特征选择方法。Information 13 (7): 314.
25. Kumar, D., Arora, V.K., & Sawhney, R. (2022). WSN（无线传感器网络）中转发路由协议的不同类别：综述。Mobile Computing and Sustainable Informatics: Proceedings of ICMCSI, 2022，pp. 509–521。Lalitpur (Kathmandu), Nepal，Jan. 27–28, 2022.
26. Bamhdi, A.M., Abrar, I., 和 Masoodi, F. (2021). 使用多数投票进行有效入侵检测的集成方法。Telkomnika (Telecommunication Computing Electronics and Control) 19 (2): 664–671.
27. Amin, U., Ahanger, A.S., Masoodi, F., 和 Bamhdi, A.M. (2021). 基于 UNSW-NB15 数据集的云环境集成有效入侵检测系统。SCRS Conference Proceeding Intelligent System，pp. 483–494，India，Apr. 26, 2022.
28. Masoodi, F. (2021). NSL-KDD 数据集上入侵检测分类分析的机器学习。Turkish Journal of Computer and Mathematics Education (TURCOMAT) 12 (10): 2286–2293.

## 11 基于深度学习的无线网络入侵检测

Shadab Alam¹ 和 Sadaf Ahmad²

¹沙特阿拉伯吉赞大学工程与计算机科学学院计算机科学系

²印度北方邦阿里格尔穆斯林大学计算机科学系

### 11.1 引言

现代通信世界与无线网络密不可分。无线网络不仅对移动电话至关重要，对物联网（IoT）、工业自动化和云计算中的应用也必不可少。然而，与其他所有领域一样，无线技术的广泛使用也带来了新的网络安全问题。如今，犯罪黑客和敌对国家使用更复杂的方法，在窃取信息和造成损害方面取得更好的效果[1]。就无线网络而言，这些方法中最基本的是发送大量数据包以拒绝为合法用户提供服务。其他方法，如窃听（监听）、数据库攻击和实地侦查，对当今的网络犯罪分子来说也变得更加容易实现。此外，对于当今的无线网络，更大、更快、更贪婪的数据包风暴意味着造成严重损害的可能性也在增加。深度学习（DL）是人工智能（AI）的一个子领域，已成为改进无线网络中入侵检测系统（IDS）的变革性技术[2]。与传统机器学习模型需要手工设计特征不同，深度学习技术自动从高维网络流量数据中提取有意义的模式。各种深度学习架构已成功用于解决入侵检测任务。卷积神经网络（CNN）擅长检测网络流量中的结构模式，而循环神经网络（RNN）擅长捕获序列攻击模式[3]。第三种深度学习架构——长短期记忆（LSTM）网络，是一种专门的 RNN，在某些入侵检测任务上表现出比普通 RNN 更好的性能。LSTM 模型在捕获网络流量中的序列模式方面非常有效[4]。使用深度学习进行入侵检测的主要优势包括：(i) 自动特征提取，显著减少了开发合适模型所需的手动工作量；(ii) 在多种网络行为下具有非常高的检测精度和性能适应性；(iii) 实时检测能力，这意味着基于深度学习的 IDS 可应用于有严格延迟要求的场景，如 IoT 和 5G 网络[5]。

基于深度学习的 IDS 在无线网络中的优势是显而易见的。然而，这些系统面临重大挑战，如果要在广泛部署的无线环境中有效使用，就必须克服这些挑战，因为在这些环境中 IDS 必须尽可能高效和轻量级[6]。本章首先对无线环境中网络安全面临的诸多严峻挑战进行了较为全面的概述，这些挑战是传统入侵检测方法必须克服的。这让我们得以一窥这些基于深度学习的方法在应对这些挑战时的强大能力。在本章的后半部分，作者揭示了这些新方法面临的许多关键挑战，以及它们在无线网络环境中保持有效和高效所必须采取的未来研究方向。

### 11.2 无线网络安全与 IDS 挑战

无线网络与有线网络的不同之处在于其独特的特性和安全漏洞。这些网络在开放的通信介质上运行，使其更容易受到各种形式的网络威胁[7]。主要挑战包括：

- **有限物理安全：** 与受益于受控访问等物理安全措施的有线网络不同，无线网络面临恶意接入点、未授权拦截和信号干扰等威胁。

- **去中心化和动态架构：** 无线网络，尤其是 IoT 和 MANET，缺乏集中控制，这使得在所有节点上建立一致的安全措施变得具有挑战性[8]。

- **资源限制：** 许多无线设备以有限的电力和计算资源运行，降低了实施加密和基于深度学习的 IDS 等复杂安全机制的可行性。

- **传统 IDS 的高误报率：** 传统的基于签名的 IDS 难以检测新型和不断演变的威胁，而基于异常的 IDS 由于无线流量的动态特性经常产生误报[9]。
