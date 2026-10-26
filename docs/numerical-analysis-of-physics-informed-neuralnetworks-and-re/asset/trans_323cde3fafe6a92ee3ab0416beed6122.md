

![](img/1feac31c3be82ff11343dd49645de758_55_0.png)

![](img/1feac31c3be82ff11343dd49645de758_55_1.png)

**图6.1.** 对于ν = 0.01的Navier–Stokes方程的实验结果。总误差\(\mathcal{E}\)和训练误差\(\mathcal{E}_T\)相对于残差点数量\(N_{\mathrm{int}}\)显示（a），并与定理6.5）的界限进行比较，同时也彼此比较（b）。经IMA许可，转载自De Ryck等人（2024a）。

存在与\(d\)无关的常数\(C, \alpha > 0\)，使得

\[
\mathbb{E}[\mathcal{E}(\theta^*(S))^2] \le C d^\alpha \left( \mathbb{E}[\mathcal{E}_T(\theta^*(S), S)] + \frac{\ln(N_{\mathrm{int}})}{N_{\mathrm{int}}^2} + \frac{\ln(N_t)}{N_t^2} + \frac{\ln(N_s)}{N_s^4} \right). \tag{6.10}
\]

关于线性Kolmogorov方程的一个更一般的结果，包括\(C\)和\(\alpha\)的更详细表达式，可以在De Ryck和Mishra（2022a）中找到。与Navier–Stokes方程的相应结果（定理6.5）进行比较可以揭示以下内容。

- 正如Navier–Stokes方程一样，当训练集足够大时，总误差与训练误差的平方根成比例，\(\mathcal{E}(\theta) \sim \sqrt{\mathcal{E}_T(\theta, S)}\)。
- 对于Navier–Stokes方程（其中\(d = 2\)或\(d = 3\)），我们发现需要选择\(N_{\mathrm{int}} \gg N_s \gg N_t\)。然而，在这种情况下，我们发现内部所需的训练点要少得多，因为\(N_s \gg N_t \approx N_{\mathrm{int}}\)就足够了。

作为第一个例子，Mishra和Molinaro（2022）考虑了区域\([-1, 1]\)上的一维热方程，初始条件为\(\sin(\pi x)\)，最终时间\(T = 1\)。结果见图6.2。可以看到，泛化误差和训练误差都随着求积点数量的增加而减小。特别是，也（近似）观察到了关系\(\mathcal{E}(\theta) \sim \sqrt{\mathcal{E}_T(\theta, S)}\)。

![](img/1feac31c3be82ff11343dd49645de758_56_0.png)

![](img/1feac31c3be82ff11343dd49645de758_56_1.png)

**图6.2.** 热方程的实验结果。泛化误差\(\mathcal{E}_G\)和训练误差\(\mathcal{E}_T\)相对于残差点数量\(N_{\mathrm{int}}\)显示（a），并与定理6.7）的界限进行比较，同时也彼此比较（b）。图来自Molinaro（2023）。

作为第二个例子，我们考虑具有参数化初始条件的一维热方程，其中参数空间是非常高维的。更详细地说，所考虑的初始条件由\(\mu\)参数化，并由下式给出

\[
u_0(x; \mu) = \sum_{i=1}^{d} \frac{-1}{d i^2} \sin(i\pi(x - \mu_i)). \tag{6.11}
\]

![](img/1feac31c3be82ff11343dd49645de758_56_2.png)

**图6.3.** 对于具有参数化初始条件的热方程，相对泛化百分比误差\(\mathcal{E}_G\)与参数维度\(d\)的关系。图来自Molinaro（2023）。

图6.3表明，泛化误差\(\mathcal{E}_G\)不会随参数维度\(d\)呈指数增长（而是呈亚二次增长），因此维数灾难得到了缓解。即使对于非常大的\(d\)，相对泛化误差也小于2%。

### 例6.8（标量守恒律）。

我们再次考虑标量守恒律的弱PINN。回顾稳定性结果（定理5.8），泛化误差由下式给出

\[
\mathcal{E}(\theta,\varphi,c) = -\int_0^1\int_0^T\big(|u_{\theta^*(\mathcal{S})}(x,t)-c|\partial_t\varphi(x,t)+Q[u_{\theta^*(\mathcal{S})}(x,t);c]\partial_x\varphi(x,t)\big)\,dx\,dt + \int_0^1|u_\theta(x,0)-u(x,0)|\,dx + \int_0^T|u_\theta(0,t)-u_\theta(1,t)|\,dt. \tag{6.12}
\]

为此，我们考虑随机（蒙特卡洛）求积的最简单情况，并生成一组配置点

\[
\mathcal{S} = \{(x_i,t_i)\}_{i=1}^N \subset D \times [0,T],
\]

其中所有\((x_i,t_i)\)都是从\(D\times[0,T]\)上的均匀分布中独立同分布抽取的。对于固定的\(\theta\in\Theta\)，\(\varphi\in\Phi_\epsilon\)，\(c\in\mathcal{C}\)以及该数据集\(\mathcal{S}\)，我们可以定义训练误差

