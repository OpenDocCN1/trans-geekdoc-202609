
• 第一个选项是经典的 `for` 循环写法。如果你总是从 `i = 0` 开始，直到 `i < n`，你就知道循环会执行 `n` 次，而无需额外思考（当然要用 `i++`）。因此，这个第一个例子会打印八个 "$"。

• 第二个例子与第一个完全相同，只是把 `for` 循环改写为 `while` 循环。你可以看到 `i = 0`、`i < 8`、以及 `i++`。因此，这个例子也会打印八个 "$"。

• 第三个例子说明我们总是坚持使用第一个例子中的约定。这里我们需要进行推理：`i` 会在 `7`、`10`、`13`、`16`、`19`、`22`、`25`、`28` 取值，最后在 `31` 处失败。这有八个不同的值，意味着循环会执行八次。因此，这个例子也会打印八个 "$"。

**5.**  答案是 E。

• `Integer.MAX_VALUE` 是一个常量，表示 `int` 类型能够存储的最大值。在此问题中，我们需要确保 `a + b` 不会超过该值。

• 方案 b 看起来是合理的做法，但如果 `a + b` 超出 `int` 范围，则无法将它们相加来判断是否超出。`a + b` 会发生溢出。

• 我们需要进行一些基本代数运算，在等式两边都减去 `a`，得到：

`b < Integer.MAX_VALUE - a`

• 表达式两边的顺序被交换了，所以需要翻转不等式。将 `<` 翻转为 `>=`。

**6.**  答案是 D。

• 外层循环将执行 10 次：`j = 0` 到 `j = 9`。

• 内层循环比较复杂，其执行次数取决于 `j`。

• 第一次循环时，`j = 0`，则 `k = 10`、`9`、`8` … `1`（共 10 次）。

• 第二次循环时，`j = 1`，则 `k = 10`、`9`、`8` … `2`（共 9 次）。

• 第三次循环时，`j = 2`，则 `k = 10`、`9`、`8` … `3`（共 8 次）。

• 这里有一个明显的规律，所以不需要逐一列出全部情况。需要注意的是要在正确的位置停止。

• 最后一次循环时，`j = 9`，则 `k = 10`（仅 1 次）。

• 总计：`10 + 9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1 = 55`

**7.**  答案是 A。

• `b1` 和 `b2` 都为 `true`。`while` 条件中的 OR（`||`）要求至少有一个为 `true`，因此我们第一次进入循环。

• `7 > 4`，所以执行 `b2 = ! b2`。这是一个用于翻转布尔值的小语句：因为 `b2` 为 `true`，`!b2` 为 `false`，随后把 `false` 赋回 `b2`，使其变为 `false`。

• 跳过 `else` 语句，减去 1 给 `x`。

• 循环底部：`b1 = true`，`b2 = false`，`x = 6`。

• `while` 条件现在为 `(true || false)`，仍为 `true`，因此继续执行循环。

• `6 > 4`，所以再次翻转 `b2`。`b2` 现在为 `true`。

• 跳过 `else`，减去 1 给 `x`。

• 循环底部：`b1 = true`，`b2 = true`，`x = 5`。

• `while` 条件为 `(true || true)`，仍为 `true`，继续执行循环。

• `5 > 4`，所以再次翻转 `b2`。`b2` 现在为 `false`。

• 跳过 `else`，减去 1 给 `x`。

• 循环底部：`b1 = true`，`b2 = false`，`x = 4`。

• `while` 条件为 `(true || false)`，仍为 `true`，继续执行循环。

• 这次 `if` 条件为假，执行 `else`，它会翻转 `b1` 的状态。`b1` 现在为 `false`。

• 减去 1 给 `x`。

• 循环底部：`b1 = false`，`b2 = false`，`x = 3`。

• 现在检查 `while` 条件，得到 `(false || false)`，不再执行循环。输出 `x` 的值，即 `3`。

**8.**  答案是 C。

• 选项 I

• 进入循环第一次时，`i = 1`，这会被打印。随后 `i = i * 2`，即 `i = 2`。

• 打印 `2`，`i = i * 2`，即 `i = 4`。

• 打印 `4`，`i = i * 2`，即 `i = 8`。

• 打印 `8`，`i = i * 2`，即 `i = 16`，循环条件不满足，退出循环。

• 最终输出：`1 2 4 8`

• 选项 II

• 通过观察 `for` 循环可知，循环会执行 4 次：`i = 4`、`3`、`2`、`1`。

• 每次循环打印 `(4 - i) * 2 + 1`。

• `(4 - 4) * 2 + 1 = 1`

• `(4 - 3) * 2 + 1 = 3`

• `(4 - 2) * 2 + 1 = 5`

• `(4 - 1) * 2 + 1 = 7`

• 最终输出：`1 3 5 7`

• 选项 III

• 通过观察 `for` 循环可知，循环会执行 4 次：`i = 0`、`1`、`2`、`3`。

• 每次循环打印 `(int)Math.pow(2, i)`。(`Math.pow` 返回 `double`，需要强制转换为 `int` 再打印。)

• `2⁰ = 1`

• `2¹ = 2`

• `2² = 4`

• `2³ = 8`

• 最终输出：`1 2 4 8`

• 选项 I 和 III 的输出相同。

**9.**  答案是 A。

• 第一次循环：`count = 6.0`，`num = 0`。

• 检查 `if` 条件：`6.0 != 0`，但 `0 / 6` 为 `0`，为 `false`，因此跳过 `if` 语句，回到循环顶部。

• 回到循环顶部：`count` 仍为 `6.0`，`num = 1`。

• 检查 `if` 条件：`6.0 != 0` 且 `1 / 6.0 > 0`，结果为 `true`，执行 `if` 语句，`count = 6.0 - 1 = 5.0`。

• 回到循环顶部：`count = 5.0`，`num = 2`。

• 检查 `if` 条件：`5.0 != 0` 且 `1 / 5.0 > 0`，结果为 `true`，执行 `if` 语句，`count = 5.0 - 2 = 3.0`。

• 回到循环顶部：`count = 3.0`，`num = 3`。

• 检查 `if` 条件：`3.0 != 0` 且 `3 / 3.0 > 0`，结果为 `true`，执行 `if` 语句，`count = 3.0 - 3 = 0.0`。

• 回到循环顶部：`count = 0.0`，`num = 4`。

• 检查 `if` 条件：这里很有趣。如果执行 `4 / 0.0`，程序会因除以零而抛出 `ArithmeticExceptionError`，但不会发生。第一部分 `count != 0` 为 `false`，Java 知道 `false AND` 任何值都是 `false`，因此不会执行第二部分，这称为短路求值，常用于此目的。条件为 `false`，`if` 语句块不执行。

• 回到循环顶部：`count = 0.0`，`num = 5`，循环结束，打印 `count` 的值，即 `0.0`。

**10.**  答案是 A。

• 唯一可行的做法是逐行仔细跟踪代码直至得到答案。

• `n = 0`，打印 `0 % 4`，结果为 `0`

• `0 % 5 = 0`，执行 `else`，`n = 3`

• 打印 `3 % 4`，结果为 `3`

• `3 % 5 = 3`，执行 `else`，`n = 6`

• 打印 `6 % 4`，结果为 `2`

• `6 % 5 = 1`，执行 `else`，`n = 9`

• 打印 `9 % 4`，结果为 `1`

• `9 % 5 = 1`，执行 `else`，`n = 12`

• 打印 `12 % 4`，结果为 `0`

• `12 % 5 = 2`，执行 `if`，`n = 16`

• 打印 `16 % 4`，结果为 `0`

• `16 % 5 = 1`，执行 `else`，`n = 19`

• 打印 `19 % 4`，结果为 `3`

• `19 % 5 = 4`，执行 `else`，`n = 22`，循环结束

• 打印序列：`0 3 2 1 0 0 3`

**11.**  答案是 D。

• 进入循环时，`tabulate = 100`，`repeat = 1`

• `tabulate = 100 - Math.pow(1, 2) = 99`；`repeat` 加 1 变为 `2`

• `99 > 20`，进入循环

• `tabulate = 99 - Math.pow(2, 2) = 95`；`repeat` 加 1 变为 `3`

• `95 > 20`

• `tabulate = 86 - Math.pow(3, 2) = 86 - 9 = 77`；`repeat` 加 1 变为 `4`

• `77 > 20`

• `tabulate = 77 - Math.pow(4, 2) = 77 - 16 = 61`；`repeat` 加 1 变为 `5`

• `61 > 20`

• `tabulate = 61 - Math.pow(5, 2) = 61 - 25 = 36`；`repeat` 加 1 变为 `6`

• `36 > 20`

• `tabulate = 36 - Math.pow(6, 2) = 36 - 36 = 0`；`repeat` 加 1 变为 `7`

• `0 < 20`，退出循环并打印 `0`

**12.**  答案是 B。

• 可以通过使用索引的起始值和结束值来求得该值。

• 内层循环从 `n` 开始，到 `i+1` 结束，步长为 1。

• 因此，执行次数为 `n - (i+1) - 1`。

# 概述

本单元是第 2 单元“使用对象”的延续。在本单元中，你将学习如何设计自己的类。完全理解类的设计、编写构造函数以及编写方法，是取得 AP 计算机科学 A 考试好成绩的关键。

![Images](img/idea.jpg)

## 关键概念

![image](img/star.jpg) `Java` 是一种面向对象的编程语言，其基础建立在 `class` 和 `object` 之上。

![image](img/star.jpg) `类` 用于描述从中创建的任何 `对象` 的特征。

![image](img/star.jpg) `对象` 是使用 `类` 作为蓝图创建的虚拟实体。

![image](img/star.jpg) `对象` 用于在程序中存储和操作信息。

![image](img/star.jpg) `实例变量` 用于存储对象的属性。

![image](img/star.jpg) `方法` 是对象可以执行的操作。

![image](img/star.jpg) `new` 关键字用于创建对象。

![image](img/star.jpg) `引用变量` 存储对象的地址，而不是对象本身。

![image](img/star.jpg) `对象` 按引用传递，而基本类型（primitives）按值传递。

![image](img/star.jpg) `数据封装` 是一种隐藏用户信息的方式。

![image](img/star.jpg) `重载构造函数` 具有相同的名称但不同的参数列表。

![image](img/star.jpg) `重载方法` 具有相同的名称但不同的参数列表。

![image](img/star.jpg) `静态变量` 称为类变量，且在同一类的所有对象之间共享。

![image](img/star.jpg) `静态 final 变量` 称为类常量，赋值后在程序运行期间不可更改。

![image](img/star.jpg) `this` 关键字用于指代当前对象。

![image](img/star.jpg) `作用域` 描述变量在程序中的可见范围。

## 类与对象之间的关系概述

面向对象编程语言的意图是提供一个框架，使程序员在将信息存储到对象后，能够对其进行操作。下面的段落描述了理解 Java 作为面向对象编程语言所需掌握的众多术语之间的关系。这些术语高度相互关联，因此我希望将它们整体而非分条列出。

**警告：请谨慎阅读**

下面的段落包含大量新术语。你可能需要多次阅读本节。如果你期望在考试中取得 5 分，你必须掌握以下全部内容。挑战自己，学得如此熟练，以至于你能够向他人讲解整个章节。

Java 类表示名词（人、地点或事物）。**类** 是构建从中产生的所有 **对象** 的蓝图。类中 **对象** 的属性通过 **实例变量** 表示。对象的所有实例变量的值决定了对象的 **状态**。当任何实例变量的值发生变化时，对象的状态就会改变。**方法** 是对象可以执行的虚拟操作。它们可能 **返回** 答案，或提供服务。

