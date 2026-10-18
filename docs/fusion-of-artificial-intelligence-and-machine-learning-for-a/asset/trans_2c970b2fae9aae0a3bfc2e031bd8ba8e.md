

# 10.4 帧选择与平均分算法

视频图像帧选择算法及其最大平均分的估计系数将在以下步骤中讨论：

1. 视频帧选择基于离散小波变换方法的平均值，该方法首先识别给定的输入图像（`I`），其可评估为：

   `I^I(DWT) = [I^I[ap], I[v, h, d]^I]`

   其中；`I[ap]` 表示图像的估计系数；`I[v,h,d]` 包含垂直、水平和垂直边带的系数细节。

   Fusion of Artificial Intelligence and Machine Learning for Advanced Image Processing, Data Analysis, and Cyber Security

2. 将应用高通滤波器和低通滤波器进行滤波过程，用于父小波的分解。

3. 下一级 DWT 现在已应用于第一步近似带中实现的第一个近似。

   `I^I(DWT) = [I^I[ap], I[v, h, d]^I]`

   其中；`I^I[ap], I[v, h, d]^I` 表示输入图像（`I`）的第二级估计。

4. 通过将图像分为 `xxy` 窗口并捕获它们来评估每个 DWT 带的平均值。`H(j) = - ∑(i=1 to m) P(j_i) log₂P(j_i)` 其中；`P(j[j])` 是概率质量函数，以概率形式指示像素值，反映在邻域中；`m` 是像素总数。

5. 如果窗口大小为 `L xW` 则：`x yP(j_i) = m_ji / (L_x × W_y)` 其中；`m[ii]` 表示窗口中的像素数量。

6. 现在将每个窗口的平均值合并以评估带的特征值。`FH = ∑(i=1 to μ) (|E_i|)` 其中；`FH` 表示特征分数值；`p` 是窗口数量；`E[i]` 是 `i[th]` 窗口的熵。

7. 图像 `I,FH (I)` 的最终总分是通过单独平均每个带的特征值得到的：`FH(I) = FH(I[ap]^I) + FH(I[h, v, d]^I) + FH(I[h, v, d])`

8. 对于视频图像 `V[i]`；帧的特征分数 `(f[i])` 由 `FH(f[i])` 表示，并使用以下公式获得最大-最小归一化：`m_min = (FH(f_i) - min(FH)) / (max(FH) - min(FH))` 其中；`FH` 表示 `V[i]` 的所有特征分数；`min(FH)`，`max(FH)` 表示 `FH` 的最小值和最大值。

9. 一旦评估了每个单独帧的分数，将执行帧选择的自适应过程以识别最佳帧集合。`θ_i = {1, if n_i ≥ σ_n + μ_n / 2; 0, otherwise}` 其中；`µp[n]` 表示适合特征值的均值；`σ[n]` 表示标准差。

10. 对从数据库检索到的丰富特征帧进行了测试，并使用匹配分数进行了验证以实现完美身份验证。与 Eigen、随机和正常特征图像相比，特征训练图像的误接受率和误拒绝率较高。从安全角度来看，有必要保持这些率较低，以实现理想的高验证性能。然而，特征训练图像的高误接受率是实现高验证率的积极指示。这有助于在视频监控和身份验证等实时图像应用中保持安全措施，如 [图 10.8](#ch10.xhtml#fig10_8) 和 [图 10.9](#ch10.xhtml#fig10_9) 所示。

![图 10.8 误接受率 (FAR)。来源：经 Upadhyay et al., 2023 许可复制。https://creativecommons.org/licenses/by/4.0/](images/fig10_8_C.jpg)

[图 10.8 误接受率 (FAR)。](#ch10.xhtml#R_fig10_8) *来源：* 经 Upadhyay et al., 2023 许可复制。[https://creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/)

![图 10.9 误拒绝率 (FRR)。来源：经 Upadhyay et al., 2023 许可复制。https://creativecommons.org/licenses/by/4.0/](images/fig10_9_C.jpg)

