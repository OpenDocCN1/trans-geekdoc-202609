
FIGURE 13.1 Framework of the data analysis for quantifying cerebrovascular changes from MRA imaging data.

#### 手动训练切片分割

患者的 MRA 数据包含 160 片 MRA 切片。每隔十片切片手动分割，使用 Adobe Photoshop（Adobe Systems, CA）将血管从周围组织中分离。该方法能够在像素级别上准确划分体内血管与周围组织，其主要局限性是 MRI 机器本身的分辨率。手动分割的二值训练切片（黑色为周围组织，白色为目标血管）被称为真实情况（GT），因为图像无伪影或噪声（Figure 13.2）。手动分割的选定切片用于初始化和优化分割算法，随后该算法用于分割所有获取的切片。

![FIGURE 13.2 (a) Original MRA image slice of sample patient at day 0. (b) Manually segmented ground truth (GT) image from the image in (a).](img/fig13_2.jpg)

FIGURE 13.2 (a) Original MRA image slice of sample patient at day 0. (b) Manually segmented ground truth (GT) image from the image in (a).

#### 自动分割

在常规计算机辅助诊断中，准确提取 3D 脑血管信息是一项主要挑战。我们的方法是通过在统计框架内定义感兴趣区域的概率模型，而不预先固定这些模型 \[15, 16, 17\]。对每张 MRA 切片，使用 LCDG 作为灰度分布的近似模型，并将切片划分为三个个体化的 LCDG，分别对应暗灰（骨骼和脂肪）、浅灰（脑组织）和亮灰（血管）三种主导模式。通过设定强度阈值来标记血管，随后对提取的体素应用 3D 连通性过滤，选择所需的血管树结构。该方法在分割精度和准确性上优于其他方法 \[16\]。

将期望–最大化（EM）技术适配到 LCDG，可精确识别特定模型（包括其分量数量（正负）），并构造一个连续的 LCDG 模型，包含概率分布。

为确定 LCDG 模型，采用包含期望对数似然的标准，即 \[16\]。假设一个三维 MRA 图像由 `X = (X[s]: s = 1,…, S)` 表示，其中包含 `S` 个共注册的二维切片 `X[s] = (X[s] (i, j): (i, j) ∈ R; X[s] (i, j) ∈ Q)`。另一方面，支撑三维图像的矩形算术格子由 `R` 表示，有限的灰度集合和 `Q` 进制强度由 `Q = {0, 1,…, Q−1}` 表示。令 `F[s] = (f[s](q): q ∈ Q; ∑_{q∈Q} f[s](q) = 1`；在本方程中，`q` 为一种灰度值，被视为切片 `X[s]` 的灰度的经验边缘概率分布。

根据 Ref. \[18\]，每个 MRA 切片被视为 `K` 模态的，即具有 `K` 个主要模式的感兴趣区域的固定数目。为实现分层切片，需要分别估计信号的概率分布。这些信号对应 `F[s]` 中的每个模式。`F[s]` 与对抗传统的每个区域一个高斯混合模型（Gaussian mixture）相近，或略具灵活性的包含其他简单分布的混合模型，每个区域一个。子模型，每个代表主导模式，是 LCDG 图像的划分结果 \[19, 20, 21\]。

离散高斯分布定义在整数集合（灰度值） `Q = {0,1,…,Q−1}` 上，其概率质量函数为

$$\psi{\left( q \middle| \theta \right) = \begin{Bmatrix} {\Phi\left( 0.5 \right),} & {q = 0} \\ {\Phi\left( q + 0.5 \right) - \Phi\left( q - 0.5 \right)} & {1 \leq q < Q - 1} \\ {1 - \Phi\left( q - 0.5 \right),} & {q = Q - 1,} \\ \end{Bmatrix}}$$

其中参数 `θ = (μ, σ)`，`Φ` 为均值为 `μ`、方差为 `σ²` 的正态分布的累积分布函数。

随后，LCDG 具有 `C[p]` 个正向分量和 `C[n]` 个负向分量，且 `C[p] ≥ K`，其概率质量函数为

$${p_{w,\Theta}\left( q \right) = \sum\limits_{r = 1}^{C_{p}}w_{p,r}\psi\left( {q\text{|}\theta_{p,r}} \right) - \sum\limits_{l = 1}^{C_{n}}w_{n,l}\psi\left( q \middle| \theta_{n,l} \right)}\mspace{54mu}\operatorname{(13.1)}$$

权重 `w = (w[p,1],…, w[p,Cp], w[n,1],…, w[n,Cn])` 受限为全部非负，并满足

$${\sum\limits_{r = 1}^{C_{p}}w_{p,r} - \sum\limits_{l = 1}^{C_{n}}w_{n,l} = 1}\mspace{54mu}\operatorname{(13.2)}$$

总体而言，为使概率有效，必须非负：`p[w]`、`Θ(q) ≥ 0` 对所有 `q ∈ Q`。这意味着仅使用概率分布的 LCDG 子集是有效的；但该子集仍可能包含负组分，即 `p[w]`、`Θ(q) < 0` 对某些 `q ∈ Q`。

