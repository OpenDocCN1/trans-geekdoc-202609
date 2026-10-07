
Kane 模型、`Klassen` 模型和 `Hurkx` 模型是局部 BTBT 模型，而 `WKB` 模型是非局部 BTBT 模型。在局部模型中，使用简单的方程来驱动电场，这是寻找隧道宽度和隧道电流的重要参数。局部模型参数可以很容易拟合 TFET 仿真以找到其有效参数。然而，这些模型并不适用于 TFET 仿真，因为 BTBT 根本上是一个取决于隧道势垒宽度和能级的物理过程。非局部 BTBT 过程在物理上取决于隧道势垒的宽度和电荷流的方向。尽管许多商业器件仿真工具使用 TCAD（`Sentaurus`、`Silaco`、`Medici` 和 `HyENEXSS`），但它们为了执行目的继承了 TFET 模型的属性。其中，我们使用 `Sentaurus` 仿真软件进行分析，因为大多数制造商在制造过程中都遵循这一标准。事实上，BTBT 具有多维效应。隧道电流是通过考虑在器件结处施加反向偏压时，沿每个隧道切片的能量带分布来确定的。图 9 显示了价带电子允许隧道电流范围内的能量带分布示意图。

# 3 异质结隧道场效应晶体管

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_83_0.png)

图 3.8 (a) 双栅极 n 型 TFET 和 MOSFET 的示意图。(b) 传统 MOSFET（蓝色）与 TFET（绿色）在开启和关断状态下的亚阈值斜率对比。

源极区和沟道区电势差的增大。同样，在亚阈值区域之外获得显著的跨导仍然是困难的。TFET 的亚阈值摆幅（SS）可以通过对隧道电流关于栅电压（`$V_{GS}$`）的一阶导数得到 [37]。

```
$S = \log \left| 1 \frac{dR_R}{V_R V_{GS}} + \varepsilon + B \frac{d\varepsilon}{dV_{GS}} \right| (3.6)$
```

从该方程可以预测，亚阈值斜率几乎独立于温度（KT/q）。

## 3.1.5.4 TFET 性能增强技术

从之前的讨论可以分析出，TFET 的亚阈值斜率和开启电流受结电场控制，由偏置电压控制。对于短沟道器件，特性长度是一个有效参数。特性的缩小是通过结构工程（如纳米线、双栅、等效氧化层厚度 EOT 和更小的体厚）实现的，这可以增强 TFET 的性能。另一种方法是掺杂工程，通过在源极附近注入不同极性的结区/晕环（pocket/halo）掺杂，有效提高硅 TFET 的性能。结区区将被耗尽，留下电离正电荷，从而在给定偏置电压下产生指向内区的电场。通过调节，产生率将随着亚阈值斜率的陡峭而提高。

## 3.1.5.5 TFET 中的漏电流

有五种影响 TFET 器件在关断区域的主要漏电流。漏电流源于源极和漏极之间内建电势的热发射和高 k 堆叠。在所有因素中，栅极引起的漏极漏电（GIDL）被认为是关断模式下有效的漏极漏电流。GID 上的热载流子由于感应陷阱和氧化层捕获电荷而产生。此前，热发射是隧穿的并行过程，用于将空穴和电子载流子从价带传输到导带。`Shockley-Read-Hall` 复合决定了器件的热效应，因为在低偏置电压下热效应非常显著。除了 InAs 等窄带隙材料外，在带对带间隧穿过程中，一种新的漏电流将占据主导地位。在此过程中，电子将受到热激发并形成价带以截获陷阱。这防止了偏置电压超过 `$E_g/q$`，由于漏极侧的少数载流子将产生反向偏置，导致双极性电导。这种双极性电导可以通过在漏极侧建立非对称性来降低。这可以通过栅极提升和栅极重叠条件实现。另一种方法是在源极侧使用与沟道和漏极相比带隙低的异质材料。

## 3.1.6 仿真工具

数值仿真在现代科学研究工作中变得越来越重要。计算机辅助设计（TCAD）仿真工具提供了设计结构特性的原型，这些特性可以在较短的时间内准确预测。因此，它节省了我们分析和实验工作的时间、成本和大量精力。TCAD 工具以 2D 或 3D 的形式执行，根本上取决于有限元法（FEM），根据器件电场、掺杂分布、电势偏置、载流子密度等物理处理机制或电机制可以评估器件的制造及其电行为 [40–41]。

`Centaurus TCAD` 工具是一种基于行业标准并与多个制造商合作的仿真工具，其原型根据实验细节进行了调整。该技术已被证明能够对未来系统的特性提供精确预测，以满足半导体国际技术路线图（ITRS）的需求 [19]。

## 3.3.1.6 TFET 模型

在 TCAD 仿真工具中，TFET 模型基本上分为两类带对带隧穿（BTBT）模型：

- 局部 BTBT 模型
- 非局部 BTBT 模型

