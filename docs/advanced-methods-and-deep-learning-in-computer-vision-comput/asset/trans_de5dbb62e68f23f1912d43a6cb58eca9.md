

这些方法是为各自的任务而设计的。即使对于去噪这一特定任务，基于模型的方法（如 BM3D (Dabov et al., 2007) 和 WNNM (Gu et al., 2014)）也能处理不同的噪声水平，而 (Jain and Seung, 2009) 的基于学习的方法则为每个噪声水平分别训练不同的模型。因此，这两类方法各有优缺点，研究它们的整合以充分发挥各自的优势是很有吸引力的。

基于模型的方法与基于学习的方法的整合催生了深度即插即用图像恢复（deep plug-and-play IR）方法，该方法用基于学习的 CNN 去噪器先验替代基于模型优化中的去噪子问题。深度即插即用图像恢复的主要思想是，借助变量分裂算法，如交替方向乘子法（ADMM）(Boyd et al., 2011) 和半二次分裂（HQS）(Geman and Yang, 1995)，可以将数据项和先验项分开处理 (Parikh et al., 2014)，特别是先验项仅对应于一个去噪子问题 (Danielyan et al., 2010; Heide et al., 2014; Venkatakrishnan et al., 2013)，该子问题可以通过深度 CNN 去噪器求解。因此，可以将深度即插即用方法视为基于模型方法的一个特例。

除了深度即插即用方法之外，深度展开方法也可以整合基于模型的方法和基于学习的方法。它们的主要区别在于，后者通过在大规模训练集上最小化损失函数来以端到端的方式优化参数，因此即使在迭代次数更少的情况下通常也能产生更好的结果。从数学上讲，深度展开方法可以建模为

$$\begin{cases}\min_{\theta} \sum_{i=1}^{N} \mathcal{L}(\hat{\mathbf{x}}_i, \mathbf{x}_i) & \text{(14.4a)} \\ s.t.\ \hat{\mathbf{x}}_i = \arg\min_{\mathbf{x}} \frac{1}{2\sigma^2}\|\mathbf{y}_i - (\mathbf{x} \otimes \mathbf{k}) \downarrow_s\|^2 + \lambda \mathcal{R}(\mathbf{x}). & \text{(14.4b)}\end{cases}$$

换句话说，深度展开方法旨在用展开推理式 Eq. (14.4b) 替换预定义函数 Eq. (14.3b)，因此可以将其视为基于学习方法的一个特例。深度展开图像恢复的主要思想是，首先通过半二次分裂算法展开基于模型的能量函数，得到一个迭代交替求解两个子问题的推理过程，一个与数据项相关，另一个与先验项相关；然后将该推理过程视为一个深度网络，用神经模块替换这两个子问题的求解。由于这两个子问题分别对应强制退化一致性知识和保证去噪器先验知识，深度展开方法具有明确的退化和先验约束，这是其相对于普通基于学习的 SISR 方法的一个显著优势。图 14.1 展示了基于学习的方法、基于模型的方法、深度即插即用方法和深度展开方法之间联系的示意图。

本章其余部分的组织如下。由于深度即插即用和深度展开方法都与变量分裂算法高度相关，我们首先在 14.2 节介绍其中最流行的一种算法，即半二次分裂（HQS）算法。然后我们在 14.3 节介绍深度即插即用图像恢复方法。具体来说，我们提出了一种高度灵活且有效的 CNN 去噪器先验，然后将深度去噪器先验作为模块化部分插入 HQS 算法中，以解决各种图像恢复问题。在 14.4 节中，我们提供了深度展开图像恢复方法，该方法可以通过单一模型处理不同模糊核和尺度因子的去模糊和超分辨率问题。14.5 节展示了定量和定性结果，并提供了对超参数设置和中间结果的深入分析，以更好地理解深度即插即用方法和深度展开方法的工作机制。

![](img/fe161b7f6e96e35e7e853eece52c6dce_504_0.png)

图 14.1 基于学习的方法、基于模型的方法、深度即插即用方法和深度展开方法之间联系的示意图。

## 14.2 半二次分裂（HQS）算法

尽管存在各种变量分裂算法可以求解 Eq. (14.2)，但半二次分裂（HQS）算法因其简单和快速收敛而广受欢迎。因此，本章采用 HQS。通常，HQS 通过引入辅助变量 z 来解决 Eq. (14.2)，从而得到以下近似等价关系

$E_{\mu}(\mathbf{x}, \mathbf{z}) = \frac{1}{2\sigma^2} \|\mathbf{y} - (\mathbf{z} \otimes \mathbf{k}) \downarrow_{\mathbf{s}} \|^2 + \lambda \Phi(\mathbf{x}) + \frac{\mu}{2} \|\mathbf{z} - \mathbf{x}\|^2, \qquad (14.5)$

其中 $\mu$ 是惩罚参数。这样的问题可以通过迭代求解关于 $\mathbf{x}$ 和 $\mathbf{z}$ 的子问题来处理