**对象** 使用保存蓝图的类创建。**类** 包含一段代码，称为 **构造函数**，它告诉计算机如何根据该类构建（构造）对象。关键字 `new` 用于创建对象。当 `new` 后跟类的构造函数名称时，会创建一个新对象。构造对象的操作也称为 **实例化** 对象，该对象被称为类的 **实例**。此外，在创建新对象的同时，也会创建一个 **引用**。**对象引用变量** 保存新创建对象的内存地址，并用于调用对象类中包含的方法。

编写自定义类将在第 5 单元中详细讨论。本单元介绍了可用的 `String`、`Math`、`Integer` 和 `Double` 类。

### `class` 声明

当你设计自己的类时，应该创建一个包含 **类声明** 的文件。类名在该声明中被标识。遵循 Java 命名规范，类名总是以大写字母开头并使用驼峰命名法。类被设为 `public`，以便用户可以创建该类的对象。

### 示例

创建一个名为 `Circle` 的类：

![Image](img/f0177-01.jpg)

#### 实例变量

描述类中对象的虚拟属性被称为 **实例变量**。类可以拥有任意数量、任意数据类型的实例变量，只要这些变量描述类中对象的某些特征或特点。与局部原始类型变量不同，默认值会在创建时分配给实例变量（`int` 变量为 `0`，`double` 为 `0.0`，`boolean` 为 `false`，对象为 `null`）。术语 **has-a** 指代类的实例变量，例如：对象 Name has-a 实例变量 Name。

### 示例

每个 `Circle` 对象都有 `radius`，因此创建一个名为 `radius` 的实例变量：

![Image](img/f0177-02.jpg)

#### `private` 与 `public` 可见性

**private** 和 **public** 称为 **可见性修饰符**（或 **访问级别修饰符**）。为了保持属性的内部封装，实例变量应设为 `private`。在实例变量声明中使用 `private` 确保其他类无法直接访问变量的数据，除非通过对象提供的方式。在类声明中使用 `public` 确保任何程序员都可以创建该类的对象。

![images](img/power.jpg)

`private` 与 `public`

在 AP 计算机科学 A 考试中，始终为实例变量提供 `private` 可见性。这能确保这些变量中的数据被隐藏。

#### 构造函数

**构造函数** 是虚拟对象的构建者。它们与关键字 `new` 一起使用，用于从类中创建对象。构造函数的名称与类名相同，通常位于类的顶部。构造函数被设为 `public`。构造函数用于设置对象的初始状态，这包括为所有实例变量提供初始值。

#### 无参构造函数

构造函数是创建新对象时调用的代码。当你定义新类时，它会附带一个 **无参构造函数**。根据所使用的 IDE，你可能会或可能看不到它。对于初学者来说，强烈建议自行编写一个。

#### 参数化构造函数及参数

如果你在创建对象之前就知道一些关于对象的信息，那么你可以在类中编写一个 **参数化构造函数** 来给实例变量提供初始值。参数化构造函数中定义的参数位于 **参数列表** 中，并与构造函数声明在同一行。

传递参数到构造器的过程称为向构造器 `传递参数`。传递给构造器的实际值称为 `参数`（或 `实际参数`），而在构造器内部接收该值的变量称为 `形式参数`。你在参数化构造器中包含一行代码，用于将形式参数的值赋值给实例变量。

如果你选择为类编写一个参数化构造器，那么默认的无参构造器将不复存在。这就是为什么通常建议你直接编写自己的构造器。

### 示例

编写 `Circle` 类的无参构造器和一个参数化构造器。参数化构造器必须包含一个用于表示圆半径的参数变量。

![Image](img/f0178-01.jpg)

![Image](img/power.jpg)

参数列表中的参数

参数是位于构造器声明中参数列表内的变量。构造器名称后的圆括号括起来整个参数列表。

例如，`Circle` 类的参数化构造器在参数列表中包含一个参数变量。该参数名为 `rad`（半径的缩写），其数据类型为 `double`。`Circle` 类的无参构造器在参数列表中没有任何参数。

![Image](img/f0179-01.jpg)

#### 方法

面向对象编程语言的真正魅力在于你开始操作对象。`method`（方法）定义了一个操作，允许你执行这些操作。方法有两种可能性。它可能仅仅执行某种服务，或者它会计算一个值并返回结果。返回值的操作称为 **返回** 值。

仅执行操作的方法称为 **void** 方法。返回值的方法称为 **return**（或 **非 void**）方法。`return` 方法必须定义其返回的数据类型，并包含 `return` 语句。`return` 方法可以返回任何数据类型。在非 void 方法中，返回表达式会按照返回类型进行评估，并返回该值的复制。但如果返回表达式是对象的引用，则返回的是引用的复制，而非对象本身。这称为“按引用返回”。

在 **method declaration**（方法声明）中使用 `public` 关键字可确保该方法可被其他类的对象访问。声明为 `private` 的方法仅在类内部可访问。

![images](img/power.jpg)

`return` 语句在 AP 计算机科学 A 考试中

必须返回值的方法必须包含可到达的 `return` 语句。void 方法不包含 `return` 语句。这一点在 AP 计算机科学 A 的自由响应题中尤为重要，因为如果在 void 方法或构造器中包含 `return` 语句，你将被扣分。

#### 访问器和修改器方法

在学习如何为类编写方法时，初学者通常会学习两类方法：

1. 允许你访问实例变量中存储值的方法
2. 允许你修改实例变量值的方法

返回实例变量值的方法称为 **访问器**（或 **getter**）方法。修改实例变量值的方法称为 **修改器**（或 **mutator** 或 **setter**）方法。不执行这两项职责的方法仅称为方法。

![images](img/power.jpg)

我的碳酸饮料是汽水还是可乐？

它们指的是同一种东西，只是取决于你居住的地方。就像这样，检索类中实例变量的方法也可以被称为访问器或 getter 方法，而修改实例变量值的方法则称为修改器、mutator 或 setter 方法。

#### 声明方法

方法使用称为 **方法声明** 语句的一行代码来声明。声明包括访问修饰符、返回类型、方法名称和参数列表。方法 **签名** 仅包括方法名称和参数列表。

方法声明的通用形式

`accessModifier returnType methodName(parameterList)`

单一目的

方法应只有一个目标。方法名称应清晰描述其目的。

#### `toString` 方法

建议你重写 `Object` 类中提供的 `toString()` 方法。通过这样做，类设计者（即你）在用户调用 `System.out.print()` 时拥有控制权，可以显示有意义的属性表示，而不是仅仅显示内存地址的引用（这有什么用呢？）。

在下面的 `Circle` 类中，如果没有重写 `toString()` 方法，那么调用 `System.out.println(myCircle)` 将打印 `Circle@7852e922`（或其他指向内存位置的值）。

### 示例

使用已编写的 `Circle` 类，编写一个访问半径的访问器方法、一个修改半径的修改器方法、一个计算并返回圆面积的方法，以及一个 `toString` 方法，返回描述圆属性的字符串。

![Image](img/f0181-01.jpg)

Java 忽略空格

Java 忽略所有不相关的空格。编译器不关心代码在 IDE 中看起来多么整洁，只要语法正确即可。在 AP 计算机科学 A 考试中，有时会看到经过精简的代码以节省页面空间。

例如，`Circle` 类的 `getRadius` 方法在考试中可能显示为：

![Image](img/f0181-02.jpg)

### 整合：`Circle` 和 `CircleRunner` 类

我现在将把我们刚才创建的 `Circle` 类与另一个类结合起来，演示两个类在面向对象环境中交互的示例代码。`Circle` 类定义了如何创建 `Circle` 对象。`CircleRunner` 类是程序员创建虚拟 `Circle` 对象并对其进行操作的地方。至于类名是否必须叫 `CircleRunner`，并不重要，但它传达了“我是运行包含圆的程序的类”这一含义。

#### `Circle` 类摘要

每个圆都有一个半径，因此 `Circle` 类定义了一个名为 `radius` 的实例变量。类还提供了两个构造器供创建 `Circle` 对象。无参构造器用于在创建 `Circle` 对象时尚不知晓半径的情况。半径默认获得 `double` 类型的默认值，即 `0.0`。参数化构造器用于在创建 `Circle` 对象时已知半径的情况。你在调用参数化构造器时传递半径，构造器将该参数值赋给实例变量。

`Circle` 类还包含四个方法：

1. 第一个方法 `getRadius` 返回该对象的半径。由于该方法是“获取”半径供程序员使用，因此它被称为访问器（或 getter）方法。
2. 第二个方法 `setRadius` 是一个 `void` 方法，用于设置对象的半径值。它被称为修改器（或 mutator 或 setter）方法。该方法包含一个参数，该参数在方法被调用时接收值并赋值给实例变量 `radius`。
3. 第三个方法 `getArea` 根据对象的半径计算并返回圆的面积。
4. 最后，第四个方法 `toString` 返回一个包含圆半径和面积的字符串。

#### `CircleRunner` 类摘要

The `Circle` class 无法单独工作。要有用，`Circle` 对象必须在 `Circle` 类之外的类中创建。每个由类创建的对象都称为该类的实例，构建对象的过程称为实例化对象。包含 main 方法的类有时被称为 runner class，其他情况下称为 client programs。main 方法是程序的入口点，这意味着当程序员运行程序时，Java 会先找到 main 方法并执行它。AP 计算机科学 A 考试中无需编写 main 方法。

请注意，`Circle` 类不包含 `public static void main(String[] args)`。`Circle` 类的目的在于定义如何构建和操作 `Circle` 对象；然而，`Circle` 对象的创建和操作在包含 main 方法的另一个类中进行。

如何从类中创建新对象

当你想要从类中创建对象时，需要调用类的构造器之一。然而，你可能有多个构造器，包括无参构造器或一个或多个带参数的构造器。计算机通过查看每个构造器声明中的参数列表来决定调用哪个构造器。匹配调用构造器的构造器用于创建对象。

**示例**

![Image](img/f0183-01.jpg)

### 示例

编写一个 runner class，实例化三个 `Circle` 对象。使第一个 `Circle` 对象的半径为 10，而第二和第三个 Circle 使用默认值。操作这些 Circle 的半径并打印它们的面积。对每个 Circle 对象调用 `toString` 方法，打印每个圆的半径和面积。

![Image](img/f0183-02.jpg)

![Image](img/f0184-01.jpg)

每个相同类的对象都是不同的对象

每个由类构造的对象都有自己的实例变量。两个 *不同* 的对象可以有相同的 **状态**，这意味着它们的实例变量具有相同的值。

在这个例子中，`CircleRunner` 类创建了三个不同的 `Circle` 对象，分别称为 `myCircle`、`hisCircle` 和 `herCircle`。请注意，`myCircle` 对象的半径为 10，因为在创建 `Circle` 对象时，计算机查找参数化构造器，找到后将 10 赋值给参数 `rad`，从而将实例变量 radius 设为 10.0。对于 `hisCircle` 和 `herCircle` 对象，调用了无参构造器，实例变量 radius 被赋予默认值 0.0。

请记住，`myCircle`、`hisCircle` 和 `herCircle` 都指向不同的对象，这些对象均来源于同一个 `Circle` 类，每个对象都有自己的 radius。当每个对象调用 `getArea` 方法时，它使用 *自己的* radius 来计算面积。

![images](img/power.jpg)

### The Dot Operator

点运算符用于调用对象的方法。对象的引用变量名称后跟一个点，然后是方法名称。

`objectReference.methodName();`

### 理解关键字 `new` 在对象构造时的作用

新手程序员常常难以理解为什么在创建对象时（如 `Circle` 对象在 `CircleRunner` 中）类名会出现两次。让我们分析下面这行代码，看看到底发生了什么。

![Image](img/f0184-02.jpg)

第一次出现的 Circle 是变量的数据类型。它类似于我们定义 `int` 或 `double` 变量的方式。变量 `myCircle` 被称为 **引用变量**，其类型为 Circle。它类似于基本类型变量，因为它保存一个值，但它 *并不* 保存 `Circle` 对象本身。`myCircle` 保存的是即将创建的 `Circle` 对象的内存地址。

