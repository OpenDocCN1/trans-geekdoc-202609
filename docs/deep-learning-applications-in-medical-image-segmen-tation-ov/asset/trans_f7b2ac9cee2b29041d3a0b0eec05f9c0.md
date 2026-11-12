

### Table 8.8 GAN-based segmentation method for pelvic

| Reference | Modality | Model | Dataset | Performance (DSC) |
|---|---|---|---|---|
| Rezaei et al. (2018a) | MRI | FCN-GAN | 私有 | 0.41 |
| Rezaei et al. (2018b) | MRI | 3D APA-Net (3D 对抗金字塔各向异性卷积深度神经网络) | PROMISE12 | 整体: 0.906<br>基底: 0.891<br>顶端: 0.869 |
| Ronneberger et al. (2015) | MRI | U-Net GAN | PROMISE12 | 0.8624 |
| La Rosa et al. (2021) | CT | U-Net CGAN Pix2Pix | 私有 | 前列腺: 0.929<br>子宫: 0.724 |
| Ruan et al. (2020) | CT | FCN GAN U-Net | 私有 | 前列腺: 0.868<br>膀胱: 0.762<br>直肠: 0.719 |
| Schlegl et al. (2019) | CT, MRI | CycleGAN | 私有 | 膀胱: 0.93<br>前列腺: 0.88<br>直肠: 0.88<br>左股骨头: 0.94<br>右股骨: 0.94 |

### Table 8.9 GAN-based segmentation method using MRI as modality

| Reference | Region of Interest | Model | Dataset | Performance |
|---|---|---|---|---|
| Conze et al. (2021) | 整个病变、FLAIR 高信号区和造影增强区域 | GAN | BraTS 2017 | DSC = 0.82 |
| Dong et al. (2018) | 颅颌面骨结构 | U-Net CycleGAN | ADNI | DSC = 0.8856 |
| Mahapatra et al. (2017) | 左心室 (LV)、右心室 (RV) 和心肌 (MYO) | U-Net GAN | ACDC | DSC = 0.96, 0.92, 0.87 |
| Radford et al. (2016) | 肝脏、右肾、左肾、脾脏、多器官 | U-Net CGAN | CHAOS | (肝脏, 右肾, 左肾, 脾脏, 多器官) F-score = 85.53, 70.17, 70.39, 64.77, 69.92, 68.78 |

### Table 8.10 Segmentation of CT images using GAN based Methods

| Reference | Region of Interest | Model | Dataset | Performance |
|---|---|---|---|---|
| Decourt and Duong (2020) | 白质 | CGAN pix2pix | ADNI | DSC = 0.817 |
| Kohl et al. (2017) | 脑组织 | GAN | MICCAI 2012 MRBrainS13 | DSC = 0.92 DSC = 0.85 |
| Radford et al. (2016) | 肝脏、右肾、左肾、脾脏、多器官 | U-Net CGAN | CHAOS | (肝脏, 右肾, 左肾, 脾脏, 多器官) F-score = 85.53, 70.17, 70.39, 64.77, 69.92, 68.78 |

Oh 等人（2020 年）在 CT 图像中分割白质，实现了脑组织的精确勾画。Tan 等人（2021 年）将基于 EM 距离的损失函数与 GAN 相结合，以精确分割输入 CT 扫描中的肺部。Conze 等人（2021 年）利用 GAN 对腹部 CT 图像进行自动多器官分割，有效实现了多器官的同时分割（表 8.10）。

## 8.4.2.3 Segmentation of Other Modalities Using GAN

X 线成像是一种广泛使用的医学诊断技术，利用电离辐射创建人体内部的详细图像。X 射线在可视化骨骼方面特别有效，有助于诊断骨折、感染和某些疾病。该过程涉及将身体的一部分暴露在少量电离辐射下，生成的 X 线图像为各种医学专科（如骨科和牙科）的医疗专业人员提供了宝贵信息。OCT 是一种非侵入性成像技术，利用光波捕获生物组织的高分辨率断层图像。它常用于眼科，以可视化视网膜的各个层，从而允许早期检测和监测黄斑变性和青光眼等眼部疾病。此外，OCT 在其他医学领域（包括心脏病学和皮肤病学）也有应用，在不需要电离辐射的情况下，它能提供关于组织结构的详细洞察（表 8.11）。

### Table 8.11 Segmentation of other modalities using GAN based Methods

