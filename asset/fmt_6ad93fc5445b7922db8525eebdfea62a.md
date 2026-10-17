
## 标准模型中的 PAKE 改进

Nguyen 和 Vadhan (2004)、Barak 等人 (2005) 以及 Goyal 等人 (2010) 改进了 Goldreich-Lindell 标准模型 PAKE (Goldreich 和 Lindell 2001)，但这些标准模型构造都不实用。

关于 CRS 模型，Gennaro 和 Lindell (2003) 推广了 KOY 协议，允许采用其他 SPHF 友好的 Cramer-Shoup 加密实例化，例如基于二次剩余假设或 Paillier 加密 (Paillier 1999) 中使用的 N-剩余假设。同一篇论文还指出，CCA 安全加密可以放宽为非延展性承诺。

Katz 等人 (2005) 观察到，复用 Canetti 等人 (2005) 在 UC PAKE 背景下应用的思路，`B` 的加密只需满足 CPA 安全。

Gennaro (2008) 表明可以用 MAC 替换 `A` 的一次性签名。

Jiang 和 Gong (2004) 展示了 KOY 更强的简化（也实现了 3 轮 PAKE-EA，见第 10.4.4 节）：`A` 的加密可以是带有关联 SPHF 的 CPA 安全，而 `B` 可以使用不需要 SPHF 的 CCA 安全加密。取而代之的是，以一种类似于 Fujisaki-Okamoto 编译器 (Fujisaki 和 Okamoto 1999) 从 CPA 到 CCA PKE 的方式（然而，Fujisaki 和 Okamoto (1999) 的编译器在 ROM 中工作，而 Jiang 和 Gong (2004) 的 PAKE 在标准模型中工作），`B` 在加密 `c[B]` 中的随机性源自其 SPHF 密钥 `sk[B]`，因此可以由 `A` 重新计算（从而验证）。

Abdalla 等人 (2015b) 还展示了一个 BPR 安全版本的 KOY，其中 `B` 的加密是 CPA 安全的，而 `A` 的加密是 PCA 安全的，即仅针对明文检查攻击安全（直观上，解密预言机可以被仅识别加密值是否为固定挑战密码的预言机所替代）。

## 最小轮数 PAKE

Katz 和 Vaikuntanathan (2011) 表明 KOY 协议可以变为*非交互式*，即各方可以独立选择带有投影的 SPHF 哈希密钥，加密其密码，将加密和投影对发送给对方，然后各方可以使用接收到的投影密钥在本地对其陈述进行哈希，并使用自己的哈希密钥对对方的陈述进行哈希。如果 CCA PKE 拥有 SPHF，且投影密钥可以在没有（完整）陈述的情况下计算，这将成为可能。（此类 SPHF 从此被称为 *KV-SPHF*）。

Katz 和 Vaikuntanathan (2011) 在标准群中使用 Naor-Yung CCA PKE (Naor 和 Yung 1990) 实现了这一点，该 PKE 由两个 ElGamal 密文和 Sahai (1999) 的模拟可靠 NIZK（明文相等性）组成；在双线性映射群中使用决策线性 (DLIN) 假设和 Groth-Sahai NIZK (Groth 和 Sahai 2008)，生成的 PAKE 每方使用 70 个群元素。

Libert 和 Yung (2012) 将其减少到 32 个元素，随后 Jutla 和 Roy (2012) 展示了模拟可靠 NIZK 的一种放宽，在双线性映射曲线上的对称外部 Diffie-Hellman (SXDH) 假设下，实现了每方 20 个群元素的非交互式 BPR 模型 PAKE。

Benhamouda 等人 (2013) 随后展示了 Cramer-Shoup CCA PKE 的高效 KV-SPHF，在标准群中实现了非交互式 BPR 模型 PAKE，基于 DDH 安全，每方仅需 6 个群元素。

## 标准模型中的 UC PAKE

Canetti 等人 (2005) 通过在 KOY 协议的最后一轮添加密码重加密和模拟可靠 NIZK，展示了首个 UC PAKE（见第 10.5 节）。

