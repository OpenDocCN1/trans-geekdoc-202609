
# 重载、作用域、this 关键字、引用与方法参数

## 重载

注意，就重载而言，方法的返回类型无关紧要。你不能拥有两个签名相同但返回类型不同的方法。编译器会报错称方法调用不明确。

在同一个类中拥有多个构造器是重载的一个示例。重载构造器提供了多种初始化该类对象的方式。

## 作用域

变量或方法的*作用域*是指该变量或方法可见且可被访问的区域。

类的实例变量、静态变量和方法属于该类的作用域，该作用域从类定义的左大括号延伸到右大括号。在类内部，所有实例变量和方法均可访问，且可直接通过名称引用（无需点运算符！）。

*局部变量*是在方法内部定义的。它甚至可以定义在语句内部。其作用域从声明处开始，延伸到包含其声明的代码块末尾。*代码块*是由一对 `{}` 括起来的代码片段。当退出代码块时，局部变量的内存会被自动回收。

局部变量优先于同名的实例变量。（然而，使用相同名称会给程序员带来歧义，导致错误。应避免这种做法。）

## `this` 关键字

实例方法总是为特定对象而调用。该对象是方法的*隐式参数*，并通过关键字 `this` 来引用。考试要求你掌握这一术语。

在实例方法的实现中，所有实例变量均可加上 `this` 前缀并后跟点运算符来书写。

### 示例 1

在方法调用 `obj.doSomething("Mary", num)` 中，其中 `obj` 是某个类的对象，`doSomething` 是该类的方法，括号内的 `"Mary"` 和 `num` 这些参数是*显式*参数，而 `obj` 是*隐式*参数。

### 示例 2

下面是一个将 `this` 用作参数的示例：

![images](img/f101-01.jpg)

![images](img/f101-02.jpg)

假设客户端类包含以下代码行：

```
Person p = new Person("Dan", 10);
p.printPerson();
```

`printPerson` 方法中的语句

```
System.out.println(this);
```

意味着“打印当前的 `Person` 对象”。输出应为 `Dan 10`。注意 `System.out.println` 会调用 `Person` 类的 `toString` 方法。

### 示例 3

`BankAccount` 类的 `deposit` 方法可以按如下方式引用 `balance`：

![images](img/f101-03.jpg)

在上述示例中，使用 `this` 是不必要的。

### 示例 4

考虑一个名为 `Rational` 的有理数类，它有两个私有实例变量：

![images](img/f101-04.jpg)

现在考虑 `Rational` 类的一个构造器：

![images](img/f102-01.jpg)

为显式参数和私有实例变量使用相同的名称绝对*不是*好主意。但如果你这样做了，可以通过引用 `this.num` 和 `this.denom` 来表示正在构造的当前对象，从而避免错误。（`this` 的这种特定用法不会在考试中测试。）

## 引用

### 引用类型 vs. 基本数据类型

简单的内置数据类型，如 `double` 和 `int`，以及 `char` 和 `boolean` 类型，都是*基本*数据类型。所有对象和数组都是*引用*数据类型，例如 `String`、`Random`、`int[]`、`String[][]`、`Cat`（假设程序中有一个 `Cat` 类）等。基本数据类型和引用数据类型的区别在于它们的存储方式。

请看以下语句：

![images](img/f102-02.jpg)

变量 `num1` 和 `num2` 可以被看作是内存槽，分别标记为 `num1` 和 `num2`：

![images](img/f102-03.jpg)

如果现在改变上述任一变量，另一个不会受影响。每个变量都有自己的内存槽。

将此与引用数据类型的声明进行对比。回顾一下，对象是使用 `new` 创建的：

```
Date d = new Date(2, 17, 1948);
```

该声明创建了一个引用变量 `d`，它引用一个 `Date` 对象。`d` 的值是该对象在内存中的地址：

![images](img/f102-04.jpg)

假设现在进行如下声明：

```
Date birthday = d;
```

该语句创建了引用变量 `birthday`，它包含与 `d` 相同的地址：

![images](img/f103-01.jpg)

为同一个对象拥有两个引用称为*别名*。别名可能给程序员带来意想不到的问题。语句

```
d.changeDate();
```

也会自动改变 `birthday` 所引用的对象。

程序员可能想要创建一个名为 `birthday` 的第二个对象，其属性与 `d` 完全匹配。如果不使用 `new`，就无法实现这一点。例如，

```
Date birthday = new Date(d.getMonth(), d.getDay(), d.getYear());
```

现在语句 `d.changeDate()` 将不会改变 `birthday` 对象。

### 空引用

声明

```
BankAccount b;
```

定义了一个未初始化的引用 `b`。（构造 `b` 所引用的对象需要 `new` 运算符和一个 `BankAccount` 构造器。）未初始化的对象变量称为*空引用*或*空指针*。你可以使用关键字 `null` 来测试变量是引用对象还是未初始化：

```
if (b == null)
```

如果引用不为空，可以用以下语句将其设为空：

```
b = null;
```

尝试使用空引用调用实例方法可能导致程序因 `NullPointerException` 而终止。例如，

![images](img/f103-07.jpg)

