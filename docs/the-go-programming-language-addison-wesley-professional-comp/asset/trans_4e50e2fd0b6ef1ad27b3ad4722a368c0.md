
对此主题存在无数种病态变体。执行完这条语句后：

```
pT := uintptr(unsafe.Pointer(new(T))) // NOTE: wrong!
```

不存在任何指针引用 `new` 创建的变量，因此垃圾收集器有权在该语句完成后回收其存储空间，此后 `pT` 包含的地址是该变量曾经所在的位置，但该变量已不复存在。

目前没有任何 Go 实现使用移动式垃圾收集器（尽管未来的实现可能会），但这并非掉以轻心的理由：当前版本的 Go 确实会在内存中移动*某些*变量。回顾 [第 5.2 节](#part0044.html#id-recursion)，goroutine 栈会根据需要增长。发生这种情况时，旧栈上的所有变量可能会被重定位到一个新的、更大的栈上，因此我们不能依赖变量地址的数值在其生命周期内保持不变。

在撰写本文时，关于 Go 程序员在将 `unsafe.Pointer` 转换为 `uintptr` 后可以依赖什么，几乎没有明确的指导（参见 Go issue 7192），因此我们强烈建议你假设最低限度的保证。将所有 `uintptr` 值视为包含变量的*旧*地址，并将 `unsafe.Pointer` 转换为 `uintptr` 与使用该 `uintptr` 之间的操作数量降到最低。在上面的第一个例子中，三个操作——转换为 `uintptr`、加上字段偏移量、转换回去——全都出现在单个表达式中。

当调用返回 `uintptr` 的库函数时，例如下面来自 `reflect` 包的函数，结果应立即转换为 `unsafe.Pointer`，以确保它继续指向同一个变量。

```
package reflect

func (Value) Pointer() uintptr
func (Value) UnsafeAddr() uintptr
func (Value) InterfaceData() [2]uintptr // (index 1)
```

## 13.3 示例：深度相等

`reflect` 包中的 `DeepEqual` 函数报告两个值是否“深度”相等。`DeepEqual` 使用内置的 `==` 运算符比较基本值；对于复合值，它会递归遍历它们，比较对应的元素。因为它适用于任意一对值，甚至包括那些无法用 `==` 比较的值，所以它在测试中被广泛使用。以下测试使用 `DeepEqual` 来比较两个 `[]string` 值：

```
func TestSplit(t *testing.T) {
    got := strings.Split("a:b:c", ":")
    want := []string{"a", "b", "c"}
    if !reflect.DeepEqual(got, want) { /* ... */ }
}
```

虽然 `DeepEqual` 很方便，但其区分标准看似随意。例如，它不认为 nil 映射等于非 nil 的空映射，也不认为 nil 切片等于非 nil 的空切片：

```
var a, b []string = nil, []string{}
fmt.Println(reflect.DeepEqual(a, b)) // "false"

var c, d map[string]int = nil, make(map[string]int)
fmt.Println(reflect.DeepEqual(c, d)) // "false"
```

在本节中，我们将定义一个函数 `Equal` 来比较任意值。与 `DeepEqual` 一样，它基于元素比较切片和映射，但与 `DeepEqual` 不同，它认为 nil 切片（或映射）等于非 nil 的空切片（或映射）。对参数的基本递归可以用反射来完成，采用的方法类似于我们在 [第 12.3 节](#part0114.html#id-display) 中看到的 `Display` 程序。照例，我们为递归定义一个未导出的函数 `equal`。暂时不用担心 `seen` 参数。对于每一对待比较的值 `x` 和 `y`，`equal` 检查两者是否都有效（或都无效），并检查它们是否具有相同的类型。函数的结果定义为一组 switch case，用于比较两个相同类型的值。由于篇幅限制，我们省略了若干 case，因为到现在模式应该已经很熟悉了。

```
func equal(x, y reflect.Value, seen map[comparison]bool) bool {
    if !x.IsValid() || !y.IsValid() {
        return x.IsValid() == y.IsValid()
    }
    if x.Type() != y.Type() {
        return false
    }

    // ...cycle check omitted (shown later)...

    switch x.Kind() {
    case reflect.Bool:
        return x.Bool() == y.Bool()

    case reflect.String:
        return x.String() == y.String()

    // ...numeric cases omitted for brevity...

    case reflect.Chan, reflect.UnsafePointer, reflect.Func:
        return x.Pointer() == y.Pointer()

    case reflect.Ptr, reflect.Interface:
        return equal(x.Elem(), y.Elem(), seen)

    case reflect.Array, reflect.Slice:
        if x.Len() != y.Len() {
            return false
        }
        for i := 0; i < x.Len(); i++ {
            if !equal(x.Index(i), y.Index(i), seen) {
                return false
            }
        }
        return true

    // ...struct and map cases omitted for brevity...
    }
    panic("unreachable")
}
```

照例，我们不在 API 中暴露反射的使用，因此导出函数 `Equal` 必须对其参数调用 `reflect.ValueOf`：

```
// Equal reports whether x and y are deeply equal.
func Equal(x, y interface{}) bool {
    seen := make(map[comparison]bool)
    return equal(reflect.ValueOf(x), reflect.ValueOf(y), seen)
}

type comparison struct {
    x, y unsafe.Pointer
    t    reflect.Type
}
```

为确保算法即使对于循环数据结构也能终止，它必须记录已经比较过哪些变量对，并避免第二次比较它们。`Equal` 分配一个 `comparison` 结构体集合，每个结构体保存两个变量的地址（用 `unsafe.Pointer` 值表示）和比较的类型。除了地址之外，我们还需要记录类型，因为不同的变量可能具有相同的地址。例如，如果 `x` 和 `y` 都是数组，`x` 和 `x[0]` 具有相同的地址，`y` 和 `y[0]` 也是如此，区分我们是比较了 `x` 和 `y` 还是 `x[0]` 和 `y[0]` 非常重要。

一旦 `equal` 确定其参数具有相同类型，在执行 switch 之前，它会检查是否在比较两个已经见过的变量，如果是，则终止递归。

```
// cycle check
if x.CanAddr() && y.CanAddr() {
    xptr := unsafe.Pointer(x.UnsafeAddr())
    yptr := unsafe.Pointer(y.UnsafeAddr())
    if xptr == yptr {
        return true // identical references
    }
    c := comparison{xptr, yptr, x.Type()}
    if seen[c] {
        return true // already seen
    }
    seen[c] = true
}
```

这是我们的 `Equal` 函数的实际运行效果：

```
fmt.Println(Equal([]int{1, 2, 3}, []int{1, 2, 3}))        // "true"
fmt.Println(Equal([]string{"foo"}, []string{"bar"}))      // "false"
fmt.Println(Equal([]string(nil), []string{}))             // "true"
fmt.Println(Equal(map[string]int(nil), map[string]int{})) // "true"
```

它甚至适用于类似于导致 [第 12.3 节](#part0114.html#id-display) 中的 `Display` 函数陷入循环的循环输入：

```
// Circular linked lists a -> b -> a and c -> c.
type link struct {
    value string
    tail  *link
}
a, b, c := &link{value: "a"}, &link{value: "b"}, &link{value: "c"}
a.tail, b.tail, c.tail = b, a, c
fmt.Println(Equal(a, a)) // "true"
fmt.Println(Equal(b, b)) // "true"
fmt.Println(Equal(c, c)) // "true"
fmt.Println(Equal(a, b)) // "false"
fmt.Println(Equal(a, c)) // "false"
```
