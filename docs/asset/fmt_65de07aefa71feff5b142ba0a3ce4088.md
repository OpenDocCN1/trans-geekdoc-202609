
# 第 15 章：联邦学习中的数据估值

## 15.7.2 基于相似度的梯度估值

当 HFL 中关注的对象从数据转变为梯度时，基于相似度的效用函数仍然足够通用以适用。由于客户端通常发送梯度给服务器以供后续聚合，因此提出了更适合梯度比较的相似度度量。

Xu 等人 [\[22\]](#Chp015_281-296_B9780443190377000247.xhtml#br0110) 提出利用梯度向量对齐来捕捉客户端上传梯度的贡献。直观上，梯度与所有客户端聚合梯度越接近，其贡献就越大。聚合梯度是全局模型损失值下降最快的方向。从这个角度来看，（方向上）相似的梯度在降低损失方面会更有效。具体而言，令第 `t` 次迭代中客户端 `m` 的参数更新为 `Δw[m, t] ≜ −η[t]∇gm)`，其中 `η[t]` 是第 `t` 次迭代的学习率，`gm)` 是第 `m` 个客户端关于 `w[m]^(t)` 的局部训练损失。服务器对梯度进行归一化和聚合：`u[m, t] ≜ ΓΔw[m, t]/||Δw[m, t]||`，`u[C, t] ≜ ∑[m ∈ C] r[m] u[m, t]`，其中 `Γ` 是用于防止梯度爆炸的归一化系数，`r[m]` 是可选的重要性权重因子。在这种公式化下，梯度对齐可通过*余弦相似度*来度量，效用函数定义如下：

```
ν(D_m) = cos(u_{m,t}, u_{A,t}) = ⟨u_{m,t}, u_{A,t}⟩ / (||u_{m,t}|| ⋅ ||u_{A,t}||)
```

![Image](img/si67.png)(15.16)

注意，上述效用函数可应用于客户端联盟 `C` 的数据 `D[C]`。我们将 (15.16) 与 (15.13) 和 (15.14) 结合使用，以获得数据的相应 Shapley 值。该方法称为余弦梯度 Shapley 值 (CGSV)。它使我们能够在无需任何辅助数据集的情况下，对贡献的梯度进行数据估值。值得注意的是，Shi 等人 [\[14\]](#Chp015_281-296_B9780443190377000247.xhtml#br0070) 持有相同观点，并提出了一种名为 FedFAIM 的类似梯度贡献评估公式化。在 (15.16) 的余弦相似度基础上，他们额外考虑了低质量局部梯度的质量检测与过滤。

## 15.8 基于学习的估值

在本节中，我们偏离了博弈论解概念，尽管已有近似努力，但当客户端数量庞大时，这些概念可能效率低下。*我们能否利用深度学习和强化学习的进展，直接对数据价值或评分函数进行建模？*

Yoon 等人 [\[25\]](#Chp015_281-296_B9780443190377000247.xhtml#br0125) 首先提出了利用强化学习进行数据估值的想法 (DVRL)。它将数据估值与目标预测模型的训练过程相结合，并利用强化信号来训练一个用于数据估值的网络。更具体地说，评估器 `g[ψ] : (x, c) → ω` 将训练样本映射为选择概率 `ω`，该概率代表在训练迭代中使用该样本的概率。目标预测模型记为 `f[θ]`。在一次训练迭代中，评估器首先估计大小为 `B[s]` 的一批训练样本 `{(x^(i), c^(i))}[i=1]^(B[s])` 的选择概率 `ω`。随后基于 `ω` 进行随机样本选择，得到选择向量 `S = [s[1], …, s[B[s]]]`，其中 `s[i] ∈ {0, 1}`。此处，0 和 1 分别代表丢弃或包含该样本。选中的样本继续训练预测器 `f[θ]`，其验证损失与之前损失的移动平均值 `δ` 相比较，所得结果作为奖励信号，通过强化学习训练评估器。评估器网络收敛后，选择概率在此学习任务中作为相对贡献（即数据价值）的替代指标。

上述思路已被 Zhao 等人 [\[26\]](#Chp015_281-296_B9780443190377000247.xhtml#br0130) 应用于联邦学习 (FL)。我们不再考虑数据样本，而是考虑客户端粒度的贡献或价值。联邦 REINFORCE 客户端贡献评估 (F-RCCE) 修改了评估器，使其以梯度（或等价地，通信轮结束时的局部模型）作为输入，即 `g[ϕ] : w[m]^(t) → ω`。与 DVRL 类似，`S^(t) ∈ {0, 1}^(n)`，奖励函数定义为

```
r(S^(t)) = (1/n_val) ∑_{k=1}^{n_val} ℓ(w^(t); x_val,k, c_val,k) - δ
```

![Image](img/si76_u2.png)(15.17)

其中 `ℓ` 是全局模型在验证集 `{(x[val, k], c[val, k])}[k=1]^(n[val])` 上的损失，`δ` 是之前损失的移动平均值。评估器的模型参数 `ψ` 以学习率 `α` 更新，

```
ψ^(t+1) ← ψ^(t) - α r(S^(t)) ∇[ψ] log p(S^(t)|ψ)|[ψ^(t)]
```

![Image](img/si78_u1.png)(15.18)

注意，在该框架中，评估器和全局目标模型首先被完全训练，然后固定评估器，在另一轮全新的目标模型重新训练中测量贡献。在 FL 这种情况下，迭代 `t` 的选择概率被解释为客户端在通信轮 `t` 中的相对贡献。总体而言，类似于 (15.14)，客户端 `m` 的数据价值是其在所有轮次中的选择概率之和。

DVRL 和 F-RCCE 相对高效，因为它们只需要对估值网络（即评估器）进行一次完整的训练。然而，该方法现在衡量的是某个数据或客户端被用于训练预测模型的可能性，这无法直接与学习中的相对贡献划等号。因此，上述论文 [\[25\]](#Chp015_281-296_B9780443190377000247.xhtml#br0125)、[\[26\]](#Chp015_281-296_B9780443190377000247.xhtml#br0130) 仅基于排名而非相对数据价值进行实验。值得注意的是，Shapley 值所实现的公平数据估值的理想性质和公理，并不由 DVRL 或 F-RCCE 保证。

## 15.9 结论与未来工作

受机器学习应用中评估数据价值的兴趣日益增长的驱动，本章概述了协作机器学习中的数据估值方法，重点关注联邦学习。数据估值为协作学习场景中的数据集提供了一种可解释的贡献归因方法。然而，必须注意现有方法的局限性以及未来研究的开放问题。

首先，当前的垂直数据估值方法并未针对 `FL` 的迭代学习过程量身定制。我们是应该对最终模型进行特征估值，还是像水平数据估值那样考虑按轮次估值，这尚有争议。其次，基于学习的估值仅应用于 `HFL`。探讨基于学习的估值在 `VFL` 上的适用性将很有趣。第三，通信带宽、算力、客户端的诚实度和可用性等属性是客户端对 `FL` 贡献的额外维度，这些有可能构成一个更完整的客户端估值框架。开放问题清单当然并不详尽，我们邀请感兴趣的读者对这一具有实际意义的新兴领域开展进一步研究。

总之，我们讨论了将传统数据估值方法扩展到联邦设置中的情况，并描述了专门为 `FL` 开发的水平和垂直数据估值方法。本章为一套多功能工具箱提供了指南，使 `FL` 从业者能够在各种场景中应用数据估值。

## 参考文献

*   [[1]](#Chp015_281-296_B9780443190377000247.xhtml#cf0255) Gavin Brown, Adam Pocock, Ming-Jie Zhao, Mikel Luján, Conditional likelihood maximisation: a unifying framework for information theoretic feature selection, *Journal of Machine Learning Research* 2012;13(1):27–66.

*   [[2]](#Chp015_281-296_B9780443190377000247.xhtml#cf0315) Wei-Sheng Chin, Bo-Wen Yuan, Meng-Yuan Yang, Yong Zhuang, Yu-Chin Juan, Chih-Jen Lin, LIBMF: a library for parallel matrix factorization in shared-memory systems, *Journal of Machine Learning Research* 2016;17(86):1–5.

*   [[3]](#Chp015_281-296_B9780443190377000247.xhtml#cf0170) R. Dennis Cook, Detection of influential observation in linear regression, *Technometrics* 1977;19(1):15–18.

*   [[4]](#Chp015_281-296_B9780443190377000247.xhtml#cs0020_1) Soumi Das, Manasvi Sagarkar, Suparna Bhattacharya, Sourangshu Bhattacharya, CheckSel: Efficient and accurate data-valuation through online checkpoint selection, 2022.

*   [[5]](#Chp015_281-296_B9780443190377000247.xhtml#cf0195) P. Dubey, On the uniqueness of the Shapley value, *International Journal of Game Theory* 1975;4(3):131–139.

*   [6] Zhenan Fan, Huang Fang, Zirui Zhou, Jian Pei, Michael P. Friedlander, Changxin Liu, Yong Zhang, Improving fairness for data valuation in horizontal federated learning, *Proc. ICDE*. 2022:2440–2453.

*   [7] Amirata Ghorbani, James Zou, Data Shapley: equitable valuation of data for machine learning, *Proc. ICML*. 2019:2242–2251.

*   [8] Xiao Han, Leye Wang, Junjie Wu, Data valuation for vertical federated learning: an information-theoretic approach, [arXiv:2112.08364](http://www.arxiv.org/abs/2112.08364); 2021.

*   [[9]](#Chp015_281-296_B9780443190377000247.xhtml#cs0025_1) Andreas Krause, Carlos Guestrin, Nonmyopic active learning of Gaussian processes: an exploration-exploitation approach, *Proc. ICML*. 2007:449–456.

*   [[10]](#Chp015_281-296_B9780443190377000247.xhtml#cs0025_2) John K. Kruschke, Bayesian approaches to associative learning: from passive to active learning, *Learning & Behavior* 2008;36(3):210–226.

*   [[11]](#Chp015_281-296_B9780443190377000247.xhtml#cf0285) Yongchan Kwon, James Zou, Beta Shapley: a unified and noise-reduced data valuation framework for machine learning, *Proc. AISTATS*. 2022.

*   [[12]](#Chp015_281-296_B9780443190377000247.xhtml#cf0230) Scott M. Lundberg, Su-In Lee, A unified approach to interpreting model predictions, *Proc. NeurIPS*. 2017:4768–4777.

*   [[13]](#Chp015_281-296_B9780443190377000247.xhtml#cf0105) Vassil Panayotov, Guoguo Chen, Daniel Povey, Sanjeev Khudanpur, LibriSpeech: an ASR corpus based on public domain audio books, *Proc. ICASSP*. 2015:5206–5210.

*   [[14]](#Chp015_281-296_B9780443190377000247.xhtml#cf0340) Zhuan Shi, Lan Zhang, Zhenyu Yao, Lingjuan Lyu, Cen Chen, Li Wang, Junhao Wang, Xiang-Yang Li, FedFAIM: a model performance-based fair incentive mechanism for federated learning, *IEEE Transactions on Big Data* 2022:1–13.

*   [[15]](#Chp015_281-296_B9780443190377000247.xhtml#cf0165) Rachael Hwee Ling Sim, Yehong Zhang, Mun Choon Chan, Bryan Kian Hsiang Low, Collaborative machine learning with incentive-aware model rewards, *Proc. ICML*. 2020:8927–8936.

*   [16] Tianshu Song, Yongxin Tong, Shuyue Wei, Profit allocation for federated learning, *Proc. IEEE Big Data*. 2019:2577–2586.

*   [[17]](#Chp015_281-296_B9780443190377000247.xhtml#cf0155) Sebastian Shenghong Tay, Xinyi Xu, Chuan Sheng Foo, Bryan Kian Hsiang Low, Incentivizing collaboration in machine learning via synthetic data rewards, *Proc. AAAI*. 2022.

*   [[18]](#Chp015_281-296_B9780443190377000247.xhtml#cf0245) Guan Wang, Charlie Xiaoqian Dang, Ziye Zhou, Measure contribution of participants in federated learning, *Proc. IEEE Big Data*. 2019:2597–2604.

*   [[19]](#Chp015_281-296_B9780443190377000247.xhtml#cf0185) Jiacheng Wang, Ruoxi Jia, Data Banzhaf: a data valuation framework with maximal robustness to learning stochasticity, *Proc. AISTATS*. 2023.

*   [20] Tianhao Wang, Johannes Rausch, Ce Zhang, Ruoxi Jia, Dawn Song, A principled approach to data valuation for federated learning, *Federated Learning*. Springer; 2020:153–167.
