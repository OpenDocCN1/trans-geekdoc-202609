

## 152 基于机器学习的多准则决策

Wu Yunna, Yang Meng, Zhang Haobo, Kaifeng, Wang Yang, "基于云模型和PROMETHEE方法的电动汽车充电站最优选址", Energies, 9(3), 157, 2016. https://doi.org/10.3390/en90301571

Xiuxong He, Yingying Yu, "考虑里程焦虑和充电时间的电动汽车最优里程", World Electric Vehicle Journal, 14(1), 21, 2023. https://doi.org/10.3390/wevj14010021

Wu Peng-Sheng, Yi-Chih, "电动汽车充电站选址的混合研究方法", Computers & Industrial Engineering, 70, 195–204, 2014. https://doi.org/10.1016/j.cie.2014.02.001

Wei Weifeng, Jianhua, Wen Fushan, Dong Zoyang, Xu Yuesheng, Xu Yang, Men Ke, "综合配电与电动汽车充电系统的目标协同规划策略", IEEE Transactions on Power Systems, 29(4), 1811–1821, 2014. https://doi.org/10.1109/TPERS.2013.226615

Yingwen Wu, Fu Gaojian, Shao Chao, Jianfeng Guo, "电动汽车普及与局部pm2.5：来自中国的证据", Journal of Cleaner Production, 396, 136508, 2023. https://doi.org/10.1016/j.clepro.2023.136508

Yiao Yue, Yuan Jian-Xin, Liu Hichen, Zhen Lu, "基于区间二元语言信息的扩展VIK方法的群体多准则供应商选择", Expert Systems with Applications, 42(4), 1906–1916, 2015. https://doi.org/10.1016/j.eswa.2014.10.004

Yildirim, B., Kuzu Yildirim, S. "使用模糊VIK方法评估市政服务的市民满意度：2014–2019年期间分析", Decision Making: Applications in Management and Engineering, 5, 50–66, 2022. https://doi.org/10.3181/dame118221001

Zhao Hui-ru, Gao Sen, Fu Liwen, "中国可再生能源补贴成本与效益评述", Renewable and Sustainable Energy Reviews, 37, 538–549, 2014. https://doi.org/10.1016/j.rser.2014.05.061

Zhang Nian, Wei Guishu, "基于犹豫模糊集的决策问题VIK方法的扩展", Applied Mathematical Modelling, 37(7), 4938–4947, 2013. https://doi.org/10.1016/j.apm.2012.10.002

Zou X, Li D. A., "基于GIS的土地整合项目潜力评估的多学科方法：一种模型及其应用", 在第7届WESAI应用计算与计算科学国际会议上. 中国；551–6, 2008.

## 11 直觉性模糊图的最优拓扑指数

J. Senbagamalar 和 V. Gomathi

### 11.1 引言

模糊集给出对象在给定集合中的隶属程度（Zadeh, 1965）。直觉性模糊图（IFG）包含二值逻辑（两个维度），其值介于[0, 1]之间。IFG边值（最小值和最大值）基于顶点。IFG仅表示隶属度和非隶属度。1974年，Rosenfeld执行了基本的理论概念和模糊图运算。K. Y. Atanov在1986年引入了直觉性模糊集（Atansov, 1986），并在1999年引入了区间值直觉模糊集（Atansov, 1999）。模糊图、直觉图和中性图分别引入了一维（仅隶属度）、二维（隶属度和非隶属度）和三维（隶属度、非隶属度和不确定性）的模糊集中心和离心（Bhattacharya）。IFG扩展了模糊图，而中性图扩展了IFG（Szzmidt and Kaczprzyk, 2000）。Akram引入了直觉性模糊图、顶点、循环和直觉性模糊图中的树（Akram and Alsheheri, 2014）。2012年，讨论了直觉性模糊图上的图运算（Akram and Davvaz, 2012），并研究了直觉性模糊图的连通性（Alzoubi and Alhasner, 2021）。一项现实应用涉及使用维纳模糊图的人口贩卖和非法移民（近期 et al., 2019）。2016年，Akram引入了关于直觉模糊图结构的操作的想法（Akram and Akmal, 2018）。在本章中，我们表征了IFG的若干拓扑指数：第一Zagreb、第二Zagreb、遗忘和和谐指数（Javeria Dinar, 2023）。

### 11.2 基础知识

#### 11.2.1 直觉性模糊图

IFG是包含直觉性模糊集的经典模糊图的扩展。模糊图处理边和顶点带有[0,1]区间隶属度的图（Rosenfeld, A.,1975）。直觉性模糊集通过引入第三个参数非隶属度来扩展表示不属于集合的程度。直觉性模糊图同时使用隶属度和非隶属度来模拟边和顶点的不确定性。这使得基于图的不确定性具有更灵活的表示。Nagoi（2016）表征了直觉性模糊图。