#### 注意

如果你在方法中使用局部变量前未将其初始化，将会得到编译时错误。如果你对类的实例变量犯同样的错误，编译器会为基本类型变量提供合理的默认值（数字为 0，布尔值为 `false`），代码可能在没有错误的情况下运行。然而，如果你不初始化类中的*引用*实例变量，如上例所示，编译器会将它们设为 `null`。该类对象的任何试图访问空引用的方法调用都将导致运行时错误：程序将因 `NullPointerException` 而终止。

不要使用值为 `null` 的对象进行方法调用。

## 方法参数

### 形式参数 vs. 实际参数

方法头定义了该方法的*参数*。例如，考虑 `BankAccount` 类的 `withdraw` 方法：

![images](img/f104-01.jpg)

该方法有两个显式参数，`acctPassword` 和 `amount`。这些是*虚拟*或*形式参数*。可将它们视为占位符，对应客户端程序中特定方法调用将提供的一对*实际参数*或*实参*。

例如，

![images](img/f104-2.jpg)

这里 `"TimB"` 和 `250` 是与 `withdraw` 方法的 `acctPassword` 和 `amount` 相匹配的实际参数。

#### 注意

1. 方法调用中的实参数量必须等于方法头中的形参数量，且每个实参的类型必须与对应的形参类型兼容。

2. 除了显式参数外，`withdraw` 方法还有一个隐式参数 `this`，即将从中取款的 `BankAccount`。在方法调用

![images](img/f104-03.jpg)

中，与 `this` 相匹配的实际参数是对象引用 `b`。

### 基本类型作为参数传递

参数是*按值传递*的。对于基本类型，这意味着当调用方法时，会为每个参数分配一个新的内存槽。每个实参的值被复制到与每个形参对应的新创建的内存槽中。

在方法执行期间，参数对于该方法而言是局部的。**对参数所做的任何更改都不会影响调用程序中实参的值。** 当方法退出时，参数的局部内存槽会被清除。

这是一个示例。输出将是什么？

![images](img/f105-01.jpg)

![images](img/f105-02.jpg)

输出将是

![images](img/f105-03.jpg)

尽管进行了方法调用，实参 `a` 和 `b` 保持不变！

通过描绘程序执行期间内存槽的状态，可以理解这一点。

就在 `foo(a, b)` 方法调用之前：

![images](img/f105-04.jpg)

在 `foo(a, b)` 方法调用时：

![images](img/f105-05.jpg)

就在退出方法之前：（注意 `x` 和 `y` 的值已被更改。） `a`

![images](img/f105-06.jpg)

退出方法后：（注意 `x` 和 `y` 的内存槽已被回收。`a` 和 `b` 的值保持不变。）

![images](img/f105-07.jpg)

### 将对象作为参数传递

在 Java 中，基本类型和对象引用都是按值传递的。当对象的引用作为参数时，使用将副本复制到局部内存的相同机制。关键区别在于复制的是**地址**（引用），而不是各个实例变量的值。与基本类型一样，对参数所做的更改不会改变匹配实参的值。这在实践中意味着，方法无法用另一个对象替换一个对象——你无法更改被传递的引用。然而，可以通过作用于对象的方法来更改参数所引用对象的状态。

#### 示例 1

更改对象状态的方法：

![images](img/f106-01.jpg)

![images](img/f106-02.jpg)

以下是在 `chargeFee` 方法调用前的内存槽：

![images](img/f106-03.jpg)

在 `chargeFee` 方法调用时，创建匹配参数的副本：

![images](img/f106-04.jpg)

就在退出方法之前：(`BankAccount` 对象的 `balance` 字段已被更改。)

![images](img/f107-01.jpg)

退出方法后：（所有参数内存槽已被清除，但对象保持被修改状态。）

![images](img/f107-02.jpg)

#### 注意

`andysAccount` 引用在整个程序段中保持不变。然而，它所引用的对象已被更改。这很重要。请将其与下面的示例 2 进行对比，示例 2 尝试替换对象本身。

#### 示例 2

`chooseBestAccount` 方法试图——错误地——将其 `betterFund` 参数设置为余额较高的 `BankAccount`：

![images](img/f107-03.jpg)

![images](img/f107-04.jpg)

意图是执行 `chooseBestAccount` 语句后，`betterFund` 将成为对 `paulsFund` 对象的引用。查看内存槽可以说明为什么这会失败。

在 `chooseBestAccount` 方法调用之前：

![images](img/f108-01.jpg)

在 `chooseBestAccount` 方法调用时，创建匹配引用的副本：

![images](img/f108-03.jpg)

就在退出方法之前，`better` 的值已被更改；然而 `betterFund` 保持不变：

![images](img/f109-01.jpg)

退出方法后，所有参数槽已被清除：

![images](img/f109-02.jpg)

注意 `betterFund` 引用继续为 `null`，这与程序员的意图相反。

解决该问题的方法是修改方法，使其返回较好的账户。从方法返回对象意味着你正在返回该对象的地址。

![images](img/f110-01.jpg)

![images](img/f110-02.jpg)

#### 注意

