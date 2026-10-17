
```
var ErrInsufficientFunds = errors.New("cannot withdraw, insufficient funds")
```

```
func (w *Wallet) Withdraw(amount Bitcoin) error {
	if amount > w.balance {
		return ErrInsufficientFunds
	}
	w.balance -= amount
	return nil
}
```

`var` 关键字允许我们定义包级别的全局值。

这本身就是个很好的改进，因为现在我们的 `Withdraw` 函数看起来非常清晰。

接下来，我们可以重构测试代码，用这个值代替具体的字符串。

```
func TestWallet(t *testing.T) {
	t.Run("Deposit", func(t *testing.T) {
```

```
wallet := Wallet{}
wallet.Deposit(Bitcoin(10))
assertBalance(t, wallet, Bitcoin(10))
})
t.Run("Withdraw with funds", func(t *testing.T) {
	wallet := Wallet{Bitcoin(20)}
	wallet.Withdraw(Bitcoin(10))
	assertBalance(t, wallet, Bitcoin(10))
})
t.Run("Withdraw insufficient funds", func(t *testing.T) {
	wallet := Wallet{Bitcoin(20)}
	err := wallet.Withdraw(Bitcoin(100))
	assertError(t, err, ErrInsufficientFunds)
	assertBalance(t, wallet, Bitcoin(20))
})
func assertBalance(t testing.TB, wallet Wallet, want Bitcoin) {
	t.Helper()
	got := wallet.Balance()
	if got != want {
		t.Errorf("got %q want %q", got, want)
	}
}
func assertError(t testing.TB, got, want error) {
	t.Helper()
	if got == nil {
		t.Fatal("didn't get an error but wanted one")
	}
	if got != want {
		t.Errorf("got %q, want %q", got, want)
	}
}
```

现在测试也更容易理解了。

```
assertBalance(t, wallet, Bitcoin(10))
})

t.Run("Withdraw with funds", func(t *testing.T) {
    wallet := Wallet{Bitcoin(20)}
    err := wallet.Withdraw(Bitcoin(10))

    assertNoError(t, err)
    assertBalance(t, wallet, Bitcoin(10))
})

t.Run("Withdraw insufficient funds", func(t *testing.T) {
    wallet := Wallet{Bitcoin(20)}
    err := wallet.Withdraw(Bitcoin(100))

    assertError(t, err, ErrInsufficientFunds)
    assertBalance(t, wallet, Bitcoin(20))
})
}

func assertBalance(t testing.TB, wallet Wallet, want Bitcoin) {
    t.Helper()
    got := wallet.Balance()

    if got != want {
        t.Errorf("got %s want %s", got, want)
    }
}

func assertNoError(t testing.TB, got error) {
    t.Helper()
    if got != nil {
        t.Fatal("got an error but didn't want one")
    }
}

func assertError(t testing.TB, got error, want error) {
    t.Helper()
    if got == nil {
        t.Fatal("didn't get an error but wanted one")
    }
```

```
}
    if got != want {
        t.Errorf("got %s, want %s", got, want)
    }
}
```

## 总结

### 指针

-   Go 在把值传给函数或方法时会进行拷贝，所以如果你要编写一个需要修改状态的函数，就需要让它接收一个指向要修改内容的指针。

-   Go 对值进行拷贝这一特性在很多情况下都很有用，但有时你不希望系统拷贝某个东西，这时就需要传入引用。例如引用非常大的数据结构，或者只需要一个实例的东西（比如数据库连接池）。

### nil

-   指针可以为 nil。

-   当函数返回一个指向某物的指针时，你需要确保检查它是否为 nil，否则可能会引发运行时异常——编译器在这里帮不了你。

-   当你想要描述一个可能缺失的值时，这会很有用。

### 错误

-   错误是表示调用函数或方法失败的方式。

-   通过倾听测试的意见，我们得出结论：检查错误中的字符串会导致测试不稳定。因此我们重构实现，改用有意义的值，这不仅让测试更容易编写，也让我们 API 的用户更省心。

-   错误处理并不是到此为止，你还可以做更复杂的事情，但这只是入门。后续章节会介绍更多策略。

-   [不要只检查错误，要优雅地处理它们。]

### 基于已有类型创建新类型

-   可以为值增加更多领域特定的含义。

-   可以让你实现接口。

指针和错误是编写 Go 代码的重要部分，你需要习惯于它们。幸运的是，如果你做错了什么，编译器`通常`会帮你指出问题，只需耐心阅读错误信息。

## 映射

你可以在这里找到本章所有代码。

