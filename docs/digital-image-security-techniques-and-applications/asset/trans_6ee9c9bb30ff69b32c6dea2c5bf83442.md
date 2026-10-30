
现在，c₀ 和 c₁ 是复数；因此，它们可以用等价的极坐标表示：

```
c₀ := r₀ e^{i φ₀},
 c₁ := r₁ e^{i φ₁},  (3.3)
```

或，

```
|ψ⟩ = cos θ |0⟩ + e^{i φ} sin θ |1⟩,
 φ := φ₁ - φ₀, r₀ = cos θ, r₁ = sin θ  (3.4)
```

其中 rᵢ 为振幅，φᵢ 为相位。这样复系数可以表示为单位球面上的点。选择球面而非圆的逻辑在于两个复系数共有四个变量。然而，由于公式 3.2，只有三个变量是独立的。因此，需要一个三维球面才能真正表示任意的量子比特态。

传统上，在量子比特的布洛赫球表示中，|0⟩ 态，即 c₀ = 1 且 c₁ = 0 的态矢量，表示在单位球的北极。|1⟩ 态，即 c₀ = 0 且 c₁ = 1 的态矢量，表示在单位球的南极。见图 3.2。

### 3.3.4.3 Measurement

在此阶段需要注意量子计算中基的概念，因为这对于理解后面出现的一些内容是必要的。根据玻恩规则，测量量子比特态 |ψ⟩ 在态 |x⟩ 中的概率 P(x) 将由公式 3.5 给出：

```
P(x) := |⟨x | ψ⟩|²  (3.5)
```

![](img/6e4271af21d9a195003ab8711aa79d27_63_0.png)

图 3.2 量子比特的布洛赫球表示。

其中左角括号称为 bra，是行向量的简写，⟨Bra | ket⟩ 是行向量元素与表示 ket 的列向量的复共轭的内积。

因此，在态 |0⟩ 中测量 |0⟩，即 |⟨0|0⟩|²，将给出概率 1。类似地，在态 |1⟩ 中测量 |0⟩，即 |⟨1|0⟩|²，将给出概率 0（正交）。

如果 |ψ⟩ = 1/√2 |0⟩ + 1/√2 |1⟩：

|⟨0|ψ⟩|² = |⟨0| 1/√2 |0⟩ + 1/√2 |1⟩|² (3.6)

化简后，

|⟨0|ψ⟩|² = 1/2 |⟨0|0⟩ + ⟨0|1⟩|² = 1/2 (3.7)

测量可以在量子比特态 |0⟩ 或 |1⟩ 或任何其他正交态中进行。这样的正交态集合称为基。如果基态为 |0⟩ 和 |1⟩，则称为计算基或 z 基。

另一种正交态的集合是 |+⟩ = 1/√2 |0⟩ + 1/√2 |1⟩ 和 |−⟩ = 1/√2 |0⟩ − 1/√2 |1⟩。它被称为 x 基。

### 3.3.4.4 Single qubit gates

现在，为了让量子比特执行某些计算，我们必须有转换它们的方法。这些转换方法称为“门” [25]。

由于玻恩规则，态矢量 |ψ⟩ 总是保持在布洛赫球的表面上，因为 ||ψ|| = 1；然而，态矢量可以自由地在球面上旋转。单量子比特门不过是态矢量在布洛赫球上的旋转。标准的单量子比特门如下：

- 1. X-gate: Rotates |ψ⟩ to |1⟩ and vice versa. It is rotation by π around the x-axis.
- 2. Y-gate and Z-gate: perform rotations by π radians around y and z-axis of the Bloch sphere, respectively.
- 3. H-gate: This makes a rotation around the line between the x and z-axis.
  - If applied to |0⟩, generates equal superposition, i.e., 1/√2 |0⟩ + 1/√2 |1⟩ state.
  - If applied to |1⟩, generates equal superposition, i.e., 1/√2 |0⟩ − 1/√2 |1⟩ state.
- 4. I-gate: Identity gate; does not change the state. X applied twice becomes I gate.
- 5. S-gate: It does a quarter-turn around the Bloch sphere. S applied twice becomes Z gate.
- 6. Rx-gate: Rotation around x-axis by a specified angle.
- 7. Ry-gate: Rotation around y-axis by a specified angle.
- 8. Rz-gate: Rotation around y-axis by a specified angle.

### 3.3.4.5 Two qubit gates