Groce 和 Katz (2010) 推广了 Jiang 和 Gong (2004) 的 BPR 模型 PAKE 方案，并展示了其形式化为 UC PAKE-EA 的 UC 安全版本。Groce 和 Katz (2010) 的 UC PAKE-EA 在 Jiang 和 Gong (2004) 的 PAKE-EA 基础上增加了一个额外的加密流和明文相等性的模拟可靠 NIZK，其开销本质上与 Canetti 等人 (2005) 的 UC PAKE 在 KOY 协议 (Katz 等人 2001) 的 BPR 模型 PAKE 基础上增加的开销相同。

Katz 和 Vaikuntanathan (2011) 将他们的非交互式 BPR 模型 PAKE 扩展为非交互式 UC PAKE，方法是在 SPHF 中构建一个陷门（他们在 CRS 下加密哈希密钥，并添加一个模拟可靠 NIZK 证明加密的哈希密钥对应于投影密钥），以便模拟器甚至可以在*不正确*陈述上计算 SPHF 哈希值（回想一下模拟器不知道诚实方的密码）。他们的非交互式 UC PAKE 在标准群上基于 DLIN 安全，但这是一个可行性结果（(Jutla 和 Roy 2015) 估计每方需要超过 65 个群元素）。

Benhamouda 等人 (2013) 将此类 SPHF 形式化为*陷门 SPHF* (TSPHF)，并在 SXDH 下展示了更高效的 TSPHF 构造，实现了每方 11 个群元素的非交互式 UC PAKE。

## 自适应 UC PAKE

Abdalla 等人 (2009) 使用可提取和模棱两可 (`E`²) 承诺，将 Canetti 等人 (2005) 的 UC PAKE 升级到*自适应对手*设置（假设可靠擦除），但他们的构造使用了 Ω(`κ`²) 个群元素。

Abdalla 等人 (2013) 使用 SPHF 友好的 `E`² 承诺对此进行了改进，使得生成的自适应 UC PAKE（带擦除）是非交互式的，并在 SXDH 曲线上使用了 Ω(`κ`) 个元素。

随后 Jutla 和 Roy (2015) 展示了 Katz-Vaikuntanathan 非交互式 PAKE 的一个版本，该版本使用他们引入的*对偶系统*模拟可靠 NIZK 保持安全，在相同的 SXDH 设置下，实现了仅使用 4 个群元素的自适应 UC PAKE（带擦除）。

关于无擦除的自适应安全性，我们仅知晓 Canetti 等人 (2012) 基于 OT 的 PAKE，它使用 Θ(`κ`) 个 UC OT 实例。

## 10.7. PAKE 效率优化

第 10.3 节 和 第 10.4 节 中讨论的两个 EKE 版本，即 Bellare 等人 (2000) 的 EKE2 协议和 Boyko 等人 (2000) 的 PPK 协议，在假设理想化模型 IC 和 ROM 的情况下，被证明在 CDH 和/或 DDH 下安全。（回想一下，IC 此处代表群元素上的 IC；见第 10.3.5 节。）

在 第 10.6 节 中，我们讨论了标准模型中的 PAKE，但假设理想化模型的 PAKE 不限于 Bellare 等人 (2000) 和 Boyko 等人 (2000) 的结果。

EKE2 版本的 EKE (图 10.3) 最大的问题是它使用了群上的 IC，而 PPK 版本 (图 10.4) 使用了到群的哈希。此外，任一版本的完整证明都花了一些时间才出现和/或由后续工作开发。

Bresson 等人 (2003) 在 IC+ROM 模型下，基于 CDH 为 Bellare 和 Rogaway (2000) 的 *AuthA* 协议给出了 BPR 模型安全性证明，该协议曾被考虑用于 IEEE P1363.2 公钥密码学标准。

协议 AuthA 类似于 EKE2 (图 10.3)，不同之处在于 `A` 先发送 `g^x` 而不进行密码加密，但有一个第三协议流，`A` 发送密钥确认消息，例如 图 10.2 中的值 `τ`。关键在于，`B` 不能将其认证器 `γ` 附加到第二流，否则会存在离线攻击，因此 AuthA 意味着四轮相互 PAKE-EA，这与 Boyko 等人 (2000) 的 EKE 的三轮 PAKE-EA 版本 *PAK* 形成对比；MacKenzie (2001b, 2002) (见第 10.4.4 节)，它也节省了密码加密的一方，但来自响应方 `B`。

