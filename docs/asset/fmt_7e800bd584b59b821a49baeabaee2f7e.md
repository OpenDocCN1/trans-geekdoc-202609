
# 参考文献

Shannon, C.E. (1949). Communication theory of secrecy systems. *Bell Systems Technical Journal*, 28(4), 656–715.

Shoup, V. (2001a). OAEP reconsidered. In *CRYPTO 2001*, vol. 2139 of *LNCS*, Kilian, J. (ed.). Springer, Heidelberg.

Shoup, V. (2001b). A proposal for an ISO standard for public key encryption. Cryptology ePrint Archive, Report 2001/112 \[Online\]. Available at: [`eprint.iacr.org/2001/112`](https://eprint.iacr.org/2001/112).

Shoup, V. (2004). Sequences of games: A tool for taming complexity in security proofs. Cryptology ePrint Archive, Report 2004/332 \[Online\]. Available at: [`eprint.iacr.org/2004/332`](https://eprint.iacr.org/2004/332).

Targhi, E.E. and Unruh, D. (2016). Post-quantum security of the Fujisaki-Okamoto and OAEP transforms. In *TCC 2016-B, Part II*, vol. 9986 of *LNCS*, Hirt, M., Smith, A.D. (eds). Springer, Heidelberg.

Wee, H. (2010). Efficient chosen-ciphertext security via extractable hash proofs. In *CRYPTO 2010*, vol. 6223 of *LNCS*, Rabin, T. (ed.). Springer, Heidelberg.

Wee, H. (2016). KDM-security via homomorphic smooth projective hashing. In *PKC 2016, Part II*, vol. 9615 of *LNCS*, Cheng, C.-M., Chung, K.-M., Persiano, G., Yang, B.-Y. (eds). Springer, Heidelberg.

Yamakawa, T., Yamada, S., Hanaoka, G., Kunihiro, N. (2016). Adversary-dependent lossy trapdoor function from hardness of factoring semi-smooth RSA subgroup moduli. In *CRYPTO 2016, Part II*, vol. 9815 of *LNCS*, Robshaw, M., Katz, J. (eds). Springer, Heidelberg.

Yang, R., Lai, J., Huang, Z., Au, M.H., Xu, Q., Susilo, W. (2020). Possibility and impossibility results for receiver selective opening secure PKE in the multi-challenge setting. In *ASIACRYPT 2020, Part I*, vol. 12491 of *LNCS*, Moriai, S., Wang, H. (eds). Springer, Heidelberg.

# 注释

1. 一种称为通用单向哈希函数族的较弱原语 (Naor and Yung 1989) (也可称为目标抗碰撞哈希) 也可被使用。然而，为简单起见，我们此处选择使用抗碰撞哈希函数。

2. 相应地，加密实际消息的过程称为*数据封装机制 (DEM)*，但由于其功能等同于 SKE，我们将主要使用 SKE。

3. 可访问：[`csrc.nist.gov/projects/post-quantum-cryptography`](https://csrc.nist.gov/projects/post-quantum-cryptography)。

4. 严格来说，如果我们仅关心渐近安全性保证，则右侧的 `![image](img/i46.jpg)` 替换为某个正常数 `c` ≤ 1 的 `![image](img/i47.jpg)` 即已足够，且 `![image](img/b.jpg)` 的运行时间可以是 `![image](img/a.jpg)` 运行时间的多项式。这种更一般的情况与归约的紧致性背道而驰。

5. 注意，基于“该方案是多用户/多挑战 IND-CCA 安全的”这一假设，PKE 方案总是紧致安全的。因此，只有当底层假设（问题）*P* 是文献中经过充分研究的（如 DDH）时，紧致安全性才有意义。

# 2 签名与安全概念

**Marc FISCHLIN**

*Technische Universität Darmstadt, Germany*

我们介绍数字签名方案的概念并讨论实践中使用的一些示例方案。随后我们讨论签名方案的基本安全属性，特别是针对选择消息攻击的不可伪造性和强不可伪造性。

## 2.1 签名方案

在本节中，我们描述数字签名方案的接口，以及签名者生成的真实签名可被验证为正确的最小功能要求。然后我们讨论两个此类签名方案的经典示例。

### 2.1.1 定义

#### 数字签名方案

与手写签名类似，我们期望数字签名 `σ` 将来自某个可接受消息空间 `![image](img/m.jpg)` 的消息 `m` 的内容与签名者绑定。签名者由公钥 `pk` 标识，该公钥可能经过认证，从而与身份关联。由于我们期望只有签名者能够创建此类签名，因此签名者持有与 `pk` 匹配的密钥 `sk`，二者通过某个 `KGen` 算法共同生成。使用密钥 `sk` 进行签名由方案的 `Sig` 算法执行，而在公钥 `pk` 下的验证则通过 `Vf` 算法完成。

有了上述接口，三个算法 `KGen`、`Sig` 和 `Vf` 尚未“关联”。这是通过正确性属性来实现的：该属性指出，由 `KGen` 生成的密钥下，通过算法 `Sig` 生成的签名会被验证算法 `Vf` 识别为正确。注意，原则上让 `Vf` 接受任何签名即可轻松实现这一点。但我们稍后将要求：在不知道密钥的情况下，很难找到这种有效签名，即这种不可伪造性概念与正确性要求在这方面可以视为对立面。

**定义 2.1（签名方案）。** *数字签名方案* `S` = (`S`.`KGen`, `S`.`Sig`, `S`.`Vf`) *由三个概率多项式时间算法组成，满足：*

*– **密钥生成**：密钥生成算法以单元编码的安全参数 `1^λ` 为输入，输出一对密钥和公钥，`(sk, pk)` ←[$] `S`.`KGen`(`1^λ`)。我们假设每个密钥都能高效恢复 `1^λ`，且安全参数决定了一个消息空间 `![image](img/m.jpg)`[λ] ⊆ {0, 1}^∗。*

*– **签名**：签名算法接收密钥 `sk` 和消息 `m` ∈ `![image](img/m.jpg)`[λ] 作为输入，输出一个签名，`σ` ←[$] `S`.`Sig`(`sk, m`)。*

*– **验证**：验证算法接收公钥 `pk`、消息 `m` ∈ `![image](img/m.jpg)`[λ] 和潜在签名 `σ` 作为输入，输出一个决策比特，`d` ←[$] `S`.`Vf`(`pk, m, σ`)。*

*正确性表明，以压倒性概率（作为 `λ` 的函数），对于任意消息 `m` ∈ `![image](img/m.jpg)`[λ]，当 `(sk, pk)` ←[$] `S`.`KGen`(`1^λ`)、`σ` ←[$] `S`.`Sig`(`sk, m`) 且 `d` ←[$] `S`.`Vf`(`pk, m, σ`) 时，有 `d` = 1。如果正确性以概率 1 成立，则称该方案为**完全正确**。*

我们针对概率验证算法定义了签名方案。在所有已知方案中，验证都是确定性的，如果签名算法输出一个签名，则（确定性）验证者也会接受该签名。尽管如此，当今一些实用的签名方案，特别是基于格的方案如 `Dilithium` (Bai et al. 2020)，可能在单次执行中无法创建有效签名，因此需要在此情况下迭代。此时，该算法理论上可能永远运行，或者需要在一定迭代次数后中止，导致签名生成过程中通常出现可忽略的错误。对于实际用途，该概率无关紧要。

我们注意到，理论上，对于确定性验证者，很容易修复可忽略的正确性错误，且不违背不可伪造性。为此，签名者在输出签名 `σ` 前先对其进行验证，若验证失败则改为输出签名密钥 `sk`。验证算法随后也接受密钥作为任意消息 `m` 的签名，从而修复签名过程中的任何错误。此处假设可以检查 `sk` 是否为 `pk` 的有效签名密钥。如果 `sk` 包含执行 `KGen` 生成密钥对所用的随机性，则后者易于实现。但请再次强调，该解决方案仅具有理论意义。

### 2.1.2 实用方案示例

本节介绍实践中部署最广泛的两种签名方案。我们将在后续章节介绍安全概念后，再讨论它们的安全属性。

#### 2.1.2.1 数字签名算法

数字签名算法 (DSA) 由美国国家标准与技术研究院 (NIST) 提出，最早于 1994 年作为数字签名标准 (National Institute of Standards and Technology 1994) 中唯一的签名算法。该算法使用一个群 `G`，并在 `G` 的一个由元素 `g` ∈ `G` 生成的素数阶 `q` 的子群中工作。我们用 ⟨`g`⟩ 表示这个由 `g` 生成的循环群。最初，NIST 仅建议使用群 `G` = `![image](img/zsp.jpg)`，其中素数 `p` 在 512 位到 1024 位之间，`q` 的阶为 2¹⁶⁰。最新版 DSS 标准 (National Institute of Standards and Technology 2013) 允许 `(p, q)` 采用 (1024, 160)、(2048, 224)、(2048, 256) 或 (3072, 256) 位的其他选择，并包含一个称为 ECDSA 的椭圆曲线版本。我们首先采用模 `p` 乘法群 `![image](img/zsp.jpg)` 形式来描述算法，随后讨论 ECDSA 的变化。

对于签名消息 `m`，DSA 部署一个函数 `H` 将消息哈希为短字符串。随后通过标准的字符串到整数转换将该字符串嵌入 `![image](img/z1.jpg)`[q]，这要求哈希算法的输出足够短。我们在此简单假设 `H`(`m`) 是来自 `![image](img/z1.jpg)`[q] 的值。NIST 建议使用 National Institute of Standards and Technology (2015) 中指定的任何安全哈希算法。由于最新版哈希标准提出了输出长度各异的不同算法，较大的哈希输出可能需要截断。

**构造 2.2（数字签名算法）。** *群 ⟨`g`⟩* ⊆ `![image](img/zsp.jpg)` *上素数阶为 `q`、带哈希函数* `H` *的* `DSA` *包含以下算法：*

*– **密钥生成**：对于给定群，密钥生成算法随机选取 `sk` ←[$] `![image](img/z1.jpg)`[q]，设定 `pk` ← `g^sk` mod `p`，并输出 `(sk, pk)` 作为密钥对。*

*– **签名**：为签名消息 `m` ∈ {0, 1}^∗，签名者随机选取 `k` ←[$] `![image](img/zsp.jpg)` 并计算*

```
r = (g^k mod p) mod q
s = k^(−1) (H(m) + sk · r) mod q
```

*其中 `k^(−1)` 是 `k` 在 `![image](img/z1.jpg)`[q] 上的逆元。它输出 `σ` = (`r, s`) 作为 `m` 的签名。若 `r` = 0 或 `s` = 0，则签名者须重启签名过程。*

*– **验证**：输入 `pk`、`m` 和 `σ` = (`r, s`)，验证者检查 `r` 和 `s` 是否在 `![image](img/zsq.jpg)` 中，即 `0 < r, s < q`，然后计算*

```
u1 = H(m) · s^(−1) mod q
u2 = r · s^(−1) mod q
```

*并检查 `r` = (`g^u1` · `pk^u2` mod `p`) mod `q`。当且仅当所有测试均通过时，验证者输出 1，否则输出 0。*

关于正确性，我们注意到，对于公钥 `pk` 下消息 `m` 的合格签名 `σ` = (`r, s`)，有

```
g^u1 · pk^u2 = g^(H(m)·s^(−1)) · g^(sk·r·s^(−1))
            = g^(H(m)·s^(−1) + sk·r·s^(−1))
            = g^(s·k^(−1)·s^(−1))   (因为 s = k^(−1)(H(m) + sk·r))
            = g^k   (mod p)
```

因此，对该值取模 `q` 可得值 `r`，验证者接受该签名。

椭圆曲线版本称为 ECDSA，运行在特殊群上（同样为素数阶 `q`），群元素由 `x` 坐标和 `y` 坐标组成。椭圆曲线也提供群运算，通常称为加法而非乘法。因此，生成元由一对 `g` = (`g[x]`, `g[y]`) 组成，我们可以将步骤 `g^k` 解释为在曲线上对 (`g[x]`, `g[y]`) 进行 `k` 次加法。

请注意，我们可以保留原始 DSA 中 `![image](img/z1.jpg)`[`q`] 中的标量运算不变，但只需要调整模 `p` 的运算，具体来说是在签名步骤中计算 `r` ← (`g^k` mod `p`) mod `q`，以及在验证签名时验证 `r` = (`g`^(`u`[1]) `pk`^(`u`[2]) mod `p`) mod `q`。在椭圆曲线情况下，我们不能简单地计算 `g^k` 然后将其模约到 `q`，因为群元素由坐标对组成。ECDSA 标准则让 `r` 成为 `g^k` 的 `x` 坐标，验证者检查计算出的群元素的 `x` 坐标是否与给定的 `r` 匹配。

#### 2.1.2.2 施诺尔签名方案

施诺尔签名方案（Schnorr 1990, 1991）是菲亚特-沙米尔范式（Fiat and Shamir 1987）的一个基于离散对数的变体，用于将识别方案转化为签名方案。因此，它遵循承诺-质询-响应范式，其中非交互式签名方案中的质询是通过将哈希函数 `H` 应用于初始承诺和消息来计算的。与 DSA 情况类似，哈希函数的范围再次可以嵌入到 `![image](img/z1.jpg)`[`q`] 中，其中 `q` 为素数，表示生成元 `g` 的群 〈`g`〉 的阶。事实上，施诺尔的安全性证明促使了素数阶 `q` 的使用。为了演示，我们再次假设由 `g` 生成的群位于 `![image](img/zsp.jpg)` 中。也存在椭圆曲线变体，它是对椭圆曲线上运算的直接改编。

**构造 2.3（施诺尔签名方案）。** – *在素数阶 q 的群 〈g〉* ⊆ `![image](img/zsp.jpg)` *上，带有哈希函数* `H` *的施诺尔签名方案* `Schnorr` *包含以下算法：*

**密钥生成：** 对于给定的群，密钥生成算法随机选取 `sk` ←[$] `![image](img/z1.jpg)`[`q`]，设置 `pk` ← `g^(sk)` mod `p`，并输出 (`sk`, `pk`) 作为密钥对。

**签名：** 要对消息 `m` ∈ {0, 1}^∗ 进行签名，签名者选取随机 `r` ←[$] `![image](img/z1.jpg)`[`q`] 并计算

```
c = H(g^r mod p, m)
y = r + c · sk mod q
```

输出 `σ` ← (`c`, `y`) 作为 `m` 的签名。

**验证：** 输入 `pk`、`m` 和 `σ` = (`c`, `y`)，验证者检查 `c` 和 `y` 是否在范围 `![image](img/z1.jpg)`[`q`] 内，如果是，则验证 `H`(`g^y pk`^(−`c`), `m`) = `c`。当且仅当所有测试都通过时，验证者输出 1，否则输出 0。

对于正确性，我们观察到对于由 `Schnorr`.`Sig` 在密钥 `sk` 下生成的签名 `σ` = (`c`, `y`)，有 `y` = `r` + `c` · `sk` mod `q`，其中 `r` 是签名步骤中使用的随机数。但随后 `g^y · pk`^(−`c`) = `g`^(`r`+`c`·`sk`) · `g`^(−`c`·`sk`) = `g^r` mod `p`，验证中推导出的值与签名者计算的值 `R` = `g^r` mod `p` 匹配。因此，验证中的哈希函数求值也将 `H`(`g^y · pk`^(−`c`), `m`) 映射到 `c`，验证成功。

## 2.2 不可伪造性

在本节中，我们讨论不可伪造性的基本概念。我们还结合所达到的安全保证，重新审视前面的方案。

### 2.2.1 讨论

直观地说，我们对安全签名方案的期望很容易阐述，即没有人能够伪造签名。为了形式化这一点，我们必须考虑对手在攻击中能做什么，以及何时对手获胜。我们从后者开始，遵循 Goldwasser 等人（1988）的工作：

– **完全攻破：** 对手能够计算出签名者的密钥。

– **普遍伪造：** 对手能够找到一个与签名者过程功能等价的算法。

– **选择性伪造：** 对手能够为一个预先选定的消息伪造签名。

– **存在性伪造：** 对手能够为一个任意的、可能毫无意义的消息伪造签名。