| Reference | Region of Interest | Modality | Model | Dataset | Performance |
|---|---|---|---|---|---|
| Israel et al. (2017) | 视网膜异常 | OCT | CycleGAN | K's 数据集 | DSC = 0.8239 |
| Kan et al. (2021) | 乳腺肿块 | X 线 | CGAN | INbreast | DSC = 88.81 |
| Kurutach et al. (2018) | 肺结节 | CT | 3D CGAN | LIDC | DSC = 0.989 |
| Lahiri et al. (2017) | 肺结节 | CT | GAN | LIDC-IDRI | DSC = 0.7986 |
| Son et al. (2019) | 肺部 | CT(3D) | TD-GAN | 私有 | DSC = 0.894 |
| | 心脏 | | | | DSC = 0.870 |
| | 肝脏 | | | | DSC = 0.817 |
| | 骨骼 | | | | DSC = 0.835 |

Wang 等人（2021b 年）提出了一种弱监督学习网络，用于分割 OCT 图像中的病变。Shen 等人（2019 年）使用 CycleGAN 生成了 X 线乳腺肿块图像。Jin 等人（2018 年）提出了一种创新的多掩膜重建损失，将其纳入 GAN 以生成高度逼真的肺结节图像。Jain 等人（2021 年）通过集成专门用于肺结节分割的海草杂乱牧羊人优化算法，改进了 GAN 模型以实现精确的肺癌检测。在他们的 2020 年研究（Sultana et al. 2020）中，Sultana 等人采用了多类 3D U-Net 对盆腔结构进行粗分割，随后采用改进的 GAN 进行更精细的器官分割。在他们的研究中，Zhang 等人（Zhang et al. 2018a）在 X 线图像上使用了多器官的无监督分割。

## 8.4.3 Classification on the Basis of GAN Model Employed

在本节中，使用 GAN 的医学图像分割技术是根据所实现的特定 GAN 变体进行组织的。所考虑的模型范围涵盖了基于 U-Net 的 GAN、CycleGAN、DCGAN（深度卷积 GAN）、CGAN（条件 GAN）和 Pix-2-Pix GAN。这种分类有助于区分和分类在医学图像分割背景下使用的多样化 GAN 架构。每个模型代表一种独特的方法，反映了该领域各项研究中采用的细致策略和方法学。

### 8.4.3.1 Segmentation Using U-Net Based GAN

Xue 等人（2018 年）将 U-Net 用作 GAN 的生成器，并引入了多尺度 L1 损耗方法，从而实现了直接高效的脑肿瘤分割。Shi 等人（2019 年）引入了 UG-net（GAN 内的修改版 U-Net），专门用于分割海马子区。Guo 等人（2020 年）利用 U-Net 识别边界，利用 GAN 进行形状预测，专门针对胸肌区域的分割。Guo 等人（2020 年）分别将 U-Net 和金字塔结构用作生成器和判别器，以从冠状动脉中提取复杂特征。Sultana 等人（2020 年）利用具有多类功能的 3D U-Net 对盆腔结构进行初步分割，随后实施增强版 GAN 以进行更精确的器官分割。Wang 等人（2020 年）将 U-Net 的结构元素纳入 GAN 中，以改进 OCT 图像中食管的分割（表 8.12）。

### 8.4.3.2 Segmentation Using Conditional GANs (CGAN, pix2pix GAN, and ACGAN)

Oh 等人（2020 年）使用在 pix2pix 框架内实现的 CGAN，准确分割了 18F-FDG PET/CT 图像中的白质。该方法实现了脑组织的精确勾画。Jiang 等人（2018 年）引入了 CGAN 及其 Dice 损耗函数，开创了漆裂分割的先河。Shen 等人（2019 年）是首个采用 CGAN 的研究者。

### Table 8.12 Segmentation using U-Net based GAN models

| Reference | Region of Interest | Modality | Dataset | Performance |
|---|---|---|---|---|
| (Borne et al. (n.d.)) | 整个肿瘤 | MRI | BraTS 2013 | 整体 DSC = 0.84 |
| | 肿瘤核心 | | | 核心 DSC = 0.70 |
| | GD 增强的肿瘤核心 | | | 增强 DSC = 0.65 |
| Dong et al. (2019) | 海马（CA1, CA2, DG, CA3, 头部, 尾部, SUB, ERC 和 PHG） | MRI | CIND Center | DSC = 0.919 |
| Li et al. (2021a) | 胸部肌肉 | 乳腺X光摄影 | 私有 | DSC = 0.9703 |
| Ruan et al. (2020) | 前列腺 膀胱 直肠 | CT | 私有 | DSC = 0.90, DSC = 0.96, DSC = 0.91 |

