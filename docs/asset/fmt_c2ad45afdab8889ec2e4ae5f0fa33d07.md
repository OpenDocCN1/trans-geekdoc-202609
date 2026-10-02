
到目前为止，我们讨论了数组，但 Go 语言中的数组还有几点未提及。由于数组是固定大小的，我们无法在运行时添加任何元素。我们必须在编译时定义数组的大小。这增加了时间复杂度。对于数组，我们不允许使用变量来定义其数组大小。如果像下面所示声明数组，编译器将给出`"invalid array length size"`的错误：

```go
func main() {
    var size int = 4
    arrval := [size]int{1, 4, 7, 2}
    fmt.Println("sum of array elements is:", arrval)
}
```

## 切片简介

为了解决我们在数组上面临的问题，Go 提供了更强大的动态数据类型——切片。切片是数组的一个片段，包含了一些具有相同数据类型的元素。切片的类型取决于其所包含的元素，而不是取决于其大小。

## 声明切片

和数组一样，切片是可以索引的，且声明方式与数组相同，但不需要指定大小：

语法：`var s []int`

它声明了一个整数类型的空切片，因为切片如果没有引用数组，则被视为 `nil`。

## 初始化切片

切片可以使用切片字面量进行初始化，就像初始化数组时不指定大小一样。由于切片是数组的引用，在使用字面量创建切片时，它会先创建一个数组，然后返回该切片的引用。基本上，切片不包含任何数据。数据存储在数组中，而该数组的引用被定义为切片。

示例：

```go
func main() {
    var slice1 []int = []int{1, 2, 3, 5}
    slice2 := []int{1, 2, 3, 5}
    fmt.Println("slice with literal", slice1) // slice with literal [1 2 3 5]
    fmt.Println("slice short hand declaration", slice2) // slice short hand declaration [1 2 3 5]
}
```

### 从数组创建切片

切片是数组的一个片段。我们也可以从数组创建切片。要从数组创建切片，我们需要指定两个索引：`low` 和 `high`，其中 `low` 表示数组的起始索引，`high` 表示最后一个索引的下一个位置。这意味着我们获取从索引 `low` 到 `high-1` 的所有数组元素。在声明切片时，这两个索引用冒号隔开。默认情况下，`low` 为索引 0，`high` 为数组的长度。如果未指定这些索引，编译器将假设它们的默认值以创建切片。

语法：

`var name_of_slice []type_of_slice := name_of_array[low:high]`

示例：

```go
func main() {
    var arrayval [10]int = [10]int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
    slice1 := arrayval[3:7]
    slice2 := arrayval[:6]
    slice3 := arrayval[5:]
    slice4 := arrayval[:]

    fmt.Println("slice from array:", slice1)
    fmt.Println("slice with default low indice:", slice2)
    fmt.Println("slice with default high indice:", slice3)
    fmt.Println("slice with default low and high indice:", slice4)
}
```

输出：

```
slice from array: [4 5 6 7]
slice with default low indice: [1 2 3 4 5 6]
slice with default high indice: [6 7 8 9 10]
slice with default low and high indice: [1 2 3 4 5 6 7 8 9 10]
```

### 从切片创建切片

我们可以像从数组创建切片一样，从现有的切片创建切片。重新切片不会复制数据，但会创建一个同样引用原始数组的新切片。

在前面的示例中，切片包含了从索引 2 到 4 的元素（3 个元素）。因此，切片的长度为 3。切片可以扩展到数组的最大索引，在这里是 9。因此，切片的容量是索引从 2 到 9 的元素个数；在这里是 8。

切片的扩展不能超出其容量。此外，切片不能在零以下进行切片。

示例：

```go
func main() {
    var arrayval [10] int = [10] int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
    slice1 := arrayval[2:5]
    fmt.Println("length of slice", len(slice1))
    // length of slice 3
    fmt.Println("capacity of slice", cap(slice1))
    // capacity of slice 8
}
```

### 使用 `make` 函数创建切片

Go 提供了一个用于创建空切片的内置函数。空切片引用一个空数组。要创建此类切片，必须在声明切片时定义其大小。要创建一个非零长度的空切片，我们按照以下方式声明切片：

`name_of_slice := make([], type_of_slice, length_of_slice, capacity_of_slice)`

`make` 函数创建一个指定类型的数组并将其引用赋值给切片。在这里，切片的容量是可选的。默认情况下，考虑的切片大小是其容量。

`s := make([]int, 5, 10)`

这创建了一个大小为十的整数类型数组，并将引用赋值给切片 `s` 直到索引 5。

示例：

```go
func main() {
    slice1 := make([]int, 2, 4)
    fmt.Println("length of slice", len(slice1)) // length of slice 2
    fmt.Println("capacity of slice", cap(slice1)) // capacity of slice 4
    fmt.Println("value of slice", slice1) // value of slice [0 0]

    slice1[0] = 194
    slice1[1] = 18
    fmt.Println("value of slice", slice1) // value of slice [194 18]

    slice1[2] = 78 // error as length of slice is 2
}
```

在前面为索引 2 赋值的示例中，它会退出，因为我们定义了它的长度为 2。之后，我们可以通过追加更多元素将切片扩展到索引 3，因为它的容量是 4。

