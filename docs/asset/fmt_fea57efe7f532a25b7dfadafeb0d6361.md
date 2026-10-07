
```go
func createCounts(lines []string, separators []string, linesRead int) [][]int {
	counts := make([][]int, len(separators))
	for sepIndex := range separators {
		counts[sepIndex] = make([]int, linesRead)
		for lineIndex, line := range lines {
			counts[sepIndex][lineIndex] = strings.Count(line, separators[sepIndex])
		}
	}
	return counts
}
```

`createCounts()` 函数的目的是填充一个矩阵，其中存储读取的每行每个分隔符的计数。该函数首先创建一个 `int` 类型的切片切片，其切片数量与分隔符的数量相同。如果有四个分隔符，这会将 `counts` 设置为 `nil`。外层循环将每个 `nil` 替换为一个长度与行数相等的 `[]int`，因为 Go 会初始化为零值。内层循环用于填充计数。对于每个计数，都会统计每个分隔符出现的次数，并相应地更新 `counts`。

一旦第一个 map 构建完成，我们就输出第一份报告：按字母顺序列出的所有遇到的唯一单词及其对应的频率。然后，我们创建一个 map 的反转版本并输出第二份报告：按数字排序的频率及其关联单词列表。

```go
func commandLineFiles(files []string) []string {
	if runtime.GOOS == "windows" {
		args := make([]string, 0, len(files))
		for _, name := range files {
			if matches, err := filepath.Glob(name); err != nil {
				args = append(args, name) // Invalid pattern
			} else matches != nil { // At least one match
				args = append(args, matches...)
			}
		}
		return args
	}
}
```

`commandLineFiles()` 函数在 Linux 和 Mac OS X 等 Unix 平台上简单地返回它接收到的 `[]string`，因为在这些平台上，shell 会自动执行通配符展开（即将 `*.txt` 替换为任何匹配的文本文件，例如 `README.txt`、`INSTALL.txt` 等）。Windows shell `cmd.exe` 不执行通配符展开，因此如果用户在命令行输入 `*.txt`，程序将返回什么？为了提供合理的跨平台一致性，我们每当在 Windows 上时都会执行通配符展开。（处理平台差异的另一种方法是使用特定平台的 `.go` 文件——这将在后面的章节 9.1.1.1 中介绍，➤ 410。）

```go
func updateFrequencies(filename string, frequencyForWord map[string]int) {
	var file *os.File
	var err error
	if file, err = os.Open(filename); err != nil {
		log.Println("failed to open the file: %v", err)
		return
	}
	defer file.Close()
	readAndUpdateFrequencies(bufio.NewReader(file), frequencyForWord)
}
```

此函数专门用于文件处理。它在函数返回时关闭文件，并将实际工作传递给 `readAndUpdateFrequencies()` 函数。通过将文件读取器作为 `*bufio.Reader`（通过 `bufio.NewReader()` 调用产生），我们确保被调用的函数可以逐行读取读取文件，而不是必须读取原始字节。

## 4.4 示例

```go
func readAndUpdateFrequencies(reader *bufio.Reader,
    frequencyForWord map[string]int) {
    for {
		line, err := reader.ReadString('\n')
		for _, word := range SplitOnNonLetters(strings.TrimSpace(line)) {
			if len(word) > utf8.UTFMax ||
				utf8.RuneCountIn(word) > 1 {
				frequencyForWord[strings.ToLower(word)] += 1
			}
		}
		if err != nil {
			if err != io.EOF {
				log.Println("failed to finish reading the file: ", err)
			}
			break
		}
	}
}
```

这个函数的第一个部分现在应该已经非常熟悉了。我们创建了一个无限循环并逐读取文件，在到达文件末尾或发生错误时跳出循环（在这种情况下，我们会向用户报告错误）。当我们遇到错误时并不会终止程序，因为可能有很多文件需要读取，我们倾向于尽可能多工作并报告遇到的任何问题，而不是在第一个错误处停止。

内部循环是进行有趣处理的地方。任何给定的行都可能包含标点、数字、符号和其他非单词字符，因此我们通过按单词迭代，将行拆分为单词并使用自定义的 `SplitOnNonLetters()` 函数丢弃任何非单词字符。而且我们最初获取的字符串已经修剪了两端的空白。

我们只想包含至少两个字母的单词。实现此点最简单的方法是使用单子句语句，即 `if utf8.RuneCountIn(word) > 1`，这运行良好。

