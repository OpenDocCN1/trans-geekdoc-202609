
-   [Listing 1.2](#ch01.xhtml#list1.2) 显示 `loop1.py` 的内容，演示如何遍历 NumPy 数组和 Python 列表的元素。

***LISTING 1.2: loop1.py***

```python
import numpy as np
list = [1,2,3]
arr1 = np.array([1,2,3])
for e in list:
    print(e)
for e in arr1:
    print(e)
```

[Listing 1.2](#ch01.xhtml#list1.2) 初始化变量 `list`，它是一个 Python 列表，同时初始化变量 `arr1`，它是一个 NumPy 数组。[Listing 1.2](#ch01.xhtml#list1.2) 的下一部分包含两个循环，分别遍历 `list` 和 `arr1` 的元素。可以看到，两个循环的语法完全相同。执行 [Listing 1.2](#ch01.xhtml#list1.2) 的输出如下：

1 2 3 1 2 3 

-   [Listing 1.3](#ch01.xhtml#list1.3) 显示 `append1.py` 的内容，演示如何向 NumPy 数组和 Python 列表中追加元素。

***LISTING 1.3: append1.py***

```python
import numpy as np
arr1 = np.array([1,2,3])  # 这些操作不工作：#arr1.append(4) #arr1 = arr1 + [5]
arr1 = np.append(arr1,4)
arr1 = np.append(arr1,[5])
for e in arr1:
    print(e)
arr2 = arr1 + arr1
for e in arr2:
    print(e)
```

[Listing 1.3](#ch01.xhtml#list1.3) 初始化变量 `list`（Python 列表）和变量 `arr1`（NumPy 数组）。[Listing 1.3](#ch01.xhtml#list1.3) 的输出如下：

1 2 3 4 5 2 4 6 8 10 

-   [Listing 1.4](#ch01.xhtml#list1.4) 显示 `append2.py` 的内容，演示另一种向 NumPy 数组和 Python 列表中追加元素的示例。

***LISTING 1.4: append2.py***

```python
import numpy as np
arr1 = np.array([1,2,3])
arr1 = np.append(arr1,4)
for e in arr1:
    print(e)
arr2 = arr1 + arr1
for e in arr2:
    print(e)
```

[Listing 1.4](#ch01.xhtml#list1.4) 初始化变量 `arr1`（NumPy 数组）。请注意，NumPy 数组没有“append”方法，该方法是通过 NumPy 本身提供的。再次注意，Python 列表和 NumPy 数组之间的一个区别在于，“+”运算符对 Python 列表进行连接，而在 NumPy 数组中，该运算符会使数组元素翻倍。执行 [Listing 1.4](#ch01.xhtml#list1.4) 的输出如下：

4 2 4 6 

-   [Listing 1.5](#ch01.xhtml#list1.5) 显示 `multiply1.py` 的内容，演示如何对 Python 列表和 NumPy 数组中的元素进行乘法运算。

***LISTING 1.5: multiply1.py***

```python
import numpy as np
list1 = [1,2,3]
arr1 = np.array([1,2,3])
print('list: ',list1)
print('arr1: ',arr1)
print('2*list:',2*list)
print('2*arr1:',2*arr1)
```

[Listing 1.5](#ch01.xhtml#list1.5) 包含一个名为 `list` 的 Python 列表和一个名为 `arr1` 的 NumPy 数组。`print()` 语句显示 `list` 和 `arr1` 的内容，以及对 `list1` 和 `arr1` 进行“翻倍”后的结果。请记住，对 Python 列表进行“翻倍”与对 NumPy 数组进行“翻倍”不同，这一点在执行 [Listing 1.5](#ch01.xhtml#list1.5) 时的输出中可见：

('list: ', [1, 2, 3]) ('arr1: ', array([1, 2, 3])) ('2*list:', [1, 2, 3, 1, 2, 3]) ('2*arr1:', array([2, 4, 6])) 

-   [Listing 1.6](#ch01.xhtml#list1.6) 显示 `double_list1.py` 的内容，演示一种在 Python 列表中翻倍元素的方法。

***LISTING 1.6: double_list1.py***

```python
import numpy as np
list1 = [1,2,3]
list2 = []
for e in list1:
    list2.append(2*e)
print('list1:',list1)
print('list2:',list2)
```

[Listing 1.6](#ch01.xhtml#list1.6) 包含一个名为 `list1` 的 Python 列表和一个空的 Python 列表 `list2`。下一段代码遍历 `list1` 的元素并将其追加到 `list2`。两条 `print()` 语句显示 `list1` 和 `list2` 的内容，表明它们相同。执行 [Listing 1.6](#ch01.xhtml#list1.6) 的输出如下：

('list: ', [1, 2, 3]) ('list2:', [2, 4, 6]) 

-   [Listing 1.7](#ch01.xhtml#list1.7) 显示 `exponent_list1.py` 的内容，演示如何计算 Python 列表中元素的指数。

***LISTING 1.7: exponent_list1.py***

```python
import numpy as np
list1 = [1,2,3]
list2 = []
for e in list1:
    list2.append(e*e)  # e*e = squared
print('list1:',list1)
print('list2:',list2)
```

[Listing 1.7](#ch01.xhtml#list1.7) 包含一个名为 `list1` 的 Python 列表和一个空的 NumPy 列表 `list2`。下一段代码遍历 `list1` 的元素，并将每个元素的平方追加到 `list2`。两条 `print()` 语句显示 `list1` 和 `list2` 的内容。执行 [Listing 1.7](#ch01.xhtml#list1.7) 的输出如下：

('list1:', [1, 2, 3]) ('list2:', [1, 4, 9]) 

-   [Listing 1.8](#ch01.xhtml#list1.8) 显示 `exponent_array1.py` 的内容，演示如何计算 NumPy 数组中元素的指数。

***LISTING 1.8: exponent_array1.py***

```python
import numpy as np
arr1 = np.array([1,2,3])
arr2 = arr1**2
arr3 = arr1**3
print('arr1:',arr1)
print('arr2:',arr2)
print('arr3:',arr3)
```

[Listing 1.8](#ch01.xhtml#list1.8) 包含一个名为 `arr1` 的 NumPy 数组，随后是两个名为 `arr2` 和 `arr3` 的 NumPy 数组。请注意，`arr2` 以 `arr1` 元素的平方初始化，`arr3` 以 `arr1` 元素的立方初始化。三条 `print()` 语句显示 `arr1`、`arr2` 和 `arr3` 的内容。执行 [Listing 1.8](#ch01.xhtml#list1.8) 的输出如下：

('arr1:', array([1, 2, 3])) ('arr2:', array([1, 4, 9])) ('arr3:', array([ 1,  8, 27])) 

-   [Listing 1.9](#ch01.xhtml#list1.9) 显示 `mathops_array1.py` 的内容，演示如何对 NumPy 数组中的元素进行数学运算（平方根、对数、指数）。

***LISTING 1.9: mathops_array1.py***

```python
import numpy as np
arr1 = np.array([1,2,3])
sqrt = np.sqrt(arr1)
log1 = np.log(arr1)
exp1 = np.exp(arr1)
print('sqrt:',sqrt)
print('log1:',log1)
print('exp1:',exp1)
```

[Listing 1.9](#ch01.xhtml#list1.9) 包含一个名为 `arr1` 的 NumPy 数组，随后是三个名为 `sqrt`、`log1` 和 `exp1` 的 NumPy 数组，分别初始化为 `arr1` 元素的平方根、对数和指数。三条 `print()` 语句显示 `sqrt`、`log1` 和 `exp1` 的内容。执行 [Listing 1.9](#ch01.xhtml#list1.9) 的输出如下：

('sqrt:', array([1.        , 1.41421356, 1.73205081])) ('log1:', array([0.        , 0.69314718, 1.09861229])) ('exp1:', array([2.71828183, 7.3890561,  20.08553692])) 

-   [Listing 1.10](#ch01.xhtml#list1.10) 显示 `npsubarray2.py` 的内容，演示如何使用“-1”来表示 NumPy 数组中除最后一个元素之外的子范围。

***LISTING 1.10: npsubarray2.py***

```python
import numpy as np
# -1 => "all *except* the last element in . . ." (row or col)
arr1 = np.array([1,2,3,4,5])
print('arr1:',arr1)
print('arr1[0:-1]:',arr1[0:-1])
print('arr1[1:-1]:',arr1[1:-1])
print('arr1[::-1]:', arr1[::-1])  # reverse!
```

[Listing 1.10](#ch01.xhtml#list1.10) 包含一个名为 `arr1` 的 NumPy 数组，随后是四条 `print` 语句，分别显示 `arr1` 的不同子范围。执行 [Listing 1.10](#ch01.xhtml#list1.10) 的输出如下：

('arr1:',       array([1, 2, 3, 4, 5])) ('arr1[0:-1]:', array([1, 2, 3, 4])) ('arr1[1:-1]:', array([2, 3, 4])) ('arr1[::-1]:', array([5, 4, 3, 2, 1])) 

-   [Listing 1.11](#ch01.xhtml#list1.11) 显示 `np2darray2.py` 的内容，演示如何在二维 NumPy 数组中选择不同的元素范围。

***LISTING 1.11: np2darray2.py***

