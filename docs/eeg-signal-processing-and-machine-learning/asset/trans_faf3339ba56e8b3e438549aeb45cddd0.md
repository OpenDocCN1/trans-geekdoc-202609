
其中 ![images](images/c17-i0001.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msubsup><mi>x</mi><mi>i</mi><mn>0</mn></msubsup><mfenced open="(" close=")"><mi>n</mi></mfenced></math> 为眨眼参考信号，*i* 为前述各电极位置的索引。由于包含眨眼伪迹的 IC 在特定 τ 值下具有较大的相关性，而包含正常 EEG 活动的 IC 则不然，因此该特征值对于包含眨眼伪迹的 IC 将更大。

*   **特征 IV**：使用 IC 分布与更可能包含 EOG 的电极信号分布之间的统计距离。这可以通过 Kullback-Leibler (KL) 距离来度量，定义如下：(17.5)![equation](images/c17-disp-0005.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msub><mi>f</mi><mn>4</mn></msub><mo>=</mo><msubsup><mo>&#8747;</mo><mrow><mo form="postfix">&#8722;</mo><mo>&#8734;</mo></mrow><mo>&#8734;</mo></msubsup><mi>p</mi><mfenced open="(" close=")"><mrow><mi>u</mi><mfenced open="(" close=")"><mi>t</mi></mfenced></mrow></mfenced><mo mathvariant="italic">ln</mo><mfrac><mrow><mi>p</mi><mfenced open="(" close=")"><mrow><mi>u</mi><mfenced open="(" close=")"><mi>t</mi></mfenced></mrow></mfenced></mrow><msub><mi>p</mi><mi mathvariant="italic">ref</mi></msub></mfrac><mi mathvariant="italic">du</mi><mfenced open="(" close=")"><mi>t</mi></mfenced><mspace width="1em"/><mtext>for</mtext><mspace width=".8em"/><mo>&#8704;</mo><mi>t</mi><mspace width="0.2em"/></math>

其中 *p*(.) 表示概率密度函数 (pdf)，*p*[*ref*] 为参考分布。当 IC 包含 OA 时，其 pdf 与参考 IC 的 pdf 之间的 KL 距离将近似为零，而与正常 EEG 信号 pdf 之间的 KL 距离则会更大。

随后，使用带有 RBF 非线性核的 SVM 根据上述特征对 IC 进行分类。据报道，EOG IC 的检测准确率高达 99% [[98]](#c17.xhtml#c17-bib-0098)。

标记伪迹信号后，将其置零。然后，将所有估计源重新投影到头皮电极，以重建无伪迹的 EEG 信号。

同样的思路已被直接用于从 EEG 中提取运动相关特征 [[99]](#c17.xhtml#c17-bib-0099)。该研究声称，无需任何长期训练，即可通过 BSS 后接分类器，判断某手指是否存在运动。采用改进的遗传算法 (GA) 与 SVM 分类器相结合的方法，对选定特征进行调节和分类。

## 17.4 多维 EEG 分解

所有运动相关电位在持续时间和频率上均受限。此外，每个通道均包含 EEG 数据的空间信息。PCA 和 ICA 已广泛用于 EEG 多传感器记录的分解。然而，高效的数据分解需要融合空间、时间和频率维度。

时频 (TF) 分析利用了时间和频率两个维度的变化。大多数脑信号均可在 TF 域中分解。这更好地体现为 EEG 源在 TF 域中的稀疏性。此外，TF 域特征对神经活动的描述性更强。例如在 [[100]](#c17.xhtml#c17-bib-0100) 中，已确定受试者特定频带的特征，并使用 LDA 进行分类。

在一种更通用的方法中，空间信息也被纳入考量。这是因为大多数事件定位于不同的大脑区域。作为一种有利的方法，EEG 的联合时空频分类已被研究用于 BCI 应用 [[39](#c17.xhtml#c17-bib-0039), [101](#c17.xhtml#c17-bib-0101)]。在该方法中，EEG 信号参考“数字连接耳垂”(DLE) 进行测量。DLE 电压可通过左右耳垂轻松求得，公式如下：

(17.6)![equation](images/c17-disp-0006.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><msubsup><mi>V</mi><mi>e</mi><mi mathvariant="italic">DLE</mi></msubsup><mo>=</mo><msub><mi>V</mi><mi>e</mi></msub><mo>&#8722;</mo><mfrac><mn>1</mn><mn>2</mn></mfrac><mfenced open="(" close=")"><mrow><msub><mi>V</mi><msub><mi>A</mi><mn>1</mn></msub></msub><mo>+</mo><msub><mi>V</mi><msub><mi>A</mi><mn>2</mn></msub></msub></mrow></mfenced><mspace width="0.2em"/></math>

其中 ![images](images/c17-i0002.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msub><mi>V</mi><msub><mi>A</mi><mn>1</mn></msub></msub><mtext>and</mtext><mspace width="0.2em"/><msub><mi>V</mi><msub><mi>A</mi><mn>2</mn></msub></msub></math> 分别为左、右耳垂参考电压。因此，多变量 EEG 信号由各电极的 DLE 信号组成。之所以称为多变量信号，是因为它们由来自多个源的信号组成。在剔除受眨眼伪迹污染的片段后 [[39]](#c17.xhtml#c17-bib-0039)，已对多变量信号进行分解以得到单变量分类。

有多种方式可书写用于分类目的的 TF 分布一般类别 [[102]](#c17.xhtml#c17-bib-0102)。在上述工作中，单通道 EEG 信号 *x*(*t*) 的特征函数 (CF) *M*(*θ*, *τ*) 定义如下（假设为连续时间，实际中可使用离散化版本）：

(17.7)![equation](images/c17-disp-0007.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>C</mi><mfenced open="(" close=")"><mrow><mi>t</mi><mo>,</mo><mi>&#969;</mi></mrow></mfenced><mo>=</mo><mfrac><mn>1</mn><mrow><mn>4</mn><msup><mi>&#960;</mi><mn>2</mn></msup></mrow></mfrac><msubsup><mo>&#8747;</mo><mrow><mi>&#964;</mi><mo>=</mo><mo form="postfix">&#8722;</mo><mo>&#8734;</mo></mrow><mo>&#8734;</mo></msubsup><msubsup><mo>&#8747;</mo><mn>0</mn><mrow><mn>2</mn><mi>&#960;</mi></mrow></msubsup><mi>M</mi><mfenced open="(" close=")"><mrow><mi>&#952;</mi><mo>,</mo><mi>&#964;</mi></mrow></mfenced><msup><mi>e</mi><mrow><mo form="prefix">&#8722;</mo><mi mathvariant="italic">j&#952;t</mi><mo>&#8722;</mo><mi mathvariant="italic">j&#964;&#969;</mi></mrow></msup><mtext mathvariant="italic">d&#952;d&#964;</mtext></math>

(17.8)![equation](images/c17-disp-0008.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>M</mi><mfenced open="(" close=")"><mrow><mi>&#952;</mi><mo>,</mo><mi>&#964;</mi></mrow></mfenced><mo>=</mo><mi>&#966;</mi><mfenced open="(" close=")"><mrow><mi>&#952;</mi><mo>,</mo><mi>&#964;</mi></mrow></mfenced><mi>A</mi><mfenced open="(" close=")"><mrow><mi>&#952;</mi><mo>,</mo><mi>&#964;</mi></mrow></mfenced></math>

其中
