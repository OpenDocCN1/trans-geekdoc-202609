
**证明**：设 `m = m[1] ⋅ m[2] ⋅ … ⋅ m[r]`，则 `(m/m[j], m[j]) = 1`。设 `R(m[j])` 表示模 `m` 的简化剩余系，它包含所有与 `m[j]` 互素的元素集合。因此，`∀ a ∈ R(m[j]), ∃ x ∈ R(m[j]) : a*x ≡ 1 (mod m[j])`，这意味着，`∃ b[j] ∈ R(m[j]) : (m/m[j]) * b[j] ≡ 1 (mod m[j])`。设 `x[0]` 为一个解，则 `x[0] = ∑(j=1 to r) ((m/m[j]) ⋅ b[j] ⋅ a[j] mod m[j])`，因为 `((m/m[j]) ⋅ b[j] ⋅ a[j]) ≡ a[j] (mod m[j])`。

### 1.1.6 二次剩余

如果 `p` 是奇素数且 `a` 是与 `p` 互素的整数，那么 "a" 是否为模 `p` 的完全平方数？求二次剩余可以回答这个问题。如果 `m` 是正整数，我们称整数 "a" 为 `m` 的二次剩余，当且仅当 `gcd(a,m) = 1` 且同余式 `x² ≡ a (mod m)` 有解。如果 `x² ≡ a (mod m)` 无解，则称 "a" 为 `m` 的二次非剩余 [[2]](#01chap_01.xhtml#ref1_2)，[[3]](#01chap_01.xhtml#ref1_3)。

**示例**：判定哪些整数是 11 的二次剩余。

*   **步骤 1**：因为 `m = 11` 是素数，所以 `{1,2,…10}` 均与 `m` 互素。

*   **步骤 2**：计算整数 `{1,2,…10}` 的平方：`1² ≡ 10² ≡ 1 (mod 11)`，`2² ≡ 9² ≡ 4 (mod 11)`，`3² ≡ 8² ≡ 9 (mod 11)`，`4² ≡ 7² ≡ 5 (mod 11)`，`5² ≡ 6² ≡ 3 (mod 11)`。

*   **二次剩余**：1, 3, 4, 5, 9。**二次非剩余**：2, 6, 7, 8, 10。

**结论**：给定任意固定的正整数 `m`，只需列出所有小于 `m` 且与 `m` 互素的正整数，将它们平方并对 `m` 取模，即可确定二次剩余。

**引理**：如果 `p` 是奇素数且 `a` 是与 `p` 互素的整数，则同余式 `x² ≡ a (mod m)` 要么无解，要么恰好有两个模 `p` 不合同的解。

**证明**：如果 `x² ≡ a (mod p)` 有解，设为 `x = x[0]`，则我们可以很容易地证明 `x = -x[0]` 是第二个不合同解，因为 `(-x[0])² = x[0]² ≡ a (mod p)`。

**注**：`x[0] ≢ -x[0] (mod p)`（`2*x[0] ≡ 0 (mod p)`，这是不可能的，因为 `p | x[0]`）。

现在我们要证明不存在超过两个不合同的解。假设 `x = x[0]` 和 `x = x[1]` 都是 `x² ≡ a (mod p)` 的解。`x[0]² ≡ a (mod p)` 且 `x[1]² ≡ a (mod p)`，则 `x[0]² - x[1]² ≡ 0 (mod p)`。`(x[0]+x[1])(x[0]-x[1]) ≡ 0 (mod p)`，即 `p | (x[0]+x[1])` 或 `p | (x[0]-x[1])`。`x[1] ≡ -x[0] (mod p)` 或 `x[1] ≡ x[0] (mod p)`。

**定理**：如果 `p` 是奇素数，则 `p` 恰有 `(p - 1)/2` 个二次剩余和 `(p - 1)/2` 个二次非剩余。

**证明**：考虑整数 `{1,2,…p−1}` 的所有平方。我们知道 `x² ≡ (p-x)² ≡ a (mod p)`。设 `1 < b < p - 1`。`(p-b)² ≡ b² (mod p)`。

```
1², 2², …, ((p - 1)/2)² ≡ ((p + 1)/2)², …, (p - 2)², (p - 1)²
```

(1.6)

因为 `1² ≡ (p-1)² (mod p)`，同理，式 (1.6) 中的其他元素之间也存在同样的关系。因此，`1², 2², …, ((p - 1)/2)²` 互不相同。

#### 1.1.6.1 欧拉判别法

欧拉判别法精确地告诉我们整数 `a` 何时为模奇素数 `p` 的二次剩余。设 `p` 为奇素数且 `gcd(a,p) = 1`。当且仅当 `a^((p - 1)/2) ≡ 1 (mod p)` 时，`a` 是模 `p` 的二次剩余。

**证明**：设 `a` 为二次剩余，则 `x² ≡ a (mod p)`。`(x²)^((p - 1)/2) ≡ a^((p - 1)/2) (mod p)`。`x^(p - 1) ≡ a^((p - 1)/2) (mod p)`。由费马小定理，`x^(p-1) ≡ 1 (mod p)`，因此，`a^((p - 1)/2) ≡ 1 (mod p)`。

**反之**：已知 `a^((p - 1)/2) ≡ 1 (mod p)`。证明："a" 是模奇素数 `p` 的二次剩余。

**证明**：我们知道存在模 `p` 的一个原根 `g`，使得 `ℤ[p]` 中的任意整数均可表示为 `g^(i) (mod p)`，`1 ≤ i ≤ p - 1`，且 `g^(m) ≡ 1 (mod p)` 仅当 `p-1 | m`（`m=0` 或 `p-1`）时成立。对于某个 `1 ≤ i ≤ p - 1`，有 `a ≡ g^(i) (mod p)`。`g^(i((p - 1)/2)) ≡ a^((p - 1)/2) ≡ 1 (mod p)`（已知）。由原根的性质 `p - 1 | i((p - 1)/2)`；因此，`i` 必为偶数，设 `i = 2j`，这意味着 `a ≡ g^(2j) (mod p)`，`a ≡ (g^(j))² (mod p)`。因此，`a` 是模奇素数 `p` 的二次剩余。

### 1.1.7 勒让德符号

这是一个方便的符号，用于指示整数 `a` 是否为模奇素数 `p` 的二次剩余。`a (mod p)` 的勒让德符号记为 `(a/p)`。正式定义如下：

```
( a/p ) = {  1,  若 a 是模 p 的非零二次剩余
           { -1,  若 a 是模 p 的非零二次非剩余
           {  0,  若 p | a
```

(1.7)

示例：`(2/7) = 1`，`(2/5) = -1`，`(12/5) = -1`，`(101/97) = 1`，`(97/101) = 1`。

如果 `p` 除 `a` 有余数，即 `a = q*p + r`，则 `(a/p) = (r/p)`。由欧拉判别法，`a^((p - 1)/2) ≡ (a/p) (mod p)`。

#### 1.1.7.1 二次互反律

二次互反律关联了两个勒让德符号 `(p/q)` 和 `(q/p)`，其中 `p` 和 `q` 为奇素数：

```
( p/q ) ( q/p ) = (-1)^(((p - 1)/2) * ((q - 1)/2))
```

(1.8)

其中，当 $p \equiv 1 \pmod 4$ 时 $\frac{p - 1}{2}$ 为偶数，当 $p \equiv 3 \pmod 4$ 时为奇数。因此，若 $p \equiv 1 \pmod 4$ 或 $q \equiv 1 \pmod 4$，则 $\frac{p - 1}{2} \cdot \frac{q - 1}{2}$ 为偶数；而若 $p \equiv q \equiv 3 \pmod 4$，则 $\frac{p - 1}{2} \cdot \frac{q - 1}{2}$ 为奇数。因此，

$$

\left( \frac{p}{q} \right)\left( \frac{q}{p} \right) = \left\{

\begin{matrix}

1, & \text{若 } p \equiv 1 \pmod 4 \text{ 或 } q \equiv 1 \pmod 4 \text{（或两者皆满足）} \\

-1, & \text{若 } p \equiv q \equiv 3 \pmod 4

\end{matrix}

\right.

$$

(1.9)

由于 $\left( \frac{p}{q} \right)$ 和 $\left( \frac{q}{p} \right)$ 的唯一可能值为 $\pm 1$。因此，

$$

\left( \frac{p}{q} \right) = \left\{

\begin{matrix}

\left( \frac{q}{p} \right), & \text{若 } p \equiv 1 \pmod 4 \text{ 或 } q \equiv 1 \pmod 4 \text{（或两者皆满足）} \\

-\left( \frac{q}{p} \right), & \text{若 } p \equiv q \equiv 3 \pmod 4

\end{matrix}

\right.

$$

(1.10)

#### 1.1.7.2 雅可比符号

雅可比符号是勒让德符号的推广，其正式定义如下：

设 $n$ 为正整数，其质因数分解为 $n = p_1^{t_1} p_2^{t_2} \dots p_m^{t_m}$，设 $a$ 为与 $n$ 互质的正整数。则雅可比符号 $\left( \frac{a}{n} \right)$ 定义为：

$$

\left( \frac{a}{n} \right) = \left( \frac{a}{p_1^{t_1} p_2^{t_2} \dots p_m^{t_m}} \right) = \left( \frac{a}{p_1} \right)^{t_1} \left( \frac{a}{p_2} \right)^{t_2} \dots \left( \frac{a}{p_m} \right)^{t_m}

$$

(1.11)

例如：$\left( \frac{2}{45} \right) = \left( \frac{2}{3² \cdot 5} \right) = \left( \frac{2}{3} \right)² \left( \frac{2}{5} \right) = (-1)² (-1) = -1$ 和 $\left( \frac{109}{385} \right) = \left( \frac{109}{5 \cdot 7 \cdot 11} \right) = \left( \frac{109}{5} \right) \left( \frac{109}{7} \right) \left( \frac{109}{11} \right) = \left( \frac{4}{5} \right) \left( \frac{4}{7} \right) \left( \frac{10}{11} \right) = \left( \frac{2}{5} \right)² \left( \frac{2}{7} \right)² \left( \frac{-1}{11} \right) = (-1)² (1) (-1) = -1$。

上述关于数论概念的讨论是理解密码算法 [[4]](#01chap_01.xhtml#ref1_4)、[[5]](#01chap_01.xhtml#ref1_5) 的必要前提。

## 1.2 抽象代数

抽象代数 [[6]](#01chap_01.xhtml#ref1_6)、[[7]](#01chap_01.xhtml#ref1_7) 代表了一类强大的数学工具，应用于各个领域。它是经典代数的延伸，处理的是群、环、域等抽象结构，而非通常的数系。在本节中，我们将概述这些结构，这是理解密码体制核心的前提。

代数结构由以下三个组成部分刻画：

*   一个底层集合，通常称为代数结构的**载体集合**。

*   定义在底层集合元素上的运算。

*   集合中的特殊元素，称为代数结构的**常数**。

例如：$(\mathbb{Z}, +, 0)$ 是一个代数结构，其中 $\mathbb{Z}$ = 整数集，$+$ = 二元运算（从 $\mathbb{Z}² \to \mathbb{Z}$ 的映射），$\mathbb{Z}²$ 表示该运算作用于集合 $\mathbb{Z}$ 的两个元素上，且结果元素也属于集合 $\mathbb{Z}$，$0$ = $C$ 代数常数。

一般来说，算子可以取 $m$ 个元素：$S^m \to S$，此处 $m$ 称为运算的**元数**。任意两个代数结构可能具有相同的签名、相同数量且元数相同的运算以及相同数量的常数。例如，$(\mathbb{Z}, +, \cdot, -, 1, 0)$ 和 $(\mathbb{R}, +, \cdot, -, 1, 0)$，此处 $\mathbb{R}$ 为实数集。具有相同签名的两个代数未必具有相同的性质。$(\mathbb{Z}, -, 0)$ 和 $(\mathbb{Q}, +, 0)$。此处，交换律对第二个结构成立，但对第一个不成立。

**子代数结构**：设 $A = \langle S, \circ, \triangle, k \rangle$ 和 $A' = (S', \circ', \triangle', k')$ 为两个代数，则若满足 i) $S' \subseteq S$，ii) $a \circ' b = a \circ b, \forall a, b \in S'$，iii) $\triangle' a = \triangle a, \forall a \in S'$ 且 iv) $k' = k$，则 $A'$ 为 $A$ 的子代数。若 $A'$ 是 $A$ 的子代数，则 $A'$ 具有与 $A$ 相同的签名并遵守相同的公理。

**零元与一元**：设 $\circ$ 为 $S$ 上的二元运算。元素 $1 \in S$ 称为运算 $\circ$ 的**单位元**，若对每个 $x \in S$，有 $1_l \circ x = x \circ 1_r = x$。元素 $0 \in S$ 称为运算 $\circ$ 的**零元**，若对每个 $x \in S$，有 $0_l \circ x = x \circ 0_r = 0$。

考虑以下代数结构：$S = \{a, b, c\}$，运算：$\circ$，运算表：

$$

\begin{matrix}

\circ & a & b & c \\

a & a & b & b \\

b & a & b & c \\

c & a & b & c

\end{matrix}

$$

求零元和单位元。

*解*：右零元 = $a, b$，无左零元，左单位元 = $b$，无右单位元。

**定理**：设 $\circ$ 为 $S$ 上的二元运算，具有左单位元 $1_l$ 和右单位元 $1_r$。则 $1_l = 1_r$，这称为**双边单位元**。

*证明*：由左单位元得：$1_l \circ x = x$。令 $x = 1_r$。由右单位元得：$x \circ 1_r = x$。令 $x = 1_l$，得 $1_l \circ 1_r = 1_l$。因此 $1_r = 1_l$。

### 1.2.1 半群

半群是具有签名 $\langle S, \circ \rangle$ 的代数结构。半群通常由具有单个二元运算且满足封闭性和结合律的代数结构组成。例如：$\langle \mathbb{Z}, + \rangle$、$\langle \mathbb{Z}, \cdot \rangle$、$\langle \mathbb{R}, + \rangle$、$\langle \Sigma^*, \text{concatenation} \rangle$。

### 1.2.2 幺半群

幺半群是具有签名 $\langle S, \circ, 1 \rangle$ 的代数结构，其中 $\circ$ 为二元结合运算，$1$ 为运算 $\circ$ 的双边单位元。它满足封闭性、结合律和单位元公理。幂半群的例子包括：$\langle \mathbb{Z}, +, 0 \rangle$、$\langle \mathbb{Z}, \cdot, 1 \rangle$、$\langle \mathbb{R}, +, 0 \rangle$、$\langle \Sigma^*, \text{concatenation}, \lambda \rangle$。

### 1.2.3 群

群是具有签名 $\langle S, \circ, 1, - \rangle$ 的代数结构，其中 $\circ$ 为二元结合运算，常数 $1$ 为运算 $\circ$ 的双边单位元，$-$ 为定义在载体上的一元运算，使得 $\forall x \in S, \bar{x}$ 为 $x$ 关于 $\circ$ 的逆元。它满足封闭性、结合律、单位元和逆元公理。群的例子包括：$\langle \mathbb{Z}, +, 0, - \rangle$，此处 $-$ 表示一元取负运算。若 $\circ$ 运算满足交换律，则该群称为**阿贝尔群**（或交换群）。群是构造密码体制中最常用的代数结构。因此，我们将在篇幅限制内尽可能详细地介绍。

**群具有唯一逆元**：设群元素 $a$ 有两个逆元 $b$ 和 $c$，$b \circ a = e$ 且 $c \circ a = e$，这蕴含 $b \circ a = c \circ a \Rightarrow b \circ a \circ b = c \circ a \circ b$。设 $a \circ b = d$，则 $b \circ d = c \circ d$。我们知道群中每个元素都有逆元，故 $b \circ d \circ d^{-1} = c \circ d \circ d^{-1} \Rightarrow b \circ e = c \circ e$。因此，$b = c$。

由于逆元的存在，群中允许左消去和右消去。

#### 1.2.3.1 对称有限群

对称有限群定义在有限集合 *n* ∈ ℕ = {1,2,3,4,……,*n*} 上，通常表示为 *S*[*n*]。为了构造对称群，我们必须考虑 *n* 个元素的集合排列，并为每个排列指定一个名称。这些排列将成为群 *S*[*n*] 的元素，然后我们必须定义合成律。例如：

*S*[1] = {*i*} *S*[1] 的排列：
