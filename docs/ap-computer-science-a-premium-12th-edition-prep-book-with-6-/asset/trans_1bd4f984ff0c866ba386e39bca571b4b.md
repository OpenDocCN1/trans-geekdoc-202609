

# 习题解析

## 21. (C)
`mat` 的行数由 `mat.length` 给出。行索引范围为 `0` 到 `mat.length - 1`。`mat` 的列数由 `mat[0].length` 给出。你可以将其视为 `mat[0]`（第一行）所代表数组的长度。（注意所有行长度相同，但使用 `mat[0]` 更明智，因为矩阵至少有一行。例如 `mat[1]` 可能越界。）列索引范围为 `0` 到 `mat[0].length - 1`。按行优先（或列优先）遍历时最后访问的元素位于右下角——即 `mat[mat.length - 1][mat[0].length - 1]`。

## 22. (C)
如果 `responses` 数组包含像 `12` 这样的无效值，程序将尝试给 `freq[12]` 加 1。这超出了 `freq` 数组的边界。

## 23. (D)
实现 I 调用 `super.computePay()`，这等同于 `Employee` 超类中的 `computePay` 方法。该方法返回 `(salary - taxWithheld)`。然后正确地将 `BONUS` 加到该表达式上，符合要求。实现 III 正确使用了 `Consultant` 类继承的公共访问器方法 `getSalary()` 和 `getTax()`。注意 `Consultant` 类无法直接访问私有实例变量 `salary` 和 `taxWithheld`。实现 II 错误地返回工资加 `BONUS`——没有扣税。表达式 `super.computePay()` 返回等于工资减税的值，但该值既未存储也未包含在 `return` 语句中。

## 24. (E)
注意 `p` 被声明为 `Employee` 类型，而 `Employee` 类没有 `getPayFraction()` 方法。为避免错误，必须将 `p` 转型为 `PartTimeEmployee`，如下所示：

```
double g = ((PartTimeEmployee) p).getPayFraction();
```

## 25. (E)
代码完全符合预期行为。`writePayInfo` 参数类型为 `Employee`，`empList` 数组的每个元素都是 `Employee`（满足 is-a 关系），因此无需转型为实际实例类型。这是多态的一个例子，即在运行时选择合适的 `computePay()` 方法。不会发生 `ArrayIndexOutOfBoundsException`（选项 B），因为数组通过增强 `for` 循环访问。数组元素均非 null，因此不会有 `NullPointerException`（选项 A）。选项 C 不会发生，因为 `getName()` 方法被 `Consultant` 和 `PartTimeEmployee` 类继承。只有当 `Employee` 超类是抽象类时选项 D 才会发生，但实际并非如此。

## 26. (D)
片段 I 错误，因为 `num` 不是循环中的索引：它是数组中的值。因此正确的测试是 `if (num > 0)`，这在片段 II 中正确使用。片段 III 是一个常规 `for` 循环，与给定的 `while` 循环完全等价。

## 27. (D)
第一个 `for` 循环将 `value` 放置在定义矩形的顶行和底行。第二个 `for` 循环填充侧边剩余的边框元素。注意 `top + 1` 和 `bottom - 1` 的初始化和终止条件避免了重复填充角落元素。

## 28. (D)
片段 I 可行，因为每个 `int` 值 `i + 1` 都被自动装箱为 `Integer`。片段 II 使用 `add()` 方法的重载版本同样可行。第一个参数是索引，第二个参数是要添加的元素。片段 III 失败，因为尝试在空列表中除位置 `0` 以外的位置添加元素会抛出 `IndexOutOfBoundsException`。

## 29. (E)
排除选项 A 和 B：比较 `Book` 对象时不能使用简单的不等号运算符；必须使用 `compareTo()`。若调用对象小于参数对象，应使用小于 0 的测试（这是一个很好的记忆方法！）。

## 30. (A)
当列表中存在连续负值时，`removeNegs()` 方法将无法正常工作。这是因为从 `ArrayList` 移除元素会导致其右侧元素左移填补“空洞”。然而给定算法中的索引总是向右移动一位。因此在选项 A 中，移除 `-1` 后，`-2` 会被跳过，最终列表变为 `6 -2 5`。

## 31. (A)
若列表已排序，二分查找是最高效的算法。二分查找将当前待检查数组部分对半分割，直到找到目标元素或无元素可查。最坏情况下需对半分割 7 次：

![images](images/f419-01.jpg)

快捷方式：将 120 四舍五入到最近的 2 的幂 128。因为 128 = 2⁷，最坏情况下的比较次数等于指数 7。

## 32. (B)
顺序查找需检查所有 *n* 个元素。二分查找最多将数组对半分割 log₂*n* 次。当目标在列表首位时，顺序查找首次比较即可找到；二分查找先检查中间元素则不行。条件 I 是顺序查找的最坏情况，所需比较次数远多于二分查找。条件 III 约在列表中间，但二分查找首次尝试（检查 `arr[n/2]`）也不会找到。尽管如此，目标仍会在少于 log*n* 次尝试内定位，而顺序查找需要超过 *n*/2 次尝试。

## 33. (D)
`remove()` 方法从 `arr` 中移除元素 `arr[index]`。它通过将 `arr[0]` 到不包括 `arr[index]` 的所有元素复制到数组 `b` 来实现。因此 `b[k] == arr[k]` 对 `0 <= k < index` 成立。然后将 `arr[index + 1]` 到 `arr[arr.length - 1]` 的所有元素复制到 `b`。由于 `b` 中无空隙，`b[k] == arr[k + 1]` 对 `index <= k < arr.length - 1` 成立。用小例子最易理解。若 `arr` 为 2, 6, 4, 8, 1, 7，要移除索引 2 处的元素（即 4），示意图如下：

![images](images/f419-02.jpg)

注意 `arr.length` 为 6，但 `k` 止于 4。

## 34. (E)
该片段是无限循环示例。以下是 `n` 的连续值，通过 `div` 运算符连续除以 2 更新：

![images](images/f419-03.jpg)

注意 `0/2` 等于 `0`，永远不会使 `n >= 0` 测试失败。

## 35. (A)
选项 A 非法，因为它未通过此测试：`TennisPlayer` is-a `WeakPlayer`？答案是否定的，不一定。

## 36. (D)
语句

```
double value = Math.random();
```

生成范围 0 ≤ `value` < 1 的随机 `double`。由于随机双精度值在该区间均匀分布，45% 的时间 `value` 会落在 0 ≤ `value` < 0.45 范围内。因此，测试 `value` 是否在此范围内可作为 `WeakPlayer` 发球是否入界的判断。因为 `Math.random()` 永不返回负数，实现 II 中的测试 `value < 0.45` 即足够。若将实现 I 中的 `||` 改为 `&&`（“或”改为“且”——两部分均须为真）则正确。实现 III 也可行。表达式

```
(int) (Math.random() * 100)
```

返回 0 到 99 的随机整数，概率均等。因此 45% 的时间整数 `val` 会在 0 ≤ `val` ≤ 44 范围内。故测试 `val` 是否在此范围内可用于判断发球是否入界。

