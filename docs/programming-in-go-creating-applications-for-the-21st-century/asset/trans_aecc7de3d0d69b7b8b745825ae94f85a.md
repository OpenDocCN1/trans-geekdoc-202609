

## 9.1. 自定义包

```go
Package omap - Go 编程语言
File Edit View Go Tools Tabs Help
://localhost:9000/pkg/src/qrac.eu/omap/#New
func New
func New(less func(interface{}, interface{})) bool) *Map
New 返回一个空的 Map，它使用给定的 less 函数来比较键。
例如：

type Point struct { X, Y int }
pointMap := omap.New(func(a, b interface{}) bool {
	a, b := a.(Point), b.(Point)
	if a.X < b.X {
		return a.X < b.X
	}
	return a.Y < b.Y
}))
```

图 9.2 omap 包的 New() 函数的文档

函数和方法的文档必须紧接在它们的第一行代码之前。这是 omap 包的通用 New() 构造函数的文档。当使用 godoc 将作为网页显示时，它看起来是这样。此图也说明了文档中的缩进文本会被渲染为 HTML 中的 `code`。然而，在编写时，godoc 不支持任何标记（例如**粗体**、*斜体*、链接等）。

```go
// NewCaseFoldKey 返回一个不区分大小写键的空 Map。
func NewCaseedKey() *Map {
```

上面的代码片段显示了预定义 less 函数的文档。

```go
// Insert 向 Map 插入一个新的键值对，如果键相等则返回 true；
// 否则替换现有的键值对的值并返回 false。例如：
// inserted := myMap.Insert(key, value).
func (m *Map) Insert(key, value interface{}) (inserted bool) {
```

这是 Insert() 方法的文档。注意在 Go 中，函数或方法的文档以函数或方法的名称开头，并且（按照习惯）在引用函数或方法时不使用括号。

### 9.1.3. 单元测试与基准测试

Go 标准库对单元测试提供了良好的支持。为某个包设置单元测试的方法是在与要测试的包相同的目录下创建一个测试文件。该文件应该以包名开头并以 `_test.go` 结尾。例如，omap 包的测试文件名为 `omap_test.go`。

在书中示例中，测试文件存放在被测试的包中（例如 `omap`），这种情况下不需要导入被测试的包。这种方法意味着可以测试未导出的类型，并且可以添加方法来支持测试。然而，一些 Go 程序员更倾向于黑盒测试（black-box testing）。

测试文件的特殊之处在于它没有 `main()` 函数。相反，它有一个或多个以 `Test` 开头、接受单个 `testing.T` 类型参数且没有返回值的函数。我们可以添加任何需要的辅助函数，只要它们的名称以 Test 开头。

```go
func TestStringKey(t *testing.T) {
	word := omap.NewCaseedKey()
	for _, word := range []string{"one", "Two", "THREE", "four", "Five"} {
		word.Insert(word, word)
	}
	var words []string
	word.Do(func(_, value interface{}) {
		words = append(words, value.(string))
	})
	actual, expected := strings.Join(words, ""), "FiveTHREE"
	if actual != expected {
		t.Error("%q != %q", actual, expected)
	}
}
```

这是 `omap_test.go` 文件中的一个测试。它通过创建一个空的 omap.Map 开始，然后插入一些不区分大小写的字符串键和值。我们使用 `Map.Do` 方法遍历 map 中所有的键值对，并将每个值连接成一个字符串，检查它是否符合预期。如果匹配失败，我们调用 `testing.T.Error` 方法报告失败并提供一些解释。如果没有调用该方法，则假设测试通过。

```go
func BenchmarkFind(b *testing.B) {
	b.StopTimer() // 不要计时创建和填充
	intMap := omap.New()
	for i := 0; i < 1e6; i++ {
		intMap.Insert(i, i)
	}
	b.StartTimer() // 为 Find() 方法
	for i := 0; i < b.N; i++ {
		intMap.Find(i)
	}
}
```

该函数首先停止计时器，因为我们不想计时 omap.Map 的创建和填充。我们随后创建一个空的 omap.Map 并用百万个键值对填充它。默认情况下，test 不运行任何基准测试，如果我们想运行它们，必须显式使用 `-bench` 选项并提供匹配我们要运行的基准测试的正则表达式。`.*` 正则匹配任何内容，也就是说测试文件中的所有基准测试都可以工作。

```bash
$ go test -bench=.*
ok    qrac.eu/omap
PASS
BenchmarkFind-Success    1000000    1380 ns/op
BenchmarkFind-Failure  1000000    1350 ns/op
```

此输出显示了两个基准测试运行了 1,000,000 次迭代，单位是每次操作的纳秒。迭代次数（即 `b.N` 的值）由 `go test` 选择，但我们可以使用 `-bench` 选项查看我们希望每个基准测试运行的大致秒数。

除了 omap 包之外，书中其他几个示例也有 `package_test.go` 文件。

### 9.1.2. 导入包

Go 允许我们为包起别名。这个功能可能非常方便且有用——使得在包的两个实现之间切换变得容易。例如，我们可以这样导入包：`import v1 "v1"`，这样在代码中访问的就是 `v1` 包。稍后当有更成熟的实现时，我们可以通过将导入改为 `v2` 来切换到它。如果 v1 和 v2 提供了相同的 API（或者 v2 的 API 是 v1 的超集），这种方法将行有效，并且意味着其余代码可以保持不变。另一方面，为标准库包名起别名可能是最好的，因为这可能会给以后维护者带来困惑或不满。

正如我们在第 5 章（5.6.2）中提到的，当一个包被导入时，它的 `init()` 函数会被执行（如果有的话）。在某些情况下，我们不想显式使用某个包，但希望它的 `init()` 执行。

例如，如果我们正在处理图像，我们可能注册 Go 支持的所有格式，但实际上并不使用提供格式的包函数。这是第 7 章练习题 `imag1.go` 的导入语句。

```go
import (
    "fmt"
    "image"
    "os"
    "path/filepath"
    "runtime"
    "image/gif"
    "image/jpeg"
    "image/png"
)
```

我们导入 image/gif、image/jpeg 和 image/png 包纯是为了执行它们的 `init()` 函数（这会将它们的格式注册到 image 包中）。这些包的每一个都别名为空白标识符 `_`，Go 不会抱怨在代码中没有显式使用其中任何一个。

