
每个神经元群体由两个模块建模。第一个模块将传入神经元群体的动作电位平均脉冲密度转换为平均突触后膜电位，后者可以是兴奋性的，也可以是抑制性的。该模块被称为突触后电位（PSP）模块，代表一种线性变换，其冲激响应由文献 [\[20\]](#c03.xhtml#c3-bib-0020) 给出：

![Figure 3.10 Simplified model for brain cortical alpha generation. The input is a pulse‐shaped waveform.](images/c03f010.gif)

[**图 3.10**](#c03.xhtml#R_c3-fig-0010) 大脑皮层 α 节律生成的简化模型。输入为脉冲形波形。

(3.37)![equation](images/c3-disp-0039.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>h</mi><mi>e</mi></msub><mfenced open="(" close=")"><mi>t</mi></mfenced><mo>=</mo><mfenced open="{" close=""><mtable><mtr><mtd><maligngroup/><mi mathvariant="italic">Aat</mi><msup><mi>e</mi><mrow><mo form="prefix">&#8722;</mo><mi mathvariant="italic">at</mi></mrow></msup><mspace width="0.2em"/><mi>t</mi><mo>&#8805;</mo><mn>0</mn></mtd></mtr><mtr><mtd><maligngroup/><mn>0</mn><mspace width="0.2em"/><mi>t</mi><mo>&#60;</mo><mn>0</mn></mtd></mtr></mtable></mfenced></math> 

用于兴奋性情况，抑制性情况如下：

(3.38)![equation](images/c3-disp-0040.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>h</mi><mi>i</mi></msub><mfenced open="(" close=")"><mi>t</mi></mfenced><mo>=</mo><mfenced open="{" close=""><mtable><mtr><mtd><maligngroup/><mi mathvariant="italic">Bbt</mi><msup><mi>e</mi><mrow><mo form="prefix">&#8722;</mo><mi mathvariant="italic">bt</mi></mrow></msup><mspace width="0.2em"/><mi>t</mi><mo>&#8805;</mo><mn>0</mn></mtd></mtr><mtr><mtd><maligngroup/><mn>0</mn><mspace width="0.2em"/><mi>t</mi><mo>&#60;</mo><mn>0</mn></mtd></mtr></mtable></mfenced></math> 

`A` 和 `B` 分别决定兴奋性和抑制性 PSP 的最大振幅，`a` 和 `b` 是神经元树突网络中被动膜时间常数倒数之和以及所有其他空间分布延迟的集总表示。`Sigm` 函数定义如下 [\[21\]](#c03.xhtml#c3-bib-0021)：

[(3.39)](#c03.xhtml#R_c3-disp-0041)![equation](images/c3-disp-0041.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mtext mathvariant="italic">Sigm</mtext><mfenced open="(" close=")"><mi>v</mi></mfenced><mo>=</mo><mfrac><mrow><mn>2</mn><msub><mi>e</mi><mn>0</mn></msub></mrow><mrow><mn>1</mn><mo>+</mo><msup><mi>e</mi><mrow><mi>r</mi><mfenced open="(" close=")"><mrow><msub><mi>v</mi><mn>0</mn></msub><mo>&#8722;</mo><mi>v</mi></mrow></mfenced></mrow></msup></mrow></mfrac></math> 

其中 `e` [`0`] 表示神经元群体的最大放电率，`v` [0] 为达到 50% 放电率时的 PSP，`r` 为 S 型变换的陡峭程度。图中的连接常数 `C[1]` – `C[4]` 表征锥体细胞与兴奋性、抑制性中间神经元之间的相互作用，反映了神经元间建立的突触总数。

作为经验值，考虑 `C = C[1] = 135`，其余参数的典型建议值为 `C[2] = 0.8C`，`C[3] = 0.25C`，`C[4] = 0.25C`，`A = 3.25`，`B = 22`，`v` [0] `= 6`，`a = 100 s^(−1)`，`b = 50 s^(−1)` 和 `a[d] = 30`。

上述系统已扩展用于视觉诱发电位（VEP）的建模，这基于这样一个事实：VEP 是两个或多个所谓皮层柱相互作用的结果。[图 3.11](#c03.xhtml#c3-fig-0011) 展示了一个用于 VEP 的双柱模型，其中每个模块代表 [图 3.10](#c03.xhtml#c3-fig-0010) 中的模型。

此类模型的主要问题在于仅产生单通道 EEG，与第 [3.2.2](#c03.xhtml#c3-sec-0004) 小节解释的相位耦合模型不同，它没有对通道间关系和脑区固有连接性进行建模。因此，必须定义一个更准确的模型，以实现多通道 EEG 生成系统的仿真。这仍是一个开放性问题，也是研究领域之一。

![Figure 3.11 A two‐column model for generation of VEP. Two connectivity constants K1 and K2 attenuate the output of a column before it is fed to the other.](images/c03f011.gif)

[**图 3.11**](#c03.xhtml#R_c3-fig-0011) 用于 VEP 生成的双柱模型。两个连接常数 `K[1]` 和 `K[2]` 在一柱的输出馈入另一柱之前对其进行衰减。

## 3.4 直接从 EEG 信号导出的数学模型

这些模型基本上是用有限数量的统计参数来描述单通道和多通道信号，这些参数不仅表征波形的形态，还表征其时间或空间采样相关性。在这些模型中，内部和外部噪声通常被视为与脑源性信号无关的非相关时间信号。

### 3.4.1 线性模型

#### 3.4.1.1 预测方法

使用预测方法的主要目的是找到一组模型参数，以最好地描述信号生成系统。此类模型通常需要噪声型输入。在信号的自回归（AR）建模中，单通道 EEG 测量的每个采样点被定义为与其若干前序采样点线性相关，即：

(3.40)![equation](images/c3-disp-0042.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>y</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>=</mo><mo form="prefix">&#8722;</mo><msubsup><mo>&#8721;</mo><mrow><mi>k</mi><mo>=</mo><mn>1</mn></mrow><mi>p</mi></msubsup><msub><mi>a</mi><mi>k</mi></msub><mi>y</mi><mfenced open="(" close=")"><mrow><mi>n</mi><mo>&#8722;</mo><mi>k</mi></mrow></mfenced><mo>+</mo><mi>x</mi><mfenced open="(" close=")"><mi>n</mi></mfenced></math> 

其中 `a[k]` ，`k = 1,2,…,p` 为线性参数，`n` 表示归一化为单位的离散采样时刻，`p` 称为模型阶或预测阶，`x(n)` 为噪声输入。在自回归滑动平均（ARMA）线性预测模型中，每个采样点基于其若干前序输入和输出采样值获得，即：

(3.41)![equation](images/c3-disp-0043.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>y</mi><mfenced open="(" close=")"><mi>n</mi></mfenced><mo>=</mo><mo form="prefix">&#8722;</mo><msubsup><mo>&#8721;</mo><mrow><mi>k</mi><mo>=</mo><mn>1</mn></mrow><mi>p</mi></msubsup><msub><mi>a</mi><mi>k</mi></msub><mi>y</mi><mfenced open="(" close=")"><mrow><mi>n</mi><mo>&#8722;</mo><mi>k</mi></mrow></mfenced><mo>+</mo><msubsup><mo>&#8721;</mo><mrow><mi>k</mi><mo>=</mo><mn>0</mn></mrow><mi>q</mi></msubsup><msub><mi>b</mi><mi>k</mi></msub><mi>x</mi><mfenced open="(" close=")"><mrow><mi>n</mi><mo>&#8722;</mo><mi>k</mi></mrow></mfenced></math> 

其中 `b[k]` *，k =* 1, 2,…, `q` 为额外的线性参数。参数 `p` 和 `q` 为模型阶。赤池准则可用于通过最大化关于模型阶的对数似然方程 [\[22\]](#c03.xhtml#c3-bib-0022) 来确定测量信号适当模型的阶数：