Bresson 等人 (2004) 还在 ROM 下基于 CDH 为 Boyko 等人 (2000) 的 PAKE-EA 变体展示了 BPR 模型安全性，该变体去掉了最后 `A` 到 `B` 的密钥确认流，实现了具有服务器到客户端认证的两流 PAKE。

Abdalla 和 Pointcheval (2005) 证明了 SPAKE2 在 ROM 中基于 CDH 假设具有 BPR 安全性，SPAKE2 是 EKE 的一个最小轮数版本，其流程类似于图 10.4 的协议 PPK，不同之处在于 CRS 由两个随机群元素 `M, N` 修正，且 `H(pw^A)` 和 `H(pw^B)` 分别被群元素 `M^(pwd[A])` 和 `N^(pw[B])` 替换。（假设密码被哈希到 `q` 上，并且必须以某种方式打破对称性，因为 `A` 和 `B` 不能使用相同的 CRS 元素。）

Jablon (1996) 的 SPEKE 协议以及 Hao 和 Shahandashti (2014) 提出了对 EKE 的如下变体：在用 DH 密钥交换实例化的 EKE 中，双方不再在密码下加密 `g^x` 和 `g^y`，而是可以使用设置为 `g = H(pw)` 的 DH 基 `g` 来运行 DH 密钥交换，其中 `H` 是映射到群上的 RO 哈希。

Haase 和 Labrique (2019) 提出了 SPEKE 的一种特定椭圆曲线实例化，称为 CPace，并被 IETF CFRG 在对称 PAKE 类别的竞赛中推荐采纳 (Smyshlyaev 2020)。

MacKenzie (2001a) 证明了 SPEKE 在 *反转加法 DDH* 假设下具有 BMP 模型安全性（如果模拟器针对每个被攻击会话获得*两个*测试密码查询），即元组 `(g^(1/x), g^(1/y), g^(1/(x+y)))` 与随机群元素三元组不可区分。

请注意，除了非标准安全假设外，SPEKE 需要哈希到群，而 SPAKE2 不需要；且 SPEKE 每方成本为 2vb 指数运算，而 SPAKE2 为 3fb+1vb，因此仅在无法利用预计算加速固定基指数运算的空间受限场景下，SPEKE 才开销更小。

然而，Pointcheval 和 Wang (2017) 提出了一个 SPEKE 变体，称为 TBPEKE，它通过设置 `g = M^(H(pw)) * N`（其中 `M, N` 是 CRS 中的两个（随机）群元素）同时解决了这两个问题。

在实践中获得关注的*非* EKE 变体的 PAKE 协议是 J-PAKE (Hao 和 Ryan 2010)，它被包含在 OpenSSL 库中。

Abdalla 等人 (2015a) 证明了 J-PAKE 在 ROM 中基于 DDH 变体具有 BPR 安全性，但 J-PAKE 似乎相较于 SPAKE2 或 TBPEKE 没有优势，因为它需要更多轮次，且带宽和计算量大约多 6 倍。

### 基于 RSA 的 PAKE

基于用 RSA 类 KEM 实例化的 EKE 来构建 PAKE 看似是一个有吸引力的选项，因为它可以创建一个开销不对称的 PAKE：如果客户端发送 `c[A] ← E(pw, (r^e mod N))`（针对随机密钥 `r`），服务端恢复 KEM 密钥为 `r ← [D(pw, c[A])]^d mod N`，那么如果指数 `e` 可以很短，这样的 PAKE 将支持弱客户端。

然而，如果 `(e, N)` 被篡改使得 `r^e mod N` 不是模 `N` 的随机整数，服务端一方就能作弊。

确实，随后几个基于 RSA 的 EKE 版本 (Bellovin 和 Merritt 1992; Lucks 1998) 都被攻破了 (Patel 1997; MacKenzie 等人 2000; Zhang 2004a)。

MacKenzie 等人 (2000)、Zhang (2004b) 和 Park 等人 (2007) 给出了安全版本（在 ROM 中基于 RSA 假设的 BPR 模型下），适用于长度递减的 `e`，但即使是 (Park 等人 2007) 也要求 `|e| = Ω(κ)`，且客户端必须测试 `e` 的素性。

