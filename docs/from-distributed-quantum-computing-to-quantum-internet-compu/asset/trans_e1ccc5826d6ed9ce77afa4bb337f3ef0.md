

如果 \( A \) 希望 \( B \) 执行 \( H \) 门而不是 \( Z \) 门会怎样？如前所述，\( A \) 拥有 \( |\psi\rangle \) 并向 \( B \) 发送一个加密量子态，即选择 \( a, b \in \{0, 1\} \) 并发送 \( |\psi'\rangle = X^a Z^b |\psi\rangle \)，以使 \( B \) 在该状态上应用 \( H \)。\( B \) 对其执行 \( H \) 以得到 \( H |\psi'\rangle \) 并将其发送回 \( A \)。\( A \) 在接收到 \( H |\psi'\rangle \) 后，对其应用 \( Z^a X^b \)（注意，此解密操作与用于 \( X \) 和 \( Z \) 门的 \( Z^b X^a \) 不同）以得到：

```
Z^a X^b \left( H \, | \psi' \rangle \right) = Z^a X^b H X^a Z^b | \psi \rangle
= Z^a X^b Z^a H Z^b | \psi \rangle \qquad \text{(since } H X^a = Z^a H \text{)}
= Z^a X^a Z^b X^b H \, | \psi \rangle \qquad \text{(since } H Z^b = X^b H \text{)}
= \left\{\begin{array}{ll} H \, | \psi \rangle, \quad & \text{if } a=0, b=0 \\ XXX H \, | \psi \rangle = H \, | \psi \rangle, \quad & \text{if } a=0, b=1 \\ ZZ H \, | \psi \rangle = H \, | \psi \rangle, \quad & \text{if } a=1, b=0 \\ ZXZX H \, | \psi \rangle = - Z X X Z H \, | \psi \rangle = - H \, | \psi \rangle, \quad & \text{if } a=1, b=1 \end{array}\right.
```

忽略全局相位 "-"，\( A \) 然后得到所需的 \( H \, | \psi \rangle \)。

如果 \( A \) 希望 \( B \) 执行 \( P \) 门而不是 \( Z \) 门会怎样？\( P \) 门或相位门采用以下形式：\(\begin{bmatrix} 1 & 0 \\ 0 & i \end{bmatrix}\)，即 \( P \, | 0 \rangle = | 0 \rangle \)，且 \( P \, | 1 \rangle = i \, | 1 \rangle \)。如前所述，\( A \) 拥有 \( |\psi\rangle \) 并向 \( B \) 发送一个加密量子态，即选择 \( a, b \in \{0, 1\} \) 并发送 \( |\psi'\rangle = X^a Z^b |\psi\rangle \)，以使 \( B \) 在该状态上应用 \( P \)。\( B \) 对其执行 \( P \) 以得到 \( P \, |\psi'\rangle \) 并将其发送回 \( A \)。\( A \) 在接收到 \( P \, |\psi'\rangle \) 后，对其执行 \( Z^{a \oplus b} X^a \)（注意这与上面的情况不同）以得到：

```
Z^{a \oplus b} X^a P \, | \psi' \rangle = Z^{a \oplus b} X^a P X^a Z^b \, | \psi \rangle
= (-i)^a Z^{a \oplus b} X^a Z^a X^a P Z^b \, | \psi \rangle \qquad \text{(since } P X^a = (-i)^a Z^a X^a P \text{)}
= (-i)^a Z^{a \oplus b} X^a Z^a X^a Z^b P \, | \psi \rangle \qquad \text{(since } P Z^b = Z^b P \text{)}
= \left\{\begin{array}{ll} P \, | \psi \rangle, \quad & \text{if } a=0, b=0 \\ ZZ P \, | \psi \rangle = P \, | \psi \rangle, \quad & \text{if } a=0, b=1 \\ (-i) X Z X X P \, | \psi \rangle = i X Z X X P \, | \psi \rangle = i P \, | \psi \rangle, \quad & \text{if } a=1, b=0 \\ (-i) X X Z X P \, | \psi \rangle = i X Z X X P \, | \psi \rangle = i P \, | \psi \rangle, \quad & \text{if } a=1, b=1 \end{array}\right.
```

忽略全局相位 "i"，\( A \) 然后得到所需的 \( P \, | \psi \rangle \)。

如果 \( A \) 希望 \( B \) 执行 CNOT 门会怎样？\( A \) 现在有一个双量子比特态 \( |\psi\rangle \) 并向 \( B \) 发送加密量子态，即选择 \( a, b, c, d \in \{0, 1\} \) 并发送 \( |\psi'\rangle = X^a Z^b \otimes X^c Z^d |\psi\rangle \)，以使 \( B \) 在该状态上应用 CNOT。\( B \) 对其执行 CNOT 以得到 CNOT \( |\psi'\rangle \) 并将其发送回 \( A \)。\( A \) 在接收到 CNOT \( |\psi'\rangle \) 后，对其应用 \( Z^{b+d} X^a \otimes Z^d X^{a+c} \) 以得到：

(Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT} |\psi'\rangle
= (Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT}((X^a Z^b \otimes X^c Z^d) |\psi\rangle)
= (Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT}(X^a \otimes X^c)(Z^b \otimes Z^d) |\psi\rangle
= (Z^{b+d}X^a \otimes Z^d X^{a+c})\text{CNOT}(X^a \otimes \mathbf{I})(\mathbf{I} \otimes X^c)(Z^b \otimes \mathbf{I})(\mathbf{I} \otimes Z^d) |\psi\rangle
= (Z^{b+d}X^a \otimes Z^d X^{a+c})(X^a \otimes X^a)(\mathbf{I} \otimes X^c)\text{CNOT}(Z^b \otimes \mathbf{I})(\mathbf{I} \otimes Z^d) |\psi\rangle
(since \text{CNOT}(X^a \otimes \mathbf{I}) = (X^a \otimes X^a)\text{CNOT and CNOT}(\mathbf{I} \otimes X^c) = (\mathbf{I} \otimes X^c)\text{CNOT})
= (Z^{b+d}X^a \otimes Z^d X^{a+c})(X^a \otimes X^a)(\mathbf{I} \otimes X^c)(Z^b \otimes \mathbf{I})(Z^d \otimes Z^d)\text{CNOT} |\psi\rangle
(since \text{CNOT}(Z^b \otimes \mathbf{I}) = (Z^b \otimes \mathbf{I})\text{CNOT and CNOT}(\mathbf{I} \otimes Z^d) = (Z^d \otimes Z^d)\text{CNOT})
= (Z^{b+d}X^a X^a Z^b Z^d \otimes Z^d X^{a+c} X^a X^c Z^d)\text{CNOT} |\psi\rangle = \text{CNOT} |\psi\rangle

我们反复使用了恒等式 \(AB \otimes CD = (A \otimes C)(B \otimes D)\)。因此，\(A\) 得到所需的 \(\text{CNOT} |\psi\rangle\)。请注意，我们也可以使用 \(Z^{b \oplus d}X^a \otimes Z^d X^{a \oplus c}\) 并得到相同的结果，将 “+” 替换为 “\(\oplus\)。”

如果 \(A\) 希望 \(B\) 执行 \(R\) 门会怎样？请注意，\(R\) 门是 \(\begin{bmatrix} 1 & 0 \\ 0 & e^{i\pi/4} \end{bmatrix}\)，即 \(R|0\rangle = |0\rangle\)，且 \(R|1\rangle = e^{i\pi/4}|1\rangle\)。如果我们使用一直在使用的方法并配合适当的操作来恢复结果会怎样？假设 \(A\) 现在有一个单量子比特态 \(|\psi\rangle\) 并向 \(B\) 发送加密量子态，即选择 \(a, b \in \{0, 1\}\) 并发送 \(|\psi'\rangle = X^a Z^b |\psi\rangle\)，以使 \(B\) 在该状态上应用 \(R\)。\(B\) 然后将 \(R|\psi'\rangle\) 发送回 \(A\)。\(A\) 如何从 \(R|\psi'\rangle\) 恢复 \(R|\psi\rangle\)？

如 Broadbent [2015] 所述，这并不那么直接，因为我们有：

\(R |\psi'\rangle = R X^a Z^b |\psi\rangle
= \begin{cases} R |\psi\rangle, & \text{if } a = 0, b = 0 \\ RZ |\psi\rangle = ZR |\psi\rangle, & \text{if } a = 0, b = 1 \\ RX |\psi\rangle = XZPR |\psi\rangle, & \text{if } a = 1, b = 0 \\ RXZ |\psi\rangle = XZPRZ |\psi\rangle = XZPZR |\psi\rangle \\ = XPZZR |\psi\rangle = XPR |\psi\rangle, & \text{if } a = 1, b = 1 \end{cases}\)

由于 \(RZ = ZR\)，\(RX = XZPR\)（忽略全局相位），且 \(ZP = PZ\)，即 \(R |\psi'\rangle = X^a Z^a Z^b P^a R |\psi\rangle\)。这意味着当 \(a=0\) 时，\(A\) 只需对 \(R |\psi'\rangle\) 应用 \(Z^b\) 即可得到 \(R |\psi\rangle\)：\(Z^b (R |\psi'\rangle) = Z^b (Z^b R |\psi\rangle) = R |\psi\rangle\)。但当 \(a=1\) 时，我们在 \(R\) 前面有额外的 \(P\)。需要对 \(XPR |\psi\rangle\) 应用 \(ZP\) 以移除 \(P\)，例如当 \(a=1, b=1\) 时，可以对 \(XPR |\psi\rangle\) 应用 \(ZPX\) 以得到 \(ZPX(XPR |\psi\rangle) = ZPPR |\psi\rangle = ZZR |\psi\rangle = R |\psi\rangle\)，因为 \(Z = PP\)。但是，请回顾我们假设客户端受限且不能自行执行 \(P\)（因此它正在使用更强大的 \(B\) 来执行此操作！），因此不能执行 \(ZP\)

![](img/fb3eb7e935470a2da12b03f528f097ee_156_0.png)

图 5.1 \(R\)-门协议，其中服务器的输出为 \(|\psi''\rangle = X^{a \oplus b} Z^{c \oplus (c \oplus b \oplus 1) \oplus b \oplus d \oplus y} R |\psi\rangle\)。客户端随机且均匀地选择 \(y, d \in \{0, 1\}\)。这是一种让服务器以受客户端控制的方式执行 \(P\) 操作的方法。这可以称为 \(R\)-门“小工具”。

要移除 $P$。这有两种解决方法。一种方法是要求 $B$ 执行此额外的 $P$ 操作，如前所述，但这需要在 \(a=1\) 和 \(a=0\) 时都进行（在 \(a=0\) 的情况下使用一个虚拟量子比特，以便 \(B\) 不知道 \(a\) 是否为 1），这涉及双向量子通信。

另一种方法是使用下面概述的 Broadbent [2015] 的协议，该协议除了发送 \(X^a Z^b |\psi\rangle\) 外，还发送一个随机从四个可能状态中选择的辅助量子比特态，以及一个经典比特，如下所述。服务器发送回结果和一个经典比特以解密结果。实现该协议的电路如图 5.1 所示。

客户端（例如 $A$）随机且均匀地选择 \(a, b \in \{0, 1\}\) 以将状态 \(|\psi\rangle\) 加密为 \(X^a Z^b |\psi\rangle\)。$A$ 将 \(X^a Z^b |\psi\rangle\) 发送给服务器，即 $B$。此外，$A$ 随机且均匀地选择 \(y, d \in \{0, 1\}\)，计算 \(x = a \oplus y\)，并将 $x$ 和量子态 \(Z^d P^y |+\rangle\) 发送给服务器 $B$。这是一种让服务器以受客户端控制的方式执行 $P$ 操作，同时不向服务器泄露任何关于 $a$ 的信息的方法（请记住我们上面提到，当 $a=1$ 时，我们需要应用一个额外的 $P$，而此电路使服务器执行此操作——要看到这一点，当 $a=0$ 时，$x = a \oplus y = y$，查看图 5.1 中从 \(|+\rangle\) 到 \(|\psi''\rangle\) 的量子线上的门，当 \(x=y=1\) 时，我们有 \(P^x Z^d P^y = PZ^d P = PPZ^d = ZZ^d\)，当 \(x=y=0\) 时，我们有 \(P^x Z^d P^y = Z^d\)，因此不应用 $P$，但当 $a=1$ 时，$x = 1 \oplus y$，即要么 \(x=0\) 且 \(y=1\)，要么 \(x=1\) 且 \(y=0\)，这意味着 \(P^x Z^d P^y = PZ^d\) 或 \(P^x Z^d P^y = Z^d P\)，因此应用了操作 $P$；请注意，即使服务器知道 $x$，它也不知道 $a$ 是什么，因为 $y$ 可以是 0 或 1）。

请注意，当 \(y=1\) 时，客户端 $A$ 实际上并不将 $P$ 应用于 \(|+\rangle\)，但根据我们的假设，我们假设客户端可以从以下状态中随机且均匀地选择一个：\(\{|+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle), |-\rangle = \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle), |+_i\rangle = \frac{1}{\sqrt{2}}(|0\rangle + i|1\rangle), |-_i\rangle = \frac{1}{\sqrt{2}}(|0\rangle - i|1\rangle)\}\)（我们之前陈述的假设 1），这等同于客户端随机且均匀地选择 \(y, d \in \{0, 1\}\) 并计算 \(Z^d P^y |+\rangle\)，因为：

