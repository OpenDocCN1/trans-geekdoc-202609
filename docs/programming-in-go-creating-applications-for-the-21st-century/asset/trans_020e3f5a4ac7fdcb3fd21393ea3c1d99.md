

# 304
第 6 章 面向对象编程

omap.Map.Find() 方法返回给定键对应的项的值，返回类型为 `interface{}`；如果不存在该项，则返回 true、nil 和 false。omap.Map.Delete() 方法删除给定键的项并返回 true——如果不存在该项，则什么都不做并返回 false。

如果我们想存储自定义类型的键，可以通过使用 `tomap.Map.New()` 函数创建 Map 并为其提供一个合适的 `less` 方法来实现。
例如，这里是一个非常简单的自定义类型实现。

```go
type Point struct{X, Y int}
func (point Point) String() string {
	return fmt.Sprintf("{%d, %d}", point.X, point.Y)
}
```

现在我们将看到如何创建一个有序 map，该 map 将 *Point 作为键（key）*，并将到原点的距离作为值（value）*。

在下面的代码段中，我们创建了一个空 map，它包含一个用于比较 *Point 键* 的 `less` 函数。然后，我们创建了一个 *Points* 切片并根据这些点填充了 map。最后，我们使用 omap.Map.Do() 方法按照键的顺序打印 map 的键和值。

```go
distanceForPoint := omap.Map.New(func(a, b interface{}) bool {
	alpha, beta := a.(*Point), b.(*Point)
	if a.X != b.X {
		return alpha.Y < beta.Y
	}
})
points := []*Point{{3, 1}, {1, 2}, {2, 3}, {1, 3}, {3, 2}, {2, 1}, {2, 2}}
for _, point := range points {
	distance := math.Hypot(float64(point.X), float64(point.Y))
	distanceForPoint.Insert(point, distance)
}
distanceForPoint.Do(func(key, value interface{}) {
	fmt.Printf("%v -> %.2v\n", key, value)
})
```

- (1, 2) -> 2.2
- (1, 3) -> 3.2
- (2, 1) -> 2.2
- (2, 2) -> 2.8
- (2, 3) -> 3.6
- (3, 1) -> 3.2
- (3, 2) -> 3.6

## 6.5. 示例

尽管如此，我们仍然可以在 distancePoint map 上使用有序 map 的 `Delete()`、`Find()` 和 `Len()` 方法，其方式与对 wordFor map 的完全相同，但前两个方法使用的是 *Point 键*（因为 `less` 函数是基于 *Points* 而非 Points 运行的）。

现在我们已经看到了有序 map，将回顾它的实现。我们不会涵盖 `Delete()` 的辅助方法和函数，因为其中一些非常复杂，涵盖它们并不会增加我们对 Go 编程的理解。（当然，所有这些函数都在书的源码中，位于 `omap/emap.go` 文件中）。我们将开始查看用于实现有序 map 的两个类型（Map 和 node），然后是构造函数。接着，我们将查看 Map 的方法以及一些将更复杂处理传递给辅助函数的方法。正如 Go 编程中常见的，大多数方法都非常

```go
type Map struct {
  *node
  less func(interface{}, interface{}) bool
  length int
}

type node struct {
  key, value interface{}
  red bool
  left, right *node
}
```

有序 map 是通过两个自定义类型实现的。第一个结构体类型是 `Map` 结构体，它持有左倾红黑树的根节点、一个用于比较键的 `less` 函数，以及一个存储 map 中项数量的 `length`。Map 的字段都是导出的，且 `less` 函数的零值为 `nil`，因此直接创建变量将产生一个无效的 Map。文档解释了这一点，并指导用户使用 omap 的构造函数之一来创建有效的 Map。第二个结构体类型是 `node` 结构体，它表示单个的键值项。除了 `key` 和 `value` 字段外，`node` 结构体还三个三个实现树所需的字段。类型为 `bool` 的 `red` 字段用于标识节点是“红色”（true）还是“黑色”（false）——这在树的部分进行旋转以保持其平衡时使用。类型为 `*node` 的 `left` 和 `right` 字段持有指向节点左子树和右子树的指针（可以是 `nil`）。

# 308
6. 面向对象编程

omap 包提供了几个构造函数；在这里，我们将查看通用的 omap.New() 函数以及另外几个。

```go
func New(less func(interface{}, interface{}) bool) *Map {
	return &Map{less: less}
}
```

这是该包的通用函数，用于为任何内置或自定义类型创建有序 map，只要我们能提供合适的 `less` 函数即可。

```go
func NewFoldKey() *Map {
	return &Map{less: func(a, b interface{}) bool {
		return strings.ToLower(a.(string)) < strings.ToLower(b.(string))
	}}
}
```

这个构造函数创建一个具有字符串键的有序 map，这些键比较是不区分大小写的。

```go
func NewIntKey() *Map {
	return &Map{less: func(a, b interface{}) bool {
		return a.(int) < b.(int)
	}}
}
```

omap 包还有 `NewStringKey()` 函数，用于创建区分大小写的字符串键有序 map（其实现与 `NewFoldKey()` 几乎相同，没有 `strings.ToLower()` 调用），以及 `NewFloat64Key()` 函数，它与 `NewIntKey()` 相似，使用的是 `float64` 代替 `int`。

```go
func (m *Map) Insert(key, value interface{}) (inserted bool) {
	m.root, inserted = m.insert(m.root, key, value)
	m.root.red = false
	if inserted {
		m.length++
	}
	return inserted
}
```

该方法在结构上是 Go 方法的典型，因为它将大部分工作传递给了一个未导出的 `insert()` 方法。树的根可能会因为插入而改变，要么因为树是空的现在包含了一个必须成为根节点的节点，要么因为插入导致了保持树平衡的旋转并涉及根节点。

`insert()` 方法返回树的根以及一个布尔值。如果布尔值为 true，则表示插入了新项，在这种情况下我们增加 map 的长度。如果布尔值为 false，则意味着给定键已存在于 map 中，因此所做的只是用给定的值替换该项当前的值，map 的长度保持不变。我们不会解释为什么节点变为红色或黑色或为什么要进行旋转。这些问题在 Robert Sedgewwick 的论文中有详细解释——参见脚注；

```go
func (m *Map) insert(root *node, key, value interface{}) (*node, bool) {
  inserted := false
  if root == nil // 如果键在树中，它本该在这里
    return &node{key: key, value: value, red: true}, true
  if isRed(root.left) && isRed(root.right) {
    colorFlip(root)
  }
  if m.less(key, root.key) {
    root.left, inserted = m.insert(root.left, key, value)
  } else if m.less(root.key, key) {
    root.right, inserted = m.insert(root.right, key, value)
  } else { // 键已经在树中，所以只需替换其值
    root.value = value
  }
  if isRed(root.right) && !isRed(root.left) {
    root = rotateLeft(root)
  }
  if isRed(root.left) && isRed(root.left.left) {
    root = rotateRight(root)
  }
  return root, inserted
}
```

