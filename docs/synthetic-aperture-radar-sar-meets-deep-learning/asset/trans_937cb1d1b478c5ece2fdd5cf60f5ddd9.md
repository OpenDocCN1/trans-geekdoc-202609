
The use of the centroid distance is able to speed up bounding box alignment. Figure 21 displays different regression loss curves in the training phase. The TDIoU loss directly minimizes the distance between corresponding centroids and vertices of two boxes and, thus, converges much faster than other losses. Moreover, since we use the triangle distance rather than the diagonal length of the smallest enclosing box to construct the denominator of penalty term, TDIoU loss reduces the training time by nearly half compared with other IoU-based losses, indicating that the computing complexity of our method is greatly reduced. All in all, the proposed TDIoU loss is more applicable to rotated bounding box regression.

![](img/828a5d28a36454f7b3332df93f35492f_345_0.png)

图 20. 基于不同回归损失的 RetinaNet-R 在 (a) RSSD、(b) SSDD 和 (c) HRSC2016 上的 P–R 曲线。

![](img/828a5d28a36454f7b3332df93f35492f_345_1.png)

图 21. RetinaNet-R 在 RSSD 上的回归损失曲线。(a) 不同回归损失的整体比较；(b) TDIoU 损失与近似 IoU 损失的比较；(c) TDIoU 损失与其他基于 IoU 损失的比较。

## 6.3.3. AW-FPN 的有效性

由于所提出的 AW-FPN 结合了多重跳跃尺度连接和注意力加权特征融合（AWF）策略，我们希望了解它们各自对精度提升的贡献。因此，我们实现了七种具有不同连接路径和融合方法的特征融合网络以验证 AW-FPN 的有效性，如表 7–9 所示。值得注意的是，为了消除无关因素的影响，所有特征融合网络的结构仅使用一次。

表 7 显示了我们在 RSSD 上的结果。不同连接路径之间的比较表明，传统的 FPN 不可避免地受限于单一的自顶向下信息流，并且精度最低。具有额外自底向上路径的 PANet 在近岸 AP、离岸 AP 和测试 AP 上分别提升了 0.68%、0.59% 和 0.63%。具有单横向跳跃尺度连接和线性加权融合（LWF）策略的 BiFPN 分别将 AP 提升了 1.87%、1.13% 和 1.35%。对于同时具有横向和纵向跳跃尺度连接的 AW-FPN，即使是最简单的加法融合方法也能达到与 BiFPN 相似的性能。当使用与 BiFPN 相同的 LWF 方法时，AW-FPN 将 AP 提升了 2.38%、1.34% 和 1.58%，表明纵向跳跃尺度连接对特征融合也很重要。在不同融合方法之间的比较中，使用 AFF（仅通道注意力）时 AW-FPN 提升了 2.91%、1.63% 和 1.97%，使用所提出的 AWF（通道和空间注意力）时提升了 4.09%、2.06% 和 2.84%，表明基于注意力的融合方法优于线性融合方法，并且为了生成非线性融合权重，使用通道和空间注意力比仅使用单一通道注意力更好。当 CS²A-Net 用作基础检测器时，我们最终的 AW-FPN 进一步将 AP 提升了 3.96%、0.38% 和 1.50%。在另外两个数据集上也获得了类似的实验结果。从表 8 和表 9 可见，对于 SSDD 和 HRSC2016，所提出的 AW-FPN 在 RetinaNet-R 上取得了最出色的性能，并在先进的 CS²A-Net 上实现了显著提升，这证明了我们方法的有效性。

### 表 7. RSSD 上不同特征融合网络的比较。实验中所有特征融合网络的结构仅使用一次。这里，ADD 表示特征图的直接相加，而 LWF 表示 BiFPN [27] 中的线性加权融合方法。

| 检测器 | 融合网络 | 融合方法 | 融合类型 | 近岸 AP | 离岸 AP | 测试 AP |
|---|---|---|---|---:|---:|---:|
| RetinaNet-R (R-50) | FPN (baseline) | ADD | 线性 | 44.30 | 91.38 | 72.13 |
| RetinaNet-R (R-50) | PANet [25] | ADD | 线性 | 44.98 (+0.68) | 91.97 (+0.59) | 72.76 (+0.63) |
| RetinaNet-R (R-50) | BiFPN [27] | LWF | 线性 | 46.17 (+1.87) | 92.51 (+1.13) | 73.48 (+1.35) |
| RetinaNet-R (R-50) | AW-FPN | ADD | 线性 | 45.72 (+1.42) | 92.42 (+1.04) | 73.31 (+1.18) |
| RetinaNet-R (R-50) | AW-FPN | LWF | 线性 | 46.68 (+2.38) | 92.72 (+1.34) | 73.71 (+1.58) |
| RetinaNet-R (R-50) | AW-FPN | AFF (channel) | 软选择 | 47.21 (+2.91) | 93.01 (+1.63) | 74.10 (+1.97) |
| RetinaNet-R (R-50) | AW-FPN | AFF (channel + spatial) | 软选择 | **48.39 (+4.09)** | **93.44 (+2.06)** | **74.97 (+2.84)** |
| CS²A-Net (R-50) | FPN (baseline) | ADD | 线性 | 70.99 | 96.13 | 85.95 |
| CS²A-Net (R-50) | AW-FPN | AWF (channel + spatial) | 软选择 | **74.95 (+3.96)** | **96.51 (+0.38)** | **87.45 (+1.50)** |

