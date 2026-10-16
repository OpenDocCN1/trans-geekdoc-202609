
```
}
}
```

当你在对同一个值进行多次比较时 *通常* 将其重构为 `switch` 会提高可读性并使代码更容易扩展。

如果传入的结构体的值是指针怎么办？

## 首先编写测试

添加此用例

```
{
    "Pointers to things",
    &Person{
        "Chris",
        Profile{33, "London"},
    },
    []string{"Chris", "London"},
},
```

## 尝试运行测试

```
=== RUN   TestWalk/Pointers_to_things
panic: reflect: call of reflect.Value.NumField on ptr Value
[recovered]
    panic: reflect: call of reflect.Value.NumField on ptr Value
```

## 编写足够代码使其通过

```
func walk(x interface{}, fn func(input string)) {
    val := reflect.ValueOf(x)

    if val.Kind() == reflect.Ptr {
        val = val.Elem()
    }
}
```

```
for i := 0; i < val.NumField(); i++ {
    field := val.Field(i)

    switch field.Kind() {
    case reflect.String:
        fn(field.String())
    case reflect.Struct:
        walk(field.Interface(), fn)
    }
}
}
```

无法在指针 `Value` 上使用 `NumField`，我们需要在使用 `Elem()` 提取底层值后才能执行此操作。

## 重构

让我们将从给定的 `interface{}` 中提取 `reflect.Value` 的职责封装到一个函数中。

```
func walk(x interface{}, fn func(input string)) {
    val := getValue(x)

    for i := 0; i < val.NumField(); i++ {
        field := val.Field(i)

        switch field.Kind() {
        case reflect.String:
            fn(field.String())
        case reflect.Struct:
            walk(field.Interface(), fn)
        }
    }
}
```

```
func getValue(x interface{}) reflect.Value {
    val := reflect.ValueOf(x)

    if val.Kind() == reflect.Ptr {
```

```
val = val.Elem()
}

return val
}
```

实际上这增加了更多代码，但我觉得抽象层级是合适的。

- 获取 x 的 reflect.Value 以便我可以检查它，我不在乎具体如何。
- 遍历字段，根据其类型执行所需的操作。

接下来，我们需要处理切片。

## 首先编写测试

```
{
"Slices",
[]Profile {
{33, "London"},
{34, "Reykjavík"},
},
[]string{"London", "Reykjavík"},
},
```

## 尝试运行测试

```
=== RUN TestWalk/Slices
panic: reflect: call of reflect.Value.NumField on slice Value
[recovered]
panic: reflect: call of reflect.Value.NumField on slice Value
```

## 编写最少量的代码让测试运行并检查失败的测试输出

我们目前的代码确实做了这一点，但表达得并不好。我们只是在开头检查它是否是一个切片（并返回以停止其余代码的执行），如果不是我们就假设它是一个结构体。

让我们重构代码，以便先检查类型然后再执行工作。

```go
func walk(x interface{}, fn func(input string)) {
	val := getValue(x)
	switch val.Kind() {
	case reflect.Struct:
		for i := 0; i < val.NumField(); i++ {
			walk(val.Field(i).Interface(), fn)
		}
	case reflect.Slice:
		for i := 0; i < val.Len(); i++ {
			walk(val.Index(i).Interface(), fn)
		}
	case reflect.String:
		fn(val.String())
	}
}
```

看起来好多了！如果它是一个结构体或切片，我们会遍历其值并对每个值调用 walk。否则，如果它是 reflect.String，我们可以调用 fn。

不过在我看来它还可以更好。遍历字段/值然后调用 walk 的操作存在重复，但在概念上它们是相同的。

```go
func walk(x interface{}, fn func(input string)) {
	val := getValue(x)
	numberOfValues := 0
	var getField func(int) reflect.Value
	switch val.Kind() {
```

```
case reflect.String:
    fn(val.String())
case reflect.Struct:
    numberOfValues = val.NumField()
    getField = val.Field
case reflect.Slice:
    numberOfValues = val.Len()
    getField = val.Index
}

for i := 0; i < numberOfValues; i++ {
    walk(getField(i).Interface(), fn)
}
}
```

如果值是 reflect.String，那么我们就像往常一样调用 fn。

否则，我们的 switch 会根据类型提取出两件事

- 有多少个字段
- 如何提取 Value（Field 或 Index）

一旦确定了这些，我们就可以遍历 numberOfValues 并使用 getField 函数的结果调用 walk。

