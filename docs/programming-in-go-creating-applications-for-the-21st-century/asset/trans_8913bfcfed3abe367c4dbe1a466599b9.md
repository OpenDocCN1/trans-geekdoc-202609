

## 5.6. 自定义函数

每个额外的 `else if` 子句需要两行代码；对于 `switch` 版本，我们需要为每个新的 `case` 增加一行（如果使用 `gofmt` 格式化 case 则需要两行）。如果该函数用于文件管理器，它可能很容易变成处理后缀句柄，这会导致函数变得非常长。

```go
var FunctionForSuffix = map[string]func(string) (string, error) {
    ".gz": ZipFileList, ".tar": TarFileList, ".tar.gz": TarFileList,
    ".tgz": TarFileList, ".zip": ZipFileList}
func ArchiveFileListMap(file string) ([string, error) {
    if function, ok := FunctionForSuffix(Suffix(file)); ok {
        return function(file)
    }
    return nil, errors.New("unrecognized archive")
}
```

这个版本的函数使用了一个 map，其键为字符串（文件后缀），其值为签名类型 `func(string) ([string, error)` 的函数。（所有的自定义函数 `ZipFileList()`、`TarFileList()` 和 `ZipFileList()` 都是这种类型）。

该函数使用索引操作符检索与给定后缀匹配的函数，并将 `ok` 设置为 `true`；如果后缀不是 map 的键，则返回 `nil` 和 `false`。如果存在匹配的函数，则用文件名调用该函数并返回其结果。

这种函数比使用 `if` 或 `switch` 语句更具扩展性，因为无论向 `FunctionForSuffix` map 中添加多少个文件后缀项，函数都保持不变。与大型 `if` 或 `switch` 语句不同，map 的查找速度不会随着项目数量的增加而下降。此外，这样使用 map 可以让代码更清晰，并且能够动态向 map 中添加新项。

### 5.6.5.2. 动态函数创建

另一种场景是在运行时选择函数，当我们有两个或多个使用不同算法实现相同功能的函数，且不想在程序编译时确定其中任何一个（例如，允许我们为基准测试或回归测试进行动态选择）。

例如，我们使用仅包含 7 位 ASCII 字符的字符串来编写我们之前看到的 `IsPalindrome()` 函数的简单得的版本（229 ◄），并在运行时仅创建程序实际需要的版本。

> * 在一台负载较轻的 AMD-6 四核 3GHz 机器上，我们发现一旦需要考虑 50 个或更多情况，使用 map 就会始终比 `switch` 快。

## 232 第 5 章 过程化编程

实现此点的方法是声明一个具有函数签名的包级变量，并在 `init()` 函数中创建相应的函数。

```go
var IsPalindrome func(string) bool // 持有对函数的引用
func init() {
	if len(os.Args) > 1 &&
		os.Args[1] == "-a" || os.Args[1] == "-ascii" {
		os.Args = append(os.Args[:1], os.Args[2:]...) // 移除参数。
		isPalindrome = func(s string) bool { // 简单的仅 ASCII 版本
		if len(s) < 1 {
			return true
		}
			if s[0] != s[len(s)-1] {
			return false
		}
		return IsPalindrome(s[1 : len(s)-1])
	}
	} else {
		isPalindrome = func(s string) bool { // UTF-8 版本
		// ... 与之前相同 ...
	}
}
```

我们让 `IsPalindrome()` 的实现取决于命令行参数。如果给出了该参数，我们从 `os.Args` 切片中将其移除（这样程序的其余部分就不需要知道或关心它），并创建一个 7 位 ASCII 版本的 `IsPalindrome()` 函数。当我们使用 `os.Args` 保留其第一个字符串以及第三个及后续字符串，但不保留第二个字符串（字符串 `"-a"` 或 `"-ascii"`）时，这种移除操作略显微妙。我们不能在 `append()` 调用中使用 `os.Args[0]`，因为第一个参数必须是一个切片，所以我们使用 `os.Args[:1]` 作为包含 `os.Args[0]` 的单项切片（$4.2.1, 153）。如果不存在 ASCII 参数，我们创建一个与之前看到的相同的版本，该版本在 7 位 ASCII 和 UTF-8 Unicode 字符串上都能正常工作。程序的其余部分可以正常调用 `IsPalindrome()` 函数，但实际执行的代码将取决于创建了哪一个版本。（此示例的源代码位于 `palindrome/palindrome.go`。）

## 5.6.6. 通用函数

在本章前面，我们创建了一个函数来找到传递给它的 `int` 参数中的最小值值（221 ◄）。该函数中使用的算法也可以应用于其他数值类型或字符串，因为它适用于任何支持 `<` 运算符的类型。在 C++ 中，对于此类情况，我们会创建一个由类型参数化的泛型函数，这将导致编译器创建我们所需的许多个版本的函数（即每个使用的类型创建一个）。在 Go 中，在编写本文时，不支持类型参数化，因此为了获得与 C++ 相同的效果，我们必须手动创建需要的函数（例如，`MinimumInt()`、`MinimumFloat()`、`MinimumString()`）。这样，每个每个使用的类型都会得到一个函数（就像 C++ 一样，但在 Go 中每个函数必须有唯一的名称）。

Go 提供了多种替代方法，避免了创建对其操作的函数的需求，但是以了一些运行时效率为代价。对于不经常使用或运行足够快的小函数，替代方法可以非常方便。以下是泛型 `Minimum()` 函数的示例：

```go
i := Minimum(4, 3, 8, 2)
fmt.Printf("%T v\n", i)
f := Minimum(9, 5.4, 17, 3.8)
fmt.Printf("%T v\n", f)
s := Minimum("K", "B", "C", "D")
fmt.Printf("%T v\n", s)
```

该函数返回一个类型为 `interface{}` 的值，我们使用未经检查的断言（§5.1.2, 191）将其转换为预期的内置类型。

```go
func Minimum(first interface{}, rest ...interface{}) interface{} {
  minimum := first
  for _, x := range rest {
    switch x := x.(type) {
    case int:
      if x < minimum.(int) {
        minimum = x
      }
    case float64:
      if x < minimum.(float64) {
        minimum = x
      }
    case string:
      if x < minimum.(string) {
        minimum = x
      }
    }
  }
  return minimum
}
```
*(注：原文代码块在结尾不完整，此处根据逻辑补全了 switch 和 for 的闭合括号及 return)*

