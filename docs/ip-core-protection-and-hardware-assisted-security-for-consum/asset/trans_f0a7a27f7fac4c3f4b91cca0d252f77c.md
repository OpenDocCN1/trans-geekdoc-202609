

## Figure 4.16(b) 寄存器 G 中带水印的数据通路段示意图

`A1_I(3)` 是加法器 1 通过第 1 个 16:1 多路复用器在第 4 次运行中的第 1 个输入

![image](OEBPS/images/PBCS0600-04-f17a.jpg)

## Figure 4.17(a) 寄存器 DB 中不带水印的数据通路段示意图

`A1_I(3)` 是加法器 1 通过第 1 个 16:1 多路复用器在第 4 次运行中的第 1 个输入

![image](OEBPS/images/PBCS0600-04-f17b.jpg)

## Figure 4.17(b) 寄存器 DB 中不带水印的数据通路段示意图

`A1_I(3)` 是加法器 1 通过第 2 个 16:1 多路复用器在第 4 次运行中的第 2 个输入

![image](OEBPS/images/PBCS0600-04-f18a.jpg)

## Figure 4.18(a) 寄存器 LB 中不带水印的数据通路段示意图

![image](OEBPS/images/PBCS0600-04-f18b.jpg)

## Figure 4.18(b) 寄存器 LB 中不带水印的数据通路段示意图

![image](OEBPS/images/PBCS0600-04-f19a.jpg)

## Figure 4.19(a) 嵌入水印前 Reg_G 多路复用器的部分门级表示

![image](OEBPS/images/PBCS0600-04-f19b.jpg)

## Figure 4.19(b) 嵌入水印后 Reg_G 多路复用器的部分门级表示

![image](OEBPS/images/PBCS0600-04-f19c.jpg)

## Figure 4.19(c) 嵌入水印前 Reg_G 多路复用器的部分门级表示

![image](OEBPS/images/PBCS0600-04-f19d.jpg)

## Figure 4.19(d) 嵌入水印后 Reg_G 多路复用器的部分门级表示