$\begin{cases} \mathbf{z}_k = \arg\min_{\mathbf{z}} \|\mathbf{y} - (\mathbf{z} \otimes \mathbf{k}) \downarrow_{\mathbf{s}} \|^2 + \mu \sigma^2 \|\mathbf{z} - \mathbf{x}_{k-1} \|^2, & (14.6) \\ \mathbf{x}_k = \arg\min_{\mathbf{x}} \frac{\mu}{2} \|\mathbf{z}_k - \mathbf{x}\|^2 + \lambda \Phi(\mathbf{x}). & (14.7) \end{cases}$

根据 Eq. (14.6)，$\mu$ 应足够大，以便 $\mathbf{x}$ 和 $\mathbf{z}$ 近似等于不动点。然而，这也会导致收敛速度减慢。因此，一个经验法则是迭代地增大 $\mu$。为方便起见，在第 $k$ 次迭代中，$\mu$ 记为 $\mu_k$。

可以观察到，数据项和先验项分别解耦到 Eq. (14.6) 和 Eq. (14.7) 中。对于 Eq. (14.6) 的求解，在假设卷积以循环边界条件进行的情况下，可以利用快速傅里叶变换（FFT）。值得注意的是，它有一个闭式表达式 (Zhao et al., 2016)

$$\mathbf{z}_k = \mathcal{F}^{-1}\left(\frac{1}{\alpha_k}\left(\mathbf{d} - \overline{\mathcal{F}(\mathbf{k})} \odot_s \frac{(\mathcal{F}(\mathbf{k})\mathbf{d}) \Downarrow_s}{(\overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{k})) \Downarrow_s + \alpha_k}\right)\right), \tag{14.8}$$

其中 d 定义为

$$\mathbf{d} = \overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{y} \uparrow_s) + \alpha_k \mathcal{F}(\mathbf{x}_{k-1})$$

其中 $\alpha_k \triangleq \mu_k \sigma^2$，$\mathcal{F}(\cdot)$ 和 $\mathcal{F}^{-1}(\cdot)$ 分别表示 FFT 和逆 FFT，$\overline{\mathcal{F}(\cdot)}$ 表示 $\mathcal{F}(\cdot)$ 的复共轭；$\odot_s$ 表示具有逐元素乘法的独特块处理算子，即对 $\overline{\mathcal{F}(\mathbf{k})}$ 的 $s\times s$ 独特块进行逐元素乘法；$\Downarrow_s$ 表示独特块下采样算子，即对 $s\times s$ 独特块进行平均；$\uparrow_s$ 表示标准的 $s$ 倍上采样算子，即通过用零填充新条目来上采样空间大小。对于 $s = 1$ 时的去模糊特例，Eq. (14.8) 可以简洁地写为

$$\mathbf{z}_k = \mathcal{F}^{-1}\left(\frac{\overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{y}) + \alpha_k \mathcal{F}(\mathbf{x}_{k-1})}{\overline{\mathcal{F}(\mathbf{k})}\mathcal{F}(\mathbf{k}) + \alpha_k}\right). \tag{14.9}$$

换句话说，Eq. (14.8) 是 Eq. (14.9) 的推广。对于 Eq. (14.7) 的求解，众所周知，从贝叶斯的角度来看，它实际上对应于一个噪声水平为 $\beta_k \triangleq \sqrt{\lambda/\mu_k}$ 的去噪问题 (Chan et al., 2017)。

## 14.3 深度即插即用图像恢复

即插即用图像恢复通常涉及两个步骤。第一步是通过某种变量分裂算法将目标函数的数据项和先验项解耦，得到一个由交替求解数据子问题和先验子问题组成的迭代方案。第二步是使用任何现成的去噪器（如 K-SVD (Elad and Aharon, 2006)、非局部均值 (Buades et al., 2005)、BM3D (Dabov et al., 2007)）来求解先验子问题。因此，与需要指定显式且手工设计的图像先验的传统基于模型的方法不同，即插即用图像恢复可以通过去噪器隐式地定义先验。这种优势为利用非常深的 CNN 去噪器来提高有效性提供了可能性。

即插即用图像恢复可以追溯到 Danielyan et al. (2010); Zoran and Weiss (2011); Venkatakrishnan et al. (2013)。Danielyan et al. (2012) 使用纳什均衡推导出一种用于图像去模糊的迭代解耦去模糊 BM3D（IDDBM3D）方法。在 Egiazarian and Katkovnik (2015) 中，提出了一种配备 CBM3D 去噪器先验的类似方法，用于单图像超分辨率（SISR）。通过迭代更新反投影步骤和 CBM3D 去噪步骤，该方法在 PSNR 上相对于 SRCNN (Dong et al., 2016) 的提升表现出令人鼓舞的性能。在 Danielyan et al. (2010) 中，增广拉格朗日

