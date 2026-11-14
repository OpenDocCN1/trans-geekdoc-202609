
## 切片操作

如果不需要保持顺序，我们只需将最后一个元素移到空缺处：

[点击此处查看代码图像](#part0134_split_028.html#id093pro02_r)

```go
func remove(slice []int, i int) []int {
    slice[i] = slice[len(slice)-1]
    return slice[:len(slice)-1]
}

func main() {
    s := []int{5, 6, 7, 8, 9}
    fmt.Println(remove(s, 2)) // "[5 6 9 8]"
}
```

### 练习 4.3

重写 `reverse` 使其使用数组指针代替切片。

### 练习 4.4

编写一个单遍历版本的 `rotate`。

### 练习 4.5

编写一个原地函数来消除 `[]string` 切片中的相邻重复元素。

### 练习 4.6

编写一个原地函数，将 UTF-8 编码的 `[]byte` 切片中每一段相邻的 Unicode 空白字符（参见 `unicode.IsSpace`）压缩为单个 ASCII 空格。

### 练习 4.7

修改 `reverse` 以原地反转表示 UTF-8 编码字符串的 `[]byte` 切片中的字符。你能不分配新内存来做到这一点吗？

## 4.3 映射

哈希表是所有数据结构中最精巧、用途最广泛的之一。它是一个无序的键/值对集合，其中所有键都是唯一的，并且无论哈希表多大，给定键关联的值都可以通过平均常数次键比较来检索、更新或删除。

在 Go 语言中，`map` 是对哈希表的引用，映射类型写作 `map[K]V`，其中 `K` 和 `V` 分别是其键和值的类型。给定映射中的所有键具有相同类型，所有值也具有相同类型，但键的类型不必与值的类型相同。键类型 `K` 必须支持使用 `==` 进行比较，以便映射能测试给定键是否等于其中已有的键。虽然浮点数可比较，但用 `==` 比较浮点数是个坏主意，正如我们在[第 3 章](#part0028.html#id-basicdatatypes)提到的，如果 `NaN` 是可能的值，那就更糟了。值类型 `V` 没有限制。

内置函数 `make` 可用于创建映射：

[点击此处查看代码图像](#part0134_split_029.html#id094pro01_r)

```go
ages := make(map[string]int) // mapping from strings to ints
```

我们也可以使用*映射字面量*来创建一个包含初始键/值对的新映射：

```go
ages := map[string]int{
    "alice":   31,
    "charlie": 34,
}
```

这等价于

```go
ages := make(map[string]int)
ages["alice"] = 31
ages["charlie"] = 34
```

因此，新空映射的另一种表达式是 `map[string]int{}`。

映射元素通过常规的下标符号访问：

[点击此处查看代码图像](#part0134_split_030.html#id094pro02_r)

```go
ages["alice"] = 32
fmt.Println(ages["alice"]) // "32"
```

并通过内置函数 `delete` 删除：

[点击此处查看代码图像](#part0134_split_031.html#id094pro03_r)

```go
delete(ages, "alice") // remove element ages["alice"]
```

即使元素不在映射中，所有这些操作也是安全的；使用不存在的键查找映射会返回其类型的零值，因此，例如，即使 `"bob"` 还不是映射中的键，以下代码也能正常工作，因为 `ages["bob"]` 的值将是 `0`。

[点击此处查看代码图像](#part0134_split_032.html#id094pro04_r)

```go
ages["bob"] = ages["bob"] + 1 // happy birthday!
```

简短赋值形式 `x += y` 和 `x++` 也适用于映射元素，所以我们可以将上述语句重写为

```go
ages["bob"] += 1
```

甚至可以更简洁地写为

```go
ages["bob"]++
```

但映射元素不是变量，我们不能取其地址：

[点击此处查看代码图像](#part0134_split_033.html#id094pro05_r)

```go
_ = &ages["bob"] // compile error: cannot take address of map element
```

我们无法取映射元素地址的一个原因是，映射扩容可能导致现有元素被重新哈希到新的存储位置，从而可能使地址失效。

要枚举映射中的所有键/值对，我们使用基于 `range` 的 `for` 循环，这类似于我们之前见过的用于切片的循环。循环的每次迭代都会将 `name` 和 `age` 变量设置为下一个键/值对：

[点击此处查看代码图像](#part0134_split_034.html#id095pro01_r)

```go
for name, age := range ages {
    fmt.Printf("%s\t%d\n", name, age)
}
```

映射的迭代顺序是未指定的，不同的实现可能使用不同的哈希函数，导致不同的顺序。实际上，顺序是随机的，每次执行都可能不同。这是有意为之；让序列变化有助于强制程序在不同实现中保持健壮。要按顺序枚举键/值对，我们必须显式地对键进行排序，例如，如果键是字符串，可使用 `sort` 包的 `Strings` 函数。这是一种常见模式：

[点击此处查看代码图像](#part0134_split_035.html#id095pro02_r)

```go
import "sort"

var names []string
for name := range ages {
    names = append(names, name)
}
sort.Strings(names)
for _, name := range names {
    fmt.Printf("%s\t%d\n", name, ages[name])
}
```

既然我们从一开始就知道 `names` 的最终大小，预先分配所需大小的数组会更高效。下面的语句创建了一个初始为空但有足够容量容纳 `ages` 映射所有键的切片：

[点击此处查看代码图像](#part0134_split_036.html#id095pro03_r)

```go
names := make([]string, 0, len(ages))
```

在上面的第一个 `range` 循环中，我们只需要 `ages` 映射的键，所以省略了第二个循环变量。在第二个循环中，我们只需要 `names` 切片的元素，所以使用空标识符 `_` 来忽略第一个变量（索引）。

映射类型的零值是 `nil`，即不引用任何哈希表。

[点击此处查看代码图像](#part0134_split_037.html#id095pro04_r)

```go
var ages map[string]int
fmt.Println(ages == nil)    // "true"
fmt.Println(len(ages) == 0) // "true"
```

大多数映射操作，包括查找、`delete`、`len` 和 `range` 循环，在 `nil` 映射引用上执行都是安全的，因为它的行为类似空映射。但向 `nil` 映射存入元素会导致 panic：

[点击此处查看代码图像](#part0134_split_038.html#id095pro05_r)

```go
ages["carol"] = 21 // panic: assignment to entry in nil map
```

必须先分配映射，才能向其中存入元素。

通过下标访问映射元素总会产生一个值。如果键存在于映射中，你会得到对应的值；如果不存在，你会得到元素类型的零值，正如我们在 `ages["bob"]` 中看到的那样。对许多用途来说这没问题，但有时你需要知道元素是否真正存在。例如，如果元素类型是数值类型，你可能需要区分不存在的元素和碰巧值为零的元素，可以使用如下测试：

[点击此处查看代码图像](#part0134_split_039.html#id096pro01_r)

```go
age, ok := ages["bob"]
if !ok { /* "bob" is not a key in this map; age == 0. */ }
```

你经常会看到这两条语句合并，如下所示：

```go
if age, ok := ages["bob"]; !ok { /* ... */ }
```

在这种上下文中对映射进行下标操作会产生两个值；第二个值是一个布尔值，报告元素是否存在。这个布尔变量通常叫作 `ok`，特别是当它立即用于 `if` 条件中时。

与切片一样，映射之间不能相互比较；唯一合法的比较是与 `nil` 比较。要测试两个映射是否包含相同的键和相同的关联值，我们必须编写一个循环：

[点击此处查看代码图像](#part0134_split_040.html#id096pro02_r)

```go
func equal(x, y map[string]int) bool {
    if len(x) != len(y) {
        return false
    }
    for k, xv := range x {
        if yv, ok := y[k]; !ok || yv != xv {
            return false
        }
    }
    return true
}
```
