

```
lab@ubuntu:~/Desktop$ awk -f e2edelay.awk op20.tr

ReceivedPackets           =  279
Packet Delivery Ratio     =  87.7358%
Dropped Packets ratio = 0
Average End-to-End Delay  =  3.65083 ms
```

图 6.12 20个节点的DSDV端到端延迟。

```
lab@ubuntu:~/Desktop$ ns DSR.tcl
num_nodes is set 20
Creating nodes...
INITIALIZE THE LIST xlistHead
Loading random connection pattern...
Starting Simulation...
channel.cc:sendUp - Calc highestAntennaZ_ and distCST_
highestAntennaZ_ = 1.5,  distCST_ = 550.0
SORTING LISTS ...DONE!
lab@ubuntu:~/Desktop$ awk -f genthroughput.awk op20.tr
Average Throughput[kbps] = 66.66    StartTime=2.56 StopTime=99.89
```

图 6.13 20个节点的DSR吞吐量。

```
lab@ubuntu:~/Desktop$ awk -f e2edelay.awk op20.tr

ReceivedPackets           =  1584
Packet Delivery Ratio     =  79.5181%
Dropped Packets ratio = 0.114458
Average End-to-End Delay  =  5.56286 ms
```

图 6.14 20个节点的DSR端到端延迟。

同样，在无线电环境中以40、60、80、100个节点数、500×500的区域和50的队列长度，观察性能指标以获得结果。

表 6.4 和 6.5 显示了不同路由协议的不同吞吐量和端到端延迟值。

图 6.15 显示，随着节点数量的增加，不同路由协议的吞吐量呈现出不同的变化。观察发现，由于拓扑频繁变化时路由表更新机制较慢，DSDV在所有协议中的吞吐量最低。AODV和DSR等反应式协议具有较高吞吐量。

**表 6.4 不同协议的吞吐量**

| 节点数 | AODV | DSDV | DSR |
|---|---|---|---|
| 20 | 71.48 | 66.66 | 29.27 |
| 40 | 71.43 | 64.47 | 33.43 |
| 60 | 71.25 | 63.31 | 30.84 |
| 80 | 71.77 | 65.39 | 34.26 |
| 100 | 72.04 | 65.14 | 34.67 |

**表 6.5 不同协议的端到端延迟**

| 节点数 | AODV | DSDV | DSR |
|---|---|---|---|
| 20 | 3.247 | 5.562 | 3.650 |
| 40 | 6.868 | 2.982 | 3.582 |
| 60 | 3.245 | 13.659 | 3.959 |
| 80 | 7.885 | 4.019 | 3.814 |
| 100 | 3.228 | 3.246 | 3.948 |

![](img/0b5412a09266b61a5c216084aa99aac2_131_0.png)

图 6.15 不同节点数量下不同路由协议的吞吐量。

图 6.16 显示，随着节点数量的增加，不同路由协议的端到端延迟呈现出不同的变化。观察发现，更高的流量负载会增加延迟。DSR在高流量下产生最高延迟，而AODV在高流量下表现更好。随着节点数量增加，DSDV也会性能下降。

![](img/0b5412a09266b61a5c216084aa99aac2_132_0.png)

图 6.16 不同节点数量下不同路由协议的端到端延迟。

## 6.7 结论

本章介绍了不同的路由算法。基于在ns2模拟器上模拟的性能指标，观察发现，AODV作为一种反应式协议，通过最小化基于需求创建的广播消息数量，相较于DSDV具有某些额外特性。AODV的性能优于DSDV，DSDV基于表驱动方法，每个节点在路由表中维护有关邻居节点的信息；也优于DSR，DSR是一种按需发现路由的协议，即基于特定节点的需求，该节点发起路由发现机制。AODV在数据包之间产生较少的端到端延迟并实现最大吞吐量。路由协议存在多种局限性：随着节点数量增加，网络复杂性增加，链路故障等。因此，使用了不同的优化技术来寻找源点与目的地之间的最短路径。这里，研究了两种优化技术——蚁群算法（ACO）和基于群体智能的优化。ACO技术受到真实蚁群的启发。这用于解决电信领域（如路由）中的搜索问题；这也解决了自组织网络（MANETs）中的路由问题。在网络中，ACO技术在两个节点之间找到了最合适的路径，该路径作为粒子群优化技术的输入。未来，工作可以通过使用不同的概率建模技术进行扩展。

## 参考文献

- 1. Lee, S., & Kim, S. B. (2019). 用于贝叶斯网络结构学习的贪婪算法并行模拟退火。IEEE Transactions on Knowledge and Data Engineering. doi:10.1109/tkde.2019.2899096.

