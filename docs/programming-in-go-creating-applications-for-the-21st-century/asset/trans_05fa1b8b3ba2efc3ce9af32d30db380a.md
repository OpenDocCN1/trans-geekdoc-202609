

## 4.3. 映射

```go
for city, population := range populationCity {
  cityForPopulation[population] = city
}
fmt.Println(cityForPopulation)
map[12610000:Istanbul 11290000:Beijing 12690000:Mumbai 11620000:Karachi]
```

我们首先创建一个反转 map——由于 `populationCity` 的类型是 `map[string]int`，而 `cityForPopulation` map 的类型是 `map[int]string`。我们遍历原始 map，并使用原始 map 的值作为键、其键作为值，将项插入到反转 map 中。

当然，如果值并非全部唯一，map 的反转将会失败——本质上发生的情况是，遇到的某个唯一值的最后一次出现会被（作为值）存储在反转 map 中。这个问题可以通过创建一个具有多值值的反转 map 来解决，因此在这个示例中，类型为 `map[int][]string`（`int` 键和 `[]string` 值）。我们稍后将看到一个此方面的实际示例（§4.4.2）。

## 4.4. 示例

在本节中，我们将回顾两个小示例：第一个示例说明了一维和二维切片，第二个示例说明了 map，包括 map 值可能不唯一时的 map 反转，以及排序。

### 4.4.1. 示例：猜测分隔符

在某些情况下，我们可能会接收大量数据进行处理，其中每个文件每行一条记录，但不同的文件使用不同的分隔符（例如制表符或空白字符）。为了能够批量处理此类文件，我们需要能够确定每个文件所使用的分隔符。本节所示的 `guess_separator` 示例（在 `guess_separator/guess_separator.go` 文件中）尝试识别其被要求处理的文件的分隔符。以下是一个典型的运行示例：

```
$ ./guess_separator information.dat
tab-separated
Word Frequency
ability 1
about 3
```

该程序读取前五行（如果文件包含少于五行，则读取所有行），并利用这些行来猜测所使用的分隔符。一如既往，我们将回顾 `main()` 函数以及它调用的函数（除了一个未显示的函数），第一个处理是读取文件的前五行。

```go
func main() {
	if len(os.Args) == 1 || os.Args[1] == "-h" || os.Args[1] == "--help" {
		fmt.Printf("usage: %<file1> %<file2> [...<fileN>]\n",
		filepath.Base(os.Args[0]))
		os.Exit(1)
	}

	separators := []string{"\t", "*", " "}
	linesRead, lines := readToLines(os.Args[1], 5)
	counts := createCounts(lines, separators, linesRead)
	separator := guessSep(counts, separators, linesRead)
	report(separator)
}
```

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