Kane 模型、`Klassen` 模型和 `Hurkx` 模型是局部 BTBT 模型，而 `WKB` 模型是非局部 BTBT 模型。在局部模型中，使用简单的方程来驱动电场，这是寻找隧道宽度和隧道电流的重要参数。局部模型参数可以很容易拟合 TFET 仿真以找到其有效参数。然而，这些模型并不适用于 TFET 仿真，因为 BTBT 根本上是一个取决于隧道势垒宽度和能级的物理过程。非局部 BTBT 过程在物理上取决于隧道势垒的宽度和电荷流的方向。尽管许多商业器件仿真工具使用 TCAD（`Sentaurus`、`Silaco`、`Medici` 和 `HyENEXSS`），但它们为了执行目的继承了 TFET 模型的属性。其中，我们使用 `Sentaurus` 仿真软件进行分析，因为大多数制造商在制造过程中都遵循这一标准。事实上，BTBT 具有多维效应。隧道电流是通过考虑在器件结处施加反向偏压时，沿每个隧道切片的能量带分布来确定的。图 9 显示了价带电子允许隧道电流范围内的能量带分布示意图。

# 3 异质结隧道场效应晶体管

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_83_0.png)

图 3.8 (a) 双栅极 n 型 TFET 和 MOSFET 的示意图。(b) 传统 MOSFET（蓝色）与 TFET（绿色）在开启和关断状态下的亚阈值斜率对比。

TABLE 3.1 Parameters for Centaurus

| PARAMETER | DEFAULT VALUE |
| :--- | :--- |
| MC | 0.160 |
| MV | 0.240 |
| ME-TUNNEL | 0.160 |
| MH-TUNNEL | 0.250 |

![](img/f43fc2d88fdf77da6ccf8abfe605d6a7_73_1.png)

图 3.9 Schematic diagram of band-to-band tunneling (BTBT)

## 3.1.7 Major Parameters

The device performance and its functionality were determined by various parameters. The following sections discuss only a few.

### 3.7.1 Subthreshold Slope

The subthreshold slope is basically the `$V_t$` effect. Ideally, the MOSFET should have zero subthreshold slope, which in fact can never be. In reality, there is always some flowing below the threshold voltage. The SS is an important parameter for evaluating the subthreshold properties of short-channel devices.

```
$SS = \left(\frac{\partial log V_d}{\partial V_g}\right)^{-1}$ (3.7)
```

### 3.7.2 Drain Induced Barrier Lowering

Drain induced barrier lowering (DIBL) mainly predicts the `$V_t$` effect on subthreshold characteristics. Due to a large amount of drain bias, the source–channel barrier will be reduced. The DBIL basically occurs in the short channel devices in which the device is controlled by both the gate biasing and the drain biasing. It can be measured by lateral shifting of transfer curves in the subthreshold region, where change in threshold voltage (`$\Delta V_t$`) is divided by `$V_{dd}$`.

```
$DIBL = \frac{\Delta V_t}{\Delta V_{dd}}$ (3.8)
```

### 3.7.3 Cut-Off Frequency

When evaluating the devices for analog use, cut-off frequency (`$f_t$`) is the significant parameter. The value of the cut-off frequency occurs when the current gain is unity. It is given by equation 3.9, where `$g_m$` represents the transconductance and the total capacitance of the device is `$C_T$`.

```
$f_t = \frac{g_m}{2\pi C_T}$ (3.9)
```

### 3.7.4 Transconductance ($g_m$)

Transconductance (`$g_m$`) is the reciprocal of resistance and is defined by equation 3.10. It is the electrical characteristic that relates the current through a device's output to the voltage at the device's input.

```
$g_m = \frac{\Delta I_d}{\Delta V_{gs}}$ (3.10)
```

### 3.7.5 Early Voltage ($V_{EA}$)

Early voltage (`$V_{EA}$`): This parameter effectively converts the DC power into the AC frequency with the performance gain, and the term is given by equation 3.11. It is the main figure of metric for the analogy application.

```
$V_{EA} = \frac{I_d}{g_d}$ (3.11)
```

# 3 异质结隧道场效应晶体管

## 3.1.7.6 响应度与量子效率

除了响应时间和探测性外，评估光电探测器效率的其它参数还包括响应度 (`$R_\phi$`) 和量子效率 (`$Q_e$`)。`$Q$` 增益定义为电极之间每吸收一个光子通过的电荷载子数量；`$R_\phi$` 定义为单位光功率在光传感器有效区域产生的光电流。`$R_\phi$` 和 `$Q_e$` 的表达式由方程 3.12 和 3.13 所示，其中 `$h$` 代表普朗常数，`$q$` 是电子电荷，入射辐射波长用 `$\lambda$` 表示 [47]。

$$Responsivity (R_\phi) = \frac{\text{可用光电流},I_{ph}}{\text{入射光功率},P_o} (3.12)$$

$$Quantum Efficiency (Q_e) = R_\phi \frac{h}{q\lambda} (3.13)$$

## 3.1.8 建议的器件结构及其规格

