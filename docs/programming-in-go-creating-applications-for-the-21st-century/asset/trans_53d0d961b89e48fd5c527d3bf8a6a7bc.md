
# 284 第 6 章 对象面向编程

（约定），用于创建模糊布尔（Fuzzy Booleans）。当然，这可以确保只创建有效的模糊布尔。

由于 `FuzzyBool` 类型基于包含一个值的结构体，该值的类型在结构体内部，我们可以将类型简化为 `type FuzzyBool struct { float32 }`。这意味着需要更改访问值的代码——我们将在其中一个方法中看到——将 `fuzzy.value` 改为 `fuzzy.float32`。我们倾向于使用命名变量，部分是因为我们觉得它更符合审美，另一部分是因为如果我们想更改底层类型（例如改为 `float64`），需要做的更改会更少。

由于结构体只包含一个值，因此还有其他变体。例如，我们可以将类型更改为 `type FuzzyBool float32`，使其直接基于 `float32`。这样做效果良好，但需要稍多代码，并且对于实现我们使用的基于结构体的方法来说会稍微复杂一些。

然而，如果我们将自己限制在创建不可变的模糊布尔（唯一的区别是，不再通过 `Set()` 方法设置值，而是必须分配一个新的模糊布尔），我们可以通过直接基于 `float32` 类型来大大简化代码。

```go
func New(value interface{}) (*FuzzyBool, error) {
    amount, err := float32ForValue(value)
    return &FuzzyBool{amount}, err
}
```

为了方便模糊布尔用户使用，我们不只接受 `float32` 作为初始化值，还接受 `float64`（Go 的默认浮点类型）、`int`（整数类型）和 `bool`。这种灵活性通过使用自定义的 `float32ForValue()` 函数实现，该函数为给定值返回 `float32` 和 `nil`——或者在值类型不是它能处理的类型时返回一个错误。

如果我们传递了一个无效类型的值，说明我们犯了编程错误，并希望发现它。但我们不希望应用程序在用户那里崩溃。因此，我们不仅返回一个 `*FuzzyBool`，还返回一个 `error`。如果我们向 `New` 传递一个已知有效的字面量（如前面的代码段：283），我们可以安全地忽略错误；但如果我们传递一个变量，应该检查返回的错误，以防它不为 `nil`。

`New()` 函数返回一个指向 `FuzzyBool` 的指针而不是值，因为我们选择让此实现中的模糊布尔是可变的。这意味着那些修改模糊布尔的方法（在本例中，即 `Set()` 方法）必须接收指针接收者，而不是值接收者。*

> * 事实上，我们可以返回 `FuzzyBool` 值并保持类型为可变的，正如书中代码的 `fuzzy_value` 示例所示。

## 6.5. 示例

一个合理的经验法则是：对于不可变类型，创建接收接收值的方法；对于可变类型，创建接收指针的方法。（对于可变类型，让某些方法接收值而其他方法接收指针是完全可能的——但在实践中可能不方便。）对于大型结构体类型（例如具有两个或更多字段的类型），最好使用指针，以将传递它们的成本保持在单个指针上。

```go
func float32ForValue(value interface{}) (float32, error) {
	var fuzzy float32
	switch value := value.(type) { // 影子变量
	case float32:
		fuzzy = value
	case float64:
		fuzzy = float32(value)
	case int:
		fuzzy = float32(value)
	case bool:
		fuzzy = 0
		if value {
			fuzzy = 1
		}
		default:
		return 0, fmt.Errorf("float32ForValue(): %v is not a number or Boolean", value)
	}
	if fuzzy < 0 {
		fuzzy = 0
	} else if fuzzy > 1 {
		fuzzy = 1
	}
	return fuzzy, nil
}
```

这个导出的辅助函数被 `New()` 和 `Set()` 方法用于将值转换为 `[0.,1]` 范围内的 `float32`。通过使用类型分支（5.2.2.2, 17），可以轻松完成对不同类型的处理。

如果调用函数时的值无效，我们将返回一个非 `nil` 错误。这让调用者有责任检查返回值并在发生错误时做出相应响应。调用者可以在出错时触发 `panic` 并导致应用程序带回溯跟踪地崩溃，也可以自行处理问题。对于此类低级函数，当它们遇到问题时返回错误通常更好，因为它们并不了解程序的逻辑，不足以知道如何处理，因此应该将问题向上推给调用者，而调用者应该处于更合适的位置知道该做什么。

## 第 6 章 对象面向编程

虽然我们认为传递无效类型的值是一个编程错误，因此值得返回一个非 `nil` 错误，但我们选择对超出范围的值处理得更宽容一些，并简单地将它们限制（clamp）到最接近的值。

```go
func (fuzzy *FuzzyBool) String() string {
	return fmt.Sprintf("%0f%%", 100*fuzzy.value)
}
```

我们选择模糊布尔的字符串表示为整数百分比。（回想一下，"%0f"` 字符串格式指定一个没有小数点的浮点数。）

（此处后续 OCR 文本存在重复和乱码，已根据逻辑流进行处理。）

```go
func (fuzzy *FuzzyBool) Set(value interface{}) error {
	f, err := float32ForValue(value)
	if err != nil {
		return err
	}
	fuzzy.value = f
	return nil
}
```
