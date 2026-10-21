
## 64.5.2 混合卡尔曼滤波器

具有某种概率结构。利用离散指示变量，该模型可用于处理异常值、突变、系统故障、环境变化和杂波。如果 λ_t 遵循具有转移概率 p_ij = Prob[λ_t = j|λ_{t-1}= i] 的马尔可夫链机制转换过程，则上述状态空间模型变为具有机制转换的状态空间模型。

Chen 和 Liu (2000) 提出了一种特殊的序贯蒙特卡洛方法，即混合卡尔曼滤波器 (MKF)，它使用高斯分布的随机混合来近似目标分布。MKF 可用于滤波和估计具有机制转换的状态空间模型。我们在以下部分介绍 MKF 的算法。

设 y_{1:t} = (y_1,...,y_t) 为观测值，λ_{1:t} = (λ_1,...,λ_t) 为截至时间 t 的机制指示变量。我们注意到 p(x_t|y_{1:t}) = ∫ p(x_t|λ_{1:t}, y_{1:t})p(λ_{1:t}|y_{1:t})dλ_{1:t}，其中 p(x_t|λ_{1:t}, y_{1:t}) ~ N{μ_t(λ_{1:t}), Σ_t(λ_{1:t})}，其中 {μ_t(λ_{1:t}), Σ_t(λ_{1:t})} 可通过给定轨迹 λ_{1:t} 运行卡尔曼滤波器获得。MKF 的主要思想是使用指示变量的加权蒙特卡洛样本，

$$S_t = \{ (λ_{1:t}^{(1)}, w_t^{(1)}), ..., (λ_{1:t}^{(m)}, w_t^{(m)}) \}$$

用来表示分布 p(λ_{1:t}|y_{1:t})。具体而言，我们从预先选择的试验分布 q(λ_{1:t}|y_{1:t}, x_{1:t}) 中采样 λ_{1:t}^{(j)}, j = 1,...,N 并赋予 w_t^{(j)} = p(λ_{1:t}|y_{1:t})/q(λ_{1:t}|y_{1:t}, x_{1:t})。根据重要性采样逻辑，高斯分布的混合

$$\frac{1}{W_t} \sum_{j=1}^N w_t^{(j)} N\{ μ_t(λ_{1:t}^{(j)}), Σ_t(λ_{1:t}^{(j)}) \}$$

其中 W_t = ∑_{j=1}^N w_t^{(j)}，近似目标分布 p(x_t|y_{1:t})。对于任意可积函数 h(·)，我们可以估计感兴趣的量 E{h(x_t)|y_{1:t}} 为

$$\hat{E}\{h(x_t)|y_{1:t}\} = \frac{1}{W_t} \sum_{j=1}^N w_t^{(j)} \int h(x) \phi\{x; μ_t(λ_{1:t}^{(j)}), Σ_t(λ_{1:t}^{(j)})\} dx,$$

其中 φ 为高斯密度函数。

设 KF_t^{(j)} = (μ_t(λ_{1:t}^{(j)}), Σ_t(λ_{1:t}^{(j)}))，它记录了在给定轨迹 λ_{1:t}^{(j)} 且条件于 y_{1:t} 的 x_t 的后验均值和协方差矩阵。这可通过卡尔曼滤波器获得。然后 MKF 更新方案由以下步骤的递归应用组成。对于 j = 1,...,N：

- 1. 从其预测分布 $p(\lambda_{t+1}|\lambda_{1:t}^{(j)},\mathrm{KF}_t^{(j)},y_{t+1})$ 生成 $\lambda_{t+1}^{(j)}$；
- 2. 在条件 {$\mathrm{KF}_t^{(j)}$, $z_{t+1}$, $\lambda_{t+1}^{(j)}$} 下通过一步卡尔曼滤波器获得 $\mathrm{KF}_{t+1}^{(j)}$，
  $P_{t+1}=H_{\lambda_{t+1}}\Sigma_t H'_{\lambda_{t+1}}+W_{\lambda_{t+1}}W'_{\lambda_{t+1}}$
  $S_{t+1}=GP_{t+1}G'+VV'$, 
  $\mu_{t+1}=H_{\lambda_{t+1}}\mu_t+P_{t+1}G'S_{t+1}^{-1}(z_{t+1}-GH_{\lambda_{t+1}}\mu_t-Dg_{t+1})$
  $\Sigma_{t+1}=P_{t+1}-P_{t+1}G'S_{t+1}^{-1}GP_{t+1}$；并且
