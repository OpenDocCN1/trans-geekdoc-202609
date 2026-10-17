
正如输出所示，`MaxHeap` 实现帮助我们在每次出队操作中获取最大值项。这是实现优先队列的方法之一。如果需要，我们也可以一次性对整个堆进行排序，然后将排序后的数组用作优先队列。为此，我们可以实现一个称为堆排序的排序函数。它是计算机编程中最高效且最常用的排序机制之一。我们将在下一节探讨它。

## 使用堆排序

堆排序要求我们从给定的元素列表构建一个堆，然后持续检查堆属性，使整个堆始终保持排序状态。与常规堆在新插入的值满足条件后停止检查堆属性不同，在堆排序实现过程中，我们会为后续元素继续进行检查。堆排序的伪代码如下：

```
Heapsort(A as array) 

    BuildHeap(A) 

    for i = n-1 to 0 

        swap(A[0], A[i]) 

        n = n - 1 

        Heapify(A, 0) 



BuildHeap(A as array) 

    n = elements_in(A) 

    for i = floor(n/2) to 0 

        Heapify(A,i) 



Heapify(A as array, i as int) 

    left = 2i+1 

    right = 2i+2 

    max = i 



    if (left <= n) and (A[left] > A[i]) 

        max = left 



    if (right<=n) and (A[right] > A[max]) 

        max = right 



    if (max != i) 

        swap(A[i], A[max]) 

        Heapify(A, max) 
```

伪代码显示，每当我们尝试对元素列表进行排序时，起始过程取决于构建堆。每次向堆添加项目时，我们都会通过 `heapify` 函数检查其是否满足堆属性。堆构建完成后，我们检查所有元素的堆属性。现在让我们根据前面的伪代码实现堆排序：

```php
function heapSort(array &$a) { 

    $length = count($a); 

    buildHeap($a); 

    $heapSize = $length - 1; 

    for ($i = $heapSize; $i >= 0; $i--) { 

      $tmp = $a[0]; 

      $a[0] = $a[$heapSize]; 

      $a[$heapSize] = $tmp; 

      $heapSize--; 

      heapify($a, 0, $heapSize); 

    } 

} 



function buildHeap(array &$a) { 

    $length = count($a); 

    $heapSize = $length - 1; 

    for ($i = ($length / 2); $i >= 0; $i--) { 

        heapify($a, $i, $heapSize); 

    } 

} 



function heapify(array &$a, int $i, int $heapSize) { 

    $largest = $i; 

    $l = 2 * $i + 1; 

    $r = 2 * $i + 2; 

    if ($l <= $heapSize && $a[$l] > $a[$i]) { 

        $largest = $l; 

    } 



    if ($r <= $heapSize && $a[$r] > $a[$largest]) { 

        $largest = $r; 

    } 



    if ($largest != $i) { 

      $tmp = $a[$i]; 

      $a[$i] = $a[$largest]; 

      $a[$largest] = $tmp; 

      heapify($a, $largest, $heapSize); 

    } 

} 
```

现在让我们使用 `heapSort` 函数对数组进行排序。由于我们按引用传递参数，因此函数不返回任何内容。操作结束时，实际数组将被排序：

```php
$numbers = [37, 44, 34, 65, 26, 86, 143, 129, 9]; 

heapSort($numbers); 

echo implode("\t", $numbers); 
```

如果运行此代码，命令行将输出以下内容：

```
9       26      34      37      44      65      86      129     143
```

如果要将排序改为降序，只需更改 `heapify` 函数中的比较即可。如果考虑 `heapSort` 算法的时间和空间复杂度，会发现堆排序具有排序算法中最好的复杂度：

| 指标 | 复杂度 |
| --- | --- |
| 最佳时间复杂度 | `Ω(nlog(n))` |
| 最差时间复杂度 | `O(nlog(n))` |
| 平均时间复杂度 | `Θ(nlog(n))` |
| 空间复杂度（最差情况） | `O(1)` |

与归并排序相比，堆排序具有更好的空间复杂度。因此，许多开发者倾向于使用堆排序对项目列表进行排序。

## 使用 SplHeap、SplMaxHeap 和 SplMinHeap

