
# (a) Adapter cost refinement.

# (b) L1 distance refinement.

# Figure 6: Two refinement algorithms.

In order to satisfy the compute time limit $C^*_{time}$, according to Equation (1c), the parameter $k$ of each convolution must satisfy:

$$k \geq \left\lceil \frac{K}{C^*_{time} \div \left(\left\lceil \frac{H}{h} \right\rceil \times \left\lceil \frac{W}{w} \right\rceil \times \left\lceil \frac{C}{c} \right\rceil \times R \times S \div T^2\right)} \right\rceil \quad (9)$$

So we can get the minimum $k$ which satisfies Equations (8) and (9).

In addition, we can rotate a kernel by 90 degree. In this case, the total width of all convolution is $H^*_{limit}$. In order to get similar height of each convolution, the width of them is allocated according to the proportion of:

$$\left\lceil \frac{H}{h} \right\rceil \times \left\lceil \frac{W}{w} \right\rceil \times R \times S \times C \times K \div T^2 \quad (10)$$

According to Equation (1b), parameter $k$ of each convolution is calculated after allocating width. In order to satisfy the memory limit, according to Equation (1d), the parameter $c$ of each convolution must satisfy:

$$c \geq \frac{C \times K/k \times R \times S}{M_{limit} - \frac{W+S}{w} \times \frac{H+R-1}{h} \times \frac{K}{k}} \quad (11)$$

In order to satisfy the compute time limit, according to Equation (1c), the parameter $c$ of each convolution must satisfy:

$$c \geq \left\lceil \frac{C}{C^*_{time} \div \left(\left\lceil \frac{H}{h} \right\rceil \times \left\lceil \frac{W}{w} \right\rceil \times \left\lceil \frac{K}{k} \right\rceil \times R \times S \div T^2\right)} \right\rceil \quad (12)$$

## 3.4 Refinement

After placement generation, we perform two refinement algorithms to reduce adapter cost $C_{adapter}$ and L1 distance $C_{dist}$. Where the adapter cost refinement algorithm adjusts the execution parameters, the L1 distance refinement algorithm does not modify any parameters, but only changes the position of kernels or reorders them.

### 3.4.1 Adapter Cost Refinement

In adapter cost refinement algorithm, the parameters of the kernels will be redetermined to decrease $C_{adapter}$ while the compute time $C_{time}$ is unchanged. A kernel will be picked up and its $h$ and $w$ parameters will be changed to be the same to kernels which are connected to it. Then other parameters will be recalculated to keep compute time and width unchanged. This process changes the selected kernel's height. The legal adjustment area is defined as an area whose width is the kernel's width and height is the row height. As Figure 6(a) shows, the blue kernel is selected and the highlight area is legal adjustment area. If the kernel is still in the legal adjustment area, this change is acceptable. The $h$ and $w$ parameter will be redetermined to be the pair which brings the minimum $C_{adapter}$. All kernels will be tried like this. The process will run several times until there is no improvement.

### 3.4.2 L1 distance Refinement

The L1 distance refinement algorithm picks each row and moves kernels in the row to search better $C_{dist}$. We adapt a window-based local reordering technique similar to FastPlaceDP [8]. A window covering several continuously kernels will move from the beginning to the ending of the row as Figure 6(b) shows. The all possible orders of kernels in the window will be enumerated and the result will be saved if $C_{dist}$ decreases. The size of the window is set to 6 to balance the run time overhead and quality improvement. Besides, the position of some continuously kernels will be reversed as another simple strategy whose window size is much bigger than local reordering. This step will be iterated for many times until there is no improvement.

## 4 EXPERIMENTAL RESULTS

We implement GigaPlacer in C++ and compile it with g++ 5.4.0. Benchmarks [5] are from ISPD 2020 Contest with number of kernels ranges from 16 to 100 as Table 1 shows. All experiments were conducted on a linux machine with a 1.6GHz intel i5-10210U processor and 8-GB memory.

GigaPlacer generates solutions by embedding several strategies in the DP-based algorithm. The experiment shows that the placement generation strategies we design are all effective, and all these strategies appear in the final result. Figure 7 shows the final results of GigaPlacer on test cases E, I, M, and F.

## 5 CONCLUSION

