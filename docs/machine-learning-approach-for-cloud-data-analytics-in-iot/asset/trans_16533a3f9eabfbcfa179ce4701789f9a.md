
任务调度过程如下：云服务器（处理器）性能、将任务选择到云服务器上，以及任务在云服务器上的执行顺序。任务调度分为两个基本部分，即静态[8]和动态调度[9]。

本章重点关注任务调度算法中四种著名的启发式方法，即CPOP、ALAP、HEFT和PETS算法。这些算法作为基准，用于在云计算环境中与任何新提出的算法进行比较。后续章节将通过示例详细阐述这些启发式算法的详细信息。算法的比较分析使用性能指标，如调度长度、加速比、效率、调度长度比、资源利用率和成本。

## 9.2 工作流模型

工作流模型用于表示应用程序，它由有向无环图（DAG）表示，并形式化地定义为 $W_G$ = $(T, E, W)$，其中

- $T$ = ${\mathrm{X}_1, {\mathrm{X}_2, {\mathrm{X}_3},...,{\mathrm{X}_n}\}$ 是固定数量的第 $n$ 个任务。
- $E$ = ${\mathrm{e}_i, \mathrm{e}(\mathrm{X}_i, \mathrm{X}_j)\}$ 是任意两个任务 $\mathrm{X}_i$ 和 $\mathrm{X}_j$ 之间的边。
- $W$ = ${{(X_i, X_j) | X_i, X \in T}\}$ 是两个任务 $\mathrm{X}_i$ 和 $\mathrm{X}_j$ 之间边的数据传输时间。

任务之间的依赖关系必须维持，这被称为优先约束。每个DAG都有一个入口任务和出口任务。给定DAG的入口任务 $X_i$ 定义为 pred($X_i$) = $\Phi$，这意味着 $X_i$ 没有任何父任务。类似地，出口任务 succ($X_i$) = $\Phi$，表示没有任何子任务。一个简单的DAG模型如图9.2所示。

![](img/cbc35e0d02425baa6028b87d56263a7f_217_0.png)

图 9.2 简单DAG模型。

![](img/cbc35e0d02425baa6028b87d56263a7f_218_0.png)

图 9.3 任务与虚拟机的映射。

## 9.3 系统计算模型

该模型由云服务器表示，这些云服务器使用快速网络以全双工模式进行通信。云服务器记为 $S_G = \{C_s\}$，其中 $C_s = \{C_1, C_2, \dots, C_p\}$ 是有限的第 $p$ 个云服务器的集合，每个云服务器 $C_1 = \{\text{VM}_{1,1},\dots,\text{VM}_{1,m}\}$，$C_2 = \{\text{VM}_{2,1},\dots,\text{VM}_{2,m}\}, \dots$，$C_p = \{\text{VM}_{p,1},\dots,\text{VM}_{p,m}\}$ 由一个或多个虚拟机组成。这里，云服务器的虚拟机是异构平台，它们以不同的速度工作。如果两个任务 $T_i$ 和 $T_j$ 在同一 $S_G$ 中通信，则不考虑其通信时间；否则，将予以考虑。

图 9.3 显示了任务到相应云服务器的映射。

## 9.4 调度的主要目标

工作流模型调度的主要目标是减少虚拟机上的总体执行时间。其数学表示如下：

$$Sch_{\text{length}} = \min \{CTT(Exit Task X_{exit}, Virtual Machine M)\}$$

其中 CTT 是任务的完成时间。

## 9.5 调度的任务计算属性

这些属性在将任务分配到虚拟机时起着重要作用，以下详细讨论了七个属性 [26]：

- **预计计算时间 (ECT)** [10, 26, 27]

$$ECT_{ij} = \begin{bmatrix} ECT_{11} & ECT_{12} & \dots & ECT_{1n} \\ ECT_{21} & ECT_{22} & \dots & ECT_{2n} \\ \dots & \dots & \dots & \dots \\ ECT_{m1} & ECT_{m2} & \dots & ECT_{mn} \end{bmatrix}$$

其中 $ECT_{ij}$ 为 $X_i$ 在 VM$_j$ 上的值。

- **平均 ECT (AECT)** [11, 26, 27] 对于任务 $X_i$ 定义为

$$AECT_i = \frac{\sum_{j=1}^{m} ECT_{i,j}}{m}$$

- **关键路径 (CP)** [12, 13, 26, 27] 是从 X$_{entry}$ 到 X$_{exit}$ 的最长链接，如下所示：

$$CP = \max_{path \in DAG} \{length(path)\}$$

$$length(path) = \sum_{Xi \in T} AECT(Xi) + \sum_{e \in E} T_c(X_i, X_j)$$

- **最早开始时间 EST** [14, 26, 27] 如下所示：

$$EST(X_i, VM_j) = \begin{cases} 0 & if \; X_i \in X_{entry} \\ \max_{X_j \in pred(X_i)} \{EFT(X_j, VM_j) + MET(X_i) + T_c(X_i, X_j)\} & otherwise \end{cases}$$

- **最小执行时间 MET** [15, 26, 27] 定义如下：

$$MET(X_i) = min.\{ECT(X_p, VM_m)\}$$

- **最早完成时间 EFT** [15, 26, 27] 定义如下：

$$EFT(X_p, VM_j) = ECT_{ij} + EST(X_p, VM_j)$$

- **静态级别 SL** [13, 15, 26, 27]：可以定义如下：

$$SL(X_i) = AECT(X_i) + \max_{X_j \in Succ(X_i)}\;\{SL(X_j)\}$$

## 9.6 性能指标

启发式算法的比较基于以下性能指标：*调度长度、调度长度比、加速比和效率、资源利用率以及成本*。

- **i. 调度长度** [15]：这是一个重要的比较指标，因为它给出了给定DAG中任务的总体执行时间。形式上，调度长度定义为给定DAG的出口任务在可用虚拟机上所需的最短时间，即：

$$Scheduling Length = Min.\;\{EFT(T_{exit}, VM)\}$$

- **ii. 调度长度比 (SLR)** [15–17]：它是调度长度与给定DAG中关键路径（$CP_{min}$）任务的最小ECT之和的比值，即：

$$SLR = \frac{Scheduling Length of Algorithm}{\sum_{T_j \in CP_{min}} Min(ECT_{i,j})}$$

- **iii. 加速比** [17]：它定义为给定DAG上所有任务在最少时间内运行的虚拟机上ECT之和与调度长度的比值，即：

$$Speedup = \frac{Min.\left[\sum_{j=1}^{m} ECT_{i,j}\right]}{Scheduling Length}$$

其中 $m$ 是虚拟机数量。

- **iv. 效率** [17]：它定义为*加速比*与虚拟机总数量的比值，即：

$$Efficiency = \frac{Speedup}{m} \times 100$$

- **v. 资源利用率** [18]：这是云计算的重要指标，其主要目标是最大化资源利用率。通过平均资源利用率（ARU）进行计算。

$$ARU = \frac{\sum_{i=1}^{m} T(VM_i)}{Scheduling Length \times m} \times 100$$

其中 $T(VM_i)$ 是虚拟机 i 完成给定DAG中所有任务所需的时间。

- **vi. 成本** [19]：该指标由以下公式定义：

$$Cost = \sum E_{ij} \times C(VM_j)$$

其中 $E_{ij}$ 是 $X_i$ 在 $VM_j$ 上的运行时间，$C(VM_j)$ 是 $VM_j$ 每单位时间的成本。

## 9.7 启发式任务调度算法

本节将讨论云计算环境中四种著名的启发式调度算法，如HEFT [20]、CPOP [20]、ALAP [12]和PETS [21]，如图9.4所示。这些启发式算法用作标准算法，以便利用各种性能指标与任何新算法进行比较。所有四种启发式算法都基于任务的优先级属性，并根据其优先级分配到机器上。算法的详细信息将在后续章节中介绍。

![](img/cbc35e0d02425baa6028b87d56263a7f_221_0.png)

### 9.7.1 异构最早完成时间 (HEFT) 算法

HEFT [20] 是异构平台的一种列表调度类型，它具有良好的性能，具有理想的调度长度。它工作在两个不同的阶段，如下所示：

**第一阶段：任务优先级**

任务的顺序（升序或降序）称为任何任务的优先级。HEFT算法使用向上排名方法来计算给定DAG中任务的优先级。该方法也称为b-level（底层）属性。它用 $U^{Rank}$ 表示，并基于任务的平均执行时间和平均通信时间。任务优先级的计算将从出口任务开始，并向上移动到DAG。形式上，它表示为 [20]：

$$U^{Rank}(X_i)=\begin{cases} AET(X_i)+\max_{X_j\in\mathrm{SUC}(X_i)}\left(CT_{i,j}+U^{Rank}(X_j)\right)&\text{if }X_i\neq X_{exit}\\ AET(X_{exit})&\text{if }X_i=X_{exit}\end{cases}$$

其中：

- $X_i$ 是给定DAG中的任务
- $X_{exit}$ 是给定DAG中的最后一个任务
- $CT_{i,j}$ 是任务 $X_i$ 和 $X_j$ 之间的通信时间
- SUC 是 $X_i$ 的有限直接后继集合
- AET 是任务 $X_i$ 的平均执行时间，可以用以下公式表示：

$$AET(X_i)=\frac{\sum_{j=1}^{m} ECT_{i,j}}{m}$$

**一个示例**

本节通过DAG$_1$ [14, 26, 27] 的详细例子（如图9.5所示）和ECT详细阐述了任务优先级阶段

