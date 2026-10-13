
我们将以类似于其他两种排序的方式实现插入排序，但有一个细微的差别。这一次，我们将**按引用**传递数组。这样做，我们就不需要函数有任何返回值。如果我们愿意，也可以按值传递参数，并在函数结束时返回数组。这是相关代码：

```php
function insertionSort(array &$arr) { 

    $len = count($arr); 

    for ($i = 1; $i < $len; $i++) { 

      $key = $arr[$i]; 

      $j = $i - 1; 



      while($j >= 0 && $arr[$j] > $key) { 

          $arr[$j+1] = $arr[$j]; 

          $j--; 

      }      

      $arr[$j+1] = $key; 

    }     

}
```

参数数组通过引用（`&$arr`）传递给函数。因此，原始数组（而非其副本）将被直接修改。现在，我们想运行代码并检查输出。为此，我们必须运行以下代码：

```php
$arr = [20, 45, 93, 67, 10, 97, 52, 88, 33, 92];



insertionSort($arr);

echo implode(",", $arr);
```

这将产生与前两种情况相同的输出。唯一的区别是我们不期望函数返回任何数组，也不将其存储到任何新变量中。

如果我们按引用传递数组，则不必返回数组。传入的数组将在函数内部被修改。如何实现排序取决于我们的选择。

## 插入排序的复杂度

插入排序的复杂度与冒泡排序相似。与冒泡排序的基本区别在于交换次数远低于冒泡排序。以下是插入排序的复杂度：

| 最佳时间复杂度 || `Ω(n)` |
| --- | --- |
| 最差时间复杂度 || `O(n²)` |
| 平均时间复杂度 || `Θ(n²)` |
| 空间复杂度（最差情况） || `O(1)` |

## 理解用于排序的分治技术

到目前为止，我们探索的是对完整数字列表进行排序。结果是，我们每次都要比对一个庞大的数字列表。如果我们能以某种方式让列表变小，这个问题就能解决。分治法对此非常有帮助。使用这种方法，我们将一个问题分成两个或更多子问题或集合，先解决这些较小的问题，然后再将子问题的所有结果合并以获得最终结果。这就是所谓的分治法。

分治法能让我们高效地解决排序问题，并降低算法的复杂度。最流行的两种排序算法是归并排序和快速排序，它们都应用分治算法对项目列表进行排序，因此被认为是最好的排序算法。现在，我们将在下一节探索这两种算法。

## 理解归并排序

既然我们已经知道归并排序应用分治法来解决排序问题，我们需要找出两个过程来解决该问题。第一个是将问题集分成足够小、易于求解的问题，然后合并这些结果。我们将对分治部分采用递归方法。下图展示了如何采用分治方法。我们现在将考虑一组较小的数字 `20`、`45`、`93`、`67`、`97`、`52`、`88`、`33` 来解释分治部分：

![](Image00061.gif)

根据前面的图片，我们现在可以开始准备伪代码，它将包含两部分——分割和合并。以下是实现该功能的伪代码：

```text
func mergesort ( A : array of sortable items):

     n = length(A)      

     if ( n == 1 ) return a 



     var l1 as array = a[0] ... a[n/2] 

     var l2 as array = a[n/2+1] ... a[n] 



     l1 = mergesort( l1 ) 

     l2 = mergesort( l2 ) 



     return merge( l1, l2 ) 

end func



func merge( a: array, b : array )

     c = array



     while ( a and b have elements )

          if ( a[0] > b[0] )

               add b[0] to the end of c

               remove b[0] from b

          else

               add a[0] to the end of c

               remove a[0] from a

     end while



     while ( a has elements )

          add a[0] to the end of c

          remove a[0] from a

     end while



     while ( b has elements )

          add b[0] to the end of c

          remove b[0] from b

     return c

     end while

end func
```

伪代码的第一部分展示了分割过程。我们将项目数组不断分割，直到其大小达到 1。然后，我们开始使用 `merge` 函数合并结果。在 `merge` 函数中，我们有一个数组用于存储合并后的结果。正因如此，归并排序实际上比我们迄今为止看到的其他算法具有更高的空间复杂度。现在，让我们进入编码环节，使用 PHP 实现此伪代码。

## 实现归并排序

我们将首先编写分割部分，随后是合并或征服部分。PHP 有一些用于分割数组的内置函数。我们将使用 `array_slice` 函数来进行分割。代码如下：

```php
function mergeSort(array $arr): array { 

    $len = count($arr); 

    $mid = (int) $len / 2; 

    if ($len == 1) 

         return $arr; 



    $left  = mergeSort(array_slice($arr, 0, $mid)); 

    $right = mergeSort(array_slice($arr, $mid)); 



    return merge($left, $right); 

}
```

从代码中可以看出，我们以递归方式分割数组，直到数组大小变为 1。当数组大小为 1 时，我们开始向后合并，就像最后那张图片一样。这是 `merge` 函数的代码，它将接收两个数组，并按照我们的伪代码将它们合并为一个：

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

## 归并排序的复杂度

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

| 最佳时间复杂度 || `Ω(nlog(n))` |
| --- | --- |
| 最差时间复杂度 || `O(nlog(n))` |
| 平均时间复杂度 || `Θ(nlog(n))` |
| 空间复杂度（最差情况） || `O(n)` |

# 读累了记得休息一会哦~

