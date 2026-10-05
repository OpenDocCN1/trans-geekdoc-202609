
# 64

# 第 2 章 布尔值与数值

从我们执行 $\pi \times$ 计算的行，并将结果存储在 pi 中（63 $\triangleleft$， $\circ$），到我们计算 $pi \times 10^{10}$ 并返回结果的行（63 $\triangleleft$， $\circ$）——而不关心 pi 的值已被结果所覆盖。

在尽可能使用整数（ints）的地方，如果范围不足，则退回到 `int float32` 或 `float64`，此时就不需要考虑近似问题。然而，如果需要完全精确的计算，并且我们准备好付出内存和处理开销的代价，那么我们可以使用 `big Int` 或 `big Rat`——后者特别适用于财务计算——并像我们在这里需要浮点数计算的那样，根据需要进行缩放。

## 2.3.2. 浮点类型

Go 提供了浮点数类型和两种复数类型——它们的名称和范围见表 2.7。Go 中的浮点数存储在广泛使用的 IEEE-754 格式（http://en.wikipedia.org/wiki/IEEE_754-2008）中。该格式也是许多处理器和浮点单元使用的原生格式，在大多数情况下，Go 能够直接利用硬件的浮点支持。

表 2.7 Go 的浮点数类型

| 类型 | 范围 |
| --- | --- |
| float32 | $\pm3.4028236638259859811704183484516925440 \times 10^{38}$ 尾数可靠地精确到 7 位小数。 |
| float64 | $\pm1.797693134863213708152427317017456781 \times 10^{308}$ 尾数可靠地精确到 15 位小数。 |
| complex64 | 实部和虚部均为 `float32` 类型。 |
| complex128 | 实部和虚部均为 `float64` 类型。 |

Go 浮点数支持表 2.4 中列出的所有算运算（59 $\triangleright$）。该包大部分常量和所有函数列在表 2.8 到 2.10 中 $\triangleright$-$65\triangleright$。

浮点数使用小数点书写，或使用指数计数法，例如 0.0, 3, 8.2, -7.4, -64, 1.5E-3。计算机内部使用二进制表示浮点数——这意味着小数可以被精确表示（如 0.5），而其他只能近似表示（0.1 和 0.2）。此外，表示法使用了固定比特位数，因此能够存储的位数是有限的。这不是 Go 特有的问题，而是影响所有主流编程语言中浮点数的问题。然而，不精确并不总是显而易见的，因为 Go 使用了一种智能算法来输出浮点数，在保持精度的前提下使用尽可能少的数字。

## 2.3. 数值类型

| 语法 | 描述/结果 |
| --- | --- |
| math.Abs(x) | |x|, 即 x 的绝对值 |
| math.Acos(x) | 以弧度为单位的 x 反余弦 |
| math.Acosh(x) | 以弧度为单位的 x 反双曲余弦 |
| math.Asin(x) | 以弧度为单位的 x 反正弦 |
| math.Asinh(x) | 以弧度为单位的 x 反双曲正弦 |
| math.Atan(x) | 以弧度为单位的 x 反正切 |
| math.Atan2(y, x) | 以弧度为单位的 y/x 反正切 |
| math.Atanh(x) | 以弧度为单位的 x 反双曲正切 |
| math.Cbrt(x) | x 的立方根 |
| math.Ceil(x) | ⌈x�], 即大于或等于 x 的最小整数；例如 math.Ceil(5.4) = 6.0 |
| math.Copysign(x, y) | 具有 x 的幅值和 y 的符号的值 |
| math.Cos(x) | 以弧度为单位的 x 余弦 |
| math.Cosh(x) | 以弧度为单位的 x 双曲余弦 |
| math.Dim(x, y) | 实际上是 math.Max(x-y, 0.0) |
| math.E | 常数 e；约 2.7182818284945 |
| math.Erf(x) | erf(x); x 的高斯误差函数 |
| math.Erfc(x) | erfc(x); x 的互补高斯误差函数 |
| math.Exp(x) | e^x |
| math.Exp2(x) | 2^x |
| math.Exppm1(x) | e^x - 1；当 x 接近 0 时，这比使用 math.Exp(x)-1 更准确 |
| math.Float32bits(f) | f（float32 类型）的 IEEE-754 二进制表示的 uint32 |
| math.Float32frombits(u) | 由 u（uint32 类型）中的 IEEE-754 位表示的 float32 |
| math.Float64bits(x) | x（float64 类型）的 IEEE-754 二进制表示的 uint64 |
| math.Float64frombits(u) | 由 u（uint64 类型）中的 IEEE-754 位表示的 float64 |

