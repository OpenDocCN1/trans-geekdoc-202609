

## 练习 3.4

遵循 [1.7 节](#ebook_split_017.html#id-lissajous-server) 中 Lissajous 示例的方法，构建一个 Web 服务器，用于计算曲面并将 SVG 数据写入客户端。服务器必须像这样设置 `Content-Type` 头部：

[点击此处查看代码图像](#ch03_images.html#id060pro01_r)

```
w.Header().Set("Content-Type", "image/svg+xml")
```

(在 Lissajous 示例中不需要此步骤，因为服务器使用标准启发式方法，通过响应的前 512 字节来识别 PNG 等常见格式，并生成适当的头部。) 允许客户端将高度、宽度和颜色等值作为 HTTP 请求参数指定。

## 3.3 复数

Go 提供两种大小的复数，`complex64` 和 `complex128`，其分量分别为 `float32` 和 `float64`。内置函数 `complex` 由实部和虚部创建一个复数，内置的 `real` 和 `imag` 函数提取这些分量：

[点击此处查看代码图像](#ch03_images.html#id061pro01_r)

```
var x complex128 = complex(1, 2) // 1+2i
var y complex128 = complex(3, 4) // 3+4i
fmt.Println(x*y)                 // "(-5+10i)"
fmt.Println(real(x*y))           // "-5"
fmt.Println(imag(x*y))           // "10"
```

如果浮点字面量或十进制整数字面量后面紧跟 `i`，例如 `3.141592i` 或 `2i`，它就变成了一个*虚数字面量*，表示实部为零的复数：

[点击此处查看代码图像](#ch03_images.html#id061pro02_r)

```
fmt.Println(1i * 1i) // "(-1+0i)", i² = -1
```

根据常量运算规则，复数常量可以与其他数字常量（整数或浮点数，实数或虚数）相加，这让我们可以自然地书写复数，如 `1+2i`，或等价地写作 `2i+1`。上面 `x` 和 `y` 的声明可以简化为：

```
x := 1 + 2i
y := 3 + 4i
```

复数可以使用 `==` 和 `!=` 进行相等性比较。如果两个复数的实部相等且虚部相等，则它们相等。

`math/cmplx` 包提供了用于复数运算的库函数，例如复数平方根和指数函数。

[点击此处查看代码图像](#ch03_images.html#id061pro03_r)

```
fmt.Println(cmplx.Sqrt(-1)) // "(0+1i)"
```

以下程序使用 `complex128` 运算生成曼德勃罗集。

[点击此处查看代码图像](#ch03_images.html#id061pro04_r)

gopl.io/ch3/mandelbrot

```
// Mandelbrot 生成曼德勃罗分形的 PNG 图像。
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
            // 图像点 (px, py) 代表复数值 z。
            img.Set(px, py, mandelbrot(z))
        }
    }
    png.Encode(os.Stdout, img) // 注意：忽略错误
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

两个嵌套循环遍历一个 1024×1024 灰度光栅图像中的每个点，该图像代表复平面上 −2 到 +2 的部分。程序测试反复平方并加上该点所代表的数字，最终是否会“逃逸”出半径为 2 的圆。如果是，则根据逃逸所需的迭代次数对该点进行着色。如果不是，则该值属于曼德勃罗集，该点保持黑色。最后，程序将标志性分形的 PNG 编码图像写入其标准输出，如 [图 3.3](#ebook_split_030.html#id-figures-mandelbrot) 所示。

### 练习 3.5

使用函数 `image.NewRGBA` 和类型 `color.RGBA` 或 `color.YCbCr` 实现全彩色的曼德勃罗集。

### 练习 3.6

超采样是一种通过在每个像素内的多个点计算颜色值并取平均值来减少像素化效应的技术。最简单的方法是将每个像素分成四个“子像素”。请实现它。

### 练习 3.7

另一个简单的分形使用牛顿法来寻找函数（如 *z*⁴−1 = 0）的复数解。根据接近四个根之一所需的迭代次数对每个起始点进行着色。根据点所趋近的根为每个点着色。

![曼德勃罗集。](graphics/mandelbrot.png)

**图 3.3。** 曼德勃罗集。

### 练习 3.8

在高缩放级别渲染分形需要极高的算术精度。使用四种不同的数字表示来实现相同的分形：`complex64`、`complex128`、`big.Float` 和 `big.Rat`。（后两种类型位于 `math/big` 包中。`Float` 使用任意但有界精度的浮点数；`Rat` 使用无界精度的有理数。）它们在性能和内存使用方面如何比较？在什么缩放级别渲染伪影会变得可见？

### 练习 3.9

编写一个 Web 服务器来渲染分形并将图像数据写入客户端。允许客户端将 *x*、*y* 和缩放值作为 HTTP 请求的参数指定。

## 3.4 布尔值

`bool` 类型的值，或称*布尔值*，只有两个可能的值：`true` 和 `false`。`if` 和 `for` 语句中的条件是布尔值，比较运算符如 `==` 和 `<` 会产生布尔结果。一元运算符 `!` 表示逻辑非，因此 `!true` 为 `false`，或者可以说 `(!true==false)==true`，尽管就风格而言，我们总是将冗余的布尔表达式如 `x==true` 简化为 `x`。

布尔值可以与 `&&`（逻辑与）和 `||`（逻辑或）运算符结合，它们具有*短路*行为：如果答案已由左操作数的值确定，则不会对右操作数求值，这使得可以安全地编写如下表达式：

```
s != "" && s[0] == 'x'
```

如果将 `s[0]` 应用于空字符串会导致 panic。

由于 `&&` 的优先级高于 `||`（助记符：`&&` 是布尔乘法，`||` 是布尔加法），因此这种形式的条件不需要括号：

[点击此处查看代码图像](#ch03_images.html#id064pro01_r)

```
if 'a' <= c && c <= 'z' ||
    'A' <= c && c <= 'Z' ||
    '0' <= c && c <= '9' {
    // ...ASCII 字母或数字...
}
```

布尔值不会隐式转换为 0 或 1 等数值，反之亦然。必须使用显式的 `if` 语句，如：

```
i := 0
if b {
    i = 1
}
```

如果经常需要此操作，编写一个转换函数可能很有用：

[点击此处查看代码图像](#ch03_images.html#id064pro02_r)

```
// btoi 如果 b 为 true 返回 1，如果为 false 返回 0。
func btoi(b bool) int {
    if b {
        return 1
    }
    return 0
}
```

逆操作非常简单，不值得写一个函数，但为了对称，这里给出：

[点击此处查看代码图像](#ch03_images.html#id064pro03_r)

```
// itob 报告 i 是否非零。
func itob(i int) bool { return i != 0 }
```

## 3.5 字符串

字符串是一个不可变的字节序列。字符串可以包含任意数据，包括值为 0 的字节，但通常它们包含人类可读的文本。文本字符串通常被解释为 UTF-8 编码的 Unicode 码点（rune）序列，我们很快将详细探讨这一点。

