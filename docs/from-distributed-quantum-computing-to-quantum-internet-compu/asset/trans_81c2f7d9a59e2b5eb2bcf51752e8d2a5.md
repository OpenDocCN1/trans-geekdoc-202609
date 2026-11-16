

其他保真度的定义，但为了我们在此处的讨论，我们使用刚才给出的那个定义。

注意，假设 \(|\psi\rangle = \alpha|0\rangle + \beta|1\rangle\)，则其密度算符表示为

\(\rho = |\psi\rangle \langle \psi| = (\alpha|0\rangle + \beta|1\rangle)(\alpha^*\langle 0| + \beta^*\langle 1|)\)
\(= |\alpha|^2|0\rangle\langle 0| + \alpha\beta^*|0\rangle\langle 1| + \beta\alpha^*|1\rangle\langle 0| + |\beta|^2|1\rangle\langle 1|\)

其中 \((\cdot)^*\) 是共轭复数。也就是说，\(|\psi\rangle\) 被测得为 \(|0\rangle\) 的概率是 \(\langle 0|\rho|0\rangle = F(\rho, |0\rangle) = |\alpha|^2\)。同样，\(|\psi\rangle\) 被测得为 \(|1\rangle\) 的概率是 \(|\beta|^2\)。对于由密度算符表示的双量比特最大混合状态：

\(\rho = \frac{1}{4}(|00\rangle\langle 00| + |01\rangle\langle 01| + |10\rangle\langle 10| + |11\rangle\langle 11|)\)

并且 \(|\psi\rangle = |00\rangle\)，我们有：\(F(\rho, |\psi\rangle) = \langle 00|\rho|00\rangle = \frac{1}{4}\)。对于 N 量比特状态，我们有：\(F(\rho, |00\rangle) = \frac{1}{2^N}\)。

保真度衡量实际状态相对于参考状态的质量，可解释为实际状态被检测为参考状态的概率（或实际状态与参考状态之间的“重叠”）。

相对于 \(|\Phi^+\rangle\)，我们有：\(F(\rho, |\Phi^+\rangle) = \langle \Phi^+|\rho|\Phi^+\rangle\)。在没有噪声的情况下，假设 \(\rho = |\Phi^+\rangle\langle \Phi^+\|\)，则：\(F(\rho, |\Phi^+\rangle) = \langle \Phi^+|\Phi^+\rangle \langle \Phi^+|\Phi^+\rangle = 1\)。

考虑模拟某些噪声的翻转通道，位翻转的概率为 p，且最多只能发生一次位翻转，对于单量比特输入状态 \(|\psi\rangle\)，输出为 \(\rho = (1-p)|\psi\rangle\langle \psi| + pX|\psi\rangle\langle \psi|X\)。那么，

\(F(\rho, |\psi\rangle) = \langle \psi|((1-p)|\psi\rangle\langle \psi| + pX|\psi\rangle\langle \psi|X)|\psi\rangle\)
\(= (1-p)\langle \psi|\psi\rangle\langle \psi|\psi\rangle + p\langle \psi|X|\psi\rangle\langle \psi|X|\psi\rangle\)
\(= 1-p(1-\langle \psi|X|\psi\rangle^2) \le 1\)

这有可能降低保真度。

作为另一个例子，假设我们想要状态 \(|\Phi^+\rangle\)（或作为密度矩阵 \(|\Phi^+\rangle\langle \Phi^+|\)），但实际状态 \(\rho\) 可能是“不纯”的，即它有一定概率 p 处于未知噪声状态 \(|\text{unknown}\rangle\langle \text{unknown}|\)：

\(\rho = (1-p)|\Phi^+\rangle\langle \Phi^+| + p|\text{unknown}\rangle\langle \text{unknown}|\)

那么，

\(F(\rho, |\Phi^+\rangle) = \langle \Phi^+|((1-p)|\Phi^+\rangle\langle \Phi^+| + p|\text{unknown}\rangle\langle \text{unknown}|)|\Phi^+\rangle\)
\(= 1-p+p(\langle \text{unknown}|\Phi^+\rangle)^2 \le 1\)

请注意，可以使用第 3 章中看到的 CHSH 游戏来测试纠缠对的“纯度”。回顾我们使用了状态 \(|\Phi^-\rangle\) 并按以下方式应用操作：\((R(\theta_1) \otimes R(\theta_2))\frac{1}{\sqrt{2}}(|00\rangle - |11\rangle) = \frac{1}{\sqrt{2}}(cos(\theta_1 + \theta_2)(|00\rangle - |11\rangle) + sin(\theta_1 + \theta_2)(|01\rangle + |10\rangle))\)，或者等价地：

\((R(\theta_1) \otimes R(\theta_2)) | \Phi^- \rangle = cos(\theta_1 + \theta_2) | \Phi^- \rangle + sin(\theta_1 + \theta_2) | \Psi^+ \rangle\)

在存在先前建模的噪声时，我们将有：