# 表 2.9 Math 包的常量和函数 #2

| 语法 | 描述/结果 |
|---|---|
| math.Floor(x) | ⌊x⌋，即小于或等于 x 的最大整数；例如 math.Floor(5.4) == 5.0 |
| math.Frexp(x) | float64 类型的 frac 和 int 类型的 exp，使得 x = frac * 2^exp；其反函数是 math.Ldexp() |
| math.Gamma(x) | Γ(x), (x - 1)! |
| math.Hypot(x, y) | math.Sqrt(x * x, y * y) |
| math.log1(x) | 作为 int 的 x二进制指数；参见 math.Logb() |
| math.Inf(n) | 如果 int 类型的 n ≥ 0，则为 +∞ 的 float64 值；否则为 -∞ |
| math.IsInf(x, n) | 如果 float64 类型的 x 和 int 类型的 n > 0，或 x 为无穷且 n < 0，或 x 为任大且 n 为 0，则为 true |
| math.isNaN(x) | 如果 x 是 IEEE-754 “不是数字”值则为 true |
| math.J0(x) | J₀(x)，第一类贝塞尔函数 |
| math.J1(x) | J₁(x)，第一类贝塞尔函数 |
| math.Jn(n, x) | Jₙ(x)，n 阶（其中 n 为 int 类型）第一类贝塞尔函数 |
| math.Ldexp(x, n) | x * 2^n，其中 x 是 float64，n 是 int；其反函数是 math.Frexp() |
| math.Gamma(x) | 作为 float64 的 Γ(x) 以及作为 int 的 Γ(x) |
| math.Ln2(x) | ln₂(x)，约 0.693147180559 |
| math.Ln10(x) | ln₀(x)，约 2.30258509294 |
| math.Log(x) | log(x) |
| math.Log2(x) | log₂(x)，约 1.44269520633 |
| math.Log10(x) | log₀(x)，约 0.434294481903 |
| math.Logp(x) | log(1+x)；当 x 接近 0 时比使用 math.Log(1+x) 更准确 |
| math.Exppm1(x) | e^x - 1；当 x 接近 0 时比使用 math.Exp(x)-1 更准确 |
| math.Pow(x, y) | x^y |
| math.Sqrt(x) | x 的平方根 |
| math.Trunc(x) | 舍弃 x 的小数部分 |

## 2.3. 数值类型

# 表 2.10 Math 包的常量和函数 #3

| 语法 | 描述/结果 |
|---|---|
| math.E | 常数 e；约 2.71828182845904 |
| math.Pi | 常数 pi；约 3.14159265358979 |
| math.Phi | 常数 phi；约 1.61803398874989 |
| math.SmallestNonzeroFloat64 | 最小正 float64 |
| math.SmallestFloat64 | 最小正化 float64 |
| math.MaxFloat64 | 最大的 float64 |
| math.SmallestNonzeroFloat32 | 最小正 float32 |
| math.SmallestFloat32 | 最小正化 float32 |
| math.MaxFloat32 | 最大的 float32 |
| math.NaN() | “不是数字”值 |
| math.Inf() | 正无穷大 |
| math.Inf(-1) | 负无穷大 |

(注：提供的 OCR 文本包含了表 2.9 和 2.10 之间的显著重叠。我已根据 `math` 包的标准重构了内容。)
