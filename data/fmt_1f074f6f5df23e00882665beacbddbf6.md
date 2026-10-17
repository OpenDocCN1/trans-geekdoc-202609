
如果我们想修改切片中的项，必须使用一个提供有效索引而不是切片项拷贝的 `for` 循环。

## 4.2.1 数组与切片

```
for i := range amounts {
	amounts[i] *= 1.05
	sum += amounts[i]
}
fmt.Printf("%s %.1f %.1f\n", amounts, sum)
[241.7 275.0 287.6 294.0 295.1 318.3 243.0 238.7 219.7 206.9] -> 2628.1
```

我们将切片中的每个项增加了 5% 并对其进行了累加。

切片当然可以包含自定义项。这里有一个带有单个自定义方法的自定义类型。

```
type Product struct {
	name string
	price float64
}
```

```
func (product Product) String() string {
	return fmt.Sprintf("%s %.2f", product.name, product.price)
}
```

这定义了 `Product` 类型为包含 `string` 和 `float64` 字段的结构体。我们还定义了 `String()` 来控制 Go 如何使用 `%v` 打印项目（之前讨论过打印动词，3.5；我们引入了自定义类型和方法，5.5；更多覆盖请见第 6 章）。

```go
products := []*Product
```

在这里我们创建了一个指向指针的切片（`[]*Product`），并立即用三个指针初始化了切片。Go 足够聪明，可以意识到 `*Product` 需要指针。我们写的是 `products := []*Product{"Spanner", 3.99}, {"Wrench", 4.49}, {"Screwdriver", 5.99}`（回想 4.1，可以使用 `&Type` 语法创建类型的新值并立即获取其指针）。

156

集合类型

如果我们没有定义 `String()` 方法，`%v` 动词（由 `fmt.Println` 等类似函数隐式使用）将仅仅打印指针地址而不是项目本身。注意，`Product.String()` 方法接收的是 `Product` 值而不是 `*Product`——这是一个问题，尽管 Go 足够聪明可以解引用指针以使其工作 值。我们之前注意到 `for range` 循环不能用于修改它所遍历的项。然而，在每次迭代中，`product` 变量被赋值 `Product` 的拷贝；这是一个指向 `products` 切片中对应 `Product` 的指针，尽管我们应用的修改是 `Product` 值。

### 4.2.3. 修改切片

如果需要向切片追加内容，可以使用内置的 `append()` 函数。该函数接收要追加的切片和一个或多个单独项。如果我们想向切片追加一个切片，必须使用 `...`（省略号）运算符让 Go 将要添加的切片作为单独值传递。要追加的值必须与切片的值类型相同。在字符串的情况下，可以使用省略号语法将字节追加到切片。

```
s := []string{"A", "B", "C", "D", "E", "F", "G"}
t := []string{"H", "I", "M", "N"}
u := []string{"m", "n", " "r"}
s = append(s, "h","i","j") // 追加单独的值
s = append(s, t...) // 追加切片的所有值
s = append(s, u[2:5]) // 追加子切片
b := []byte{'U', 'V'}
letters := "wxy" // 将字符串的字节追加到切片
fmt.Printf("%v\n%s\n", s, b)
```

```
[A B C D E F G h i j]
UVwxy
```

内置的 `append()` 函数接收一个切片和一个多个值，并返回一个（可能是新的）切片，该切片包含原始切片的内容，加上给定的值作为其最后一个项或项。如果原始切片的容量对于新项是够的（即其长度加上新项的数量在容量范围内），

> * 编译器执行以下操作：每当创建一个操作值的方法时（例如调用 `Method()`），就会创建一个具有相同名称和签名且具有指针接收者的包装方法——效果上是，`func (value *Type) Method() { return (*value).Method() }`

`append()` 将新值或多个值放在末尾，并返回长度增加了添加数量的原始切片。如果原始切片没有足够的容量，`append()` 函数在底层创建一个新切片，并将原始切片的项以及末尾的新值或值拷贝其中，然后返回新切片——因此需要将 `append()` 的返回值赋值给原始切片变量。

有时发生在我们在切片的开头或中间插入项，而不仅仅是之后。这里有一些示例，自定义的 `InsertStringSliceCopy()` 接收要插入的切片、要插入的切片以及应该插入的索引位置。

```go
s := []string{"M", "N", "O", "P", "Q", "R"}
x := InsertStringSliceCopy(s, []string{"a", "b", "c"}, 0) // 在开头
y := InsertStringSliceCopy(s, []string{"x", "y"}, 3) // 在中间
z := InsertStringSliceCopy(s, []string{"z"}, len(s)) // 在末尾
fmt.Printf("%v\n%v\n%v\n%v\n", s, x, y, z)
```

```
[M N O P Q R]
[a b c N O P Q R]
[M N x y P Q R]
[M N O Q R]
```

