
“enough” 对我们的角度来说已经足够相等了。但有一个简单的方法可以恢复精度：我们重新排列方程，使其不再先除后乘。我们可以只通过除法来完成所有操作。

所以不是

```text
numberOfSeconds * π / 30
```

我们可以写成

```text
π / (30 / numberOfSeconds)
```

这是等价的。

在 Go 中：

```go
func secondsInRadians(t time.Time) float64 {
    return math.Pi / (30 / float64(t.Second()))
}
```

并且我们通过了测试。

```text
PASS
ok      clockface      0.005s
```

它应该看起来像这样。

## 关于除以零的说明

计算机通常不喜欢除以零，因为无穷大有点奇怪。

在 Go 中，如果你尝试显式地除以零，你会得到编译错误。

```go
package main

import (
    "fmt"
)

func main() {
    fmt.Println(10.0 / 0.0) // fails to compile
}
```

显然，编译器并不能总是预测你会除以零，例如使用我们的 `t.Second()` 时。

### 试试这个

```go
func main() {
    fmt.Println(10.0 / zero())
}

func zero() float64 {
    return 0.0
}
```

它会打印 `+Inf`（无穷大）。除以 `+Inf` 似乎会得到零，我们可以通过以下代码看到这一点：

```go
package main

import (
    "fmt"
    "math"
)

func main() {
    fmt.Println(secondsInRadians())
}

func zero() float64 {
    return 0.0
}

func secondsInRadians() float64 {
    return math.Pi / (30 / float64(zero()))
}
```

## 重复新需求

所以这里第一部分已经完成——我们知道秒针在弧度上指向的角度。现在我们需要计算坐标。

再次，让我们尽可能保持简单，只使用单位圆：半径为 1 的圆。这意味着我们的指针长度都为 1，但好的一面是，这意味着数学对我们来说很容易理解。

## 先写测试

```go
func TestSecondHandVector(t *testing.T) {
    cases := []struct {
        time  time.Time
        point Point
    }{
        {simpleTime(0, 0, 30), Point{0, -1}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := secondHandPoint(c.time)
            if got != c.point {
                t.Fatalf("Wanted %v Point, but got %v", c.point, got)
            }
        })
    }
}
```

## 尝试运行测试

```text
./clockface_test.go:40:11: undefined: secondHandPoint
```

## 编写最少的代码使测试运行并检查失败的测试输出

```go
func secondHandPoint(t time.Time) Point {
    return Point{}
}
```

```text
clockface_test.go:42: Wanted {0 -1} Point, but got {0 0}
```

## 编写足够代码使其通过

```go
func secondHandPoint(t time.Time) Point {
    return Point{0, -1}
}
```

```text
PASS
ok      clockface   0.007s
```

## 重复新需求

```go
func TestSecondHandPoint(t *testing.T) {
    cases := []struct {
        time  time.Time
        point Point
    }{
        {simpleTime(0, 0, 30), Point{0, -1}},
        {simpleTime(0, 0, 45), Point{-1, 0}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := secondHandPoint(c.time)
            if got != c.point {
                t.Fatalf("Wanted %v Point, but got %v", c.point, got)
            }
        })
    }
}
```

### 尝试运行测试

```text
clockface_test.go:43: Wanted {-1 0} Point, but got {0 -1}
```

## 编写足够代码使其通过

还记得我们的单位圆图吗？

![](img/570fb0b5bd524332c8e0fb9e37d716fb_280_0.png)

另外请记住，我们希望从 12 点钟方向测量角度，即 Y 轴，而不是从 X 轴测量，这意味着测量秒针与 3 点钟方向之间的角度。

![](img/570fb0b5bd524332c8e0fb9e37d716fb_281_0.png)

现在我们想要产生 X 和 Y 的方程。让我们把它写成秒：

```go
func secondHandPoint(t time.Time) Point {
    angle := secondsInRadians(t)
    x := math.Sin(angle)
    y := math.Cos(angle)

    return Point{x, y}
}
```

## 现在我们得到

```text
clockface_test.go:43: Wanted {0 -1} Point, but got {1.2246467991473515e-16 -1}

clockface_test.go:43: Wanted {-1 0} Point, but got {-1 -1.8369701987210272e-16}
```

等等，又怎么了？看起来我们再次被浮点数诅咒了——这两个意外的数字都是极其微小的，低到小数点后 16 位。所以再次，我们可以选择尝试提高精度，或者就说它们大致相等，然后继续生活。

