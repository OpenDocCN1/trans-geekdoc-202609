

对另外两个 qutrit 进行了测量，但未告知此方。可以看出，在不知道另外两个 qutrit 的情况下，可能的状态，即另外两个 qutrit，可以是九种组合中的任意一种：|00⟩、|01⟩、|02⟩、|10⟩、|11⟩、|12⟩、|20⟩、|21⟩ 和 |22⟩，而此方的 qutrit 被测量为 |0⟩、|1⟩ 或 |2⟩ 的概率相等（即 (α² + β² + γ²)/3）。

但现在，假设某人持有三个份额中的任意两个，比如说最后两个 qutrit。那么，上述编码可以改写如下：

```
α(|000⟩ + |111⟩ + |222⟩) + β(|012⟩ + |120⟩ + |201⟩) + γ(|021⟩ + |102⟩ + |210⟩)
= α |000⟩ + β |012⟩ + γ |021⟩ + α |111⟩ + β |120⟩ + γ |102⟩ + α |222⟩
+ β |201⟩ + γ |210⟩
= |0⟩ ⊕ (α |00⟩ + β |12⟩ + γ |21⟩) + |1⟩ ⊕ (α |11⟩ + β |20⟩ + γ |02⟩)
+ |2⟩ ⊕ (α |22⟩ + β |01⟩ + γ |10⟩)
```

然后，无论第一个 qutrit 是什么，此人实际上都可以获取秘密 qutrit，即针对三个不同状态的振幅，例如，如果第一个 qutrit 是 |0⟩，那么将剩余的两个 qutrit |00⟩ 视为“|0⟩”，|12⟩ 视为“|1⟩”，|21⟩ 视为“|2⟩”，那么此人实际上拥有秘密 qutrit：α “|0⟩” + β “|1⟩” + γ “|2⟩”。类似地，如果第一个 qutrit 是 |1⟩ 或 |2⟩，则使用不同的映射。由于剩余的两个 qutrit 在第一个 qutrit 的不同情况下不同，假设第一个 qutrit 被测量为 |1⟩，如果此人测量并得到 |20⟩ 等结果，那么此人也知道第一个 qutrit 是 |1⟩。

我们仅仅是触及了表面——Cleve 等人 [1999] 对秘密共享方案的理论性质提供了更深入的分析和定理。

在秘密共享领域，还有许多最近的进展，例如 Long 等人 [2021] 中的 (3,5)-阈值方案，以及 Tsai 等人 [2022] 和 Zhang 等人 [2019] 等其他成果，仅举几例。

## 3.2.8 量子无迟移传输（OT）

OT 是允许数据传输或查询回答的问题，其方式是保持某些保密性或隐私性质。更具体地说，假设我们有两方 A 和 B，A 拥有一个包含两个项目 d₀ 和 d₁（每个均为 n 位字符串，例如）的数据库，且 (i) B 想要检索两个项目中的一个，但不希望 A 知道它检索了哪一个，从而保护其隐私，(ii) A 可以确信 B 不会同时获得两个项目。A 拥有两个项目的特殊情况称为 1-2 OT。对 (i) 的一个简单解决方案是让 A 直接将所有（或两个）项目（或其整个数据库）发送给 B，但这将不满足 (ii)。

我们考虑 1-2 OT 协议，使用 Vidick 和 Wehner 提出的方案中的思想。18 以下，A 拥有项目 d₀, d₁ ∈ {0, 1}ⁿ，B 正在请求一个项目 y ∈ {0, 1}。目标是让协议为 B 计算 f_B((d₀, d₁), y) = d_y，为 A 计算 f_A((d₀, d₁), y) = ⊥。

