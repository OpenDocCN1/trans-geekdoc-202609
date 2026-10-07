

公理化、社会科学与哥德尔现象：工具箱 83

- 我们对图灵机使用二进制编码，该编码在它们的表格长度上也是单调的，且线性排列，即一个 3 行表格 $s1, s2, s3$ 变为行 $s1s2s3$。我们称此类单调编码为*标准编码*。

- 我们考虑所有处于 cnf（合取范式）的布尔表达式集合，包括那些不可满足或完全为假的表达式。我们赋予它通常编码，它是到 $\omega$ 的单双射。

- 考虑多项式图灵机 $V(x, s)$，当仅当真值行 $s$ 满足布尔 cnf 表达式 $x$ 时，$V(x, s) = 1$；如果 $s$ 不满足 $x$，则 $V(x, s) = 0$。

- 考虑 BGS（见 Baker *et al.*, 1975）机的枚举，$P_0, P_1, P_2, \dots$

我们从 $x$ 开始，即 cnf 形式布尔表达式的二进制编码：

- 考虑 $x$ 与 $P_0, P_1, P_2, \dots$ 直到第一个 $P_j$，使得 $P_j(x) = s_j$ 且 $s_j$ 满足 $x$（即对于验证机 $V(x, s_j) = 1$）。

- 注意存在一个界 $\leq j = f^{-1}(x)$。

这需要一些详细说明。最终，一个多项式机（在 BGS 序列中）将在输入为 $x$ 时产生一个满足条件的行。具有该能力的机器的上界由第一个 BGS 索引给出，此时 $x$ 的编码小于反例函数索引处的值。这意味着：我们得到了一个机器 $M_n$，它输出一个直到 $x$ 输入的正确行，然后开始输出错误的解。

- 或者，检查 $V(x,0), V(x,1) \dots$ 直到——如果发生的话——某个 $s$ 使得 $V(x,s) = 1$；或者，

¹⁷ 合取范式。
¹⁸ 请记住 BGS 机器集是一组时间多项式图灵机，包含了模拟所有时间多项式图灵机的算法。见上文并检查（见 Baker *et al.*, 1975）。

# 社会科学中数学建模的局限

- 如果 $f_c$ 是快速增长的，由于 $P_j$ 的操作时间受限于 $|x|^k+k$，我们得到 $k \leq j$，因此它以 $O(f_c^{-1}(x))$ 的速度增长。这将是一个增长非常缓慢的函数。BGS 机器由一对对 $\langle m,k \rangle$ 编码，其中 $m$ 是图灵机哥德尔索引，$k$ 如上。因此，只要我们使用单调编码，我们在所有图灵机中编码 BGS 机器的索引 $j$ 将大于 $k$。更精确地说，它必须测试到 $j$，即操作时间将受到 $f_c^{-1}(x)(|f_c^{-1}(x)|+f_c^{-1}(x))$ 的限制。再次注意 BGS 索引 $j \geq k$，其中 $k$ 是多项式机的次数。

## 附录 K。几乎高效的市场

更多关于几乎高效市场的讨论。对于一个具有足够算术性——我们在此不作模糊处理——且具有递归可枚举定理集合的理论 $S$，对于任何可证明的全全函数 $h$，都存在一个递归全函数 $g$ 使其增长速度超过 $h$。现在假设我们猜想：形式句子 $P < NP$ 没有通过初等算术证明。那么，反例函数 $f$ 的增长阶至少是阿克曼函数的阶。在该条件下，我们可以说明：

### 命题 K.1. 如果 $P < NP$ 没有通过初等算术证明，则存在几乎高效的市场。

## 附录 L。一个疯狂的想法：基数？

我们猜想：某些快速增长函数的存在取决于不可及基数。回想不可及基数 $\lambda$ 满足：

- (1) $\lambda > \omega$。
- (2) 如果 $\alpha$ 是基数且 $\alpha < \lambda$，则 $2^\alpha < \lambda$。
- (3) 对于每一个族 $\eta_i, i \in \iota, \iota < \lambda$，且对于每个 $i$， $\eta_i < \lambda$，则 $\sup(\eta_i) < \lambda$。