- 3. 将新权重更新为 $w_{t+1}^{(j)}=w_t^{(j)}\times u_{t+1}^{(j)}$，其中
  $u_{t+1}^{(j)}=\frac{p(\lambda_{1:t}^{(j)},\lambda_{t+1}^{(j)}|y_{1:t+1})}{p(\lambda_{1:t}^{(j)}|y_{1:t})p(\lambda_{t+1}^{(j)}|\lambda_{1:t}^{(j)},\mathrm{KF}_t^{(j)},y_{t+1})}\propto p(y_{t+1}|\mathrm{KF}_t^{(j)})$
  $=\sum_{i\in I}p(y_{t+1}|\Lambda_{t+1}=i,\mathrm{KF}_t^{(j)})p(\Lambda_{t+1}=i|\lambda_{1:t}^{(j)})$, 
- 4. （重采样- rejuvenation）如果 $w_{t+1}$ 的方差系数超过阈值，则以概率与权重 $w_{t+1}^{(j)}$ 成比例地从 {$\mathrm{KF}_t^{(1)},...,\mathrm{KF}_t^{(m)}$} 中重采样一组新的 $\mathrm{KF}_{t+1}$。

其中 $I$ 是 $\Lambda_t$ 的可能取值集合。具体而言，MKF 更新步骤 3 可按以下步骤实现：

- (3.1) 对于每个 $\Lambda_{t+1}=i$, $i\in I$，运行卡尔曼滤波器得到 $v_i^{(j)}\propto p(y_{t+1}|\Lambda_{t+1}=i,\mathrm{KF}_t^{(j)})p(\Lambda_{t+1}=i|\lambda_{1:t}^{(j)})$，其中 $p(\Lambda_{t+1}=i|\lambda_{1:t}^{(j)})$ 是指示变量的先验转移概率，而 $p(y_{t+1}|\Lambda_{t+1}=i,KF_t^{(j)})$ 是卡尔曼滤波器的副产物 $p(y_{t+1}|y_{1:t},\lambda_{1:t},\lambda_{t+1})\sim N(GH_{\lambda_{t+1}}\mu_t+Dg_{t+1},S_{t+1})$；
- (3.2) 以与 $v_i^{(j)}$ 成比例的概率从集合 $I$ 中采样一个 $\lambda_{t+1}^{(j)}$；
- (3.3) 令 $\mathrm{KF}_{t+1}^{(j)}$ 为具有 $\Lambda_{t+1}=\lambda_{t+1}^{(j)}$ 的那个；并且
- (3.4) 新权重为 $w_{t+1}^{(j)}=w_t^{(j)}\sum_{i\in I}v_i^{(j)}$。

在给定所有参数以及可观测输入和输出变量的时间序列的情况下，具有机制转换的状态空间模型的对数似然可通过运行 MKF 获得。它有如下显式公式，

$\hat{l}(\theta|y_{1:T})=\log\left(\sum_{j=1}^{m}w_T^{(j)}\right)$, 

其中 $\theta$ 是包含所有参数的向量。因此，我们可以通过最大化对数似然函数的以下无偏估计来估计 $\theta$。

## 64.5.3 应用

目前仅有一项资产定价研究在估计具有机制转换的状态空间模型时应用了 MKF。Chang, Chen, Wang 和 Wu (2018) 使用 MKF 来检测股票价格中周期性崩溃的理性泡沫。他们将股票-股息-泡沫系统表达为具有马尔可夫转换的对数线性化高斯状态空间模型。双机制设定包括存续和崩溃机制，其中泡沫以大于或小于资产要求的回报率的速度增长，同时施加理性泡沫条件。他们应用 MKF 策略对模拟观测值和真实美国股票市场指数估计模型。该方法可以更好地拟合泡沫过程并识别历史上大多数泡沫崩溃事件。他们还讨论了三机制设定的可行性和优越性。