\[
\mathcal{E}_T(\theta,\mathcal{S},\varphi,c)= -\frac{T}{N}\sum_{i=1}^N\big(|u_\theta(x_i,t_i)-c|\partial_t\varphi(x_i,t_i)+Q[u_\theta(x_i,t_i);c]\partial_x\varphi(x_i,t_i)\big) + \frac{T}{N}\sum_{i=1}^N|u_\theta(x_i,0)-u(x_i,0)| + \frac{T}{N}\sum_{i=1}^N|u_\theta(0,t_i)-u_\theta(1,t_i)|. \tag{6.13}
\]

在训练过程中，我们旨在获得神经网络参数\(\theta^*_{\mathcal{S}}\)、测试函数\(\varphi^*_{\mathcal{S}}\)和标量\(c^*_{\mathcal{S}}\)，使得

\[
\mathcal{E}_T(\theta^*_{\mathcal{S}},\mathcal{S},\varphi^*_{\mathcal{S}},c^*_{\mathcal{S}})\approx\min_{\theta\in\Theta}\max_{\varphi\in\Phi_\epsilon}\max_{c\in\mathcal{C}}\mathcal{E}_T(\theta,\mathcal{S},\varphi,c) \tag{6.14}
\]

对于某个\(\epsilon>0\)。我们将得到的神经网络\(u^*:=u_{\theta^*_{\mathcal{S}}}\)称为弱PINN（wPINN）。如果网络宽度为\(W\)，深度为\(L\)，其权重以\(R\)为界，且参数\(\epsilon>0\)如定理5.10中所述，那么我们得到以下定理（De Ryck等人 2024c，定理3.9和推论3.10）。

**定理6.9.** 设\(\mathcal{C}\)为\(u\)的本质值域，设\(N,L,W\in\mathbb{N}\)，\(R\ge\max\{1,T,|\mathcal{C}|\}\)，其中\(L\ge2\)且\(N\ge3\)。此外，设\(u_\theta:D\times[0,T]\to\mathbb{R}\)，\(\theta\in\Theta\)，为tanh神经网络，其隐藏层至多\(L-1\)层，宽度至多\(W\)，权重和偏置以\(R\)为界。假设\(\mathcal{E}_G\)和\(\mathcal{E}_T\)以\(B\ge1\)为界。则以至少\(1-\delta\)的概率成立

\[
\mathcal{E}_G(\theta^*_{\mathcal{S}},\varphi^*_{\mathcal{S}},c^*_{\mathcal{S}})\le\mathcal{E}_T(\theta^*_{\mathcal{S}},\mathcal{S},\varphi^*_{\mathcal{S}},c^*_{\mathcal{S}})+\frac{3BLW}{\sqrt{N}}\sqrt{\ln\left(\frac{C\ln(1/\epsilon)WRN}{\epsilon^3\delta B}\right)}. \tag{6.15}
\]

## 7. 训练

尽管在前几节中对我们前三个问题（Q1–Q3）的回答总体上是肯定的，但物理信息机器学习中已经发现了重大问题。可以说，最首要的问题在于使用（变体的）梯度下降方法来*训练*这些框架。越来越多的观察表明，PINN及其变体即使在某些模型问题上也*训练缓慢，甚至不可行*，训练过程要么不收敛，要么收敛到不可接受的大损失值（Krishnapriyan *et al.* 2021, Moseley, Markham and Nissen-Meyer 2023, Wang, Teng and Perdikaris 2021a, Wang, Yu and Perdikaris 2022b）。这些观察凸显了我们的第四个问题的相关性。

### 问题4（Q4）

能否使训练误差\(\mathcal{E}_T^*\)足够接近损失函数\(\min_\theta \mathcal{J}(\theta, \mathcal{S})\)的真正最小值？

为了回答这个问题，我们必须找出训练物理信息机器学习算法时观察到的问题背后的原因。经验研究如Krishnapriyan *et al.*（2021）将失败模式归因于非凸的损失景观，与监督学习的损失景观相比，它要复杂得多。其他人如Moseley *et al.*（2023）和Dolean、Heinlein、Mishra和Moseley（2023）则暗示神经网络的众所周知的谱偏差（Rahaman *et al.* 2019）是训练不佳的一个原因，而Wang *et al.*（2021a）和Wang、Wang和Perdikaris（2021b）利用无限宽NTK理论提出，损失函数中PDE残差与监督组件之间的微妙平衡可以解释并可能改善训练问题。尽管如此，可以公平地说，在物理信息机器学习的背景下，对梯度下降算法的训练过程仍然缺乏原则性的分析。

接下来，我们首先证明，当问题4有肯定回答（或假设如此）时，就有可能对通过最小化物理信息损失函数学习到的模型的误差提供*先验误差估计*（第7.1节）。其次，我们推导出物理信息损失函数的梯度下降可以被*简化梯度下降*算法逼近的精确条件，这相当于训练动力学的*线性化*形式的梯度下降更新（第7.2节）。然后我们会发现，梯度下降的收敛速度与一个算子的*条件数*有关，而该算子又由底层PDE的微分算子（\(\mathcal{L}\)）的*厄米平方*（\(\mathcal{L}^* \mathcal{L}\)）和与底层模型的切线核相关联的*核积分算子*组成（第7.3节）。这一分析自然表明，*预处理*所得到的算子对于缓解物理信息机器学习的训练问题是必要的（第7.4节）。最后，在第7.5节中，我们讨论了不同的预处理策略如何克服训练瓶颈，以及现有技术（在……中提出的）如何

