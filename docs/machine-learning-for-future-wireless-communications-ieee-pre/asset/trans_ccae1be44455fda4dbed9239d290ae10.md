
1. (1) 当热门内容在不同的 `FAN` 中随机缓存时，如何为每个 `UT` 的请求识别最可行的 `FAN` 以最大化网络吞吐量和全局公平性。

2. (2) 在动态无线网络条件和衰落信道特征下，如何为关联的 `FAN`‐`UT` 对有效分配通信带宽以最小化服务时延。

值得注意的是，由于文件放置在内容分发网络的设计中已被广泛研究 Baştug et al. ([2015](#c19.xhtml#c19-bib-0002))，Li et al. ([2015](#c19.xhtml#c19-bib-0025))，Liu et al. ([2017](#c19.xhtml#c19-bib-0026))，本章的重点是 `UT` 与 `FAN` 之间的动态关联，而这很少被研究过。

尽管最常用的 AI 技术，如 `DL` 和深度 `RL`，可能并不最适合立即应用于雾网络中的所有资源管理，是否可以部署 AI 技术来实现部分功能，从而使所有资源管理受益？受此问题以及数据挖掘在学习用户行为方面的最新进展的启发 Kumar and Tomkins ([2010](#c19.xhtml#c19-bib-0021))，Huang et al. ([2016b](#c19.xhtml#c19-bib-0019))，Yang et al. ([2017a](#c19.xhtml#c19-bib-0045))，Zhang et al. ([2014](#c19.xhtml#c19-bib-0054))，Wang et al. ([2015](#c19.xhtml#c19-bib-0043))，本章提出了一种预测调度模型并开发了预测多层操作调度（`PMOS`）算法，其中假设 `FCN` 在有限的未来时间窗口内能够获知用户的未来请求信息。

此外，本章进一步讨论了多层雾计算网络中的成本模型以及由此产生的成本最小化用户调度问题。一般来说，`FCN` 由与 `UT` 签订服务合同的电信运营商运营，而 `FAN` 属于不同个人。为了更好地激励 `FAN` 共享资源，应考虑成本模型，特别是针对 `FAN` 的成本模型。为此，本章提出了一种统一的多层成本模型，包括服务时延和线性反需求动态支付方案。相应地，基于势博弈的成本导向用户调度（`COUS`）算法在本章中有所报道。

本章其余部分组织如下。系统模型在 [第19.2节](#c19.xhtml#c19-sec-0002) 中提出。在雾启用网络架构下，问题在 [第19.3节](#c19.xhtml#c19-sec-0007) 中被表述。在线 `FEMOS` 算法在 [第19.3.1节](#c19.xhtml#c19-sec-0012) 中提出，对应的性能分析在 [第19.3.2节](#c19.xhtml#c19-sec-0017) 中进行。[第19.4节](#c19.xhtml#c19-sec-0021) 在所提出的 `FEMOS` 算法和预测的用户信息的基础上进一步开发了 `PMOS` 算法。此外，[第19.5节](#c19.xhtml#c19-sec-0025) 提出了一种统一的多层成本模型以激励 `FAN` 进行资源共享，并开发了 `COUS` 算法以有效解决由此产生的成本最小化用户调度问题。[第19.6节](#c19.xhtml#c19-sec-0046) 总结了本章。

## 19.2 系统模型

我们考虑一个如图 [图19.1](#c19.xhtml#c19-fig-0001) 所示的雾启用多层异构节点网络，其中包括一个 `FCN` 层、一个 `FAN` 层以及所考虑区域内的一组多个静止或低移动性的 `UT`。每个 `UT` 具有较小的存储容量、较小的通信能力和几乎没有或没有计算能力。`UT` 通过无线链路从 `FAN` 层请求文件下载。由于传输功率受限和动态无线环境，`FAN` 与其邻近 `UT` 之间的通信信道不可靠且时变。`FAN` 层中的每个 `FAN` 配备有限的存储容量、中等的计算能力，但强大的通信能力。它们都缓存了一部分热门文件。通过可靠的回程链路，`FAN` 与 `FCN` 相连，`FCN` 位于云和核心网络旁边，拥有网络的全局信息，并且是文件库的服务器。`FCN` 具有足够的存储容量和强大的计算能力。我们在此强调，在我们的模型中，回程链路传输从 `FCN` 到 `FAN` 的控制信息，并且每个 `FAN` 缓存的文件仅在非高峰时段刷新。为明确起见，如果 `UT` 请求的文件未缓存在 `FAN` 上，则 `FAN` 不会通过回程链路从运营中心获取该文件。在这些条件下，我们可以更清楚地看到 `FAN` 动态分配和资源调度的好处。

记 `FAN` 的集合为 ![images](images/c19-i0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="script">H</mi></mrow></math>，`UT` 的集合为 ![images](images/c19-i0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="script">U</mi></mrow></math>，文件库为 ![images](images/c19-i0003.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="script">F</mi></mrow></math>。每个 `FAN` 所见的大尺度衰落和小尺度衰落系数假定相互独立。我们假设网络以时隙系统运行，索引为 ![images](images/c19-i0004.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>t</mi><mo>&#8712;</mo><mo stretchy="false">&#123;</mo><mn>0</mn><mo>,</mo><mn>1</mn><mo>,</mo><mn>2</mn><mo>,</mo><mi>&#8230;</mi><mo stretchy="false">&#125;</mo></mrow></math>，时隙长度为 ![images](images/c19-i0005.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi mathvariant="script">T</mi></mrow></math>。`FCN` 在每个时隙开始时确定 `UT` 的动态 `FAN` 分配，以无记忆模式优化网络吞吐量，基于网络状态、请求队列长度并忽略所有先前的决策。然后每个 `UT` 请求的文件将由其关联的 `FAN` 通过无线链路传输。当前未服务请求缓冲区的队列长度反过来会影响 `FCN` 在下一个时隙对 `FAN` 分配的决策。然后每个 `FAN` 独立地实施其每时隙调度策略，包括对其关联的 `UT` 的带宽和服务速率分配。符合此设置，被请求的文件 ![images](images/c19-i0006.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><mrow><mi>f</mi></mrow></math> 只能从已缓存它的 `FAN` 下载。如果被请求的文件未缓存在 `UT` 关联的 `FAN` 上，则服务速率为零。

### FAN 分配和文件放置
