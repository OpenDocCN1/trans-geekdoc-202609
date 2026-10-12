
关于表 3，`REFDL` 节省的内存和处理时间分别显示在图 4 和图 5 中。结果表明，与每种训练方法相比，`REFDL` 在最大限度地减少资源（内存和时间）方面表现更好。结果显示，使用 `PySyft` 虚拟工作节点构造（模拟真实虚拟机并在同一 Python 脚本中独立运行）可提升 `REFDL` 的性能。具体而言，它展示了 `REFDL` 模型采用 4 个隐藏层 (`4L`) 和 2 个虚拟工作节点 (`2VW`) 可能呈现出较低内存消耗的潜在模型。它还表明，采用三隐藏层网络架构增加虚拟员工数量可实现内存节省。

我们在 `FL` 场景下使用 `FCNN` 和 `CNN` 集成，在 MNIST 图像数据集上评估了 `REFDL`，以证明其在网络安全领域之外的泛化能力和有效性（见表 4）。通过评估其在与物联网无关的数据集上的性能，我们可以了解该方法是否可作为设备端学习的通用选择。特别是为了获得 `CNN` 在图像分类上超越人类专家的优势及其高效资源管理能力的收益。通过此分析，我们使用 `PySyft WS`（网络）模拟工作节点，比较了 `BFDL` 和 `REFDL` 在所有联邦训练场景下的功效。与作为同一 Python 程序内构造运行的 `PySyft` 虚拟工作节点不同，该方法通过模拟客户端和服务器驻留在同一机器上的网络来评估 `REFDL` 的性能。在所有 `DNN`（`CNN` 和 `FCNN`）变体中，`REFDL` 的准确率均优于 `BFDL`。由于 MNIST 数据集对训练和测试样本都具有相对平衡的分布，这可能是其取得卓越性能的原因。且完成一个训练会话所需的时间显著缩短。结果证明了正则化在处理 `DNN` 波动时保护准确率的重要性。这激励在实际场景中开展进一步研究。

表 4. 使用 BFDL 和 REFDL 在 MNIST 数据集上模拟联邦训练有效性的对比研究。

| 过程 | 联邦学习 | 时间 (分钟) | 测试集 (准确率 %) | 时间 (节省 %) |
| --- | --- | --- | --- | --- |
| FCNN-MNIST | BFDL | 1.393 | 34.64 | N/A |
| | 资源高效联邦深度学习 | 1.346 | 91.03 | 3.374 |
| CNN-MNIST | BFDL | 1.583 | 90.59 | N/A |
| | 资源高效联邦深度学习 | 1.457 | 98.28 | 7.960 |

![图 4. XCS-1003 数据集在 REFDL 联邦内存中的模型训练数据。](img/fig6_4_B.jpg)

图 4. XCS-1003 数据集在 REFDL 联邦内存中的模型训练数据。

![图 5. 使用 XCS-1003 数据集训练减少了资源高效联邦深度学习模型的时间和资源。](img/fig6_5_B.jpg)

图 5. 使用 XCS-1003 数据集训练减少了资源高效联邦深度学习模型的时间和资源。

## 实验结果分析

利用移动网络模拟器计算了在四台 GB-BXBT-2807 边缘设备上，使用 Ennio Doorbell 和 Samsung SNH 物联网数据集训练资源高效联邦深度学习（`REFDL`）和基线联邦深度学习（`BFDL`）所需的空间。表 5 中的内存规格数据是所有四台设备的平均值。研究结果表明，`REFDL` 更适合实时物联网攻击检测，且内存需求比 `BFDL` 更少。联邦客户端的数量和特征分布选择决定了精确的内存和 CPU（运行时）减少量。处理复杂数据的广泛客户群可能会带来更大的成本节约。

### 表 5. 使用资源高效联邦深度学习和基线联邦深度学习的联邦模型训练内存利用率

| Dataset | Model | Memory (MB) | Test (accuracy %) | Memory (Saving %) |
| --- | --- | --- | --- | --- |
| Ennio Doorbell | BFDL | 33.965 | 89.00 | Not Applicable |
| Ennio Doorbell | Resource Efficient Federated Deep Learning | 31.981 | 89.00 | 5.84 |
| Samsung SNH | BFDL | 32.519 | 86.10 | Not Applicable |
| Samsung SNH | Resource Efficient Federated Deep Learning | 30.550 | 86.10 | 6.05 |

如图 6 所示，Ennio Doorbell 和 Samsung SNH 物联网数据集的数据被用于训练 `BFDL` 和 `REFDL`。还提供了平均预测收敛的实时描绘。在发现物联网攻击方面，`REFDL` 所需的实时时间不如 `BFDL` 多。研究结果验证了 `REFDL` 在受限环境中降低计算需求的用途。图 7 显示更多的分布式边缘设备可以提高效率。

