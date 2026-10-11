

然而，功耗优化需要精确的功耗模型，这些模型一方面要提供准确的估算，另一方面又能高效计算。为此，CRC 876 贡献了 CoPoMo [[192]](#backmatter-001.xhtml#b_9783110785944-010_ref_192)，这是一种马尔可夫功耗模型，用于计算当前 LTE 和 LTE-A 终端的功耗。该计算考虑了设备特定的消费特性、频谱资源利用率、使用的频率范围、移动性、建筑环境以及数据业务类型。

![Fig. 9.11 Simulation results of the energy consumption (left) and query response time (right) as a function of the number of concurrently replying nodes for different backoff configurations and minimum query response ratio. ©[2018] IEEE. Reprinted, with permission, from [206].](graphic/b_9783110785944-009_fig_011.png)

**图 9.11** 不同退避配置和最小查询响应比下，能量消耗（左）和查询响应时间（右）作为并发回复节点数量函数的仿真结果。©[2018] IEEE. 经许可转载自 [[206]](#backmatter-001.xhtml#b_9783110785944-010_ref_206)。

以下章节介绍 CoPoMo 的基本概念，随后展示用于资源优化的扩展和案例研究。

### 9.2.4.1 感知上下文的功耗建模

本节介绍 CoPoMo 的基本概念 [[192]](#backmatter-001.xhtml#b_9783110785944-010_ref_192)。与所有通信系统一样，UE 的功耗取决于当前的工作状态，而工作状态又受到众多上下文和系统参数的影响。功耗由数字信号处理以及用于接收和发射无线信号的高频（HF）元件的运行引起。由于使用了专用集成电路（ASIC），信号处理的特点是功耗相对较低，仅随有效数据吞吐量微不足道地缩放，因此在许多情况下，正在进行的传输过程中可假设其为常数。HF 接收机的消耗通常也不受接收场强和有效数据吞吐量的影响，因此在接收期间，针对各自的频段也假设为一个常数值 [[191]](#backmatter-001.xhtml#b_9783110785944-010_ref_191)。

UE 的功耗主要由发射功率放大器在上行链路发送消息时的消耗主导，特别是在为克服高路径损耗而需要高发射功率时 [[191]](#backmatter-001.xhtml#b_9783110785944-010_ref_191)。[图 9.12](#9783110785937_093138.xhtml#b_9783110785944-009_fig_012) 显示了智能手机的平均功耗作为发射功率放大器发射功率的函数关系。测量涵盖整个系统，即包括主处理器、显示屏、信号处理和所有有源 HF 元件。后台活动和显示亮度均降至恒定最小值。

可以观察到，在低发射功率下功率略微增加，在高发射功率下功耗陡增。原因是典型地使用了两个工作范围不同的功率放大器，它们根据阈值 `γ` 进行切换以提高效率。由于在各自的工作范围内功耗近似呈线性，CoPoMo 使用两个线性模型进行功率估算，分别由各自的斜率 `α`、y 轴截距 `β` 和切换点 `γ` 组成，这些参数通过针对每个系统和频段的实测系列确定。

![Fig. 9.12 Power consumption of a Samsung Galaxy S5 smartphone at 800 MHz in relation to transmission power. ©[2017] IEEE. Reprinted, with permission, from [208].](graphic/b_9783110785944-009_fig_012.png)

**图 9.12** 三星 Galaxy S5 智能手机在 800 MHz 下的功耗与发射功率的关系。©[2017] IEEE. 经许可转载自 [[208]](#backmatter-001.xhtml#b_9783110785944-010_ref_208)。

![Fig. 9.13 Markovian power state model of LTE User Equipment (UE). ©[2017] IEEE. Reprinted, with permission, from [208].](graphic/b_9783110785944-009_fig_013.png)

**图 9.13** LTE 用户设备（UE）的马尔可夫功率状态模型。©[2017] IEEE. 经许可转载自 [[208]](#backmatter-001.xhtml#b_9783110785944-010_ref_208)。

进一步研究表明，可以使用线性模型的四个参考点 `P̄[1]`、`P̄[2]`、`P̄[3]` 和 `P̄[4]` 准确估算功耗，因此 LTE UE 的功耗可以用由四个相应状态组成的状态模型来描述 [[190]](#backmatter-001.xhtml#b_9783110785944-010_ref_190)。状态模型如[图 9.13](#9783110785937_093138.xhtml#b_9783110785944-009_fig_013)所示。状态 1 表示无外发数据传输时的空闲状态功耗。状态 2 表示低发射功率下的传输（0 dB 处的点），状态 3 表示高发射功率下的传输（`γ` 与最大发射功率之间的中点），状态 4 表示最大发射功率 23 dBm 下的传输。

状态间的转移以转移概率 `λ[i]` 和 `μ[i]` 给出，且总是经过状态 1，因为状态 2、3 和 4 代表具有外发传输的状态，在此期间 UE 保持在当前状态，无法切换到不同的传输相关功率状态。状态转移源自增广的整体模型，如[图 9.14](#9783110785937_093138.xhtml#b_9783110785944-009_fig_014)所示。`λ[i]` 计算为 `λ[i] = λ · ϑ[i]`，其中 `1/λ` 对应外发数据传输的到达率，`ϑ[i]` 满足 `∑_{i=2}^{4} ϑ_i = 1`，指示状态 2、3 和 4 中的驻留时间分布。后者取决于小区环境 `κ`、移动性 `ρ` 和载波频率 `f[c]`，可通过射线追踪分析和路径损耗的统计评估来确定。`μ[i]` 是服务率的倒数，计算公式为 `μ_i = R_i / D`，其中 `D` 为平均文件大小，`R[i]` 为状态 `i` 下达到的平均上行数据速率。数据速率反过来取决于分配的 RB 数量 `M(i)` 和调制编码方案（MCS）`ID(i)`，这些是根据基站的调度策略动态分配的。

![Fig. 9.14 Overview of CoPoMo. ©[2013] IEEE. Reprinted, with permission, from [192].](graphic/b_9783110785944-009_fig_014.png)

**图 9.14** CoPoMo 概览。©[2013] IEEE. 经许可转载自 [[192]](#backmatter-001.xhtml#b_9783110785944-010_ref_192)。

最后，可以从转移概率确定状态概率，进而描述在每个状态中的平均驻留时间。结合特定状态的功耗，即可确定 UE 的平均功耗。

![Fig. 9.15 Uplink power control of UE and its underlying system parameters are typically hidden to the application layers. However, this knowledge is crucial for predictions and estimations of the involved power consumption in energy-aware applications and system-level simulations. The proposed model derives this information from passive connectivity indicators. ©[2018] IEEE. Reprinted, with permission, from [207].](graphic/b_9783110785944-009_fig_015.png)