**11.2.1.1 定义**
模糊图 $G=(S, \alpha, \mu)$ 是由非空集 $S$ 以及一对函数 $\alpha: S \to [0,1]$ 和 $\mu: S \to [0,1]$ 组成的，对于所有 $x \in S$，有 $\mu(x) \leq \alpha(x)$。

**11.2.1.2 定义**
设 $G=(S, T)$ 为IFG，如果：
(1) $S=\{v_1, v_2, v_3, \dots, v_n\}$，$\alpha_i: S \to [0,1]$, $\mu_i: S \to [0,1]$ 表示元素 $v_i$ 的隶属度和非隶属度，对于每个 $v_i$，有 $0 \leq \alpha_i + \mu_i \leq 1$。
(2) $T \subseteq S \times S$，$\alpha_{ij}(v_i, v_j): S \times S \to [0,1]$, $\mu_{ij}(v_i, v_j): S \times S \to [0,1]$ 使得 $\alpha_{ij}(v_i, v_j) \leq \min[\alpha_i, \alpha_j]$ 且 $\mu_{ij}(v_i, v_j) \geq \max[\mu_i, \mu_j]$ 分别表示边 $(v_p, v_q) \in T$ 的隶属度和非隶属度，对于每个 $(v_p, v_q) \in T$，有 $0 \leq \alpha_{pq} + \mu_{pq} \leq 1$。

**11.2.1.3 定义**
当 $xy \in T$ 且 $\mu(xy) = \min[\mu(x), \mu(y)]$ 以及 $\sigma(xy) = \max[\sigma(x), \sigma(y)]$ 时，称 $G=(S, T)$ 为强IFG。

**11.2.1.4 定义**
当 $xy \in T$ 且 $\mu(xy) = \min[\mu(x), \mu(y)]$ 以及 $\sigma(xy) = \min[\sigma(x), \sigma(y)]$ 时，称 $G=(S, T)$ 为完全图，$C_m(G)$ 定义。

**11.2.1.5 定义**
模糊图中的第一Zagreb指数由 Kalishari 等人（2019）引入：$M(G) = \sum_{i=1}^{n} \sigma(u_i) d_{i}^2$，对于 $u_i \in S$。

**11.2.1.6 定义**
模糊图中的第二Zagreb指数也由 Kalishari 等人（2019）引入：$M^*(G) = \frac{1}{2} \sum_{ij \in T} \sigma(u_i)d_i d_j$，对于 $i \neq j$。

**11.2.1.7 定义**
模糊图中的遗忘指数为 $F(G) = \sum_{i=1}^{n} \sigma(u_i)d_i^2$，对于 $u_i \in S$。

**11.2.1.8 定义**
模糊图中的和谐指数由 Kalishari 等人引入：$H(G) = \frac{1}{2} \sum_{u_i \in T} \frac{1}{\sigma(u_i)d_i + \sigma(v_j)d_j}$，对于 $i \neq j$。

**11.2.1.9 定义**
Kalishari 等人还引入了模糊图的Randić指数：$R(G) = \frac{1}{2} \sqrt{\sum_{i=1}^{n} \sigma(u_i)d_i \cdot \sigma(v_j)d_j}$，对于 $i \neq j$。

### 11.3 直觉拓扑指数

#### 11.3.1 第一Zagreb指数
设 $G=(S,T)$ 为IFG，其中 $S$ 是顶点集，$T$ 是图上的边集。第一Zagreb指数记为 $M(G)$并定义为
$M(G) = \sum_{i=1}^{n} [T_S(u_i) \cdot F_S(u_i)]d_i^2$。

$G=(S,T)$ 的顶点集 $S=\{u_1, u_2, u_3, u_4\}$满足 $(T_S(u_1), F_S(u_1))=(0.3,0.5)$,$(T_S(u_2), F_S(u_2))=(0.2,0.4)$,$(T_S(u_3), F_S(u_3))=(0.1,0.3)$,以及$(T_S(u_4), F_S(u_4))=(0.4,0.6)$。边集包含$(T_F(u_1),F_T(u_1))=(0.2,0.5)$,$(T_F(u_2),F_T(u_2))=(0.1,0.4)$以及$(T_F(u_3),F_T(u_3))=(0.3,0.6)$以及$(T_F(u_4),F_T(u_4))=(0.1,0.6)$。结果如下：

![](img/62c36bee0e5ae6b397770e7de372b0e7_185_0.png)

图 11.1 (a) 一个模糊图；(b) 补补模糊图 G。

