
### 适应度评估
为评估每个潜在解的适用性，计算其客观函数值。利用 Equation (2) 确定加载因子。

(2)

```
$$\\begin{array}{l} {\\text{Loaded~Equation=}\\frac{\\text{Total~Processing~Time~of~All~Tasks}}{\\text{Total~Available~Processing~Time}}} \\\\ {d\\mathbf{L}^{\\prime}\\text{e}v\\text{y} \\sim \\text{u} = \\text{t}^{- \\lambda},(1 < \\lambda \\leq 3)} \\\\ \\end{array}$$
```

所有已完成或正在进行的任务的处理时间总和，即 fog 节点上每个任务的总处理时间。整体可用处理时间指 fog 节点内可用的总处理时长，受 CPU 处理能力、可用内存以及其他相关资源限制的影响。

雾节点的利用率因子范围在 0 到 1 之间，0 表示未使用，1 表示已满载。计算 Equation (3) 所示的欧几里得距离时，使用距离公式 (d) 如下：

(3)

```
$$d = \\sqrt{\\left( {x\\_{1} - x\\_{2}} \\right)^{2} + \\left( {y\\_{1} - y\\_{2}} \\right)^{2} + \\left( {z\\_{1} - z\\_{2}} \\right)^{2}}$$
```

其中 (*x*[1], *y*[1], *z*[1]) 与 (*x*[2], *y*[2], *z*[2]) 分别表示两个点的坐标。

首先分别减去这两个位置的相应坐标，对每个差值进行平方，将平方差相加，最后对和开根号。

计算过程为：(*x*[1] – *x*[2])²、(*y*[1] – *y*[2])² 以及 (*z*[1] – *z*[2])² 表示两个位置的 *x*、*y*、*z* 坐标的平方差，通过 Equation (2) 与 3) 可将可用节点和最近节点视为更佳节点。

* **任务排序**：采用三列提案（块、等待、调度列表），代表被拒绝并等待可用节点的请求。
* **巢穴选择**：如果旧候选解的适应度值较低，则用新候选解替换旧巢穴（即候选解）。
* **生成新解**：在三列机制的指导下，选择随机飞行或随机游走来生成新候选解。
* **接受准则**：若新候选解的适应度值高于当前解，则批准该解；否则根据最近与前一解的适应度差异，按特定概率接受。
* **停止准则**：当满足停止要求（如达到一定的迭代次数或适应度值达标）时停止该方法。
* **返回最佳解**：返回在优化过程中发现的最佳候选解，作为优化结果。

在此，为该建议过程创建了流程图，如图 Figure 35.2 所示。

