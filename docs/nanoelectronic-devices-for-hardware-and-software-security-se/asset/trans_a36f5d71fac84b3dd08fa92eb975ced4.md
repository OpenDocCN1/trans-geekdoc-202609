

用于电荷等离子 TFET 的 28 种纳米电子器件

## 1.1.2 电荷等离子 TFET 中的双极性

双极性问题在这些这些 JLTFET 和 DLTFET 中是固有的。为了减少双极性，研究人员已经提出了许多器件架构。双极性基本上是指在负 $V_{GS}$ 或负栅极电压下，电子通过从沟道中的价带隧道穿到漏极区域的导带而导电。在 TFET 中，负栅极电压导致漏极-沟道界面隧道势垒变窄是一个普遍现象，这在第 1.8.3 节中也有了解释。在本节中，我们仅关注了减少电荷等离子 TFET（即 JLTFET 和 DLTFET）双极性的技术。目前已提议在源极和漏极上使用具有低功函数材料的三栅结构 [20][56]。源极侧的低功函数材料负责提高 ON 状态性能。漏极侧的低功函数材料在双极性状态（即负电压）下加宽了隧道势垒。尽管这种技术达到了目的，但从缩放角度来看极具挑战性。另一个选项是在漏极使用双功函数电极。双漏极电极也通过改变双极性状态下漏极-沟道界面的载流子浓度来加宽隧道势垒 [52][55][6][66]。研究人员还提议在栅极和漏极电极之间的源极下方嵌入低功函数金属杂质，这会改变漏极-沟道界面的载流子浓度 [53]，从而导致双极性状态下隧道势垒的加宽。在栅极和漏极电极之间应用较厚的间隔层（~15 nm），通过抑制价带（沟道）和导带（漏极）的重叠来进一步加宽隧道势垒 [64]。

## 1.12 JLTFET 和 DLTFET 的仿真环境

所有仿真均通过二维器件仿真器 Silvaco Atlas [33] 实现。无结区 TFET 的仿真是根据 [50] 中给出的器件规格进行的。为了考虑载流子的隧道效应，激活了非局部 BTBT 模型。同时也考虑了界面陷阱的影响。在 SRH（Shockley–Read–Hall）表达式所需的本征载流子浓度计算中，实现了 Fermi-Dirac 统计。由于我们假设使用了高 k 金属防护，因此没有使用栅极漏电流模型。SRH 复合模型和 Lombardi 迁移率模型用于模拟高杂质原子的影响。量子局域模型由 Hansch [34] 以类似于 [50] 的方式实现。带隙模型被用于模拟高掺杂的影响。高 k 间隔层对无结区 TFET 硅沟道的影响处理方式与 [50] 中提到的类似，即通过包含高 k 间隔层与半导体界面处的缺陷来实现。隧道区域具有非常细的网格间距，以便高效计算隧道效应产生的电流。

## 1.13 结论

在本章中，我们研究了无结区和无掺杂器件中载流子传输的基本器件物理。这些基于电荷等离子子的无结区或无掺杂器件在较低工艺节点具有替代化学掺杂结器件的巨大潜力。对于亚阈值性能或低功耗应用，基于电荷等离子体的场效应晶体管为传统的或化学掺杂 TFET 提供了一个非常好的替代方案。然而，这些基于电荷等离子无结区晶体管或无结区 FET 面临一些需要解决的主要挑战，以获得更好的器件性能。无结区晶体管中的 GITL 问题通过加宽漏极-沟道界面形成的隧道势垒或通过降低寄生 BIT 中的浓度来抑制。使用静电掺杂漏极是一种非常好的提议技术 [[67][4]。在无结区 TFET 中，本章强调了低 ON 状态电流和双极性的优势。这些问题可以通过使用双 k 间隔层或尺寸背栅 [51][35] 来解决。此外，通过采用这些技术，可以提高无结区器件的性能。这些无结区器件可能是微电子器件的未来。

## REFERENCES

- [1] Behzad Razavi, *Fundamentals of microelectronics*, Student edition. Wiley, 2006.
- [2] I. Tuoni, "The Lives and Death of Moore’s Law," *First Monday*, vol. 7, no. 11, 2002.
- [3] "Electrical & Electronic Engineering: MOSFET, MOS structure, Voltage MOSFET, MOSFET Different Region," [Online]. Available: http://eeinvestigationblog.com/2013/12/mosfet-mos-structure.html.
- [4] M. A. Raushan, N. Alam, and M. J. Siddiqui, "Design to Improve the Performance of JAMFETs," *IEEE Circuits, Devices and Systems*, vol. 14, no. 3, pp. 333–339, May 2020
- [5] Girish Wada and B. Raj, "Design and Performance Analysis of Junctionless TFET Biosensor for High Sensitivity," *IEEE Nanotechnology*, vol. 18, pp. 567–574, 2019.
- [6] "Semiconductor Device Physics 1 Electronics & Applied Projects." [Online]. Available: http://ekm16.blogspot.com/2015/04/device-physics.html.
- [7] J. Lilenberg, "Design and Analysis for Controlling Electronic Circuits," U.S. Patent, 08 October 1926.
- [8] Girish Wada, Priyanka Kombo, and B. Raj, "Design Optimization of Junctionless TFET Biosensor for High Sensitivity," *Advances in Nanoscale and Technology*, vol. 10, pp. 04501, 2020.
- [9] S. Gudrapani, "Investigation of Junction-Less Transistor (JLT) for CMOS Scaling," Department of Electrical Engineering, Indian Institute of Bombay, 2012.
- [10] T. K. Kim *et al.*, "First Demonstration of Junctionless Accumulation-Bulk FinFETs with Robust Junction Isolation," *IEEE Device Letters*, vol. 34, no. 12, pp. 1479–1481, 2013.
- [11] S. Gudrapani, S. Ganguly, and A. Kottantharaj, "Enhanced Electrostatic Control of Short-Channel Junctionless Transistor with High-K Spacers,” *IEEE Device Letters*, vol. 32, no. 10, pp. 1325–1332, 2011.
- [12] Soumila, Shendra Gandhi, Girish Wada, and B. Raj, "An Analytical Modeling for Dual Source Tunnel Field Effectistor," *International Journal of Recent Technology and Engineering (INRTE)*, vol. 8, no. 2. (2019).
- [13] Shalendra Gandhi and B. Raj, "Design and Analysis of Heterojunction Tunnel Field Effectistor,” *Journal of Electronics*, vol. 48, no. 10, pp. 6255–6260, 2019.
- [14] C. Sahu and J. Singh, "Potential Benefits and Sensitivity of Dopless Transistor,"（注：原文为Dopless，应为Dopeless，翻译时保持原文术语或根据语境理解，此处保留原意：无掺杂晶体体的潜在收益与灵敏度）...此处根据指令要求，参考文献列表的标题通常保持英文。

*(抱歉，由于参考文献列表包含大量专业术名和标题，按照学术文档规范，参考文献部分通常不翻译以确保检索准确性。)*

