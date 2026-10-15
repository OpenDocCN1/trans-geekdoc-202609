

其中，TPM、TPMO、TPVM 和 TPN 分别表示被正确分类的“轻度痴呆”样本、“中度痴呆”图像样本、“中度痴呆”样本被正确分类?? 实际上应为“被正确分类的‘中度痴呆’图像样本”、“被正确分类的‘极轻度痴呆’样本”和“被正确分类的‘非痴呆’样本”。N 表示样本总数。

## 召回率

SEN_M、SEN_MO、SEN_VM 和 SEN_N 分别表示模型正确预测的“轻度痴呆”样本、“中度痴呆”样本、“极轻度痴呆”图像样本和“非痴呆”样本所占的比例。其计算公式如下：

$$SEN_M = \frac{TPM}{TPM + FNM}\tag{9.11}$$ $$SEN_{MO} = \frac{TPMO}{TPMO + FNMO}\tag{9.12}$$ $$SEN_{VM} = \frac{TPVM}{TPVM + FNVM}\tag{9.13}$$ $$SEN_N = \frac{TPN}{TPN + FNN}\tag{9.14}$$

实验使用原始数据库和增强数据库进行。原始样本的分类准确率为 71%。由于各类别之间存在数据差异，模型无法捕获相关属性。因此，需要采用数据级过采样方法。在 softmax 分类器中，采用 softmax 函数计算得到的似然分数用于 AD 分类。此设置（S1）正确预测了 121 个 MD 样本、4 个 MOD 样本、531 个 ND 样本和 330 个 VMD 样本。表 9.3 展示了不同设置所得的性能指标。

在设置（如 S2、S5 和 S8）中使用了带线性核的 SVM 分类器，而在 S3、S6 和 S9 等设置中则使用了带欧几里得核（K 值为 5）的 KNN 分类器。SVM 和 KNN 模型分别在 S2 和 S3 设置中使用提取的 1280 个特征进行评估。实验结果表明，SVM 分类器优于 KNN，准确率达到 74.2%。在 S4、S7 和 S10 等设置中采用了 Bi-LSTM 网络。该模型预测 MD 图像的准确率为 77%，MOD 图像为 41.6%，ND 图像为 84.3%，VMD 图像为 75.8%。

引入特征选择技术可以显著提高分类器的性能。利用小波变换来选择有用的属性。使用单级 Haar 小波将属性分解为近似系数和细节系数。由于近似频带包含重要信息，因此仅考虑这些特征。最终共选取了 640 个特征。在 S5 和 S6 设置中，分别使用这些特征对 SVM 和 KNN 分类器进行评估。S5 和 S6 设置分别获得了 79.5% 和 78.3% 的准确率。在 S7 设置中，使用 640 个特征对 Bi-LSTM 网络进行评估。该网络对 MD 图像的分类准确率为 78.7%，MOD 图像为 50%，ND 图像为 87.5%，VMD 图像为 80.3%。

## 表 9.3
不同配置下获得的性能指标

| 分类器 | ACC | SEN_M | SEN_MO | SEN_VM | SEN_N |
|---|---|---|---|---|---|
| S1 (Softmax) | 77.1 | 67.6 | 33.3 | 83 | 73.7 |
| S2 (SVM) | 74.2 | 44.7 | 50 | 72 | 89.7 |
| S3 (KNN) | 73.7 | 55.3 | 83.3 | 70.9 | 84.6 |
| S4 (Bi-LSTM) | 79.9 | 77 | 41.6 | 84.3 | 75.8 |
| S5 (Haar + SVM) | 79.5 | 78.2 | 33.3 | 83.5 | 75.4 |
| S6 (Haar + KNN) | 78.3 | 77.4 | 41.6 | 85.2 | 74.6 |
| S7 (Haar + Bi-LSTM) | 83.4 | 78.7 | 50 | 87.5 | 80.3 |
| S8 (Haar + PCA + SVM) | 82.4 | 77 | 50 | 92.1 | 71.4 |
| S9 (Haar + PCA + KNN) | 81.3 | 78.7 | 33.3 | 89 | 72.5 |
| S10 (Haar + PCA + Bi-LSTM) | 87.4 | 83.7 | 50 | 90.6 | 85.3 |

