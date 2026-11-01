
# 星系数据与卡尔曼滤波分析

来自 24 个不同星系的数据获得⁵并列于表 [2](#9789815124842-C2.html#t2) 中。距离 `D` 使用 Tully-Fisher 关系测量。退行速度 `V[r]` 使用红移方法测量。⁶

## 表 2 星系数据

| 星系 | `D` (`Mpc`) | `V[r]` (`kmps`) | `D` 的误差 | `V[r]` 的误差 |
|---|---|---|---|---|
| NGC 7814 | 12 | 1050 | 2.881 | 4 |
| NGC 0157 | 16.226 | 1652 | 5.014 | 5 |
| NGC 0578 | 18.282 | 1628 | 4.774 | 3 |
| NGC 0063 | 18.6 | 1160 | 0.164 | 3 |
| NGC 0289 | 19.162 | 1629 | 3.627 | 2 |
| NGC 0150 | 19.291 | 1584 | 4.242 | 4 |
| NGC 0584 | 20.4 | 1802 | 4.463 | 3 |
| NGC 0596 | 21.452 | 1876 | 4.385 | 11 |
| NGC 0514 | 25.669 | 2472 | 3.975 | 1 |
| NGC 0524 | 26.43 | 2403 | 4.171 | 5 |
| NGC 0448 | 27.12 | 1908 | 7.246 | 5 |
| NGC 0274 | 27.525 | 1750 | 12.522 | 10 |
| VV 730 | 33.3 | 2700 | 10.203 | 2 |
| NGC 0470 | 34.726 | 2374 | 6.828 | 3 |
| NGC 0632 | 38.525 | 3168 | 5.843 | 6 |
| NGC 0048 | 41.967 | 1776 | 17.431 | 8 |
| MCG -01-02-001 | 44.5 | 3709 | 9.173 | 4 |
| UGC 12914 | 50.8 | 4371 | 11.02 | 8 |
| UGC 00139 | 55.605 | 3963 | 7.843 | 4 |
| NGC 0536 | 60.69 | 5189 | 10.593 | 5 |
| NGC 0523 | 62.725 | 4758 | 8.049 | 4 |
| NGC 0452 | 62.946 | 4962 | 4.613 | 5 |
| UGC 01087 | 63.275 | 4485 | 8.578 | 1 |
| NGC 0494 | 65.187 | 5462 | 6.595 | 10 |

测量值的图示见图 (5)。

![](Images/9789815124842-C2-F5.jpg) 图 (5)

测量值。

X 轴表示距离 (`D`)，单位为 *Mpc*，Y 轴表示径向速度 (`V[r]`)，单位为 *kms*^(−1)。

⁵数据收集自：[https://ned.ipac.caltech.edu/level5/NED1D/ned1d.html](https://ned.ipac.caltech.edu/level5/NED1D/ned1d.html)

⁶参见附录了解更多。

## 卡尔曼滤波过程

卡尔曼滤波过程根据方程 (34)、(35)、(36) 按照以下考虑进行：

### 1. 状态矩阵的获取
`D` 定义了星系距离地球的距离，单位为 *Mpc*，`V[r]` 表示径向速度，单位为 *kms*^(−1)。

| ![](Images/9789815124842-C2-EQ45.jpg) | (45) |
|---|---|
| ![](Images/9789815124842-C2-EQ46.jpg) | (46) |
|---|---|

### 2. 状态方程的获取
`H[o]` 表示哈勃常数⁶的值，等于 73 *kms*^(−1)*Mpc*^(−1)。

| ![](Images/9789815124842-C2-EQ47.jpg) | (47) |
|---|---|
| ![](Images/9789815124842-C2-EQ48.jpg) | (48) |
|---|---|

[7]哈勃常数值来源于 [https://ned.ipac.caltech.edu/](https://ned.ipac.caltech.edu/)

### 3. 使用从数据获得的测量值

| ![](Images/9789815124842-C2-EQ49.jpg) | (49) |
|---|---|

其中，`V[rm]` 表示径向速度测量值，`D[m]` 表示距离测量值。

使用方程 (37)、(38) 和 (39)，进行卡尔曼滤波以估计距离 `D` 和径向速度 `V[r]` 的值。矩阵 `H`、`C` 和 `I` 均为 2x2 单位矩阵。

下面的代码片段使用简单的 MATLAB 命令计算估计状态。

```
clc ;
clear ;
format long ;
set (0, ' defaulttextinterpreter ','Latex ');
S =\[ Inf, Inf \];
% Initial Estimated State Matrix
v = 100;
d = 1;
X = \[v;d\];
disp (X);
Ho = 73;
A = \[0 Ho ;0 1\];
disp (A);
H = eye (2, 2);
C = eye (2, 2);
I = eye (2, 2);
% Initial Estimated Process Covariance matrix
dv2 = 5;
dd2 = 0.25;
dvd = dv2 \*dd2;
ddv = dd2 \*dv2;
P = \[dv2 dvd ;ddv dd2 \];
% Measurement Values
file\_vm = fopen ('velocity . txt ', 'r');
file\_dm = fopen ('distance . txt ','r');
file\_vm\_err = fopen (' velocity\_error . txt ', 'r');
file\_dm\_err = fopen (' distance\_error . txt ','r');
format\_vm = '%d';
format\_dm = '%f';
format\_vm\_err = '%d';
format\_dm\_err = '%f';
size\_vm = \[1, Inf \];
size\_dm = \[1, Inf \];
size\_vm\_err = \[1, Inf \];
size\_dm\_err = \[1, Inf \];
vm = fscanf (file\_vm, format\_vm, size\_vm);
dm = fscanf (file\_dm, format\_dm, size\_dm);
vm = vm ';
v = 100;
d = 1;
X = \[v;d\];
disp (X);
Ho = 73;
A = \[0 Ho ;0 1\];
disp (A);
H = eye (2, 2);
C = eye (2, 2);
I = eye (2, 2);
% Initial Estimated Process Covariance matrix
dv2 = 5;
dd2 = 0.25;
dvd = dv2 \*dd2;
ddv = dd2 \*dv2;
P = \[dv2 dvd ;ddv dd2 \];
% Measurement Values
file\_vm = fopen ('velocity . txt ', 'r');
file\_dm = fopen ('distance . txt ','r');
file\_vm\_err = fopen (' velocity\_error . txt ', 'r');
file\_dm\_err = fopen (' distance\_error . txt ','r');
format\_vm = '%d';
format\_dm = '%f';
format\_vm\_err = '%d';
format\_dm\_err = '%f';
size\_vm = \[1, Inf \];
size\_dm = \[1, Inf \];
size\_vm\_err = \[1, Inf \];
size\_dm\_err = \[1, Inf \];
vm = fscanf (file\_vm, format\_vm, size\_vm);
dm = fscanf (file\_dm, format\_dm, size\_dm);
vm = vm ';
```

图 (6) 显示了使用卡尔曼滤波计算得到的径向速度 (`V[r]`)（单位为 *kms*^(−1)）与距离 (`D`)（单位为 *Mpc*）之间的关系图。

![](Images/9789815124842-C2-F6.jpg) 图 (6)

卡尔曼滤波图。

从图中得到的斜率等于哈勃常数，计算结果为：72.3 *kms*^(−1)*Mpc*^(−1)。

根据宇宙的 Milne 模型 [[10](#9789815124842-C2.html#r10)]，哈勃常数 (`H[o]`^(−1)) 的倒数给出宇宙年龄（以秒为单位），等于：

| ![](Images/9789815124842-C2-EQ50.jpg) | (50) |
|---|---|

约等于 135.3 亿年。

## 卡尔曼滤波的局限性

虽然高效且具有诸多优点，卡尔曼滤波技术仍存在一些局限性：

1. 卡尔曼滤波只能用于线性系统。虽然它比其他曲线拟合方法更快，但与某些其他滤波器相比仍可能更慢。
2. 在一维情况下，如果所有测量值均低于或高于真实值，则使用卡尔曼滤波技术永远无法获得真实值。

## 其他滤波器

存在各种其他滤波器，它们更快、更高效，并且能够滤除非线性系统，但可能需要较高的计算成本。这些包括：

1. 扩展卡尔曼滤波器
2. 无迹卡尔曼滤波器
3. 粒子滤波器

## 未来展望

1. 卡尔曼滤波可用于大气缪子中微子的轨迹重建。

如图 (7) 所示，印度基于中微子观测站 (INO) 的铁量能器用于研究涉及大气缪子中微子和反中微子的相互作用。探测器测量动量和方向以追踪缪子。探测器需要轨迹重建。使用卡尔曼滤波，轨迹估计很容易完成 [[11](#9789815124842-C2.html#r11)]。

![](Images/9789815124842-C2-F7.jpg) 图 (7)

INO 铁量能器位于 VECC。

2. 使用卡尔曼滤波在 GLAST 中重建电子轨迹 - 卡尔曼滤波可用于估计航天器的路径。
3. 根据非线性应用修改卡尔曼滤波。大量实际应用涉及非线性动力学。在这种情况下，卡尔曼滤波无法对变量进行适当的估计。因此，对卡尔曼滤波方法进行修改，使其对非线性系统也适用。

## 结论性评论- 卡尔曼滤波概览

我们已在两种情况下使用卡尔曼滤波：

1. 分析大量简单摆周期观测数据，找出其周期的真实值，并利用该结果计算地球上重力加速度的实际值。
