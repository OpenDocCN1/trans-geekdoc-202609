
Using baseline data, specific patterns can be detected based on the time spent within each zone. Using the cleaners’ data as an example, Fig. 4.13 depicts the data collected over the baseline period for a single zone.

The cleaners are assigned specific areas and supported by other cleaners where necessary. Cleaners are also expected to cover an alternate floor when another cleaner falls sick or goes on holiday. As an example, Cleaner 8 is the primary cleaner for the 3<sup>rd</sup> floor. However, other cleaners will provide support where necessary. For example, they might help to collect the refuse once the individual desk bins have been emptied.

Using a point-based anomaly approach, Fig. 4.13 analyses the cleaners’ access data for Zone 1 on the 3<sup>rd</sup> floor (over the baseline period).

The data highlights an interesting pattern: The regular cleaner (Cleaner 8), spends more time in the zone and visits the zone more frequently.

![image](img/fig4.13.jpg)

**Fig. 4.13.**Average daily activity in a single zone.

The non-regular cleaners’ data is clearly grouped, they collectively spend a shorter period of time within the zone under analysis.

This pattern is reflected across the entire floor, showing the primary cleaner spending considerably more time within each zone, whilst the supporting cleaners enter the zones less frequently and for a shorter period. Based on the working practices of the job role this could be considered normal behaviour.

Using the same point-based anomaly approach, a single zone was analysed over a 7-day period. The purpose was to identify normal and abnormal activity.

Figure 4.14 uses a point-based anomaly approach, detailing the time each cleaner spent within a typical zone.

Using the data provided, there is a clear demarcation point between standard and unusual activity.

This data set is typical across all the zones, except when a cleaner was at a hotspot. In that case, the time spent within that area increased.

![image](img/fig4.14.jpg)

**Fig. 4.14.**Typical zone activity.

When determining threat metrics, it is important to understand the thresholds for normal, unusual and anomalous behaviour.

Figure 4.15 references the demarcation point as a percentage of normal operating activity that includes a margin of error based on the data collected. The chart includes a detailed breakdown of user activity within one zone over a 7-day period.

Activity has been correlated into three bands — normal, unusual and abnormal activity. It is evident that the normal time spent within this specific zone by one job role accounts for 95.5% of all activity. It can therefore be assumed that this data group represents normal activity.

The data defines a much smaller grouping that can be identified as unusual behaviour (3.5%). The last recorded data point for this zone was between 7–8 minutes (1.5%) and this has been designated as abnormal.

Data recorded beyond this demarcation point would be considered a potential threat and an alert would be generated.

The snapshot of data detected within Zone 3/1 is typical of other zones within the target organisation. Whilst each zone may have differing time values, which can be dependent on the specific zone or the job role, the percentages stay constant.

![image](img/fig4.15.jpg)

**Fig. 4.15.**Point-based anomaly chart detailing user activity (source: Dakota).

Novikova and Murenin observe that making note of the duration each employee stays in the controlled zone allows one to identify anomalies and potential malicious behaviour (Novikova and Murenin, 2017).

### 4.6.8. Zone metrics

Once the individual leaves a specific floor, their activity can be analysed and appropriate metrics applied through the algorithm. When the individual leaves a controlled zone, it can be detected as the data set will have no corresponding data set on that floor, see Table 4.6.

Figure 4.16 depicts zone data extracted from the proximity solution and confirms the working practices of selected job functions. Using Fig. 4.16 as a reference, it is possible to determine in which floors a cleaner predominately operates.

![image](img/fig4.16.jpg)

**Fig. 4.16.** Average zones visited.

This can provide a baseline metric to highlight significant changes to the work patterns that might indicate unusual behaviour. Determining thresholds can be challenging as it may be necessary to temporarily reassign staff to different floors.

Working on the same metrics used when determining anomalies within zone activity, a similar threshold can be applied when determining significant pattern changes.

Using a single individual as an example, Fig. 4.16 details the average number of zones visited by Cleaner 5. The metrics are taken from the proximity monitoring solution and confirm the floors in which the cleaner is a regular visitor.

