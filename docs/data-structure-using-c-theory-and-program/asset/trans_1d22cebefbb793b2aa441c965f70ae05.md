

# 第8章 搜索与排序

2. Ashenbut, R.L., External Sorting based on the radix principle, Theory of switching, Harvard University Press.

3. Bentley, J.L., and M.D. McElroy, Way of partitioning, software practice and experience, 23, pp. 1249-1265.

4. Betz, B.K., Memorandum, Minneapolis-Honeywell Router Co., 1956.

5. Bing-Chao Huang, Michael A. Langston, Practical in Merge, Communication of the ACM, 31, pp. 348-352.

6. Demuth, H.B., Ph.D. Thesis, Stanford University, A Sorting using Bubble sort principle with two tapes, 1956.

7. Frager, W.D., and A.C. McKeller, Multipartition quick sort, Journal of the ACM, 17,, pp. 496-497.

8. Friend, E.H., Quadric sort. 44, pp. 246-253.

9. Gilstad, R.L., Poly phase merge sort, processing of Eastern joint computer conference, 18, pp. 143-148.

10. Harlan and M Sobel, A Survey on external sorting techniques, technical report, University of Minnesota, No. 121, 1969.

11. Hildebrand, P., M. Hitzburg, H. Rising and J.Schwarz, in the word of sort, journal of ACM, 6, pp. 156-167.

12. Hoare, C.A., Quick sort, journal number 5 (1), pp. 10-15.

13. Hwang, F.K., and Lin, S., Binary Merge SICCOMP (Journal of SICCOMP), Society for Industrial and Applied Mathematics (SIAM), 1, pp. 31-39.

14. Incerpi, Janet, Sedgewick, Robert, How to sort a large collection? Journal of computer system and science, 31, pp. 210-224.

15. Isaac, E.J., and R.C.Singleton, Efficient partitioning method for quick sort, journal of ACM,3, pp. 169-174.

16. Knuth, D.E., The art of computer programming, 2nd Ed., 3. Sorting and searching, Stanford University, Addison-Wesley, New York, USA.

17. Knuth Donald E., The art of computer programming, 2nd Ed., Addison-Wesley, CA, USA.

18. Lumoto, N., Programming reels, Addison-Wesley, Reading MA, New York.

19. Sedgewick, Robert, let's make quick sort communication of ACM, 21, pp. 847-857.

20. Sedgewick, Robert, sorting algorithm for linear data, journal of algorithm, 7, pp. 159-173.

21. Shell, Donald, L., Better than N² sorting with sequential data storage, communication of the ACM, 2, 7, pp. 30-32.

22. Sobel, Sheldon, Oscillatory Sorting: An external sorting approach, journal of ACM, 9, pp. 327-375.

23. Tanner, R. Michael, Minnean merging and sorting: an algorithm, SIAM, journal of computing, 7, pp. 18-38.

24. Weiss, M.A., Improving the O(N²) sorting for sequential storage data, computer journal, 34, pp. 88-91.

25. Williams, J.W.J., Non-linear sorting with heap data structure, communication of the ACM, 6, pp. 347-358.

26. Noah, N.B., A technique of the partition exchange or quick sort on data stored on two tapes, ACM, 8, pp. 649-657.

![](img/3d5da05d64722faaa72fdc4daca105f9_408_0.png)

# 哈希技术

## 9.1 引言
我们已经见过了不同的搜索技术，其搜索时间基本上取决于元素的数量。顺序搜索、二分查找以及所有的搜索树完全依赖于元素的数量和涉及的键比较。假设所有元素都在一个大小为 n 的数组中。让我们假设所有键都是唯一的，且范围在 0 到 n-1 之间。现在我们根据键将记录存储在数组中，其中数组索引和键相同。现在，我们可以在常数时间内通过比较来访问记录。

## 9.2 哈希表
哈希表支持最高效的搜索类型之一：哈希。从根本上说，哈希表由一个数组，通过称为“键”（key）的特殊索引来访问数据。哈希表背后的思想是使用哈希函数在所有可能的键集合与数组位置之间建立映射关系。哈希函数接受一个键并返回其哈希值。键的类型各异，但代码始终是整数。由于计算哈希值和对数组索引都可以在常数时间内完成，哈希的妙之处在于它保证没有两个键会生成相同的哈希代码，生成的哈希表被称为直接寻址表。这是理想的，但在实践中很少能实现直接寻址。通常，哈希表中的条目相对于所有可能的键范围很小。因此，大多数哈希函数会将某些键映射到表中的相同位置。当两个键映射到相同位置时，它们就会冲突（collision）。良好的哈希函数会尽可能地减少冲突，但我们仍然必须准备好处理它们。

## 9.3 哈希表的应用

哈希表的一些应用包括：

### 1. 数据库系统
通常，数据库系统试图在顺序访问和随机访问两种访问方法之间进行优化。哈希表是高效随机访问部分，因为提供了一种在常时间内定位数据的方法。

### 2. 符号表
编译器用于维护程序中符号信息的表。编译器频繁访问符号信息。因此，以非常高效的方式实现符号表至关重要。

### 3. 标记缓冲区（Tagged Buffers）
一种与机器无关的方式存储和检索数据的机制。每个数据成员存储在缓冲器的固定偏移处。哈希表存储在缓冲区中，以便能够快速确定每个标记成员的位置。标记缓冲区的一个用途是跨网络发送结构化数据。

### 4. 字典
支持添加、删除和搜索的数据结构。

## 9.4 哈希化
哈希是一种将值范围转换为索引范围的技术。我们使用模运算来获取哈希值。

## 9.5 哈希函数
哈希函数是将固定大小的数据映射到范围的函数。我们希望这些元素能够分布开。

## 良好哈希函数的特征
良好的函数具有四个主要特征：
- 哈希值完全由数据决定。
- 哈希函数使用了所有输入数据。
- 哈希函数在数组中均匀分布元素。

## 9.6 哈希函数的类型

### 1. 除法法
所有哈希方法中，最简单的可能是除法法，它规定将整数 $x$ 除以 $M$，然后留对模 $M$ 的余数。在这种情况下，哈希函数为
```
h(x) = x \mod M
```