其效果是创建 `betterFund` 引用，它引用与 `paulsFund` 相同的对象：

![images](img/f110-03.jpg)

该方法**不**会创建一个新对象供 `betterFund` 引用。要做到这一点需要 `new` 关键字和使用 `BankAccount` 构造器。假设已向 `BankAccount` 类添加了 `getPassword()` 访问器方法，代码将如下所示：

![images](img/f110-04.jpg)

将此修改后的方法与上述相同的 `main()` 方法一起使用，会产生以下效果：

![images](img/f111-01.jpg)

## 章节总结

到现在为止，你应该能够为任何给定对象编写代码，将其私有数据字段和方法封装在一个类中。请确保你了解各种类型的方法——静态方法、实例方法和重载方法。你应该知道如何包含构造器，包括无参构造器和带参数的构造器。

你还应该理解基本类型的存储与用于对象的引用之间的区别。

# 关于类和对象的多项选择题

第 1-3 题参考下面声明的 `Time` 类。

![images](img/f112-01.jpg)

1. 以下关于方法的陈述哪一项是错误的？

   (A) `equals`、`lessThan` 和 `toString` 都是访问器方法。

   (B) `increment` 是修改器方法。

   (C) `Time()` 是无参构造器。

   (D) `Time` 类有三个构造器。

   (E) 该类中没有静态方法。

2. 以下哪项代表带参数构造器的正确**实现代码**？

   (A) ![images](img/f112-08.jpg)

   (B) ![images](img/f112-09.jpg)

   (C) ![images](img/f112-10.jpg)

   (D) ![images](img/f112-11.jpg)

   (E) `Time = new Time(h, m, s);`

3. 客户端类有一个 `display` 方法，用于写入其参数所表示的时间：

   ![images](img/f113-01.jpg)

   以下哪项是 `/*` **方法体** `*/` 的正确替代？

   ![images](img/f113-01a.jpg)

   (A) 仅 I

   (B) 仅 II

   (C) 仅 III

   (D) 仅 II 和 III

   (E) I、II 和 III

4. 关于参数的哪项陈述是错误的？

   (A) 参数的作用域是定义它们的方法。

   (B) 静态方法没有隐式参数 `this`。

   (C) 同一个类中的两个重载方法必须具有不同名称的参数。

   (D) Java 中所有参数都是按值传递的。

   (E) 给定类中的两个不同构造器可以具有相同数量的参数。

第 5-11 题参考以下 `Date` 类声明。

![images](img/f113-02.jpg)

5. 以下哪项在客户端类中正确构造了一个 `Date` 对象？

   (A) `Date d = new (2, 13, 1947);`

   (B) `Date d = new Date(2, 13, 1947);`

   (C) `Date d;`  
   `d = new (2, 13, 1947);`

   (D) `Date d;`  
   `d = Date(2, 13, 1947);`

   (E) `Date d = Date(2, 13, 1947);`

6. 以下哪项将导致错误消息？

   I. `Date d1 = new Date(8, 2, 1947); Date d2 = d1;`

   II. `Date d1 = null; Date d2 = d1;`

   III. `Date d = null; int x = d.year();`

   (A) 仅 I

   (B) 仅 II

   (C) 仅 III

   (D) 仅 II 和 III

   (E) I、II 和 III

7. 客户端程序按如下方式创建一个 `Date` 对象。

   ![images](img/f114-01.jpg)

   以下哪个后续代码段将导致错误？

   (A) `String s = d.toString();`

   (B) `int x = d.day();`

   (C) `Date e = d;`

   (D) `Date e = new Date(1, 13, 2002);`

   (E) `int y = d.year;`

8. 考虑添加到 `Date` 类中的 `write()` 方法的实现。

   ![images](img/f114-02.jpg)

   以下哪项可用作 `/*` **实现代码** `*/`？

   I. `System.out.println(`  
   `month + “/” + day + “/” + year);`

   II. `System.out.println(`  
   `month() + “/” + day() + “/” + year());`

   III. `System.out.println(this);`

   (A) 仅 I

   (B) 仅 II

   (C) 仅 III

   (D) 仅 II 和 III

   (E) I、II 和 III

## 习题 9-23

### 9

这是一个使用 `Date` 对象的客户端程序：

![images](img/f115-01.jpg)

以下哪项是 `/* code to get birthDate */` 的正确替代？

I. ![images](img/f115-03.jpg)

II. ![images](img/f115-04.jpg)

III. ![images](img/f115-05.jpg)

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 I 和 II

(E) 仅 I 和 III

### 10

`Date` 类的一个客户端程序中的方法具有以下声明。

`Date d1 = new Date(mo, da, yr);`

此处，`mo`、`da` 和 `yr` 是先前定义的整型变量。该方法现在创建第二个 `Date` 对象 `d2`，它是 `d1` 所引用对象的精确副本。以下哪个代码段将**无法**正确完成此操作？

I. `Date d2 = d1;`

II. `Date d2 = new Date(mo, da, yr);`

III. `Date d2 = new Date(d1.month(), d1.day(), d1.year());`

(A) 仅 I

(B) 仅 II

(C) 仅 III

(D) 仅 II 和 III