如果不想实现自己的堆，可以使用标准 PHP 库（SPL）中的内置堆类。SPL 有三种不同的堆实现：通用堆 `SplHeap`、最大堆 `SplMaxHeap` 和最小堆 `SplMinHeap`。重要的是要注意，SPL 类在 PHP 7 上运行时不被认为性能很好。因此我们不会在这里详细探讨它们。我们将只关注一个示例，以便如果使用 PHP 7 以外的版本，可以使用这些内置类。让我们尝试一个使用 `SplMaxHeap` 的示例：

```php
$numbers = [37, 44, 34, 65, 26, 86, 143, 129, 9]; 



$heap = new SplMaxHeap; 



foreach ($numbers as $number) { 

    $heap->insert($number); 

} 



while (!$heap->isEmpty()) { 

    echo $heap->extract() . "\t"; 

}
```

由于我们使用了最大堆，预期输出为降序。以下是命令行的输出：

```
143     129     86      65      44      37      34      26      9
```

如果想反向排序，可以使用 `SplMinHeap`。

## 总结

在本章中，我们学习了另一种高效的数据结构——堆。使用堆实现优先队列被认为是最高效的实现。我们还学习了另一种高效的排序方法——堆排序，它可以通过堆数据结构实现。至此，我们结束了本书关于数据结构的讨论。在剩余章节中，我们将专注于高级算法、算法和数据结构的内置函数，以及最后的函数式数据结构。首先，我们将在下一章探索动态规划的世界。

## 使用高级技术解决问题

到目前为止，我们在本书中探讨了不同的数据结构和算法。我们尚未探索算法中一些最令人兴奋的领域。在计算机编程中，有许多高效的做事方法。本章将重点介绍一些关键的高级技术和概念。这些主题非常重要，甚至可以单独写成一本书。然而，我们将重点放在这些高级主题的基础理解上。当我们说高级主题时，指的是备忘录模式、动态规划、贪心算法、回溯、解谜、机器学习等。让我们在以下部分学习一些新的、令人兴奋的主题。

## 备忘录模式

备忘录模式是一种优化技术，我们存储之前昂贵操作的结果，并在不重复操作的情况下使用它们。它能显著加快解决方案的速度。当我们遇到具有重复子问题的问题时，可以轻松应用此技术存储这些结果，稍后使用而无需重复步骤。由于 PHP 对关联数组和动态数组属性有很好的支持，我们可以毫无问题地缓存结果。有一点必须记住：虽然我们通过缓存结果节省了时间，但需要更多内存来存储缓存中的这些结果。因此，我们必须在空间和内存之间做出权衡。现在，让我们重温第 5 章 *应用递归算法 - 递归* 中生成斐波那契数的递归示例。我们将修改该函数，添加一个计数器以了解函数被调用的次数，以及函数运行时间以获取第 30 个斐波那契数。代码如下：

## PHP 递归与备忘录模式优化

### 斐波那契数列的递归实现

```php
$startTime = microtime(); 

$count = 0;

function fibonacci(int $n): int { 
    global $count; 
    $count++; 
    if ($n == 0) { 
        return 1; 
    } else if ($n == 1) { 
        return 1; 
    } else { 
        return fibonacci($n - 1) + fibonacci($n - 2); 
    } 
} 

echo fibonacci(30) . "\n"; 
echo "Function called: " . $count . "\n"; 
$endTime = microtime(); 
echo "time =" . ($endTime - $startTime) . "\n";
```

输出结果如下（时间和结果可能因系统或 PHP 版本而异）：

```
1346269

Function called: 2692537

time =0.531349
```

第一个数字 `1346269` 是第 30 个斐波那契数，第二行显示 `fibonacci` 函数在生成第 30 个数时被调用了 2,692,537 次。整个过程耗时 0.5 秒（使用 PHP 的 `microtime` 函数）。如果生成第 50 个斐波那契数，函数调用次数将超过 400 亿次。根据斐波那契公式，计算 *n* 时通过 *n-1* 和 *n-2* 进行，而这些值在前面的步骤中已计算过，因此存在大量重复计算，严重影响时间和效率。

### 使用备忘录模式优化

我们可以将斐波那契结果存储在索引数组中，检查所需数字是否已计算。若已计算则直接使用，否则计算并存储结果。以下是使用备忘录模式的修改代码：