- 2. Mokube, I., & Adams, M. (2007). 蜜罐：概念、方法与挑战。载于第45届东南区域年会论文集。纽约，美国：ACM，第321–326页。

- 3. Bhushan, B., & Sahoo, G. (2017). 无线传感器网络中攻击、技术挑战、漏洞及其对策的最新进展。*Wireless Personal Communications*, 98(2), 2037–2077. doi:10.1007/s11277-017-4962-0.

- 4. Yue, Y., Cao, L., Hang, B., & Luo, Z. (2018). 带有移动汇聚节点的无线传感器网络路由恢复策略的群体智能算法。*IEEE Access*, 6, 67434–67445. doi:10.1109/access.2018.2879364.

- 5. Prashar, D., Kumar, D., & Jyoti, K. (2016, March). 无线传感器网络中安全定位技术的性能分析。载于《第二届信息通信技术竞争性策略国际会议论文集》，第48页。Udaipur: ACM.

- 6. Abo-Zahhad, M., Ahmed, S. M., Sabor, N., & Sasaki, S. (2015). 基于移动汇聚节点的自适应免疫节能聚类协议，用于提高无线传感器网络的生存期和稳定期。*IEEE Sensors Journal*, 15(8), 4576–4586. doi:10.1109/jsen.2015.2424296.

- 7. Kaur, A., & Gujaral, R. (2016). 用于改善网络生存期的WSN优化GAF协议睡眠/唤醒协议。载于《2016年第3届信号处理与集成网络国际会议（SPIN）》。doi:10.1109/spin.2016.7566729.

- 8. Pietro, N. D., & Boutros, J. J. (2017). 构造-a格网的利奇星座。*IEEE Transactions on Communications*, 65(11), 4622–4631. doi:10.1109/tcomm.2017.2736563.

- 9. Jain, V., & Khan, N. A. (2014). 无线传感器网络中定向扩散和SPIN路由协议的仿真分析。载于《2014年商业、工业和政府IT会议（CSIBIG）》。doi:10.1109/csibig.2014.7056990.

- 10. Jaitly, S., Malhotra, H., & Bhushan, B. (2017). 无线传感器网络干扰攻击的安全漏洞及对策：一项调查。载于《2017年计算机、通信与电子国际会议（Comptelix）》。doi:10.1109/comptelix.2017.8004033.

- 11. Sarkar, S., & Datta, R. (2017). 移动自组织网络的移动感知路由选择技术。*IET Wireless Sensor Systems*, 7(3), 55–64. doi:10.1049/iet-wss.2016.0058.

- 12. Pradittasnee, L., Camtepe, S., & Tian, Y. (2017). 大规模传感器网络可靠路由的高效路由更新与维护。*IEEE Transactions on Industrial Informatics*, 13(1), 144–156. doi:10.1109/tii.2016.2569523.

- 13. Kumar, A., & Prashar, D. (2018). 无线传感器网络节点定位的新方法。载于：Singh, R., Choudhury, S., & Gehlot, A.（编）。*智能通信、控制与设备*（第419–428页）。新加坡：Springer.

- 14. Singhal, A., & Daniel, A. (2014). 移动自组织网络的稳定且可扩展的按需路由。载于《2014年商业、工业和政府IT会议（CSIBIG）》。doi:10.1109/csibig.2014.7056989.

- 15. Sahu, P. K., Acharya, B., & Panda, N. (2018). MANET中AODV和DSR路由协议的QoS性能分析。载于《2018年第2届数据科学与商业分析国际会议（ICDSBA）》。doi:10.1109/icdsba.2018.00046.

- 16. Wang, Z., Chen, Y., & Li, C. (2014). PSR：面向移动自组织网络的轻量级主动源路由协议。*IEEE Transactions on Vehicular Technology*, 63(2), 859–868. doi:10.1109/tvt.2013.2279111.

- 17. Abdelbar, A. M., & Salama, K. M. (2019). 用于连续优化的蚁群算法中的参数自适应。*IEEE Access*. doi:10.1109/access.2019.2896104.

- 18. Shang, J., Wang, X., Wu, X., Sun, Y., Ding, Q., & Liu, J. (2019). 基于蚁群优化的基因互作检测方法综述。*IEEE Access*. doi:10.1109/access.2019.2894676.

- 19. Sharma, N., Kaushik, I., Bhushan, B., Gautam, S., & Khampari, A. (2020). 医疗保健领域中WSN和生物识别模型的适用性。载于《无线传感器网络安全增强深度学习策略——信息安全、隐私与伦理进展》，第304–329页。doi:10.4018/978-1-7998-5068-7.ch016.

