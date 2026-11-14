
### 35.3.5 确定性策略梯度方法 1152

### 35.3.6 无梯度方法 1153

## 35.4 基于模型的强化学习 1153

### 35.4.1 模型预测控制 (MPC) 1153

### 35.4.2 结合基于模型和无模型方法 1155

### 35.4.3 使用高斯过程的 MBRL 1156

### 35.4.4 使用深度神经网络的 MBRL 1157

### 35.4.5 使用潜变量模型的 MBRL 1158

### 35.4.6 对模型误差的鲁棒性 1160

## 35.5 非策略学习 1160

### 35.5.1 基本技术 1161

### 35.5.2 视界诅咒 1164

### 35.5.3 致命三元组 1165

## 35.6 控制即推断 1167

### 35.6.1 最大熵强化学习 1167

### 35.6.2 其他方法 1169

### 35.6.3 模仿学习 1170

## 36 因果性 1173

### 36.1 引言 1173

### 36.2 因果形式主义 1175

### 36.2.1 结构因果模型 1175

### 36.2.2 因果 DAG 1176

### 36.2.3 识别性 1178

### 36.2.4 反事实与因果层次 1180

### 36.3 随机对照试验 1182

### 36.4 混杂变量调整 1183

### 36.4.1 因果 estimand, 统计 estimand, 和识别性 1183

### 36.4.2 带观测混杂变量的 ATE 估计 1186

### 36.4.3 不确定性量化 1191

### 36.4.4 匹配 1191

### 36.4.5 实际考虑与程序 1192

### 36.4.6 总结与实际建议 1195

### 36.5 工具变量策略 1197

### 36.5.1 加性未观测混杂 1198

### 36.5.2 工具单调性和局部平均处理效应 1200

### 36.5.3 两阶段最小二乘法 1203

### 36.6 双重差分法 1204

### 36.6.1 估计 1207

### 36.7 可信性检验 1208

### 36.7.1 安慰剂检验 1208

### 36.7.2 对未观测混杂的敏感性分析 1209

### 36.8 do-演算 1217

### 36.8.1 三条规则 1217

### 36.8.2 重访后门调整 1218

### 36.8.3 前门调整 1219

### 36.9 建议阅读 1220

## 索引 1223

## 参考文献 1241

## 前言

> 我正在写一本比平时更长的 [书]，因为没有足够的时间写一本短书。
> (布莱斯·帕斯卡，改写。)

这本书是 [Mur22] 的续作，对机器学习（ML）的各种主题进行了更深入的探讨。之前的书籍主要集中在学习形式为 \( f : \mathcal{X} \rightarrow \mathcal{Y} \) 的函数的技术上，其中 \( f \) 是某种非线性模型，例如深度神经网络，\( \mathcal{X} \) 是可能输入的集合（通常 \( \mathcal{X} = \mathbb{R}^D \)），而 \( \mathcal{Y} = \{1, \dots, C\} \) 代表分类问题的标签集合，或 \( \mathcal{Y} = \mathbb{R} \) 代表回归问题。著名人工智能研究员 Judea Pearl 将这种 ML 称为一种"花哨的曲线拟合"（引用自 [Har18]）。

在这本书中，我们扩展了 ML 的范围以涵盖更具挑战性的问题。例如，我们考虑在不同分布下进行训练和测试；我们考虑生成高维输出，例如图像、文本和图，因此输出空间可以说是 \( \mathcal{Y} = \mathbb{R}^{256 \times 256} \)；我们讨论基于潜变量模型发现数据"洞察"的方法；并且我们讨论如何使用概率模型进行因果推断和在不确定性下进行决策。

我们假设读者对 ML 及其他相关数学主题（例如，概率、统计、线性代数、优化）有一定的先行接触。这些背景材料可以在本书的前传 [Mur22] 以及几本其他优秀书籍（例如，[Lin+21b; DFQ20]）中找到。

可在网上找到用于复现几乎所有图表的 Python 代码（主要使用 JAX）。特别是，如果图注写着"由 gauss_plot_2d.ipynb 生成"，则可以在 probml.github.io/notebooks#gauss_plot_2d.ipynb 处找到相应的 Jupyter 笔记本。点击书籍 PDF 版本中的图表链接将带您进入此笔记本列表。点击笔记本链接将在 Google Colab 中打开它，这将让您轻松自行复现该图表，并修改底层源代码以更深入地理解这些方法。(Colab 为您提供免费 GPU 访问权限，这对于某些计算量较大的演示很有用。)

