
在理想情况下，对于 `i ≠ j` 有 `a[ji] = 0`。最小化 `l0` 范数（即非零样本的数量），在大多数情况下通过 `l1` 范数（非零样本绝对值之和）来近似，是估计源信号最合乎逻辑的方法之一。`l1` 范数最小化是一种分段线性运算，它将 `x(n)` 的能量部分分配给矩阵 `A` 的 `M` 个列向量，这些列向量在 ℜ^M 空间中形成一个包围 `x(n)` 的锥体。剩余的 `N-M` 个列向量被分配零系数。因此，`l1` 范数最小化可以表现为：

[(5.33)](#c05.xhtml#R_c5-disp-0037)![equation](images/c5-disp-0037.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><munder><mo mathvariant="bold">min</mo><mi mathvariant="bold">s</mi></munder><msub><mfenced open="&#8214;" close="&#8214;"><mrow><mi mathvariant="bold">s</mi><mfenced open="(" close=")"><mi mathvariant="bold-italic">n</mi></mfenced></mrow></mfenced><mn mathvariant="bold">1</mn></msub><mspace width="0.2em"/><mtext mathvariant="bold">subject to</mtext><mspace width="0.2em"/><mi mathvariant="bold">As</mi><mfenced open="(" close=")"><mi mathvariant="bold-italic">n</mi></mfenced><mo>=</mo><mi mathvariant="bold">x</mi><mfenced open="(" close=")"><mi mathvariant="bold-italic">n</mi></mfenced></math>

Takigawa 等人 [\[21\]](#c05.xhtml#c5-bib-0021) 详细讨论了使用 `l1` 范数最小化进行信号恢复的方法。

基追踪、平滑 `l0` [\[161\]](#c05.xhtml#c5-bib-0161)、聚焦欠定系统求解器 (FOCUSS) 和正交匹配追踪 (OMP) 等多种方法被用来近似以下问题的解：![images](images/c5-i0023.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><munder><mo mathvariant="bold">min</mo><mi mathvariant="bold">s</mi></munder><msub><mfenced open="&#8214;" close="&#8214;"><mrow><mi mathvariant="bold">s</mi><mfenced open="(" close=")"><mi mathvariant="bold-italic">n</mi></mfenced></mrow></mfenced><mn mathvariant="bold">0</mn></msub><mspace width="0.2em"/><mtext mathvariant="bold">subject to</mtext><mspace width="0.2em"/><mi mathvariant="bold">As</mi><mfenced open="(" close=")"><mi mathvariant="bold-italic">n</mi></mfenced><mo>=</mo><mi mathvariant="bold">x</mi><mfenced open="(" close=")"><mi mathvariant="bold-italic">n</mi></mfenced></math>。下一小节将简要解释最流行的方法。

### 5.4.1 稀疏源恢复的标准算法

流行的方法中包括贪婪算法家族，它们关注支撑集，然后使用简单的最小二乘法获得 `s` 的非零值。由于支撑集的离散性质，贪婪算法大多是离散的。相比之下，另一类算法，即松弛算法家族，试图用连续信号来近似稀疏信号，并采用连续优化过程。

#### 5.4.1.1 基于贪婪的解法

Mallat 和 Zhang [\[159\]](#c05.xhtml#c5-bib-0159) 引入了一种用于稀疏分解的贪婪方法，称为匹配追踪 (MP)。他们证明了当字典（混合矩阵）是正交的且观测信号由 `k << n` 个原子组成时，该算法在 `n` 步后精确恢复源信号 [\[163\]](#c05.xhtml#c5-bib-0163)。实际上，MP 基于对混合矩阵的次优前向搜索。后续的贪婪算法，如 OMP [\[164\]](#c05.xhtml#c5-bib-0164) 和压缩采样匹配追踪 (CoSaMP) [\[165\]](#c05.xhtml#c5-bib-0165)，均基于 MP 的概念。OMP 方法选择与残差相关性最大的列，事实上，这也是导致残差下降最陡峭的那一列，这意味着 OMP 是贪婪的。

回顾 `x = As`，其中 `s` 是一个 `k` 稀疏信号。由于 `k` 稀疏信号的非零系数数量等于 `k`，如果确定了这些系数的位置，就可以通过求逆或伪求逆 `A` 中对应的 `m × k` 子矩阵来找到非零值。这是算法中最复杂的部分。在 OMP 算法中，非零位置是逐个找到的。首先，`x` 的某一行与 `A` 的某一列具有最高的归属度（关联度），这为该列是支撑集提供了最大似然性。为了找到支撑集的其他成员，恢复的信号（及相关列）被通缩。此过程重复进行，直到估计出支撑集的其他成员。

#### 5.4.1.2 基于松弛的解法

松弛方法通过用其他函数或范数来近似，从而平滑 `l0` 范数。

给定 `ρ[α](s) ≈ ‖s‖[0]`，例如，`ρ[α](s)` 可以是 ![images](images/c5-i0024.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msub><mi mathvariant="normal">&#961;</mi><mi>&#945;</mi></msub><mfenced open="(" close=")"><mi>s</mi></mfenced><mo>=</mo><mn>1</mn><mo form="postfix">&#8722;</mo><mo>exp</mo><mfenced open="(" close=")"><mrow><mo form="prefix">&#8722;</mo><mfrac><msup><mi>s</mi><mn>2</mn></msup><mi>&#945;</mi></mfrac></mrow></mfenced></math>、![images](images/c5-i0025.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="inline" overflow="scroll"><msub><mi mathvariant="normal">&#961;</mi><mi>&#945;</mi></msub><mfenced open="(" close=")"><mi>s</mi></mfenced><mo>=</mo><mfrac><msup><mi>s</mi><mn>2</mn></msup><mrow><msup><mi>s</mi><mn>2</mn></msup><mo>+</mo><mi>&#945;</mi></mrow></mfrac></math> 或 `ρ[α](s) = |s|^(α)`。当 `α` 趋近于零时，这些函数更接近 `l0` 范数。值得注意的是，这些函数作用于源向量的元素，最终范数根据以下公式计算（[式 5.34](#c05.xhtml#c5-disp-0038)）：

[(5.34)](#c05.xhtml#R_c5-disp-0038)![equation](images/c5-disp-0038.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><mi>f</mi><mfenced open="(" close=")"><mi mathvariant="bold">s</mi></mfenced><mo>=</mo><munderover><mo>&#8721;</mo><mrow><mi>q</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msub><mi mathvariant="normal">&#961;</mi><mi>&#945;</mi></msub><mfenced open="(" close=")"><msub><mi>s</mi><mi>q</mi></msub></mfenced></math>

其中 `s[q]` 和 `f(s)` 分别指 `s` 的第 `q` 个元素和平滑范数。该家族中一种流行的算法是 FOCUSS [\[171\]](#c05.xhtml#c5-bib-0171)。FOCUSS 采用一种称为迭代递加权最小二乘法 (IRLS) 的优化方法。基于此概念，平滑 `l0` 范数 (`ρ[α](s)`) 被构建为加权 `l2` 范数，如下所示：

(5.35)![equation](images/c5-disp-0039.png)<math xmlns="http://www.w3.org/1998/Math/MathML" display="block" overflow="scroll"><munderover><mo>&#8721;</mo><mrow><mi>q</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msub><mi mathvariant="normal">&#961;</mi><mi>&#945;</mi></msub><mfenced open="(" close=")"><msub><mi>s</mi><mi>q</mi></msub></mfenced><mo>&#8594;</mo><munderover><mo>&#8721;</mo><mrow><mi>q</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><mfrac><mrow><msub><mi mathvariant="normal">&#961;</mi><mi>&#945;</mi></msub><mfenced open="(" close=")"><msub><mi>s</mi><mi>q</mi></msub></mfenced></mrow><msubsup><mi>s</mi><mi>q</mi><mn>2</mn></msubsup></mfrac><msubsup><mi>s</mi><mi>q</mi><mn>2</mn></msubsup><mo>=</mo><munderover><mo>&#8721;</mo><mrow><mi>q</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msub><mi>w</mi><mi>q</mi></msub><msubsup><mi>s</mi><mi>q</mi><mn>2</mn></msubsup></math>
