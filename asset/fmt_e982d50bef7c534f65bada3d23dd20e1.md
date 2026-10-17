
# SVG 时钟编写器与测试重构

## 代码实现

```go
"time"
)

const (
    secondHandLength = 90
    clockCentreX     = 150
    clockCentreY     = 150
)

//SVGWriter writes an SVG representation of an analogue clock, si
func SVGWriter(w io.Writer, t time.Time) {
    io.WriteString(w, svgStart)
    io.WriteString(w, bezel)
    secondHand(w, t)
    io.WriteString(w, svgEnd)
}

func secondHand(w io.Writer, t time.Time) {
    p := secondHandPoint(t)
    p = Point{p.X * secondHandLength, p.Y * secondHandLength} //
    p = Point{p.X, -p.Y}                                   //
    p = Point{p.X + clockCentreX, p.Y + clockCentreY}      //
    fmt.Fprintf(w, `<line x1="150" y1="150" x2="%f" y2="%f" style
}

const svgStart = `<?xml version="1.0" encoding="UTF-8" standalone
<!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org
<svg xmlns="http://www.w3.org/2000/svg"
    width="100%"
    height="100%"
    viewBox="0 0 300 300"
    version="2.0">`

const bezel = `<circle cx="150" cy="150" r="100" style="fill:#ff:`