![Figure 35.2 A flowchart of the proposal's steps](img/fig35_2_B.jpg)

Figure 35.2 A flowchart of the proposal's steps

### 评估指标

在雾计算中，延迟是指从过程开始到完成之间经过的时间量。对于许多应用而言，降低延迟是关键目标，因为它会显著影响雾计算系统的整体性能。延迟在 Equation (4) 中计算如下。

(4)

*Latency* *Equation*(*L*) = *P* + *R*

*P* 表示处理时间；*R* 表示网络延迟。

*P* 可通过将处理率 *R*（processing rate）乘以任务的处理时间 *T* 来估计：

(5)

*P* = *R* × *T*

网络延迟可通过加入传输时间 (*T[t]*) 与传播时间 (*T[p]*) 来分析：

(6)

*N* = *T*[*t*] + *T*[*p*]

传输时间可以通过传输速率 (*R[t]*) 与任务大小 (*S*) 的乘积来计算：

(7)

```
$$T\_{t} = \\frac{S}{R\_{t}}$$
```

当传播速度 (*S*) 与距离 (*d*) 相乘时，可得到传播时间。

### 实验评估与研究

本文提出的 CS 方法旨在在小距离内降低延迟和延迟。该策略包括从 Table 35.2 中选择理想参数集。通过此选择，可降低延迟并提升系统效率。实现使用 Python，并在 Visual Studio Code 中进行开发。

Table 35.2 Parameters of the fog environment

| Parameter || Value |
| --- | --- |
| Router || 6 |
| Users’ node || 33 |
| Fog node || 12 |
| Base broker || 3 |

该建议方法通过使用 CS 算法确定每个用户最近的节点并估计节点与用户之间的距离，从而降低了延迟。程序成功识别了在评估期间由基部代理人传递的 4 个用户请求的处理节点。结果表明，采用 CS 方法可显著降低延迟。该方法通过与未使用该方法相比的延迟进行对比，验证了其有效性。表格对比了使用和未使用库库鸟算法时的延迟（微秒）和距离（公里）。

| Latency (µs) with Cuckoo | Latency (µs) without Cuckoo | Distance (km) with Cuckoo | Distance (km) without Cuckoo |
| --- | --- | --- |
| 0.0092 | 0.0284 | 7.0711 | 21.21324 |
| 0.0130 | 0.0748 | 5.02 | 28.0180 |
| 0.0064 | 0.0068 | 1.01 | 1.02 |
| 0.0213 | 0.1086 | 7.0712 | 35.3555 |

Table 35.3 Final outcome

## Conclusion

总之，CS 算法被开发为雾计算中资源分配的高效技术，尤其在缓解延迟相关困难方面表现出色。其成功归功于独特特性：将雾节点与用户之间的距离测量纳入适应性函数，并结合基础代理的队列调度和 3 个建议列表，这些都依赖于加载标准决定节点是否可用。节点选择的精确性显著减少随机性，提升了整体系统性能。延迟是评估资源分配的关键指标，涵盖请求处理的各个阶段，包括接收、调度和响应传输。基于 CS 算法的建议方法在降低延迟和提升系统效能方面展现出显著优势。这些结果凸显了 CS 算法的重要意义及其在雾计算系统优化中的潜在变革作用。未来研究可进一步深入，特别是在物联网（IoT）应用领域，CS 方法在资源分配方面具有重要前景。

## References

* Abd-Ali, R. S., Radhi, S. A., and Rasool, Z. I. (2020). A survey: The role of the internet of things in the development of education. Indonesian J. Elect. Engg. Comp. Sci. 19(1), 215–221. [`doi.org/10.11591/ijeecs.v19.i1.pp215-221`](https://doi.org/10.11591/ijeecs.v19.i1.pp215-221).
* Abd Elaziz, M., Abualigah, L., and Attiya, I. (2021). Advanced optimization technique for scheduling IoT tasks in cloud-fog computing environments. Fut. Gen. Comp. Sys., 124, 142–154.
* Agarwal, M. and Srivastava, G. M. S. (2018). A Cuckoo search algorithm-based task scheduling in cloud computing. Adv. Intel. Sys. Comput., 554, 293–299. [`doi.org/10.1007/978-981-10-3773-3_29`](https://doi.org/10.1007/978-981-10-3773-3_29).
* Alsadie, D. (2022). Resource management strategies in fog computing environment-A comprehensive review. Int. J. Comp. Sci. Netw. Sec., 22(4), 310–328.
* Bhatia, H., Panda, S. N., and Nagpal, D. (2020). Internet of things and its applications in healthcare-A survey. 2020 8th Int. Conf. Reliab. Infocom Technol. Optim. (ICRITO), 305–310. [`doi.org/10.1109/ICRITO48877.2020.9197816`](https://doi.org/10.1109/ICRITO48877.2020.9197816).
* Bittencourt, L. F., Diaz-Montes, J., Buyya, R., Rana, O. F., and Parashar, M. (2017). Mobility-Aware application scheduling in fog computing. IEEE Cloud Comput., 4(2), 26–35. [`doi.org/10.1109/MCC.2017.27`](https://doi.org/10.1109/MCC.2017.27).
* Ghobaei-Arani, M., Souri, A., and Rahmanian, A. A. (2020). Resource management approaches in fog computing: A comprehensive review. J. Grid Comput., 18(1), 1–42.
* Hao, Z., Ed Novak, Yi, S., and Li, Q. (2017). Challenges and software architecture for fog computing. IEEE Int. Comput., 21(2), 44–53. [`doi.org/10.1109/MIC.2017.26`](https://doi.org/10.1109/MIC.2017.26).
* Hong, Cheol-ho, and Varghese, B. (2018). Resource management in fog / edge computing: A survey. J. Supercomput. 75. [`doi.org/10.1007/s13227-018-02763-2`](https://doi.org/10.1007/s13227-018-02763-2).
* Islam, M. S. Ul, Kumar, A., and Hu, Y.-C. (2021). Contextaware scheduling in fog computing: A survey, taxonomy, challenges, and future directions. J. Netw. Comp. Appl., 180, 103008.
* Iyapparaja, M., Naif Khalaf Alshammari, M. Sathish Kumar, S. Krishnan, and Chiranji Lal Chowdhary. (2022). Efficient Resource Allocation in Fog Computing Using QTCS Model. Computers, Materials & Continua. 70(2). DOI:[10.32604/cmc.2022.015707](http://dx.doi.org/10.32604/cmc.2022.015707), 1–15.
* Jamil, B., Ijaz, H., Shojafar, M., Munir, K., and Buyya, R. (2022). Resource allocation and task scheduling in fog computing and internet of everything environments: A taxonomy, review, and future directions. ACM Comput. Sur., 54(11s). [`doi.org/10.1145/3513002`](https://doi.org/10.1145/3513002).
* Jamil, Bushra, Humaira Ijaz, Mohammad Shojafar, Kashif Munir, and Rajkumar Buyya. (2020). Resource allocation and task scheduling in fog computing and internet of everything environments: A taxonomy, review, and future directions. ACM Computing Surveys (CSUR). 54(11s): 1–38.
* Kaur, Mandeep, and Rajni Aron. (2021). A systematic study of load balancing approaches in the fog computing environment. The Journal of supercomputing. 77(8), 9202–9247.
* Khattar, N., Sidhu, J., and Singh, J. (2019). Toward energyefficient cloud computing: A survey of dynamic power management and heuristics-based optimization techniques. J. Supercomput., 75. [`doi.org/10.1007/s11227-019-02764-2`](https://doi.org/10.1007/s11227-019-02764-2).
* Ma, K., Bagula, A., Nyirenda, C., and Ajayi, O. (2019). An Iot-based fog computing model. Sensors (Switzerland), 19(12), 1–17. [`doi.org/10.3390/s19122783`](https://doi.org/10.3390/s19122783).
* Mahmud, Redowan, Kotagiri Ramamohanarao, and Rajkumar Buyya. (2020). Application management in fog computing environments: A taxonomy, review and future directions. ACM Computing Surveys (CSUR). 53(4). 1–43.
* Martinez, I., Hafid, A. S., and Jarray, A. (2021). Design, resource management, and evaluation of fog computing systems: A survey. IEEE Int. Things J., 8(4), 2494–2516. [`doi.org/10.1109/JIOT.2020.3022699`](https://doi.org/10.1109/JIOT.2020.3022699).
* Member, Student, and Luo, J. (2018). Tasks scheduling and resource allocation in fog computing based on containers for smart manufacturing. IEEE Trans. Indus. Informat., 14(10), 4712–4721. [`doi.org/10.1109/TII.2018.2851241`](https://doi.org/10.1109/TII.2018.2851241).
- Moshref, Mahmoud, Rizik Al-Sayyed, and Saleh AlSharaeh. (2022). 改进无线传感器网络的服务质量，采用四个目标的增强路由遗传协议。印尼电气工程与计算机科学期刊。26(2): 1182–1196。
- Nazir, S., Shafiq, S., Iqbal, Z., Zeeshan, M., Tariq, S., and Javaid, N. (2019). 基于云计算和雾计算的智能电网作业调度蚁群优化算法。Adv. Intel. Netw. Collab. Sys. 10th Int. Conf. Intel. Netw. Collab. Sys. (INCoS-2018), 34–46。
