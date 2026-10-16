
(这对于字典来说可能似乎没什么用。然而，这在其他用例中可能是关键场景。)

```
func TestSearch(t *testing.T) {
    dictionary := Dictionary{"test": "this is just a test"}

    t.Run("known word", func(t *testing.T) {
        got, _ := dictionary.Search("test")
        want := "this is just a test"

        assertStrings(t, got, want)
    })

    t.Run("unknown word", func(t *testing.T) {
        _, err := dictionary.Search("unknown")
        want := "could not find the word you were looking for"

        if err == nil {
            t.Fatal("expected to get an error.")
        }

        assertStrings(t, err.Error(), want)
    })
}
```

在 Go 中处理这种情况的方式是返回第二个参数，该参数为 Error 类型。

错误可以通过 .Error() 方法转换为字符串，我们在将其传递给断言时就是这样做的。我们还用 if 保护 assertStrings，以确保不会在 nil 上调用 .Error()。

## 尝试并运行测试

这无法编译

```
./dictionary_test.go:18:10: assignment mismatch: 2 variables but 1 values
```

## 编写最少量的代码使测试运行并检查输出

```
func (d Dictionary) Search(word string) (string, error) {
    return d[word], nil
}
```

你的测试现在应该会以更清晰的错误信息失败。

dictionary_test.go:22: expected to get an error.

## 编写足够多的代码使其通过

```
func (d Dictionary) Search(word string) (string, error) {
    definition, ok := d[word]
    if !ok {
        return "", errors.New("could not find the word you were looking for")
    }
    
    return definition, nil
}
```

为了使其通过，我们使用了 map 查找的一个有趣特性。它可以返回 2 个值。第二个值是一个布尔值，表示键是否成功找到。

这个特性使我们能够区分一个不存在的词和一个只是没有定义的词。

## 重构

```
var ErrNotFound = errors.New("could not find the word you were looking for")
```

```
func (d Dictionary) Search(word string) (string, error) {
```

```
definition, ok := d[word]
if !ok {
    return "", ErrNotFound
}

return definition, nil
}
```

我们可以通过将其提取为变量来消除 Search 函数中的魔法错误。这也将使我们能够拥有更好的测试。

```
t.Run("unknown word", func(t *testing.T) {
    _, got := dictionary.Search("unknown")

    assertError(t, got, ErrNotFound)
})
```

```
func assertError(t testing.TB, got, want error) {
    t.Helper()

    if got != want {
        t.Errorf("got error %q want %q", got, want)
    }
}
```

通过创建新的辅助函数，我们能够简化测试，并开始使用我们的 ErrNotFound 变量，这样即使将来更改错误文本，测试也不会失败。

## 先写测试

我们有一种很好的搜索字典的方法。然而，我们没有办法向字典中添加新词。

```
func TestAdd(t *testing.T) {
    dictionary := Dictionary{}
    dictionary.Add("test", "this is just a test")
```

```
want := "this is just a test"
got, err := dictionary.Search("test")
if err != nil {
    t.Fatal("should find added word:", err)
}

if got != want {
    t.Errorf("got %q want %q", got, want)
}
}
```

在此测试中，我们利用了 Search 函数，使字典的验证变得稍微容易一些。

## 编写最少量的代码使测试运行并检查输出

在 dictionary.go 中

```
func (d Dictionary) Add(word, definition string) {
}
```

你的测试现在应该会失败

```
dictionary_test.go:31: should find added word: could not find the word you were looking for
```

## 编写足够多的代码使其通过

```
func (d Dictionary) Add(word, definition string) {
    d[word] = definition
}
```

向 map 添加元素也类似于向数组添加元素。你只需要指定一个键并将其设为等于一个值。

## 指针、拷贝等

map 的一个有趣特性是，你可以在不将其作为地址传递的情况下修改它（例如 `&myMap`）

这可能使它们*感觉*像“引用类型”，但正如 Dave Cheney 所描述的那样，它们并不是。