```php
$startTime = microtime(); 

$fibCache = []; 
$count = 0; 

function fibonacciMemoized(int $n): int { 
    global $fibCache; 
    global $count; 
    $count++; 
    if ($n == 0 || $n == 1) { 
        return 1; 
    } else {
        if (isset($fibCache[$n - 1])) { 
            $tmp = $fibCache[$n - 1]; 
        } else {
            $tmp = fibonacciMemoized($n - 1); 
            $fibCache[$n - 1] = $tmp; 
        } 

        if (isset($fibCache[$n - 2])) { 
            $tmp1 = $fibCache[$n - 2]; 
        } else { 
            $tmp1 = fibonacciMemoized($n - 2); 
            $fibCache[$n - 2] = $tmp1; 
        } 

        return $tmp + $tmp1; 
    } 
} 

echo fibonacciMemoized(30) . "\n"; 
echo "Function called: " . $count . "\n"; 

$endTime = microtime(); 
echo "time =" . ($endTime - $startTime) . "\n"; 
```

运行结果：

```
1346269

Function called: 31

time =5.299999999997E-5
```

**结果分析**：第 30 个斐波那契数相同，但函数调用次数从 270 万次降至 31 次，耗时仅 0.000053 秒，比非备忘录版本快 10,000 倍。

通过这个简单示例，我们可以看到在适用场景下利用备忘录模式可显著优化方案。备忘录模式适用于存在重复子问题或需利用前序计算结果的场景。虽然会占用额外空间存储部分计算数据，但能大幅提升性能。

## 模式匹配算法

模式匹配是日常最常见的任务之一。PHP 内置正则表达式支持，我们通常依赖正则表达式和内置字符串函数解决此类问题。PHP 提供现成函数 `strpos`，返回字符串在文本中首次出现的位置。因其仅返回首次出现位置，我们可尝试编写函数返回所有可能位置。

### 暴力匹配算法

首先探索暴力法：依次将实际字符串的每个字符与模式串的每个字符进行比对。实现函数如下：

```php
function strFindAll(string $pattern, string $txt): array { 
    $M = strlen($pattern); 
    $N = strlen($txt); 
    $positions = []; 

    for ($i = 0; $i <= $N - $M; $i++) { 
        for ($j = 0; $j < $M; $j++) 
            if ($txt[$i + $j] != $pattern[$j]) 
                break; 

        if ($j == $M) 
            $positions[] = $i; 
    }

    return $positions; 
} 
```

**算法逻辑**：从实际字符串位置 0 开始，一直检索到 `$N-$M` 位置（`$M` 为模式串长度）。即使最坏情况下无匹配，也无需搜索完整个字符串。

#### 调用示例

```php
$txt = "AABAACAADAABABBBAABAA"; 
$pattern = "AABA"; 
$matches = strFindAll($pattern, $txt); 

if ($matches) { 
    foreach ($matches as $pos) { 
        echo "Pattern found at index : " . $pos . "\n"; 
    } 
} 
```

输出结果：

```
Pattern found at index : 0

Pattern found at index : 9

Pattern found at index : 16
```

在 `$txt` 中可找到 3 处 `AABA` 模式：开头、中间、接近末尾。该算法时间复杂度为 `O((N - M) * M)`，其中 N 为文本长度，M 为模式长度。

### Knuth-Morris-Pratt (KMP) 算法实现

KMP 字符串匹配算法与暴力法相似，核心区别在于：KMP 利用部分匹配信息，在失配时决定停止匹配位置；可预计算模式可能存在的位置，减少重复比对。KMP 通过预计算表辅助搜索，提高效率。实现 KMP 需计算 **最长真前缀后缀** (`LPS`)。

#### 计算 LPS 数组

```php
function ComputeLPS(string $pattern, array &$lps) { 
    $len = 0; 
    $i = 1; 
    $M = strlen($pattern); 

    $lps[0] = 0; 

    while ($i < $M) { 
        if ($pattern[$i] == $pattern[$len]) { 
            $len++; 
            $lps[$i] = $len; 
            $i++; 
        } else { 
            if ($len != 0) { 
                $len = $lps[$len - 1]; 
            } else { 
                $lps[$i] = 0; 
                $i++; 
            } 
        } 
    } 
}
```

以模式 `AABA` 为例，其 LPS 数组为 `[0,1,0,1]`。下面编写 KMP 算法完整实现：
