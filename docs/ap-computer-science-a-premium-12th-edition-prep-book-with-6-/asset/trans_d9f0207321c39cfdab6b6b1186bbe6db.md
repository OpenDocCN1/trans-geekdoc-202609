

### 37
下面的方法 `changeNegs` 应该将其矩阵参数中每一个负整数的出现替换为 0。

![images](images/f265-01.jpg)

![images](images/f265-02.jpg)

哪一个是 `/* code */` 的正确替换？

![images](images/f265-03.jpg)

(A) 仅 I
(B) 仅 II
(C) 仅 III
(D) 仅 I 和 II
(E) I、II 和 III

### 38
一个包含 `double` 值的二维数组 `rainfall` 将被用来表示某一年的每日降雨量。在这个方案中，`rainfall[month][day]` 表示给定月份和日期的降雨量。例如，

![images](images/f266-01.jpg)

该数组可以按如下方式声明。

![images](images/f266-02.jpg)

这将创建 13 行（索引从 `0` 到 `12`）和 32 列（索引从 `0` 到 `31`），所有元素均初始化为 `0.0`。第 `0` 行和第 `0` 列将被忽略。第 `4` 行第 `31` 列将被忽略，因为 4 月 31 日不是有效日期。在非闰年中，第 `2` 行的第 `29`、`30` 和 `31` 列将被忽略，因为 2 月 29 日、30 日和 31 日不是有效日期。

考虑下面的方法 `averageRainfall`。

![images](images/f266-03.jpg)

以下哪一个是 `/* more code */` 的正确替换，以便满足该方法的后置条件？

![images](images/f266-04.jpg)

(A) 无
(B) 仅 I
(C) 仅 II
(D) 仅 III
(E) 仅 II 和 III

### 39
本题基于下面的 `Point` 类。

![images](images/f267-01.jpg)

下面的方法 `changeNegs` 接受一个 `Point` 对象矩阵作为参数，并将至少有一个负坐标的每个 `Point` 替换为 `Point` (0,0)。

![images](images/f267-02.jpg)

哪一个是 `/* code */` 的正确替换？

![images](images/f268-01.jpg)

(A) 仅 I
(B) 仅 II
(C) 仅 III
(D) 仅 I 和 II
(E) I、II 和 III

### 40
`Pixel` 类有多个修改器方法，允许更改 `Pixel` 的颜色。例如，

![images](images/f269-01.jpg)

考虑一个 `Picture` 类，它有一个私有实例变量 `pixels`，这是一个 `Pixel` 对象的二维数组。还有 `int` 变量 `rows` 和 `cols`，分别包含 `pixels` 数组的行数和列数。

`Picture` 类中的方法 `removeRed` 将每个像素的红色值设置为零。

![images](images/f269-03.jpg)

哪一个是 `/* code to set red value to 0 */` 的正确替换？

I. ![images](images/f269-04.jpg)
II. ![images](images/f269-05.jpg)
III. ![images](images/f269-06.jpg)

(A) 仅 I
(B) 仅 II
(C) 仅 III
(D) 仅 I 和 II
(E) I、II 和 III

### 41
考虑一个具有私有实例变量 `mat` 的类 `MatrixStuff`。

![images](images/f270-01.jpg)

以下方法使用矩阵中心的垂直镜像将矩阵的左半部分反射到右半部分。以下两个示例展示了将二维数字数组从左到右垂直镜像的结果。（另一种说法是矩阵的右半部分被左半部分的垂直镜像所替换。）

**示例 1：**

![images](images/f270-02.jpg)

**示例 2：**

![images](images/f270-03.jpg)

![images](images/f270-04.jpg)

哪个 `/* element assignments */` 的替换能使该方法按预期工作？

(A) `mat[row][col] = mat[row][width - col];`
(B) `mat[row][width - col] = mat[row][col];`
(C) `mat[row][width - 1 - col] = mat[row][col];`
(D) `mat[row][col] = mat[row][width - 1 - col];`
(E) `mat[row][width - 1 - col] = mat[col][row];`

