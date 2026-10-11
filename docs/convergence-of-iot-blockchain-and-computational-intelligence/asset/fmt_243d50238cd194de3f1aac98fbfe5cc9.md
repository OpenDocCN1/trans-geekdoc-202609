
## 文献综述表

| 参考文献 | 研究问题 | 方法/贡献 | 局限性 |
| :--- | :--- | :--- | :--- |
| [12] | Vehicle routing problem with multiple drones and trucks | Solves scheduling problems of multiple trucks and drones | Drones perform both pick-up and delivery of parcels that causes less time to prepare food for nearby restaurants |
| [13] | Routing and optimization problem | Used an arc-based approach along with price algorithm to compute average waiting times of drones | Does not consider flight range issue; Does not overcome the problem of road congestion |
| [14] | Vehicle routing and landing problem of drones | Used drones and vehicles instead of robots for delivery of packages | Employs limited number of customers |
| [15] | Drone assignment | Used Poisson distribution and shortest time first scheduling algorithm for assignment of drone requests | No robots are assigned for pick-up process; Makes system complex by using Poisson distribution on random drone requests |
| [16] | Drone range and depot deployment issues | Drones are recharged from recharging stations with battery swapping feature | No real data is used to validate the results; Unable to handle larger number of requests |
| [17] | Delivery times from pick-up to destination | Swarm optimization and time scheduling approach | Multiple swapping batteries lead to complex system design |
| [18] | Delivery criteria using robots and drones at an individual level | Empirical study and analysis | Missed the hybrid last mile delivery approach |
| [19] | Drone landing issues | Machine learning algorithms for landing drones on terraces | Lack of simulation and analysis to validate the proposed design |
| [20] | Drone landing issues | Filter and localization of drones | Lack of simulation and analysis to validate the proposed design |
| [21] | Legal issues related to drones | Empirical and investigative method | No real case study to guarantee the effect of autonomous vehicles in delivery services |
| [22] | Delivery-related issues | Matrix function analysis | No real case study to guarantee the effect of autonomous vehicles in delivery services |
| [23] | Emission criteria across different delivery zones | Swarm optimization algorithm | No standards are inferred because of varying emission levels across different zones |
| [24] | Dimension problem of drones | Schedule delivery and maintenance approach | Consider drones for both pick-up and delivery services |

## 13.3 方法论

据此陈述，城市地区的配送过程是一项繁琐的任务，导致道路交通拥堵。交通系统的性能——促进经济增长的关键因素之一——因低效的配送流程而深受影响。然而，随着新兴技术的出现，即 AGV（机器人）和 AAV（无人机），本章提出了混合配送流程，从而缓解拥堵问题。

### 13.3.1 基于 AGV（机器人）的拟议配送流程

该方法在个体层面使用机器人。机器人系统网络由一组交叉口和链路组成。它表示为 `R (I, L)`，其中 `I` 表示交叉口，`L` 表示连接各节点的链路。

交叉口包含属性 `x` 和 `y`，其中 **`x` 表示取货位置（在此称为餐厅）**，**`y` 表示目的地（在此称为目标位置）**，由客户设定。系统还包含 **车辆 (`V`)** 和 **食品包裹 (`FP`)**，其中车辆代表 **机器人 (`R`)**。该流程如图 13.1 所示。

![FIGURE 13.1 Food delivery process using robots](images/fig13_1.jpg)

**图 13.1** 使用机器人的食品配送流程

### 13.3.2 基于本体论的混合方法拟议配送流程（无人机+机器人）

混合方法克服了在特定目的地投递包裹时的拥堵问题和较高等待时间。混合方法是两个阶段的融合：机器人用于取餐包，无人机用于将餐包投递至目的地。

#### 13.3.2.1 阶段 1

**机器人 (`R`)** 从 **仓库 (`α`)** 出发，前往附近的 **餐厅 (`β`)** 取餐包。采用机器人是为了避免道路拥堵，它们可以侧向行驶，从而给餐厅留出足够的备餐时间。此阶段还使用了一个 **机器人食品请求表 (`RFRT`)**。在此阶段，机器人仅用于从餐厅取货并送回仓库 (`α`)。

#### 13.3.2.2 阶段 2

无人机用于从 **仓库 (`α`)** 取包裹并投递至 **目的地 (`π`)**。原因在于无人机更快的行驶速度，克服了道路网络的拥堵问题，从而以更快的速度和更少的等待时间增强配送流程。它使用 **无人机食品请求表 (`DFRT`)**。整个流程如图 13.2 所示。

![FIGURE 13.2 Food delivery process using hybrid approach](images/fig13_2.jpg)

**图 13.2** 使用混合方法的食品配送流程

混合配送流程的算法如下：

该流程参考图 13.2。

### 13.3.3 混合系统中基于本体论的因素以筛选配送订单

分配无人机完成订单请求后，无人机需要从仓库飞往目的地。配送完成后，可能出现一架无人机接到两个不同目的地订单的情况。在这种情况下，需要筛选位置参数。这产生了以本体论形式创建知识库或存储的需求，该知识库按位置筛选订单。它包括：

知识库可以借助本体论编辑器（如 `PROTÉGÉ`、`HOZO` 等）自动或手动创建。

## 13.4 案例研究与分析

为分析三个系统的性能，选取了 CP, Delhi 地区，因其为高密度人口城市区域，并取其晚高峰时段（下午 6:00 至 7:00）的经纬度数据 [[25]](#chapter13.xhtml#ref13_25)。

仿真模型使用节点，即餐厅 (`β`)、仓库 (`α`) 和目的地 (`π`)。假设使用 “X” 网站识别源位置边界 2 公里范围内的附近餐厅。仓库 (`α`) 位置选在中央德里，因为它标志着枢纽或充电站，无人机和机器人从此出发执行配送任务。仿真值使用 `MATLAB` 和 `Simulink` [[26]](#chapter13.xhtml#ref13_26)–[[28]](#chapter13.xhtml#ref13_28) 记录，并在给定地点进行物理搭建。订单通过在下午 6:00 至 7:00 期间的均匀分布，匹配附近的餐厅节点和目的地节点来生成。针对配送需求和订单频率上升，调查并记录了几种场景。
