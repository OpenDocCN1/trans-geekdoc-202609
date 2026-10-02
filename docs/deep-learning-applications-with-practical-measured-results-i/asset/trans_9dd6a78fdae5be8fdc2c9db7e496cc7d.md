
在“window”内推导分解。我们定义图像块的局部低频 DW-SSIM $S_{L,t}$ 和高频 DW-SSIM $S_{H,t}$ 为

$$S_{L,t}(\mathbf{c}^{(1)},\mathbf{c}^{(2)}) = \frac{2\left[\sum_u \sum_v c_{LL}^{(1)}[u,v]c_{LL}^{(2)}[u,v] + K\right]}{\sum_u \sum_v |c_{LL}^{(1)}[u,v]|^2 + \sum_u \sum_v |c_{LL}^{(2)}[u,v]|^2 + K}, \tag{7}$$

$$S_{H,t}(\mathbf{c}^{(1)},\mathbf{c}^{(2)}) = \frac{1}{J}\sum_{j=1}^{J} \frac{2\left|\sum_u \sum_v \sum_i c_i^{(1)}[u,v]c_i^{(2)}[u,v]\right| + K}{\sum_i \sum_u \sum_v |c_i^{(1)}[u,v]|^2 + \sum_i \sum_u \sum_v |c_i^{(2)}[u,v]|^2 + K}, i \in \{LH_j, HL_j, HH_j\}. \tag{8}$$

在公式（7）和（8）中，$K$ 是一个用于算术鲁棒性的小正常数，且 $K$ 设为 0.01。$\mathbf{c}^{(1)}$ 和 $\mathbf{c}^{(2)}$ 分别指原始图像块和经 2D-DWT 后恢复图像块对应的子带图像。我们使用的波函数是 Haar 小波。$t$ 为图像块索引。$J = 3$ 为最大分解层数，$c_{LH_j}, c_{HL_j}, c_{HH_j}$ 为第 $j$ 层的高频子带图像。

为了更好地理解公式（7），可以忽略 $K$，将 $\mathbf{c}$ “向量化”（如第 2.2.1 节所述）为 $\mathbf{c}_v$ 并重写为

$$S_{L,t}(\mathbf{c}^{(1)},\mathbf{c}^{(2)}) = S_{L,t}(\mathbf{c}_v^{(1)},\mathbf{c}_v^{(2)}) = 2\frac{|\mathbf{c}_v^{(1)} \cdot \mathbf{c}_v^{(2)}|}{\|\mathbf{c}_v^{(1)}\|_2^2 + \|\mathbf{c}_v^{(2)}\|_2^2}$$
$= 2\frac{\|\mathbf{c}_v^{(1)}\|_2 \|\mathbf{c}_v^{(2)}\|_2}{\|\mathbf{c}_v^{(1)}\|_2^2 + \|\mathbf{c}_v^{(2)}\|_2^2} \frac{|\mathbf{c}_v^{(1)} \cdot \mathbf{c}_v^{(2)}|}{\|\mathbf{c}_v^{(1)}\|_2 \|\mathbf{c}_v^{(2)}\|_2}$
$= 2\left(\frac{\|\mathbf{c}_v^{(1)}\|_2}{\|\mathbf{c}_v^{(2)}\|_2} + \frac{\|\mathbf{c}_v^{(2)}\|_2}{\|\mathbf{c}_v^{(1)}\|_2}\right)^{-1} |\cos(\theta)|. \tag{9}$$

在公式（9）中，第一项由子带图像的能量决定。只有当 $\|\mathbf{c}_v^{(1)}\|_2 = \|\mathbf{c}_v^{(2)}\|_2$ 时，它才会达到最大值 1。在第二项中，$\cos(\theta) = \frac{\mathbf{c}_v^{(1)} \cdot \mathbf{c}_v^{(2)}}{\|\mathbf{c}_v^{(1)}\|_2 \|\mathbf{c}_v^{(2)}\|_2}$ 是余弦相似度 [50]。如果 $\mathbf{c}_v^{(1)}$ 和 $\mathbf{c}_v^{(2)}$ 大致指向同一方向，余弦相似度将接近 1。然而，余弦函数的值域为 $[-1,1]$。因此我们取绝对值使其落在 $[0,1]$。公式（8）的解释在很大程度上与公式（7）相同。公式（8）额外对各层子带的贡献进行平均，以应对地下矿井图像中的规律性噪声。这可通过第 3.3 节的讨论更好地理解。

在第二阶段，对 $S_{H,t}$ 和 $S_{L,t}$ 进行加权求和以形成最终的 DW-SSIM $S$：

$$S(\mathbf{x},\hat{\mathbf{x}}) = \frac{1}{T}\sum_{t=1}^{T} \left(\gamma_1 S_{L,t} + \gamma_2 S_{H,t}\right), \tag{10}$$

其中 $T$ 为图像块总数，$\gamma_1$ 和 $\gamma_2$ 为调整低频子带和高频子带权重的参数。由于我们希望强调图像中边缘和尖峰等高频细节，因此设 $\gamma_1 = 0.2$ 且 $\gamma_2 = 0.8$。

DW-SSIM 的计算在算法 1 中进行了总结。所提方法中的窗口长度 $l$ 设为 15。窗口在每次迭代中移动的步长 $s$ 设为 8。

## 算法 1：计算离散小波相似度（DW-SSIM）的过程。

