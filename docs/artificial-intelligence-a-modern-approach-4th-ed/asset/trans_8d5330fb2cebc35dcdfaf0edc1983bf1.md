
$\\begin{array}{l} {\\mathbf{P}(P\_{1,1},\\ldots,P\_{4,4},B\_{1,1},B\_{1,2},B\_{2,1})\\ =} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\mathbf{P}\\text{(}B\_{\\text{1,1}}\\text{,}\\, B\_{\\text{1,2}}\\text{,}\\, B\_{\\text{2,1}}\\text{~|~}P\_{\\text{1,1}}\\text{,}\\ldots\\text{,}P\_{\\text{4,4}}\\text{)}\\mathbf{P}\\text{(P}\_{\\text{1,1}}\\text{,}\\ldots\\text{,}P\_{\\text{4,4}}\\text{)~}\\text{.}} \\\\ \\end{array}$

这种分解使得联合概率值应该是什么变得容易看出。第一项是给定坑配置的微风配置的条件概率分布；如果所有有微风的方格都与坑相邻，则其值为 1，否则为 0。第二项是坑配置的先验概率。每个方格以概率 0.2 包含一个坑，与其他方格独立；因此，

$\\begin{matrix} {\\mathbf{P}(P\_{1,1},\\ldots,P\_{4,4}) = {\\prod\\limits\_{\\text{i},\\ j = \\text{1,1}}^{4,4}{\\mathbf{P}(P\_{i,j}).}}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(12}\\text{.22)}} \\\\ \\end{matrix}$

对于恰好有 n 个坑的特定配置，其概率为 0.2^n × 0.8^{6-n}。

在 [图 12.5(a)](#Chapter12-07.xhtml#fig12-5) 的情况下，证据包括每个被访问方格中观察到的微风（或其缺失），以及每个此类方格不包含坑的事实。我们将这些事实简写为 `b = ¬b[1,1] ∧ b[1,2] ∧ b[2,1]` 和 `known = ¬p[1,1] ∧ ¬p[1,2] ∧ ¬p[2,1]`。我们有兴趣回答诸如 `P(P1,3 | known, b)` 这样的查询：鉴于迄今为止的观察，\[1,3\] 包含一个坑的可能性有多大？

要回答此查询，我们可以遵循 [方程 (12.9)](#Chapter12-03.xhtml#eq12-9) 的标准方法，即对完整联合分布的条目求和。令 `Unknown` 为除已知方格和查询方格 \[1,3\] 之外的方格的 `Pi,j` 变量集合。然后，根据 [方程 (12.9)](#Chapter12-03.xhtml#eq12-9)，我们有

$\\begin{matrix} \\left. \\mathbf{P}(P\_{1,3} \\middle| known,b\\text{)~=~}\\alpha{\\sum\\limits\_{unknown}{\\mathbf{P}\\text{(}P\_{\\text{1,3}}\\text{,}known,b,unknown\\text{)}\\text{.}}} \\right. & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\text{(12}\\text{.23)}} \\\\ \\end{matrix}$

完整的联合概率已经指定，因此我们完成了——也就是说，除非我们关心计算。有 12 个未知方格；因此求和包含 2^12 = 4096 项。一般来说，求和随着方格数量呈指数增长。

当然，有人可能会问，其他方格不是无关紧要的吗？\[4,4\] 如何影响 \[1,3\] 是否有坑？事实上，这种直觉大致是正确的，但需要更精确地表述。我们真正的意思是，如果我们知道我们关心的方格相邻的所有坑变量的值，那么其他更远方格中的坑（或其缺失）就不会对我们的信念产生进一步影响。

令 `Frontier` 为与已访问方格相邻的坑变量（不包括查询变量），在本例中仅为 \[2,2\] 和 \[3,1\]。此外，令 `Other` 为其他未知方格的坑变量；在本例中，有 10 个其他方格，如 [图 12.5(b)](#Chapter12-07.xhtml#fig12-5) 所示。有了这些定义，`Unknown = Frontier∪Other`。上面给出的关键见解现在可以表述如下：观察到的微风在给定已知、前沿和查询变量的情况下，与其他变量条件独立。为了利用这一见解，我们将查询公式操作成微风以所有其他变量为条件的形式，然后应用条件独立性：

$\\begin{array}{l} \\left. \\mathbf{P}(P\_{1,3} \\middle| known,b\\text{)} \\right. \\\\ {\\,\\,\\,\\,\\text{~=~}\\alpha{\\sum\\limits\_{unknown}{\\mathbf{P}\\text{(}P\_{\\text{1,3}}\\text{,}known,b,unknown\\text{)}\\,\\,\\,\\,\\,\\,\\,\\,\\text{(from~Equation~(12}\\text{.23))}}}} \\\\ {\\,\\,\\,\\,\\,\\text{~=~}\\alpha{\\sum\\limits\_{unknown}\\left. \\mathbf{P}\\text{(}b \\middle| P\_{\\text{1,3}}\\text{,}known,unknown\\text{)}\\mathbf{P}\\text{(}P\_{\\text{1,3}}\\text{,}known,unknown\\text{)~(}product\\ rule\\text{)} \\right.}} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\text{~=~}\\alpha{\\sum\\limits\_{frontier}{\\sum\\limits\_{other}\\left. \\mathbf{P}\\text{(}b \\middle| known,P\_{\\text{1,3}},frontier,other\\text{)}\\mathbf{P}\\text{(}P\_{\\text{1,3}}\\text{,}known,\\ frontier,\\ other\\text{)~} \\right.}}} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\text{~=~}\\alpha{\\sum\\limits\_{frontier}{\\sum\\limits\_{other}\\left. \\mathbf{P}\\text{(}b \\middle| known,P\_{\\text{1,3}},frontier\\text{)}\\mathbf{P}\\text{(}P\_{\\text{1,3}}\\text{,}known,\\ frontier,\\ other\\text{)~}, \\right.}}} \\\\ \\end{array}$

