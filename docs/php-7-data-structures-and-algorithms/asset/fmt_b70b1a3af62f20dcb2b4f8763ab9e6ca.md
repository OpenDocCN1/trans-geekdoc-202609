
As we can see, we have reduced the number of comparisons from `90` to `38` with our improvement. So, we can certainly boost up the algorithm with some improvements to reduce the number of comparisons required.

# Understanding selection sort

Selection sort is another comparison-based sorting algorithm, which looks similar to bubble sort. The biggest difference is that it takes fewer swapping than bubble sort. In selection sort, we first find the minimum/maximum item of the array and place it in the first place. If we are sorting in descending order, then we will take the maximum value from the array. For ascending order, we will take the minimum value. In the second iteration, we will find the second-most maximum or minimum value of the array and place it in second place. This goes on until we place each number into a correctly sorted position. This is known as selection sort. The pseudocode for selection sort looks like this:

```
procedure selectionSort( A : list of sortable items )

   n = length(A)

   for i = 1 to n inclusive do

     min = i

     for j = i+1 to n inclusive do

       if A[j] < A[min] then

         min = j

       end if

     end for



     if min != i

        swap(a[i],a[min])

     end if



   end for

end procedure
```

If we look at the preceding algorithm, we can see that, after iteration one in the outer loop, the first minimum item is stored in position one. During the first iteration, we selected the first item and then found the minimum value from the remaining items (from 2 to `n`). We assumed that the first item is the minimum value. If we find another minimum value, we would mark its position until we have scanned the remaining list and found a new minimum value. If no minimum value is found, then our assumption is correct, and that is indeed the minimum value. Here is a picture illustrating our `20`, `45`, `93`, `67`, `10`, `97`, `52`, `88`, `33`, `92` arrays during the first two steps in selection sort:

![](Image00059.gif)

As we can see in the preceding image, we started with the first item in the list, which is `20`. Then, we found the minimum value from the rest of the array, which is `10`. At the end of the first iteration, we just swapped the values from two places (marked by arrows). As a result, at the end of the first iteration, we have the minimum value from the array stored in the first place. Then, we pointed to the next item, which is `45`, and started finding the next smallest items compared to `45` from the right side of its position. We found `20` from the remaining items (as shown by two arrows). At the end of the second iteration, we are just swapping the second position number to the newly found smallest one from the remainder of the list. This continues until the last element, and, at the end of the process, we have a sorted list of arrays. Let's now convert the pseudocode into a PHP code.

# 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

# Implementing selection sort

We will take the same approach as the bubble sort where our implementation will take an array as an argument and return a sorted array. Here is the implementation in PHP:

```
function selectionSort(array $arr): array {

    $len = count($arr);

    for ($i = 0; $i < $len; $i++) {

      $min = $i;

      for ($j = $i+1; $j < $len; $j++) {

          if ($arr[$j] < $arr[$min]) {

            $min = $j;

          }

      }



      if ($min != $i) {

          $tmp = $arr[$i];

          $arr[$i] = $arr[$min];

          $arr[$min] = $tmp;

      }

    }

    return $arr;

}
```

As can be seen, this is the simplest way to sort an array in ascending order. If you want to do it in descending order, we just need to change the comparison `$arr[$j] < $arr[$min]` to `$arr[$j] > $arr[$min]` and replace `$min` with `$max`.

# Complexity of selection sort

Selection sort also looks similar to bubble sort and has two `for` loops with 0 to `n`. The basic difference between bubble sort and selection sort is that, selection sort makes maximum `n-1` number of swapping, whereas bubble sort can have `n*n` number of swapping, in the worst case scenario. However, in the selection sort, the best case, worst case, and average case have similar complexity. Here is the complexity chart for selection sort:

| Best time complexity | `Ω(n²)` |
| --- | --- |
| Worst time complexity | `O(n²)` |
| Average time complexity | `Θ(n²)` |
| Space complexity (worst case) | `O(1)` |

# Understanding insertion Sort

So far, we have seen two comparison-based sorting algorithms. Now, we will explore another sorting algorithm that is somewhat efficient compared to the previous two. We are talking about the insertion sort. It has the simplest implementation compared to the other two sorting algorithms we have just seen. If the number of items is smaller, insertion sort works better than bubble sort and selection sort. If the data set is large, then it becomes inefficient, like bubble sort. Since the swapping is almost linear for insertion sort, it is recommended that you use insertion sort instead of bubble sort and selection sort.

As the name suggests, insertion sort works on the principle of inserting the number to its correct place on the left-hand side. It starts from the second item of the array and checks whether the items that are left to it are smaller than the current value or not. If so, it shifts the item and stores the smaller item in its correct position. Then, it moves to the next item, and the same principle continues until the full array is sorted. The pseudocode for insertion sort looks like this:

```
procedure insertionSort( A : list of sortable items )

   n = length(A)

   for i = 1 to n inclusive do

     key = A[i]

     j = i - 1

     while j >= 0 and A[j] > key   do

       A[j+1] = A[j]

       j--

     end while



     A[j+1] = key



   end for

end procedure
```

If we consider our previous list of numbers used for bubble sort and selection sort, then we will have the following scenario for which we must do insertion sort.

The elements of our array were: `20`, `45`, `93`, `67`, `10`, `97`, `52`, `88`, `33`, `92`.

Let's start with the second item, which is `45`. Now, we will start from the first item to the left of `45` and go to the beginning of the array to see whether there is a value greater than `45` on the left. As there is only `20`, no insertion is required as the item so far is sorted until the second element (`20`, `45`). Now, we will move our pointer to `93`, and it starts again, comparing left of the array starting from `45` and search if the value is bigger. Since `45` is not bigger than `93`, it stops there, as previously, we concluded that the first two items are already sorted. Now, we have the first three items (`20`, `45`, `93`) sorted. Next, we have `67`, and we start again by comparing from the left of the numbers. The first number to the left is `93`, which is bigger, so it has to move one place. We move `93` to the position that was held by `67`. Then, we move to the next item to the left of it, which is `45`. `45` is smaller than `67`, and no further comparison is required. Now, we will insert `67` at the position that was held by `93` and `93` will have to be moved to `67`'s position. This continues until the full array is sorted. This image illustrates the full sorting process using insertion sort at each step:

![](Image00060.gif)

# Implementing insertion sort
