
设 `H`=`C²`，并考虑态矢 `|z>`=`1/(2 ^(1/2))` ⋅![Equation](Images/F000205si33.png) (`|0>` +i ⋅![Equation](Images/F000205si34.png)`|1>`)；目标是找到与该 `H` 中简单元素对应的纯态映射 `ρ[z]`![Equation](Images/F000205si35.png)。利用伴矢：`<z|`=`1/(2 ^(1/2))` ⋅![Equation](Images/F000205si36.png) (`<0|` + − i ⋅![Equation](Images/F000205si37.png) `<1|`)，则 `<z, z>`=1，且 `ρ[z]`![Equation](Images/F000205si38.png) 是一个纯态。现在将选取 `H` 的另一个简单元素，并观察 `|u>` 在 `ρ[z]`![Equation](Images/F000205si39.png) 下的像。设 `|u>`=`1/(2 ^(1/2))` ⋅![Equation](Images/F000205si40.png) (`|0>` + − 1 ⋅![Equation](Images/F000205si41.png) `|1>`)，因为内积为 `<z, u>`=(1+ i)/2；由此可得 `ρ[z]`![Equation](Images/F000205si42.png)(`u`)=((1+ i)/2) ⋅![Equation](Images/F000205si43.png) `|z>`=((1+ i)/((2)^(3/2))) ⋅![Equation](Images/F000205si44.png) (`|0>` + i ⋅![Equation](Images/F000205si45.png) `|1>`)=(2 ^(1/2) `e`^( `i` `π`/4)![Equation](Images/F000205si46.png)/((2)^(3/2))) ⋅![Equation](Images/F000205si47.png) (`|0>` + i ⋅![Equation](Images/F000205si48.png) `|1>`)=1/2 ⋅![Equation](Images/F000205si49.png) (`|0>` + i ⋅![Equation](Images/F000205si50.png) `|1>`).

以下为第 4.10 节中的等式恒等式。它们在描述纠缠和非纠缠时是必需的，如下所述。

希尔伯特空间张量积的等式恒等式：

1. 1) 线性：`c x (v1 ⊗ v2)`=`(c x v1) ⊗ v2`=`v1 ⊗ (c x v2)`.
2. 2) 分配律：`(v1 + w1) ⊗ w2`=`v1 ⊗ w2 + w1 ⊗ v2`.
3. 3) 分配律：`v1 ⊗ (v2 + w2)`=`v1 ⊗ v2 + v1 ⊗ w2`.
4. 4) 内积：`< v1 ⊗ v2, w1 ⊗ w2 >`=`<v1, w1> <v2, w2>`.

纯态 `ρ[z]`![Equation](Images/F000205si61.png) 在希尔伯特空间 `H1 ⊗ H2` 中被称为非纠缠，这意味着存在在 `H1` 中作用的纯态 `ρ[v]`![Equation](Images/F000205si62.png) 和在 `H2` 中作用的纯态 `ρ[w]`![Equation](Images/F000205si63.png)，使得张量积：`ρ[v]⊗ρ[w]` = `ρ[z]`![Equation](Images/F000205si65.png)。一个最重要的事实是，纯态 `ρ[z]`![Equation](Images/F000205si66.png) 是非纠缠的当且仅当对于 `H1` 中的 `v` 和 `H2` 中的 `w`，有 `z`=`v ⊗ w`，即当 `z` 是 `H1 ⊗ H2` 的一个简单元素时。这可以通过参考希尔伯特空间张量积的定义来看到。利用等式恒等式：4) 内积，其中 `v1` 和 `w1` 在 `H1` 中，`v2` 和 `w2` 在 `H2` 中；则该恒等式为 `<v1 ⊗ v2, w1 ⊗ w2>`=`<v1, w1> <v2, w2>`，于是将其应用于纯态：`ρ[z]`=(<z, ->/<z, z>) `z`=(<v ⊗ w, ->/< v ⊗ w, v ⊗ w>) `v ⊗ w`=(<v, ->/<v, v>) (<w, ->/<w, w>) `v ⊗ w`。然后利用希尔伯特空间张量定义中的 1) 线性重新排列：(<v, ->/<v, v>) `v` ⊗ (<w, −>/<w, w>) `w`=`ρ[v]`![Equation](Images/F000205si77.png) ⊗ `ρ[w]`![Equation](Images/F000205si79.png)。

