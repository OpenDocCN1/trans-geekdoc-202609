
# (a) 适配器成本细化。

# (b) L1 距离细化。

# 图 6：两种细化算法。

为了满足计算时间限制 $C^*_{time}$，根据公式 (1c)，每个卷积的参数 $k$ 必须满足：

$$k \geq \left\lceil \frac{K}{C^*_{time} \div \left(\left\lceil \frac{H}{h} \right\rceil \times \left\lceil \frac{W}{w} \right\rceil \times \left\lceil \frac{C}{c} \right\rceil \times R \times S \div T^2\right)} \right\rceil \quad (9)$$

因此我们可以得到满足公式 (8) 和 (9) 的最小 $k$。

此外，我们可以将核旋转 90 度。在这种情况下，所有卷积的总宽度为 $H^*_{limit}$。为了使每个卷积的高度相似，其宽度按以下比例分配：

$$\left\lceil \frac{H}{h} \right\rceil \times \left\lceil \frac{W}{w} \right\rceil \times R \times S \times C \times K \div T^2 \quad (10)$$

根据公式 (1b)，在分配宽度后计算每个卷积的参数 $k$。为了满足内存限制，根据公式 (1d)，每个卷积的参数 $c$ 必须满足：

$$c \geq \frac{C \times K/k \times R \times S}{M_{limit} - \frac{W+S}{w} \times \frac{H+R-1}{h} \times \frac{K}{k}} \quad (11)$$

为了满足计算时间限制，根据公式 (1c)，每个卷积的参数 $c$ 必须满足：

$$c \geq \left\lceil \frac{C}{C^*_{time} \div \left(\left\lceil \frac{H}{h} \right\rceil \times \left\lceil \frac{W}{w} \right\rceil \times \left\lceil \frac{K}{k} \right\rceil \times R \times S \div T^2\right)} \right\rceil \quad (12)$$

## 3.4 细化

在布局生成后，我们执行两种细化算法以降低适配器成本 $C_{adapter}$ 和 L1 距离 $C_{dist}$。其中适配器成本细化算法调整执行参数，L1 距离细化算法不修改任何参数，仅改变核的位置或重新排序它们。

### 3.4.1 适配器成本细化

在适配器成本细化算法中，核的参数将被重新确定以降低 $C_{adapter}$，同时计算时间 $C_{time}$ 保持不变。会挑选一个核，并将其 $h$ 和 $w$ 参数更改为与其相连的核相同。然后重新计算其他参数以保持计算时间和宽度不变。此过程会改变所选核的高度。合法调整区域定义为宽度为核的宽度、高度为行高的区域。如图 6(a) 所示，蓝色核被选中，高亮区域为合法调整区域。如果核仍在合法调整区域内，则此更改是可以接受的。$h$ 和 $w$ 参数将被重新确定为使 $C_{adapter}$ 最小的配对。所有核都将以这种方式尝试。该过程将多次运行，直到没有改进为止。

### 3.4.2 L1 距离细化

L1 距离细化算法挑选每一行并移动该行中的核以搜索更好的 $C_{dist}$。我们采用与 FastPlaceDP [8] 类似的基于窗口的局部重排序技术。一个覆盖若干连续核的窗口将从行的开头移动到行尾，如图 6(b) 所示。窗口中核的所有可能顺序将被枚举，如果 $C_{dist}$ 减小则保存结果。窗口大小设置为 6 以平衡运行时间开销和质量提升。此外，一些连续核的位置将被反转，作为另一种简单的策略，其窗口大小远大于局部重排序。此步骤将迭代多次，直到没有改进为止。

## 4 实验结果

我们使用 C++ 实现 GigaPlacer 并使用 g++ 5.4.0 编译。基准测试 [5] 来自 ISPD 2020 竞赛，核的数量范围从 16 到 100，如表 1 所示。所有实验均在配备 1.6GHz Intel i5-10210U 处理器和 8GB 内存的 Linux 机器上进行。

