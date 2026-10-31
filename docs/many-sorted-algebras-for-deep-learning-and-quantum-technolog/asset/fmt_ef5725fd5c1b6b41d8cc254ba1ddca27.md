
As previously mentioned, operations involving multiple qubits are very often inputted with these qubits tensored together. For the case involving two qubits, the operation `X`: `H` ⊗![Equation](Images/F000060si36.png) `H`→`H` ⊗![Equation](Images/F000060si37.png) `H`. As an instance of this is the operator `X`=`CNOT`. Most often, for a multiple-qubit gate, the first qubit is used as a control qubit. This means that the actual operation is employed to the other, the second qubit. Here, the second qubit is conditioned on the state of the first qubit, and the second qubit is called the target. An example of this type of operation is detailed next.

Consider the `CNOT` gate, also known as the conditional not operation. The input to this operation is `|x>` ⊗![Equation](Images/F000060si38.png) `|y>`, where ⊗![Equation](Images/F000060si39.png) denotes the tensor operation. The tensored product is written more briefly as `|x y>`, where `x` is the first or top qubit and the second is `y`. Both `x` and `y` can take on only the values of zero or one. This gate is illustrated in [Fig. 16.2](#Ch016_291-305_B9780443136979000060.xhtml#f0015).

![Figure 16.2 CNOT gate.](Images/F000060f16-02-9780443136979.jpg)

[Figure 16.2](#Ch016_291-305_B9780443136979000060.xhtml#Bf0020) `CNOT` gate.

As can be seen from this diagram, the first qubit `|x>` passes through not altered. The bottom output is the qubit `|y (+) x>`, where `(+)` denotes the `mod2` operation or exclusive or. Thus `|y (+) x>`=0 when and only when `x`=`y`; otherwise it equals 1. The `CNOT` operation is given in `C⁴`![Equation](Images/F000060si40.png) by the matrix:

$\\begin{matrix} {|1} & 0 & 0 & {0|} \\\\ {|0} & 1 & 0 & {0|} \\\\ {|0} & 0 & 0 & {1|} \\\\ {|0} & 0 & 1 & {{0|}.} \\\\ \\end{matrix}$

![Equation](Images/F000060si41.png)

The aforementioned `CNOT` matrix is symmetric and an involution; this shows that the `CNOT` operation is unitary. This matrix multiplies `|x y>` when expressed as a column vector in `C⁴`![Equation](Images/F000060si42.png) after the tensor product is utilized. There are four possibilities for this input; they are as follows: `|0 0>`=`|0>` ⊗![Equation](Images/F000060si43.png) `|0>`=`(1 0)`′ ⊗![Equation](Images/F000060si44.png) `(1 0)`′, `|0 1>`=`(1 0)`′ ⊗![Equation](Images/F000060si45.png) `(0 1)`′, `|10>`=`(0 1)`′ ⊗![Equation](Images/F000060si46.png) `(1 0)`′, and finally, `|11>`=`(0 1)`′ ⊗![Equation](Images/F000060si47.png) `(0 1)`′. The 4x1 vector representations are given as column vectors in the corresponding order:

$\\begin{matrix} {|1|} & {|0|} & {|0|} & {|0|} \\\\ {|0|} & {|1|} & {|0|} & {|0|} \\\\ {|0|} & {|0|} & {|1|} & {|0|} \\\\ {|0|} & {|0|} & {|0|} & {{|1|}.} \\\\ \\end{matrix}$

![Equation](Images/F000060si48.png)

The matrix `CNOT` when operating on these vectors in the exact same order is as follows:

$\\begin{matrix} {|1|} & {|0|} & {|0|} & {|0|} \\\\ {|0|} & {|1|} & {|0|} & {|0|} \\\\ {|0|} & {|0|} & {|0|} & {|1|} \\\\ {|0|} & {|0|} & {|1|} & {|0|} \\\\ \\end{matrix}$

![Equation](Images/F000060si49.png)

Now these resulting vectors must be interpreted in terms of tensored kets.

Representing the 4x1 vectors above, in order and in terms of kets, gives `|0 0>`, `|0 1>`, `|1 1>`, and finally, `|1 0>`. Accordingly, when the first qubit is zero, the output is `|x y>` and is unchanged. When the first qubit is one, then the second qubit flips sign, that is, the output becomes `|x (1−y)>`. The determinant of `CNOT` is minus one, so it is in the Lie group `U(4, C)`, but it isn’t in the Lie group `SU(4, C)`.

Notice that the `CNOT` operator is an entangler, but also it is an unentangler. For instance, `CNOT`(1/2^(1/2) (`|0 0>`+`|1 0>`))=1/2^(1/2) (`|0 0>`+`|1 1>`); the last qubit pair is entangled. It is one of the Bell states. To see this, first note that `|+0>`=1/2^(1/2) (`|0>`+`|1>`) ⊗![Equation](Images/F000060si50.png) `|0>` so the input to the `CNOT` is not entangled. Finally, to see that the output is entangled, note that the most general `|0>` and `|1>` qubit tensor product is `z`=`a11`|0>` ⊗![Equation](Images/F000060si51.png) `|0>`+`a12`|0>` ⊗![Equation](Images/F000060si52.png) `|1>`+`a21`|1>` ⊗![Equation](Images/F000060si53.png) `|0>`+`a22`|1>` ⊗![Equation](Images/F000060si54.png) `|1>`. The tensor is called a pure tensor iff `a11 a22`=`a12 a21`; otherwise it is entangled. Here `a21`=0, but `a11`=`a22`=1. See [Section 7.4](#Ch007_131-144_B9780443136979000205.xhtml#s0025) for further information on entanglement.

Finally, using the `Pauli` matrices `X`, `Y`, and `Z` are as follows:

$\\begin{matrix} {|0} & {i|} & {|0} & {{- 1}|} & {|i} & {0|} \\\\ {|i} & {0|} & {|1} & {0|} & {|0} & {{- i}|} \\\\ \\end{matrix}$

![Equation](Images/F000060si55.png)

`CNOT` = `|0>`  `<` `0`| ⊗ `I` + `|1>`  `<` `1`| ⊗ `X` = (`I`+`Z`) ⊗ `I` + (`I`−`Z`) ⊗ `X`/2

![Equation](Images/F000060si56.png)

In higher dimensional Hilbert spaces, unitary operators can be replaced by the `CNOT` gate in `U(4,C)` along with single-qubit gates in `U(2,C)` ([Nielsen and Chuang, 2000](#Ch016_291-305_B9780443136979000060.xhtml#bib6))

The `Pauli` group on `n` qubits consists of `{1, −1, i, −i} x {I, X, Y, Z}^(@*n*)`, where the last set involves the `Pauli` matrices tensored together `n` times. In a similar manner as in the single-qubit case, the Clifford `n` qubit group consists of all the unitary matrices `U` such that for `P` and `P′` in the `n` qubit `Pauli` group, `U P U*`=`P′`.

### Example 16.13

For the two qubit case, notice that when using operations in order by multiplying the following three matrices, `CNOT`, (`Z` ⊗![Equation](Images/F000060si57.png) `I`), `CNOT*`, the result is the `Z` ⊗![Equation](Images/F000060si58.png) `I`. That is, `CNOT`.(`Z` ⊗![Equation](Images/F000060si59.png) `I`). `CNOT*`=`Z` ⊗![Equation](Images/F000060si60.png) `I`. Likewise, `CNOT`.(`I` ⊗![Equation](Images/F000060si61.png) `Z`). `CNOT*`=`Z` ⊗![Equation](Images/F000060si62.png) `Z`, `CNOT`.(`I` ⊗![Equation](Images/F000060si63.png) `X`). `CNOT*`=`I` ⊗![Equation](Images/F000060si64.png) `X`, and `CNOT`.(`X` ⊗![Equation](Images/F000060si65.png) `I`). `CNOT*`=`X` ⊗![Equation](Images/F000060si66.png) `X`. For the last identity, note that `X` ⊗![Equation](Images/F000060si67.png) `I`, `CNOT`.(`X` ⊗![Equation](Images/F000060si68.png) `I`), and `X` ⊗![Equation](Images/F000060si69.png) `X` are given in order as follows:

$\\begin{matrix} {|0} & 0 & 1 & {0|} & {|0} & 0 & 1 & {0|} & {|0} & 0 & 0 & {1|} \\\\ {|0} & 0 & 0 & {1|} & {|0} & 0 & 0 & {1|} & {|0} & 0 & 1 & {0|} \\\\ {|1} & 0 & 0 & {0|} & {|0} & 1 & 0 & {0|} & {|0} & 1 & 0 & {0|} \\\\ {|0} & 1 & 0 & {0|} & {|1} & 0 & 0 & {0|} & {|1} & 0 & 0 & {{0|}.} \\\\ \\end{matrix}$

![Equation](Images/F000060si70.png)

## 16.5 The swapping operation

The `CNOT` gate is additionally useful in creating other important gates. In particular, the swap gate is designed by utilizing three `CNOT` gates in succession. See [Fig. 16.3](#Ch016_291-305_B9780443136979000060.xhtml#f0020). The symbol for the swap gate is `SWAP`. When used `SWAP`: `H`[`A`]⊗`H`[`B`]→`H`[`B`]⊗`H`[`A`]![Equation](Images/F000060si71.png). For input state `|x y>`, the swap gate yields `SWAP`(`|x y>`) = `|y x>`. It begins with the first bit as a control bit in the first `CNOT`. Then the second bit is used as a control bit in the second `CNOT`, and finally for the last `CNOT`, the first bit is used again as the control bit. The following sequence illustrates the swapping operation, with a single arrow indicating the use of a `CNOT` operation: `|x y>`→![Equation](Images/F000060si72.png) `|x, x (+) y>`→![Equation](Images/F000060si73.png) `|x (+) x (+) y, x (+) y>`=`|y, x (+) y>`→![Equation](Images/F000060si74.png) `|y, x (+) y (+) y>`=`|y x>`.

![Figure 16.3 The SWAP Gate.](Images/F000060f16-03-9780443136979.jpg)

[Figure 16.3](#Ch016_291-305_B9780443136979000060.xhtml#Bf0020) The `SWAP` Gate.

## 16.6 Universal quantum gate set
