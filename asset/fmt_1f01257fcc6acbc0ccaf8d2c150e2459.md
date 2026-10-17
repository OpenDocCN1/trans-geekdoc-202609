
```php
function merge(array $left, array $right): array { 

    $combined = []; 

    $countLeft = count($left); 

    $countRight = count($right); 

    $leftIndex = $rightIndex = 0; 



    while ($leftIndex < $countLeft && $rightIndex < $countRight) { 

      if ($left[$leftIndex] > $right[$rightIndex]) { 

          $combined[] = $right[$rightIndex]; 

          $rightIndex++; 

      } else { 

          $combined[] = $left[$leftIndex]; 

          $leftIndex++; 

      } 

    } 

    while ($leftIndex < $countLeft) { 

      $combined[] = $left[$leftIndex]; 

      $leftIndex++; 

    } 

    while ($rightIndex < $countRight) { 

      $combined[] = $right[$rightIndex]; 

      $rightIndex++; 

    } 

    return $combined;

}
```

代码现已完成，因为我们已合并两个提供的数组，并将合并结果返回给 `mergeSort` 函数。我们刚刚以递归方式解决了该问题。如果你运行以下代码，将得到一个升序排列的项目列表：

```php
$arr = [20, 45, 93, 67, 10, 97, 52, 88, 33, 92];

$arr = mergeSort($arr);

echo implode(",", $arr);
```

现在，让我们探索归并排序的复杂度。

### 归并排序的复杂度

由于归并排序遵循分治法，我们必须同时处理这两方面的复杂度。对于大小为 n 的数组，我们首先需要将数组分成两半，然后将它们合并以得到一个大小为 n 的数组。这可以用 `T(n)` 表示为：

```text
T(n)     = T(n/2) + T(n/2) + n    , for N>1 with T(1) = 0 

         = 2 T(n/2)+n 



T(n)/n   = 2 T(n/2)/n + 1              // divide both side by n 

         = T(n/2)/(n/2)  + 1                  

         = T(n/4)/(n/4)  + 1+ 1        // telescoping 

         = T(n/8)/(n/8)  + 1+ 1 + 1      // again telescoping 

         = ...... 

         = T(n/n)/(n/n)  + 1 + 1 + 1 + ....... + 1 

         = log (n)                     // since T(1) = 0      



So T(n)  = n log (n)                   // multiply both side with n 
```

因此，归并排序的复杂度为 `O(n log(n))`。以下是归并排序的复杂度图表：

| 最佳时间复杂度 | `Ω(nlog(n))` |
| --- | --- |
| 最差时间复杂度 | `O(nlog(n))` |
| 平均时间复杂度 | `Θ(nlog(n))` |
| 空间复杂度（最差情况） | `O(n)` |

## 读累了记得休息一会哦~

**公众号：古德猫宁李**

* 电子书搜索下载
* 书单分享
* 书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

* 电子书搜索下载
* 电子书打包资源分享
* 学习资源分享

## 理解快速排序

快速排序是另一种采用分治法的高效排序算法。虽然它不像归并排序那样分成相等的两半，但它会创建动态分区来对数据进行排序。快速排序的工作原理如下：

1. 从数组中选取一个随机值，我们称之为 `pivot`（基准值/枢轴）。
2. 重新排序数组，使得小于 `pivot` 的项移至其左侧，大于或等于 `pivot` 的项移至其右侧。这称为分区。
3. 递归调用*步骤 1* 和 *2* 来处理两个子数组（`pivot` 的左侧和右侧），直到所有项都排好序。

从数组中选取 `pivot` 有很多方法。我们可以选择数组最左侧的项，也可以选择最右侧的项。在这两种情况下，如果数组已经有序，都会导致最坏情况的复杂度。选择一个好的 `pivot` 可以提高算法的效率。分区也有几种不同的方法。我们将讲解 *Hoare 分区法*（Hoare Partition），与其他分区方法相比，它进行的交换操作相对较少。以下是我们的快速排序伪代码算法。我们将进行原地排序，因此不需要额外的空间：

```
procedure Quicksort(A : array, p : int, r : int)

    if (p < r)

       q = Partition(A, p, r)

       Quicksort(A, p, q)

       Quicksort(A, q + 1, r)

    end if

end procedure



procedure Partition(A : array, p : int, r : int)

    pivot = A[p]

    i = p - 1

    j = r + 1

    while (true)

           do

            i := i + 1

           while A[i] < pivot    

           do

             j := j - 1

           while A[j] > pivot



      if i < j then

          swap A[i] with A[j]

      else

          return j

      end if

   end while

end procedure
```

我们使用第一个元素作为 `pivot` 元素。也可以选择最后一个元素，或取中位数来选择 `pivot` 元素。现在让我们使用 PHP 实现该算法。