在数组和切片中，你了解了如何按顺序存储值。现在，我们将学习如何按键存储项并快速查找。

映射允许你以类似字典的方式存储条目。你可以把键看作单词，把值看作定义。而学习映射的最佳方式莫过于构建我们自己的字典，还有什么比这更好的呢？

首先，假设字典中已经有一些单词及对应定义，如果我们查找一个单词，它应该返回该单词的定义。

## 先编写测试

在 `dictionary_test.go` 中：

```
```go

package main

import "testing"

func TestSearch(t *testing.T) {

    dictionary := map[string]string{"test": "this is just a test"}

    got := Search(dictionary, "test")

    want := "this is just a test"

    if got != want {

        t.Errorf("got %q want %q given, %q", got, want, "test")

    }

}

```
```

声明映射与声明数组有些类似。只不过它以 `map` 关键字开头，并且需要两个类型。第一个是键类型，写在 `[]` 内。第二个是值类型，紧跟 `[]` 之后。

键类型比较特殊。它只能是可比较的类型，因为如果无法判断两个键是否相等，我们就无法确保取到正确的值。可比较类型在语言规范中有详细说明。

另一方面，值类型可以是任何你想要的类型，甚至可以是另一个映射。

这个测试中的其余部分你应该都很熟悉。

## 尝试运行测试

运行 `go test` 时，编译器会报错：`./dictionary_test.go:8:9: undefined: Search`。

### 编写最少代码让测试运行并检查输出

在 `dictionary.go` 中：

```
```go

package main

func Search(dictionary map[string]string, word string) string {

    return ""

}

```
```

现在你的测试应该会失败，并给出清晰的错误信息：

```
dictionary_test.go:12: got '' want 'this is just a test' given, 'test'.
```

### 编写足够的代码让它通过

```
```go

func Search(dictionary map[string]string, word string) string {

    return dictionary[word]

}

```
```

从映射中取值与从数组中取值一样，都是 `map[key]`。

### 重构

```
```go

func TestSearch(t *testing.T) {

    dictionary := map[string]string{"test": "this is just a test"}

    got := Search(dictionary, "test")

    want := "this is just a test"

    assertStrings(t, got, want)

}

func assertStrings(t testing.TB, got, want string) {

    t.Helper()

    if got != want {

        t.Errorf("got %q want %q", got, want)

    }

}

```
```

我决定创建一个 `assertStrings` 辅助函数，使实现更通用。

### 使用自定义类型

我们可以通过围绕 map 创建新类型，并把 `Search` 改为方法，从而改进字典的用法。

在 `dictionary_test.go` 中：

```
```go

func TestSearch(t *testing.T) {

    dictionary := Dictionary{"test": "this is just a test"}

    got := dictionary.Search("test")

    want := "this is just a test"

    assertStrings(t, got, want)

}

```
```

我们开始使用 `Dictionary` 类型，但还没有定义它。然后在 `Dictionary` 实例上调用 `Search`。

我们不需要修改 `assertStrings`。

在 `dictionary.go` 中：

```
```go

type Dictionary map[string]string

func (d Dictionary) Search(word string) string {

    return d[word]

}

```
```

这里我们创建了一个 `Dictionary` 类型，它是对 map 的简单封装。定义好自定义类型后，就可以创建 `Search` 方法了。

## 先编写测试

基本的搜索实现起来很容易，但如果我们提供字典中不存在的单词，会发生什么？

实际上我们会得到一个空值。这还不错，因为程序可以继续运行，但还有更好的做法。函数可以报告该单词不在字典中。这样，用户就不会困惑于到底是不存在这个单词，还是仅仅没有定义。

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

错误可以通过 `.Error()` 方法转换为字符串，我们在将其传递给断言时就是这样做的。我们还用 `if` 保护 `assertStrings`，以确保不会在 nil 上调用 `.Error()`。

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

我们可以通过将其提取为变量来消除 `Search` 函数中的魔法错误。这也将使我们能够拥有更好的测试。

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

通过创建新的辅助函数，我们能够简化测试，并开始使用我们的 `ErrNotFound` 变量，这样即使将来更改错误文本，测试也不会失败。

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

在此测试中，我们利用了 `Search` 函数，使字典的验证变得稍微容易一些。

## 编写最少量的代码使测试运行并检查输出

在 `dictionary.go` 中

```
func (d Dictionary) Add(word, definition string) {
}
```

你的测试现在应该会失败

```
dictionary_test.go:31: should find added word: could not find the word you were looking for
```

## 编写足够多的代码使其通过
