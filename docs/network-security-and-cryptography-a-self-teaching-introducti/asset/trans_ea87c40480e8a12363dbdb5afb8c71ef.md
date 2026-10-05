

# 经典加密算法 • 205

对于 $n=3$，$C$ 和 $P$ 是长度为 3 的列向量，代表明文和密文，$K$ 是一个 $3\times 3$ 矩阵，代表加密密钥。运算对模 26 进行。该系统可以用列向量和矩阵描述为：

```
$$\begin{bmatrix} c_1 \\ c_2 \\ c_3 \end{bmatrix} = \begin{bmatrix} k_{11} & k_{12} & k_{13} \\ k_{21} & k_{22} & k_{23} \\ k_{31} & k_{32} & k_{33} \end{bmatrix} \begin{bmatrix} p_1 \\ p_2 \\ p_3 \end{bmatrix} \pmod 26$$
```

这可以用以下方程表示：

```
$c_1 = (k_{11}p_1 + k_{12}p_2 + k_{13}p_3) \pmod 26$
$c_2 = (k_{21}p_1 + k_{22}p_2 + k_{23}p_3) \pmod 26$
$c_3 = (k_{31}p_1 + k_{32}p_2 + k_{33}p_3) \pmod 26$
```

密文字母通过 $n$ 个连续明文字母的线性组合生成。

**解密：** 矩阵 $K$ 的逆矩阵即 $K^{-1}$ 被用作解密密钥，解密过程定义为：

```
$P = K^{-1} \pmod 26 \quad (5.4)$
```

由于接收端解密密文需要 $K^{-1}$，因此矩阵 $K$ 必须是非奇异矩阵。

## 5.4

假设 $n=2$。假设要发送的明文是 $"CD"$

```
$P = \begin{bmatrix} "C" \\ "D" \end{bmatrix$，将此类结构放入矩阵中
```

```
且 $K = \begin{bmatrix} 2 & 3 \\ 3 & 4 \end{bmatrix}$
```

## 206 • 网络安全与密码学

**加密：** $C = KP \text{ mod } 26 = \begin{bmatrix} 2 & 3 \\ 3 & 4 \end{bmatrix} \times \text{mod } 26$

“CD” 在加密后传输为“NS”。

**解密：** 确定解密密钥 $K^{-1}$，

$K^{-1} = \begin{bmatrix} 4 & -3 \\ -3 & 2 \end{bmatrix} \begin{bmatrix} 4 & -3 \\ -3 & 2 \end{bmatrix} = \begin{bmatrix} -4 & 3 \\ -3 & 2 \end{bmatrix}$
$(2\times4)-(3\times3) = -1$

$P = K^{-1}C \text{ mod } 26 = \begin{bmatrix} -4 & 3 \\ -3 & 2 \end{bmatrix} \times \begin{bmatrix} 13 & "C" \\ 14 & \end{bmatrix} \text{mod } 26$
$= \begin{bmatrix} 2 \\ 3 \end{bmatrix} \begin{bmatrix} "C" \\ "D" \end{bmatrix}$

因此，在接收端解密后，恢复了原始明文“CD”。

## 示例 5.5

假设 $n = 2$。假设要发送的明文是“EB”

$P = \begin{bmatrix} "E" \\ "B" \end{bmatrix}$, $\begin{bmatrix} 7 & 5 \\ 4 & 3 \end{bmatrix}$ 将此类结构放入矩阵形式，且 $K =$

**加密：** $C = KP \text{ mod } 26 = \begin{bmatrix} 7 & 4 \\ 4 & 3 \end{bmatrix} \times \begin{bmatrix} 4 \\ 1 \end{bmatrix} \text{mod } 26$
$= \begin{bmatrix} 7 \\ 19 \end{bmatrix} \begin{bmatrix} "H" \\ "T" \end{bmatrix}$

“EB” 在加密后传输为“HT”。

## 经典加密算法 • 207

**解密：** 确定解密密钥 $K^{-1}$，

