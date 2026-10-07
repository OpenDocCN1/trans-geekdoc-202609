

```go
package main

import "fmt"

func bubbleSort(numbers []int) {
  n := len(numbers)
  for i := 0; i < n; i++ {
    if sweep(numbers, i) {
      return
    }
  }
}

func sweep(numbers []int, currentPass int) bool {
  var idx int
  idxNext := idx + 1
  n := len(numbers)
  var swap bool

  for idxNext < (n - currentPass) {
    a := numbers[idx]
    b := numbers[idxNext]
    if a > b {
      numbers[idx] = b
      numbers[idxNext] = a
      swap = true
    }
    idx++
    idxNext = idx + 1
  }
  return swap
}

func main() {
  org := []int{1, 3, 2, 4, 8, 6, 7, 2, 3, 0}
  fmt.Println(org)
  bubbleSort(org)
  fmt.Println(org)
}
```

在列表 6 中，展示了一个用 Go 编写的冒泡排序示例。该排序算法遍历整数集合并在每轮遍历中交换值。根据列表的顺序，可能需要对集合进行多次遍历才能完成所有排序。

问题：`bubbleSort` 函数的负载工作是否适合乱序执行？我认为答案是否定的。可以将整数集合拆分成更短的列表，并对这些列表进行并发排序。然而，在完成所有并发工作后，没有高效的方法可以将这些较小的列表合并排序。这里有一个并发版本的冒泡排序示例。

## 列表 8

```go
func bubbleSortConcurrent(goroutines int, numbers []int) {
  totalNumbers := len(numbers)
  lastGoroutine := goroutines - 1
  stride := totalNumbers / goroutines

  var wg sync.WaitGroup
  wg.Add(goroutines)

  for g := 0; g < goroutines; g++ {
    go func(g int) {
      start := g * stride
      end := start + stride
      if g == lastGoroutine {
        end = totalNumbers
      }

      bubbleSort(numbers[start:end])
      wg.Done()
    }()
  }

  wg.Wait()

  // 哎，我们必须再次对整个列表排序。
  bubbleSort(numbers)
}
```

在列表 8 中展示了 `bubbleSortConcurrent` 函数，它是 `bubbleSort` 函数的并发版本。它使用多个 Goroutine 并发排序列表的部分。然而，你最终得到的是一个分块排序后的值列表。假设有一个包含 36 个数字的列表，按每组 12 个分组，如果不在第 25 行再次对整个列表进行排序，那么结果将如所示。

## 列表 9

| 之前 | 之后 |
| :--- | :--- |
| 51 15 57 87 10 10 85 90 32 98 53 | 10 10 15 25 32 51 53 57 85 87 90 98 |
| 91 82 84 97 67 37 71 94 26 2 81 79 | 2 26 37 67 71 79 81 82 84 91 94 97 |
| 66 70 93 86 19 81 52 75 85 10 87 49 | 10 19 49 52 66 70 75 81 85 86 87 93 |

由于冒泡排序的本质是遍历列表，第 25 行对 `bubbleSort` 的调用将抵消使用并发带来的任何潜在收益。对于冒泡排序，使用并发并不会带来性能提升。

## 读取文件

目前展示了两个 CPU 密集型负载，但 I/O 密集型负载呢？当 Goroutine 自然然地进入和退出等待状态时，语义会有何不同？让我们来看一个读取文件并执行文本搜索的 I/O 密集型负载。

第一个版本是名为 `find` 函数的顺序版本。

## 列表 10

```go
func find(topic string, docs []string) int {
  var found int
  for _, doc := range docs {
    items, err := read(doc)
    if err != nil {
      continue
    }
    for _, item := range items {
      if strings.Contains(item.Description, topic) {
        found++
      }
    }
  }
  return found
}
```

在列表 10 中展示了 `find` 的顺序版本。该函数遍历文档，读取每个文件，并在项目中检查是否存在该主题。