设置 S8、S9 和 S10 证明了小波变换和 PCA 的功效。提取的特征数量从 640 个减少到 254 个。使用这些属性对 SVM 和 KNN 分类器进行评估，在 S8 和 S9 设置中分别达到了 82.4% 和 81.3% 的准确率。显然，S8 和 S9 设置的计算复杂度低于 S2 和 S3 设置。

使用 254 个特征对 Bi-LSTM 模型进行实验评估，达到了 87.41% 的准确率。此设置（S10）预测 MD 图像的准确率为 83.7%，MOD 图像为 50%，ND 图像为 90.6%，VMD 图像为 85.3%。根据研究结果，当使用有用属性而非原始属性对分类器进行评估时，模型准确率有所提高。

对于定制的 ViT 模型，进行了微调。训练方式是针对四类分类问题定制 patch 嵌入层和分类器。另一方面，transformer 编码器的参数保持不变。本工作实现了三种不同模型尺寸的同构 ViT（例如，tiny [ViTT]、small [ViTS] 和 base [ViTB]）。表 9.4 展示了不同 ViT 获得的指标。可以推断，小型 ViT 模型以 88.6% 的总体准确率表现最佳。该模型正确分类了 154 个 MD 图像、6 个 MOD 图像、585 个 ND 图像和 388 个 VMD 图像。

## 表 9.4
不同 ViT 获得的性能指标

| 分类器 | ACC | SEN_M | SEN_MO | SEN_VM | SEN_N |
|---|---|---|---|---|---|
| ViTT | 87.4 | 82.1 | 41.6 | 89.6 | 84.2 |
| ViTS | 88.6 | 86 | 50 | 91.4 | 86.6 |
| ViTB | 86.8 | 83.7 | 50 | 89.5 | 85.2 |

将 S10 配置和 ViTS 模型获得的分数进行集成，准确率达到 90.38%。最终的 SVM 分类器正确预测 MD 图像的准确率为 87.1%，MOD 图像为 41.6%，ND 图像为 92.9%，VMD 图像为 89.2%。

## 与先前工作的比较
考虑将 Hon 等人 [14]、Farooq 等人 [12]、Ramzan 等人 [15]、Geneedy 等人 [23] 和 Islam 等人 [24] 提出的工作进行比较。预训练模型使用以下超参数实现：
- 批量大小：32
- 学习率：0.0001
- 最大轮数：100
- Adam 优化器

表 9.5 显示了不同模型获得的指标。Geneedy 等人提出的模型正确预测了 1279 张图像中的 1065 张，准确率为 83.3%。Islam 等人提到的对 DenseNet-121、DenseNet-161 和 DenseNet-169 的实验研究表明，DenseNet-161 模型的准确率最高，达到 85.6%。从研究结果可以推断，使用多数投票集成技术聚合三个模型的结果可将准确率提高 2%。最终的集成模型正确分类了 143 个 MD、9 个 MOD、571 个 ND 和 401 个 VMD 图像。这导致准确率达到 87.8%。Farooq 等人提出的研究三种深度 CNN（GoogLeNet、ResNet-18 和 ResNet-152）性能的实验表明，ResNet-152 模型的预测效果更好。在 1279 张图像中，有 1085 张图像被正确预测，准确率达到 84.8%。Ramzan 等人研究了 ResNet-18 中残差连接在从 MRI 图像预测 AD 疾病方面的有效性。结果表明，该模型正确预测了 1279 张图像中的 1070 张，准确率达到 83.6%。Hon 等人提到的对 VGG-16 和 Inception V4 的实验研究，其各自的模型总体准确率分别达到了 82.64% 和 84.6%。

