

## 3.3 复数

如果浮点字面量或十进制整数字面量后面紧跟着 `i`，例如 `3.141592i` 或 `2i`，它就变成了一个 `虚数字面量`，表示一个实部为零的复数：

[点击此处查看代码图像](#part0132_split_021.html#id061pro02_r)

```
fmt.Println(1i * 1i) // "(-1+0i)", i² = -1
```

根据常量运算规则，复数常量可以与其他数值常量（整数或浮点数，实数或虚数）相加，这让我们可以自然地书写复数，如 `1+2i` 或等价的 `2i+1`。上面 `x` 和 `y` 的声明可以简化为：

```
x := 1 + 2i
y := 3 + 4i
```

复数可以使用 `==` 和 `!=` 进行相等比较。如果两个复数的实部相等且虚部相等，则它们相等。

`math/cmplx` 包提供了用于复数操作的库函数，例如复数平方根和指数函数。

[点击此处查看代码图像](#part0132_split_022.html#id061pro03_r)

```
fmt.Println(cmplx.Sqrt(-1)) // "(0+1i)"
```

下面的程序使用 `complex128` 算术来生成曼德勃罗集合。

[点击此处查看代码图像](#part0132_split_023.html#id061pro04_r)

`gopl.io/ch3/mandelbrot`

```
// Mandelbrot emits a PNG image of the Mandelbrot fractal.
package main

import (
    "image"
    "image/color"
    "image/png"
    "math/cmplx"
    "os"
)

func main() {
    const (
        xmin, ymin, xmax, ymax = -2, -2, +2, +2
        width, height          = 1024, 1024
    )

    img := image.NewRGBA(image.Rect(0, 0, width, height))
    for py := 0; py < height; py++ {
        y := float64(py)/height*(ymax-ymin) + ymin
        for px := 0; px < width; px++ {
            x := float64(px)/width*(xmax-xmin) + xmin
            z := complex(x, y)
            // Image point (px, py) represents complex value z.
            img.Set(px, py, mandelbrot(z))
        }
    }
    png.Encode(os.Stdout, img) // NOTE: ignoring errors
}

func mandelbrot(z complex128) color.Color {
    const iterations = 200
    const contrast = 15

    var v complex128
    for n := uint8(0); n < iterations; n++ {
        v = v*v + z
        if cmplx.Abs(v) > 2 {
            return color.Gray{255 - contrast*n}
        }
    }
    return color.Black
}
```

两个嵌套循环遍历一个 1024×1024 灰度光栅图像中的每个点，该图像代表复平面上 -2 到 +2 的区域。程序测试该点代表的数反复平方并加上自身后，最终是否会“逃逸”出半径为 2 的圆。如果会逃逸，则根据逃逸所需的迭代次数对该点进行着色。如果不会逃逸，该值属于曼德勃罗集合，该点保持黑色。最后，程序将标志性分形的 PNG 编码图像写入标准输出，如 [图 3.3](#part0031.html#id-figures-mandelbrot) 所示。

**练习 3.5：** 使用 `image.NewRGBA` 函数和 `color.RGBA` 或 `color.YCbCr` 类型实现一个全彩色的曼德勃罗集合。

**练习 3.6：** 超采样是一种通过计算每个像素内多个点的颜色值并取平均来减少像素化效应的技术。最简单的方法是将每个像素分成四个“子像素”。请实现它。

**练习 3.7：** 另一个简单的分形使用牛顿法寻找函数（如 *z*⁴−1 = 0）的复数解。根据逼近四个根之一所需的迭代次数为每个起始点着色。根据点逼近的根为其着色。

![曼德勃罗集合。](images/00010.jpeg)

**图 3.3。** 曼德勃罗集合。

**练习 3.8：** 在高缩放级别渲染分形需要极高的算术精度。使用四种不同的数字表示实现相同的分形：`complex64`、`complex128`、`big.Float` 和 `big.Rat`。（后两种类型位于 `math/big` 包中。`Float` 使用任意但有界精度的浮点数；`Rat` 使用无界精度的有理数。）它们在性能和内存使用方面如何比较？在什么缩放级别下渲染伪影会变得可见？

**练习 3.9：** 编写一个 Web 服务器来渲染分形并将图像数据写入客户端。允许客户端将 *x*、*y* 和缩放值作为 HTTP 请求的参数指定。

## 3.4 布尔值

`bool` 类型的值，或称*布尔值*，只有两个可能的值：`true` 和 `false`。

`if` 和 `for` 语句中的条件是布尔值，比较运算符如 `==` 和 `<` 会产生布尔结果。

一元运算符 `!` 是逻辑非，所以 `!true` 是 `false`，或者可以说 `(!true==false)==true`，尽管出于风格考虑，我们总是将冗余的布尔表达式如 `x==true` 简化为 `x`。

布尔值可以与 `&&`（逻辑与）和 `||`（逻辑或）运算符结合使用，它们具有*短路*行为：如果答案已经由左操作数的值决定，则不会对右操作数求值，这使得编写如下表达式成为安全的：

```
s != "" && s[0] == 'x'
```

如果对空字符串应用 `s[0]` 会导致 panic。

由于 `&&` 的优先级高于 `||`（记忆法：`&&` 是布尔乘法，`||` 是布尔加法），这种形式的条件不需要括号：

[点击此处查看代码图像](#part0132_split_024.html#id064pro01_r)

```
if 'a' <= c && c <= 'z' ||
    'A' <= c && c <= 'Z' ||
    '0' <= c && c <= '9' {
    // ...ASCII letter or digit...
}
```

没有从布尔值到数值（如 0 或 1）的隐式转换，反之亦然。

必须使用显式的 `if`，如下所示：

```
i := 0
if b {
    i = 1
}
```

如果经常需要此操作，编写一个转换函数可能是值得的：

[点击此处查看代码图像](#part0132_split_025.html#id064pro02_r)

// btoi returns 1 if b is true and 0 if false.
func btoi(b bool) int {
    if b {
        return 1
    }
    return 0
}

逆操作太简单了，不值得写成函数，但为了对称，这里给出：

[点击此处查看代码图像](#part0132_split_026.html#id064pro03_r)

// itob reports whether i is non-zero.
func itob(i int) bool { return i != 0 }

## 3.5 字符串

字符串是一个不可变的字节序列。

字符串可以包含任意数据，包括值为 0 的字节，但通常它们包含人类可读的文本。

文本字符串通常被解释为 UTF-8 编码的 Unicode 码点（rune）序列，我们很快将详细探讨这一点。

内置函数 `len` 返回字符串中的字节数（而非 rune 数），索引操作 `s[i]` 获取字符串 `s` 的第 *i* 个字节，其中 0 ≤ `i` < `len(s)`。

[点击此处查看代码图像](#part0132_split_027.html#id064pro04_r)

```
s := "hello, world"
fmt.Println(len(s))     // "12"
fmt.Println(s[0], s[7]) // "104 119"  ('h' and 'w')
```

尝试访问此范围之外的字节会导致 panic：

[点击此处查看代码图像](#part0132_split_028.html#id064pro05_r)

```
c := s[len(s)] // panic: index out of range
```

字符串的第 *i* 个字节不一定是字符串的第 *i* 个字符，因为非 ASCII 码点的 UTF-8 编码需要两个或更多字节。

字符处理将在稍后讨论。

子串操作 `s[i:j]` 生成一个新字符串，包含原字符串从索引 `i` 开始到索引 `j` 之前（不包括 `j`）的字节。结果包含 `j-i` 个字节。

```
fmt.Println(s[0:5]) // "hello"
```

同样，如果任一索引越界或 `j` 小于 `i`，会导致 panic。

`i` 和 `j` 操作数可以省略其中一个或两个，在这种情况下分别默认为 `0`（字符串开头）和 `len(s)`（字符串结尾）。

[点击此处查看代码图像](#part0132_split_029.html#id065pro01_r)