-   [数据在为期两个月的期间内收集并处理，用于构建基线；然而，一旦“Shadow Cloud”应用完全部署后，该指标将实时更新。](https://wiki.example.org/feynmans_learning_method)

1.  以[第 2 层](https://chapter4.xhtml#fig4.17)为例（见图 4.17），可以看到 Cleaner 5 的日均区域访问次数为 75 次。使用相同的误差率指标（如前所述用于测量区域活动），当某一天的访问次数≥日均访问次数的 50%时，行为被视为异常。

![image](img/fig4.17.jpg)

**Fig. 4.17.** Cleaner 5 访问的区域。

再次使用相同的方法，当阈值达到≥100%时，行为可被视为异常。如果日区域访问次数≥200%，则会立即触发警报。

### 4.6.9. 模式触发

异常检测过程的最终分析阶段可能被认为是最为复杂的。在开放式办公室中通过运动分析，由于物理控制有限，这可能是一项挑战。

![image](img/fig4.18.jpg)

**Fig. 4.18.** Cleaner 8 通过多个区域的移动模式。

通过 proximity 监测解决方案记录的运动数据，在为期两个月的时间段内进行了分析，以基于工作角色及其他缓解因素（如热点或工作站配置）识别特定模式。

清洁工被用作例子，因为他们提供持续的数据流，可以在基线期间进行分析。Figure 4.18 详细展示了在 proximity 监测解决方案记录的一个小时内的数据提取。移动模式看起来是受控的，遵循可预测的路径。清洁工在预期的入口处进入楼层，并在相邻区域停留，直到运动模式中出现三个尖峰并被识别和标记。将这些区域与楼层图进行交叉参考，可以提供一些澄清，解释运动中略有偏离的原因。这些偏离不代表且可能不表示异常行为。

通过历史模式分析，可以检测到可能影响基线数据的异常。然而，需要容纳细微变化，以降低误报的风险。对于某些角色而言，历史模式分析可能不可行，因为数据因任务的本质而不可用。

例如，管道工可能不定期前往现场，可能仅在发生紧急情况时才出现。他们可能还需要访问建筑物的所有区域以处理漏水。

在实验中，当存在足够数据以构建运动分析的基线模式时，数据被分析以尝试为每个楼层的每个角色识别标准模式。Figure 4.19 展示了三天相同时间的运动情况。可以看出，运动模式过于随机，难以进行准确的模式分析，可能会导致在构建有效的威胁模型时产生过多的误报。这一点在分析清洁工时尤为明显，他们的移动可能紊乱，并且可能有正当理由在开放式办公区域自由移动。

![image](img/fig4.19.jpg)

**Fig. 4.19.** 三个不同日期的模式分析。

然而，当分析其他工作功能的运动时，可以基于历史模式分析构建触发器。例如，空调工程师会在或附近操作每个楼层的气流提取风扇。这些风扇位于办公区的特定位置，因此可以在它们移动到其他没有正当理由的区域时设置触发器。

Figure 4.20 展示了两天内同一個人的跟踪数据。这使得可以可视化运动模式在每天可能完全不同，并说明如何在复杂的运动模式中检测异常。

单个事件可能不足以表明异常行为，并可能导致误报。威胁异常解决方案不仅基于单一方法来检测异常行为，而是依赖于多种因素和过程。每种因素都有可能触发警报或增加风险计数，直到多个事件组合触发警报。Murinien *et al.* (2017) 描述了如何通过分析人类运动轨迹以及在非常规受控区域中的路径异常来检测异常行为。

![image](img/fig4.20.jpg)

**Fig. 4.20.** 包含触发器的移动模式。

### 4.7. The Algorithm

本研究论文的主要目标之一是构建一个强大有效的算法，利用最近部署的 proximity 监测解决方案获取的数据。该算法是 Shadow Cloud 应用的核心部分，该应用是本研究项目创建的。

算法由具有主动功能的元素组成，每个元素都能够发出警报并增加运行的威胁计数器。当承包商进入 Dakota 的受控办公空间时，计数器会重置为“0”（零）。

算法的主要元素如下：

- Entry point（入口点）

- Date（日期）

- Time of day（一天中的时间）

- Time spent in each zone（在每个区域停留的时间）

- Number of zones entered（进入的区域数量）

- Zone pattern anomaly（区域模式异常）

Figure 4.21 展示了该算法的流程图。

### 4.7.1. 验证过程

在 Dakota 的工作实践以及其 3<sup>rd</sup> 方包商完全集成 proximity 解决方案后，启动了验证过程。在设施部门和安保人员的协助下，测试了 Shadow Cloud 应用中的算法，以确定是否存在异常和误报。

在算法的每个阶段配置了触发器，并分析了这些触发器，以确保指标在可接受的误差范围内。

Figure 4.22 展示了算法的每个阶段以及在为期两个月期间各阶段的触发器平均百分比。例如，每位清洁工在每个区域停留的时间在允许范围内的比例为 95%。这可以在 Fig. 4.15 中看到，该图指示正常行为。

算法被设计为容纳一些误报，以提供误差余量。例如，Dakota 的威胁阈值设定为“3”。该阈值基于目标的分析及收集的数据。其他组织的阈值可能更高或更低，这取决于风险偏好、工作功能或建筑物的物理属性。

### 4.7.2. 误报

威胁模型的初始测试阶段产生了一些误报，需要加以解决。对算法每个阶段进行了详细分析，以确保在设计中加入适当的控制措施。

![image](img/fig4.21.jpg)

**Fig. 4.21.** 算法的流程。

![image](img/fig4.22.jpg)

**Fig. 4.22.** 算法触发器。

专注于 8 位清洁工，Fig. 4.22 展示了在为期两个月的基线期间，清洁工在算法的各个阶段触发的触发器百分比。Table 4.6 详细列出了在基线期间每位清洁工激活触发器的具体实例数量。

-   每个 `trigger` 都被调查以确保 `threshold` 值足以在整体 `algorithm` 中防止不必要的 `false positives`。为确保 `experiment` 不会产生 `false working patterns`，`data subjects` 未被直接接触。`Facilities` 和 `security` 受到质询，以确保 `cleaners` 的活动正常。存在两种 `methods` 可用于设置 `threshold` 级别。其中一种可在 `algorithmic` `function` 阶段进行，另一种需要对整体 `threat detection` 级别进行修改。为了提供最大灵活性，每个 `stage` 的 `algorithm` 都被调整，以根据 `false detection` 率给出误差余量。

**Table 4.6.**`False positive` triggers over a two-month baseline period from December 2017 to January 2018.