- 1. A 选择一个随机的 2n 位比特串 x = x₁ ... x₂ₙ ∈ {0, 1}²ⁿ 和一个随机的基串 θ = θ₁ ... θ₂ₙ ∈ {0, 1}²ⁿ，向 B 发送在所选基中编码的比特（类似于我们见过的 BB84），作为量子比特 Hθ₁|x₁⟩、...、Hθ₂ₙ|x₂ₙ⟩。
- 2. B 在随机基（计算基或 Hadamard 基）中测量每个接收到的量子比特。B 使用的基记录为 θ′ = θ′₁ ... θ′₂ₙ。测量结果记录在字符串 x′ = x′₁ ... x′₂ₙ 中。
- 3. A 和 B 都等待时间 t（等待足够长的时间，使 B 的量子内存“过期”（假设它会过期！），这样 B 在下一步之前就不能拥有接收到的量子比特——它必须在那时之前测量量子比特并存储结果——这是一个安全要求，因为 B 需要在知道 A 的编码基串之前测量其接收到的量子比特）。
- 4. 时间 t 过后，A 假设 B 已完成测量，并向 B 发送基串 θ；B 确定其使用与 A 相同的基的索引集合，即 S = {j|θ_j = θ′_j }。B 设置 S_y = S 和 S_{1−y} = {1, ... , 2n}\S。B 向 A 发送 (S₀, S₁)——我们假设对于足够大的 n，|S₀| = |S₁| = n。
- 5. A 向 B 发送 d′₀ = d₀ ⊕ x_{S₀} 和 d′₁ = d₁ ⊕ x_{S₁}，其中 ⊕ 是模 2 的按位加法，x_{S₀} = x_{k₁} ... x_{kₙ}，其中 k_i ∈ S₀，x_{S₁} 类似定义。注意 d′₀ 和 d′₁ 是 d₀ 和 d₁ 的加密值，B 只能解密其中一个。
- 6. A 然后输出 ⊥，B 输出 d′_y ⊕ x′_{S_y} 。

可以看出，该协议正确计算了上面的 f_A 和 f_B：A 在协议结束时输出 ⊥，B 计算出其想要的结果：

```
d′_y ⊕ x′_{S_y} = (d_y ⊕ x_{S_y}) ⊕ x′_{S_y} = d_y
```

这是因为 x_{S_y} ⊕ x′_{S_y} = 0，即 x_{S_y} = x′_{S_y}，因为 S = {j|θ_j = θ′_j }，并且根据上面的步骤 (4)，S_y = S，A 和 B 对 S_y 中索引的所有比特都使用了相同的基。Vidick 和 Wehner 对安全性质提供了更详细的讨论，但我们可以看到，在步骤 (3) 中，如果他们等待的时间不够长，B 可以将量子比特保留在内存中，直到它从 A 接收到编码基 θ，然后以与 A 相同的基测量所有量子比特，然后像步骤 (4) 那样向 A 发送 (S₀ = {1, ... , n}, S₁ = {n + 1, ... , 2n})，当 A 像步骤 (5) 那样向 B 发送 d′₀ 和 d′₁ 时，B 可以同时计算出 d₀ 和 d₁，因为对于 y = 0 和 y = 1 均有 x_{S_y} ⊕ x′_{S_y} = 0！为了确保 B 在发送 θ 之前已经完成测量，另一种方法是让 B 测量并使用比特承诺协议承诺其测量比特。由于在步骤 (5) 中 A 将两个数据项（albeit 加密形式）都发送给了 B，因此 A 不知道 B 请求了什么。请注意，该协议与 BB84 协议有相似之处，因为它基本上使用在相同基中测量的比特作为共享密钥。还有推广到 1-N OT，例如量子 OT 的综述见 [Santos et al., 2022]。

## 3.2.9 讨论

我们已研究了多方之间的若干量子协议。许多协议具有密码学性质，并在量子密码学中被广泛讨论，但我们概述了其中一些，因为它们在分布式计算环境中将很有用。这些也是相当“经典”的协议，自那时以来已有许多新进展。但希望本合集能提供一系列量子协议的概述，并让人了解其中涉及的高度技术性推理。

## 3.3 总结

一般来说，纠缠不是通信的替代品。但我们已经看到，如果不允许经典通信，纠缠可以实现某些没有纠缠就不可能进行的分布式计算；如果允许经典通信，那么借助纠缠，执行某些分布式计算所需的经典通信比特会更少。但通信复杂度的降低并非总是如此，即不适用于任何分布式计算。¹⁹ 我们还研究了许多有趣的量子协议，它们在经典分布式计算环境中有类似物。对于我们已见过的问题，还有其他更高级的协议，以及一些我们未考虑的协议，例如量子多方计算。我们看到，共享纠缠态是许多这些协议中的关键思想。这些协议的更深入分析也给出在原始引用论文中，我们未在本章中提供。

