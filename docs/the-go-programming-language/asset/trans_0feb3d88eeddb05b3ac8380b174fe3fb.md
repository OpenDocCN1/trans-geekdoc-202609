

```
func IsUp(v Flags) bool     { return v&FlagUp == FlagUp }
func TurnDown(v *Flags)     { *v &^= FlagUp }
func SetBroadcast(v *Flags) { *v |= FlagBroadcast }
func IsCast(v Flags) bool   { return v&(FlagBroadcast|FlagMulticast) != 0 }

func main() {
    var v Flags = FlagMulticast | FlagUp
    fmt.Printf("%b %t\n", v, IsUp(v)) // "10001 true"
    TurnDown(&v)
    fmt.Printf("%b %t\n", v, IsUp(v)) // "10000 false"
    SetBroadcast(&v)
    fmt.Printf("%b %t\n", v, IsUp(v))   // "10010 false"
    fmt.Printf("%b %t\n", v, IsCast(v)) // "10010 true"
}
```

作为 `iota` 更复杂的示例，此声明为 1024 的幂命名：

[点击此处查看代码图像](#ch03_images.html#id078pro01_r)

```
const (
    _ = 1 << (10 * iota)
    KiB // 1024
    MiB // 1048576
    GiB // 1073741824
    TiB // 1099511627776              (超过 1 << 32)
    PiB // 1125899906842624
    EiB // 1152921504606846976
    ZiB // 1180591620717411303424     (超过 1 << 64)
    YiB // 1208925819614629174706176
)
```

`iota` 机制有其局限性。例如，无法生成更常见的 1000 的幂（KB、MB 等），因为没有指数运算符。

**练习 3.13：** 尽可能紧凑地为 KB、MB 直到 YB 编写 `const` 声明。

### 3.6.2 无类型常量

Go 中的常量有点特别。虽然常量可以拥有任何基本数据类型，如 `int` 或 `float64`，包括命名的基本类型如 `time.Duration`，但许多常量并不绑定特定类型。编译器用比基本类型值高得多的数值精度来表示这些未绑定常量，并且它们的运算比机器运算更精确；你可以假设至少有 256 位的精度。这些未绑定常量共有六种类型，称为*无类型*布尔型、无类型整型、无类型符文、无类型浮点型、无类型复数型和无类型字符串。

通过推迟这种绑定，无类型常量不仅能保持其更高的精度直到后期，而且无需转换即可参与比已绑定常量多得多的表达式。例如，上面示例中的 `ZiB` 和 `YiB` 值太大，无法存储在任何整型变量中，但它们是合法的常量，可用于如下表达式：

```
fmt.Println(YiB/ZiB) // "1024"
```

作为另一个示例，浮点常量 `math.Pi` 可用于任何需要浮点或复数值的地方：

```
var x float32 = math.Pi
var y float64 = math.Pi
var z complex128 = math.Pi
```

如果 `math.Pi` 已绑定到特定类型（如 `float64`），结果精度会降低，且在需要 `float32` 或 `complex128` 值时，将需要类型转换才能使用它：

[点击此处查看代码图像](#ch03_images.html#id079pro01_r)

```
const Pi64 float64 = math.Pi

var x float32 = float32(Pi64)
var y float64 = Pi64
var z complex128 = complex128(Pi64)
```

对于字面值，语法决定其类型。字面值 `0`、`0.0`、`0i` 和 `'\u0000'` 都表示具有相同值但不同类型的常量：无类型整型、无类型浮点型、无类型复数型和无类型符文。类似地，`true` 和 `false` 是无类型布尔值，字符串字面值是无类型字符串。

回想一下，`/` 可能代表整数除法或浮点除法，具体取决于其操作数。因此，字面值的选择可能会影响常量除法表达式的结果：

[点击此处查看代码图像](#ch03_images.html#id079pro02_r)

```
var f float64 = 212
fmt.Println((f - 32) * 5 / 9)     // "100"; (f - 32) * 5 是 float64
fmt.Println(5 / 9 * (f - 32))     // "0";   5/9 是无类型整数，结果为 0
fmt.Println(5.0 / 9.0 * (f - 32)) // "100"; 5.0/9.0 是无类型浮点数
```

只有常量可以是无类型的。当无类型常量被赋值给变量时（如下面的第一条语句），或出现在带有显式类型的变量声明的右侧时（如其他三条语句），如果可能，该常量会隐式转换为该变量的类型。

[点击此处查看代码图像](#ch03_images.html#id079pro03_r)

```
var f float64 = 3 + 0i // 无类型复数 -> float64
f = 2                  // 无类型整数 -> float64
f = 1e123              // 无类型浮点数 -> float64
f = 'a'                // 无类型符文 -> float64
```

上述语句因此等价于：

```
var f float64 = float64(3 + 0i)
f = float64(2)
f = float64(1e123)
f = float64('a')
```

无论是隐式还是显式，将常量从一种类型转换为另一种类型，都要求目标类型能表示原始值。允许对实数和复数浮点数进行舍入：

[点击此处查看代码图像](#ch03_images.html#id080pro01_r)

```
const (
    deadbeef = 0xdeadbeef // 无类型 int，值为 3735928559
    a = uint32(deadbeef)  // uint32，值为 3735928559
    b = float32(deadbeef) // float32，值为 3735928576（向上舍入）
    c = float64(deadbeef) // float64，值为 3735928559（精确）
    d = int32(deadbeef)   // 编译错误：常量溢出 int32
    e = float64(1e309)    // 编译错误：常量溢出 float64
    f = uint(-1)          // 编译错误：常量下溢 uint
)
```

在不带显式类型的变量声明中（包括短变量声明），无类型常量的类型隐式决定了变量的默认类型，如下例所示：

[点击此处查看代码图像](#ch03_images.html#id080pro02_r)

```
i := 0      // 无类型整数；        隐式 int(0)
r := '\000' // 无类型符文；           隐式 rune('\000')
f := 0.0    // 无类型浮点数；隐式 float64(0.0)
c := 0i     // 无类型复数；        隐式 complex128(0i)
```

注意这种不对称性：无类型整数转换为 `int`，其大小不固定；但无类型浮点数和复数转换为显式大小的类型 `float64` 和 `complex128`。语言没有类似于无大小 `int` 的无大小 `float` 和 `complex` 类型，因为在不知道浮点数据类型大小的情况下，很难编写正确的数值算法。

要赋予变量不同的类型，我们必须显式地将无类型常量转换为所需类型，或在变量声明中指明所需类型，如下例所示：

```
var i = int8(0)
var i int8 = 0
```

这些默认规则在将无类型常量转换为接口值时（见[第 7 章](#ebook_split_059.html#id-interfaces)）尤为重要，因为它们决定了其动态类型。

[点击此处查看代码图像](#ch03_images.html#id080pro03_r)

```
fmt.Printf("%T\n", 0)      // "int"
fmt.Printf("%T\n", 0.0)    // "float64"
fmt.Printf("%T\n", 0i)     // "complex128"
fmt.Printf("%T\n", '\000') // "int32" (rune)
```

我们现在已经介绍了 Go 的基本数据类型。下一步是展示如何将它们组合成更大的组合，如数组和结构体，进而构成解决实际编程问题的数据结构；这是[第 4 章](#ebook_split_034.html#id-compositetypes)的主题。

# 4. 组合类型

在[第 3 章](#ebook_split_027.html#id-basicdatatypes)中，我们讨论了作为 Go 程序数据结构构建块的基本类型；它们是我们世界的原子。在本章中，我们将了解*组合*类型，即通过以各种方式组合基本类型而创建的分子。我们将讨论四种这样的类型——数组、切片、映射和结构体——并在本章末尾，展示如何使用这些类型的结构化数据编码为 JSON 数据并从中解析，以及如何用于从模板生成 HTML。