### 42
考虑一个类中的方阵，该类具有私有实例变量 `mat`。

![images](images/f271-01.jpg)

类中的方法 `alter` 会改变 `mat`。

![images](images/f271-02.jpg)

如果 `mat` 当前值为

![images](images/f271-03.jpg)

执行方法 `alter` 后 `mat` 的内容是什么？

![images](images/f271-04.jpg)

### 43
一个简单的井字棋棋盘是一个 3×3 的数组，填充有 X、O 或空白。

这是一个井字棋游戏的类。

![images](images/f272-01.jpg)

哪个代码段代表了 `toString` 方法中 `/* more code */` 的正确替换？

![images](images/f273-01.jpg)

### 答案解析

#### 1
**(E)** 代码段 I 是一个初始化列表，等同于

![images](images/f274-01.jpg)

代码段 II 创建了四个整数槽位，默认初始化为 `0`。因此代码段 III 中的 `for` 循环是不必要的。然而，它并不**错误**。

#### 2
**(C)** 如果 `arr` 不包含负整数，`i` 的值最终将超过 `N-1`，`arr[i]` 将导致抛出 `ArrayIndexOutOfBoundsException`。

#### 3
**(E)** 意图是对元素 `arr[0]`、`arr[1]`、...、`arr[arr.length-1]` 求要注意，然而，当 `i` 的值为 `arr.length-1` 时，它在循环中被增量为 `arr.length`，因此语句 `sum += arr[i]` 使用了 `arr[arr.length]`，这超出了范围。

#### 4
**(A)** 该代码段的效果是从数组 `arr1` 中移除所有 0 的出现。该算法将非零元素复制到 `arr1` 的前端。然后将它们传输到数组 `arr2`。

#### 5
**(C)** 如果对于从 `2` 到 `k` 的所有 `i` 都有 `arr[i] < someValue`，则在 `for` 循环的每次迭代中都会打印 `SMALL`。由于有 `k - 1` 次迭代，`SMALL` 最多可打印 `k - 1` 次。

#### 6
**(C)** 数组 `arr` 被 `doSomething` 改变了。以下是内存槽位：

![images](images/f274-02.jpg)

![images](images/f274-03.jpg)

#### 7
**(D)** 数组长度固定，如果数据集大小变化，数组不会收缩或增长。`ArrayList` 会自动调整列表大小。选项 A 是错误的：`[]` 表示法简洁且易于使用。选项 B 不是有效理由，因为数组 `arr` 也通过 `arr.length` 提供对其长度的即时访问。选项 C 无效，因为数组也可以包含对象。此外，在给定程序中，泛型性不相关：列表*必须*保存 `String` 对象。选项 E 是错误的：无论 `String` 对象是 `arr[i]` 还是 `list.get(i)`，调用 `String` 方法同样容易。

#### 8
**(A)** 要将数值元素添加到 `ArrayList` 中，必须在插入列表前将每个元素包装在包装类中。然后，要从 `ArrayList` 检索数值，必须使用 `intValue` 或 `doubleValue` 方法对元素进行拆箱。即使这些操作可以通过自动装箱和拆箱来处理，但存在效率成本。在数组中，你只需使用 `[]` 表示法进行赋值（如 `arr[i] = num`）或检索（`value = arr[i]`）。注意选项 B 和 C 是错误陈述：数组的插入和删除都涉及编写代码来移动元素。`ArrayList` 通过其 `add` 和 `remove` 方法自动处理此问题。选项 D 选择数组的理由不充分。虽然 `ArrayList` 的 `get` 和 `set` 方法可能比使用 `[]` 表示法稍显笨拙，但两种机制都相当容易使用。选项 E 是错误的：访问效率大致相同。

#### 9
**(D)** 对于 `list` 中的每个 `Address` 对象 `a`，使用 `a.getName()` 访问该对象的名称。