本研究的目标是寻找一个 `K`‑模态概率模型，能够逼近灰度值的边缘分布（该分布未知）。若 `F` 为 `F[s]` 的贝叶斯估计，则可描述为

`f(q) = (|R| f[s](q) + 1)/(|R| + Q)`

模型应在最大化统计独立经验数据的期望对数似然，以及其他参数的同时工作：

$${L\left( {w,\operatorname{}\Theta} \right) = \sum\limits_{q \in Q}f\left( q \right)\log p_{w},_{\Theta}\left( q \right)}\mspace{54mu}\operatorname{(13.3)}$$

整个分割算法如下 \[16\]。

1. 对每个切片 `X[s]`，`s = 1,…, S`，

    - 首先聚集边缘经验概率分布 `F[s]`，它代表灰度值。

    - 使用初始化算法确定一个接近 `F[s]` 的 LCDG 模型，该算法可估计 `C[p] − K`、`C[n]` 以及正负离散高斯分布（DG）的权重 `w`、均值 `θ`（即均值、方差）的参数。

    - 固定 `C[p]` 与 `C[n]`，使用改进的 EM 算法细化 LCDG 模型，调整其他参数。

    - 将最终 LCDG 模型划分为 `K` 个子模型，每个子模型对应一个主导模式。通过最小化误分类错误并选择平均值最大（即亮度最高的像素）的 LCDG 子模型，作为所需血管模型。

    - 使用强度阈值 `t` 提取血管体素，使其从背景中分离，从而将对应的 LCDG 子模型与背景分开。

2. 借助连接滤波器，对提取的体素整体进行去除伪影，该滤波器通过 3D 增长算法（即最大相连树）构建系统 \[23\]。Algorithm 13.1 概括了所采用的分割方法：

该过程旨在解码每个 MRA 切片的阈值，从而实现对亮血管的完整提取，同时去除暗色的不需要组织，并将可能因亮度相似且边界相同的周围非血管组织也分离出来。当步骤 1b 初始化时，创建基于非负初始概率 `p[w]`、参数 `θ(q)` 的 LCDG。步骤 1c 中进行的细化则提升似然，但保持概率非负。Ref. \[16\] 中的实验表明，相反的情况从未出现。

自动分割的准确性通过与地面真实的总错误来衡量。评估指标包括真阳性（TP）、真阴性（TN）、假阳性（FP）和假阴性（FN）。

在 Figure 13.3 中，若 `C` 为分割区域，`G` 为地面真实，`R` 为整个图像框架，则 `TP = |C∩G|`，`TN = |R−C∪G|`，`FP = |C−C∩G|`，`FN = |G−C∩G|`。总错误 `ε` 如 Ref. \[24\] 给出：`ε = (FN + FP)/(TP + FN) = (FN + FP)/G`。

![FIGURE 13.3 Illustration of segmentation accuracy and errors of the proposed automatic segmentation (C) by comparing to the ground truth (G) \[5\].](images/fig13_3.jpg)

FIGURE 13.3 Illustration of segmentation accuracy and errors of the proposed automatic segmentation (C) by comparing to the ground truth (G) \[5\].

#### Voxel Matching

Voxels are defined as arrays of volume elements constituting a notional 3D space. A 3D affine registration is employed to handle pose, orientation, data spacing, and other scanning parameter changes between day 0 and day 700 \[25\]. In this step, the Euclidean radii are converted into diameter values, and the output is then transformed into a distance map.

#### Probability Distribution Function Generation and Validation

The EM‑based technique is adapted to the LCDG‑model. To calculate the probability distribution of changes in the cerebrovascular structure, the distance map is used to extract pixel distance distribution. White pixel distribution is marked by the PDF as the true value, while black pixels are ignored for the dataset. Vessel diameters are determined by estimating Euclidean center‑to‑edge distances. The data points in the generated PDFs are then extracted and compared with BP data using statistical analysis.

#### 计算累积分布函数（CDF）

PDF 的积分用于生成 CDF。（随机变量 `X` 的 CDF `F[X]` 通过其 PDF `f[X]` 使用 `$F_{X}\left( x \right) = \int\limits_{ - \infty}^{x}f_{X}\left( t \right)dt$` 计算。）CDF 显示血管在小于或等于代表每个切片中平均血管直径的直径值时，累计概率的总和。CDF 在上限为 1 的情况下显示 PDF 的累计分布。CDF 线越快接近 1，说明血管直径相对于 CDF 线较慢接近 1 的情况更小。此现象在结果部分有所说明。

### 13.2.3 统计分析

