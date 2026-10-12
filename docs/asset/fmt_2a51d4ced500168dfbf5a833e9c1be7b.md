
为了证明这一主张，我们令 *F* 为事件：对手 ![image](img/a.jpg) 至少查询一个在 Game 4 中未被拒绝的非法密文。和以前一样，只需推导出 Pr\[*F*\] 的信息论界限即可，因为 Pr\[*S*[1]\] − Pr\[*S*[2]\] ≤ Pr\[*F*\]。回想一下，![image](img/a.jpg) 不允许查询 (*u[i], υ[i], w[i], e[i]*) = (*u*^∗, *v*^∗, *w*^∗, *e*^∗)。这一性质，连同截至 Game 4 的拒绝条件，我们得到：要使 *F* 发生的查询必须满足 *H*(*u[i], υ[i], w[i]*) ≠ *H*(*u*^∗, *υ*^∗, *w*^∗)。令 *t[i]* = *H*(*u[i], υ[i], w[i]*) 和 *t* = *H*(*u*^∗, *υ*^∗, *w*^∗)（因此 *t[i] ≠ t*）。令 *ℓ* = log[*g*1] *g*[2]。对于每个查询 *C[i]* = (*u[i], υ[i], w[i], e[i]*)，我们记 *r[i]* = log[*g*1] *u[i]*, ![image](img/rpi.jpg) = log[*g*2] *υ[i]* 和 *z[i]* = log[*g*1] *e[i]*。`Dec` 中的有效性检查等式，即 ![image](img/i34.jpg) 等价于 ![image](img/i35.jpg)。为简化起见，我们首先假设不失一般性地 ![image](img/a.jpg) 在挑战前不进行查询。因此，![image](img/a.jpg) 可以使其第一个（挑战后）查询为非法，同时也在 Game 4 中不被拒绝，方法是猜测 ![image](img/i36.jpg)，其中 *r*[1] ≠ ![image](img/rp1.jpg) 使得

![image](img/p13-1.jpg)

现在我们观察到 ![image](img/a.jpg) 可能知道的关于 *a, b, a*′, *b*′ 的信息包括

![image](img/p13-2.jpg)

