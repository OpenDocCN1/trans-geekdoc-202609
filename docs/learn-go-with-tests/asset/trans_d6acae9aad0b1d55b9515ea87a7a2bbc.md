
-   创建某种“初始”结果值。
-   遍历集合，对结果和切片中的下一个项应用某种操作（或函数），为结果设置新值
-   返回结果。

这个想法在函数式编程圈中常被讨论，通常被称为 'reduce' 或 fold。

在函数式编程中，fold（也称为 reduce、accumulate、aggregate、compress 或 inject）指的是分析递归数据结构的一系列高阶函数，通过使用给定的合并操作，重新组合递归处理其组成部分的结果，构建出返回值。通常，fold 会带有一个合并函数、数据结构的一个顶节点，以及可能在某些条件下使用的默认值。然后 fold 会以系统的方式使用该函数合并数据结构层次结构中的元素。

Go 一直拥有高阶函数，自版本 1.18 起也拥有泛型，因此现在可以定义我们在更广泛领域中讨论的一些函数。没有必要在沙子里埋头，这在 Go 生态系统之外是一个非常常见的抽象，了解它会很有益处。

现在，我知道你们中有些人可能对此感到不适。

Go 应该是简单的

**不要混淆易用性与简洁性**。做循环和复制粘贴代码很容易，但不一定是简单的。关于简单 vs 易用，观看 Rich Hickey 的精彩演讲 - Simple Made Easy。

**不要混淆不熟悉与复杂性**。Fold/reduce 最初听起来可能很吓人，很像计算机科学，但它本质上只是对一种非常常见操作的抽象。取一个集合，并
将其组合成一个项目。当你退一步看，你会意识到你可能经常这样做 *很多*。

## A generic refactor

人们在使用 shiny new 语言特性时常犯的一个错误是，他们在没有具体用例的情况下就开始使用它们。他们依靠推测和猜测来指导自己的努力。

幸运的是，我们已经编写了我们的“有用”函数并围绕它们编写了测试，因此现在我们在 TDD 的重构阶段可以自由地尝试想法，并且知道我们尝试的任何东西都可以通过单元测试来验证其价值。

使用泛型作为重构步骤中简化代码的工具，更有可能引导你做出有用的改进，而不是过早的抽象。

我们可以安全地尝试，重新运行测试，如果我们喜欢这个更改，我们可以提交。如果不喜欢，就撤销更改。这种实验的自由是 TDD 的真正巨大价值之一。

你应该已经从上一章熟悉了泛型语法，尝试编写自己的 `Reduce` 函数并在 `Sum` 和 `SumAllTails` 中使用它。

## Hints

如果你先考虑函数的参数，它会给你一个非常小的有效解决方案集合

-   你想要归约的数组
-   某种合并函数，或 *累加器*

"Reduce" 是一个记录非常详尽的模式，没有必要重新发明轮子。阅读 wiki，特别是列表部分，它
会提示你还需要另一个参数。

在实践中，拥有一个初始值是方便且自然的

## My first-pass of Reduce

```
func Reduce[A any](collection []A, accumulator func(A, A) A, initialValue A) A {
    var result = initialValue
    for _, x := range collection {
        result = accumulator(result, x)
    }
    return result
}
```

Reduce 捕捉了该模式的本质，它是一个接受集合、累加函数、初始值并返回单个值的函数。没有围绕具体类型的混乱干扰。

如果你理解泛型语法，你应该没有问题理解这个函数的作用。通过使用公认的术语 Reduce，其他语言的程序员也能理解意图。

## The usage

```
// Sum calculates the total from a slice of numbers.
func Sum(numbers []int) int {
    add := func(acc, x int) int { return acc + x }
    return Reduce(numbers, add, 0)
}
```

