
*d̂*[*n*] = **w**^(*T*)**u**[*n*]

并利用期望响应序列 *d*[*n*] = *s*[*n* − 1] 来估计未知抽头。已知 𝔼\[*s*[*n*]\] = 𝔼\[*η*[*n*]\] = 0 且

*Σ*[*s*] = *σ*[*s*]²*I*, *Σ*[*η*] = *σ*[*η*]²*I*。

注意，对于期望响应，我们使用了延迟 *L* = 1。为了更好地理解使用延迟的原因，且不深入过多细节（对于经验丰富的读者，请注意信道是非最小相位的，例如 \[41\]），观察到在时刻 *n*，方程 [(4.58)](#Chp004_119-175_B978044329238500010X.xhtml#deq94) 中 *u*[*n*] 的主要贡献来自符号 *s*[*n* − 1]，其权重为 1，而采样值 *s*[*n*] 的权重为 0.5；因此，从直观角度来看，在时刻 *n* 收到 *u*[*n*] 后，尝试获得 *s*[*n* − 1] 的估计值是最自然的。这证明了使用延迟的合理性。

[图 4.15](#Chp004_119-175_B978044329238500010X.xhtml#f0080)A 展示了输入信息序列 *s*[*n*] 的一个实现。它由随机生成的、等概率的 ±1 采样值组成。信道的效应是 (a) 将连续的信息采样组合在一起（ISI）以及 (b) 添加噪声；均衡器的目的是最优地消除这两者。[图 4.15](#Chp004_119-175_B978044329238500010X.xhtml#f0080)B 展示了 *u*[*n*] 的相应实现序列，该序列在接收机前端接收。观察可知，仅凭肉眼无法从中识别出原始序列；噪声连同 ISI 确实改变了它的“外观”。

![Figure 4.15 (A) A realization of the information sequence comprising equiprobable, randomly generated, ±1 samples of Example 4.2. (B) The received at the receiver-end corresponding sequence. (C) The sequence at the output of the equalizer for a low channel noise case. The original sequence is fully recovered with no errors. (D) The output of the equalizer for high channel noise. The samples in gray are in error and of opposite polarity compared to the originally transmitted samples.](images/B978044329238500010X/gr015.jpg)

图 4.15 (A) 由等概率、随机生成的 ±1 采样值组成的信息序列的一个实现，见[示例 4.2](#Chp004_119-175_B978044329238500010X.xhtml#enun0030)。(B) 接收机端接收到的相应序列。(C) 低信道噪声情况下均衡器输出的序列。原始序列被完全恢复，无任何错误。(D) 高信道噪声情况下均衡器的输出。灰色的采样点为错误点，其极性与原始发送采样相反。

遵循与前一个示例类似的过程，我们得到（问题 [4.14](#Chp004_119-175_B978044329238500010X.xhtml#o0075)）