## 实现快速排序

正如伪代码所示，我们将用两个函数来实现快速排序：一个函数执行快速排序本身，另一个用于分区。以下是执行快速排序的实现：

```php
function quickSort(array &$arr, int $p, int $r) {

  if ($p < $r) {

    $q = partition($arr, $p, $r);

    quickSort($arr, $p, $q);

    quickSort($arr, $q + 1, $r);

  }

}
```

以下是执行分区的实现：

```php
function partition(array &$arr, int $p, int $r) { 

  $pivot = $arr[$p]; 

  $i = $p - 1; 

  $j = $r + 1; 

  while (true) 

  { 

   do { 

    $i++; 

   } while ($arr[$i] < $pivot && $arr[$i] != $pivot); 

   do { 

    $j--; 

   } while ($arr[$j] > $pivot && $arr[$j] != $pivot); 



   if ($i < $j) { 

    $temp = $arr[$i]; 

    $arr[$i] = $arr[$j]; 

    $arr[$j] = $temp; 

   } else { 

    return $j; 

      } 

  } 

}



$arr = [20, 45, 93, 67, 10, 97, 52, 88, 33, 92]; 



quickSort($arr, 0, count($arr) - 1); 

echo implode(",", $arr);
```

如果我们用图示来展示分区中的 `pivot` 和排序过程，可以看到下图。为简单起见，我们仅展示发生交换的步骤：

![](img/Image00062.gif)

## 快速排序的复杂度

快速排序的最坏情况复杂度可能类似于冒泡排序。`pivot` 的选择正是导致这种情况的原因。以下是快速排序的复杂度图表：

| 最佳时间复杂度 | `Ω(nlog(n))` |
| --- | --- |
| 最坏时间复杂度 | `O(n²)` |
| 平均时间复杂度 | `Θ(nlog(n))` |
| 空间复杂度（最坏情况） | `O(log(n))` |

## 理解桶排序

桶排序也称为箱排序。桶排序是一种分布式排序系统，其中数组元素被放置在不同的桶中。然后通过另一种排序算法，或通过递归应用桶排序，对每个桶单独进行排序。使用 PHP 实现的桶排序如下所示：

```php
function bucketSort(array &$data) { 



    $n = count($data); 

    if ($n <= 0) 

         return;                          



    $min = min($data); 

    $max = max($data); 

    $bucket = []; 

    $bLen = $max - $min + 1; 



    $bucket = array_fill(0, $bLen, []); 



    for ($i = 0; $i < $n; $i++) { 

         array_push($bucket[$data[$i] - $min], $data[$i]); 

    } 



    $k = 0; 

    for ($i = 0; $i < $bLen; $i++) {

         $bCount = count($bucket[$i]);



      for ($j = 0; $j < $bCount; $j++) { 

          $data[$k] = $bucket[$i][$j];

          $k++;

      }

    }

} 
```

桶排序的时间复杂度相较于其他基于比较的排序算法要好得多。以下是桶排序的复杂度：

| 最佳时间复杂度 | `Ω(n+k)` |
| --- | --- |
| 最坏时间复杂度 | `O(n²)` |
| 平均时间复杂度 | `Θ(n+k)` |
| 空间复杂度（最坏情况） | `O(n)` |

## 使用 PHP 内置排序函数

PHP 拥有丰富的预定义函数库，其中也包含不同的排序函数。它提供了不同的函数，按值或按键/索引对数组中的项目列表进行排序。我们在排序时也可以保留数组值与其各自键的关联。PHP 的另一个重要功能是用于排序多维数组的内置函数。以下是这些函数的总结：

| 函数名 | 用途 |
| --- | --- |
| `sort()` | 按升序对数组排序。不保留值/键关联。 |
| `rsort()` | 按降序/逆序对数组排序。不保留索引/键关联。 |
| `asort()` | 对数组排序并保持索引关联。 |
| `arsort()` | 按逆序对数组排序并保持索引关联。 |
| `ksort()` | 按键对数组排序。它保持键到数据的关联。这主要用于关联数组。 |
| `krsort()` | 按键逆序对数组排序。 |
| `natsort()` | 使用“自然排序”算法对数组排序，并保持值/键关联。 |
| `natcasesort()` | 使用不区分大小写的“自然排序”算法对数组排序，并保持值/键关联。 |
| `usort()` | 使用用户定义的比较函数按值对数组排序，不保留值/键关联。第二个参数是用于比较的可调用函数。 |
| `uksort()` | 使用用户定义的比较函数按键对数组排序，并保持值/键关联。第二个参数是用于比较的可调用函数。 |
| `uasort()` | 使用用户定义的比较函数按值对数组排序，并保持值/键关联。第二个参数是用于比较的可调用函数。 |

