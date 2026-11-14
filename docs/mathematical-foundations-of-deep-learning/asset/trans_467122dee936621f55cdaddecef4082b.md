

但由于当 \( D(G(\mathbf{z})) \) 接近 0 时会出现梯度消失，因此更倾向于使用非饱和生成器损失：

\[
\mathcal{L}_G = -\mathbb{E}_{\mathbf{z}\sim p_\mathbf{z}}[\log D(G(\mathbf{z}))]. \quad (515)
\]

GANs的收敛性与 \( D^*(\mathbf{x}) \) 的性质以及 \( p_g \) 与 \( p_{\text{data}} \) 的对齐性本质上是相关联的。然而，由于目标函数的非凸性，模式崩溃和训练不稳定性经常被观察到。Wasserstein GANs（WGANs）通过用Wasserstein-1距离取代JS散度来解决这些问题，其定义为

\[
W(p_{\text{data}}, p_g) = \inf_{\gamma \in \Pi(p_{\text{data}}, p_g)} \mathbb{E}_{(\mathbf{x}, \mathbf{y}) \sim \gamma} [||\mathbf{x} - \mathbf{y}||]. \quad (516)
\]

其中 \( \Pi(p_{\text{data}}, p_g) \) 是 \( p_{\text{data}} \) 和 \( p_g \) 的所有耦合集合。利用Kantorovich-Rubinstein对偶性，Wasserstein距离被重新表述为

\[
W(p_{\text{data}}, p_g) = \sup_{||f||_L \le 1} \mathbb{E}_{\mathbf{x} \sim p_{\text{data}}}[f(\mathbf{x})] - \mathbb{E}_{\mathbf{x} \sim p_g}[f(\mathbf{x})]. \quad (517)
\]

其中 \( f \) 是一个1-Lipschitz函数。为了强制执行Lipschitz约束，应用了梯度惩罚，确保 \( ||\nabla f(\mathbf{x})|| \le 1 \)。

GANs的数学框架整合了博弈论、优化和信息几何的要素。其训练涉及求解高维非凸博弈，由于鞍点以及 \( G \) 与 \( D \) 之间复杂的相互作用，收敛的理论保证具有挑战性。尽管如此，GANs代表了生成建模的一种数学优雅范式，正在进行的研究正在扩展其理论和实践能力。

## 9.3 自动编码器和变分自动编码器

### 文献综述

Zhang等人（2024）[303] 探索了VAEs与图像压缩中速率失真理论之间的理论联系。他们建立了将概率自动编码与有损图像压缩联系起来的数学框架，并引入了分层变分推断以提高生成建模能力。

Wang和Huang（2025）[304] 开发了过参数化VAEs中收敛的正式数学证明。他们为训练VAEs建立了严格的数学极限，并引入了神经切核（NTK）理论来研究VAEs在过参数化下的行为。

Li等人（2024）[305] 将VAEs扩展到材料科学，优化晶体结构预测。他们开发了基于VAE的分子建模框架，并展示了生成模型在图像应用之外的作用。

Huang（2024）[306] 回顾了VAEs、GANs和扩散模型在图像生成中的关键技术。他们分析了VAEs中与基于扩散的方法相比的概率建模，并建立了生成模型的理论层次结构。

Chenebuah（2024）[307] 研究了用于能源材料模拟和分子性质预测的自动编码器。他们引入了一种用于物理模拟的新型AE-VAE混合模型，并建立了密度泛函理论（DFT）与自动编码器之间的理论联系。

Furth等人（2024）[308] 探索了用于预测化学性质的图神经网络（GNNs）和VAEs。他们为基于图的学习建立了VAEs的理论属性，并将自动编码器扩展到化学反应预测。

Gong等人 [309] 研究了用于材料设计的条件变分自动编码器（CVAEs）。他们为条件生成建模引入了新的损失函数，并从理论上证明了VAEs如何优化材料选择。

Kim等人 [310] 使用基于Transformer的自动编码器（AEs）进行视频异常检测。他们建立了AEs用于时间序列异常检测的理论改进，并使用时空自动编码器嵌入来捕捉视频中的异常。

Albert等人（2024）[311] 比较了用于降维的核心学习嵌入（KLE）和变分自动编码器。他们引入了用于大气建模的基于VAE的模型，并建立了VAEs与基于核的模型之间的数学比较。

Sharma等人（2024）[312] 探索了自动编码器在网络入侵检测中的实际应用。他们将自动编码器确立为异常检测的强大特征提取器，并对自动编码器潜空间表示进行了正式研究。

