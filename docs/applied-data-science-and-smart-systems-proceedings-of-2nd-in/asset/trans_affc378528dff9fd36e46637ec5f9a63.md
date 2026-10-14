
| ([Kumar et al., 2022](#ch37.xhtml#ref37_18)) || 传输图像在互联网上会面临诸多问题，如保护、版权、修改、认证 || 提供更高的安全性、增强且强健的安全性，难以被未经授权的访问者突破 || LSB 隐写术和 AES 加密 |

| ([Krishna, 2018](#ch37.xhtml#ref37_17)) || 云端存储数据的安全性。采用全局变量计算公钥的非对称区块密码模式 || 与错误校正码（ECC）相比，立方样条曲线密码实现时间更短。所提方法支持大容量大数据。抗主动碰撞和重放攻击 || 利用立方样条曲线公钥密码实现大数据的完全同态加密。工作可在样条曲线的边界条件周围进行，可扩展支持数字签名标准（DSS） |

| ([Zolfaghari and Koshiba, 2022](#ch37.xhtml#ref37_31)) || 研究神经网络对密码学的交叉影响 || 对神经网络与密码学进行详细研究 || 未提出任何技术。未来应将两种数据隐藏技术相互交叉 |

| ([Adnan and Ariffin, 2019](#ch37.xhtml#ref37_2)) || 增强记录在通信过程中免受攻击和威胁的保密性、隐私性、保密性和可用性 || 降低成本、提升保护水平并消除漏洞 || 3D-AES 加密。仍需增强以保护云存储 |

| ([Adee and Mouratidis, 2022](#ch37.xhtml#ref37_1)) || 利用加密与隐写技术在云环境中确保和隐藏数据，从而降低数据盗取和数据篡改攻击 || 更高的冗余性、灵活性、效率和保密性，能够在攻击者试图破坏机密、隐私和完整性时提供更强的安全性和隐私性 || 采用 RSA‑AES，随后是基于身份的加密算法，再使用 LSB 隐写术。未来研究应专注于提升隐写与加密的组合，以增强安全性 |

| ([Maata, Cordova, and Halibas, 2020](#ch37.xhtml#ref37_21)) || 大数据在传输时的信息安全 || 消息大小显著增大，加密和解密耗时较长。作者认为该方法高效且有效 || 双鱼（Two‑Fish）加密 |

| ([El-Shafai et al., 2022](#ch37.xhtml#ref37_9)) || 在通信过程中保护图像 || 该加密系统安全、高效且免受各种噪声攻击。由于堆叠自动编码器（SAE）的并行化，计算复杂度降低 || 在感兴趣区域使用改进的深度学习（DL）提取医学图像，随后进行压缩，最后在多阶段安全加密中嵌入水印，以提高医疗数据在远程医疗中广播时的鲁棒性 |

| ([Akkasaligar and Biradar, 2020](#ch37.xhtml#ref37_5)) || 确保大容量字节数据集中的医学图像的安全与机密性 || 抵抗多种攻击类型。该 SEDMI 方法计算时间仅为 0.236 秒，适用于电子健康护理应用 || 选择性数字化医学图像加密（SEDMI） |

| ([Awadh, Alasady, and Hamoud, 2022](#ch37.xhtml#ref37_8)) || 确保图像在 Internet 上的安全与容量 || 图像质量为 68%，解决了安全与容量问题 || 采用离散波束变换（DWT）与 AES 加密的混合层安全压缩，再使用最小比特（LSB）进行隐藏。提出的改进混合安全方法使用随机隐藏算法，可在其他语言中实现 |

| ([Avula Gopalakrishna and Basarkod, 2023](#ch37.xhtml#ref37_7)) || 开发基于区块链的可扩展、轻量框架，以满足现代医疗的复杂需求并提供安全存储 || 构建了轻量区块链框架，结合人工智能提升可访问性 || 使用 Merkle 树结构进行哈希，并采用基于格的同态代理重新加密方案进行加密，安全存储于区块链互联网文件系统（IPFS）中 |

### Proposed hybrid method (PHM)

EMI 免受网络黑客侵害的安全性是一个重要挑战，本研究重点提升 EMI 在存储时的安全性和隐私性（[Ali et al., 2022](#ch37.xhtml#ref37_6)）。密码学的作用是确保 EMI 的机密性（[Zolfaghari and Koshiba, 2022; [Sharma and Prabha, 2023](#ch37.xhtml#ref37_27)））。所提 PHM 方法使用的数据集包含 5856 张 JPEG 格式的 X‑ray 图像，图像大小、尺寸各不相同，分别属于不同时间的不同患者。PHM 的第一步是将覆盖图像 Lena 进行归一化。随后，每一张 X‑ray 图像逐一使用边缘基于隐写术（EBS）隐藏在归一化后的 Lena 图像边缘（背景区域）的红、绿、蓝三个颜色分量上，生成隐写图像（stego‑image）。随后，该隐写图像经过三层加密，生成加密隐写图像（crypto‑stego‑image）。该加密隐写图像可以保存在中心位置或分布式云数据库中。PHM 的逆过程用于恢复原始 X‑ray 图像。

#### Normalized cover image Lena

首先，将 Lena 图像的尺寸扩展至 1080 × 1080。RONI 区域是指除 Lena 本身之外的区域（[Hachaj, Koptyra, and Ogiela, 2021](#ch37.xhtml#ref37_12)），利用在线 Pixlr 工具（[https://pixlr.com/e/#editor](https://pixlr.com/e/#editor)）[https://Pixlr.Com/](https://Pixlr.Com) n.d.）检测无兴趣区域。覆盖图像 Lena 的背景区域被随机生成的黑白噪声填充。图 37.4（[Figure 37.4](#ch37.xhtml#fig37_4)）展示了归一化覆盖图像 Lena 的过程，输出结果称为归一化覆盖图像 Lena。该归一化覆盖图像 Lena 通过边缘基于隐写术（EBS）一次隐藏一张 X‑ray 图像，将图像均匀地分布在 Lena 边缘向背景的红、绿、蓝三个颜色分量上。

![Figure 37.4 Process of normalization of cover image Lena](images/fig37_4_C.jpg)

[Figure 37.4 Process of normalization of cover image Lena](#ch37.xhtml#R_fig37_4)

#### Proposed hybrid steganography with layered cryptography method

PHM 的输入是从 5856 张 JPEG 格式的 X‑ray 图像数据集中逐一加载的一张图像（[Kermany, Zhang, and Goldbaum, 2018](#ch37.xhtml#ref37_15)），如图 37.5（[Figure 37.5](#ch37.xhtml#fig37_5)）所示。将一张 X‑ray 图像加载后，将其在先前归一化的 Lena 图像边缘（Lena 在噪声背景中）隐藏，如图 37.4（[Figure 37.4](#ch37.xhtml#fig37_4)）所示。随后，对生成的隐写图像（stego‑image）应用三层加密，得到加密隐写图像（crypto‑stego‑image）。该 PHM 方法的详细说明见本文算法 1（[Table 37.2](#ch37.xhtml#tab37_2)）。

![Figure 37.5 Few of the 5856 X-ray images that act as input for the PHM](images/fig37_5_B.jpg)

[Figure 37.5 Few of the 5856 X-ray images that act as input for the PHM](#ch37.xhtml#R_fig37_5)

[Table 37.2 The stego-encryption algorithm for the PHM](#ch37.xhtml#R_tab37_2)

| Algorithm 1: Algorithm for implementing the proposed hybrid EBS steganography with three-layers of cryptography for enhancing security of EMI |