GigaPlacer 通过在基于 DP 的算法中嵌入多种策略来生成解决方案。实验表明，我们设计的布局生成策略都有效，并且所有这些策略都出现在最终结果中。图 7 显示了 GigaPlacer 在测试案例 E、I、M 和 F 上的最终结果。

## 5 结论

在本文中，我们提出了 GigaPlacer 用于在 WSE 上放置 NN 层。通过基于二分搜索的框架实现了最小计算时间。两种关注不同目标的基于 DP 的算法被集成以放置核。为了进一步降低核间通信开销，我们调整了相连核的参数并尝试重新排序一些核。与 ISPD2020 竞赛的第一名相比，GigaPlacer 不仅更好而且更快。我们未来的工作将改进判断函数以自动优化核间距离，而不是手动设置行数限制。我们还打算探索更多拓扑以放置核以获得更好的性能。

# 表 1：ISPD2020 基准测试结果比较

| 案例 | 内核数 | w_time | w_dist | w_adapter | C_time ISPD'20 | C_time 我们 | C_dist ISPD'20 | C_dist 我们 | C_adapter ISPD'20 | C_adapter 我们 | C_total ISPD'20 | C_total 我们 | 运行时间(s) ISPD'20 | 运行时间(s) 我们 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A | 16 | 1 | 1 | 0 | 34496 | 34496 | 1314 | 1189.5 | 15 | 16 | 35810 | 35685.5 | 35 | 3 |
| B | 32 | 1 | 1 | 0 | 63504 | 64512 | 2639.5 | 2004 | 18 | 10 | 66143.5 | 66516 | 37 | 15 |
| C | 100 | 1 | 1 | 0 | 64512 | 64768 | 2408 | 1959.5 | 185 | 249 | 66920 | 66727.5 | 210 | 59 |
| D | 52 | 1 | 1 | 0 | 33712 | 33712 | 2722 | 2084.5 | 123 | 137 | 36434 | 35796.5 | 37 | 22 |
| E | 16 | 1 | 10 | 100 | 39312 | 39312 | 562 | 569.5 | 11 | 8 | 46032 | 45807 | 76 | 5 |
| F | 32 | 1 | 10 | 100 | 65170 | 65170 | 1489.5 | 1488.5 | 12 | 14 | 81265 | 81455 | 116 | 15 |
| G | 100 | 1 | 10 | 100 | 64512 | 71680 | 2508.5 | 1945.5 | 98 | 17 | 99397 | 92835 | 188 | 56 |
| H | 52 | 1 | 10 | 100 | 39520 | 43008 | 1104.5 | 887 | 49 | 12 | 55465 | 53078 | 76 | 20 |
| I | 25 | 1 | 4 | 0 | 52136 | 49392 | 617.5 | 1284.5 | 13 | 10 | 54606 | 54530 | 69 | 10 |
| J | 79 | 1 | 4 | 0 | 50274 | 49392 | 2472.5 | 1988 | 69 | 134 | 60164 | 57344 | 90 | 49 |
| K | 16 | 1 | 4 | 0 | 432 | 504 | 240 | 211.5 | 3 | 7 | 1392 | 1350 | 28 | 1 |
| L | 52 | 1 | 4 | 0 | 864 | 864 | 279 | 283 | 18 | 178 | 1980 | 1996 | 38 | 16 |
| M | 23 | 1 | 4 | 0 | 22111840 | 22111840 | 3610.5 | 3365.5 | 41 | 44 | 2226282 | 22253202 | 68 | 13 |
| N | 26 | 1 | 4 | 0 | 1482 | 1640 | 480.5 | 437.5 | 10 | 9 | 3404 | 3390 | 3 | 1 |
| O | 25 | 1 | 40 | 400 | 52136 | 52136 | 617.5 | 617.5 | 13 | 13 | 82036 | 82036 | 121 | 10 |
| P | 79 | 1 | 40 | 400 | 57792 | 57792 | 1101 | 1625 | 85 | 11 | 135832 | 127192 | 122 | 38 |
| Q | 16 | 1 | 40 | 400 | 882 | 896 | 166 | 153 | 6 | 7 | 9922 | 9816 | 27 | 2 |
| R | 52 | 1 | 40 | 400 | 8064 | 1008 | 259 | 324 | 20 | 27 | 26424 | 24768 | 66 | 10 |
| S | 23 | 1 | 400 | 400 | 2396300 | 2396160 | 1897.5 | 1352 | 48 | 47 | 3174500 | 2955760 | 95 | 13 |
| T | 26 | 1 | 40 | 400 | 4102 | 4875 | 208.5 | 176.5 | 4 | 5 | 14042 | 13935 | 5 | 1 |
| Avg Ratio | | | | | 1.32 | 1 | 1.08 | 1 | 1.65 | 1 | 1.02 | 1 | 7.23 | 1 |