刚刚描述的简单测试可能有些开销，因为它将解析整个单词。因此在程序中，如果第一个子句采用更廉价的方法，我们会使用双子句语句。第一个子句检查单词中的字节数是否大于 `utf8.UTFMax`（这是一个值为 4 的常量，是表示单个 UTF-8 字符所需的最大字节数）。这是一个非常快速的测试，因为 Go 字符串知道它们包含多少字节，而且 Go 的二进制布尔运算符（`&&` 和 `||`）具有短路特性（见 2.2, 56）。当然，其他由四个字节或更少字节组成的字符（例如 7 位 ASCII 字符或几个 2 字节的 UTF-8 字符）将通过这个第一个检查，但这不是问题，因为第二个检查（rune）会很快的，因为它始终只有四个或更少的字符需要计数。

在这种情况下使用双子句值得吗？这实际上取决于输入——需要处理的单词越多、长度越长，节省性能的潜力就越大。唯一确定的方法是使用实际数据进行基准测试。

```go
func SplitOnNonLetters(s string) string {
	notLetter := func(char rune) bool { return unicode.IsLetter(char) }
	return strings.FieldsFunc(s, notLetter)
}
```

此函数用于根据非字母分割字符串。首先我们创建一个对字母返回 true、对非字母返回 false 的匿名函数。然后我们使用该函数调用 `strings.FieldsFunc`。

```go
func reportByWords(frequencyForWord map[string]int) {
	words := make([]string, 0, len(frequencyForWord))
	wordWidth, frequencyWidth := 0, 0
	for word, frequency := range frequencyForWord {
		words = append(words, word)
		if width := utf8.RuneCountIn(word); width > wordWidth {
			wordWidth = width
		}
		if width := len(fmt.Sprint(frequency)); width > frequencyWidth {
			frequencyWidth = width
		}
	}
	sort.Strings(words)
	fmt.Printf("%s   %s\n", "Word", "Frequency")
	for _, word := range words {
		fmt.Printf("%-*s%d\n", wordWidth, word, frequencyForWord[word])
	}
}
```

`reportWords()` 函数被调用以输出数据。我们希望输出按字母（最终是 Unicode 码点）排序，因此我们首先创建一个空的 `[]string` 来存储单词。我们还想知道长单词的字符宽度以及最高频率的宽度（即它有多少位数字），以便我们产生整齐的列输出。

一旦切片填充完毕，我们就设置它。我们不需要担心大小写敏感问题，因为所有的单词都是小写的（这在 `readUpdateFrequencies()` 函数中已完成）。

# 第 4 章 集合类型

对应的切片值。由于新 map 的值是切片，因此数据不会丢失，即使原始 map 有多个具有相同值的键也是。

```go
func reportByFrequency(wordsForFrequency map[int]string) {
	frequencies := make([]int, 0, len(wordsForFrequency))
	for frequency := range wordsForFrequency {
		frequencies = append(frequencies, frequency)
	}
	sort.Ints(frequencies)
	width := len(fmt.Sprint(frequencies[len(frequencies)-1]))
	fmt.Println("Frequency -> Words")
	for _, frequency := range frequencies {
		words := wordsForFrequency[frequency]
		sort.Strings(words)
		fmt.Printf("%d %s\n", width, frequency, strings.Join(words, ", "))
	}
}
```

该函数在结构上与 `reportWords()` 函数非常相似。它首先创建一个频率切片，然后对其进行顺序排序。接着，它计算出容纳最大频率所需的宽度，并将其作为第一列的宽度。接下来，它输出报告的标题。最后，它遍历频率，并输出每个频率以及对应的单词（单词按字母升序排列，如果频率有多个单词，则用逗号分隔）。

我们已经回顾了本章的两个完整示例，并对 Go 中指针的使用以及 Go 切片和 map 类型的强大性和并发性有了些见解。在下一章中，我们将学习如何创建自定义函数；这将为 Go 过程化编程奠基础。一旦涵盖了函数，我们就可以准备处理面向对象编程了，之后是并发编程。

## 4.5. 练习

共有五个练习题，每个练习都需要创建一个小型函数，并利用本章介绍的切片和 map 覆盖内容。我们把所有五个函数都放在同一个 `.go` 文件（`chap4_ans/chap4_ans.go`）中，并添加了一个使用所有这些函数的 `main()` 函数，以便于测试。（适当的测试将在后文中第 9 章，9.S.1.1.3，414页中介绍。）

- 1. 创建一个接受 `[]int` 并返回 `[]int` 的函数，该切片是原始切片的副本但去除了重复项。例如，给定参数 `[]int{9, 1, 9, 5, 4, 2, 1, 5, 4, 8, 8, 4, 3, 6, 9, 7, 5, 7}`，该函数应返回 `[]int{9, 1, 5, 4, 2, 8, 3, 6, 7}`。在 `chap4_ans.go` 解决方案文件中，该函数名为 `UniqueInts()`。该函数使用了复合字量语法而不是内置的 `make()` 函数，长度为 11 行。这应该很容易。

