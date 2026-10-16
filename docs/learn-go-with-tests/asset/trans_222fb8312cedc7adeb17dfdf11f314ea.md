
## 罗马数字

你可以在这里找到本章的所有代码。

一些公司会在面试过程中要求你完成“罗马数字练习”。本章将展示如何使用TDD来应对它。

我们将编写一个函数，将阿拉伯数字（0到9的数字）转换为罗马数字。

如果你没听说过罗马数字，它们就是罗马人记录数字的方式。

将符号拼接在一起就能构成数字，这些符号代表数值。

所以 I 表示“一”，III 表示三。

看起来容易，但有几个有趣的规则。V表示五，但IV是4（不是IIII）。

MCMLXXXIV是1984。这看起来很复杂，很难想象我们如何从一开始就写出代码来解决这个问题。

正如本书所强调的，软件开发人员的一项关键技能是尝试识别有用功能的“薄垂直切片”，然后进行迭代。TDD工作流有助于促进迭代开发。

所以，与其从1984开始，不如我们先从1开始。

### 先编写测试

```
func TestRomanNumerals(t *testing.T) {
	got := ConvertToRoman(1)
	want := "I"

    if got != want {
        t.Errorf("got %q, want %q", got, want)
    }
}
```

如果你已经读到这里，这会让你觉得非常无聊和常规。这是一件好事。

### 尝试运行测试

```
./numeral_test.go:6:9: undefined: ConvertToRoman
```

让编译器来指引方向。

### 编写最少量的代码，使测试能够运行并检查失败的测试输出

创建我们的函数，但先不要让测试通过，始终确保测试以你预期的方式失败。

```
func ConvertToRoman (arabic int) string {
    return ""
}
```

现在它应该可以运行了。

```
=== RUN   TestRomanNumerals
--- FAIL: TestRomanNumerals (0.00s)
    numeral_test.go:10: got '', want 'I'
FAIL
```

### 编写足够的代码使其通过

```
func ConvertToRoman(arabic int) string {
    return "I"
}
```

### 重构

目前没什么需要重构的。

*我知道*，硬编码结果感觉很奇怪，但在TDD中，我们希望能尽可能长时间地远离“红色”状态。我们可能*觉得*没有完成多少，但我们已经定义了API，并有一个测试捕获了我们的一个规则；即使“真正的”代码相当愚蠢。

现在利用这种不安的感觉，编写一个新的测试，迫使我们写出稍微不那么愚蠢的代码。

### 先编写测试

我们可以使用子测试来很好地分组我们的测试。

```
func TestRomanNumerals(t *testing.T) {
    t.Run("1 gets converted to I", func(t *testing.T) {
        got := ConvertToRoman(1)
        want := "I"

        if got != want {
            t.Errorf("got %q, want %q", got, want)
        }
    })

    t.Run("2 gets converted to II", func(t *testing.T) {
        got := ConvertToRoman(2)
        want := "II"

        if got != want {
            t.Errorf("got %q, want %q", got, want)
        }
    })
}
```

### 尝试运行测试

```
=== RUN   TestRomanNumerals/2_gets_converted_to_II
--- FAIL: TestRomanNumerals/2_gets_converted_to_II (0.00s)
    numeral_test.go:20: got 'I', want 'II'
```

没什么好惊讶的。

### 编写足够的代码使其通过

```go
func ConvertToRoman(arabic int) string {
    if arabic == 2 {
        return "II"
    }
    return "I"
}
```

是的，仍然感觉我们并没有真正解决问题。所以我们需要编写更多的测试来推动我们前进。

### 重构

我们的测试中有一些重复。当你测试的内容感觉像是“给定输入X，我们期望Y”这种情况时，你可能应该使用基于表格的测试。

```go
func TestRomanNumerals(t *testing.T) {
    cases := []struct {
        Description string
        Arabic      int
        Want        string
    }{
        {"1 gets converted to I", 1, "I"},
        {"2 gets converted to II", 2, "II"},
    }

for _, test := range cases {
    t.Run(test.Description, func(t *testing.T) {
        got := ConvertToRoman(test.Arabic)
        if got != test.Want {
            t.Errorf("got %q, want %q", got, test.Want)
        }
    })
}
}
```