第二次出现的 `Circle(10)` 是对 `Circle` 类参数化构造器的调用。关键字 **new** 告诉计算机：“我们即将创建一个新对象”。计算机在寻找一个只接受一个参数且数据类型与 10 匹配的构造器。找到后，它将 10 传递给参数 `rad`。构造器中的代码将实例变量 radius 设为参数 rad 的值。然后，`voilá!` `Circle` 对象的 radius 变为 10。

最后，计算机在内存（RAM）中查找存储 `Circle` 对象的位置，找到后记录其地址。`Circle` 的构建完成，`myCircle` 的引用变量现在保存了新对象的地址。

现在，任何想要操作 `myCircle` 所引用的对象（例如修改其半径）的操作，实际上是让 `myCircle` 去找到它所指向的对象（也称为 *pointing to*），然后设置该对象的 radius。

![images](img/power.jpg)

### 引用变量

引用变量不保存对象本身，而是保存对象在 RAM（随机访问内存）中存储的地址。

### 引用变量与实际对象的区别

下面的示意图旨在帮助你可视化引用变量与对象之间在计算机内存中的关系。注意：内存地址是模拟的，仅用于举例。

**问题 1：** 执行以下两行代码后会发生什么？

![Image](img/f0185-01.jpg)

**问题 2：** 执行以下这行代码后会发生什么？

![Image](img/f0186-01.jpg)

如果遵循示意图，你会看到 `herCircle` “获得”了 `hisCircle` 引用变量的地址。`herCircle` 包含与 `hisCircle` 相同的地址，这意味着这两个引用变量指向同一个对象。这种情况称为 **别名**（aliasing）。

观察 `herCircle` 之前引用的对象，发现没有任何引用指向它，它已被 **脱离** 并会被 **垃圾回收**（garbage collected） by Java。这意味着 Java 会在合适的时候删除它。

![Image](img/f0186-02.jpg)

### `null` 引用

当一个对象引用变量被创建但未被赋值为任何对象的地址时，它拥有 **null reference**。这意味着它本应知道对象的位置，但实际上不知道。每当你创建一个对象引用变量且没有给它赋值为实际对象的地址时，它的值为 **null**，即没有值。你也可以将引用变量赋值为 null，以清除它对之前对象的记忆。

![Image](img/power.jpg)

### `null` 引用

未包含任何对象地址的引用变量称为 `null` 引用。

**问题 3：** 执行以下语句时会发生什么？

`hisCircle = null;`

引用变量 `hisCircle` 现在为 null，即没有值。这意味着它不包含任何对象的地址。`herCircle` 仍然保存着 `Circle` 对象的地址，因此它可以调用该对象的方法。

![Image](img/f0187-01.jpg)

### 参数

#### 基本类型按值传递

传递给方法或构造器的值称为 **实际参数**（或 **实参**），而方法声明中的参数列表中的变量称为 **形式参数**。当实际参数是基本类型时，其值在方法内部无法被修改，因为只传递了变量的 *值*。

换句话说，形式参数变量会变成实际参数的复制品。该方法无法修改实际参数变量的值。形式参数变量仅接收实际参数的 `value`。该方法只有能力修改形式参数变量的值，而不能修改实际参数的值。

#### Objects Are Passed by Reference

对象是通过引用传递的。这意味着什么？

* 简单答案：当对象传递给方法时，该方法有能力修改对象的状态。

* 技术答案：当实际参数是对象时，真正作为参数的是对象的引用。这意味着当方法接收到引用并将其存储到形式参数变量中时，该方法现在有能力修改对象的状态，因为它知道对象的存储位置。形式参数现在是实际参数的别名。本质上，你已经把车钥匙交给了。

### Example

展示引用传递和值传递的区别。对象的状态在方法内被修改，而基本类型变量的状态保持不变。

![Image](img/f0188-01.jpg)

#### Comparing Against a `null` Reference

回顾，如果尝试对一个为 `null` 的引用变量调用方法，会出现 `nullPointerException` 错误。如何检查引用变量是否为 `null` 以避免该错误？答案是进行 **空检查**。使用 `==` 或 `!=` 运算符比较引用变量。千万不要使用 `equals` 方法进行空检查，否则会出现 `nullPointerException`！

### Example

使用 `Circle` 类演示如何进行空检查。如果 `Circle` 引用不为 `null`，则计算其面积；如果为 `null`，则返回 -1 作为面积。

![Image](img/f0189-01.jpg)

![Image](img/error.jpg)

Checking Against `null`

切勿使用 `equals` 方法判断对象引用是否为 `null`。只使用 `==` 或 `!=` 来检查引用变量是否为 `null`。

### Overloaded Constructors

一个类可以有多个构造器。构造器总是使用类名声明，但其参数列表可以不同。如果一个类中有两个或更多构造器，它们被称为 **重载构造器**。计算机根据参数列表决定使用哪个构造器。重载构造器具有相同的名称，但必须满足以下任一条件：

• 参数数量不同

• 参数数量相同，但至少有一个参数类型不同

• 参数类型相同，但顺序不同

### Example

为 `Student` 类声明四个构造器。构造器名称与类名相同，但因为参数列表不同而被视为不同。

![Image](img/f0190-01.jpg)

### Overloaded Methods

参数列表不同但名字相同的方法称为 **重载方法**。计算机根据参数列表决定使用哪个方法。重载方法必须具有相同的名字，并可能有不同的返回类型，但必须满足以下任一条件：

• 参数数量不同

• 参数数量相同，但至少有一个参数类型不同

• 参数类型相同，但顺序不同

### Example

声明四个重载方法。这些方法名相同，但参数列表不同。

![Image](img/f0191-01.jpg)

Blast from the Past

回顾 `String` 类中的 `substring` 方法是重载的。它有两个版本，但因为参数列表不相同而被视为不同。

### `static, static, static`

#### `static` Variables (Class Variables)

有时类需要有一个变量，该变量由所有来自该类的对象共享。该变量在声明和赋值时类似于实例变量，但使用关键字 **static** 进行声明。static 变量也称为 **类变量**，可以声明为 `private` 或 `public`。

#### `static final` Variables (Class Constants)

同样，类有时需要一个 **常量**，供类中所有对象使用。顾名思义，常量在程序的任何位置都不能被重新赋值。否则会出现编译错误。类常量使用关键字 `static` 和 `final` 声明，并使用全大写字母（必要时使用下划线）。这些 static final 变量也称为类常量。

#### `static` Methods (Class Methods)

如果方法被标记为 `static`，它只能调用其他 static 方法，并且只能使用或修改 static 变量。static 方法不能访问或修改实例变量，也不能调用非 static 方法。类方法与类相关联，而非与单个对象相关联。

### Example

假设你被星巴克雇佣，负责跟踪店铺总数。你已经决定创建名为 `StarbucksStore` 的类，那么如何跟踪店铺总数？解决方案是使用一个 static 变量，名为 `storeCount`。每次创建一个店铺（字面意思）时，increment 这个类变量。通过创建一个 static 方法 `getStoreCount` 来访问 `storeCount`。假设你还想有一个变量保存所有店铺的标志。你选择将其作为常量，因为所有店铺共享标志，且不应被修改。为此，我们将创建一个 static final 变量 `STARBUCKS_LOGO`，并初始化为 “`Mermaid`”。

![Image](img/f0193-01.jpg)

![Image](img/f0194-01.jpg)

你是否注意到类方法 `getStoreCount()` 和常量 `STARBUCKS_LOGO` 是如何在主程序中被调用的？由于这些方法和常量属于类而不是特定对象，它们使用类名 `StarbucksStore` 进行调用。这看起来很熟悉吗？你之前已经做过类似的事情，比如调用 `Math.abs()`（`Math` 类的 static 方法）或 `Integer.MAX_VALUE`（`Integer` 类的 static 常量）。

### Data Encapsulation

#### Information Hiding

在软件开发中，通过限制访问来保护信息很重要。由于类是 public 的，来自该类的所有对象都是 public 的。在 Java 中隐藏信息或 **封装数据** 的方式是使用 private 访问修饰符。

Encapsulated Data

在 AP Computer Science A 考试中，预期类的所有实例变量都声明为 private。访问它们的唯一方法是使用类提供的访问器或修改器方法。

#### What Happens If I Declare an Instance Variable `public`?

假设你想知道如果声明实例变量为 public 会发生什么。结果是任何使用点运算符的人都可以访问该实例变量。

### Example

将 `Circle` 类中的 `radius` 实例变量声明为 public。注意，现在任何使用点运算符的人都可以访问该公共变量。对 private 变量使用点运算符会导致编译错误。

![Image](img/f0195-01.jpg)

![images](img/power.jpg)

The Integer Class and Its `public` Fields

记住我们是如何访问 `Integer` 的最大值和最小值的？我们使用点运算符直接获取值。因为 `MAX_VALUE` 和 `MIN_VALUE` 是 `Integer` 类的 public 常量字段。你不需要使用访问器方法来获取它们。