## 表 9.5
各种模型与所提出模型的性能对比分析

| 作者 | ACC | SEN_M | SEN_MO | SEN_VM | SEN_N |
|---|---|---|---|---|---|
| Farooq 等人 [2017] | 84.8 | 71.5 | 83.3 | 86.1 | 87.6 |
| Hon 等人 [2017] | 84.6 | 74.3 | 83.3 | 85.9 | 86.7 |
| Islam 等人 [2018] | 87.8 | 79.8 | 75 | 89.5 | 89.2 |
| Ramzan 等人 [2019] | 83.6 | 70.9 | 75 | 86.2 | 86.2 |
| Geneedy 等人 [2023] | 83.3 | 70.9 | 91.7 | 85.0 | 85.9 |
| 所提模型 | 90.4 | 97.1 | 41.6 | 89.2 | 92.9 |

Inception V4 的架构改进使得 1279 张图像中有 1083 张被正确预测。

研究结果表明，所提出的模型优于其他现有方法。由于 MOD 图像的分布与其他三个类别不同，所提出的模型可能无法捕获 MOD 图像的独特特征。因此，MOD 图像的灵敏度远低于现有方法。然而，与其他模型相比，所提出的模型有效地捕获了 MD、ND 和 VMD 图像的特征，从而降低了误分类率。

## 9.5 结论
本文提出了一种利用 CNN 和 ViT 对 AD 阶段进行分类的有效框架。在不同的设置中使用不同的分类器对定制 CNN 获得的属性进行分类。每个设置的有效性在一个包含 21,994 张 MRI 图像（5198 张 MD、5212 张 MOD、5760 张 ND 和 5824 张 VMD 照片）的数据集上进行了评估。结果表明，使用 PCA 和小波变换获得的有用属性在使用 Bi-LSTM 网络进行分类时能显著提高性能。结论是，结合 CNN 和 Bi-LSTM 显著改善了 AD 分类任务的整体结果。微调定制的小型 ViT 模型实现了 88.6% 的总体准确率。通过使用堆叠集成方法整合最佳配置的 EfficientNet-B0 和最佳 ViT 模型的性能，观察到准确率的提高。在 1279 张图像中，所提出的方法正确预测了 1156 张图像。因此，所提出的方法可能有助于神经科医生对 AD 阶段进行分类。

## 参考文献
- 1. “World Alzheimer report 2018—The state of the art of dementia research: New frontiers.” Alzheimer’s Disease International, vol. 48, pp. 1–48, 2018.
- 2. R. Brookmeyer, E. Johnson, K. Ziegler Graham, and H. M. Arrighi, “Forecasting the global burden of Alzheimer’s disease.” Alzheimer’s and Dementia: The Journal of the Alzheimer’s Association, vol. 3, no. 3, pp. 186–191, Jul 2007.
- 3. S. S. Khan and G. S. Bloom, “Tau: The center of a signaling nexus in Alzheimer’s disease.” Frontiers in Neuroscience, vol. 10, pp. 1–5, Feb 2016.
- 4. P. Elangovan and M. K. Nath, “Glaucoma assessment from color fundus images using convolutional neural network.” International Journal of Imaging Systems and Technology, vol. 31, no. 2, pp. 955–971, June 2021.
- 5. P. Elangovan, D. Vijayalakshmi, and M. K. Nath, “Detection of glaucoma from fundus images using pre-trained densenet201 model.” Indian Journal of Radio and Space Physics, vol. 50, no. 1, pp. 33–39, March 2021.
- 6. P. Elangovan and M. K. Nath, “A novel shallow ConvNet-18 for malaria parasite detection in thin blood smear images.” SN Computer Science, vol. 2, no. 5, pp. 1–11, Jul 2021.
- 7. S. Majumdar, P. Pramanik, and R. Sarkar, “Gamma function based ensemble of CNN models for breast cancer detection in histopathology images.” Expert Systems with Applications, vol. 213, pp. 119022, Mar 2023.