const svgEnd = `</svg>`
```

最漂亮的 SVG writer？不。但希望它能完成工作...

clockface_acceptance_test.go:56: Expected to find the second hand with x2 of 150 and y2 of 60, in the SVG output <?xml

version="1.0" encoding="UTF-8" standalone="no"?>

    <!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN" "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">

    <svg xmlns="http://www.w3.org/2000/svg"

        width="100%"

        height="100%"

        viewBox="0 0 300 300"

        version="2.0"><circle cx="150" cy="150" r="100" style="fill:#fff;stroke:#000;stroke-width:5px;"/><line x1="150" y1="150" x2="150.000000" y2="60.000000" style="fill:none;stroke:#f00;stroke-width:3px;"/></svg>

哎呀！`%f` 格式指令会把我们的坐标打印到默认的精度级别——六位小数。我们应该明确我们期望坐标的精度级别。让我们说三位小数。

```go
fmt.Fprintf(w, `<line x1="150" y1="150" x2="%.3f" y2="%.3f"`
```

并且在测试中更新我们的期望后

```go
x2 := "150.000"

y2 := "60.000"
```

我们得到：

```
PASS

ok      clockface  0.006s
```

我们现在可以简化我们的 `main` 函数：

```go
package main

import (

    "os"

    "time"

    "github.com/gypsydave5/learn-go-with-tests/math/v7b/clockface"

)

func main() {

    t := time.Now()

```

```go
clockface.SVGWriter(os.Stdout, t)

}

```

这就是现在应该的样子。

并且我们可以按照相同的模式为另一个时间写一个测试，但在那之前……

## 重构

有三件事很突出：

1. 我们并不是真正测试了需要确保存在的所有信息——比如 `x1` 值呢？
2. 另外，那些 `x1` 等属性的属性真的不是字符串吗？它们是数字！
3. 我真的在乎手的样式吗？或者说，`zek` 生成的空 `Text` 节点呢？

我们可以做得更好。让我们对 `Svg` 结构体和测试做一些调整，使一切更清晰。

```go
type SVG struct {

    XMLName xml.Name `xml:"svg"`

    Xmlns   string    `xml:"xmlns,attr"`

    Width   string    `xml:"width,attr"`

    Height  string    `xml:"height,attr"`

    ViewBox string    `xml:"viewBox,attr"`

    Version string    `xml:"version,attr"`

    Circle  Circle    `xml:"circle"`

    Line    []Line    `xml:"line"`

}

```

```go
type Circle struct {

    Cx float64 `xml:"cx,attr"`

    Cy float64 `xml:"cy,attr"`

    R  float64 `xml:"r,attr"`

}

```

```go
type Line struct {

    X1 float64 `xml:"x1,attr"`

    Y1 float64 `xml:"y1,attr"`

    X2 float64 `xml:"x2,attr"`

    Y2 float64 `xml:"y2,attr"`

}

```

这里我

- 将结构体中重要的部分命名为类型 -- `Line` 和 `Circle`
- 将数值属性改为 `float64` 而不是 `string`。
- 删除了未使用的属性，如 `Style` 和 `Text`
- 将 `Svg` 重命名为 `SVG`，因为这是 *正确的做法*。

这将让我们能够更精确地断言我们正在查找的线条：

```go
func TestSVGWriterAtMidnight(t *testing.T) {

    tm := time.Date(1337, time.January, 1, 0, 0, 0, 0, time.UTC)

    b := bytes.Buffer{}

    clockface.SVGWriter(&b, tm)

    svg := SVG{}

    xml.Unmarshal(b.Bytes(), &svg)

    want := Line{150, 150, 150, 60}

    for _, line := range svg.Line {

        if line == want {

            return

        }

    }

    t.Errorf("Expected to find the second hand line %+v, in the s")

}

```

最后我们可以借鉴单元测试中的表格，并编写一个辅助函数 `containsLine(line Line, lines []Line) bool`

真正让这些测试出彩：

```go
func TestSVGWriterSecondHand(t *testing.T) {

    cases := []struct {

        time time.Time

        line Line

    }{

        {

            simpleTime(0, 0, 0),

            Line{150, 150, 150, 60},

        },

        {

            simpleTime(0, 0, 30),

            Line{150, 150, 150, 240},

        },

    }

    for _, c := range cases {

        t.Run(testName(c.time), func(t *testing.T) {

            b := bytes.Buffer{}

            clockface.SVGWriter(&b, c.time)

            svg := SVG{}

            xml.Unmarshal(b.Bytes(), &svg)

            if !containsLine(c.line, svg.Line) {

                t.Errorf("Expected to find the second hand line `"

            }

        })

    }

}

func containsLine(l Line, ls []Line) bool {

    for _, line := range ls {

        if line == l {

            return true

        }

    }

    return false

}

```

它看起来像这样

现在 *那就是* 我所说的验收测试！

## 先写测试

所以秒针已经完成了。现在让我们开始处理分针。

```go
func TestSVGWriterMinuteHand(t *testing.T) {

    cases := []struct {

        time time.Time

        line Line

    }{

        {

            simpleTime(0, 0, 0),

            Line{150, 150, 150, 70},

        },

    }

    for _, c := range cases {

        t.Run(testName(c.time), func(t *testing.T) {

            b := bytes.Buffer{}

            clockface.SVGWriter(&b, c.time)

            svg := SVG{}

            xml.Unmarshal(b.Bytes(), &svg)

            if !containsLine(c.line, svg.Line) {

                t.Errorf("Expected to find the minute hand line `"

            }

        })

    }

}

```

## 尝试运行测试

clockface_acceptance_test.go:87: Expected to find the minute hand line {X1:150 Y1:150 X2:150 Y2:70}, in the SVG lines

[{X1:150 Y1:150 X2:150 Y2:60}]

我们最好开始构建其他一些时钟指针。就像我们为秒针生成测试一样，我们可以迭代生成以下一组测试。再次在我们使其正常工作时注释掉我们的验收测试：

```go
func TestMinutesInRadians(t *testing.T) {

    cases := []struct {

        time  time.Time

        angle float64

    }{

        {simpleTime(0, 30, 0), math.Pi},

    }

    for _, c := range cases {

        t.Run(testName(c.time), func(t *testing.T) {

            got := minutesInRadians(c.time)

            if got != c.angle {

                t.Fatalf("Wanted %v radians, but got %v", c.angle

```

## 尝试运行测试

./clockface_test.go:59:11: undefined: `minutesInRadians`

## 为测试运行编写最少量的代码并检查失败的测试输出

```go
func minutesInRadians(t time.Time) float64 {

    return math.Pi

}

```

## 为新需求重复

好吧，好的——现在让我们做一些 *真正* 的工作。我们可以将分针建模为仅在整分钟移动——这样它就会在 30 分和 31 分之间“跳跃”而不在此期间移动。但那样看起来有点糟糕。我们希望它每秒移动 *一点点*。

```go
func TestMinutesInRadians(t *testing.T) {

    cases := []struct {

        time    time.Time

        angle   float64

    }{

        {simpleTime(0, 30, 0), math.Pi},

        {simpleTime(0, 0, 7), 7 * (math.Pi / (30 * 60))},

    }

    for _, c := range cases {

        t.Run(testName(c.time), func(t *testing.T) {

            got := minutesInRadians(c.time)

            if got != c.angle {

                t.Fatalf("Wanted %v radians, but got %v", c.angle

            }

        })

    }

}

```

这点小幅度是多少呢？嗯...

- 一分钟六十秒
- 半圈中有三十分钟 (`math.Pi` 弧度)
- 所以半圈中有 `30 * 60` 秒。
- 所以如果时间是整点后 7 秒 ...
- ... 我们预计分针会在 12 点之后 `7 * (math.Pi / (30 * 60))` 弧度处。

## 尝试运行测试

```

clockface_test.go:62: Wanted 0.012217304763960306 radians, but

got 3.141592653589793

```

## 编写足够代码使其通过

在詹妮弗·安妮斯顿的不朽名言中：这里来科学部分

```go
func minutesInRadians(t time.Time) float64 {

    return (secondsInRadians(t) / 60) +

        (math.Pi / (30 / float64(t.Minute())))

}

```

与其从头开始计算每秒钟将分针推过表盘的距离，这里我们可以直接利用 `secondsInRadians` 函数。每秒钟，分针将移动秒针移动角度的 1/60。

`secondsInRadians(t) / 60`

然后我们只需加上分钟的移动量——类似于秒针的移动。

`math.Pi / (30 / float64(t.Minute()))`

并且...

```
PASS

ok      clockface  0.007s
```

很简单。这就是现在的情况

## 为新需求重复

我应该为 `minutesInRadians` 测试添加更多用例吗？目前只有两个。在进行 `minuteHandPoint` 函数的测试之前，我需要多少个用例？

我最喜欢的 TDD 名言之一，常被归因于 Kent Beck,3 是

> 写测试直到恐惧转变为无聊。

说实话，我对测试那个函数感到厌倦了。我有信心知道它是如何工作的。所以下一个。

## 先写测试

```go
func TestMinuteHandPoint(t *testing.T) {

    cases := []struct {

        time  time.Time

        point Point

    }{

        {simpleTime(0, 30, 0), Point{0, -1}},

    }

    for _, c := range cases {

        t.Run(testName(c.time), func(t *testing.T) {

            got := minuteHandPoint(c.time)

            if !roughlyEqualPoint(got, c.point) {