-   [Java 中的 `int` 类型](https://example.org) 是一个基本类型，用于表示整数。

1.  变量的 **scope** 指的是在程序中变量的可见范围。如果尝试在变量的 scope 之外使用该变量，会产生编译时错误。

2.  不同类型的变量拥有不同的 scope。

    • `local variable` 的 scope 位于最近一对包围它的大括号 `{}` 之间。

    • `parameter` 的 scope 是它被声明所在的方法或构造函数的范围。

    • `instance variable` 的 scope 是它所在的类的范围。

### 文档

#### 内联注释

我一直在使用内联注释，并且会在本书的其余部分继续使用它们。内联注释以两个正斜杠 `//` 开头。`//` 后面的所有文本（在同一行）都会被编译器忽略。

`// This is an example of an inline comment.`

#### 多行注释

当你的注释跨越多行时，需要使用多行注释。多行注释以 `/*` 开头，以 `*/` 结尾。编译器会忽略这两个特殊字符序列之间的所有内容。

`/*`

`This is how to write a multiple-line comment. Everything typed here is ignored by the compiler; even mi mysteaks is spelling, so be particularly careful of your spelling when you are typing multiple-line comments!`

`*/`

#### Javadoc 注释

你会在 AP 计算机科学 A 考试中看到 **Javadoc 注释**（也称为 **文档注释**），尤其是在 FRQ 部分。这些注释以 `/**` 开头，以 `*/` 结尾。编译器会忽略这两个字符序列之间的所有内容。

`/**`

`* This is an example of a Javadoc comment.`

`* You will see these “documentation” comments on the AP CS exam.`

`*/`

#### Javadoc

**Javadoc** 是一个工具，用于生成格式化为 HTML 的文档，用于总结类（包括构造函数、实例变量、方法等）的可读格式。在程序员之间，这个文档本身通常也被称为 Javadoc。该总结被称为该类集合的 API（应用程序编程接口），对于程序员来说非常有用。你应该参考 Oracle Java 网站查看所有 Java 类及其方法的列表（但只有在 Java Quick Reference 中列出的类和方法会在 AP 计算机科学 A 考试中被测试）。

#### Javadoc 标签

类似于标签（hashtag），`@param` 是 Javadoc 注释中使用的标签。当程序员使用 `@param` 标签时，他们会声明参数的名称并提供简要描述。Javadoc 标签会被 Javadoc 工具自动检测并出现在 API 中。

`@return` 也是 Javadoc 标签。它仅用于返回方法，程序员会标明返回的变量名称以及简要描述。

#### 文档注释在 AP 计算机科学 A 考试中的使用

你不需要在 AP 计算机科学 A 考试中编写任何注释，只需要知道如何阅读它们即可。

#### 前置条件和后置条件

你了解假设会带来什么后果吗？一个 **前置条件**（precondition）是对参数在文档注释中可以假设的内容的描述。它是出现在构造函数或方法签名之前的文档注释的一部分，描述了参数的期望。方法并不保证检查前置条件是否满足。如果在前置条件未满足的情况下调用方法，那么方法很可能不会按预期工作。在 AP 计算机科学 A 考试中，阅读前置条件可以帮助你理解参数的性质。一个 **后置条件**（postcondition）是执行程序代码段后必须始终为真的条件。后置条件描述了执行结果，例如返回值或对象的状态。程序员在前置条件满足时，必须编写代码使后置条件成立。

### 示例

这是之前创建的 `Circle` 类的同一个版本，但现在已加入在 AP 计算机科学 A 考试中可能出现的 Javadoc 标签和前置/后置条件语句。此外，还使用了 `Math` 类的改进方法来计算面积。

![Image](img/f0197-01.jpg)

### `this` 关键字

关键字 **this** 是对当前对象的引用，或者说是正在调用的方法或构造函数所属的对象。它也被称为 **隐式参数**（implicit parameter）。

##### 示例 1

将隐式参数 **this** 传递给类中的另一个方法。这种用法可能会在考试中被测试。

![Image](img/f0198-01.jpg)

##### 示例 2

使用关键字 `this` 的常见位置是当实例变量的名字与构造函数的参数名相同时。`this` 用于赋值语句左侧，用来将实例变量的值赋为参数的值。左侧是实例变量，右侧是参数变量。使用 `this` 表示“我知道我们有相同的名字，所以这些是我的实例变量而不是参数”。

![Image](img/f0199-01.jpg)

### `IllegalArgumentException`

如果向方法传递的参数值不满足该方法所需的特定条件，运行时可能会抛出 `IllegalArgumentException` 错误。程序员也可以选择在不接收预期输入时让方法直接抛出 `IllegalArgumentException`。

![Image](img/arrow1.jpg) Rapid Review

#### 类

• 类包含用于创建单个对象的蓝图或设计图。

• 类通常表示名词。

• 类声明（或类定义）是声明类的代码行。

• 按命名惯例，类名以大写字母开头，并使用驼峰命名法。

• AP 计算机科学 A 考试中测试的两个访问修饰符是 `public` 和 `private`。

• 所有类都应该声明为 `public`。

• `public` 类表示该类对所有类都可见。

#### 实例变量

• 实例变量（或字段）是同一类中所有对象都具备的属性，它们帮助在同一类中区分一个对象与另一个对象。

• 所有实例变量都应该声明为 `private`。

• 类可以有适量的实例变量，以描述对象的所有属性。

• 按命名惯例，所有实例变量以小写字母开头，并使用驼峰命名法。

• 所有基本类型的实例变量都会有默认值。`int` 的默认值是 0，`double` 的默认值是 0.0，`boolean` 的默认值是 `false`，引用类型的默认值是 `null`。

• 对象的实例变量的当前值决定了对象的状态。

• 当任何实例变量被修改时，对象的状态就会改变。

#### 构造函数

• 默认情况下，每个类都有一个无参数（空）构造函数。

• 如果在创建对象时需要为实例变量赋值，应该创建参数化构造函数。

• 类可以有多个参数化构造函数，只要它们是相关的。

• 参数化构造函数的主要目的是在创建对象时为实例变量赋值。

• 构造函数中还可以编写其他代码。

• 参数是方法或构造函数参数列表中接收值的变量。

#### 方法

• 类中的方法描述对象可以执行的操作。

• 方法通常表示动词。

• 按命名惯例，方法名以小写字母开头，并使用驼峰命名法。

• 方法名应该描述其目的。

• 方法不应具有多功能性。它们应有一个目标。

• 方法声明描述与该方法相关的信息，例如访问修饰符、返回类型、方法名称和参数列表。

• 不返回值的方法称为 `void` 方法。

• 返回某数据类型值的方法称为返回方法。

• 方法可以返回任何数据类型。

• 返回方法必须包含一个可到达的 `return` 语句。

• 返回实例变量值的方法称为访问器（或 getter）方法。

• 修改实例变量值的方法称为变异器（或 modifier 或 setter）方法。

• 所有参数的数据类型必须在参数列表中定义。

• 声明为 public 的方法可以在类之外使用。

• 声明为 private 的方法只能在类内部使用。

• 在设计类时，程序员决定哪些数据可以从外部类访问和修改。

• 一个类的对象是对该类的虚拟实现。

• 对象存储其自身数据。

• 类的实例与类的对象是同一概念。

• “实例化”一词用于描述创建对象的操作。实例化是构造新对象的行为。

• 关键字 `new` 用于创建对象时。

• 引用变量存储实际对象所在的内存地址，且只能引用一个对象。

• 引用变量本身不存储对象。

• 两个引用变量相等仅当它们指向完全相同的对象时。

• 单词 `null` 表示无值。

• `null` 引用描述一个不包含任何对象地址的引用变量。

• 可以从一个类中创建任意数量的对象，每个对象存储在计算机内存的不同位置。

• 传递给方法或构造函数的参数变量称为实际参数（或实参）。

• 在方法或构造函数中接收值的参数变量称为形式参数。

• 按值传递意味着只传递变量的值。

• 原始类型变量按值传递。

• 无法改变按值传递的实际参数的值。

• 按引用传递意味着传递对象存储地址。

• 对象按引用传递（包括数组）。

• 当按引用传递时，对象的状态可以被修改。

• 可以改变按引用传递的实际参数的值。

• 重载构造函数可能有 (1) 参数数量不同，(2) 参数数量相同但类型不同，或 (3) 参数类型相同但顺序不同。

• 重载方法具有相同的名称，但其参数列表有所不同。

• 重载方法可能有 (1) 参数数量不同，(2) 参数数量相同但类型不同，或 (3) 参数类型相同但顺序不同。

• static 变量也称为类变量。

• 类变量是所有类实例共享的变量。

• 任何对象对类变量的修改都会反映在所有类实例的状态中。

• static final 变量也称为类常量。

• 类常量使用 both the keywords **static** and **final** 进行声明。

• 按惯例，常量使用大写字母和下划线命名。

• 常量在运行时不能被修改。

• 若方法被声明为 static，则它只能调用其他 static 方法并引用 static 变量。

• 变量的作用域指它在程序中可见的区域。

• 局部变量的作用域是其定义所在的代码块。

• 实例变量的作用域是其所在的类。

• 参数的作用域是其所在的方法或构造函数。

• 文档标签由 Javadocs 使用。

• `@param` 标签用于描述参数。

• `@return` 标签用于描述方法返回的内容。

• 前置条件描述参数所接收的值的预期情况。

• 后置条件描述方法结束时的结果标准。

• 数据封装是隐藏实例变量值的行为。

• 将实例变量声明为 private 可实现封装。

• 使用关键字 `this` 可引用对象本身。

• 当传递的参数未满足程序员设定的条件时，会出现 `IllegalArgumentException` 错误。

• ![ImageReview Questions](https://wiki.example.org/feynmans_learning_method)

• **1. (A) The terms *class* and *object* mean the same thing.**

• **2. (C) A class is the blueprint for an object and objects are instantiated from it.**

• **3. (A) `Student sam = new Student();`**

• **4. (B) `System.out.println(sam.getName());`**

• **5. (A) `public void setGPA(double newGPA) { gpa = newGPA; }`**

• **6. (E) Nothing will be printed. There will be a run-time error.**

• **7. (C) `23`**

• **8. (A) `40 49 40`**

# 编译时错误；重复变量。

## 考虑以下圆面积的计算。

`double area = Math.PI * Math.pow(radius, 2);`

`Math.PI` 可以最好地描述为：

(A) `Math` 类中的一个方法。

(B) 包含给定代码行的类中的一个方法。

(C) `Math` 类中的一个公共静态最终 double。

(D) `Math` 类中的一个私有静态最终 double。

(E) 包含给定代码行的类中的一个私有静态最终 double。

## 程序员正在设计一个 `BankAccount` 类。除了银行账户通常需要的信息外，她还想有一个变量来计数已经实例化了多少个 `BankAccount` 对象。她问你如何做到这一点。你告诉她：

(A) 这不可能完成，因为每个对象都有自己的变量空间。

(B) 她应该使用类常量。

(C) 她应该调用一个修改器方法来更改每个对象中保存的 `numAccounts` 变量。

(D) 她应该创建一个 `static` 变量，并在构造器中将其在每个对象创建时递增。

(E) Java 会自动保持计数。她应该引用 Java 维护的变量。

## 在类中拥有相同名称但参数数量不同或参数类型不同的多个方法的情况称为：

(A) 抽象化

(B) 方法重载

(C) 封装

(D) 方法可见性

(E) 参数化

### 高级水平

## 考虑以下方法。

![Image](img/f0205-01.jpg)

关于该方法的以下陈述哪一个是真的？

(A) `mystery` 返回三个整数 `a`、`b` 和 `c` 中最小的值。

(B) `mystery` 始终返回 `a` 的值。

(C) `mystery` 始终返回 `a` 和 `c` 的值。

(D) `mystery` 有时返回三个值 `a`、`b` 和 `c`。

(E) `mystery` 无法编译，因为在某些条件下返回语句看起来不可达。

## 将上一个问题中的方法重写如下所示。

![Image](img/f0206-01.jpg)

关于该方法的以下陈述哪一个是真的？

(A) `mystery2` 返回三个整数 `a`、`b` 和 `c` 中最小的值。

(B) `mystery2` 始终返回 `c` 的值。

(C) `mystery2` 返回 `a` 和 `c` 的值或 `b` 和 `c` 的值。

(D) `mystery2` 有时返回三个值 `a`、`b` 和 `c`。

(E) `mystery2` 无法编译，因为在某些条件下返回语句看起来不可达。

## 考虑以下类声明。

![Image](img/f0206-02.jpg)

下面的代码段出现在另一个类的 `main` 方法中。

![Image](img/f0206-03.jpg)

执行代码段后打印的结果是什么？

(A) `30`

(B) `15`

(C) `7.75`

(D) `7.5`

(E) `7`

## 考虑以下方法声明。

`public int workaround(int a, double b)`

以下哪个方法声明可以正确地重载给定的方法？

I. `public double workaround(int a, double b)`

II. `public int workaround(double b, int a)`

III. `public int workaround(String s, double b)`

IV. `public double workaround(int a, double b, String s)`

V. `public int workaround(int b, double a)`

(A) 仅 I

(B) 仅 IV

(C) 仅 II 和 III

(D) 仅 II、III 和 IV

(E) 所有以上

## 免费练习：Dream Vacation 类

每个人都幻想去梦想假期。

编写一个完整的 `DreamVacation` 类，包含以下内容：

a. 一个用于目的地名称的实例变量

b. 一个用于假期费用（美元和美分）的实例变量

c. 无参构造器

d. 参数化构造器，接受假期名称和费用

e. 用于两个实例变量的访问器（ getter ）方法

f. 用于两个实例变量的修改器（ setter ）方法

## 免费练习：Height 类

`Height` 类的目的在于保存以英尺和英寸为单位的测量值，便于对该测量值进行加法运算，并保持测量值为最简形式（即 inches < 12）。`Height` 对象可以用以英尺和英寸或以总英寸数来实例化。

编写完整的 `Height` 类，包括以下内容：

a. 实例变量 `int feet` 表示英尺数，`int inches` 表示英寸数。这些实例变量在任何更改时都必须更新，以便它们始终保持最简形式，即 inches 必须始终小于 12（见 C 部分所述的方法）。

b. 两个构造器，一个接受两个参数（英尺和英寸），另一个接受一个参数（总英寸数）。参数不一定代表最简形式。

c. 一个名为 `simplify()` 的方法，在必要时重新计算英尺和英寸，使得 inches 小于 12。

d. 一个名为 `add(int inches)` 的方法，接受要添加的英寸数并相应更新实例变量。

e. 一个名为 `add(Height ht)` 的方法，接受一个 `Height` 对象作为参数，将该对象的英尺和英寸与当前对象的英尺和英寸相加，并在必要时进行更新。

f. 用于实例变量 `inches` 和 `feet` 的访问器（ getter ）方法。

• s2 references a Student object with the state information: name = "Charlie Cole", gpa = 3.2

• When we execute the statement s2 = s1, s2 changes its reference. It now references the exact same object that s1 references, with the state information: name = "Brody Kai", gpa = 3.9

• s2.setGpa(4.0); changes the gpa in the object that both s1 and s2 reference, so when s1.getGpa(); is executed, that’s the value it retrieves and that’s the value that is printed.

`7` The answer is D.

• When the method call `calculate(var, count)` is executed, the arguments 9 and 2 are passed by value. That is, their values are copied into the parameters a and b, so a = 9 and b = 2 at the beginning of the method.

• a = 9 − 2 = 7

• int c = 2

• b = 7 \* 7 = 49

• a = 49 – (7 + 2) = 40 and that is what will be returned.

`8` The answer is B.

• When the method call `calculate(a, b)` is executed, the arguments 9 and 2 are passed by value, that is their values are copied into the parameters a and b. The parameters a and b are completely different variables from the a and b in the calling method and any changes made to a and b inside the method do not affect a and b in the calling method in any way.

• We know from problem #1 that calculate(9, 2) will return 40.

• 9 2 40 will be printed.

`9` The answer is C.

• All instance variables in the classes we write must be declared private. In fact, the AP Computer Science A exam readers may deduct points if you do not declare your variables private. However, some built-in Java classes provide us with useful constants by making their fields public.

• We access these fields by using the name of the class followed by a dot, followed by the name of the field. We can tell that it is a constant because its name is written entirely in capital letters. Some other public constants that we use are Integer.MAX_VALUE and Integer.MIN_VALUE.

• Note that we can tell this is not a method call, because the name is not followed by (). The Math.pow(radius, 2) is a method call to a static method of the `Math` class.

`10` The answer is D.

• Option A is incorrect. It correctly states that each object has its own variable space, and each object’s variables will be different. However, it is not correct about it being impossible.

• Option B is incorrect. It says to use a constant, which doesn’t make sense because she wants to be able to update its value as objects are created.

• Option C is incorrect. There is no one mutator method call that will access the instance variables of each object of the class.

• Option D is correct. A `static` variable or class variable is a variable held by the class and accessible to every object of the class.

• Option E is simply not true.

`11` The answer is B.

• Method overloading allows us to use the same method name with different parameters.

`12` The answer is E.

• The intent of the mystery method is to find and return the smallest of the three integers. We know that all possible conditions are covered by the if statements and one of them has to be true, but the compiler does not know that. The compiler just sees that all of the `return` statements are in if clauses, and so it thinks that if all the conditions are false, the method will not return a value. The compiler generates an error message telling us that the method must return a value.

`13` The answer is A.

• The first time a `return` statement is reached, the method returns to the caller. No further code in the method will be executed, so no further returns will be made.

`14` The answer is E.

• There are a lot of calls here, but only two that will affect the value of `val`, since the only time val is changed is in the constructor.

• It’s important to notice that `val` is a static variable. That means that the class maintains one copy of the variable, rather than the objects each having their own copy. Since there is only one shared copy, changes made to `val` by any object will be seen by all objects.

• The first time the constructor is called is when the word “object” is instantiated. val = 31 when the constructor is called and this call to the constructor changes its value to 15 (integer division).

• The second time the constructor is called is when the sentence object is instantiated. This time val = 15 when the constructor is called and this call to the constructor changes its value to 7 (integer division).

`15` The answer is D.

• Options I and V are incorrect. An overloaded method must have a different parameter list so that the compiler knows which version to use.

• Options II, III, and IV are valid declarations for overloaded methods. They can all be distinguished by their parameter lists.

`16` On the AP Computer Science A exam, you are often asked to write an entire class, like you were in this question. Check your answer against our version below. The comments are to help you read our solution. Your solution does not need comments.

Make Variable Names Meaningful

It’s OK if you use different variable names from what we use in the solutions to the chapter questions. Just be sure that the names are meaningful.

![Image](img/f0210-01.jpg)

![Image](img/f0211-01.jpg)

`17` The `Height` class

![Image](img/f0211-02.jpg)

![Image](img/f0212-01.jpg)

Note: There are many ways to write the `simplify` method. If you aren’t sure if yours works, type it into your IDE. Here’s one alternate solution:

![Image](img/f0212-02.jpg)

## UNIT **6**

## Array

**IN THIS UNIT**

**Summary:** Sometimes a simple variable is not enough. To solve certain problems, you need a list of variables or objects. The array, the two-dimensional array, and the `ArrayList` are three complex data structures that are tested on the AP Computer Science A Exam. `ArrayList` and 2D array will be discussed in Units 7 and 8. You must learn the advantages and disadvantages of each of these data structures, know how to work with them, and be able to choose the best one for the job at hand. Programmers use algorithms extensively to write the code that will automate a process in a computer program. The algorithms described in this unit are some of the fundamental algorithms that you should know for the AP Computer Science A Exam.

![Images](img/idea.jpg)

**Key Ideas**

![image](img/star.jpg) An array is a data structure that can store a list of variables of the same data type.

![image](img/star.jpg) An array is not resizable once it is created.

![image](img/star.jpg) To traverse a data structure means to visit each element in the structure.

![image](img/star.jpg) The enhanced for loop (`for-each` loop) is a special looping structure that can be used by either arrays or `ArrayLists`.

![image](img/star.jpg) An algorithm is a set of steps that when followed complete a task.

![image](img/star.jpg) Pseudocode is a hybrid between an algorithm and actual Java code.

![image](img/star.jpg) Efficient code performs a task in the fastest way.

![image](img/star.jpg) The `accumulate` algorithm traverses a list, adding each value to a total.

![image](img/star.jpg) The `find-highest` algorithm traverses and compares each value in the list to determine which one is the largest.

### What Is a Data Structure?

Have you ever dreamed about having the high score in the “Top Scores” of a game? How does Facebook keep track of your friends? How does TikTok know what video to loop next? All of these require the use of a complex data structure.

#### Simple Data Structure Versus Complex Data Structure

-   [数据结构](https://wiki.example.org/data_structures) 用于存储信息。原始变量是一个 `简单数据结构` 的示例，因为它可以在稍后检索时存储单个值。一个能够存储其他变量列表的变量被称为 `复杂数据结构`。

![Image](img/f0214-01.jpg)

-   使用虚拟对象来表示物理对象可能很具挑战性。真正出色的程序员能够可视化复杂的现实场景，并设计数据结构来以虚拟方式表示这些物理对象。在下面的图中，程序员正在尝试通过创建一个复杂的数据结构来表示午餐菜单中的选择。

![Image](img/f0214-02.jpg)

#### 三个重要的复杂数据结构

在 AP 计算机科学 A 考试中会考查三种复杂数据结构：

• `数组`（或一维数组）

• `二维数组`

• `ArrayList`

数组将在本单元后详细解释，`ArrayList` 将在 第 7 单元 中解释，二维数组将在 第 8 单元 中解释，但在此我希望给出在什么情况下哪种数据结构最合适的概述。你需要成为判断特定情境下最佳数据结构的专家。这通常需要经验，但下面给出了一些示例，说明在什么情况下哪种结构最合适。

![Image](img/f0215-01.jpg)

#### 数组

#### 数组的定义

非编程语境下的数组定义是“一种令人印象深刻的特定事物展示”。在日常语言中，我们会说“哇，看看商场里所有的手机壳的 **数组**！”这意味着有一组或列表中包含同类事物。

在 Java 中，**数组**（一维数组）是一种 **复杂数据结构**，因为它可以存储一系列 **基本类型** 或 **对象**。它以每个列表项都可以通过 **索引** 来引用的方式存储这些值。也就是说，数组为每个存放值的槽分配一个数字。通过这样做，程序员可以轻松找到槽中存储的值，修改它，打印它等。数组中的值被称为 **数组元素**。数组可以存储任意数据类型，无论是基本类型还是对象。

#### 使用预定义列表初始化数组

在 AP 计算机科学 A 考试中，创建数组的两种常见方式。第一种使用 **初始化列表**。当你已经知道要存储的值并且不打算再添加新元素时使用这种方式。 **一对方括号** `[]` 告诉编译器创建一个数组对象，而非普通变量。

**使用预定义列表创建数组的通用形式**

`dataType[] nameOfArray = {dataValue1, dataValue2, dataValue3, … };`

注意在 `dataType` 后面的方括号 `[]`。方括号表示该变量是指向一个数组对象的引用。

### 示例

声明一个 `String` 类型的数组，用于表示餐厅的食物选择：

![Image](img/f0216-01.jpg)

右侧的图是 `foodChoices` 数组的可视化表示。实际的食物选择字符串（Pizza、Cheeseburger 等）是数组的 **元素**，每个槽被赋予一个数字，称为 **索引**（0、1、2 等）。索引是数字，让程序员知道哪个元素位于哪个槽。索引的起始值总是 0，最后一个索引总是数组长度减 1。

![Image](img/f0216-02.jpg)

#### “Speak” 数组

谈论数组中的元素时，我们会说“Pizza 是 foodChoices 数组的第一个元素，其索引为 0”或“The element at index 2 of the foodChoices array is Tacos.”

#### `length` 字段

数组创建并初始化后，可以通过 **length** 字段询问它有多少个槽。把 length 看作数组的实例变量。注意，length 后面不跟括号，因为它不是方法。

### 示例

获取 `foodChoices` 数组的长度：

![Image](img/f0216-03.jpg)

**数组的 length**

数组的 `length` 字段返回为该数组预留的槽总数。它不返回数组中有效元素的总数。此外，由于数组的索引从 0 开始，数组的长度总是比最后一个索引大 1。

#### 使用 `new` 关键字声明数组

第二种创建数组的技术用于你知道数组长度但不确定具体数值的情况。同样，使用 **一对方括号** `[]` 告诉编译器创建数组对象而非普通变量。

**使用 `new` 创建数组的通用形式**

`dataType[] nameOfArray = new dataType[numberOfSlots];`

`dataType nameOfArray [ ] = new dataType[numberOfSlots];`

槽的数量是固定的，数组中所有元素都会获得该数据类型的默认值。你也可以先声明只有一个数组引用变量，然后在需要时使用 `new` 创建数组。

![Image](img/f0217-02.jpg)

#### 不能对数组进行调整大小

数组创建后不能调整大小。

### 示例

声明一个数组来表示高中四年级的所有学期绩点平均值（假设每年有两个学期，共八个学期）。因此，声明一个保存八个 `double` 值的数组并命名为 `myGPAs`。

![Image](img/f0217-03.jpg)

![Image](img/f0217-04.jpg)

假设你大二第二学期获得了 3.75 的绩点。

![Image](img/f0217-07.jpg)

**聪明但不够聪明**

计算机并不知道这些数字代表学生的绩点，它只是把一堆数字存储在数组中。

### 示例

从颜色名称数组中随机选择一种颜色：

![Image](img/f0218-01.jpg)

#### `ArrayIndexOutOfBoundsException`

数组的有效索引范围是 0 到数组元素数量减 1（包含）。如果你不小心使用了过大的索引（大于等于数组长度）或负数，程序会在运行时抛出 **ArrayIndexOutOfBoundsException** 运行时错误。

### 示例

声明一个 `Circle` 对象数组并尝试打印最后一个圆的半径，但会因为索引过大而抛出 `ArrayIndexOutOfBoundsException`。注意：数组长度为 6，最后一个 `Circle` 对象的索引为 5。正确写法如下：

![Image](img/f0218-03.jpg)

![Image](img/error.jpg)

**常见错误**

常见错误是不小心将数组索引设为数组的长度。由于数组索引从 0 开始，数组的最后一个索引是 **length – 1**。

![Image](img/f0218-04.jpg)

#### 遍历数组

To `traverse` an array means to move through each slot in the array, one at a time. The most common way to perform a `traversal` is to start with the first index and end with the last index. But that’s not the only way. You could start with the last index and move toward the first. You also could do all of the even indices first and then all of the odds. You get what I’m saying? Traversing an array just means that you visit every element at every index in an array.

`Print the Contents of an Array by Traversing It`

`Example`

Print out the names of all your friends on Facebook using a `for` loop. By traversing the array from the first element to the last element, you can print each friend’s name.

![Image](img/f0219-01.jpg)

![Image](img/error.jpg)

Off-by-One Error

This is a logic error that every programmer has committed at some point. It means that in a loop of some kind, your index is off by one number. You either went one index card too high or one index too low. This will result in an `ArrayIndexOutOfBoundsException` being thrown.

`The Enhanced for Loop (the for-each Loop)`

The `enhanced for loop` (aka the `for-each loop`) can also be used to traverse an array. It does not work the same way as the standard `for` loop. The `for-each` loop always starts at the beginning of the array and ends with the last element in the array. As the name indicates, the `for-each` loop iterates through each of the elements in the array, and *for each* element, the temporary variable “takes on” its value. The temporary variable is only a copy of the actual value and any changes to the temporary variable are not reflected in the actual value.

An enhanced `for` loop is simpler to write than a standard `for` loop since you don’t have to keep track of an index. The enhanced `for` loop is also less error-prone because Java automates the setup and processing of the loop control information. However, the enhanced `for` loop cannot be used to move through an array in reverse order, it cannot assign elements to an array, and since it does not have an index, it can’t track any position in the array.

General Form for the Enhanced for Loop (the for-each Loop)

![Image](img/f0219-02.jpg)

There is no loop control variable for the enhanced `for` loop (it is a `black box`). You only have access to the elements in the array, not the index. Also, the data type of the temporary variable **must** be the same as the data type of the array.

`Traversing an Array Using the Enhanced for Loop`

`Example`

Print out the names of all your friends on Facebook using a `for-each` loop. Note: `friend` is a temporary variable that is of the same data type as the data stored in the array.

![Image](img/f0220-01.jpg)

![Image](img/error.jpg)

Mistake When Printing the Contents of an Array

Beginning programmers make the mistake of trying to print the contents of an array by printing the array reference variable. The result that is printed is *garbage*. This is because the reference variable only contains the address of where the array is; it does not store the elements of the array.

![Image](img/f0220-02.jpg)

Note: The best way to print the contents of an array is to traverse the array using either a `for` loop or a `for-each` loop.

### How We Use Algorithms

In our daily lives, we develop and use algorithms all the time without realizing that we are doing it. For example, suppose your grandma calls you because she wants to watch *The Crown* using the Nexflix app on her smart TV, but she can’t figure out how to do it. You would respond to her by saying, “Hi, Grandma, well, the first thing you have to do is turn your TV on,” then yada, yada, yada until finally you say, “Press play.”

What you have just done is developed a process for how to solve a problem. Now, if she insists that you write the steps down on a notecard so she can follow it anytime she wants to, then, you will be writing the algorithm for “How to watch *The Crown* on grandma’s smart TV.”

Give a man a fish and he will eat for a day; teach a man to fish and he will eat for a lifetime.

—Chinese proverb

### Why Algorithms Are Important

The word `algorithm` can be simply defined as “a process to be followed to solve a problem.” Computer programmers use algorithms to teach the computer how to automate a process.

The number of algorithms to learn is infinite, so rather than attempting to learn all possible algorithms, my goal is to teach you *how to write an algorithm*. This will be handy on the AP Computer Science A Exam when you have to either analyze or generate code to accomplish something you’ve never done before. The two algorithm concepts in this book teach you how to think like a programmer.

Give developers a line of code and they will smile for a day; teach developers to write their own algorithms and they will smile for a lifetime.

—Coding proverb

### Algorithm Versus Pseudocode Versus Real Java Code

Algorithms are great as directions for how to do something; however, they can’t be typed into a computer as a real Java program. The integrated development environment (IDE) needs to have the correct syntax so that the compiler can interpret your code properly. Can you imagine typing in the directions for Grandma as lines of code?

So, to solve this problem, programmers translate algorithms into `pseudocode`, which is a code-like language. This pseudocode is then translated into real code that the computer will understand.

![Image](img/f0221-01.jpg)

This process is really powerful because as programming languages change, the algorithms can stay the same. In the examples that follow, I’ve written the code in Java, but it could’ve easily been written in C++, Python, etc.

Turning Your Ideas into Code

Pseudocode is an inner step when turning your ideas into code. It is code-like but does not use the syntax of any programming language.

#### The Swap Algorithm

Swapping is the concept of switching the values that are stored in two different variables. The ability to swap values is essential for sorting algorithms (explained in Unit 7). To complete a swap, you need to use a temporary variable to store one of the values.

**Problem:** Swap the values inside two integer variables. For example, if a = 6 and b = 8, then make a = 8 and b = 6.

**Algorithm:**

Step 1: Let a = 6 and b = 8

Step 2: Create a temporary variable called c

Step 3: Assign c the value of a

Step 4: Assign a the value of b

Step 5: Assign b the value of c

Step 6: Now, the value of a is 8 and b is now 6

**Pseudocode:**

set a = 6

set b = 8

c = a

a = b

b = c

**Java Code:**

![Image](img/f0222-01.jpg)

#### The Copy Algorithm for the Array

Making a copy of an array means to create a brand-new object that is a duplicate of the original. This is different from creating a new array variable that references the original array. That was called making an alias. It is easy for new programmers to make the mistake of thinking that these two are the same.

**Problem:** Suppose you have an array of integers. Make a new array object that is a copy of this array. The two arrays should contain the same exact values but not be the same object. In Unit 7 we will modify the code to work with an `ArrayList` of `Integers`.

**Algorithm:**

Step 1: Create an array that is the same length as the original

Step 2: Look at each of the values in the original array one at a time

Step 3: Assign the value in the copy to be the corresponding value in the original

Step 4: Continue until you reach the last index of the original array

**Pseudocode:**

Create an array called duplicate that has the same length as the original array for (iterate through each element in the original array)

![Image](img/f0222-02.jpg)

##### Java Code 1: Java code using a for loop

![Image](img/f0223-01.jpg)

##### Java Code 2: Java code using a for-each loop

![Image](img/f0223-02.jpg)

![Image](img/error.jpg)

Copying an Array Reference Versus Copying an Array

-   [下面的代码演示了在尝试复制数组时常见的错误。](https://f0223-03.jpg)

-   这段代码使引用变量的复制指向与原始变量相同的对象。这意味着如果你在复制变量中更改一个值，原始变量中的值也会随之改变。这段代码 **并未创建一个与原始对象相同的副本**。

-   这段代码使两个引用变量都指向同一个对象（即原始变量所指向的对象）。

#### The Accumulate Algorithm

-   假设你有一个包含所有棒球队球员的列表，想要找出该队伍总共的安打数。作为人类，我们可以很容易地做到这一点，只需将它们相加。但是如何教会计算机完成这项工作呢？

-   **通用问题**：为棒球队的所有安打求和。

-   **精炼问题**：编写一个方法，计算安打数组中所有安打的总和。

-   **最终问题**：编写一个名为 `findSum` 的方法，包含一个参数：`int` 数组。该方法应返回数组中所有元素的总和。在 Unit 7 中，我们将修改代码以使其适用于 `ArrayList` 的 `Integer`，而在 Unit 8 中，我们将修改代码以使其适用于 `int` 值的二维数组。

-   **算法**：

    -   步骤 1：创建一个名为 `sum` 的变量，并将其设置为零。

    -   步骤 2：查看列表中的每个元素。

    -   步骤 3：将元素添加到 `sum` 中。

    -   步骤 4：继续，直到到达列表的末尾。

    -   步骤 5：返回 `sum`。

-   **伪代码**：

    ![Image](img/f0224-03.jpg)

-   **Java 代码 1：使用 for 循环的 Java 代码**

    ![Image](img/f0224-01.jpg)

-   **Java 代码 2：使用 for-each 循环的 Java 代码**

    ![Image](img/f0224-02.jpg)

#### The Find-Highest Algorithm

-   你最喜欢的视频游戏中的最高分是多少？随着更多人玩游戏，计算机如何找出列表中的最高分？

-   **通用问题**：在视频游戏的所有分数中找出最高分。

-   **精炼问题**：编写一个方法，找出分数列表中的最高分。

-   **最终问题**：编写一个名为 `findHigh` 的方法，包含一个参数：`int` 数组。该方法应返回数组中最大的值。在 Unit 7 中，我们将修改代码以使其适用于 `ArrayList` 的 `Integer`，而在 Unit 8 中，我们将修改代码以使其适用于 `int` 值的二维数组。

-   **算法**：

    -   步骤 1：创建一个名为 `high` 的变量，并将其设置为列表中的第一个元素。

    -   步骤 2：查看列表中的每个分数。

    -   步骤 3：如果分数大于 `high` 分数，则将其设置为新的 `high` 分数。

    -   步骤 4：继续，直到到达列表的末尾。

    -   步骤 5：返回 `high` 分数。

-   **伪代码**：

    ![Image](img/f0225-05.jpg)

-   **Java 代码 1：使用 for 循环的 Java 代码**

    ![Image](img/f0225-01.jpg)

-   **Java 代码 2：使用 for-each 循环的 Java 代码**

    ![Image](img/f0225-02.jpg)

#### 解决方案 1：将最高值设置为列表中的第一个元素。

-   **算法**：

    -   步骤 1：创建一个名为 `high` 的变量，并将其设置为列表中的第一个元素。

    -   步骤 2：查看列表中的每个分数。

    -   步骤 3：如果分数大于 `high` 分数，则将其设置为新的 `high` 分数。

    -   步骤 4：继续，直到到达列表的末尾。

    -   步骤 5：返回 `high` 分数。

-   **伪代码**：

    ![Image](img/f0225-05.jpg)

-   **Java 代码 1：使用 for 循环的 Java 代码**

    ![Image](img/f0225-01.jpg)

-   **Java 代码 2：使用 for-each 循环的 Java 代码**

    ![Image](img/f0225-02.jpg)

#### 解决方案 2：将最高值设置为一个极低的值。

-   解决高/低问题的另一种方法是修改前一个算法的第一步。

-   **步骤 1**：创建一个名为 `high` 的变量，并将其设置为一个 **极其、极其小的数值**。

-   该算法的前提是该 **极其、极其小的数值** 必须保证小于列表中至少一个数值。在 Java 中，我们可以使用 `Integer` 类的公共字段来解决这个问题。

  `int high = Integer.MIN_VALUE;`

-   同样，为了解决 **找最小值** 的问题，可以将 `low` 设置为一个 **极其、极其大的数值**。

  `int low = Integer.MAX_VALUE;`

![images](img/power.jpg)

### 查找列表中的最小项

-   如果我们修改前面的例子，将其改为查找列表中的 **最低分**，则 `if` 语句中的比较运算符将从大于 (`>`) 变为小于 (`<`)。

### ![Image](img/arrow1.jpg) 快速回顾

#### 数组

-   数组是一个复杂的数据结构，可以存储同一种数据类型的列表。

-   数组也被称为一维（或 1D）数组。

-   数组可以通过赋予它一个预定义的列表来创建。

-   数组可以使用 `new` 关键字创建。

-   数组可以存储基本数据类型或对象引用类型。

-   尽管数组是对象，但它们没有方法。

-   数组有一个公共字段，名为 `length`。

-   数组的长度是指可以存储在数组中的元素数量，并在数组创建时确定。

-   数组的长度在声明后无法调整，即数组在创建后不能变得更短或更长。

-   数组的 `length` 字段返回数组中存在的总位置数量，而不是数组中有意义的元素数量。

-   数组的元素指的是存储在数组中的项目。

-   数组的索引指的是元素在数组中的位置。

-   数组的第一个索引是 0。数组的最后一个索引是其长度减 1。

-   数组中未使用的索引会自动获得该数据类型的默定值。

-   如果数组包含对象，它们的默认值为 `null`。在使用数组中的每个元素之前，需要为每个元素实例化对象。

-   使用超出数组范围的索引会抛出 `ArrayIndexOutOfBoundsException`。

#### 遍历数组

-   遍历数组指的是访问数组中每个元素的过程。

-   虽然有许多遍历数组的方法，但最常见的方式是从头开始，逐个访问直到末尾。

-   根据情况，有时可能需要从尾部开始，逐个访问直到头部。

-   有时可能需要只遍历数组的一部分。

-   使用 `for` 循环遍历数组时，访问最后一个元素时应使用 `length - 1` 而不是 `length`。

-   增强 `for` 循环会遍历数组中的每个元素，而无需使用索引。

-   增强 `for` 循环也称为 for-each 循环。

-   增强 `for` 循环总是从第一个元素开始，到最后一个元素结束。

-   当你不需要知道每个元素的索引，且不需要以任何方式改变元素时，使用增强 `for` 循环。

#### 算法和伪代码

-   该概念的目的是教你如何将一个想法转化为代码。

-   算法是一系列步骤，当按顺序执行时，会产生特定的结果。

-   算法是软件开发的极其重要组成部分，因为你需要教会计算机如何自己完成某事。

-   伪代码是算法和真实代码之间的混合体。

-   伪代码不使用正确的语法，也不是在 IDE 中输入的。

-   伪代码帮助你将算法转化为真实代码，因为它看起来像代码，比算法更加精炼。

-   程序员将算法转化为伪代码，然后将伪代码转化为真实代码。

#### 交换算法

-   交换算法允许你交换两个不同变量中的值。

-   要交换两个不同变量中的值，必须创建一个临时变量来存储其中一个原始变量的值。

#### 复制算法

-   复制算法用于创建数据结构的复制版本。

-   它会查看原始列表中的每个元素，并将其赋值给复制列表。

-   复制版本不是原始版本的别名；它是一个新对象，包含与原始对象相同的所有值。

#### 累积算法

-   累积算法用于计算列表中所有项目的总和。

-   它会逐个查看列表中的元素，并将值添加到总和中。

#### 找最大值算法

-   找最大值算法用于找出列表中的最大值。

-   它逐个检查列表中的每个元素，将其值与当前最高值进行比较。

-   实现此算法的常见方法是将最高值初始化为列表中的第一个值，或初始化为一个极小的负数。

-   最高值查找算法可以被修改以在列表中找到最小的项。

### ![Image](img/arrow1.jpg) Review Questions

## Basic Level

**1.**  Consider the following code segment.

![Image](img/f0228-01.jpg)

What is printed as a result of executing the code segment?

(A)     `0`

(B)     `13`

(C)     `26`

(D)     `28`

(E)     `56`

**2.**  Consider the following code segment.

![Image](img/f0228-02.jpg)

What is printed as a result of executing the code segment?

(A)     `0`

(B)     `1`

(C)     `3`

(D)     `7`

(E)     `16`

**3.**  Consider the following code segment.

![Image](img/f0228-03.jpg)

What is printed as a result of executing the code segment?

(A)     `91`

(B)     `746`

(C)     `913`

(D)     `79416385`

(E)     `416385`

**4.**  Which segment of code will correctly count the number of even elements in an array arr?

![Image](img/f0229-01.jpg)

(A)     I only

(B)     II only

(C)     III only

(D)     I and II only

(E)     II and III only

**5.**  Consider the following code segment.

![Image](img/f0229-04.jpg)

What will be printed after the code segment is executed?

(A)     9.05 9.05 6.13 4.2 2.25

(B)     7.28 2.25 4.2 6.13 9.05

(C)     6.13 4.2 2.25 7.28 7.28

(D)     9.05 6.13 4.2 2.25 7.28

(E)     Nothing will be printed. An `ArrayIndexOutOfBoundsException` will occur.

### Advanced Level

**6.**  Consider the following code segment.

![Image](img/f0229-05.jpg)

What values are stored in array `nums` after executing the code segment?

(A)     `ArrayIndexOutOfBoundsException`

(B)     `{2, 2, 3, 3, 4, 4, 5, 5}`

(C)     `{0, 0, 1, 3, 5, 7, 9, 11}`

(D)     `{0, 0, 1, 1, 3, 4, 5, 6}`

(E)     `{0, 0, 1, 2, 2, 3, 4, 5}`

**7.**  A postcondition of a method is: arr\[0\] > arr\[k\] for all k such that 0 < k < arr.length. Which of the following is a correct conclusion?

(A)     All values in the array are identical.

(B)     The array elements are in ascending order.

(C)     The array elements are in descending order.

(D)     The smallest value in the array is arr\[0\].

(E)     The largest value in the array is arr\[0\].

**8.**  Consider the following code segment intended to count the number of elements in array `fruits` that contain the letter “e”.

![Image](img/f0230-01.jpg)

Which of the following substitutions for <statement> will cause the segment to work as intended?

![Image](img/f0230-02.jpg)

**9.**  Consider two parallel arrays which contain the names and corresponding scores of players in a trivia game.

![Image](img/f0230-03.jpg)

Which of the following code segments correctly prints the names and scores of all the players who scored above `high`?

![Image](img/f0230-04.jpg)

**10.**  Count the number of occurrences.

Write a method that counts the number of values in an array that are between a lower bound and an upper bound. The method takes as parameters a double array, and two doubles representing lower and upper respectively. The method should return a count representing the number of elements in the array that are greater than or equal to the upper bound or less than or equal to the lower bound.

For example, if the lower bound is 250.0, the upper bound is 750.0, and the array passed to the method is:

![Image](img/f0231-01.jpg)

The method should return the value 6.

![Image](img/f0231-02.jpg)

**11.**  Determine the relative strength index of a stock.

The relative strength index (RSI) of a stock determines if the stock is overpriced or underpriced. The range of the RSI is from 0 to 100 (inclusive). If the value of the RSI is greater than or equal to 70, then the stock is determined to be overpriced and should be sold.

Write a method that takes an array of RSI values for a specific stock and determines when the stock is overpriced. The method has one parameter: a double array. The method should return a new array of the same length as the parameter array. If the value in the RSI array is greater than 70, set the value in the overpriced array to `true`. If the RSI value is less than or equal to 70, set the value in the overpriced array to `false`.

For example, if the RSI array passed to the method is:

![Image](img/f0231-03.jpg)

The overpriced array that is returned by the method will be:

![Image](img/f0231-04.jpg)

**12.**  Fill an array with even numbers.

Write a method that fills an array with random even numbers. The method takes two parameters: the number of elements in the array and the range of the random numbers (0–number inclusive).

For example:

![Image](img/f0231-05.jpg)

result contains the following (results will change each time program is run):

![Image](img/f0231-06.jpg)

### ![Image](img/arrow1.jpg) Answers and Explanations

Bullets mark each step in the process of arriving at the correct solution.

**1.**  The answer is D.

•     This is a `for-each` loop. Read it like this: “For each int (which I will call val) in values.…”

•     The loop will go through each element of the array values and add it to number. Notice that number starts at 13.  

![Image](img/f0232-01.jpg)

**2.**  The answer is D.

•     values\[total\] = values\[3\] = -2. Remember to start counting at 0.

•     3 + -2 = 1, now total = 1.

•     values \[total\] = values\[1\] = 6.

•     1 + 6 = 7 and that is what is printed.

**3.**  The answer is C.

•     Let’s lay out the array along with its indices.

![Image](img/f0232-02.jpg)

•     The first time through the loop, i = 3.

•     values\[3–2\] = values \[1\] = 9 Print it.

•     Next time through the loop, i = 5.

•     values \[5–2\] = values \[3\] = 1 Print it.

•     Next time through the loop, i = 7.

•     Remember that even though the last index is 7, the length of the array is 8.

•     values \[7–2\] = values\[5\] = 3 Print it.

•     We exit the loop having printed “913”.

**4.**  The answer is B.

•     Segment I checks if the index of the element is even, not the element itself.

•     Segment II correctly checks if the element is even.

•     Segment III correctly checks if the element is even, but because the increment is +2, it doesn’t check each element of the array.

**5.**  The answer is A.

•     The loop will shift each of the elements to the right starting at the second to last element.

**6.**  The answer is D.

•     On entering the loop, nums = {0, 0, 1, 1, 2, 2, 3, 3} and i = 3. Set nums\[4\] to 3.

•     Now nums = {0, 0, 1, 1, 3, 2, 3, 3} and i = 4. Set nums\[5\] to 4.

•     Now nums = {0, 0, 1, 1, 3, 4, 5, 3} and i = 5. Set nums\[6\] to 5.

•     Now nums = {0, 0, 1, 1, 3, 4, 5, 6} and i = 6. Set nums\[7\] to 6.

•     Now nums = {0, 0, 1, 1, 3, 4, 5, 6} and i = 7. nums.length − 1 = 7, so exit the loop.

**7.**  The answer is E.

•     Since the condition arr\[0\] > arr\[k\] holds true for each element, element arr\[0\] must be the largest.

**8.**  The answer is D.

•     The `indexOf` method returns the index of the first occurrence of the string parameter.

•     If the string parameter is not found the value –1 is returned.

**9.**  The answer is C.

•     Since we need to access the index of an element a standard `for` loop must be used, not a `for-each` loop.

•     Only elements that are above `high` should be printed, so the inequality > must be used.

**10.**  Count the number of occurrences.

**Algorithm:**

Step 1: Initialize a counter to 0

Step 2: Look at each value in the list

Step 3: 如果值小于或等于 lower，则计数器加 1

Step 4: 如果值大于或等于 upper，则计数器加 1

Step 5: 继续，直到你到达列表的末尾

Step 6: 返回计数器

**Pseudocode:**

创建并初始化一个临时计数器变量

for (遍历数组中的所有值)

![Image](img/f0233-01.jpg)

**Java 代码:**

![Image](img/f0233-02.jpg)

**11.**  Determine the relative strength index of a stock.

**Algorithm:**

Step 1: 创建一个名为 `temp` 的数组，长度与参数数组相同

Step 2: 查看数组中的每个分数

Step 3: 如果分数 > 70，则将 temp 数组中对应位置的元素设为 true；否则设为 false

Step 4: 继续，直到你到达列表的末尾

Step 5: 返回 temp

**Pseudocode:**

创建一个长度与参数数组相同的布尔数组 temp

for (遍历参数数组中的所有元素)

![Image](img/f0234-01.jpg)

**Java 代码:**

![Image](img/f0234-02.jpg)

**12.**  Fill an array with even numbers.

**Algorithm:**

Step 1: 创建一个名为 `temp` 的整数数组，长度与参数数组相同

Step 2: 循环次数等于参数数组的长度

Step 3: 在适当范围内生成一个随机数

Step 4: 如果随机数不是偶数，则在适当范围内再次生成随机数

Step 5: 将随机数放入数组中

Step 6: 继续，直到完成正确的迭代次数

Step 7: 返回 temp

**Pseudocode:**

创建一个长度与参数数组相同的整数数组 temp

for (遍历次数等于参数数组长度)

![Image](img/f0234-03.jpg)

**Java 代码:**

![Image](img/f0235-01.jpg)

## UNIT 7

## ArrayList

## IN THIS UNIT

## Summary: In this unit we will discuss the `ArrayList`, along with some of the methods that are used to access and manipulate its elements. In addition to the array algorithms that were introduced in the previous unit (which can also be done with `ArrayLists`), we will look at searching and sorting algorithms that you need to know for the AP Computer Science A Exam.

![Images](img/idea.jpg)

## Key Ideas

![image](img/star.jpg) An `ArrayList` is a data structure that can store a list of objects from the same class.

![image](img/star.jpg) An `ArrayList` resizes itself as objects are added to and removed from the list.

![image](img/star.jpg) To traverse a data structure means to visit each element in the structure.

![image](img/star.jpg) The enhanced `for` loop (`for-each` loop) is a special looping structure that can be used by either arrays or `ArrayLists`.

![image](img/star.jpg) The sequential search algorithm finds a value in a list.

![image](img/star.jpg) The `Insertion Sort`, `Selection Sort`, and `Merge Sort` are sorting routines.

### The `ArrayList`

#### Definition of an `ArrayList`

An `ArrayList` is a **complex data structure** that allows you to add or remove objects from a list and it changes size automatically.

#### Declaring an `ArrayList` Object

An `ArrayList` is an object of the `ArrayList` class. Therefore, to create an `ArrayList`, you need to use the keyword `new` along with the constructor from the `ArrayList` class. You also need to know the data type of the objects that will be stored in the list. The `ArrayList` uses a pair of **angle brackets**, < and >, to enclose the class name of the objects it will store.

Using a raw `ArrayList` (without <>) allows the user to store a different data type in each position of the `ArrayList`, which is not typically done since Java 5.0 arrived in 2004. The `ArrayList <E>` notation is preferred over `ArrayList` because it allows the compiler to find errors that would otherwise be found at run-time. You might see some released AP Computer Science A Exam questions from previous years using this syntax.

General Form for Declaring an `ArrayList`

ArrayList <E> nameOfArrayList = new ArrayList<E>();

where the generic type E specifies the type of elements that will be stored in the `ArrayList`

The graphic that follows is a visual representation of what the `ArrayList` looks like in memory.

### Example

Declare an `ArrayList` of `Circle` objects. Please note that I am referring back to the Circle class from Unit 5 and that the memory address is simulated.

![Image](img/f0238-02.jpg)

#### An `ArrayList` Always Starts Out Empty

When you create an `ArrayList` object, it is empty, meaning that there are no items in the list. It’s like when your mom starts to make a “To Do” list and she writes the words “To Do” on the top of a piece of paper. The list is created but there is nothing in the list.

### Example

![Image](img/f0239-01.jpg)

#### An `ArrayList` Is Resizable

When your mom writes, “Go grocery shopping” or “Buy awesome video game for favorite child” on her To Do list, the size of the list grows. As she completes a task on the list, she crosses it out and the size of the list shrinks. This is exactly how an `ArrayList` is resized.

Automatic Resizing

An awesome feature of the `ArrayList` is its ability to resize itself as elements are added to or removed from the list. The `size()` method (explained later) immediately recalculates how many elements are in the list.

#### An `ArrayList` Requires an `import` Statement

The `ArrayList` is not part of the built-in Java language package, so you have to let the compiler know that you plan on creating an `ArrayList` by putting an import statement prior to the class declaration.

`import java.util.ArrayList;`

You will not see or need to write any import statements on the AP Computer Science A exam.

#### An `ArrayList` Can Only Store Objects

Unlike the array, which could store primitive variables like an `int` or `double`, as well as objects, like Strings, the `ArrayList` *can only store objects*. If you want to store an `int` or `double` in an `ArrayList`, you must use the `Integer` or `Double` wrapper classes. This is one of the reasons why the wrapper classes were created (refer back to Unit 2 when they were introduced).

### Example

Create an `ArrayList` of `Integer`. Add an `int` to the `ArrayList` and secretly watch as the `int` is automatically converted to an integer using a secret, Java black box technique called **autoboxing** (also introduced back in Unit 2).

![Image](img/f0239-03.jpg)

-   [执行第 3 行代码后：`ArrayList` 中有 3 个 `Circle` 对象。](https://f0240-04.jpg)

#### 另一个 `add` 方法

[The **add(int index, E object)** 方法将对象插入到 `ArrayList` 中的 `index` 位置，将该位置及其后面的所有对象向后移动一个位置。受 **add** 操作影响的对象的索引会被递增。该方法不返回任何值。]

-   [可以将 `ArrayList` 可视化为学校的午餐队列。想象有 10 名学生站成队伍，编号从 0 到 9，其中 0 号学生排在最前面。]

-   [假设发生不可思议的情况：一名学生插队。他/她将自己插入到列表中。如果 *cutter*（插队者）现在是第 3 个人，那么他/她执行了 `add(2, "cutter")`。此操作会影响所有在 *cutter* 之后的队友。原来在位置 2 的人现在变成了位置 3，原来在位置 3 的人现在变成了位置 4，以此类推。*cutter* 后面的每个人的索引都 **增加了 1**。]

`line 4: myCircles.add(1, new Circle(4));`

-   [执行第 4 行代码后：radius 为 4 的 `Circle` 对象被插入到索引为 1（即第二个位置）的位置。之后的所有 `Circle` 对象都必须向后移动一个槽位。](https://f0241-02.jpg)

#### `size` 方法

-   [The **size()** 方法返回 `ArrayList` 中元素的数量。请注意，这与数组的 **length** 域不同，后者告诉你为数组预留了多少个槽位，而不是实际存储的有效元素数量。](https://error.jpg)

`IndexOutOfBoundsException`

-   [就像 1D 数组和 2D 数组一样，如果你尝试访问列表范围之外的对象，会出错。使用 `ArrayList` 时出现的错误称为 `IndexOutOfBoundsException`。](https://f0241-04.jpg)

-   [索引 88 不在 0 ≤ index ≤ myCircle.size() 的范围内。](https://f0241-04.jpg)

#### `remove` 方法

-   [The **remove(int index)** 方法删除列表中位于 `index` 位置的对象。之后的所有对象都会向下移动一个索引位置。该方法还会返回被删除对象的引用。](https://f0242-01.jpg)

-   [执行第 6 行代码后：原来在索引 2 的 `Circle` 对象被移除（半径为 0.0 的圆）。之后的 `Circle` 对象都会向下移动一个槽位，`someCircle` 现在指向被移除的 `Circle` 对象。](https://f0242-02.jpg)

#### `get` 方法

-   [The **get(int index)** 方法返回 `ArrayList` 中位置 `index` 的对象。它不移除对象，只是返回对象引用的副本，从而创建了别名（多个引用指向同一个对象）。`index` 的值必须大于等于 0 且小于 `ArrayList` 的大小。](https://f0242-03.jpg)

### 示例

-   [获取索引 2 的 `Circle` 对象并赋值给另一个 `Circle` 引用变量：](https://f0242-03.jpg)

#### `set` 方法

-   [The **set(int index, E object)** 方法将 `ArrayList` 中位置 `index` 的对象替换为 `object`。它返回原来位于 `index` 位置的对象引用。](https://f0242-04.jpg)

![Image](img/power.jpg)

-   [你将获得一张 Java 快速参考表，可用于选择题和自由响应题，其中列出了可能在考试中包含的 `ArrayList` 类方法。考试前请务必熟悉它。](https://power.jpg)

**`length` 与 `size()` 与 `length()`**

-   [要获取数组的槽位数量，使用 `length` 域。](https://f0245-01.jpg)

-   [要获取 `ArrayList` 中的对象数量，使用 `size()` 方法。](https://f0245-01.jpg)

-   [要获取字符串中的字符数量，使用 `length()` 方法。](https://f0245-01.jpg)

#### 使用 `for` 循环遍历 `ArrayList`

-   [遍历是通过迭代访问数组或 `ArrayList` 中每个元素的方式。以下代码使用 `for` 循环打印 `ArrayList` 中每个 `Circle` 对象的面积。代码通过 `get` 方法获取每个 `Circle` 对象，然后调用 `getArea` 方法。](https://f0243-01.jpg)

#### 使用增强 `for` 循环遍历 `ArrayList`

-   [增强 `for` 循环（`for-each` 循环）可与 `ArrayList` 一起使用。以下代码打印 `ArrayList` 中每个 `Circle` 对象的面积。请注意，临时变量 `element` 的数据类型与 `ArrayList` 中的对象相同。与上面的普通 `for` 循环不同，增强 `for` 循环不使用循环控制变量，因此 **不需要 `get(i)` 方法**，因为变量 `element` 是每次循环的 `Circle` 对象的副本，可以直接调用 `getArea` 方法。](https://f0243-02.jpg)

#### 打印 `ArrayList` 的内容

-   [与数组不同，`ArrayList` 的内容可以通过打印引用变量来显示到控制台。内容以方括号括起来，元素之间用逗号分隔。](https://f0244-02.jpg)

-   [如果想在打印 `ArrayList` 内容时格式化输出，应该遍历 `ArrayList`。](https://error.jpg)

#### 不要在增强 `for` 循环中使用 `remove()`

-   [在遍历过程中删除元素需要特殊技术以避免跳过元素。请 **永远不要** 在增强 `for` 循环中使用 `remove` 方法来删除 `ArrayList` 中的项目。该循环不使用索引，因此无法安全删除元素。]

-   [如果必须删除元素，请使用带索引的 `while` 循环。递增索引以访问下一个元素。但是，如果执行删除操作，**不要递增索引**。](https://f0244-01.jpg)

#### 避免运行时异常

-   [由于 `ArrayList` 的索引从 0 开始，到元素数量减 1 结束，访问超出范围的索引会导致 `ArrayIndexOutOfBoundsException` 被抛出。](https://power.jpg)

-   [在使用增强 `for` 循环遍历 `ArrayList` 时，修改其大小（添加或删除元素）会导致 `ConcurrentModifcationException` 被抛出。因此，使用增强 `for` 循环遍历 `ArrayList` 时，**不要添加或删除元素**。](https://power.jpg)

-   [你将获得一张 Java 快速参考表，可用于选择题和自由响应题，其中列出了可能在考试中包含的 `String` 类方法。考试前请务必熟悉它。](https://f0245-01.jpg)

### array vs ArrayList

-   [数组和 `ArrayList` 都用于存储数据集合，因此你只需选择适合你代码的一个（有选择权真是太好了）。它们都有局限性。数组的大小在声明时必须确定且不可更改，而 `ArrayList` 会根据需要动态增长和缩小。`ArrayList` 只能存储对象（如 `String`、`Circle`、`Integer`），而数组可以存储基本类型（int、double、boolean）或对象。]

-   [添加或移除 `ArrayList` 中的元素需要调用方法，而数组通常需要编写循环来移动所有元素以腾出空间。]

-   [下面是数组与 `ArrayList` 之间差异的总结。](https://f0245-02.jpg)

### The Accumulate Advanced Algorithm

-   [你被高中棒球队雇佣来编写计算球员统计数据的程序。你决定创建一个名为 `BaseballPlayer` 的类。每个 `BaseballPlayer` 都有姓名、`numberOfHits`（安打数）和 `numberOfAtBats`（上垒次数）。`BaseballRunner` 有一个名为 `roster` 的 `BaseballPlayer` 数组。你的目标是计算球队的打击率。](https://wiki.example.org/feynmans_learning_method) 的灵感源于诺贝尔物理奖获得者 **理查德·费曼**。

1. 运用费曼技巧，你只需花上 `20 min` 就能深入理解知识点，而且记忆深刻，*难以遗忘*。

```
