
此处的签名（方法名加参数类型）分别为 `print(int)` 和 `print(double)`。参数名 `x` 无关紧要。选项 A 正确：当方法退出时，所有局部变量和参数都会超出作用域（被擦除）。选项 B 正确：静态方法作用于整个类。只有实例方法拥有隐式的 `this` 参数。即使对于对象参数，选项 D 也是正确的：它们的引用是按值传递的。注意选项 E 正确，因为可能存在两个具有不同签名但参数数量相同的构造方法（例如，一个用于 `int` 参数，一个用于 `double` 参数）。

[5](#48_Chapter40.xhtml#fn3-5). **(B)** 构造对象需要关键字 `new` 和 `Date` 类的构造方法。排除选项 D 和 E，因为它们省略了 `new`。类名 `Date` 应出现在赋值语句的右侧，紧随关键字 `new` 之后。这排除了选项 A 和 C。

[6](#48_Chapter40.xhtml#fn3-6). **(C)** 代码段 III 将导致抛出 `NullPointerException`，因为 `d` 是空引用。不能为空引用调用方法。代码段 II 的效果是将 `null` 赋值给 `d1` 和 `d2`——晦涩但并不错误。代码段 I 创建了对象引用 `d1`，然后声明了第二个引用 `d2`，它指向与 `d1` 相同的对象。

[7](#48_Chapter40.xhtml#fn3-7). **(E)** 客户端程序无法访问私有实例变量。

[8](#48_Chapter40.xhtml#fn3-8). **(E)** 所有选项均正确。由于 `write()` 是 `Date` 的实例方法，因此在其实现代码中使用私有数据成员是可以的。代码段 III 打印 `this`，即当前的 `Date` 对象。这种用法是正确的，因为 `write()` 是 `Date` 类的一部分。`toString()` 方法保证按要求的格式打印日期。（参见 [第 153 页](#50_Chapter42.xhtml#page_153)。）

[9](#48_Chapter40.xhtml#fn3-9). **(A)** 这里的思路是分别读入月、日、年三个变量，然后使用 `new` 和带有三个参数的 `Date` 类构造方法来构造所需的日期。代码段 II 无效，因为 `month()`、`day()` 和 `year()` 是访问器方法，用于访问现有值，不能用于将新值读入 `bDate`。代码段 III 错误，因为它试图从客户端程序访问私有实例变量。

[10](#48_Chapter40.xhtml#fn3-10). **(A)** 代码段 I 不会创建第二个对象。它只是导致 `d2` 指向与 `d1` *相同* 的对象，这并非题目所要求。关键字 `new` *必须* 用于创建新对象。

[11](#48_Chapter40.xhtml#fn3-11). **(C)** 当 `recentDate` 在 `main()` 中声明时，其值为 null。回顾一下：方法无法替换对象引用，因此 `recentDate` 保持为 null。注意该程序的意图是将 `recentDate` 更改为指向更新后的 `oldDate` 对象。然而，代码并未做到这一点。选项 A 错误：没有使用空引用调用方法。选项 B 错误，因为 `addYears()` 是修改器方法。即使方法不改变其对象参数的地址，它也可以改变对象的内容，这正是此处发生的情况。选项 D 和 E 错误，因为 `addCentury()` 方法无法改变其 `recentDate` 参数的值。

[12](#48_Chapter40.xhtml#fn3-12). **(B)** 方法 `getPondTemperature` 是唯一适用于多只青蛙的方法。因此它应该是静态的。所有其他方法都直接与某一特定的 `Frog` 对象相关。因此 `f.swim()`、`f.die()`、`f.getWeight()` 和 `f.eat()` 都是 `Frog` 类的单个实例 `f` 的合理方法。另一方面，说 `f.getPondTemperature()` 是讲不通的。说 `Frog.getPondTemperature()` 更合理，因为同一个值将适用于该类中的所有青蛙。

[13](#48_Chapter40.xhtml#fn3-13). **(E)** 以下是在 `strangeMethod(a, b)` 开始时的内存槽：

![images](images/f126-01.jpg)

退出 `strangeMethod(a, b)` 之前：

![images](images/f126-02.jpg)

注意退出前输出了 `9 27`。退出 `strangeMethod(a, b)` 后，内存槽为

![images](images/f126-03.jpg)

下一步输出 `6 3`。

[14](#48_Chapter40.xhtml#fn3-14). **(C)** `reduce()` 方法仅用于 `Rational` 类实例方法的实现中。它是一个私有辅助方法。

[15](#48_Chapter40.xhtml#fn3-15). **(D)** `Rational` 类中的构造方法均不接受实数参数。因此，选项 D 中的实数参数将需要转换为整数。由于通常将实数截断为整数会涉及精度损失，因此不会自动执行——你必须显式地使用强制类型转换来完成。省略强制类型转换会导致编译时错误。

[16](#48_Chapter40.xhtml#fn3-16). **(E)** 必须使用新计算出的 `numer` 和 `denom` 创建一个新的 `Rational` 对象。然后必须在返回前对其进行约简。选项 A 错误，因为它没有正确创建新对象。选项 B 返回一个正确构造的对象，但未经过约简。选项 C 对当前对象 `this` 进行约简，而不是新对象 `rat`。选项 D 错误，因为它为 `Rational` 类调用 `reduce()`，而不是为特定的 `rat` 对象调用。

[17](#48_Chapter40.xhtml#fn3-17). **(D)** `Rational` 类的 `plus` 方法只能由 `Rational` 对象调用。由于 `n` 是 `int`，选项 D 中的语句将导致错误。

[18](#48_Chapter40.xhtml#fn3-18). **(B)** 这是一个*别名*的例子。关键字 `new` 仅使用了一次，这意味着仅构造了一个对象。以下是每次声明后的内存槽：

![images](images/f127-01.jpg)

[19](#48_Chapter40.xhtml#fn3-19). **(E)** 注意 `isValidTemp` 是 `Temperature` 类的静态方法，这意味着它应该用类名 `Temperature` 来调用，如选项 E 所示。不应使用 `Temperature` 对象 `t` 来调用该方法，如选项 C 所示。（即使 `t.isValidTemp` 可能有效，但不鼓励使用。好的编译器会给出警告。）选项 A 不是好选择，因为它不够健壮：它允许程序使用可能无效的数据继续运行。选项 B 失败，因为它使用了 `isNotValidTemp`，这是程序中不存在的方法。选项 D 失败，因为 `isValidTemp` 不是 `TempTest` 类的方法。

[20](#48_Chapter40.xhtml#fn3-20). **(D)** 必须构造一个新的 `Temperature` 对象，以防止当前 `Temperature` 被更改。直接将转换公式应用于 `degrees` 的代码段 I 是最佳方式。代码段 II 虽然不是最佳算法，但确实有效。语句

![images](images/f127-05.jpg)

的效果是将 `result` 温度升高 32 度，完成转换。代码段 III 失败，因为

![images](images/f127-06.jpg)

会改变当前对象的 `degrees` 实例变量，

![images](images/f127-07.jpg)

也是如此。为了正确，这些操作必须应用于 `result` 对象。

[21](#48_Chapter40.xhtml#fn3-21). **(A)** 这是一个关于变量作用域的问题。在 `main()` 中声明的 `count` 变量的作用域延伸至 `main()` 的右大括号。在 `doSomething()` 中，`count` 是局部变量。在 `for` 循环中的方法调用后，局部变量 `count` 超出作用域，打印的值是 `main()` 中 `count` 的值，它保持不变，仍为 `0`。

[22](#48_Chapter40.xhtml#fn3-22). **(A)** 以下是在第一次调用 `someMethod` 之前的内存槽：

![images](images/f128-01.jpg)

即将退出 `x = someMethod(y)` 时：

![images](images/f128-02.jpg)

退出

`x = someMethod(y);`

后：`x` 已被重新赋值，因此 `num = 2` 的对象已被回收：y

![images](images/f128-03.jpg)