![图 6. 使用联邦模型在不同数据集上 REFDL 和 BFDL 训练执行时间的比较](img/fig6_6_B.jpg)

图 6. 使用联邦模型在不同数据集上 REFDL 和 BFDL 训练执行时间的比较

![图 7. 在合成和真实网络环境下，考察 REFDL 和 BFDL 在 Ennio 数据集上的性能](img/fig6_7_B.jpg)

图 7. 在合成和真实网络环境下，考察 REFDL 和 BFDL 在 Ennio 数据集上的性能

结果证明，在实际网络中使用 `REFDL` 比虚拟 `WS` 连接节省更多资金。这证明了 `REFDL` 在有限资源跨多个客户端设备共享的环境中降低能耗的潜力。

我们使用 MNIST 数据集比较了 `REFDL` 与 `BFDL` 在节省时间方面的表现。根据图 8，`REFDL` 在训练的所有阶段都比 `BFDL` 更有效。与 MNISTFCNN 相比，MNIST 联邦 CNN 的训练过程更繁琐，需要更多的数据存储空间。如果最小化开发成本是首要目标，FCNN DNN 变体的资源高效联邦深度学习是直接在设备上学习的一种可能解决方案。`REFDL` 是在物联网资源环境中实施的首选方法。

![图 8. 使用 REFDL 和 BFDL 在 MNIST 数据集上联邦模型的训练时间](img/fig6_8_B.jpg)

图 8. 使用 REFDL 和 BFDL 在 MNIST 数据集上联邦模型的训练时间

图 9 展示了 `REFDL` 和 `BFDL` 在 MNIST 数据集上的收敛精度与其他 DNN 版本的比较。因此，可以假设 `REFDL` 将始终优于 `BFDL`。通过结合 CNN 和 FCNN (DNN) 模型的多种变体，它可以正确分类图像样本。这一发现指明了优化过程在开发全局深度联邦模型中的价值。它进一步突显了在 FL 技术中有效使用 CNN 以提高准确性的成效。这很有帮助，因为它利用了各种 DNN 模型在设备上学习效率的差异。

![图 9. 利用 MNIST 数据集估算 REFDL 和 BFDL 的联邦模型准确率](img/fig6_9_B.jpg)

图 9. 利用 MNIST 数据集估算 REFDL 和 BFDL 的联邦模型准确率

为了评估 `REFDL` 在联邦环境中的效率和学习速度，我们在 GB-BXBT-2807 测试平台上使用不同数量的 epoch 迭代运行了 FCNN-MNIST 流程。我们可以在那里快速评估多种联邦方法的相对优劣。图 10 显示，`REFDL` 仅需一个本地 epoch 和 50 个通信周期即可达到更高的精度水平。所有后续的 epoch 迭代都保持了这种精度不断提高的模式。特别是，集成的 FCNN 模型加速了边缘设备上的学习，证明了 `REFDL` 的适用性。`REFDL` 至少需要一个 epoch 的限制是一个优势，特别是在物联网等内存限制已存在的环境中。

### 6. 结论

在本文中，我们探讨了在物联网等低资源环境中训练联邦学习的可行性，其分布式机器学习模型可以同时保护大量客户数据的隐私，并促进网络边缘节点上的设备端学习。为了提供针对物联网的有效且实用的防护。在本研究中，我们将 `BFDL` 算法 FedAvg 与几个精心挑选的模型优化策略相结合，创建了一个功能强大且数据利用经济的联邦 `REFDL` 模型。八个物联网数据集和一个图像数据集被用于在模拟和真实的 GB-BXBT-2807 测试平台上评估 `REFDL` 的功效、简洁性和效率。它在利用极少资源识别物联网攻击方面优于其他方法。在联邦训练环境中，它使用相同数据对图像数据的分类准确度高于全连接网络或卷积网络。此外，`REFDL` 生成更准确的 FL 模型所需时间比竞争对手更少。受这些令人鼓舞的发现启发，我们希望对部署过程中计算网络中更多节点/客户端设备的使用进行进一步研究，重点关注有线和无线环境。具体来说，在一个比本研究探索的连接边缘设备范围更广的真实网络场景中，我们旨在研究 `REFDL` 的鲁棒能力，以增强其对抗对抗攻击的安全弹性。通过这种方式，我们可以在广泛的地理分散边缘设备上考察我们提出的方法对资源使用和安全监控的影响。

### 参考文献