一个 **自动编码器 (AE)** 是一种无监督学习模型，试图在较低维的潜空间中学习输入数据 $\mathbf{x} \in \mathbb{R}^d$ 的紧凑表示。该模型由两个主要组件组成：编码器函数 $f_{\theta_e}$ 和解码器函数 $f_{\theta_d}$。编码器 $f_{\theta_e} : \mathbb{R}^d \rightarrow \mathbb{R}^l$ 将输入数据 $\mathbf{x}$ 映射到潜码 $\mathbf{z}$，其中 $l \ll d$，表示压缩信息。解码器 $f_{\theta_d} : \mathbb{R}^l \rightarrow \mathbb{R}^d$ 然后从这个潜码重建输入，产生一个近似值 $\hat{\mathbf{x}}$。通常用于训练自动编码器的损失函数是重建损失，通常表述为均方误差（MSE）：

\[
\mathcal{L}(\mathbf{x}, \hat{\mathbf{x}}) = \|\mathbf{x} - \hat{\mathbf{x}}\|_2^2. \quad (518)
\]

优化过程旨在在数据集 $D$ 上最小化重建误差，假设输入数据 $\mathbf{x}$ 上存在分布 $p(\mathbf{x})$。目标是通过求解以下优化问题来学习最优参数 $\theta_e$ 和 $\theta_d$：

\[
\min_{\theta_e, \theta_d} \mathbb{E}_{\mathbf{x} \sim p(\mathbf{x})} \left[ \|\mathbf{x} - f_{\theta_d}(f_{\theta_e}(\mathbf{x}))\|_2^2 \right]. \quad (519)
\]

这种表述驱动编码器-解码器架构朝着学习保留输入数据关键特征的潜在表示方向发展，从而允许其被高效重建。此问题的解通常通过 **随机梯度下降 (SGD)** 来寻求，其中计算损失相对于模型参数的梯度并通过网络进行反向传播。与确定性自动编码器相反，**变分自动编码器 (VAE)** 引入了概率模型以更好地捕捉潜在变量的分布。VAE使用潜在变量 $\mathbf{z} \in \mathbb{R}^l$ 对数据生成过程进行建模，并旨在通过对所有可能的潜在变量进行积分来最大化观测数据 $\mathbf{x}$ 的似然性。具体来说，我们有联合分布：

\[
p(\mathbf{x}, \mathbf{z}) = p(\mathbf{x}|\mathbf{z})p(\mathbf{z}). \quad (520)
\]

其中 $p(\mathbf{x}|\mathbf{z})$ 是给定潜在变量的数据似然性，而 $p(\mathbf{z})$ 是潜在变量的先验分布，通常选择为标准高斯分布 $\mathcal{N}(\mathbf{z}; \mathbf{0}, I)$。先验假设 $p(\mathbf{z}) = \mathcal{N}(0, I)$ 简化了建模，因为它对潜空间不施加特定结构，从而允许对数据分布进行灵活建模。VAE中的编码器输出潜在变量上的分布 $q_{\theta_e}(\mathbf{z}|\mathbf{x})$，通常建模为均值 $\mu_{\theta_e}(\mathbf{x})$ 和方差 $\sigma_{\theta_e}(\mathbf{x})$ 的多元高斯分布，即 $q_{\theta_e}(\mathbf{z}|\mathbf{x}) = \mathcal{N}(\mathbf{z}; \mu_{\theta_e}(\mathbf{x}), \sigma_{\theta_e}^2(\mathbf{x})I)$。解码器生成给定潜在变量 $\mathbf{z}$ 的数据 $\mathbf{x}$ 的似然性，表示为 $p_{\theta_d}(\mathbf{x}|\mathbf{z})$，对于连续数据通常采用高斯分布的形式。VAE训练中的一个核心挑战是 **边缘似然性** $p(\mathbf{x})$，它表示观测数据的概率。由于对潜在变量的积分，这个边缘似然性是不可处理的：

\[
p(\mathbf{x}) = \int p_{\theta_d}(\mathbf{x}|\mathbf{z})p(\mathbf{z}) d\mathbf{z}. \quad (521)
\]

为解决这一问题，VAE训练采用 **变分推断**，它使用变分分布 $q_{\theta_e}(\mathbf{z}|\mathbf{x})$ 来近似真实后验 $p(\mathbf{z}|\mathbf{x})$。目标是优化 **证据下界 (ELBO)**，它是对数似然性 $\log p(\mathbf{x})$ 的下界。ELBO是利用 **Jensen不等式** 推导出来的：

\[
\log p(\mathbf{x}) \ge \mathbb{E}_{q_{\theta_e}(\mathbf{z}|\mathbf{x})} [\log p_{\theta_d}(\mathbf{x}|\mathbf{z})] - \text{KL}(q_{\theta_e}(\mathbf{z}|\mathbf{x}) \| p(\mathbf{z})). \quad (522)
\]

其中第一项是给定潜在变量的数据的预期对数似然性，第二项是近似后验与先验之间的 **Kullback-Leibler (KL)散度**