可以看出，纯态 `ρ[z]`![Equation](Images/F000205si80.png) 在希尔伯特空间 `H1 ⊗ H2` 中被称为纠缠，这意味着不存在在 `H1` 中作用的纯态 `ρ[v]`![Equation](Images/F000205si82.png) 和在 `H2` 中作用的纯态 `ρ[w]`![Equation](Images/F000205si83.png)，使得张量积 `ρ[v]⊗ρ[w]` = `ρ[z]`![Equation](Images/F000205si85.png) 成立。混合态当且仅当它不能写成形如 `ρ[z]` = `ρ[v]⊗ρ[w]`![Equation](Images/F000205si87.png) 的纯态的凸组合时才是纠缠的。在下一个例子中，我们将展示希尔伯特空间中元素的张量积如何产生希尔伯特空间上的非纠缠态。

### 例 7.11

作为 `H1 ⊗ H2` 中非纠缠纯态 `ρ[z]`![Equation](Images/F000205si88.png) 的例证，考虑 `ρ[u]`![Equation](Images/F000205si90.png) 和 `ρ[v]`![Equation](Images/F000205si91.png) 均为纯态，分别在 `H1`=`H2`=`C²` 中。假设 `ρ[z]` = `ρ[u]`![Equation](Images/F000205si92.png) ⊗ `ρ[v]`![Equation](Images/F000205si94.png)，且 `|u>`=(1/(1.414)) ⋅![Equation](Images/F000205si95.png) (`|0>` + `|1>`)，而 `|v>`=(0.8 x `|0>` −0.6 x `|1>`)，其中 `|u>` 在 `H1` 中，`|v>` 在 `H2` 中。两个元素都是简单的，张量积 `|z>`= `|u> ⊗ |v>`=(1/(1.414)) ⋅![Equation](Images/F000205si97.png) (0.8 ⋅![Equation](Images/F000205si98.png) `|0, 0>` +0.8 ⋅![Equation](Images/F000205si99.png) `|1, 0>` −0.6 ⋅![Equation](Images/F000205si100.png) `|0, 1>` −0.6 ⋅![Equation](Images/F000205si101.png) `|1, 1>`) 在 `H1 ⊗ H2` 中也是简单的。这表明纯态 `ρ[z]`![Equation](Images/F000205si102.png) 是非纠缠的。 recall that the tensor is called pure iff `a11 a22`=`a12 a21`；否则，它是纠缠的。注意当这表示为 `C²` 中的向量时，可得 `|z>`=`|u> ⊗ |v>`=(1/(1.41)) ⋅![Equation](Images/F000205si104.png) (0.8 ⋅![Equation](Images/F000205si105.png) (1 0 0 0)′ +0.8 ⋅![Equation](Images/F000205si106.png) (0 0 1 0)′ −0.6 ⋅![Equation](Images/F000205si107.png) (0 1 0 0)′ −0.6 ⋅![Equation](Images/F000205si108.png) (0 0 0 1)′)=

$\\begin{matrix} \\left( {1/1.41} \\right) & \\begin{matrix} \\left| .8 \\right| \\\\ \\left| - .6 \\right| \\\\ \\left| .8 \\right| \\\\ \\left| - .6 \\right| \\\\ \\end{matrix} \\\\ \\end{matrix}.$

![Equation](Images/F000205si109.png)

`| z >` 的范数为 1。

对于希尔伯特空间 `H1 ⊗ H2` 中的 `z`，系数归一化时，`|a11|² + |a12|² + |a21|² + | a22 |²`=1，将 `ajk` 项替换为实部加 i 乘虚部得到七维球 `S⁷` 的方程。从前一节可知，单量子比特希尔伯特空间是 `S³`，因此双量子比特希尔伯特空间是 `S⁷`。Hopf 纤维化更详细地描述了这些球面。接下来，更一般地描述迹类算子。随后，这些算子被证明与希尔伯特-施密特算子密切相关。

## 7.5 跡类算子

迹类算子将迹运算从方阵推广到无限维。这些算子定义在希尔伯特空间上，所有迹类算子的集合构成一个巴拿赫空间。它们与紧算子空间以及有界算子空间密切相关。事实上，迹类算子的对偶空间是有界算子空间。此外，紧算子的对偶空间是迹类算子空间（[Argerami, 2014](#Ch007_131-144_B9780443136979000205.xhtml#bib1)）。

对于希尔伯特空间 `H` 上的线性算子 `T`，`T` 的迹是形如 `<ek, T ek>` 的内积之和的级数，其中 `{ek}` 是 `H` 的一个标准正交基。对于无限维希尔伯特空间，该级数必须收敛。通常，它是部分和序列的极限。在这种情况下，它记为 `Tr (T)`，结果必须与基无关。再次，要成为迹类，迹必须无论采用何种基都是有限的，并且定义和的所有极限必须相等。

### 例 7.12