统计分析使用 R 软件（版本 3.3）进行。采用混合效应线性模型检验 MRA 数据与临床血压（BP）测量的关系。将脑切片分为上部（位于 Willis 环上方）和下部（位于 Willis 环下方）两个区域，以评估其与临床血压读数的相关性。Willis 环位于大脑底部，是颅内脑血管动脉起始并逐渐分支的部位 \[5\]. 血压测量被合并为一个值，即估计均压 `MAP = (2 × DBP + SBP)/3`，该值作为模型的协变量。模型还包含患者年龄、性别以及每位患者的随机截距。因变量为每个区域内血管树的欧氏距离图的平均值。（分别为上下区域拟合了两个独立模型。）固定效应的统计显著性通过似然比卡方测试确定。

### 13.2.4 3D 脑血管重建

采用一种能够通过去除任何不需要的分割体素的生长树模型，并结合平滑算法，以基于分割切片生成 3D 模型 \[23\]。下图展示了生成的血管系统的示例可视化和插图，位于结果部分。

## 13.3 结果

特异性和灵敏度值如下表 13.1 所示，来自分割图像。对 15 位患者的所有自动分割切片与手动分割的参考值（GT）进行了比较，以评估算法的准确性（Figure 13.4）。分割算法的累计灵敏度为 0.997 ± 0.008（灵敏度范围 = 0.969–1），累计特异度为 0.9998 ± 0.0001（特异度范围 = 0.9994–1）。手动分割的训练切片（每第十个切片）已被排除在拟议分割方法的准确性计算之外。

![FIGURE 13.4 分割算法输出示例；(a) 患者第 0 天的样本图像切片。自动分割切片与手动分割的参考值（GT）进行比较以评估分割算法的准确性。(b) 使用生长树模型对分割的脑血管系统进行样本 3D 重建。](img/fig13_4.jpg)

FIGURE 13.4 分割算法输出示例；(a) 患者第 0 天的样本图像切片。自动分割切片与手动分割的参考值（GT）进行比较以评估分割算法的准确性。(b) 使用生长树模型对分割的脑血管系统进行样本 3D 重建。

TABLE 13.1 自动分割图像在第 0 天、第 700 天以及累计灵敏度和特异度值的灵敏度和特异度值表

| 时间 | 灵敏度 | 特异度 |
| --- | --- | --- |
| 第 0 天 | 0.997 ± 0.006 | 0.9998 ± 0.0001 |
| 第 700 天 | 0.996 ± 0.008 | 0.9998 ± 0.0001 |
| 累计 | 0.997 ± 0.008 | 0.9998 ± 0.0001 |

线性混合效应模型分析结果（Table 13.2）显示，Willis 环下方血管的平均直径与均压（MAP）呈负相关（`P` = 0.0007）。Willis 环下方血管的平均直径未发现与患者年龄或性别显著相关。Willis 环上方的血管直径随年龄呈显著下降（`P` = 0.0005）。

TABLE 13.2 混合效应线性模型统计评估

**Willis 环下方血管的平均直径**

| 效应 | 估计 | χ² | P-Value |
| --- | --- | --- | --- |
| 年龄 | 3.2 μm/y | 0.356 | 0.551 |
| 性别 | F > M 多 12.8 μm | 0.026 | 0.872 |
| 均压 | −5.3 μm/mmHg | 11.63 | 0.0007 |

**Willis 环上方血管的平均直径**

| 效应 | 估计 | χ² | P-Value |
| --- | --- | --- | --- |
| 年龄 | −16.5 μm/y | 12.29 | 0.0005 |
| 性别 | F > M 多 16.0 μm | 0.199 | 0.655 |
| 均压 | 1.6 μm/mmHg | 0.402 | 0.525 |

`P`‑值 < 0.05 为统计显著。直径表示分割图像中血管的大小。年龄、性别和时间点为临床获取的数据。

在分析中，13 位患者表现出 MAP 与 CDF 之间的显著相关性。在表现出 CDF 与 MAP 相关性的 13 位患者中，有两位示例患者（A、B）以及两位未表现出 CDF 与 MAP 相关性的患者（C、D）（Figure 13.5）。患者 C 的 CDF 偏移与 MAP 变化方向相反，患者 D 的 CDF 偏移相对于 MAP 变化更大（Figure 13.5c 与 d，Table 13.3）。患者 C 和 D 的 3D 脑血管重建显示了第 0 天与第 700 天之间的显著血管变化（Figure 13.6）。

![FIGURE 13.5 示例患者 CDF 图，展示第 0 天到 700 天的时间变化。图表指示血管直径小于或等于某一数值的概率。](img/fig13_5.jpg)

FIGURE 13.5 示例患者 CDF 图，展示第 0 天到 700 天的时间变化。图表指示血管直径小于或等于某一数值的概率。

![FIGURE 13.6 通过对二值分割图像体积应用 3D 生长算法，可视化自动分割 MRA 数据。患者 C 第 0 天（左上），患者 C 第 700 天（右上），患者 D 第 0 天（左下），患者 D 第 700 天（右下）。这些结果展示了这些患者的脑血管结构随时间变化（圆圈标记）。](img/fig13_6.jpg)