提高这些角度精度的一个选择是使用 `math/big` 包中的有理数类型 `Rat`。但鉴于目标是绘制 SVG 而不是登月，我认为我们可以容忍一点模糊性。

```go
func TestSecondHandPoint(t *testing.T) {
    cases := []struct {
        time  time.Time
        point Point
    }{
        {simpleTime(0, 0, 30), Point{0, -1}},
        {simpleTime(0, 0, 45), Point{-1, 0}},
    }

    for _, c := range cases {
        t.Run(testName(c.time), func(t *testing.T) {
            got := secondHandPoint(c.time)
            if !roughlyEqualPoint(got, c.point) {
                t.Fatalf("Wanted %v Point, but got %v", c.point, got)
            }
        })
    }
}
```

```go
func roughlyEqualFloat64(a, b float64) bool {
    const equalityThreshold = 1e-7
    return math.Abs(a-b) < equalityThreshold
}
```

```go
func roughlyEqualPoint(a, b Point) bool {
    return roughlyEqualFloat64(a.X, b.X) &&
        roughlyEqualFloat64(a.Y, b.Y)
}
```

我们定义了两个函数来定义两个 Point 之间的近似相等——如果 X 和 Y 元素之间的差异在 0.0000001 以内，它们就会生效。这仍然相当精确。

现在我们得到：

```text
PASS
ok      clockface   0.007s
```

## 重构

我对这个结果仍然相当满意。

它现在看起来是这样的。

## 重复新需求

好吧，说“新”并不完全准确——实际上，我们现在可以做的就是让那个验收测试通过！让我们回顾一下它是什么样子的：

```go
func TestSecondHandAt30Seconds(t *testing.T) {
    tm := time.Date(1337, time.January, 1, 0, 0, 30, 0, time.UTC)

    want := clockface.Point{X: 150, Y: 150 + 90}
    got := clockface.SecondHand(tm)

    if got != want {
        t.Errorf("Got %v, wanted %v", got, want)
    }
}
```

### 尝试运行测试

```text
clockface_acceptance_test.go:28: Got {150 60}, wanted {150 240}
```

## 编写足够代码使其通过

我们需要做三件事将单位向量转换为 SVG 上的点：

- 按指针长度缩放它。
- 在 X 轴上翻转它，以考虑 SVG 的原点位于左上角。
- 将其平移到正确的位置（使其原点为 (150,150)）。

有趣的时光！

```go
// SecondHand is the unit vector of the second hand of an analogue clock
// represented as a Point.
func SecondHand(t time.Time) Point {
    p := secondHandPoint(t)
    p = Point{p.X * 90, p.Y * 90}    // scale
    p = Point{p.X, -p.Y}             // flip
    p = Point{p.X + 150, p.Y + 150} // translate
    return p
}
```

按这个顺序缩放、翻转和平移。万岁，数学！

```text
PASS
ok      clockface  0.007s
```

## 重构

这里有一些魔数应该提取为常量，所以让我们这样做。

```go
const secondHandLength = 90
const clockCentreX = 150
const clockCentreY = 150
```

```go
// SecondHand is the unit vector of the second hand of an analogue clock
// represented as a Point.
func SecondHand(t time.Time) Point {
    p := secondHandPoint(t)
    p = Point{p.X * secondHandLength, p.Y * secondHandLength}
    p = Point{p.X, -p.Y}
    p = Point{p.X + clockCentreX, p.Y + clockCentreY} // translate
    return p
}
```

## 绘制时钟

好吧……至少是秒针……

让我们做这件事——因为没有什么比不交付价值更糟糕的了，而它正坐在这里等待着走进世界去惊艳人们。让我们画一个秒针吧！

我们将在主 clockface 包目录下创建一个新目录，（令人困惑地）也叫做 `clockface`。在那里，我们将放置主包，该包将创建构建 SVG 的二进制文件：

```text
|-- clockface
|   |-- main.go
|-- clockface.go
|-- clockface_acceptance_test.go
|-- clockface_test.go
```

在 `main.go` 中，你将从这段代码开始，但请更改 clockface 包的导入，使其指向你自己的版本：

```go
package main

import (
    "fmt"
    "io"
    "os"
    "time"

    "github.com/quii/learn-go-with-tests/math/clockface" // REPL.
)

func main() {
    t := time.Now()
```
