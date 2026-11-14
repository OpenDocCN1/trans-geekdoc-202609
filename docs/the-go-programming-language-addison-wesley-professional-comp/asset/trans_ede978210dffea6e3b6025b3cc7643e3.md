

## 3.1 浮点数

```go
for x := 0; x < 8; x++ {
    fmt.Printf("x = %d ex = %8.3f\n", x, math.Exp(float64(x)))
}
```

上述代码打印 `e` 的幂，保留三位小数，在八字符宽度的字段中对齐：

```
x = 0   ex =    1.000
x = 1   ex =    2.718
x = 2   ex =    7.389
x = 3   ex =   20.086
x = 4   ex =   54.598
x = 5   ex =  148.413
x = 6   ex =  403.429
x = 7   ex = 1096.633
```

除了大量常用数学函数，`math` 包还提供了创建和检测 IEEE 754 定义的特殊值的函数：正负无穷大（表示数值过大和除零的结果）以及 NaN（“非数字”，表示 `0/0` 或 `Sqrt(-1)` 等数学上可疑操作的结果）。

[点击此处查看代码图片](#part0132_split_015.html#id057pro03_r)

```go
var z float64
fmt.Println(z, -z, 1/z, -1/z, z/z) //  "0 -0 +Inf -Inf NaN"
```

函数 `math.IsNaN` 用于测试其参数是否为非数字值，`math.NaN` 返回此类值。虽然想用 NaN 作为数值计算中的哨兵值，但测试某个计算结果是否等于 NaN 充满陷阱，因为与 NaN 的任何比较**总是**返回 `false`：

[点击此处查看代码图片](#part0132_split_016.html#id057pro04_r)

```go
nan := math.NaN()
fmt.Println(nan == nan, nan < nan, nan > nan) // "false false false"
```

如果返回浮点结果的函数可能失败，最好单独报告失败，如下所示：

[点击此处查看代码图片](#part0132_split_017.html#id057pro05_r)

```go
func compute() (value float64, ok bool) {
    // ...
    if failed {
        return 0, false
    }
    return result, true
}
```

## 3.2 浮点数图形计算

下一个程序演示浮点数图形计算。它将二元函数 `z = f(x, y)` 绘制为线框 3D 曲面，使用可缩放矢量图形（SVG），一种用于线条绘图的标准 XML 表示法。[图 3.1](#part0030.html#id-surface) 显示了函数 `sin(r)/r` 的输出示例，其中 `r` 为 `sqrt(x*x+y*y)`。

![函数 sin(r)/r 的曲面图。](images/00008.jpeg)

**图 3.1.** 函数 `sin(r)/r` 的曲面图。

[点击此处查看代码图片](#part0132_split_018.html#id058pro01_r)

gopl.io/ch3/surface

```go
// Surface computes an SVG rendering of a 3-D surface function.
package main

import (
    "fmt"
    "math"
)

const (
    width, height = 600, 320            // canvas size in pixels
    cells         = 100                 // number of grid cells
    xyrange       = 30.0                // axis ranges (-xyrange..+xyrange)
    xyscale       = width / 2 / xyrange // pixels per x or y unit
    zscale        = height * 0.4        // pixels per z unit
    angle         = math.Pi / 6         // angle of x, y axes (=30°)
)

var sin30, cos30 = math.Sin(angle), math.Cos(angle) // sin(30°), cos(30°)

func main() {
    fmt.Printf("<svg xmlns='http://www.w3.org/2000/svg' "+
        "style='stroke: grey; fill: white; stroke-width: 0.7' "+
        "width='%d' height='%d'>", width, height)
    for i := 0; i < cells; i++ {
        for j := 0; j < cells; j++ {
            ax, ay := corner(i+1, j)
            bx, by := corner(i, j)
            cx, cy := corner(i, j+1)
            dx, dy := corner(i+1, j+1)
            fmt.Printf("<polygon points='%g,%g %g,%g %g,%g %g,%g'/>\n",
                ax, ay, bx, by, cx, cy, dx, dy)
        }
    }
    fmt.Println("</svg>")
}

func corner(i, j int) (float64, float64) {
    // Find point (x,y) at corner of cell (i,j).
    x := xyrange * (float64(i)/cells - 0.5)
    y := xyrange * (float64(j)/cells - 0.5)

    // Compute surface height z.
    z := f(x, y)

    // Project (x,y,z) isometrically onto 2-D SVG canvas (sx,sy).
    sx := width/2 + (x-y)*cos30*xyscale
    sy := height/2 + (x+y)*sin30*xyscale - z*zscale
    return sx, sy
}

func f(x, y float64) float64 {
    r := math.Hypot(x, y) // distance from (0,0)
    return math.Sin(r) / r
}
```

注意函数 `corner` 返回两个值，即单元格角点的坐标。

程序工作原理的解释只需要基本几何知识，但跳过也没关系，因为重点是演示浮点数计算。程序的核心是在三个不同坐标系之间映射，如[图 3.2](#part0030.html#id-figures-surface-explain)所示。第一个是 100×100 单元格的二维网格，由整数坐标 `(i, j)` 标识，从远后角的 (0, 0) 开始。我们从后向前绘制，以便背景多边形可能被前景多边形遮挡。

![三个不同的坐标系。](images/00009.jpeg)

**图 3.2.** 三个不同的坐标系。

第二个坐标系是三维浮点坐标 `(x, y, z)` 的网格，其中 `x` 和 `y` 是 `i` 和 `j` 的线性函数，平移使原点居中，并按常量 `xyrange` 缩放。高度 `z` 是曲面函数 `f(x, y)` 的值。

第三个坐标系是二维图像画布，左上角为 (0, 0)。该平面上的点记为 `(sx, sy)`。我们使用等轴测投影将每个三维点 `(x, y, z)` 映射到二维画布。`x` 值越大或 `y` 值越小，点在画布上显得越靠右。`x` 值或 `y` 值越大，且 `z` 值越小，点显得越靠下。`x` 和 `y` 的垂直和水平缩放因子源自 30° 角的正弦和余弦。`z` 的缩放因子 0.4 是任意参数。

对于二维网格中的每个单元格，`main` 函数计算多边形 `ABCD` 四个角在图像画布上的坐标，其中 `B` 对应 `(i, j)`，`A`、`C`、`D` 为其邻居，然后打印绘制它的 SVG 指令。

### 练习

**练习 3.1：** 如果函数 `f` 返回非有限 `float64` 值，SVG 文件将包含无效的 `<polygon>` 元素（尽管许多 SVG 渲染器能优雅处理）。修改程序以跳过无效多边形。

**练习 3.2：** 尝试可视化 `math` 包中的其他函数。你能生成蛋盒、雪包或鞍面吗？

**练习 3.3：** 根据高度为每个多边形着色，使峰值呈红色 (`#ff0000`)，谷值呈蓝色 (`#0000ff`)。

**练习 3.4：** 参考[第 1.7 节](#part0018.html#id-lissajous-server)中利萨如示例的方法，构建一个 Web 服务器，计算曲面并将 SVG 数据写入客户端。服务器必须设置 `Content-Type` 头，如下所示：

[点击此处查看代码图片](#part0132_split_019.html#id060pro01_r)

```go
w.Header().Set("Content-Type", "image/svg+xml")
```

（利萨如示例中不需要此步骤，因为服务器使用标准启发式方法从响应的前 512 字节识别 PNG 等常见格式，并生成适当的头部。）允许客户端通过 HTTP 请求参数指定高度、宽度和颜色等值。

## 3.3 复数

Go 提供两种大小的复数：`complex64` 和 `complex128`，其分量分别为 `float32` 和 `float64`。内置函数 `complex` 从实部和虚部创建复数，内置函数 `real` 和 `imag` 提取这些分量：

[点击此处查看代码图片](#part0132_split_020.html#id061pro01_r)

```go
var x complex128 = complex(1, 2) // 1+2i
var y complex128 = complex(3, 4) // 3+4i
fmt.Println(x*y)                 // "(-5+10i)"
fmt.Println(real(x*y))           // "-5"
fmt.Println(imag(x*y))           // "10"
```