\((R(\theta_1) \otimes R(\theta_2)) \left( \sqrt{1-p} | \Phi^- \rangle + \sqrt{p} | unknown' \rangle \right)\)
\(= \sqrt{1-p}[cos(\theta_1 + \theta_2) | \Phi^- \rangle + sin(\theta_1 + \theta_2) | \Psi^+ \rangle] + \sqrt{p} | noise \rangle\)

其中 \(|noise\rangle\) 表示对未知状态的操作。这意味着，使用与第 3 章中合适的 \(\theta_1\) 和 \(\theta_2\) 时，测量将以概率 \((1-p)cos^2(\pi/8) < 0.8536\) 得出 \(| \Phi^- \rangle\)，当 \(p\) 足够大时，且当 \(p\) 足够大时，该概率可能降至约 0.75 或以下，这已不再优于最佳经典情况（0.75）！这意味着，（获胜 CHSH 游戏的比率或概率）（即超过概率 0.75）可以作为一种“测试”，表明我们确实拥有（或正在实现）高保真纠缠。

## 6.2.2 随机化映射

我们还需要使用以下概念，称为 _随机化映射_。我们定义一个随机化映射 \(\tau : D(\mathbb{C}^2 \otimes \mathbb{C}^2) \rightarrow D(\mathbb{C}^2 \otimes \mathbb{C}^2)\)，其中 \(D(\mathbb{C}^2 \otimes \mathbb{C}^2)\) 指的是双量比特状态算符集合，它将任何双方密度算符 \(\rho_{AB}\) 映射到 _Bell 对角态_，形式如下：

\(p_1 | \Phi^+ \rangle \langle \Phi^+ | + p_2 | \Phi^- \rangle \langle \Phi^- | + p_3 | \Psi^+ \rangle \langle \Psi^+ | + p_4 | \Psi^- \rangle \langle \Psi^- |\)

其中 \(\sum_{i=1}^4 p_i = 1\)。它具有完全正迹保持（CPTP）映射的性质。$^8$

8 有关 CPTP 映射的更多信息，请参见 Artur Ekert 和 Tim Hosgood 的在线书籍：https://qubit.guide/9.9-completely-positive-trace-preserving-maps [最后访问：1/10/2023]。

随机化映射以均匀随机（等概率）的方式选取一个 Pauli 算符，并将其应用于 \(\rho_{AB}\) 中的每个量比特；我们将其写成如下形式：

\(\tau(\rho_{AB}) = \frac{1}{4} \sum_l (E_i \otimes E_l)\rho_{AB}(E_i \otimes E_l)^\dagger\)

其中 \(E_i \in \{I, X, Y, Z\}\)，即 \(E_i\) 是 Pauli 算符（例如 \(E_0 = I, E_1 = X, E_2 = Y, \text{且 } E_3 = Z\)）。

为了了解随机化映射的工作原理，我们将状态 \(| \psi \rangle\) 用 Bell 基表示：

\(| \psi \rangle = \alpha_1 | \Phi^+ \rangle + \alpha_2 | \Phi^- \rangle + \alpha_3 | \Psi^+ \rangle + \alpha_4 | \Psi^- \rangle\)

其中 \(\sum_i |\alpha_i|^2 = 1\)。设 \(\rho_{AB} = |\psi\rangle\langle\psi|\)，即

\(\rho_{AB} = (\alpha_1 |\Phi^+\rangle + \alpha_2 |\Phi^-\rangle + \alpha_3 |\Psi^+\rangle + \alpha_4 |\Psi^-\rangle) \times (\alpha_1^* \langle\Phi^+| + \alpha_2^* \langle\Phi^-| + \alpha_3^* \langle\Psi^+| + \alpha_4^* \langle\Psi^-|)\)

即

\(\rho_{AB}\rho_{AB} = \alpha_1\alpha_1^* |\Phi^+\rangle \langle\Phi^+| + \alpha_1\alpha_2^* |\Phi^+\rangle \langle\Phi^-| + \alpha_1\alpha_3^* |\Phi^+\rangle \langle\Psi^+| + \alpha_1\alpha_4^* |\Phi^+\rangle \langle\Psi^-| + \alpha_2\alpha_1^* |\Phi^-\rangle \langle\Phi^+| + \alpha_2\alpha_2^* |\Phi^-\rangle \langle\Phi^-| + \alpha_2\alpha_3^* |\Phi^-\rangle \langle\Psi^+| + \alpha_2\alpha_4^* |\Phi^-\rangle \langle\Psi^-| + \alpha_3\alpha_1^* |\Psi^+\rangle \langle\Phi^+| + \alpha_3\alpha_2^* |\Psi^+\rangle \langle\Phi^-| + \alpha_3\alpha_3^* |\Psi^+\rangle \langle\Psi^+| + \alpha_3\alpha_4^* |\Psi^+\rangle \langle\Psi^-| + \alpha_4\alpha_1^* |\Psi^-\rangle \langle\Phi^+| + \alpha_4\alpha_2^* |\Psi^-\rangle \langle\Phi^-| + \alpha_4\alpha_3^* |\Psi^-\rangle \langle\Psi^+| + \alpha_4\alpha_4^* |\Psi^-\rangle \langle\Psi^-|\)

我们注意到，由于 \(X|0\rangle = |1\rangle\)、\(X|1\rangle = |0\rangle\)、\(Z|0\rangle = |0\rangle\)、\(Z|1\rangle = -|1\rangle\)、\(Y|0\rangle = i|1\rangle\) 和 \(Y|1\rangle = -i|0\rangle\)，我们有：

| \((X \otimes X) |\Phi^+\rangle = |\Phi^+\rangle\) | \((Y \otimes Y) |\Phi^+\rangle = -|\Phi^+\rangle\) | \((Z \otimes Z) |\Phi^+\rangle = |\Phi^+\rangle\) |
| :--- | :--- | :--- |
| \((X \otimes X) |\Phi^-\rangle = -|\Phi^-\rangle\) | \((Y \otimes Y) |\Phi^-\rangle = |\Phi^-\rangle\) | \((Z \otimes Z) |\Phi^-\rangle = |\Phi^-\rangle\) |
| \((X \otimes X) |\Psi^+\rangle = |\Psi^+\rangle\) | \((Y \otimes Y) |\Psi^+\rangle = |\Psi^+\rangle\) | \((Z \otimes Z) |\Psi^+\rangle = -|\Psi^+\rangle\) |
| \((X \otimes X) |\Psi^-\rangle = -|\Psi^-\rangle\) | \((Y \otimes Y) |\Psi^-\rangle = -|\Psi^-\rangle\) | \((Z \otimes Z) |\Psi^-\rangle = -|\Psi^-\rangle\) |

由于 \(((X \otimes X) |\Phi^+\rangle)^\dagger = \langle\Phi^+|(X \otimes X)^\dagger = \langle\Phi^+|\)，因此 \((E_i \otimes E_i)^\dagger\) 算符有一组对应的等式。

然后我们有 \((I \otimes I)\rho_{AB}(I \otimes I) = \rho_{AB}\) 以及：

\((X \otimes X)\rho_{AB}(X \otimes X) = \alpha_1\alpha_1^* |\Phi^+\rangle \langle\Phi^+| - \alpha_1\alpha_2^* |\Phi^+\rangle \langle\Phi^-| + \alpha_1\alpha_3^* |\Phi^+\rangle \langle\Psi^+| - \alpha_1\alpha_4^* |\Phi^+\rangle \langle\Psi^-| - \alpha_2\alpha_1^* |\Phi^-\rangle \langle\Phi^+| + \alpha_2\alpha_2^* |\Phi^-\rangle \langle\Phi^-| - \alpha_2\alpha_3^* |\Phi^-\rangle \langle\Psi^+| + \alpha_2\alpha_4^* |\Phi^-\rangle \langle\Psi^-| + \alpha_3\alpha_1^* |\Psi^+\rangle \langle\Phi^+| - \alpha_3\alpha_2^* |\Psi^+\rangle \langle\Phi^-| + \alpha_3\alpha_3^* |\Psi^+\rangle \langle\Psi^+| - \alpha_3\alpha_4^* |\Psi^+\rangle \langle\Psi^-| - \alpha_4\alpha_1^* |\Psi^-\rangle \langle\Phi^+| + \alpha_4\alpha_2^* |\Psi^-\rangle \langle\Phi^-| - \alpha_4\alpha_3^* |\Psi^-\rangle \langle\Psi^+| + \alpha_4\alpha_4^* |\Psi^-\rangle \langle\Psi^-|\)

以及

\((Y \otimes Y)\rho_{AB}(Y \otimes Y) = \alpha_1\alpha_1^* |\Phi^+\rangle \langle\Phi^+| - \alpha_1\alpha_2^* |\Phi^+\rangle \langle\Phi^-| - \alpha_1\alpha_3^* |\Phi^+\rangle \langle\Psi^+| + \alpha_1\alpha_4^* |\Phi^+\rangle \langle\Psi^-| - \alpha_2\alpha_1^* |\Phi^-\rangle \langle\Phi^+| + \alpha_2\alpha_2^* |\Phi^-\rangle \langle\Phi^-| + \alpha_2\alpha_3^* |\Phi^-\rangle \langle\Psi^+| - \alpha_2\alpha_4^* |\Phi^-\rangle \langle\Psi^-| - \alpha_3\alpha_1^* |\Psi^+\rangle \langle\Phi^+| + \alpha_3\alpha_2^* |\Psi^+\rangle \langle\Phi^-| + \alpha_3\alpha_3^* |\Psi^+\rangle \langle\Psi^+| - \alpha_3\alpha_4^* |\Psi^+\rangle \langle\Psi^-| + \alpha_4\alpha_1^* |\Psi^-\rangle \langle\Phi^+| - \alpha_4\alpha_2^* |\Psi^-\rangle \langle\Phi^-| - \alpha_4\alpha_3^* |\Psi^-\rangle \langle\Psi^+| + \alpha_4\alpha_4^* |\Psi^-\rangle \langle\Psi^-|\)