## 64.6 结论

在本章中，我们提供了滤波方法在估计资产定价模型中应用的简要总结。我们回顾了四种类型状态空间模型的滤波方法，包括线性高斯状态空间模型、非线性高斯状态空间模型、非线性非高斯状态空间模型以及具有机制转换的状态空间模型。这些模型涵盖了从离散到连续、从结构到非结构的大多数资产定价模型。这些方法可以帮助金融研究人员估计丰富的一系列资产定价模型。

## 参考文献

Bardgett, C., Gourier, E. and Leippold, M. (2018). 推断来自标准普尔500和VIX市场的波动率动态和风险溢价. Journal of Financial Economics, forthcoming.
Bakshi, G., Carr, P. and Wu, L. (2008). 随机风险溢价、货币期权中的随机偏斜以及国际经济中的随机贴现因子. Journal of Financial Economics, 87(1), 132–156.
Carr, P. and Wu, L. (2007). 货币期权中的随机偏斜. Journal of Financial Economics, 86, 213-247.
Carr, P. and Wu, L. (2010). 股票期权与信用违约互换：估值与估计的联合框架. Journal of Financial Econometrics, 8(4), 409-449.
Carr, P. and Wu, L. (2017). 杠杆效应、波动率反馈与自激市场扰动. Journal of Financial and Quantitative Analysis, 52(5), 2119-2156.
Chang, H. and Dong, X. S. (2018). 国债期限溢价的信息含量. Working Paper.
Chang, H., Chen, R., Wang, L. and Wu, Y. (2018). 利用混合卡尔曼滤波器估计周期性崩溃的理性泡沫. Working Paper.
Chen, R. and Liu, J. S. (2000). 混合卡尔曼滤波器. Journal of the Royal Statistical Society, 62(3), 493-508.
Creal, D. (2012). 经济学和金融学中序贯蒙特卡洛方法的综述. Econometric Reviews, 31(3), 245-296.
Christoffersen, P., Dorion, C., Jacobs, K. and Karoui, L. (2014). 仿射期限结构模型中的非线性卡尔曼滤波. Management Science, 60(9), 2248-2268.
D'Amico, S., Kim, D. H. and Wei, M. (2018). 来自TIPS的提示：国债通胀保护证券价格的信息含量. Journal of Financial and Quantitative Analysis, 53(1), 395-436.
Froot, K. and Obstfeld M. (1991). 内生泡沫：股票价格的案例. American Economic Review, 81(5), 1189-1214.
Julier, S. J. (2000). 球面单纯形无迹变换. Proc. IEEE Amer. Control Conf, 3, 2430-2434.
Julier, S. J. and Uhlmann, J. K. (2004). 无迹滤波与非线性估计. IEEE Rev. 92, 401-422.
Kalman, R. E. (1960). 线性滤波与预测问题的全新方法. Journal of Basic Engineering, 82, 35.
Li, J. and Zinna, G. (2018). 方差风险溢价：构成、期限结构与股票回报可预测性. Journal of Business and Economic Statistics, 36(3), 411-425.
Li, H. and Zhao, F. (2006). 未跨期随机波动率：利率衍生品对冲的证据. Journal of Finance, 61(1), 341-378.
Liu, J. S. and Chen, R. (1998). 动态系统的序贯蒙特卡洛方法. Journal of the American Statistical Association, 93(443), 1032-1044.
Pitt, M. K. and Shephard, N. (1999). 通过模拟进行滤波：辅助粒子滤波器. Journal of the American Statistical Association, 94(446), 590-599.
Wu, J. C. and Xia, F. D. (2016). 在零下限衡量货币政策的宏观经济影响. Journal of Money, Credit and Banking, 48, 253-291.
Wu, Y. (1995). 外汇市场是否存在理性泡沫？. Journal of International Money and Finance, 14, 27-46.
Wu, Y. (1997). 股票市场的理性泡沫：解释美国股价波动. Economic Inquiry, 35, 309-319.