In this paper, we present GigaPlacer to place NN layers on WSE. A minimum compute time is achieved by a binary-search-based framework. Two DP-based algorithms focus on different objectives are integrated to place the kernels. To further reduce inter-kernel communication overhead, we adjust the parameters of connected kernels and try to reorder some kernels. Compared with the first place of the ISPD2020 Contest, GigaPlacer is not only better but also faster. Our future work will be improving the judgment function to automatically optimize the inter-kernel distance, instead of setting limitation of row numbers manually. We also intend to explore more topologies to place the kernels for better performance.

# Table 1: Result Comparison on ISPD2020 Benchmarks

| Case | Kernel Num | w_time | w_dist | w_adapter | C_time ISPD'20 | C_time Ours | C_dist ISPD'20 | C_dist Ours | C_adapter ISPD'20 | C_adapter Ours | C_total ISPD'20 | C_total Ours | Runtime(s) ISPD'20 | Runtime(s) Ours |
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

# Figure 6: Two refinement algorithms.

# Figure 7: Results of GigaPlacer on some ISPD2020 cases.

![](img/9193339587477a25149234f19dc04369_5_0.png)

![](img/9193339587477a25149234f19dc04369_5_1.png)

![](img/9193339587477a25149234f19dc04369_5_2.png)

![](img/9193339587477a25149234f19dc04369_5_3.png)

# Figure 8: Results on case D with/without L1 distance refinement

![](img/9193339587477a25149234f19dc04369_5_4.png)

![](img/9193339587477a25149234f19dc04369_5_5.png)

# REFERENCES

- [1] Cerebras. 2019. Wafer-Scale Deep Learning. In IEEE Hot Chips Symposium. 1–31.
- [2] Yun-Chih Chang, Yao-Wen Chang, Guang-Ming Wu, and Shu-Wei Wu. 2000. B*-trees: A new representation for non-slicing floorplans. In ACM/IEEE Design Automation Conference (DAC). 458–463.
- [3] Tianshi Chen, Zidong Du, Ninghui Sun, Jia Wang, Chengyong Wu, Yunji Chen, and Olivier Temam. 2014. DianNao: A small-footprint high-throughput accelerator for ubiquitous machine learning. In ACM Conference on Architectural Support for Programming Languages and Operating Systems (ASPLOS). 269–284.
- [4] Pei-Ning Guo, Chung-Kuan Cheng, and Takeshi Yoshimura. 1999. An O-tree representation of non-slicing floorplan and its applications. In ACM/IEEE Design Automation Conference (DAC). 268–273.
- [5] Michael James, Marvin Tom, Patrick Groeneveld, and Vladimir Kibardin. 2020. ISPD 2020 Physical Mapping of Neural Networks on a Wafer-Scale Deep Learning Accelerator. In ACM International Symposium on Physical Design (ISPD). 145–149.
- [6] Norman P Jouppi, Cliff Young, Nishant Patil, David Patterson, Gaurav Agrawal, Raminder Bajwa, Sarah Bates, Suresh Bhatia, Nan Boden, Al Borchers, et al. 2017. In-datacenter performance analysis of a tensor processing unit. In IEEE/ACM International Symposium on Computer Architecture (ISCA). 1–12.
- [7] Azalia Mirhoseini, Anna Goldie, Mustafa Yazgan, Joe Jiang, Ebrahim Songhori, Shen Wang, Young-sik Lee, Eric Johnson, Omkar Pathak, Sungsu Bae, et al. 2020. Chip Placement with Deep Reinforcement Learning. arXiv:2004.10746 (2020).
- [8] Min Pan, Natarajan Viswanathan, and Chris Chu. 2005. An efficient and effective detailed placement algorithm. In IEEE/ACM International Conference on Computer-Aided Design (ICCAD). 48–55.
- [9] Vivienne Sze, Yu-Hsin Chen, Tien-Ju Yang, and Joel S Emer. 2017. Efficient processing of deep neural networks: A tutorial and survey. Proc. IEEE 105, 12 (2017). 2295–2329.
- [10] Martin D.F. Wong and CL Liu. 1986. A new algorithm for floorplan design. In ACM/IEEE Design Automation Conference (DAC). 101–107.