基于 RSA 的 PAKE 提案包含一些可证明安全的研究 (Zhu 等人 2002; Wong 等人 2003; Catalano 等人 2004; Zhang 2004c; Gentry 等人 2005)，但它们要么客户端开销高，要么比使用素数阶群的 PAKE 需要更多轮次和带宽。

为弱客户端创建 PAKE 仍是一个未解之谜，但对基于 RSA 方案的兴趣似乎已减退，可能是因为任何客户端成本的节省都以固有的更高带宽为代价。

### RO 或 IC 模型中的 UC PAKE

Abdalla 等人 (2008) 证明了三轮 EKE 变体 AuthA (Bellare 和 Rogaway 2000; Bresson 等人 2003)（见上文）在 IC+RO 模型中基于 CDH 假设，甚至针对*自适应对手*且无需擦除，实现了 Canetti 等人 (2005) 的 UC PAKE 功能。

Bradley 等人 (2019a) 证明了两个实现 UC PAKE 的两轮 EKE 变体，一个是最小开销但处于 IC+RO 模型，另一个在 RO 模型但需要额外的指数运算。

Abdalla 等人 (2020) 提出了一种 UC PAKE 功能的“懒惰提取”松弛（见第 10.5 节），并证明了几个高效的最小轮数 EKE 版本，包括 SPAKE2、SPEKE、CPace 和 TBPEKE，在 ROM 中基于相应 BPR 模型证明中所用假设的 Gap 版本，实现了懒惰提取 UC PAKE 模型。

McQuoid 等人 (2020) 证明了使用特定两轮 Feistel 结构实现加密的 EKE2（见第 10.3.5 节）在 ROM 中基于 CDH 实现了 Canetti 等人 (2005) 的 UC PAKE 定义。

因此，目前最高效且最小轮数的 EKE 版本 EKE2 和 SPAKE2，分别在 CDH 和 GapDH 假设下实现了 UC PAKE 和懒惰提取 UC PAKE，其中按 McQuoid 等人 (2020) 实现的 EKE2 每方成本为 1fb+1vb 加 2 次映射到群上的 RO 哈希，SPAKE2 每方成本为 3fb+1vb。

## 10.8. 非对称 PAKE：面向客户端-服务端设置的 PAKE

Bellovin 和 Merritt (1993) 为客户端-服务端设置提出了*增强型* PAKE (aPAKE)，其中服务端持有密码*哈希 hpw* = *f* (*pw*) 而非密码本身，协议检查 `C` 和 `S` 分别持有 `pw^C` 和 `hpw^S` 使得 `f(pwd^C) = (pw^S)`，而不是检查 `pw^C` 和 `pw^S` 使得 `pw^C = pw^S`。

如果 *f* 是*紧致*单向函数 (OWF) (Benhamouda 和 Pointcheval 2013)，即对于任意域 *D*，给定 *y* = *f* (*x*)（其中 *x* ←[$] *D*），要以至少 *ϵ* 的概率找到 *x* 需要 Ω(*ϵ|D|*) 的工作量，那么攻破 `S` 所持 `hpw` 的攻击者只能以 Ω(2^(*d*)) 的工作量恢复密码 *pw*，其中 *d* 是密码熵。

这是最优的，因为给定 `hpw` 的攻击者可以通过在输入 `pw`^∗ 和 `hpw` 上分别模拟 aPAKE 执行来离线测试任意 `pw`^∗。

在 ROM 中，可设 *f* (*x*) = `H(x)`，但此时 aPAKE 协议将依赖于 `H` 的电路复杂度。

然而，设 *f* (*x*) = *g*^(`H(x)`) 在通用群模型和 ROM 中仍给出紧致 OWF (Benhamouda 和 Pointcheval 2013)，并允许高效 aPAKE 检查 `C` 持有的 `hpw^C = H(pw^C)` 是否为 `S` 持有的 `hpw^S` 的离散对数。

这可以使用 Diffie-Hellman KEM 或 DL 知识的零知识证明来完成，无论哪种选择，这种 DL 关系验证都必须受到保护以抵御离线攻击。