现在我们完成了，处理数组应该很简单。

## 首先编写测试

添加到用例中

```
{
    "Arrays",
    [2]Profile {
        {33, "London"},
        {34, "Reykjavík"},
    },
    []string{"London", "Reykjavík"},
},
```

## 尝试运行测试

```
=== RUN   TestWalk/Arrays
--- FAIL: TestWalk/Arrays (0.00s)
    reflection_test.go:78: got [], want [London Reykjavík]
```

## 编写足够代码使其通过

数组可以像切片一样处理，所以只需在 case 中加上逗号

```
func walk(x interface{}, fn func(input string)) {
    val := getValue(x)

    numberOfValues := 0
    var getField func(int) reflect.Value

    switch val.Kind() {
    case reflect.String:
        fn(val.String())
    case reflect.Struct:
        numberOfValues = val.NumField()
        getField = val.Field
    case reflect.Slice, reflect.Array:
        numberOfValues = val.Len()
        getField = val.Index
    }

    for i := 0; i < numberOfValues; i++ {
        walk(getField(i).Interface(), fn)
    }
}
```

我们接下来要处理的下一个类型是 map。

## 首先编写测试

```
{
    "Maps",
    map[string]string{
        "Foo": "Bar",
        "Baz": "Boz",
    },
    []string{"Bar", "Boz"},
},
```

## 尝试运行测试

```
=== RUN   TestWalk/Maps
--- FAIL: TestWalk/Maps (0.00s)
    reflection_test.go:86: got [], want [Bar Boz]
```

## 编写足够代码使其通过

再次如果你抽象地思考一下，你会发现 map 与 struct 非常相似，只是键在编译时是未知的。

```
func walk(x interface{}, fn func(input string)) {
    val := getValue(x)

    numberOfValues := 0
    var getField func(int) reflect.Value

    switch val.Kind() {
    case reflect.String:
        fn(val.String())
    case reflect.Struct:
        numberOfValues = val.NumField()
        getField = val.Field
    case reflect.Slice, reflect.Array:
        numberOfValues = val.Len()
        getField = val.Index
    case reflect.Map:
        for _, key := range val.MapKeys() {
            walk(val.MapIndex(key).Interface(), fn)
        }
    }
}
```

```
for i := 0; i < numberOfValues; i++ {
    walk(getField(i).Interface(), fn)
}
}
```

然而，按设计你无法通过索引从 map 中获取值。它只能通过键完成，所以这破坏了我们的抽象，可恶。

## 重构

你现在感觉如何？当时感觉可能是一个不错的抽象，但现在代码感觉有点别扭。

*这没问题！* 重构是一段旅程，有时我们会犯错。TDD 的一个重要点是它给了我们尝试这些东西的自由。

通过以测试为后盾的小步前进，这绝不是不可逆转的情况。让我们把它恢复到重构前的样子。

```
func walk(x interface{}, fn func(input string)) {
    val := getValue(x)

    walkValue := func(value reflect.Value) {
        walk(value.Interface(), fn)
    }

    switch val.Kind() {
    case reflect.String:
        fn(val.String())
    case reflect.Struct:
        for i := 0; i < val.NumField(); i++ {
            walkValue(val.Field(i))
        }
    case reflect.Slice, reflect.Array:
        for i := 0; i < val.Len(); i++ {
            walkValue(val.Index(i))
        }
    }
```

```go
case reflect.Map:
	for _, key := range val.MapKeys() {
		walkValue(val.MapIndex(key))
	}
}
```
```

我们引入了 walkValue，它使 switch 内部对 walk 的调用保持 DRY，这样它们只需要从 val 中提取出 reflect.Values。

## 一个最终问题

请记住 Go 中的 map 不保证顺序。因此你的测试有时会失败，因为我们断言对 fn 的调用是按特定顺序进行的。

为了解决这个问题，我们需要将关于 map 的断言移到一个新的测试中，在该测试中我们不关心顺序。

```go
t.Run("with maps", func(t *testing.T) {
	aMap := map[string]string{
		"Foo": "Bar",
		"Baz": "Boz",
	}

	var got []string
	walk(aMap, func(input string) {
		got = append(got, input)
	})

	assertContains(t, got, "Bar")
	assertContains(t, got, "Boz")
})
```

## 这里是如何定义 assertContains

```
```go
func assertContains(t testing.TB, haystack []string, needle string) t.Helper()
	contains := false
	...
```
```