门结构的变化可以在 [Figure 4.19(a)](#Chapter4.html#c04_fig19a) 与 [Figure 4.19(b)](#Chapter4.html#c04_fig19b) 以及 [Figure 4.19(c)](#Chapter4.html#c04_fig19c) 与 [Figure 4.19(d)](#Chapter4.html#c04_fig19d) 之间观察到。最终带水印的 FIR-2 数据通路如 [Figure 4.20](#Chapter4.html#c04_fig20) 所示。相应的不带水印（原始）FIR-2 基准如 [Figure 4.21](#Chapter4.html#c04_fig21) 所示。由于插入水印约束导致的数据通路连接变化在 [Figure 4.20](#Chapter4.html#c04_fig20) 中用 *虚线* 标记。同样，带水印数据通路中的寄存器分配变化在同一图中使用 *边界曲线* 突出显示。带水印和不带水印的 FIR-2 基准设计均使用 Altera Quartus ([2018](#Chapter4.html#c04_bib2)) 13.0 v 实现，目标 FPGA 为 cyclone II ([Cyclone II FPGA, 2018](#Chapter4.html#c04_bib5))。实现的带水印和不带水印设计的示意图分别显示在 [Figures 4.22](#Chapter4.html#c04_fig22) 和 [4.23](#Chapter4.html#c04_fig23) 中。由于在设计中嵌入单相水印约束仅改变其数据通路结构而不改变控制器，因此带水印和不带水印设计应具有相同的控制器结构。对应于两个加法器和两个乘法器资源的 FIR-2 基准控制器结构如 [Figure 4.24](#Chapter4.html#c04_fig24) 所示。不带水印和带水印 FIR-2 的仿真结果如 [Figures 4.25(a)](#Chapter4.html#c04_fig25) 和 [(b)](#Chapter4.html#c04_fig25b) 所示。可以观察到，对于同一组输入，不带水印和带水印设计都产生相同的输出。因此，单相水印保留了带水印设计的功能性和正确性。不带水印和带水印 FIR-2 设计之间的资源利用率比较如 [Table 4.5](#Chapter4.html#c04_tbl5) 所示。可以观察到，由于插入 14 位水印，总逻辑单元方面的开销几乎可以忽略不计。

![image](OEBPS/images/PBCS0600-04-f20.jpg)

## Figure 4.20 单相带水印的 FIR-2 数据通路

寄存器分配变化使用环绕线标记

![image](OEBPS/images/PBCS0600-04-f21.jpg)

## Figure 4.21 不带水印的 FIR-2 数据通路

![image](OEBPS/images/PBCS0600-04-f22.jpg)

## Figure 4.22 单相带水印的 FIR-2 示意图表示

![image](OEBPS/images/PBCS0600-04-f23.jpg)

## Figure 4.23 不带水印的 FIR-2 示意图表示

![image](OEBPS/images/PBCS0600-04-f24.jpg)

## Figure 4.24 对应于两个加法器和两个乘法器的 FIR-2 基准控制器

![image](OEBPS/images/PBCS0600-04-f25a.jpg)

## Figure 4.25(a) 不带水印的 FIR-2 仿真结果

![image](OEBPS/images/PBCS0600-04-f25b.jpg)

## Figure 4.25(b) 单相带水印的 FIR-2 仿真结果

**Table 4.5** 不带水印和单相带水印的 FIR-2 之间的资源利用率比较

| 资源利用率摘要 || 不带水印的 FIR-2 || 带水印的 FIR-2 |

| --- | --- | --- |

| 器件系列 || Cyclone II || Cyclone II |

| --- | --- | --- |

| 器件 || EP2C70F896C6 || EP2C70F896C6 |

| 总逻辑单元 || 2,034/68,416 (3%) || 2,036/68,416 (3%) |

| 总组合功能 || 2,029/68,416 (3%) || 2,028/68,416 (3%) |

| 专用逻辑寄存器 || 69/68,416 (<1%) || 69/68,416 (<1%) |

| 总寄存器 || 69 || 69 |

| 总引脚 || 145/622 (23%) || 145/622 (23%) |

## 4.3.3 三相带水印 IP 核心/硬件的设计过程

在本节中，我们描述另一种带水印 DSP IP 核心/硬件的设计过程。我们描述了 Sengupta *et al.* ([2018](#Chapter4.html#c04_bib22)) 提出的一种更稳健的三相水印方法，用于设计 DSP IP 核心。这种方法不保护非 HDL IP 核心，例如存在于逻辑 CAD 工具内置库中的标准/预定义块或符号。三相水印方法保护 IP 核心的所有权（尤其是针对 DSP/多媒体应用）。在嵌入三相水印的过程中，假设同一种类型的微 IP 核心可从至少两个不同的第三方供应商处获得，以设计宏 IP 核心（这是行业中的常见做法）。

与单相水印方法（Sengupta *et al.*, 2016）不同，针对 DSP 核心的三相水印方法 ([Sengupta *et al.*, 2018](#Chapter4.html#c04_bib22)) 在 HLS 的多个阶段嵌入水印约束。更具体地说，三相水印方法在 HLS 的调度、硬件分配和寄存器分配阶段嵌入水印约束。除了在 HLS 的三个不同阶段植入水印约束之外，签名编码方案包含七个不同的变量，每个变量都携带唯一的编码规则。因此，三相水印方法增强了鲁棒性并最大限度地降低了签名被恶意篡改或移除的可能性。此外，对于攻击者来说，也难以识别合成阶段以及水印约束以何种方式植入到设计中。

在 Sengupta *et al.* ([2018](#Chapter4.html#c04_bib22)) 中，水印约束通过修改三个信息在调度、硬件分配和寄存器分配阶段嵌入：(a) ‘非关键操作 (*μ*[*m*] > 0)’ 时序表 (*μ*[*m*] = 操作的松弛时间)，(b) ‘功能单元分配’表，以及 (c) ‘寄存器分配’表（采用自 Sengupta *et al.*, 2016）。如前所述，这种水印方法有七个不同的变量，即 ‘α’、‘β’、‘γ’、‘i’、‘I’、‘T’ 和 ‘!’。变量 ‘γ’ 修改 ‘非关键操作 (*μ*[*m*] > 0)’ 的时序表，从而在调度阶段（第一阶段）嵌入水印约束。变量 ‘α’ 和 ‘β’ 修改 ‘功能单元分配’ 表，从而在硬件分配阶段（第二阶段）嵌入水印约束。最后，变量 ‘i’、‘I’、‘T’、‘!’ 修改 ‘寄存器分配’ 表，从而在寄存器分配阶段（第三阶段）嵌入水印约束。每个变量的签名编码过程如下描述 ([Sengupta *et al.*, 2018](#Chapter4.html#c04_bib22))。

### 4.3.3.1 签名编码方案

