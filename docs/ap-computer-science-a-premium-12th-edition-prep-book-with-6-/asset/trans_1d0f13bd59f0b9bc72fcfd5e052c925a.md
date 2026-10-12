
# AP 计算机科学 A 练习题

## 第 1–3 题

I. ![images](images/f251-09.jpg)

II. ![images](images/f251-10.jpg)

III. ![images](images/f251-11.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 III

(E) I、II 和 III

---

## 第 21 和 22 题参考下面描述的 `Deck` 类。

一个 `Deck` 类包含一个数组 `cards`，其中包含偶数个 `Card` 值，以及一个 `final` 变量 `NUMCARDS`，它是一个奇数整数。

### 21. 以下是洗牌的两种可能算法。

![images](images/f252-01.jpg)

关于算法 1 和算法 2，以下哪项陈述是错误的？

(A) 算法 1 的一个缺点是它无法生成所有可能的牌组排列。

(B) 对于算法 2，要确定最后一个被洗牌的元素，平均需要调用 `NUMCARDS` 次随机数生成器。

(C) 算法 2 将导致比算法 1 更多的牌组排列。

(D) 就运行时间而言，算法 2 比算法 1 更高效。

(E) 如果算法 1 重复多次，它可能会将牌组恢复到其原始状态。

### 22. 以下 `shuffle` 方法用于打乱 `Deck` 类中的牌。

![images](images/f253-01.jpg)

该方法无法按预期工作。为了修正该方法，应进行以下哪项更改？

(A) 将第 3 行替换为
```
for (int k = NUMCARDS; k >= 0; k--)
```

(B) 将第 3 行替换为
```
for (int k = NUMCARDS - 1; k > 0; k--)
```

(C) 将第 3 行替换为
```
for (int k = 1; k <= NUMCARDS; k++)
```

(D) 将第 5 行替换为
```
int randPos = (int) (Math.random() * k);
```

(E) 将第 7–9 行替换为
```
Card temp = cards[randPos];
cards[randPos] = cards[k];
cards[k] = temp;
```

---

## 23. 考虑以下声明。

![images](images/f253-07.jpg)

哪条语句会导致错误？

(A) `strList.add(ch);`

(B) `strList.add(new String("handy andy"));`

(C) `strList.add(intOb.toString());`

(D) `strList.add(ch + 8);`

(E) `strList.add(intOb + 8);`

---

## 24. 设 `list` 为一个包含以下元素的 `ArrayList<Integer>`。

![images](images/f254-01.jpg)

以下哪条语句不会导致错误？假设每条语句独立应用于给定的列表，互不影响。

(A) `Object ob = list.get(6);`

(B) `Integer intOb = list.add(3.4);`

(C) `list.add(6, 9);`

(D) `Object x = list.remove(6);`

(E) `Object y = list.set(6, 8);`

---

## 25. 请参考下面的 `insert` 方法。

![images](images/f254-07.jpg)

假设 `element` 的类型与列表中的对象兼容，关于 `insert` 方法，以下哪项陈述是正确的？

(A) 它对所有 `element` 值都能按预期工作。

(B) 它对所有 `element` 值都会失败。

(C) 如果 `element` 大于 `list` 中的第一项则失败，在所有其他情况下均能工作。

(D) 如果 `element` 小于 `list` 中的最后一项则失败，在所有其他情况下均能工作。

(E) 如果 `element` 大于 `list` 中的第一项或小于最后一项则失败，在所有其他情况下均能工作。

---

## 26. 考虑应用于 `list`（一个 `Integer` 值的 `ArrayList`）的以下代码段。

![images](images/f254-09.jpg)

如果 `list` 初始为 `6 1 8`，执行代码段后它将变为？

(A) `2 3 4 2 1 8`

(B) `2 3 4 6 2 2 0 1 8`

(C) `2 3 4 0 1 2`

(D) `2 3 4 6 1 8`

(E) `2 3 3 2`

---

## 第 27 和 28 题基于下面给出的 `Coin` 和 `Purse` 类。

![images](images/f255-01.jpg)

### 27. 这是 `Purse` 类中的 `getTotal` 方法。

![images](images/f256-01.jpg)

以下哪项是 `/* more code */` 的正确替代？

![images](images/f256-02.jpg)

### 28. 如果两个硬币具有相同的名称或相同的价值，则称它们*匹配*。你可以假设名称相同的硬币价值相同，价值相同的硬币名称也相同。一个布尔方法 `find` 被添加到 `Purse` 类中。

![images](images/f257-01.jpg)

以下哪项是 `/* code to find match */` 的正确替代？

![images](images/f257-02.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) I、II 和 III

---

## 29. 以下哪项将一个 8×10 矩阵初始化为完全平方数的整数值？（0 是完全平方数。）

![images](images/f257-03.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) I、II 和 III

---

## 30. 考虑以下代码段。

![images](images/f258-01.jpg)

当这段代码执行时，打印的第五个元素将是？

(A) `3`

(B) `4`

(C) `5`

(D) `6`

(E) `7`

---

## 31. 考虑一个具有此私有实例变量的类。

![images](images/f259-01.jpg)

如果一个 3×4 矩阵 `mat` 是

![images](images/f259-03.jpg)

那么 `alter(1)` 将把 `mat` 改为

(A) ![images](images/f259-04.jpg)

(B) ![images](images/f259-05.jpg)

(C) ![images](images/f259-06.jpg)

(D) ![images](images/f259-07.jpg)

(E) ![images](images/f259-08.jpg)

---

## 32. 考虑将改变矩阵 `mat` 的以下方法。

![images](images/f260-01.jpg)

假设 `mat` 最初是

![images](images/f260-02.jpg)

方法调用 `matStuff(mat, 2)` 后，矩阵 `mat` 将变为

(A) ![images](images/f260-03.jpg)

(B) ![images](images/f260-04.jpg)

(C) ![images](images/f260-05a.jpg)

(D) ![images](images/f260-05.jpg)

(E) ![images](images/f260-06.jpg)

---

## 33. 假设一个方阵 `mat` 定义为

![images](images/f261-01.jpg)

以下代码段的作用是什么？

![images](images/f261-02.jpg)

你可以假设存在以下 `swap` 方法。

![images](images/f261-03.jpg)

(A) 将 `mat` 关于其主对角线反射。例如，
![images](images/f261-05.jpg)

(B) 将 `mat` 关于其副对角线反射。例如，
![images](images/f261-06.jpg)

(C) 将 `mat` 关于一条水平对称线反射。例如，
![images](images/f261-07.jpg)

(D) 将 `mat` 关于一条垂直对称线反射。例如，
![images](images/f261-08.jpg)

(E) 使 `mat` 保持不变。

---

## 34. 考虑一个具有私有实例变量的类 `MatrixStuff`。

![images](images/f262-01.jpg)

请参考 `MatrixStuff` 类中出现的 `alter` 方法。（行号仅供参考。）

![images](images/f262-02.jpg)

方法 `alter` 的意图是移除第 `c` 列。因此，如果输入矩阵 `mat` 是

![images](images/f262-04.jpg)

方法调用 `alter(mat, 1)` 应将 `mat` 改为

![images](images/f262-05.jpg)

该方法无法按预期工作。以下哪项更改将修正该问题？

![images](images/f262-06.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) I、II 和 III

---

## 35. 本题参考以下方法。

![images](images/f263-01.jpg)

现在考虑这段代码。

![images](images/f263-02.jpg)

以下哪个关于矩阵 `mat` 的条件（其类型在代码段中声明）单独就能保证

![images](images/f263-03.jpg)

计算结果为 `true`？

I. 第 2 行第 2 列的元素是 `"$"`。

II. 两条对角线上的所有元素都是 `"$"`。

III. 第 2 列的所有元素都是 `"$"`。

(A) 仅 I

(B) 仅 III

(C) 仅 I 和 II

(D) 仅 I 和 III

(E) 仅 II 和 III

---

## 36. 考虑以下方法。

![images](images/f264-01.jpg)

如果矩阵 `mat` 的当前状态是

![images](images/f264-02.jpg)

方法调用 `alterArray(mat[2])` 将导致哪个矩阵？

(A) ![images](images/f264-03.jpg)

(B) ![images](images/f264-04.jpg)

(C) ![images](images/f264-05.jpg)

(D) ![images](images/f264-06.jpg)

(E) ![images](images/f264-07.jpg)

