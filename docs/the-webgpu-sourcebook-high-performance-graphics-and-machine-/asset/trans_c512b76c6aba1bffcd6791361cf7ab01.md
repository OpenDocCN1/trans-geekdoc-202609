
# TypeScript 类型和类

## 数字类型
-   `Number.NEGATIVE_INFINITY`—负无穷大（当负值太大无法存储时返回）
-   `Number.NaN`—非数字（当操作返回不可能的值时返回，例如对字符串执行数学运算）

TypeScript 支持与 JavaScript 相同的数字操作种类。这些包括数学运算以及将数字转换为（并格式化为）字符串的操作。

## 字符串类型
字符串使得存储和操作文本成为可能。字符串变量可以通过将其设置为等于用引号——双引号或单引号——包围的一个或多个字符来初始化。以下示例展示了这一点：

```
let single_char: string = "D";
let large: string = 'Single or double, it does not matter';
```

字符串按顺序存储其字符，每个字符都有一个索引，从 0 开始。在使用字符串处理可用的众多方法时，了解这一点很重要。

## 数组类型
数组是有序的同类型元素的集合。在 TypeScript 中声明数组时，声明必须标识数组元素的类型。声明数组有两种方式：

```
let arr1: element_type[];
let arr2: Array<element_type>;
```

数组可以通过将其设置为用方括号包围的逗号分隔的元素列表来初始化。以下代码展示了如何声明和初始化数组：

```
const num_array: number[] = [5, 7, 9];
const str_array: string[] = ["p", "q", "r"];
```

声明数组后，其元素可以通过 `array[index]` 访问，其中 `index` 是元素在数组中的位置。第一个元素的索引为 0，第二个为 1。如果数组有 N 个元素，最后一个元素的索引为 N–1。以下代码展示了这一点：

```
let x: number = num_array[1];     // x = 7
let c: string = str_array[2];     // c = "r"
```

可以通过访问其 `length` 属性获得数组的长度。如果尝试读取超出数组长度的元素，编译器不会返回错误。但在执行编译后的代码时，读取错误的值将为 `undefined`。

## 元组类型
元组与数组类似，但其元素可以具有不同的类型。在元组声明中，必须按顺序提供每个元素的类型。以下代码声明并初始化了两个元组：

```
const t1: [boolean, number] = [true, 6];
const t2: [number, number, string] = [17, 5.25, "green"];
```

与数组一样，元组的某个元素可以通过其索引访问，第一个元素的索引从 0 开始。以下代码展示了这一点：

```
const x: boolean = t1[0];     // x = true
const y: number = t2[1];      // y = 5.25
```

元组似乎适合存储相互关联的数据元素。但正如我稍后会解释的，类更适合此用途。当函数需要返回包含多种类型多个值的单个数据结构时，元组特别有帮助。

## 对象类型
与元组类似，`Object` 类型的变量包含可以具有不同类型的数值。但两者之间至少有三个关键区别：
* 每个 Object 的值都有一个关联的字符串，称为 `key`，用作该值的标识符。
* 对象中值的顺序并不重要。对象值是通过键访问的，而不是通过数字索引。
* 初始化对象时，键值对用大括号包围，而不是方括号。

以下代码展示了如何声明和初始化对象：

```
let count = {first: "one", second: "two"};
let house = {num: 31, street: "Main", forSale: true};
```

如图所示，对象的键未用引号包围，尽管可以这样做。如果对象的值被引号包围，它将被解释为字符串。否则，它将被解释为其他类型。

## Any、Undefined 和 Null 类型
如果变量的类型未知，可以将其分配给 `any` 类型。这告诉编译器不必关心该变量的类型检查。不建议使用此类型，但在访问第三方 JavaScript 代码中的数据结构时可能有必要。

如果 `noImplicitAny` 未设置为 true，TypeScript 编译器会将未类型化的变量分配给 `any` 类型。但在 JavaScript 中，没有值的变量被认为是 `undefined`。在 TypeScript 中，每个值都需要一个类型，而未定义的值的类型为 `undefined`。

与 undefined 类似，任何类型的变量都可以设置为 `null` 值。这表示变量不包含数据。然而，如果变量被分配为 `null` 类型，它只能设置为 `null` 值。

理解 `undefined` 和 `null` 之间的区别很重要。如果变量已声明但未初始化，JavaScript 会将其视为 `undefined`。如果变量被设置为 `null`，它已定义且其值为 `null`。

## TypeScript 类
在软件开发的早期，用于存储数据的唯一结构是变量、字符串和数组。但随着应用程序复杂性的增加，开发人员将数据和相关操作封装到称为对象的结构中。对象的內容由其类决定。本质上，类是创建对象的蓝图。

例如，假设一个应用程序创建汽车的软件表示。组织数据的一个好方法是定义一个包含汽车相关数据的 `Car` 类。这些数据可能包括汽车的品牌、型号、发动机类型和制造年份。Car 类还可能标识汽车执行的操作，包括驾驶、停车和倒车。

在 TypeScript 中，类的变量称为属性，其例程称为方法。总体上，类的属性和方法称为成员。

最少，TypeScript 类定义由单词 `class`、类名和用大括号括起来的主体组成。例如，以下 `Car` 类有四个属性和三个方法：

```
class Car {

    // Properties
    make: string;
    model: string;
    engineType: string;
    year: number;
    // Methods
    park() { ... };
    driveForward() { ... };
    driveReverse() { ... };
}
```

定义此类后，可以通过使用 `new` 关键字调用构造函数来创建 `Car` 对象。以下 TypeScript 代码展示了这一点：

```
let myCar = new Car();
```

JavaScript 也支持使用 `new` 关键字创建对象，但 JavaScript 对象和 TypeScript 对象之间存在许多差异。一个主要区别是 TypeScript 对象不可变，这意味着它们不能被赋予新的属性或方法。

为了理解这意味着什么，假设我们想添加一个名为 `numDoors` 的新属性。创建 `myCar` 后，以下赋值在 JavaScript 中是可以接受的：

```
myCar.numDoors = 2;
```

但在 TypeScript 中，这会导致错误：`Property ‘numDoors’ does not exist on type ‘Car’`。如果你想添加新属性，需要定义一个新类。但你不必从原始类复制粘贴代码。TypeScript 使创建扩展现有类的子类成为可能。这些子类接收（或继承）原始类的成员，并可以定义自己的属性和方法。

例如，可以通过在其名称后跟 `extends B` 将 `Class A` 声明为 `Class B` 的子类。以下代码展示了其工作原理：

```
class A extends B {
    ...
}
```

作为更实际的示例，假设我们想定义一个新类 `SportsCar`，它继承 `Car` 类的成员。除了访问 `Car` 的属性和方法外，`SportsCar` 还应有一个名为 `maxSpeed` 的附加属性。`SportsCar` 类可以按以下方式定义：

```
class SportsCar extends Car {
    maxSpeed: number;
}
```