### 扩展切片

在 Go 语言中，我们可以扩展切片的容量。增加切片容量有一个简单的过程。要增加容量，创建一个新的切片（必须比旧切片大），并将切片的内容复制到新切片。现在，新切片的容量将大于旧切片。然后将此新切片赋值给旧切片。

示例：

```go
func main() {
    slice1 := []int{12, 65, 34, 78, 23, 67}
    fmt.Println("capacity of slice1:", cap(slice1))
    slice2 := make([]int, len(slice1), (cap(slice1)+1)*2)
    for i := range slice1 {
        slice2[i] = slice1[i]
    }
    slice1 = slice2
    fmt.Println("capacity of slice1:", cap(slice1))
}
```

输出：

```
capacity of slice1: 6
capacity of slice1: 14
```

在 Go 中，标准库 `slices` 包中的 `slices.Grow` 函数提供了一个简单的替代方案。

### 二维切片

像数组一样，我们也可以创建二维切片。二维切片可以定义为切片的切片。我们可以像声明数组一样的方式声明二维切片，而无需定义它们的大小：

```go
slice1 := [][]int{
    []int{1, 2},
    []int{3, 4},
    []int{5, 6},
}
```

使用 `make` 函数声明二维切片时，我们将行数定义为切片的长度。在二维切片中，内部切片的长度可以根据需要进行变化。对于未初始化的行或元素，它将取默认值。这里有一个解释二维切片的示例。

示例：

```go
func main() {
    slice1 := [][]int{
        []int{1, 2, 78, 54},
        []int{0, 3, 4},
        []int{5, 6},
    }
    fmt.Println("slice1", slice1) // slice1 [[1 2 78 54] [0 3 4] [5 6]]

    slice2 := make([][]string, 4)
    slice2[0] = []string{"College", "School"}
    slice2[1] = []string{"University", "Institute"}
    fmt.Println("slice2 using make function:", slice2)
    // slice2 using make function: [[College School] [University Institute] [] []]
}
```

### 切片函数

创建切片后，是时候以各种方式使用切片了。切片比数组更丰富，因为我们可以执行多种类型的操作。

从这个例子可以看出，`copy` 函数并没有为目标切片添加任何新值。如果该索引同时存在于两个切片，它只是修改了该索引处的元素。

### 排序切片

在 Golang 中，我们有一个 `sort` 包，它提供了多种排序方法来对 `int`、`float64` 或 `string` 类型的切片进行排序。这些排序方法始终按升序对切片进行排序。

示例：

```go
package main

import (
	"fmt"
	"sort"
)

func main() {
	slice1 := []int{23, 0, 105, 58}
	slice2 := []string{"Ram", "Akansha", "Mayank"}
	slice3 := []float64{75.84, 0.007, 85.62, 0.74637}

	fmt.Println("slice1 before sorting:", slice1)
	sort.Ints(slice1)
	fmt.Println("slice1 after sorting:", slice1)
	fmt.Println("slice1 before sorting:", slice2)
	sort.Strings(slice2)
	fmt.Println("slice1 after sorting:", slice2)
	fmt.Println("slice1 before sorting:", slice3)
	sort.Float64s(slice3)
	fmt.Println("slice1 after sorting:", slice3)
}
```

输出：

```text
slice1 before sorting: [23 0 105 58]
slice1 after sorting: [0 23 58 105]
slice1 before sorting: [Ram Akansha Mayank] slice1 after sorting: [Akansha Mayank Ram]
slice1 before sorting: [75.84 0.007 85.62 0.74637]
slice1 after sorting: [0.007 0.74637 75.84 85.62]
```

标准库中的 `slices.SortFunc` 函数允许使用比较器对切片进行自定义排序，为标准的 `sort` 包提供了一种替代方案。

### 比较切片

如果两个切片的类型相同且包含相同的元素，则认为它们是相等的。Golang 提供了 `DeepEqual` 函数来比较切片是否相等。我们可以通过使用 `reflect` 包来访问此函数。

示例：

```go
package main

import (
	"fmt"
	"reflect"
)

func main() {
	slice1 := []int{23, 0, 105, 0}
	slice2 := []string{"Ram", "Akansha", "Mayank"}
	slice3 := []float64{23, 0, 105, 0}
	slice4 := make([]int, 4)
	slice4[0] = 23
	slice4[1] = 0
	slice4[2] = 105

	fmt.Println("Is slice1 equal to slice2:", reflect.DeepEqual(slice1, slice2))
	fmt.Println("Is slice1 equal to slice3:", reflect.DeepEqual(slice1, slice3))
	fmt.Println("Is slice1 equal to slice4:", reflect.DeepEqual(slice1, slice4))
}
```

输出：

```text
Is slice1 equal to slice2: false Is slice1 equal to slice3: false Is slice1 equal to slice4: true
```

### 在切片中搜索

在 Golang 中，我们可以搜索特定元素是否存在于切片中。Go 提供了一个 `search` 函数，它可以找到一个元素并返回其在特定的整数、浮点数或字符串切片中的位置。该搜索函数对升序排列的切片执行二分查找。如果在排序后的切片中找到了该元素，搜索函数将返回该索引；如果没有找到，它将返回该元素应该插入到切片中的索引。

示例：