```
// SumAllTails calculates the sums of all but the first number c
func SumAllTails(numbers ...[]int) []int {
    sumTail := func(acc, x []int) []int {
        if len(x) == 0 {
            return append(acc, 0)
        } else {
            tail := x[1:]
            return append(acc, Sum(tail))
        }
    }

    return Reduce(numbers, sumTail, []int{})
}
```

Sum 和 SumAllTails 现在分别描述了它们在各自第一行声明的函数的行为。对集合运行计算的行为在 Reduce 中被抽象掉了。

## Further applications of reduce

使用测试我们可以玩弄我们的 reduce 函数，看看它的可重用性如何。我已从上一章复制了我们的通用断言函数。

```
func TestReduce(t *testing.T) {
    t.Run("multiplication of all elements", func(t *testing.T) {
        multiply := func(x, y int) int {
            return x * y
        }

        AssertEqual(t, Reduce([]int{1, 2, 3}, multiply, 1), 6)
    })

    t.Run("concatenate strings", func(t *testing.T) {
        concatenate := func(x, y string) string {
            return x + y
        }

        AssertEqual(t, Reduce([]string{"a", "b", "c"}, concatena
    })
}
```

## The zero value

在乘法示例中，我们展示了将默认值作为 `Reduce` 的参数的原因。如果我们依赖 Go 对 `int` 的默认值 0，我们会将初始值乘以 0，然后乘以后面的值，所以你永远只能得到 0。通过将其设置为 1，切片中的第一个元素会保持不变，其余元素会乘以下一个元素。

如果你想在你的极客朋友面前显得聪明，你会称之为恒等元素。

在数学中，二元运算在集合上的恒等元素，或中性元素，是集合中的一个元素，当该运算被应用时，它使集合中的每个元素保持不变。

在加法中，恒等元素是 0。

```
1 + 0 = 1
```

在乘法中，它是 1。

```
1 * 1 = 1
```

## What if we wish to reduce into a different type from A?

假设我们有一个 `Transaction` 列表，我们想要一个函数来接收它们，加上一个名称来计算其银行余额。

让我们遵循 TDD 流程。

## Write the test first

```
func TestBadBank(t *testing.T) {
    transactions := []Transaction{
        {
            From: "Chris",
            To:   "Riya",
            Sum:  100,
        },
        {
            From: "Adil",
            To:   "Chris",
            Sum:  25,
        },
    }

    AssertEqual(t, BalanceFor(transactions, "Riya"), 100)
    AssertEqual(t, BalanceFor(transactions, "Chris"), -75)
    AssertEqual(t, BalanceFor(transactions, "Adil"), -25)
}
```

## Try to run the test

```
#
                    github.com/quii/learn-go-with-tests/arrays/v8
[github.com/quii/learn-go-with-tests/arrays/v8.test]
./bad_bank_test.go:6:20: undefined: Transaction
./bad_bank_test.go:18:14: undefined: BalanceFor
```

## Write the minimal amount of code for the test to run and check the failing test output

我们还没有类型或函数，添加它们以使测试运行。

```
type Transaction struct {
    From string
    To   string
    Sum  float64
}
```

```go
func BalanceFor(transactions []Transaction, name string) float64 {
    return 0.0
}
```

当你运行测试时，你应该会看到以下内容：

```
```
=== RUN TestBadBank
bad_bank_test.go:19: got 0, want 100
bad_bank_test.go:20: got 0, want -75
bad_bank_test.go:21: got 0, want -25
--- FAIL: TestBadBank (0.00s)
```
```

## Write enough code to make it pass

让我们先假设我们没有 Reduce 函数来编写代码。

```go
func BalanceFor(transactions []Transaction, name string) float64 {
    var balance float64
    for _, t := range transactions {
        if t.From == name {
            balance -= t.Sum
        }
        if t.To == name {
            balance += t.Sum
        }
    }
    return balance
}
```

此时，保持一些源代码控制的纪律并提交你的工作。我们有可工作的软件，准备挑战 Monzo、Barclays 等。