对于 `sort`、`rsort`、`ksort`、`krsort`、`asort` 和 `arsort`，可用以下排序标志：

* `SORT_REGULAR`：按原样比较项目（不改变类型）
* `SORT_NUMERIC`：按数值比较项目
* `SORT_STRING`：按字符串比较项目
* `SORT_LOCALE_STRING`：按字符串比较项目，基于当前区域设置
* `SORT_NATURAL`：使用“自然排序”按字符串比较项目

## 总结

在本章中，您学习了不同的排序算法。排序是我们开发过程中不可或缺的一部分，了解不同排序算法及其复杂度将帮助我们根据问题集决定最佳的排序算法选择。还有其他排序算法，可在网上查找以供进一步学习。我们特意没有在本章涵盖堆排序，因为我们将在*第 10 章*讨论它。在下一章中，我们将讨论算法中另一个重要主题——搜索。

# 探索搜索选项

## 搜索算法

除了排序，搜索是编程世界中最常用的算法之一。无论我们是在搜索电话簿、电子邮件、数据库还是文件，我们实际上都是在执行某种搜索技术来定位我们想要查找的项目。搜索和排序是编程中最重要的两个组成部分，这一点至关重要。在本章中，您将学习不同的搜索技术及其效率。我们还将学习搜索树数据结构的不同方法。

### 线性搜索

执行搜索最常见的方法之一是将每个项目与我们要查找的项目进行比较。这被称为线性搜索或顺序搜索。这是执行搜索最基本的方法。如果我们认为列表中有 `n` 个项目，在最坏的情况下，我们必须搜索 `n` 个项目才能找到特定的项目。我们可以遍历列表或数组来查找项目。让我们考虑以下示例：

```php
function search(array $numbers, int $needle): bool {

    $totalItems = count($numbers);

    for ($i = 0; $i < $totalItems; $i++) {

        if ($numbers[$i] === $needle) {

            return TRUE;

        }

    }

    return FALSE;

}
```

我们有一个名为 `search()` 的函数，它接受两个参数。一个是数字列表，另一个是我们在列表中要查找的数字。我们运行一个 `for` 循环来遍历列表中的每个项目并将它们与我们的项目进行比较。如果找到匹配项，我们返回 `TRUE` 并不继续搜索。然而，如果循环结束仍未找到任何内容，我们在函数定义的末尾返回 `FALSE`。让我们使用 `search()` 函数通过以下程序来查找某些内容：

```php
$numbers = range(1, 200, 5);

if (search($numbers, 31)) {

    echo "Found";

} else {

    echo "Not found";

}
```

在这里，我们使用 PHP 的内置函数 `range()` 生成一个随机数组，范围为 1 到 200（含）。每个项目之间将有 5 的间隔，如 1、6、11、16 等；然后我们搜索 31，它在列表中，因为我们有 6、11、16、21、26、31 等。然而，如果我们想搜索 32 或 33，则找不到该项目。因此，对于这种情况，我们的输出将是 `Found`。

这里我们需要记住一点：我们不关心列表是否按任何特定顺序排列或以特定方式组织。如果我们要查找的项目在第一个位置，那将是最好的结果。最坏的结果可能是最后一个项目或列表中不存在的项目。在这两种情况下，我们都必须遍历列表中的所有 `n` 个项目。以下是线性/顺序搜索的复杂度：

| 复杂度 | 值 |
| :--- | :--- |
| 最佳时间复杂度 | `O(1)` |
| 最坏时间复杂度 | `O(n)` |
| 平均时间复杂度 | `O(n)` |
| 空间复杂度（最坏情况） | `O(1)` |

正如我们所见，线性搜索的平均或最坏时间复杂度为 `O(n)`，这不会因我们如何排列项目列表而改变。现在，如果数组中的项目按特定顺序排序，那么我们可能不必进行线性搜索，通过进行选择性或计算性搜索可以获得更好的结果。最流行且众所周知的搜索算法是“二分搜索”。是的，它听起来像您在第 6 章 *理解和实现树* 中学到的二叉搜索树，但我们甚至可以在不构建二叉搜索树的情况下使用该算法。那么，让我们来探索一下。

### 二分搜索

二分搜索是编程世界中非常流行的搜索算法。在顺序搜索中，我们从开头开始扫描每个项目以找到所需的项目。然而，如果列表已经排序，那么我们不需要从列表的开头或结尾开始搜索。在二分搜索算法中，我们从列表的中间开始，检查中间的项目比我们要查找的项目小还是大，并决定往哪个方向走。这样，我们将列表减半并完全丢弃其中一半，就像下图所示：

![](img/Image00063.jpg)