除了在线代码，probml.github.io/supp 还包含一些因篇幅原因从主书中排除的额外补充在线内容。有关本书主题的练习（及解答），请参见 [Gut22]。

## 贡献作者

本书是许多人付出大量努力的结果。我特别要感谢以下撰写或共同撰写各个章节或部分的人：

- Alex Alemi (Google)，与 Murphy 共同撰写了第 5.1 节（KL 散度）。
- Jeff Bilmes (华盛顿大学)，撰写了第 6.9 节（次模块化优化）。
- Peter Chang，与 Murphy 共同撰写了第 8.5.1 节（通用高斯滤波）。
- Marco Cuturi (Apple，工作在 Google 完成)，撰写了第 6.8 节（最优传输）。
- Alexander D'Amour (Google)，与 Veitch 共同撰写了第 36 章（因果性）。
- Finale Doshi-Velez (哈佛大学)，与 Kim 共同撰写了第 33 章（可解释性）。
- Roy Frostig (Google)，撰写了第 6.2 节（自动微分）。
- Justin Gilmer (Google)，撰写了第 19.8 节（对抗样本）。
- Giles Harper-Donnelly，撰写了第 8.2.4 节（信息形式滤波与平滑）。
- Been Kim (Google)，与 Doshi-Velez 共同撰写了第 33 章（可解释性）。
- Durk Kingma (Google)，与 Song 共同撰写了第 24 章（基于能量的模型）。
- Simon Kornblith (Google)，与 Poole 共同撰写了第 32 章（表征学习）。
- Balaji Lakshminarayanan (Google)，与 Papamakarios 共同撰写了第 23 章（归一化流），并与 Mohamed 和 Rosca 共同撰写了第 26 章（生成对抗网络）。
- Lihong Li (Amazon)，工作完成于 Google，与 Murphy 共同撰写了第 34.4 节（上下文盗匪）和第 35 章（强化学习）。
- Xinglong Li (UBC)，撰写了第 15.2.9 节（多元线性回归）、第 29.4.4.1 节（HMMs 的分组 Gibbs 采样）、第 29.8.4.1 节（LDS 的分组 Gibbs 采样）以及补充章节 31.2.3。
- Shakir Mohamed (Deepmind)，与 Lakshminarayanan 和 Rosca 共同撰写了第 26 章（生成对抗网络）。
- George Papamakarios (Deepmind)，与 Lakshminarayanan 共同撰写了第 23 章（归一化流）。
- Zee Patel (IIT Gandhinagar)，与 Murphy 共同撰写了第 34.7 节（主动学习）。
- Ben Poole (Google)，与 Kornblith 共同撰写了第 32 章（表征学习）。
- Mihaela Rosca (Deepmind/UCL)，共同撰写了第 26 章（生成对抗网络）。
- Vinayak Rao (Purdue)，撰写了第 31 章（非参数贝叶斯模型）。
- Yang Song (Stanford)，与 Kingma 共同撰写了第 24 章（基于能量的模型）。
- Victor Veitch (Google/U. Chicago)，与 D'Amour 共同撰写了第 36 章（因果性）。
- Andrew Wilson (NYU)，与 Murphy 共同撰写了第 17 章（贝叶斯神经网络）和第 18 章（高斯过程）。

## 其他贡献者

我也要感谢以下以其他方式提供帮助的人：

- 许多人帮助制作或改进了图表，包括：Aman Atman、Vibhuti Bansal、Shobhit Belwal、Aadesh Desai、Vishal Ghoniyya、Anand Hegde、Ankita Kumari Jain、Madhav Kanda、Aleyna Kara、Rohit Koiwal、Taksh Panchal、Dhruv Patel、Prey Patei、Nitish Sharma、Hetvi Shashtri、Mahmoud Soliman 和 Gautam Vashishtha。特别感谢 Zeel B Patel 和 Karm Patel 在提高图表质量方面所做的重大努力。
- 2021 年 Google 夏季编程计划 (GSOC) 的参与者，包括 Ming Liang Ang、Aleyna Kara、Gerardo Duran-Martin、Srikar Reddy Jilugu、Drishti Patel 以及共同导师 Mahmoud Soliman。
- 2022 年 Google 夏季编程计划 (GSOC) 的参与者，包括 Peter Chang、Giles