其中最后一步使用了条件独立性：b 在给定 known、P1,3 和 frontier 的情况下与 other 独立。现在，该表达式中的第一项不依赖于 Other 变量，因此我们可以将求和向内移动：

$\\begin{array}{l} \\left. \\mathbf{P}\\text{(}P\_{\\text{1,3}} \\middle| \\,\\, known\\text{,}\\, b\\text{)} \\right. \\\\ {\\,\\,\\,\\,\\text{~=~}\\alpha{\\sum\\limits\_{frontier}\\left. \\mathbf{P}\\text{(}b \\middle| known,p\_{1,3},frontier\\text{)}\\,{\\sum\\limits\_{other}{\\mathbf{P}(P\_{1,3},known,\\ frontier,\\ other).}} \\right.}} \\\\ \\end{array}$

根据独立性，如 [方程 (12.22)](#Chapter12-07.xhtml#eq12-22) 所示，右侧的项可以分解，然后重新排序：

$\\begin{array}{l} \\begin{array}{l} \\left. \\mathbf{P}\\text{(}P\_{\\text{1,3}} \\middle| \\,\\, known\\text{,}\\, b\\text{)} \\right. \\\\ {\\,\\,\\,\\,\\text{~=~}\\alpha{\\sum\\limits\_{frontier}\\left. \\mathbf{P}\\text{(}b \\middle| known,p\_{1,3},frontier\\text{)}\\,{\\sum\\limits\_{other}{\\mathbf{P}(P\_{1,3})P(known)P(\\ frontier)P(other)}} \\right.}} \\\\ \\end{array} \\\\ {\\,\\,\\,\\,\\,\\, = \\alpha P(know)\\mathbf{P}(P\_{1,3}){\\sum\\limits\_{frontier}\\left. \\mathbf{P}\\text{(}b \\middle| known,p\_{1,3},frontier\\text{)}\\, P(frontier){\\sum\\limits\_{other}{P(other)}} \\right.}} \\\\ {\\,\\,\\,\\,\\, = \\alpha^{\\prime}\\mathbf{P}(P\_{1,3}){\\sum\\limits\_{frontier}\\left. \\mathbf{P}\\text{(}b \\middle| known,p\_{1,3},frontier\\text{)}\\, P(frontier). \\right.}} \\\\ \\end{array}$

其中最后一步将 P(known) 折入归一化常数，并利用 ∑[*o**t**h**e**r*] P(other) 等于 1 的事实。

现在，前沿变量 `P2,2` 和 `P3,1` 的求和中只有四个项。独立性和条件独立性的使用已完全消除了其他方格的考虑。

请注意，`P(b | known, P1,3, frontier)` 中的概率在微风观察与其它变量一致时为 1，否则为 0。因此，对于 `P1,3` 的每个取值，我们对与已知事实一致的前沿变量的逻辑模型求和。（与 [图 7.5](#Chapter07-03.xhtml#fig7-5) 中对模型的枚举进行比较，见 [第 233 页](#Chapter07-03.xhtml#page_233)。）模型及其相关的先验概率——`P(frontier)`——显示在 [图 12.6](#Chapter12-07.xhtml#fig12-6) 中。我们有

描述