图 3.10a 给出了具有不同掺杂浓度的源、道、漏极的硅材料 3D 垂直 p–i–n 结构。为了缩短电荷传输的隧道长度，在源极和沟道之间引入了 10 nm 的 SiGe 材料。这将能量带隙从 1.1 eV 降低到 0.7 eV 并增强器件的导通电流。接下来的图 3.10b 将显示道宽为 50 nm、漏极长度为 30 nm 的截面。器件功函数 (`$\phi_w$`) 为 4.5 eV（n 型），使用 `Hf$_2$` 作为栅极金属功函数，宽度为 2 nm。表 2 显示了器件结构参数的描述。

图 31a 和 b 分别显示了 T 型 FETET 的等效表示、源-道区域和道-漏极区域的空穴和电子浓度（cm$^{-2}$ V·s$^{-1}$）。两种电荷浓度，`eMobility` 和 `hMobility` 在界面区域中心均为高值。这是由于与边缘处相比，器件中心具有较高的电场。

## 3.1.9 作为反相器的 T 型器件

使用 TCAD `Sentaurus` 仿真软件通过混合模式技术将 n 型和 p 型 T 型器件组合成反相器器件，如图 3.12 所示。p 型和 n 型器件之间的唯一区别是功函数和面积因子。p 型器件的这两个值将更大，即面积将是 n 型的两倍，且 n 型功函数为 4.5 eV，p 型为 5.3 eV。n 垂直 T 型 FETET 的变化是 p–i–n 结构，而垂直 T 型 FETET 是 n–i–n 结构。`Hf$_2$` 的厚度取为 2 nm，相对于 SiO$_2$ 的等效氧化层厚度（EOT）值为0.37 nm。整个仿真过程中 Si$_{,Ge}$ 摩尔分数取为 0.8。

图 3.13 在单个显示图中了 n 型和 p 型配置的器件电流特性。两个器件在 `$V_{da}$` = 1 V 时均实现了约亚阈值电压，值分别为 0.357 V 和 3.49 V。在双极性电流被抑制的情况下，导通电流与关断电流的比值约为 `$10^{-11}$`，每个器件与其图表分别表示。

# 纳米电子器件

# 3 异质结隧道场效应晶管

### 3.1.11 结论

本章讨论了 TFET 作为低功耗应用的传统 MOSFET 的基本概念和评估。提出了一种新型 p–i–n 结器件，并使用 TCAD 仿真进行了分析。垂直隧道 FET 具有源极沟道分布，该特征将增强仿真器件的可扩展性。此外，利用混合模式技术构建了 p–i–n 结器件和 n–i–p 结器件以形成反相器电路。对 SiO₂ (k= 3.9)、Si₃N₄ (k= 7.0) 和 HfO₂ (k= 21) 栅极氧化物材料的传输特性进行了比较，其中 HfO₂ 在 0 到 1 的转换中表现出最佳输出。此外，还利用电流模式的低功耗电路器件对所提器件在硬件安全系统中的应用进行了分析。

## 参考文献

- [1] Tanaka, Junko, Toyabe Yabe, Iegaho Hara, Shin'ichiro Kimura, Hiromasa Nada, and Kiyoo Ito. “亚 0.1 微米 MOSFET 的完全抑制短沟道效应的仿真。” IEEE Electron Device Letters 14, no. 8 (1993): 396–399.
- [2] Bricout, P.- and Emmanuel Dubois. “使用凹型沟道的 0.1 微米 MOSFET 的短沟道效应抑制和电流能力。” IEEE Transactions on Electron Devices 23, no. 8 (1996): 1251–1255.
- [3] Young, Konrad K. “全耗尽 MOSFET 中的短沟道效应。” IEEE Transactions on Electron Devices 36, no. 2 (1989): 399–402.
- [4] Shockley, William. “结晶体管连接的路径。” IEEE Transactions on Electron Devices 31, no. 11 (1984): 1523–1546.
- [5] Wang, Y. and B. Raj. “用于高灵敏度的无结 FET 生物传感器的设计与性能。” IEEE Nanotechnology 1, no. 8 (2019): 569–574.
- [6] Instruments, Tex. “Jack 建造的芯片。” http://www.team.com/korbyct/jackshuit.html [在线], 2011.
- [7] Moore, Gordon E. “在集成电路中挤入更多元件。” IEEE Solid-State Circuits Society 38, no. 8 (1965): 114–117.
- [8] Frank, David J., Robert H. Leonard, Edward Nowak, Paul Solomon, Yuan Taur, and Hong-Sun Philip Wong. “MOSFET 的缩放限制及其应用依赖性。” Proceedings of IEEE 89, no. 3 (2001): 259–288.
- [9] Wadhera, T., D. Kakar, G. Wadhera, and B. Raj. “垂直 FET 生物传感器领域的最新进展与进展：综述。” Journal of Electronics Materials 48, no. 12 (2019): 7635–7646.
- [10] Zhang, Victor R. Ralph K. Kevin, James A. Hutchby, and George I. Bourianoff. “二进制切换的限制：一种 Ganken 器。” Proceedings of IEEE 91, no. 11 (2003): 1934–1939.
- [11] Edgar, Julian Phillips. “控制电路的方法和目的。” 美国专利, 1745175, 1930 年 1 月 28 日颁发。
