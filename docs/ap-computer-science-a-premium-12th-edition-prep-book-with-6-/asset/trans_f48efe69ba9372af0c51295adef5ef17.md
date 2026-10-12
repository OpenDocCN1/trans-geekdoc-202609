

# 拆箱

**拆箱**是 Java 编译器从包装类到基本类型所做的自动转换。这包括将 `Integer` 转换为 `int` 以及将 `Double` 转换为 `double`。

当包装类对象作为参数传递给期望相应基本类型值的方法时，将应用拆箱。例如，

![images](images/f162-03.jpg)

当包装类对象赋值给相应基本类型的变量时，也会应用拆箱。例如，

![images](images/f162-04.jpg)

## 包装类对象的比较

拆箱常用于同类型包装对象的比较。但这比听起来更棘手。不要使用 `==` 来测试 `Integer` 对象！你可能会得到令人惊讶的结果。表达式 `if (intOb1 == intOb2)` 测试的是 `intOb1` 和 `intOb2` 是否为同一*引用*。它并不测试实际的值。

### 示例 1

![images](images/f163-01.jpg)

测试返回 `true`，但原因并非你所预期。原因在于为了效率，如果 `int` 值相同，Java 只会创建一个 `Integer` 对象。因此引用是相同的。这是安全的，因为 `Integer` 不能被修改。（它是*不可变*的。）

### 示例 2

![images](images/f163-02.jpg)