输入：原始图像 img-ori 和恢复图像 img-rec，高度 H 和宽度 W 相同（H > 0, W > 0）；分解层数 J；窗口在每次迭代中移动的步长 s；窗口长度 l；公式（10）中的权重 γ1 和 γ2

输出：img-ori 与 img-rec 之间的 DW-SSIM 相似度 S

```
S ← 0;
t ← 0;
up ← 0;
left ← 0;
while up < H do
  down ← up + l;
  while left < W do
    t ← t + 1;
    right ← left + l;
    Get image patch patch-ori within the window [up, down, left, right] from img-ori;
    Get image patch patch-rec within the window [up, down, left, right] from img-rec;
    Derive c^(1) by performing 2D-DWT on patch-ori;
    Derive c^(2) by performing 2D-DWT on patch-rec;
    Derive S_{L,t} from Equation (7);
    Derive S_{H,t} from Equation (8);
    S ← S + γ1 S_{L,t} + γ2 S_{H,t};
    left ← left + s;
  end
  up ← up + s;
end
S ← S / t;
return S;
```

DW-SSIM 损失。公式（10）定义的 DW-SSIM 的取值范围为 $(0,1]$。原始图像与恢复图像越匹配，DW-SSIM $S$ 越接近 1。然而，如果模型完美恢复，损失应接近 0。此外，损失应落在 $[0,1)$ 范围内。因此，我们将 DW-SSIM 损失定义为：

L_S(x, x̂) = 1 − S(x, x̂). (11)

## 2.4. 学习参数

编码模块和解码模块可使用所提网络架构和所提损失函数以端到端方式进行训练。采用小批量梯度下降训练模型，批量大小为 64。还使用了 Adam [51] 优化器。初始学习率设为 $5 \times 10^{-4}$。训练过程中若损失未下降，则学习率乘以 0.2。当学习率降至 $1 \times 10^{-6}$ 以下时停止训练。

## 3. 结果

### 3.1. 概述

为了推广恢复能力，所提方法的网络在我们收集的地下矿井视频图像以及 COCO 2014 数据集 [52] 的图像上进行训练。我们通过从图像中提取 $100 \times 100$ 中心裁剪块并将其转换为灰度图像来构建训练集。

模型训练完成后，将测试图像（如图 5 所示）输入模型进行压缩和恢复。我们在 Barbara、Fingerprint 和 Lena 等标准图像上测试我们的方法以验证其有效性。此外，我们还在来自真实地下矿井的采煤机和掘进机（TBM）图像上测试所提方法，以评估其在应用特定环境中的性能。

恢复质量通过峰值信噪比（PSNR）和结构相似度（SSIM） [46] 进行定量评估：

PSNR(x, x̂) = 10 log₁₀ d² / (1/N Σᵢ₌₁ᴺ (x[i] - x̂[i])² ), (12)

SSIM(x, x̂) = (2 μₓ μₓ̂ + C₁)/(μₓ² + μₓ̂² + C₁) · (2 σₓ σₓ̂ + C₂)/(σₓ² + σₓ̂² + C₂) · (σₓₓ̂ + C₃)/(σₓ σₓ̂ + C₃). (13)

在公式（12）中，d 为像素强度的动态范围，N 为图像中的像素数。在公式（13）中，μₓ 和 μₓ̂ 为 x 和 x̂ 的均值，σₓ² 和 σₓ̂² 为 x 和 x̂ 的方差。σₓₓ̂ 为 x 和 x̂ 的互相关。小正常数 C₁ = C₂ = C₃ = 0.01 用于防止各项的数值不稳定。

为了验证所提方法的有效性，在压缩比为 0.25、0.20、0.15、0.10、0.04 和 0.01 时进行定量评估，压缩比定义见公式（1）。此外，所提方法在不同压缩比下与 D-AMP [15]、ReconNet [13] 和 TVAL3 [29] 算法进行比较。为简化起见，我们未重新实现这些算法，而是使用作者网站提供的演示代码。

此外，在特定压缩比下还给出了恢复的视觉质量评估。最后，通过恢复受不同程度高斯噪声污染的图像来测试所提方法的鲁棒性。

所提方法使用 Pytorch [53] 和 pytorch_wavelet 包（https://github.com/fbcotter/pytorch_wavelets）实现。训练过程在 Ubuntu 18.04.2 上进行，使用 Nvidia Tesla K80 GPU 和 Intel Xeon CPU。有关实现的更多细节可在我们已在互联网上公开的代码中找到（https://github.com/y0umu/ResCSNet）。

![](img/8b41ef3997625b78ba4cb189dbc5f7b9_73_0.png)

图 5. 测试图像：（a）Barbara；（b）Fingerprint；（c）Lena；（d）采煤机；（e）掘进机（TBM）。

### 3.2. 定量评估

表 1 和表 2 给出了不同压缩比下所提方法和其他算法的定量测量结果。随着压缩比 r 的减小，所比较的所有算法的 PSNR 和 SSIM 均下降。从表 1 可看出，在压缩比 r ≥ 0.20 时，所提方法在标准测试图像和真实地下矿井图像上仅次于 D-AMP。然而，在压缩比 r ≤ 0.15 时，所提方法相比其他算法获得了最高的 PSNR。还应注意，在压缩比 r ≤ 0.04 时，采煤机和 TBM 图像的恢复结果中，所提方法比其他算法高出至少 1.8 dB，表明了所提方法在矿井应用特定使用方面的潜力。