map 值是指向 runtime.hmap 结构的指针。

因此，当你将 map 传递给函数/方法时，你确实在复制它，但只是指针部分，而不是包含数据的底层数据结构。

map 的一个陷阱是它们可以是 `nil` 值。`nil` map 在读取时表现得像空 map，但尝试向 `nil` map 写入会导致运行时 panic。你可以在这里阅读更多关于 maps 的内容。

因此，你永远不应该初始化一个空的 map 变量：

```
var m map[string]string
```

相反，你可以像上面那样初始化一个空 map，或者使用 `make` 关键字为你创建 map：

```
var dictionary = map[string]string{}
```

```
// OR
```

```
var dictionary = make(map[string]string)
```

这两种方法都会创建一个空的 `hash map` 并让 `dictionary` 指向它。这确保你永远不会遇到运行时 panic。

## 重构

我们的实现中没有太多需要重构的地方，但测试可以使用一点简化。

```
func TestAdd(t *testing.T) {
    dictionary := Dictionary{}
    word := "test"
    definition := "this is just a test"

    dictionary.Add(word, definition)

    assertDefinition(t, dictionary, word, definition)
}

func assertDefinition(t testing.TB, dictionary Dictionary, word, definition string) {
    t.Helper()

    got, err := dictionary.Search(word)
    if err != nil {
        t.Fatal("should find added word:", err)
    }

    if definition != got {
        t.Errorf("got %q want %q", got, definition)
    }
}
```

我们为 word 和 definition 创建了变量，并将定义断言移到了自己的辅助函数中。

我们的 Add 看起来不错。除了，我们没有考虑当我们尝试添加的值已经存在时会发生什么！

如果值已存在，Map 不会抛出错误。相反，它们会继续用新提供的值覆盖该值。这在实践中可能很方便，但使我们的函数名不够准确。Add 不应修改现有值。它应该只向字典中添加新词。

## 先写测试

```
func TestAdd(t *testing.T) {
    t.Run("new word", func(t *testing.T) {
        dictionary := Dictionary{}
        word := "test"
        definition := "this is just a test"

        err := dictionary.Add(word, definition)

        assertError(t, err, nil)
        assertDefinition(t, dictionary, word, definition)
    })

    t.Run("existing word", func(t *testing.T) {
        word := "test"
        definition := "this is just a test"
        dictionary := Dictionary{word: definition}
        err := dictionary.Add(word, "new test")

        assertError(t, err, ErrWordExists)
        assertDefinition(t, dictionary, word, definition)
    })
}

func assertError(t testing.TB, got, want error) {
    t.Helper()
    if got != want {
        t.Errorf("got %q want %q", got, want)
    }
}
```

对于此测试，我们修改了 Add 使其返回一个错误，我们将其与新的错误变量 ErrWordExists 进行验证。我们还修改了之前的测试以检查 nil 错误，以及 assertError 函数。

## 尝试运行测试

编译器会失败，因为我们没有为 Add 返回值。

```
./dictionary_test.go:30:13:  dictionary.Add(word,  definition)
used as value
./dictionary_test.go:41:13:  dictionary.Add(word,  "new  test")
used as value
```

## 编写最少量的代码使测试运行并检查输出

在 dictionary.go 中

```
var (
    ErrNotFound  = errors.New("could not find the word you were looking for")
    ErrWordExists = errors.New("cannot add word because it already exists")
)

func (d Dictionary) Add(word, definition string) error {
    d[word] = definition
    return nil
}
```

现在我们又得到了两个错误。我们仍然在修改值，并返回 nil 错误。

```
dictionary_test.go:43: got error '%!q(<nil>)' want 'cannot add word because it already exists'
dictionary_test.go:44: got 'new  test' want 'this  is  just  a test'
```

## 编写足够多的代码使其通过

```
func (d Dictionary) Add(word, definition string) error {
    _, err := d.Search(word)

    switch err {
    case ErrNotFound:
        d[word] = definition
    case nil:
