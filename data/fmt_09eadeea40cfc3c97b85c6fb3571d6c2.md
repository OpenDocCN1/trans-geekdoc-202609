
总之，我们要强调的是，本书不旨在挑战以往的临床或诊断知识。相反，我们相信，本书描述的工具和算法有可能增强 `EEG` 信号中具有重要临床意义的信息，从而辅助医生，并最终提供更具成本效益和高效的诊断工具。

两位作者衷心感谢我们以前和现在的博士生，他们为本书的内容和我们对该领域的理解做出了巨大贡献。特别感谢 Min Jing、Tracey Lee、Kianoush Nazarpour、Leor Shoker、Loukianous Spyrou 和 Wenwu Wang 提供了部分插图。最后，得益于 Maryam Zahabsaniei、Erfan Sanei 和 Ideen Sanei 的精神支持和鼓励，本书才得以完成。

*Saeid Sanei*

*Jonathon A. Chambers*

*2007 年 1 月*

## 缩略语列表

| 缩略语 | 全称 |
| :--- | :--- |
| 3D | 三维 |
| AASM | 美国睡眠医学学会 |
| ACC | 前扣带回 |
| ACE | 阿登布鲁克认知检查 |
| ACR | 反应准确率 |
| ACT | 自适应啁啾变换 |
| AD | 阿尔茨海默病 |
| ADC | 模数转换器 |
| ADD | 轻度痴呆的 AD 患者 / 注意力缺陷障碍 |
| ADHD | 注意力缺陷多动障碍 |
| AE | 近似熵 / 自编码器 |
| AEP | 听觉诱发电位 |
| AfC | 情感计算 |
| Ag–AgCl | 氯化银-银 |
| AI | 人工智能 |
| AIC | 赤池信息准则 |
| ALE | 自适应线增强器 |
| ALF | 自适应标准化 LORETA/FOCUSS |
| ALM | 增广拉格朗日乘数法 |
| ALS | 交替最小二乘法 / 肌萎缩侧索硬化症 |
| AMDF | 平均幅度差函数 |
| AMI | 平均互信息 |
| AMM | 增广混合矩阵 |
| ANN | 人工神经网络 |
| AOD | 听觉奇异范式 |
| AP | 动作电位 |
| ApEn | 近似熵 |
| APGARCH | 非对称幂 GARCH |
| AR | 自回归建模 |
| ARMA | 自回归滑动平均 |
| ASCOT | 小波系数计数在各阈值上的自适应斜率 |
| ASD | 自闭症谱系障碍 |
| ASDA | 美国睡眠障碍协会 |
| AsI | 对称性指数 |
| ASR | 自动语音识别 |
| ASS | 平均伪迹减除法 |
| AUC | 曲线下面积 |
| BAS | 行为激活系统 |
| BBCI | 柏林 BCI |
| BBI | 脑脑接口 |
| BCG | 弹道心动图 |
| BCI | 脑机接口 |
| BDS | Brock、Dechert 和 Scheinkman 检验 |
| BEM | 边界元法 |
| BF | 波束成形器 |
| BGD | 自助几何差异 |
| BIC | 贝叶斯信息准则 |
| BIS | 行为抑制系统 / 双频谱指数 |
| BMI | 脑机接口 |
| BOLD | 血氧水平依赖 |
| BP | 备动电位 / 双相情感障碍 |
| Brain/MINDS | 疾病研究的综合神经技术脑图谱绘制 |
| BSE | 盲源提取 |
| BSR | 爆发-抑制比 |
| BSS | 盲源分离 |
| bvFTD | 行为变异额颞叶痴呆 |
| Ca | 钙 |
| CAE | 契约自编码器 |
| CANDECOMP | 规范分解 |
| CBD | 皮质基底节变性 |
| CBF | 脑血流 |
| CCA | 典型相关分析 |
| CEEMDAN | 带自适应噪声的全集合 EMD |
| CF | 特征函数 / 认知波动 |
| CFS | 慢性疲劳综合征 |
| Cl | 氯 |
| CDLSA | 耦合字典学习与稀疏近似 |
| CDR | 电流分布源重建 |
| CI | 协方差相交 |
| cICA | 约束独立成分分析 |
| CIT | 隐匿信息测验 |
| CJD | 克雅氏病 |
| CMA | 情感圆环模型 |
| CMTF | 耦合矩阵与张量分解 |
| CMOS | 互补金属氧化物半导体 |
| CNN | 卷积神经网络 |
| CNS | 中枢神经系统 |
| CORCONDIA | 核心一致性诊断 |
| CoSAMP | 压缩采样匹配追踪 |
| CPS | 网络物理系统 |
| CRBPF | 约束劳黑威尔粒子滤波 |
| CSA | 中枢性睡眠呼吸暂停 |
| CSD | 电流源密度 |
| CSF | 脑脊液 |
| CSP | 共同空间模式 |
| CT | 计算机断层扫描 |
| DAE | 去噪自编码器 |
| DARPA | 国防高级研究计划局 |
| DASM | 差分不对称性 |
| DBS | 深部脑刺激 |
| DC | 直流电 |
| DCAU | 差分因果性 |
| DCM | 动态因果建模 |
| DCT | 离散余弦变换 |
| dDTF | 直接定向传递函数 |
| DE | 差分熵 |
| DeconvNet | 反卷积人工神经网络 |
| DFT | 离散傅里叶变换 |
| DFV | 优势频率变异性 |
| DHT | 离散埃尔米特变换 |
| DL | 对角加载 |
| DLE | 数字连接双耳 |
| DM | 默认模式 |
| DMN | 默认模式网络 |
| DNN | 深度神经网络 |
| DPF | 差分光程因子 |
| DSM | 诊断与统计手册 |
| DSTCLN | 深度时空卷积双向长短期记忆网络 |
| DT | 决策树 |
| DTF | 定向传递函数 |
| DTI | 弥散张量成像 |
| DUET | 退化解混估计技术 |
| DWT | 离散小波变换 |
| ECD | 电流偶极子 / 等效电流偶极子 |
| ECG | 心电图 / 心电检查 |
| ECoG | 脑电皮层图 |
| ECT | 电休克疗法 |
| ED | 误差距离 |
| EEG | 脑电图 / 脑电检查 |
| EEMD | 集合经验模态分解 |
| EGARCH | 指数 GARCH |
| EGG | 胃电图 |
| EKG | 心电图 / 心电检查 |
| EM | 期望最大化 |
| EMD | 经验模态分解 |
| EMG | 肌电图 / 肌电检查 |
| ENet | 高效神经网络 |
| EOG | 眼电图 |
| EP | 诱发电位 |
| EPN | 早期后部负波 |
| EPSP | 兴奋性突触后电位 |
| ERBM | 熵率界最小化 |
| ERD | 事件相关去同步化 |
| ERN | 错误相关负波 |
| ERP | 事件相关电位 |
| ERS | 事件相关同步化 |
| FA | 因子分析 |
| FC | 功能连接 |
| FCM | 模糊 *c*‐均值 |
| FD | 分形维数 |
| FDA | 食品药品监督管理局 |
| FDispEn | 基于波动的离散熵 |
| FDR | 假阳性率 |
| FEM | 有限元模型 |
| FFNN | 前馈神经网络 |
| FET | 场效应晶体管 |
| fICA | 快速独立成分分析 |
| FIR | 有限冲激响应 |
| fMRI | 功能性磁共振成像 |
| FMS | 纤维肌痛综合征 |
| FN | 假阴性 |
| fNIRS | 功能性近红外光谱 |
| FO | 卵圆孔 |
| FOBSS | 一阶盲源分离 |
| FOCUSS | 焦点欠定系统求解器 |
| FOOBI | 基于四阶累积量的盲识别 |
| FP | 假阳性 |
| FRDA | 额叶节律性 δ 活动 |
| FRN | 反馈相关负波 |
| FSOR | 正交回归特征选择 |
| FSP | 虚假检测源数量（位置） |
| FTD | 额颞叶痴呆 |
| FuzEn | 模糊熵 |
| GA | 遗传算法 |
| GAD | 广泛性焦虑障碍 |
| GAN | 生成对抗网络 |
| GARCH | 广义自回归条件异方差 |
| GARCH‐M | 均值 GARCH |
| GC | 格兰杰因果性 |
| GCN | 图卷积网络 |
| GFNN | 全局假最近邻 |
| GJR‐GARCH | Glosten, Jagannathan, & Runkle GARCH |
| GLM | 广义线性模型 |
| GMM | 高斯混合模型 |
| GP | 高斯过程 |
| GP‐LR | 高斯过程逻辑回归 |
| GSCCA | 组稀疏典型相关分析 |
| GSR | 皮肤电反应 |
| GWN | 高斯白噪声 |
| HBO/HbO | 氧合血红蛋白 |
| HBR/HbR | 去氧血红蛋白 |
| HBT | 总血红蛋白 |
| HCI | 人机交互 |
| HD | 亨廷顿舞蹈症 |
| HEOG | 水平眼电图 |
| HFD | Higuchi 分形维数 |
| HHT | Hilbert–Huang 变换 |
| HMD | 头戴式显示器 |
| HMM | 隐马尔可夫模型 |
| HOPLS | 高阶偏最小二乘法 |
| HOS | 高阶统计量 |
| HR | 血流动力学反应 |
| HRF | 血流动力学反应函数 |
| HT | Hilbert 变换 |
| IAPS | 国际情感图片系统 |
| IBE | 国际抗癫痫局 |
| IC | 独立成分 |
| ICA | 独立成分分析 |
| iCOH | 相干性虚部 |
| IED | 发作间期癫痫样放电 |
| iEEG | 颅内脑电图 |
| IIR | 无限冲激响应 |
| ILAE | 国际抗癫痫联盟 |
| IMF | 本征模态函数 |
| ImSCoh | S-相干性虚部 |
| INDSCAL | 个体差异标度化 |
| IoB | 脑际网络 |
| IPL | 下顶叶小叶 |
| IPSP | 抑制性突触后电位 |
| IR | 冲激响应 |
| IRLS | 迭代递归最小二乘法 |
| ISODATA | 迭代自组织数据分析技术算法 |
| Isomap | 等度量映射 |
| ISSWT | 逆同步挤压小波变换 |
| ITR | 信息传输率 |
| IVE | 沉浸式虚拟环境 |
| JAD | 联合近似对角化 |
| JADE | 特征矩阵联合近似对角化 |
| jICA | 联合 ICA |
| K | 钾 |
| Kc | 科尔莫哥洛夫复杂度 |
| KDT | 卡罗林斯卡嗜睡测试 |
| KL | Kullback–Leibler |
| KLT | Karhunen–Loéve 变换 |
| KMI | 本体运动意象 |
| KNN | k-近邻 |
| KPCA | 核主成分分析 |
| KSS | 卡罗林斯卡嗜睡量表 |
| KT | Kuhn–Tucker |
| LBD | 路易体痴呆 |
| LCMV | 线性约束最小方差 |
| LD | 线性判别 / 线性分布 |
| LDA | 线性判别分析 / 长 δ 活动 |
| LE | Lyapunov 指数 |
| LEM | 局部脑电模型 |
| LLE | 最大 Lyapunov 指数 |
| LMS | 最小均方 |
| LORETA | 低分辨率电磁断层成像算法 |
| LP | 低通 |
| LPM | 每分钟字母数 |
| LPP | 晚期正电位 |
| LRCN | 长短期循环卷积网络 |
| LRT | 低分辨率断层成像 |
| LS | 最小二乘法 |
| LSE | 最小二乘误差 |
| LSTM | 长短期记忆网络 |
| LVQ | 学习向量量化 |
| LWR | Levinson–Wiggins–Robinson |
| LZC | Lempel–Ziv 复杂度 |
| M2M | 机器对机器 |
| MA | 心算 / 移动平均 |
| MAF | 多元模糊函数 |
| MAP | 最大后验概率 |
| MCI | 轻度认知障碍 |
| MCMC | 马尔可夫链蒙特卡洛 |
| MDI | 多维定向信息 |
| MDP | 移动偶极子 |
| MEG | 磁脑电图 |
| MFDE | 多尺度基于波动的离散熵 |
| mHTT | 突变亨廷顿蛋白 |
| MI | 互信息 |
| MIL | 矩阵求逆引理 |
| ML | 最大似然 |
| MLE | 最大似然估计 / 最大 Lyapunov 指数 |
| MLP | 多层感知机 |
| MMN | 失配负波 |
| MMSE | 最小均方误差 |
| MNI | 蒙特利尔神经学研究所及医院 |
| MNLS | 最小范数最小二乘法 |
| MP | 匹配追踪 |
| MRI | 磁共振成像 |
| MRP | 运动相关电位 |
| MSE | 多系统萎缩 / 均方误差 / 多尺度熵 |
| MS | 多发性硬化 |
| MTLE | 内侧颞叶癫痫 |
| MUSIC | 多通道信号分类 |
| MVAR | 多元自回归 |
| Na | 钠 |
| NC | 正常对照 |
| NCDF | 正态累积分布函数 |
| NCSP |  |
| NDD | 神经发育障碍 |
| NES | 非癫痫性发作 |
| NIH | 美国国家卫生研究院 |
| NIR | 近红外 |
| NIRS | 近红外光谱 |
| NLMS | 归一化最小均方 |
| NMF | 非负矩阵分解 |
| NMCSP | 非参数多类公共空间模式 |
| NMR | 核磁共振 |
| NN | 神经网络 |
| NNQP | 非负二次规划 |
| NP | 神经过程 |
| NREM | 非快速眼动 |
| NSI | 非平稳指数 |
| OA | 眼部伪迹 |
| OBS | 最优基组 / 器质性脑综合征 |
| OFC | 眶额皮层 |
| OMP | 正交匹配追踪 |
| OP | 奇异范式 |
| OSA | 阻塞性睡眠呼吸暂停 |
| OSAHS | 阻塞性睡眠呼吸暂停低通气综合征 |
| PARAFAC | 并行因子分析 |
| PCA | 主成分分析 |
| PCANet | 主成分分析网络 |
| PCC | 皮尔逊积矩相关系数 / 后扣带回皮层 |
| PD | 帕金森病 |
| PDC | 偏导相干 |
| pdf | 概率密度函数 |
| Pe | 错误阳性 |
| PerEn | 排列熵 |
| PET | 正电子发射断层扫描 |
| PF | 粒子滤波 |
| PFC | 前额叶皮层 |
| PIC | 功率迭代聚类 |
| PIF | 相位相互作用函数 |
| PLED | 周期性侧向癫痫样放电 |
| PLI | 相位滞后指数 |
| PLMD | 周期性肢体运动障碍 |
| PLS | 偏最小二乘 |
| PMBR | 运动后β反跳 |
| PMBS | 运动后β同步 |
| PNRD | 非节律性δ活动 |
| POST | 枕区阳性尖锐瞬时波 |
| PPC | 相位-相位耦合 |
| PPG | 光电容积脉搏波描记法 |
| PPM | 分段普罗尼法 |
| PSD | 功率谱密度 |
| PSDM | 相空间非相似性度量 |
| PSG | 多导睡眠图 |
| PSI | 相位斜率指数 |
| PSP | 突触后电位 / 进行性核上性麻痹 |
| PSWC | 周期性尖波复合波 |
| PTSD | 创伤后应激障碍 |
| PWVD | 伪维格纳-维尔分布 |
| QEEG | 定量脑电图 |
| QGARCH | 二次 GARCH |
| QNN | 量子神经网络 |
| QP | 二次规划 |
| R&K | Rechtschtschaffen 和 Kales |
| RAP | 递归应用与投影 |
| RASM | 有理不对称性 |
| RBD | REM 睡眠行为障碍 |
| RBF | 径向基函数 |
| RBPF | Rao-Blackwell 化粒子滤波 |
| RBR | 相对β比率 |
| RCE | 递归通道消除 |
| RE | 区域熵 |
| ReLU | 修正线性单元 |
| REM | 快速眼动 |
| RF | 射频 |
| RFNN | 递归模糊神经网络 |
| RKHS | 再生核希尔伯特空间 |
| RLS | 递归最小二乘 |
| RMBF | 鲁棒最小方差波束成形器 |
| RMS | 均方根 |
| RNN | 循环神经网络 |
| ROC | 受试者工作特征曲线 |
| RP | 备战电位 |