- 2. 创建一个接受 `[][]int`（即整数的二维切片）并返回单个 `[]int` 的函数，该切片包含二维切片第一个切片中的所有整数，然后是第二个切片，以此此类推。例如，该函数名为 `Flatten`：

```go
irregularMatrix := [][]int{{1, 2, 3, 4},
{5, 6, 7, 8},
{9, 10, 11},
{12, 13, 14, 15},
{16, 17, 18, 19, 20}}
slice := Flatten(irregularMatrix)
fmt.Printf("%d\n%v\n", len(slice), slice)
// 20: [1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20]
```

`chap4_ans.go` 中的 `Flatten()` 函数即使在内部切片长度不一致时（如 `irregularMatrix` 所示）也能正常工作，但确保其正常工作需要一点小技巧，这其实非常直观。

- 3. 创建一个接受 `[][]int` 和列数（`int`）并返回 `[]int` 的函数，其中每个切片的长度等于列数。例如，如果参数是 `[]int{1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20}`，这里是一些示例结果，每个结果前面都有传入的列数：

```
3 [[1 2 3] [4 5 6] [7 8 9] [10 11 12] [13 14 15] [16 17 18] [19 20 0]]
4 [[1 2 3 4] [5 6 7 8] [9 10 11 12] [13 14 15 16] [17 18 19 20]]
5 [[1 2 3 4 5] [6 7 8 9 10] [11 12 13 14 15] [16 17 18 19 20]]
6 [[1 2 3 4 5 6] [7 8 9 10 11] [12 13 14 15 16] [17 18 19 20 0]]
```

注意有 20 个整数，3 和 6 都不是倍数，因此我们在需要时在最后一个切片中填充了零，以保持所有列（即内部切片）的长度相同。`chap4_ans.go` 中的 `Make()` 函数长度为 12 行，并使用了一个辅助函数（7 行）。`Make()` 函数及其辅助函数需要一点思考才能正确，但并不困难。

- 4. 创建一个接受 `[]string` 并返回 `map[string]map[string]` 的函数，其键为组名，值是组的键和值的键值对 map。应该忽略空行和以 `;` 开头的行。每个组由单独占一行的括号指示，组的键和值由一行或多行 `key=value` 格式表示。这里是一个函数可以处理的 `[]string` 示例。

```go
data := []string{
  "",
  "[App]",
  "Vendor=Mozilla",
  "Name=Eclipse",
  "Profile=mozilla/firefox",
  "Version=3.5.16",
  "[Gecko]",
  "MinVersion=1.9.1",
  "MaxVersion=1.9.1",
  "[XRE]",
  "EnableProfileMigrator=0",
  "EnableExtensionManager=1",
}
```

给定这些数据，函数应该返回以下 map，我们对其进行了“美化打印”以便更容易查看结构。

```
[Gecko]: map[MinVersion: 1.9.1 MaxVersion: 1.9.1]
XRE: map[EnableProfileMigrator: 0 EnableExtensionManager: 1]
App: map[Vendor: Mozilla Profile: mozilla/firefox Name: Eclipse Version: 3.5.16]
```

`ParseIni()` 函数假设任何不在组范围内的键值对都属于 "General" 组。它长度为 24 行，可能需要一点小心才能正确实现。

# 5. 过程化编程

共有五个练习题，每个练习都需要创建一个小型函数，并利用本章介绍的切片和 map 覆盖内容。我们把所有五个函数都放在同一个 `.go` 文件（`chap4_ans/chap4_ans.go`）中，并添加了一个使用所有这些函数的 `main()` 函数，以便于测试。（适当的测试将在后文中第 9 章，9.S.1.1.3，414页中介绍。）

- 1. 创建一个接受 `[]int` 并返回 `[]int` 的函数，该切片是原始切片的副本但去除了重复项。例如，给定参数 `[]int{9, 1, 9, 5, 4, 2, 1, 5, 4, 8, 8, 4, 3, 6, 9, 7, 5, 7}`，该函数应返回 `[]int{9, 1, 5, 4, 2, 8, 3, 6, 7}`。在 `chap4_ans.go` 解决方案文件中，该函数名为 `UniqueInts()`。该函数使用了复合字量语法而不是内置的 `make()` 函数，长度为 11 行。这应该很容易。

- 2. 创建一个接受 `[][]int`（即整数的二维切片）并返回单个 `[]int` 的函数，该切片包含二维切片第一个切片中的所有整数，然后是第二个切片，以此此类推。例如，该函数名为 `Flatten`：