自定义的 `InsertStringSliceCopy()` 创建一个新的切片（这就是为什么代码段中的切片 `s` 未改变），利用内置的 `copy()` 函数将它接收的第一个切片拷贝，并拷贝到第二个切片中。

```go
func InsertStringSliceCopy(slice []string, insertion []string, index int) []string {
	result := make([]string, len(slice)+len(insertion))
	at := copy(result, slice[:index])
	at += copy(result[at:], insertion)
	copy(result[at:], slice[index:])
	return result
}
```

# 158 第 4 章 集合类型

传递给内置 `copy()` 函数的切片必须是相同类型——除非第一个（目标）切片是 `[]byte`，第二个（源）参数可以是 `[]byte` 或 `string`。如果源是字符串，则它的字节将被复制到第一个参数中。（这方面的示例在第 6 章，➤ 268 中所示。）

在 `customInsertSliceCopy()` 中，我们首先创建一个新的切片（`result`），其长度足够容纳从传入的两个切片中的项。然后，我们将第一个切片的子切片（`slice[:index]`）拷贝到 `result` 切片中。我们将插入切片拷贝到 `result` 切片中，从我们到达的位置（`at`）开始。然后我们将第一个切片的剩余部分（`slice[index:]`）拷贝到 `result` 切片的下一个我们到达的位置（`at`）。最后一次拷贝我们忽略了 `copy()` 函数的返回值，因为我们不需要它。最后，我们返回 `result` 切片。

如果 `index` 为 0，则第一个拷贝语句中的 `slice[:index]` 将是 `slice[:0]`（一个空切片，所以没有进行拷贝）。同样，如果 `index` 大于或等于切片的长度，则最后一个拷贝语句中的实际上将是 `slice[len(slice):]`（即一个空切片），因此同样没有进行拷贝。

这里有一个函数的行为与 `InsertStringSlice-Copy()` 函数几乎相同，但代码短得多且简单。区别在于 `InsertStringSlice()` 函数会改变原始切片（可能还有被插入的切片），而 `InsertStringSliceCopy()` 函数则不会。

```
func InsertStringSlice(slice []string, insertion []string, index int) []string {
	return append(slice[:index], append(insertion, slice[index:]...)...)
}
```

`InsertStringSlice()` 函数将原始切片从 `index` 位置开始的结尾追加到插入切片的末尾，然后将结果切片追加到原始切片 `index` 位置的末尾。返回的切片是应用了插入后的原始切片。（记得 `append()` 接收一个切片和更多的切片，因此我们使用省略号语法将切片转换为其单独的值——在这个示例中，我们必须这样做。）

可以使用 Go 的切片语法从切片的开头和结尾移除项，但从中间移除可能需要一点。我们将首先查看如何从切片的开头、结尾和中间进行就地删除。然后我们将查看如何获取一个删除了项的切片的副本，而原切片保持不变。

```
s := []string{"A", "B", "C", "D", "E", "F", "G"}
s = s[2:] // 从前面移除 s[:2]
fmt.Println(s)
```

```
[C E F G]
```

## 4.2. 数组与切片

通过重新切片可以轻松地从切片的开头移除项。

```
s := []string("A", "B", "C", "D", "E", "F", "G")
s := s[4:] // 从结尾移除 s[4:]
fmt.Println(s)
```

从切片的结尾移除项也是通过重新切片实现的，与从开头开始相同。

```
s := []string("A", "B", "C", "D", "E", "F", "G")
s := append(s[:1], s[5:]...) // 从中间移除 s[1:5]
fmt.Println(s)
```

从切片的中间检索项是简单的——例如，为了获取切片 `s` 的中间三个项，我们将使用表达式 `s[2:5]`。但从切片的中间移除项稍微有点复杂。在这里我们使用 `append()` 函数执行移除，将我们想要的部分之后的的 `s` 子切片添加到我们想要的部分之前的的 `s` 子切片中，并将结果切片赋值回 `s`。显然，使用 `append()` 并赋值回原始切片来移除项会改变原数据。这里有一些示例，说明自定义的 `RemoveSliceCopy()` 函数返回它所收到的切片的副本，并且带有末尾的项。

```
s := []string("A", "B", "C", "D", "E", "F", "G")
x := RemoveSliceCopy(s, 0, 2) // 从前面移除 s[:2]
s := RemoveSliceCopy(s, 1, 5) // 从中间移除 s[1:5]
z := RemoveSliceCopy(s, 4, len(s)) // 从结尾移除 s[4:]
fmt.Printf("%v\n%v\n%v\n", s, x, z)
```

```
A B C D E F G
C E F
A D
```

在 `RemoveSliceCopy()` 函数中，我们首先创建一个新的切片（`result`），其长度足够容纳它将包含的项。然后我们将切片的起始位置部分（`slice[:start]`）拷贝到 `result` 切片中。接下来，我们将切片的结尾位置部分（`slice[end:]`）拷贝到 `result` 切片中我们到达的位置（`at`）。最后，我们返回结果。