1.  Tabassum, N., Ahmed, M., Shorna, N.J., Sowad, M.M.U.R. and Haque, H.M.Z. 2023. Depression detection through smartphone sensing: A Federated Learning approach. Int. J. Interact. Mob. Technol., 17(1): 40-56. doi: [10.3991/ijim.v17i01.35131](https://doi.org/10.3991/ijim.v17i01.35131).

2.  Ahmed, U., Lin, J.C.W. and Srivastava, G. 2022. Mitigating adversarial evasion attacks by deep active learning for medical image classification. Multimed. Tools Appl., 81(29): 41899-41910. doi: [10.1007/s11042-021-11473-z](https://doi.org/10.1007/s11042-021-11473-z).

3.  Zhang, C., Zhu, Y., Markos, C. Yu and Yu, J.J.Q. 2022. Toward crowdsourced transportation mode identification: A semisupervised Federated Learning approach. IEEE Internet Things J., 9(14): 11868-11882. doi: [10.1109/JIOT.2021.3132056](https://doi.org/10.1109/JIOT.2021.3132056).

4.  Marulli, F., Balzanella, A., Campanile, L., Iacono, M. and Mastroianni, M. 2021. Exploring a Federated Learning approach to enhance authorship attribution of misleading information from heterogeneous sources. In *Proceedings of the International Joint Conference on Neural Networks*, vol. 2021-July. doi: [10.1109/IJCNN52387.2021.9534377](https://doi.org/10.1109/IJCNN52387.2021.9534377).

5.  Mei, G., Guo, Z., Liu, S. and Pan, L. 2019. SGNN: A graph neural network based federated learning approach by hiding structure. In *Proceedings—2019 IEEE International Conference on Big Data, Big Data 2019*, pp. 2560-2568. doi: [10.1109/BigData47090.2019.9005983](https://doi.org/10.1109/BigData47090.2019.9005983).

6.  Zhang, Liu X., Xie, X., Zhang, J., Niu, B. and Li, K. 2022. A cross-domain federated learning framework for wireless human sensing. *IEEE Netw.*, 36(5): 122-128. doi: [10.1109/MNET.001.2200231](https://doi.org/10.1109/MNET.001.2200231).

7.  Abdelbasset, M., Hawash, H., Sallam, K.M., Elgendi, I., Munasinghe, K. and Jamalipour, A. 2022. Efficient and lightweight convolutional networks for IoT Malware detection: A Federated Learning approach. *IEEE Internet Things J.*, pp. 1. doi: [10.1109/JIOT.2022.3229005](https://doi.org/10.1109/JIOT.2022.3229005).

8.  Gogineni, V.C., Werner, S., Huang, Y. and Kuh, A. 2022. Communication-efficient online federated learning strategies for kernel regression. *IEEE Internet Things J.*, pp. 1. doi: [10.1109/JIOT.2022.3218484](https://doi.org/10.1109/JIOT.2022.3218484).

9.  Wang, S., Hosseinalipour, S., Gorlatova, M., Brinton, C.G. and Chiang, M. 2022. UAV-assisted online machine learning over multi-tiered networks: A hierarchical nested personalized Federated Learning approach. *IEEE Trans. Netw. Serv. Manag.*, pp. 1. doi: [10.1109/TNSM.2022.3216326](https://doi.org/10.1109/TNSM.2022.3216326).

10.  Imani, H., Anderson, J. and El-Ghazawi, T. 2022. I Sample: Intelligent client sampling in Federated Learning. In *Proceedings—6th IEEE International Conference on Fog and Edge Computing, ICFEC 2022*, pp. 58-65. doi: [10.1109/ICFEC54809.2022.00015](https://doi.org/10.1109/ICFEC54809.2022.00015).

11.  Zhang, D.Y., Kou, Z. and Wang, D. 2021. FedSens: A Federated Learning approach for smart health sensing with class imbalance in resource constrained edge computing. In *Proceedings—IEEE INFOCOM*, vol. 2021-May. doi: [10.1109/INFOCOM42981.2021.9488776](https://doi.org/10.1109/INFOCOM42981.2021.9488776).

12.  Akubathini, P., Chouksey, S. and Satheesh, H.S. 2021. Evaluation of machine learning approaches for resource constrained IIoT devices. In *2021 13th International Conference on Information Technology and Electrical Engineering, ICITEE 2021*, pp. 74-79. doi: [10.1109/ICITEE53064.2021.9611880](https://doi.org/10.1109/ICITEE53064.2021.9611880).

13.  Alghamdi, R. and Bellaiche, M. 2023. A cascaded federated deep learning based framework for detecting wormhole attacks in IoT networks. *Comput. Secur.*, 125. doi: [10.1016/j.cose.2022.103014](https://doi.org/10.1016/j.cose.2022.103014).