还要回想 *ℓ* ≠ 0 和 *r* ≠ *r*′。我们论证正确猜测 *z*[1] 的概率是 1/*q*。这成立是因为当 *r − r*′ 和 *r*[1] ≠ ![image](img/rp1.jpg) 和 *t*[1] ≠ *t*′ 时，*z*[1] 的表达式与 *a* + *ℓb, a*′ + *ℓb*′, 和 *r*(*a* + *ta*′) + *r*′*ℓ*(*b* + *tb*′) 线性无关。这可以通过在变量向量 (*a, a*′, *b, b*′) 上建立方程组并得到系数矩阵来确认，即

![image](img/p14-1.jpg)

并看到其行列式为 *ℓ*²(*r* − *r*′)(*r*[1] − ![image](img/rp1.jpg))(*t*′ − *t*[1]) ≠ 0。

接下来，为了处理 ![image](img/a.jpg) 在挑战前确实进行查询的情况以及多次非法查询的情况，我们采用与主张 1.5 的证明类似的方法（当时我们考虑的是第 *i* 次查询）。由此，我们可以得出 Pr\[*F*\] 可以忽略不计。

### 主张 1.12. – Pr\[*S*[5]\] = 1/2.

上述主张可以用与主张 1.6 完全相同的方式证明。

结合所有主张，我们得到 | Pr\[*S*[0]\] − 1/2| 在 DDH 假设和 ![image](img/h.jpg) 的安全性下可以忽略不计，正如所期望的那样。

![image](img/squ.jpg)

### 1.2.5. 其他具体的 PKE 方案

我们列出文献中一些重要的 PKE 方案，连同它们的安全性、假设和一些特性。注意此列表绝非详尽无遗。

#### 1.2.5.1. 基于与因式分解相关问题的 PKE

– RSA (Rivest 等人 1978)：在 RSA 假设下单向性安全。

– Rabin (Rabin 1979)：在因式分解困难性下单向性安全。

– Goldwasser-Micali (Goldwasser 和 Micali 1982)：首个被证明的 IND-CPA 安全 PKE，基于二次剩余 (QR) 假设。类似于 RSA 假设（以及下文的 DCR），QR 假设与因式分解的困难性相关，但不知是否可由后者推导。

– Blum–Goldwasser (Blum 和 Goldwasser 1984)：在因式分解困难性下 IND-CPA 安全。

– Paillier (Paillier 1999)：在判定复合剩余 (DCR) 假设下 IND-CPA 安全。它是最著名的具有加法同态特性的 PKE 之一。Damgård 和 Jurik (2001) 在相同假设下提出了明文空间更大的扩展方案。Paillier 方案的前身包括 Benaloh (1994)、Naccache 和 Stern (1998) 以及 Okamoto 和 Uchiyama (1998) 的方案。

– Cramer–Shoup (2002) (Cramer 和 Shoup 2002)：IND-CCA 安全的 PKE 方案，一个基于 DCR 假设，另一个基于 QR 假设。事实上，他们提供了一个基于所谓哈希证明系统 (HPS) 的框架，该框架推广了（也捕捉了）基于 DDH 的原始 Cramer–Shoup (1998) 方案 (Cramer 和 Shoup 1998)。

– Hofheinz-Kiltz (2009) (Hofheinz 和 Kiltz 2009)：基于因式分解困难性的首个实用 IND-CCA 安全 PKE。

– Cramer–Hofheinz–Kiltz (Cramer 等人 2010)：基于 RSA 假设的 IND-CCA 安全 PKE 方案。他们还提供了至少另一个方案（见下文）。

#### 1.2.5.2. 基于与离散对数相关问题的 PKE

– ElGamal (ElGamal 1984) 和 Cramer–Shoup (1998) (Cramer 和 Shoup 1998)。我们在上文已详细描述它们。

– Kurosawa–Desmedt (Kurosawa 和 Desmedt 2004)：基于 DDH 假设、目标抗碰撞哈希和认证的对称密钥加密 (SKE) 的 IND-CCA 安全。该方案提高了 Cramer–Shoup PKE 的效率；值得注意的是密文大小减少了一个群元素。就撰写本文而言，该方案仍然是基于 DDH 假设的最高效 IND-CCA 安全 PKE 方案之一（至少在密文大小方面）。它可被视为混合加密（见 第 1.3.1 节）。

– Boyen–Mei–Waters (Boyen 等人 2005)：在判定双线性 Diffie–Hellman (DBDH) 假设 (Boneh 和 Franklin 2001) 下 IND-CCA 安全。该方案在所有这些高效 PKE 方案中拥有最紧凑的密文，但依赖于更强的工具——双线性配对。

– Hofheinz–Kiltz (Hofheinz 和 Kiltz 2007) 和 Shacham (Shacham 2007)：在 *k*-判定线性 (*k*-DLin) 假设下 IND-CCA 安全，对于任意正整数 *k*。我们注意到 1-Dlin 假设本身就是 DDH 假设，而 (*k* + 1)-DLin 严格弱于 *k*-Dlin。另一方面，在这些方案中，密钥和密文的大小随 *k* 线性增长。

– Cash–Kiltz–Shoup (Cash 等人 2008)、Hanaoka–Kurosawa (Hanaoka 和 Kurosawa 2008)、Haralambiev 等人 (Haralambiev 等人 2010) 和 Cramer–Hofheinz–Kiltz (Cramer 等人 2010)：在计算 Diffie–Hellman (CDH) 假设下 IND-CCA 安全的 PKE 方案。注意 CDH 严格弱于 DDH。此外，这些直接构造比基于搜索问题（如 CDH）困难性的通用硬核谓词方法 (![image](img/g1.jpg) oldreich 和 Levin 1989) 构造 PKE 更高效。

#### 1.2.5.3. 基于与格相关问题的 PKE（及其他）

– Regev (Regev 2005)：首个在学习误差 (LWE) 假设下 IND-CPA 安全的 PKE。

– Peikert 和 Waters (Peikert 和 Waters 2008)：首个在 LWE 假设下 IND-CCA 安全的 PKE。Micciancio 和 Peikert (2012) 给出了一个提高效率的直接构造。

还有与其他数学结构相关的 PKE 方案，如纠错码、同源、多元多项式等。基于格的方案和这些后者方案属于后量子密码学领域，由本系列的另一本书涵盖。

#### 1.2.5.4. 随机预言模型中的 PKE

# IND-CCA 安全 PKE 的通用构造

迄今为止，我们描述和列举的仅是*标准模型*中的 PKE 方案。另一种通常能产生非常高效的 IND-CCA 安全 PKE 的流行方法，是在*随机预言机模型*（RO）（Bellare 和 Rogaway 1993）中构造方案。随机预言机是以预言机形式提供的均匀随机函数。在 RO 模型中，方案中使用的哈希函数在安全性证明中被随机预言机替代。缺点是，随机预言机模型方法仅具有启发式性质，且通常不合理（例如（Canetti 等人 1998））。RO 模型中 PKE 的一个例子是 RSA-OAEP 方案（Bellare 和 Rogaway 1995），该方案在 RO 模型下基于 RSA 假设被证明是 IND-CCA 安全的（Fujisaki 等人 2001）。另一个例子是所谓的 DHIES 方案（Abdalla 等人 2001），其在 RO 模型下的 IND-CCA 安全性可归约到所谓的 gap-DH 假设（Okamoto 和 Pointcheval 2001a），即即使对手拥有解决 DDH 问题的预言机，CDH 假设依然成立。还有一个值得一提的方案是 ElGamal 的一个变体，称为 Twin ElGamal（Cash 等人 2008），它在 RO 模型下基于 CDH 假设是 IND-CCA 安全的，并且像原始 ElGamal PKE 一样拥有非常紧凑的密文。事实上，DHIES 和 Twin ElGamal 都具有混合加密的结构（参见第 1.3.1 节）。

此外，我们还拥有更多“通用”的构造，它们可以将基础方案（通常满足某种弱安全形式，如 IND-CPA 或 CPA 下的单向性）通用地转换为在 RO 模型下达到 IND-CCA 安全的方案。（事实上，RSA-OAEP 就属于此类，它是通过将 OAEP 变换应用于 RSA 加密方案而获得的。）我们将在第 1.3.3 节中涉及它们。

## 1.3. IND-CCA 安全 PKE 的通用构造

上一节描述了一些基于具体数学假设的*特定*PKE 方案。本节描述基于通用密码学原语的*通用*IND-CCA 安全 PKE 构造。

### 1.3.1. 混合加密

通常，公钥密码学的计算量级比对称密钥密码学重且慢得多。*混合加密*是一种实用技术，旨在尽可能兼顾 PKE 的功能性和 SKE 的高效性。具体而言，要加密一条（长）消息，我们仅用 PKE 方案加密一个随机的、固定长度的“会话”密钥`K`，而实际要发送的消息则使用密钥`K`通过 SKE 进行加密。Cramer 和 Shoup（2003）为混合加密（也称为 KEM/DEM 框架）引入了现代处理方式和形式化，其中加密随机会话密钥`K`的过程被形式化为一个称为*密钥封装机制（KEM）*的专用原语。

在本节中，我们回顾混合加密的现代处理方式。具体来说，我们回顾 KEM 和 SKE 的形式化，然后回顾文献中混合加密的构造及相关结果。

KEM 由三个 PPT 算法（`KKG`、`Encap`、`Decap`）组成，语法如下：

![image](img/p17-1.jpg)

其中`Decap`是确定性算法，（`pk`、`sk`）是公钥/私钥对，`c`是在`pk`下会话密钥`K`的密文。与 PKE 一样，`Decap`允许输出特殊的无效符号⊥。

对于 KEM，IND-CCA 安全性和 IND-CPA 安全性的定义方式与 PKE 非常相似。本质区别仅在于：在 KEM 的安全性实验中，对手不再选择两个挑战明文，而是被给予挑战密文`c*`以及一个真实的会话密钥`K*`（与`c*`一起生成）或一个完全随机的会话密钥`K'`，并被要求区分这两种情况。

SKE 方案（在混合加密语境下也称为 DEM）由两个 PPT 算法（`E`、`D`）组成，语法如下：

![image](img/p17-2.jpg)

其中`D`是确定性算法，`K`表示密钥，`c`表示明文`m`在密钥`K`下的密文。与 PKE 和 KEM 一样，`D`允许输出特殊的无效符号⊥。在此语法中，密钥`K`的长度决定了安全参数。通常，SKE 方案也可能有专门的密钥生成算法，但为简化起见，此处不考虑此类语法。

在一般情况下考虑 SKE 的安全性时，我们需要考虑拥有加密预言机访问权限的对手，因为与 PKE 情况不同，对手无法自行生成密文。另一方面，对于此处混合加密语境下的 SKE，我们只要求“一次性”加密，因为混合加密将仅在每次加密时使用一个全新的会话密钥进行单次加密。回想一下，PKE 的安全概念已经以挑战密文`c*`的形式提供了一次加密（参见图 1.1）。因此，“一次性”SKE 的安全概念可以精确地定义为 PKE 的安全概念，唯一的例外是作为输入给对手的公钥`pk`变为空。我们将由此从 PKE 的 IND-CCA（分别 IND-CPA）安全性导出的 SKE 安全概念称为*IND-OT-CCA 安全性*（分别*IND-OT 安全性*），其中 OT 代表“一次性加密”。

值得一提的是，构造 IND-OT 和 IND-OT-CCA 安全的 SKE 方案相对直接。所谓的“伪随机一次性密码本”方案（即将密钥定义为伪随机生成器以随机输入为输出的一次性密码本方案）是 IND-OT 安全 SKE 的一个例子。类似地，任何强伪随机排列（Luby 和 Rackoff 1988）都可视为 IND-OT-CCA 安全的 SKE 方案，其中通过将消息输入排列来进行加密。注意，理论上，这样的排列可以从任何单向函数构造（Håstad 等人 1999；Luby 和 Rackoff 1988）。从这两个例子可知，IND-OT-CCA 和 IND-OT 安全的 SKE 均可通过加密算法为确定性且密文开销（即密文大小与待加密明文大小的差值）为零的加密方案来实现。

给定一个 KEM（`KKG`、`Encap`、`Decap`）和一个 SKE 方案（`E`、`D`），PKE 方案（`KG`、`Enc`、`Dec`）的混合加密构造如图 1.7 所述。

![图 1.7. 混合加密：从 KEM 和 SKE 构造 PKE](img/fig1-7.jpg)

**图 1.7.** *混合加密：从 KEM 和 SKE 构造 PKE*

Cramer 和 Shoup（2003）证明了如果底层 KEM 是 IND-CCA 安全的，且底层 SKE 方案是 IND-OT-CCA 安全的，那么混合加密构造就是一个 IND-CCA 安全的 PKE 方案。此外，Herranz 等人（2010）研究了混合加密构造所达到的安全概念与底层 KEM/SKE 方案的安全概念之间的关系。特别地，他们证明了如果底层 KEM 是 IND-CCA1 安全的（分别为 IND-CPA），且底层 SKE 方案是 IND-OT 安全的，那么混合加密构造就是 IND-CCA1（分别为 IND-CPA）安全的。Hofheinz 和 Kiltz（2007）给出了混合加密的另一个结果：如果底层 KEM 在*受限 CCA 安全*意义上是安全的（这是一种严格弱于 IND-CCA 安全的安全概念），且底层 SKE 方案在（一次性）认证加密（Bellare 和 Namprempre 2000）意义上是安全的（同时考虑 IND-OT 安全性和一次性真实性），那么混合加密构造仍然能达到 IND-CCA 安全。我们注意到，同时达到 IND-OT 安全性和一次性真实性的 SKE 方案自动达到 IND-OT-CCA 安全性；因此，在一次性认证加密意义上安全的要求强于 IND-OT-CCA 安全性。

Abe 等人（2005）展示了另一种不同于上述的混合加密范式，称为 Tag-KEM/DEM 框架。该框架定义了一种称为 tag-KEM 的新原语。其语法与上述普通 KEM 的区别在于，生成 KEM 密文时允许来自 SKE/DEM 部分的反馈输入。该框架的优点之一是底层 SKE 方案只需是 IND-OT 安全的，而构造 tag-KEM 通常比构造普通 KEM 更困难。

这些关于混合加密的结果使我们在设计 IND-CCA 安全的 PKE 方案时，能够专注于合适 KEM 的设计。

### 1.3.2. Naor–Yung 构造及其扩展

我们描述一种由 Naor 和 Yung（1990）提出的经典方法，用于从 IND-CPA 方案和*非交互零知识*（NIZK）证明系统（Blum 等人 1988）构造 IND-CCA1 安全的 PKE。在该构造中，明文在独立的密钥和随机数下被加密两次，然后使用 NIZK 来证明两个密文加密的是同一个明文。其直觉是：如果对手能以某种方式获得两个独立加密同一明文的密文，那么本质上它已经知道该明文了。因此，解密预言机对对手应当是无用的。

我们首先简要回顾 NP 语言的概念以及此类语言 NIZK 的语法。关于零知识证明的更多细节可参见第 3 章。语言是一组二进制字符串，记为*L* ⊂ {0, 1}^∗。如果存在一个确定性多项式时间图灵机*M*，使得*x ∈ L*当且仅当存在一个长度为|x|的多项式的*见证 w*使得*M*(*x, w*) = 1，则语言*L*属于 NP 类。

![Figure 1.8. Naor-Yung construction](img/fig1-8.jpg)

**图 1.8.** *Naor-Yung 构造*

在*公共随机字符串*（CRS）模型中，针对 NP 语言*L*的 NIZK 证明系统由三个算法（`CRSGen`、`P`、`V`）组成，其语法如下：

![image](img/p20-1.jpg)