我们现在可以轻松地添加更多用例，而无需编写更多测试样板代码。

让我们继续推进，攻克3。

### 先编写测试

将以下内容添加到我们的用例中。

```
{"3 gets converted to III", 3, "III"},
```

### 尝试运行测试

```
=== RUN   TestRomanNumerals/3_gets_converted_to_III
--- FAIL: TestRomanNumerals/3_gets_converted_to_III (0.00s)
    numeral_test.go:20: got 'I', want 'III'
```

### 编写足够的代码使其通过

```
func ConvertToRoman(arabic int) string {
    if arabic == 3 {
        return "III"
    }
    if arabic == 2 {
        return "II"
    }
    return "I"
}
```

### 重构

好吧，我开始不喜欢这些if语句了，如果你仔细观察代码，你会发现我们是在根据arabic的大小构建一串I。

我们“知道”对于更复杂的数字，我们将需要进行某种算术运算和字符串拼接。

让我们带着这些想法尝试重构，它可能不适合最终解决方案，但没关系。我们随时可以丢弃我们的代码，并依靠已有的测试重新开始。

```
func ConvertToRoman (arabic int) string {
    var result strings.Builder
    for i := 0; i < arabic; i++ {
        result.WriteString("I")
    }
    return result.String()
}
```

你可能以前没有使用过strings.Builder。

Builder用于通过Write方法高效地构建字符串。它最大限度地减少了内存复制。

通常，在遇到实际性能问题之前，我不会费心进行这种优化，但这里的代码量并不比“手动”追加字符串多多少，所以我们不妨使用更快的方法。

对我来说，这段代码看起来更好，并且描述了我们目前所知的领域。

### 罗马人也讲究DRY原则……

现在事情开始变得更加复杂。罗马人凭借他们的智慧认为，重复的字符会变得难以阅读和计数。所以罗马数字的一个规则是，同一个字符不能连续重复超过3次。

相反，你取下一个更高的符号，然后通过在其左侧放置一个符号来“减去”。并非所有符号都可以用作减数；只有I（1）、X（10）和C（100）可以。

例如，罗马数字中的5是V。要表示4，你不能写IIII，而应该写IV。

### 先编写测试

```
{"4 gets converted to IV (can't repeat more than 3 times)", 4, "IV"},
```

### 尝试运行测试

```
=== RUN TestRomanNumerals/4_gets_converted_to_IV_(cant_repeat_more_than_3_times)
--- FAIL: TestRomanNumerals/4_gets_converted_to_IV_(cant_repeat_more_than_3_times) (0.00s)
    numeral_test.go:24: got 'IIII', want 'IV'
```

### 编写足够的代码使其通过

```
func ConvertToRoman(arabic int) string {
    if arabic == 4 {
        return "IV"
    }

    var result strings.Builder

    for i := 0; i < arabic; i++ {
        result.WriteString("I")
    }

    return result.String()
}
```

### 重构

我不“喜欢”我们打破了字符串构建的模式，我想继续沿用这个模式。

```go
func ConvertToRoman(arabic int) string {
	var result strings.Builder

	for i := arabic; i > 0; i-- {
		if i == 4 {
			result.WriteString("IV")
			break
		}
		result.WriteString("I")
	}

	return result.String()
}
```

为了让4能够“契合”我目前的思路，我现在从阿拉伯数字开始倒序计数，并在过程中把符号添加到我们的字符串中。不确定从长远来看这是否可行，但让我们拭目以待！

让5也能工作吧。

### 先编写测试

```
{"5 gets converted to V", 5, "V"},
```

### 尝试运行测试

```
=== RUN   TestRomanNumerals/5 gets converted to V
--- FAIL: TestRomanNumerals/5_gets_converted_to_V (0.00s)
numeral_test.go:25: got 'IIIV', want 'V'
```

### 编写足够的代码使其通过

只需复制我们处理4的方法。

```
func ConvertToRoman (arabic int) string {

    var result strings.Builder

    for i := arabic; i > 0; i-- {
        if i == 5 {
            result.WriteString("V")
            break
        }
        if i == 4 {
            result.WriteString("IV")
            break
        }
        result.WriteString("I")
    }

    return result.String()
}
```

### 重构