$Consis(T)$ 意味着（通常的）断言理论 $T$ 一致的句子$Card(\lambda)$ 意味着 $\lambda$ 是一个基数，让 $Inac(\lambda)$ 对于理论 $T$，$\lambda$ 是不可及的。最后，$F$ 为出现在奇异表述中的快速增长部分函数：

### 命题 L.1. 存在 $\lambda_F$ 使得：$(ZFC + [F \text{ is total}]) \vdash Card(\lambda) \wedge Inac_{ZFC}(\lambda)$。证明草拟，待完善。

- (1) 由于我们假设 $Consis(ZFC + [F \text{ is total}])$ 成立，因此它有一个模型 $M$。
- (2) 现在，$ZFC + [F \text{ is total}] \vdash Consis(ZFC)$。
- (3) ZFC 的一个定理证明是：$Consis(ZFC) \leftrightarrow \exists x[x \models ZFC]$。（我们也可以将其视作 $Consis(T)$ 的定义）。
- (4) 给定 $ZFC + [F \text{ is total}] \vdash Consis(ZFC)$，存在一个集合 $x \in M$ 是 ZFC 的模型。
- (5) 写作 $V_\lambda = M - x$。
- (6) 由于 $V_\lambda$ 非空且选择公理成立，其中存在序数。
- (7) 因此，在 $V_\lambda$ 中至少有一个基数。
- (8) 选取这些基数中最小的一个；注意：$\lambda$：可以看出对于每个基数 $\alpha \in V$，$\lambda$ 都不同于 $2^\alpha$。对于序列 $\eta_i$，$\lambda$ 也不同于 $\sup \eta_i$。（如果这两个条件不成立，$\lambda$ 将属于 $V$。）
- (9) 最后，对于所有 $\alpha \in V, \lambda > \alpha$。如果不是，则存在 $\beta \in V, \lambda$ 将在 $V$ 中。

这意味着 $V$ 实际上是某个集合。这个论证并没有证明某个特定的 $\lambda$ 证明了 $P < NP$，它只是证明（或声称证明了）$ZFC + [F \text{ is total}]$ 意味着不可及基数的存在。我们现在得到了 $\lambda \leq f^*(\aleph_0)$。

# 参考文献

- Abraham, R. and Marsden, J. (1978). *Foundations of Mechanics*. Addison-Wesley.
- Adler, A. (1969). 分析中的某些不可解问题。*Proceedings of the American Society*, **22**, 523–526.
- Arnold, V. I. (1976). 数学问题 XVII（动力系统与方程）。*Proceedings of Pure Mathematics*, **28**, 59.
- Ash, C. J. and Knight, J. (2000). *Computable Structures and the Hyperarithical Hierarchy*.
- Baker, T. and Solovay, R. (1975). $P = NP$ 问题的相对化。*SIAM Journal on Computing*, **4**, 431–442.
- Balzer, W., Moulines, C. and Sneed, J. D. (1987). *Architectonic for the Structuralist Program*. Synthèse Library, D. Reidel.
- Black, M. (1993). *The Nature of Mathematics*, London.
- Ben-David, S. and Halevy, S. (s/d). 关于 $P$ vs. $NP$ 的独立性。Technion 预印本。
- Chaitin, J. J., Costa, N. C. A. and Doria, F. A. (2011). *Gödel's Wave*. CRC Press.
- Cho, Y. M. (1975). 引力和规范场的高维统一。*Journal of Mathematical Physics*, **16**, 2029–2037.
- Corson, E. M., (1953). *Introduction to Sensors, Tensors and Relativistic Wave-Equations*. Blackie & Sons.
- Costa, N. C. A. (1980). Ensaio sobre Fundamentos da Lógica. São Paulo: Hucitet-Edusp.
- Costa, N. C. A. and Chuaqui, R. (1988). On Suppes' set-theoretic predicates. *Erkenntnis*, **29**, 95–112.
- Costa, N. C. A. and Doria, F. A. (2007). 关于 $P$ vs. $NP$ 问题的元数学研究。*Applied Mathematics and Computation*, **189, 1223–1240.