也可以创建一个更简单的 `RemoveSlice()` 函数，它作用于所收到的切片，而不是创建副本。

```go
func RemoveSlice(slice []string, start, end int) []string {
	result := make([]string, len(slice)-(end-start))
	at := copy(result, slice[start:end])
	copy(result[at:], slice[end:])
	return result
}
```

这是内置 `append()` 函数所使用的从中间删除的泛化。返回的切片是删除了从起始位置到（但不包括）结束位置之间项的原始切片。

### 4.2.4. 切片的排序与搜索

标准库的 `sort` 包提供了用于对 `int`、`float64` 和 `string` 切片进行排序、检查切片是否已排序，以及在已排序切片中使用二分查找查找项的函数。还有可以易于用于自定义数据的、二分查找算法的 `sort.Sort()` 和 `sort.Search()` 函数（见表 4.2）。Go 对数字的排序并没有惊喜，正如我们在之前的章节中所看到的（73 ◀）。字符串完全根据表示它们的字节进行排序的，例如，字符串排序是区分大小写的。这里有一些字符串排序的示例以及它们的结果。

```
files := []string{"Test.conf", "util.go", "Makefile", "misc.go", "main.go"}
fmt.Printf("Unsorted: %q\n", files)
sort.Strings(files) // 标准库排序函数
fmt.Printf("Underlying bytes: %q\n", files)
SortFoldedStrings(files) // 自定义排序函数
fmt.Printf("Case insensitive: %q\n", files)
```

Unsorted: ["Test.conf", "util.go", "Makefile", "misc.go", "main.go"]

Underlying bytes: ["Test.conf", "util.go", "Makefile", "misc.go", "main.go"]

Case insensitive: ["main.go", "Makefile", "misc.go", "Test.conf", "util.go"]

```

表 4.2 Sort 包的函数

| 语法 | 描述/结果 |
|---|---|
| sort.Float64s(fs) | 对 []float64 类型的切片进行升序排序 |
| sort.Float64AreSorted(fs) | 如果 []float64 类型的切片已排序，则返回 true |
| sort.Ints(is) | 对 []int 类型的切片进行升序排序 |
| sort.IntsAreSorted(is) | 如果 []int 类型的切片已排序，则返回 true |
| sort.IsSorted(d) | 如果 sort.Interface 类型的 d 已排序，则返回 true |
| sort.Search(size, fn) | 在长度为 size 的有序切片中返回函数 (int) bool 返回 true 的索引位置（见正文） |
| sort.SearchFloat64s(fs, f) | 在排序的 []float64 类型切片 fs 中返回 float64 类型 f 的索引位置 |
| sort.SearchInts(is, i) | 在排序的 []int 类型切片 is 中返回 int 类型 i 的索引位置 |
| sort.SearchStrings(ss, s) | 在排序的 []string 类型切片 ss 中返回 string 类型 s 的索引位置 |
| sort.Sort(d) | 对 sort.Interface 类型的 d 进行排序（见） |
| sort.Strings(ss) | 对 []string 类型的切片进行升序排序 |
| sort.StringsAreSorted(ss) | 如果 []string 类型的切片已排序，则返回 true |

```

func (slice FoldedStrings) Less(i, j int) bool {

    return strings.ToLower(slice[i]) < strings.ToLower(slice[j])

}

func (slice FoldedStrings) Swap(i, j int) {

    slice[i], slice[j] = slice[j], slice[i]

}

```

`FoldedStrings()` 函数简单地调用标准库的 `sort.Sort()` 函数来完成工作——它已经使用 Go 的标准转换语法（非常廉价地）将给定的 [string](#) 转换成了 `FoldedStrings` 类型。通常情况下，每当我们创建一个基于内置类型的自定义类型时，我们都可以通过这种转换方式将该内置类型的值提升为自定义类型（自定义类型在第 6 章中介绍）。

`FoldedStrings` 提供了满足 `sort.Interface` 所需的三个方法。所有方法都是简单而易懂的；通过在 `Less()` 方法中使用 `strings.ToLower()` 函数实现了不区分大小写的比较。（如果如果我们想按降序排序，只需将 `Less()` 方法中的小于 `<` 运算符改为大于 `>`即可。）

`SortedStrings()` 函数对于 7 位 ASCII（即英文字符串）来说完全足够，但正如我们在上一章中讨论的那样，它不太可能为非英语语言提供满意的排序（§3.2, 46 ◀）。正确考虑到非英语语言的字符串排序并不是一项简单的任务。这在《Unicode 排序算法》文档 (unicode.org/reports/t10) 中有详细解释。

如果我们想对切片（slice）进行切片以找到某个特定项的位置（如果它包含该项），我们可以使用 `for range` 循环轻松实现。

```
files := []string{"Test.conf", "util.go", "Makefile", "misc.go", "main.go"}

target := "Makefile"