此测试返回 `false`，因为使用 `new` 会创建一个新对象。在本例中，`intOb1` 和 `intOb2` 是不同的引用。请参阅第 158 页（[p. 158](#50_Chapter42.xhtml#page_158)）框中关于 `String` 对象的类似情况。

### 示例 3

![images](images/f163-03.jpg)

此测试返回 `true`，因为如果比较是在 `Integer` 对象和基本整数类型之间进行的，该对象会被自动拆箱。

### 示例 4

![images](images/f163-04.jpg)

此测试返回 `true`，因为测试的是对象的值。这是测试 `Integer` 对象相等性的正确方法。

关系运算符小于（`<`）和大于（`>`）在测试 `Integer` 和 `Double` 对象时，会按照你的预期工作。

### 示例 5

![images](images/f163-05.jpg)

此测试返回 `true`，因为编译器按如下方式拆箱对象：

```
if (intOb1.intValue() < intOb2.intValue())
```

### 示例 6

![images](images/f163-06.jpg)

此测试将返回 `true`，因为同样，如果操作数之一是基本类型，该对象将被拆箱。

## `Math` 类

该类实现了标准数学函数，如绝对值、平方根、三角函数、对数函数、幂函数等。它还包含数学常量，如 *π* 和 *e*。

以下是 AP 考试你应该了解的函数：

![images](images/f164-01.jpg)

返回整数 *x* 的绝对值。

![images](images/f164-02.jpg)

返回实数 *x* 的绝对值。

![images](images/f164-03.jpg)

返回 `base`^(exp)。假设 `base` > 0，或 `base` = 0 且 `exp` > 0，或 `base` < 0 且 `exp` 为整数。

![images](images/f164-04.jpg)

![images](images/f164-05.jpg)

返回一个随机数 *r*，其中 0.0 ≤ *r* < 1.0。（参见下一节“随机数”。）

所有函数和常量均实现为静态方法和变量，这意味着不存在 `Math` 对象的实例。方法通过类名 `Math` 加点运算符来调用。

以下是一些数学公式及其等效 Java 语句的示例。

**1.** 圆的半径与面积的关系是

![images](images/f164-06.jpg)

代码中：

`radius = Math.sqrt(area / Math.PI);`

**2.** 给定原始存款 *P* 和年利率 5% 按年复利，十年后账户中的金额 *A* 为

![images](images/f164-07.jpg)

代码中：

`a = p * Math.pow(1.05, 10);`

**3.** 同一水平线上两点 *P*(*x[P]*, *y*) 和 *Q*(*x[Q]*, *y*) 之间的距离 *D* 为

![images](images/f164-08.jpg)

代码中：

`d = Math.abs(xp - xq);`

### 注意

静态导入结构允许你在不使用类名前缀的情况下使用类的静态成员。例如，语句

`import static java.lang.Math.*;`

允许在不带 `Math` 前缀的情况下使用所有 `Math` 方法和常量。因此，上述公式 1 中的语句可以写成

`radius = sqrt(area / PI);`

静态导入不属于 AP 考试大纲范围。

## 随机数

### 随机实数

语句

`double r = Math.random();`

生成一个范围在 0.0 到 1.0 之间的随机实数，其中包含 0.0 但不包含 1.0。

此范围可以缩放和平移。在 AP 考试中，你需要编写涉及 `Math.random()` 的代数表达式，以表示原始区间 0.0 ≤ *x* < 1.0 的线性变换。

### 示例 1

生成一个范围在 0.0 ≤ *x* < 6.0 的随机实数值 *x*。

`double x = 6 * Math.random();`

### 示例 2

生成一个范围在 2.0 ≤ *x* < 3.0 的随机实数值 *x*。

`double x = Math.random() + 2;`

### 示例 3

生成一个范围在 4.0 ≤ *x* < 6.0 的随机实数值 *x*。

`double x = 2 * Math.random() + 4;`

一般来说，要生成一个范围在 `lowValue` ≤ *x* < `highValue` 的随机实数值：

`double x = (highValue - lowValue) * Math.random() + lowValue;`

### 随机整数

通过 `int` 强制转换、缩放因子和偏移值，`Math.random()` 可用于生成任意范围内的随机整数。

### 示例 1

生成一个 0 到 99 的随机整数。

`int num = (int) (Math.random() * 100);`

一般来说，表达式

`(int) (Math.random() * k)`

生成一个范围在 0, 1, ..., *k* − 1 的随机 `int`，其中 *k* 称为缩放因子。注意，`int` 强制转换会截断实数 `Math.random() * k`。

### 示例 2

生成一个 1 到 100 的随机整数。

`int num = (int) (Math.random() * 100) + 1;`

一般来说，如果 *k* 是缩放因子， *p* 是偏移值，语句

`int n = (int) (Math.random() * k) + p;`

生成一个范围在 *p*, *p* + 1, ..., *p* + (*k* − 1) 的随机整数 *n*。

### 示例 3

生成一个 5 到 24 的随机整数。

`int num = (int) (Math.random() * 20) + 5;`

注意，从 5 到 24（包含两端）共有 20 个可能的整数。

## 章节总结

所有学生都应该了解如何重写 `Object` 类的 `equals` 和 `toString` 方法，并应熟悉 `Integer` 和 `Double` 包装类。

了解 AP 考试大纲范围内 `Math` 类的方法，特别是使用 `Math.random()` 生成随机数。学习 `String` 方法 `substring` 和 `indexOf`，包括了解 `String` 方法中在何处抛出异常。

## 关于某些标准类的选择题

[1](#50_Chapter42.xhtml#rfn5-1). 考虑在一个计算 `base`^(exp) 的程序中的以下声明。

![images](images/f167-01.jpg)

下面哪项是

![images](images/f167-02.jpg)

的正确替代？

I.
```
double power;
Math m = new Math();
power = m.pow(base, exp);
```

II.
```
double power;
power = Math.pow(base, exp);
```

III.
```
int power;
power = Math.pow(base, exp);
```

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 I 和 III

[2](#50_Chapter42.xhtml#rfn5-2). 考虑下面定义的 `squareRoot` 方法。

![images](images/f167-08.jpg)

哪个 `/* implementation code */` 满足后置条件？

I.
```
double x = d;
x = Math.sqrt(x);
return x;
```

II.
```
return new Double(Math.sqrt(d.doubleValue()));
```

III.
```
return Double(Math.sqrt(d.doubleValue()));
```

(A) 仅 I

(B) 仅 I 和 II