现在，这里简要讨论双量子比特门。由于单个量子比特只有两个基态，即 |0⟩ 或 |1⟩，两个量子比特可以有四个基态，即 |00⟩、|01⟩、|10⟩ 和 |11⟩。一般而言：

|ψ⟩ = c00|00⟩ + c01|01⟩ + c10|10⟩ + c11|11⟩,  (3.8)

其中，

‖c00‖² + ‖c01‖² + ‖c10‖² + ‖c11‖² = 1,  (3.9)
c00, c01, c10 and c11 ∈ ℂ

双量子比特门通常是单量子比特门的受控版本。通过示例会更清楚。标准的双量子比特门是 C-NOT 或 CX 门。CX 门的真值表在表 3.3 中给出，其中 q0 为控制量子比特，q1 为输出量子比特，q'1 为应用 CX 门后输出的状态。CX 与 H 门结合可以为我们构建纠缠量子比特对。纠缠下双量子比特系统的状态为 1/√2 |00⟩ + 1/√2 |11⟩。参见图 3.3。

表 3.3 CX 门的真值表

| q0 | q1 | q'1 |
|----|----|-----|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

![](img/6e4271af21d9a195003ab8711aa79d27_65_0.png)

图 3.3 纠缠量子比特对的生成。

### 3.3.4.6 Multi-qubit gates

多量子比特门是双量子比特门的扩展。例如，双量子比特 C-NOT 门可以定义为有两个控制量子比特和一个输出量子比特。因此，输出量子比特的状态只有在两个控制量子比特都处于 |1⟩ 态时才会改变。

### 3.3.5 Quantum circuit

到目前为止，我们在没有正确介绍的情况下使用了术语 *quantum circuit*，因此我们将在此处进行介绍。

根据 IBM Quantum:

> > 量子电路是有序的量子门、测量和重置序列，所有这些都可能取决于实时经典计算的数据并使用这些数据 [26]。

一个很好的量子电路示例，也与本章相关，是量子隐形传态电路。量子隐形传态电路是在不违反量子力学基本原理的情况下，将量子比特的状态从发送者（Alice）传输到接收者（Bob）的方法。

### 3.3.6 Quantum teleportation circuit

首次创建于 1993 年 [27]，量子隐形传态电路是量子密码学最重要的组成部分之一。为了实现量子隐形传态，发送者（Alice）和接收者（Bob）需要第三个人（通常称为 Telamon），以使他们各自从一对纠缠量子比特中各获得一个量子比特。发送者（Alice）和接收者（Bob）都需要对其量子比特执行某些门操作，并在经典信道上交换某些信息，以便在 Bob 处接收 Alice 量子比特的状态。

- **Step 1:** Suppose Alice is trying to send the state |ψ⟩ of her qubit q₀ to Bob.
- **Step 2:** The third party (Telamon) creates an entangled pair of qubits and gives one qubit (qₐ) to Alice and one qubit (q_b) to Bob.
- **Step 3:** Alice is required to apply a CX gate to qₐ with q₀ as the control qubit.
- **Step 4:** Alice is required to apply an H gate to q₀.
- **Step 5:** Alice is required to perform measurement of both her qubits and save the result in two classical bits, then send the two classical bits to Bob through a classical channel.
- **Step 6:** Now the receiver, Bob, who is receiving the qubits q_b, applies the gates as per Table 3.4.
- **Step 7:** After Step 6, Bob will have the state of his qubit same as |ψ₀⟩.

表 3.4 Bob 的操作

| Bits | Action |
|------|--------|
| 00 | Nothing |
| 01 | X |
| 10 | Z |
| 11 | ZX |

![](img/6e4271af21d9a195003ab8711aa79d27_67_0.png)

图 3.4 量子隐形传态电路。

量子隐形传态的量子电路如图 3.4 所示。给出的图演示了经典比特为 00 的情况下的量子隐形传态电路，因此 Bob 无需操作。图中 crz 和 crx 通道分别用于在应用 Z、X 门后保留测量结果。

## 3.4 QUANTUM COMMUNICATION

量子通信是上一节讨论的量子隐形传态的自然且必要的扩展。量子通信基本上利用了 3.3.2 小节中列举的量子物理定律。据预测，量子通信未来将演变为量子互联网。这样的网络将类似于经典网络；然而，该网络的端节点将是栖息着量子比特的量子处理器，所交换的信息将是量子信息 [28]。

## 3.5 SECURITY IN POST-QUANTUM ERA

我们已全面介绍了该主题的基本要素，从量子力学基础、量子计算、量子计算的门模型、标准门和量子