### 表 8. SSDD 上不同特征融合网络的比较。

| 检测器 | 融合网络 | 融合方法 | 融合类型 | 近岸 AP | 离岸 AP | 测试 AP |
|---|---|---|---|---:|---:|---:|
| RetinaNet-R (R-50) | FPN (baseline) | ADD | 线性 | 59.35 | 97.10 | 86.14 |
| RetinaNet-R (R-50) | PANet [25] | ADD | 线性 | 60.98 (+1.63) | 97.30 (+0.20) | 86.80 (+0.66) |
| RetinaNet-R (R-50) | BiFPN [27] | LWF | 线性 | 61.83 (+2.48) | 97.42 (+0.32) | 87.13 (+0.99) |
| RetinaNet-R (R-50) | AW-FPN | ADD | 线性 | 61.62 (+2.27) | 97.38 (+0.28) | 87.05 (+0.91) |
| RetinaNet-R (R-50) | AW-FPN | LWF | 线性 | 62.02 (+2.67) | 97.44 (+0.34) | 87.20 (+1.06) |
| RetinaNet-R (R-50) | AW-FPN | AFF (channel) | 软选择 | 63.11 (+3.76) | 97.54 (+0.44) | 87.58 (+1.44) |
| RetinaNet-R (R-50) | AW-FPN | AFF (channel + spatial) | 软选择 | **65.71 (+6.36)** | **97.91 (+0.81)** | **88.63 (+2.49)** |
| CS²A-Net (R-50) | FPN (baseline) | ADD | 线性 | 75.79 | 98.79 | 92.08 |
| CS²A-Net (R-50) | AW-FPN | AWF (channel + spatial) | 软选择 | **78.83 (+3.04)** | **99.32 (+0.53)** | **93.38 (+1.30)** |

### 表 9. HRSC2016 上不同特征融合网络的比较。

| 检测器 | 融合网络 | 融合方法 | 融合类型 | 测试 AP₀₇ | 测试 AP₁₂ |
|---|---|---|---|---:|---:|
| RetinaNet-R (R-50) | FPN (baseline) | ADD | 线性 | 81.63 | 84.82 |
| RetinaNet-R (R-50) | PANet [25] | ADD | 线性 | 82.44 (+0.81) | 85.62 (+0.80) |
| RetinaNet-R (R-50) | BiFPN [27] | LWF | 线性 | 82.74 (+1.11) | 85.92 (+1.10) |
| RetinaNet-R (R-50) | AW-FPN | ADD | 线性 | 82.50 (+0.87) | 85.68 (+0.86) |
| RetinaNet-R (R-50) | AW-FPN | LWF | 线性 | 82.86 (+1.23) | 86.30 (+1.48) |
| RetinaNet-R (R-50) | AW-FPN | AFF (channel) | 软选择 | 83.27 (+1.64) | 86.89 (+2.07) |
| RetinaNet-R (R-50) | AW-FPN | AWF (channel + spatial) | 软选择 | **84.10 (+2.47)** | **88.02 (+3.20)** |
| CS²A-Net (R-50) | FPN (baseline) | ADD | 线性 | 89.94 | 94.91 |
| CS²A-Net (R-50) | AW-FPN | AWF (channel + spatial) | 软选择 | **90.21 (+0.27)** | **97.22 (+2.31)** |

图 22 显示了具有不同特征融合网络的 RetinaNet-R 的 P–R 曲线。AW-FPN 的 P–R 曲线始终高于其他方法。这可能是因为多重跳跃尺度连接增强了不同分辨率和尺度特征之间的语义交互，有助于上下文信息的互补。此外，与其他线性融合方法和仅使用通道注意力的 AFF 相比，所提出的 AWF 在多尺度通道注意力模块（MCAM）和多尺度空间注意力模块（MSAM）中聚合全局和局部特征上下文，以生成更高质量的融合权重。图 23 显示了不同特征融合网络的特征可视化。感兴趣区域（ROI）在特征热力图中被突出显示。其他方法生成的特征图中的 ROI 通常过大且包含大量背景杂乱。相比之下，我们 AW-FPN 生成的特征图中船舶的轮廓和位置更清晰准确，这有助于检测器更专注于真实的船舶目标而非背景杂乱，并学习更有用的上下文信息。

![](img/828a5d28a36454f7b3332df93f35492f_347_0.png)

**图 22.** RetinaNet-R 在 (a) RSSD、(b) SSDD 和 (c) HRSC2016 上具有不同特征融合网络的 P–R 曲线。

![](img/828a5d28a36454f7b3332df93f35492f_347_1.png)

**图 23.** 不同特征融合网络的特征可视化（以 $P_5$ 为例）。(a) 输入；(b) FPN (ADD)；(c) PANet (ADD)；(d) BiFPN (LWF)；(e) AW-FPN (ADD)；(f) AW-FPN (LWF)；(g) AW-FPN (AFF)；(h) AW-FPN (AWF)。

## 6.4. 与最先进方法的比较

我们将所提出的 AW-FPN 嵌入 CS²-A-Net 中并用我们的 TDIoU 损失进行训练，然后在三个数据集上将我们的方法与最先进的方法进行比较。

### 6.4.1. RSSD 上的结果

表 10 提供了 RSSD 上不同方法的定量比较。可以看出，最新的两阶段检测方法，如 CSL、SCRDet++ 和 ReDet，通常
