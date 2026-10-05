

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
for i, file := range files {
    if file == target {
        fmt.Printf("found %s at files[%d]\n", files[i], i)
        break
    }
}
found "Makefile" at files[2]
```

对于未排序的数据，使用这种简单的线性搜索是唯一的选择，并且对于小型切片（几数百项）来说没问题。但对于较大的切片——特别是当我们反复执行搜索时——线性搜索是非常低效的，平均每次需要比较一半的项。

## 4.2. 数组与切片

Go 提供了一个 `sort.Search()` 方法，它使用了二分查找算法：这每次需要比较 `log2(n)` 个项（其中 n 是项的数量）。对比一下，对 100,000 项进行线性搜索平均需要 500,000 次比较，最坏情况需要 1,000,000 次比较；而二分查找即使在最坏情况下也只需要 20 次比较。

```
sort.Strings(files)
fmt.Printf("%s\n", files)
t := sort.Search(len(files))
func(i int) bool { return files[i] >= target }
if i < len(files) && files[i] == target {
	fmt.Printf("found %s at files[%d]\n", files[i], i)
}

"Makefile" "Test.conf" "main.go" "misc.go" "util.go"
found "Makefile" at files[0]
```

`sort.Search()` 函数接收两个参数：要处理的切片的长度，以及一个函数，该函数将已排序切片中的项与目标项进行比较（对于升序排序的切片使用 `>=` 运算符，对于降序排序的切片使用 `<=` 运算符）。该函数必须是一个闭包（closure），也就是说它必须在要处理的切片的作用域内创建，因为它必须捕获切片作为其状态的一部分。（闭包在 5.6.3 中介绍，► 225.）`sort.Search()` 返回一个 `int`；只有当它小于切片的长度且索引位置上的项与目标匹配时，我们才能确定找到了寻找的项。

这里有一个变体，它对一个已经区分大小写排序的 `[]string` 进行排序，并使用小写的目标字符串。

```
sort := "makefile"
SortFoldedStrings(files)
fmt.Printf("%q\n", files)
caseInsensitiveCompare := func(i int) bool {
	return strings.ToLower(files[i]) >= strings.ToLower(target)
}
if i < len(files) && strings.EqualFold(files[i], target) {
	fmt.Printf("found %s at files[%d]\n", files[i], i)
}

"main.go" "Makefile" "misc.go" "Test.conf" "util.go"
found "Makefile" at files[1]
```

在这里，我们在调用 `sort.Search()` 函数之外创建了比较函数。但注意，就像上一个例子一样，

## 第 4 章 集合类型

比较函数必须是要处理的切片作用域内的闭包。我们本可以使用代码 `strings.ToLower(files[i]) == target` 来进行比较，但我们使用了更方便的 `strings.EqualFold()` 函数，它可以不区分大小写地比较两个字符串。

Go 的切片是极其方便、强大且多功能的数据结构，很难想象任何非复杂的 Go 程序不大量使用它们。我们将在本章的稍后部分看到它们的实际应用（$4.4, 171.）

虽然切片可以涵盖大多数数据结构用例，但在某些情况下，我们需要 map。

### 4.3. Map（映射）

Go 的 map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

map 是键值对的集合，键是唯一的，map 存储在内存中。