```
$K^{-1} = \begin{bmatrix} 3 & -4 \\ -5 & 7 \end{bmatrix} = \begin{bmatrix} 3 & -5 \\ -4 & 7 \end{bmatrix}$
$(7\times3)-(-5\times4) = 1$

$P = K^{-1}C \text{mod} 26 = \begin{bmatrix} (21-9)\text{mod} 26 \\ (-8+13)\text{mod} 26 \end{bmatrix} \times \begin{bmatrix} 4 \\ 1 \end{bmatrix}$
$= \begin{bmatrix} "E" \\ "B" \end{bmatrix}$ 

因此，在接收端解密后，恢复了原始明文“EB”。

### 5.2.3 希尔密码强度

每个密文字母通过 $n$ 个连续字母的线性组合生成。另一种说法是每个明文字母影响许多密文。因此，明文的统计结构不会反映在密文中；而是扩散到密文中。这种现象被称为“扩散”。密钥矩阵越大，扩散越明显。对于足够大的密钥尺寸，该方案将很难破解。

### 5.2.4 牌阵密码 (Play-Fair Cipher)

牌阵密码使用 $5\times5$ 的字母矩阵进行加密/解密，如表54所示。

- 如果一对字母位于同一列，则替换为它们正下方的字母（循环方式）。列顶字母视为该列的最后一个字母。
- 对中的每个字母替换为行与列交处的字母。

**解密：** 解密算法是加密算法的逆过程。密文字母分成对进行解密。根据以下规则执行解密：

- 如果一对字母位于同一行，则替换为其左侧的字母。为此，行尾字母视为该行第一个字母的左侧。
- 如果一对字母位于同一列，则替换为其上方的字母。为此，列底字母视为该列第一个字母的上方。
- 对中的每个字母替换为行与列交处的字母。

**示例 5.6**

明文：COMING AT SIX
密文：

### 5.2.5 多表替换密码（维吉尼亚密码，Vigenere Cipher）

维吉尼亚密码或多表替换密码是一种对英文字母（A...Z）编码的明文进行加密的替换密码。

- 密钥也是由字母（A...Z）组成的字符串。
- 密钥的长度与加密明文的长度完全相同。
- 密钥通过重复发送方和接收方之间的单词生成；例如，如果明文长度为20，密钥为“COMPUTER”，则密钥将是：“COMPUTERCOMP”，长度为20。

**加密：**

假设 $p[0...n-1]$ 为明文字符串，$k[0...n-1]$ 为长度为 $n$ 的密钥字符串。

- 字母被赋予整数值“A”=0，“B”=1，“C”=2..."Z”=25。

$c[i]=p[i]+k[i] \pmod{26}, \quad 0<i<n$

其中
$p[i]:$ 明文中的第 $i$ 个字母
$k[i]:$ 密钥中的第 $i$ 个字母
$c[i]:$ 密文中的第 $i$ 个字母

**解密：** 解密过程是加密过程的逆过程。

$p[i]=(c[i]-k[i]) \pmod{26}, \quad 0<i<n$

**方案实现：**

该方案通过生成一个 $26\times26$ 的查找表来实现，如表55所示，明文字母沿 $x$ 轴，密钥字母沿 $y$ 轴。对于给定的明文字母和密钥字母，密文字母将是明文字母列与密钥字母行的交叉点。

**示例 5.7**

| 明文: COMEATSEVEN | 密钥: COMPUTER | 密文: ECYHZEKush |

提示：密文使用了小写字母以区分于明文。

## 经典算法 · 21

| A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y |
| B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A |
| C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B |
| D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C |
| E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E |
| F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F |
| G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G |
| H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H |
| I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I |
| J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J |
| K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K |
| L | M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L |
| M | N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M |
| N | O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N |
| O | P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O |
| P | Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P |
| Q | R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q |
| R | S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R |
| S | T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S |
| T | U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T |
| U | V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U |
| V | W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V |
| W | X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W |
| X | Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X |
| Y | A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | R | S | T | U | V | W | X | Y |