![](img/9193339587477a25149234f19dc04369_4_0.png)

![](img/9193339587477a25149234f19dc04369_4_1.png)

# 图 6：两种细化算法。

# 图 7：GigaPlacer 在部分 ISPD2020 案例上的结果。

![](img/9193339587477a25149234f19dc04369_5_0.png)

![](img/9193339587477a25149234f19dc04369_5_1.png)

![](img/9193339587477a25149234f19dc04369_5_2.png)

![](img/9193339587477a25149234f19dc04369_5_3.png)

# 图 8：案例 D 有/无 L1 距离细化的结果

![](img/9193339587477a25149234f19dc04369_5_4.png)

![](img/9193339587477a25149234f19dc04369_5_5.png)

# 参考文献

- [1] Cerebras. 2019. 晶圆级深度学习. In IEEE Hot Chips Symposium. 1–31.
- [2] Yun-Chih Chang, Yao-Wen Chang, Guang-Ming Wu, and Shu-Wei Wu. 2000. B*-树：非切片平面图的一种新表示. In ACM/IEEE Design Automation Conference (DAC). 458–463.
- [3] Tianshi Chen, Zidong Du, Ninghui Sun, Jia Wang, Chengyong Wu, Yunji Chen, and Olivier Temam. 2014. DianNao：一种用于无处不在机器学习的低占用高吞吐加速器. In ACM Conference on Architectural Support for Programming Languages and Operating Systems (ASPLOS). 269–284.
- [4] Pei-Ning Guo, Chung-Kuan Cheng, and Takeshi Yoshimura. 1999. 非切片平面图的一种 O-树表示及其应用. In ACM/IEEE Design Automation Conference (DAC). 268–273.
- [5] Michael James, Marvin Tom, Patrick Groeneveld, and Vladimir Kibardin. 2020. ISPD 2020 晶圆级深度学习加速器上神经网络的物理映射. In ACM International Symposium on Physical Design (ISPD). 145–149.
- [6] Norman P Jouppi, Cliff Young, Nishant Patil, David Patterson, Gaurav Agrawal, Raminder Bajwa, Sarah Bates, Suresh Bhatia, Nan Boden, Al Borchers, et al. 2017. 张量处理单元的数据中心性能分析. In IEEE/ACM International Symposium on Computer Architecture (ISCA). 1–12.
- [7] Azalia Mirhoseini, Anna Goldie, Mustafa Yazgan, Joe Jiang, Ebrahim Songhori, Shen Wang, Young-sik Lee, Eric Johnson, Omkar Pathak, Sungsu Bae, et al. 2020. 使用深度强化学习的芯片放置. arXiv:2004.10746 (2020).
- [8] Min Pan, Natarajan Viswanathan, and Chris Chu. 2005. 一种高效有效的详细放置算法. In IEEE/ACM International Conference on Computer-Aided Design (ICCAD). 48–55.
- [9] Vivienne Sze, Yu-Hsin Chen, Tien-Ju Yang, and Joel S Emer. 2017. 深度神经网络的高效处理：教程与综述. Proc. IEEE 105, 12 (2017). 2295–2329.
- [10] Martin D.F. Wong and CL Liu. 1986. 一种新的平面图设计算法. In ACM/IEEE Design Automation Conference (DAC). 101–107.

