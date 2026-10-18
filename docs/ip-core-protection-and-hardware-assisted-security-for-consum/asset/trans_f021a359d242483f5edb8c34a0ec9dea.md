

在 SRAM 存储器的情况下，一个重要的挑战是将足够的熵注入固定长度的密钥中。在 SRAM PUF 的情况下，生成的密钥会带有噪声，并且在辅助数据生成和纠错过程中会丢失熵（[Koeberl *et al*., 2014](#Chapter12.html#c12_bib30); [Maes *et al*., 2012](#Chapter12.html#c12_bib41)）。在某些情况下，辅助数据过程中的熵损失会被视为均匀分布。当熵密度乘以纠错时，熵与输出长度相等。在这种情况下，即使原始 PUF 输出的熵较低，也可以用于生成密钥。PUF 输出的熵通常未知，因此在最坏情况下应使用更严格的方法进行熵估计。在综合征构造和码偏移中，当考虑二进制线性码 *C*(*n*, *k*, *t*) 时，其中代码维度的长度由 *n* 和 *k* 表示，可纠正的最大错误数由 *t* 表示。当考虑最坏情况时，丢失的熵可以计算为 ![image](OEBPS/images/c12-Eqn-in-16.gif) bits，这可以被视为满意（[Maes *et al*., 2012](#Chapter12.html#c12_bib41)）。当原始比特熵小于 ![image](OEBPS/images/c12-Eqn-in-17.gif)/bit 时，在最坏情况下输出中将不存在熵。因此，PUF 不适合在最坏情况下生成密钥。对于计算最小熵，通常使用 NIST 规范 800-90（[Barker and Kelsey, 2015](#Chapter12.html#c12_bib3)）。设 *p*[0] 和 *p*[1] 为二进制输出源的概率，其中 ![image](OEBPS/images/c12-Eqn-in-18.gif)，可用于计算最小熵的 *p*[0] 和 *p*[1] 的最大概率如下（[Liu *et al*., 2018](#Chapter12.html#c12_bib38)）：

![image](OEBPS/images/c12_eqn12_5.gif)

其中 ![image](OEBPS/images/c12-Eqn-in-19.gif)。

为了提高源比特的熵，使用 Von Neumann 提取器来压缩比特（[Leest *et al*., 2010](#Chapter12.html#c12_bib37)）。在 Von Neumann 提取器的情况下，过程如下：考虑一个模式样本，并将其分为连续的非重叠比特。当比特对彼此不同时，所考虑的第二个比特将被丢弃。如果两个比特相等，则两者都被丢弃。在处理完所有比特后，剩余的比特将按顺序排列。为简单起见，考虑对“1”的偏差。比特对 A 和 B 具有最大概率为 ![image](OEBPS/images/c12-Eqn-in-20.gif) 和 ![image](OEBPS/images/c12-Eqn-in-21.gif)，这些概率是由于比特“1”出现引起的，概率分别为 ![image](OEBPS/images/c12-Eqn-in-22.gif) 和 ![image](OEBPS/images/c12-Eqn-in-23.gif)。提取器的输出长度与输入长度之比称为“提取率”。这可以表示为（[Liu *et al*., 2018](#Chapter12.html#c12_bib38)）：

![image](OEBPS/images/c12_eqn12_6.gif)

### 12.8 基于忆阻器的 PUF

技术缩放导致了高性能、低功耗芯片和 SoC 的设计（[Mohanty, 2015](#Chapter12.html#c12_bib53)）。晶体管尺寸已达到 12 nm（[AMD, 2018](#Chapter12.html#c12_bib1）），并且仍在进一步降低。有关 7 nm 芯片将商业化发布的猜测。但是存在一个可以达到的阈值，正在探索晶体管的替代品来取代它们。缩放也导致了许多问题，包括功耗、制造和开关速度。使用 RRAM（电阻式随机存取存储器）技术和 3D 阵列实现了高开关速度和低功耗（[Mohanty, 2015](#Chapter12.html#c12_bib53)）。这些 RRAM 也称为“忆阻器”。它是一个两端器件，其电阻取决于通过它的电压量和电流方向。因此，利用忆阻器件的这一特性，可以实现多个电阻电平。通过从一种电阻状态切换到其他状态，也可以实现连续可变电阻。电阻变化还取决于器件已经处于的状态，即在上一次迭代中已经通过器件的电压/电流。这证明忆阻器具有“电阻器”和“存储器”的特性。因此得名“忆阻器”（Memory + Resistor）。忆阻器的忆阻抗由以下公式给出（[Rose *et al*., 2013](#Chapter12.html#c12_bib59)）：

![image](OEBPS/images/c12_eqn12_7.gif)

其中提供的最大电阻（![image](OEBPS/images/c12-Eqn-in-24.gif)）表示为 ![image](OEBPS/images/c12-Eqn-in-25.gif)，最大和最小忆阻抗之间的差值表示为 ![image](OEBPS/images/c12-Eqn-in-26.gif)，施加的电压极性由 ![image](OEBPS/images/c12-Eqn-in-27.gif) 表示。![image](OEBPS/images/c12-Eqn-in-28.gif) 是迁移率，*D* 表示器件厚度。

在模拟模型的情况下，器件提供的忆阻抗将从最小值逐渐变化到最大值，并通过改变 *W* 和 *D* 来实现。[图 12.17](#Chapter12.html#c12_fig17) 显示了忆阻器的器件结构和工作原理。器件的掺杂区域和未掺杂区域将根据通过它的电流的方向和大小而变化。忆阻器包含两层二氧化钛，其中一层含有过量的氧，夹在两个金属电极之间。当沿正向方向施加电流时，氧离子将分布在整个器件中，如 [图 12.17](#Chapter12.html#c12_fig17) 所示，这会增加掺杂区域。然后器件提供的电阻将降低。同样，当沿反向方向施加电流时，氧原子将集中在一个地方，如 [图 12.17](#Chapter12.html#c12_fig17) 所示，这会减少掺杂区域。然后器件提供的电阻将显著增加。因此，在忆阻器的情况下，忆阻抗可以变化。

![image](OEBPS/images/PBCS0600-12-f17.jpg)

图 12.17 一个忆阻器器件