¹⁹ 例如，Elkin 等人 [2014] 的工作表明，节点（在网络中）共享纠缠和发送量子信息的能力，不能显著加快（与经典设置相比）某些问题（例如计算最小生成树和最短路径）的分布式算法。

## 参考文献

Dorit Aharonov, André Chailloux, Maor Ganz, Iordanis Kerenidis, and Loïck Magnin. A simpler proof of the existence of quantum weak coin flipping with arbitrarily small bias. SIAM Journal on Computing, 45(3):633–679, 2016.

¹⁹ For example, the work by Elkin et al. [2014] showed that the ability of nodes (in a network) to share entanglement and to send quantum information cannot help significantly to speed up (compared to the classical setting) distributed algorithms for certain problems such as computing the minimum spanning tree, and shortest paths.

Andris Ambainis. A new protocol and lower bounds for quantum coin flipping. Journal of Computer and System Sciences, 68(2):398–416, 2004.

A. Ambainis, H. Buhrman, Y. Dodis, and H. Rohrig. Multiparty quantum coin flipping. In Proceedings of the 19th IEEE Annual Conference on Computational Complexity, 2004, pages 250–259, 2004. doi: 10.1109/CCC.2004.1313848.

Myrto Arapinis, Nikolaos Lamprou, Elham Kashefi, and Anna Pappa. Definitions and security of quantum electronic voting. ACM Transactions on Quantum Computing, 2(1), Apr 2021. ISSN 2643-6809. doi: 10.1145/3450144.

Atul Singh Arora, Jérémie Roland, and Stephan Weis. Quantum weak coin flipping. In Proceedings of the 51st Annual ACM SIGACT Symposium on Theory of Computing, STOC 2019, pages 205–216, New York, NY, USA, 2019. Association for Computing Machinery. ISBN 9781450367059. doi: 10.1145/3313276.3316306.

Michael Ben-Or and Avinatan Hassidim. Fast quantum byzantine agreement. In Proceedings of the Thirty-Seventh Annual ACM Symposium on Theory of Computing, STOC ’05, pages 481–485, New York, NY, USA, 2005. Association for Computing Machinery. ISBN 1581139608. doi: 10.1145/1060590.1060662.

Guido Berlín, Gilles Brassard, Félix Bussières, Nicolas Godbout, Joshua A. Slater, and Wolfgang Tittel. Experimental loss-tolerant quantum coin flipping. Nature Communications, 2(1):561, 2011.

Manuel Blum. Coin flipping by telephone a protocol for solving impossible problems. SIGACT News, 15(1):23–27, Jan 1983. ISSN 0163-5700. doi: 10.1145/1008908.1008911.

Anne Broadbent and Alain Tapp. Information-theoretic security without an honest majority. In Kaoru Kurosawa, editor, Advances in Cryptology –ASIACRYPT 2007, pages 410–426, Berlin, Heidelberg, 2007. Springer-Verlag.

Harry Buhrman, Richard Cleve, Serge Massar, and Ronald de Wolf. Nonlocality and communication complexity. Reviews of Modern Physics, 82:665–698, Mar 2010. doi: 10.1103/RevModPhys.82.665.

A. Chailloux and I. Kerenidis. Optimal quantum strong coin flipping. In IEEE 50th Annual Symposium on Foundations of Computer Science (FOCS 2009), Los Alamitos, CA, USA, Oct 2009. IEEE Computer Society. doi: 10.1109/FOCS.2009.71.

David Chaum. The dining cryptographers problem: unconditional sender and recipient untraceability. Journal of Cryptology, 1(1):65–75, 1988.

Yi-Peng Chen, Jing-Yang Liu, Ming-Shuo Sun, Xing-Xu Zhou, Chun-Hui Zhang, Jian Li, and Qin Wang. Experimental measurement-device-independent quantum key distribution with the double-scanning method. Optics Letters, 46(15):3729–3732, Aug 2021.

Vicent Cholvi. Quantum byzantine agreement for any number of dishonest parties. Quantum Information Processing, 21(4):151, 2022.

