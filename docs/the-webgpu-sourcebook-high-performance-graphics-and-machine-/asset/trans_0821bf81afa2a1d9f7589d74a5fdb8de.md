
为了正确执行其工作，编译器需要了解 TypeScript 代码中使用的数据类型。数据类型可以在声明文件（`*.d.ts`）中提供，这将在后面的章节中讨论。最重要的声明文件是主库 `lib.d.ts`，它声明了像 `Array`、`Number` 和 `String` 这样的基本类型。如果在 `tsconfig.json` 中设置了 `noLib`，编译器将无法访问这些类型。

编译器除了主库之外还可以访问高级库，例如文档对象模型（DOM）的类型定义和 ECMAScript 的高级版本。如果 TypeScript 代码包含 `Promises` 和 `TypedArrays` 等特性，这就变得非常重要。为了启用访问，可以按如下方式设置 `lib` 标志：

```
"compilerOptions": {
    …
    "lib": [ "dom", "esnext" ],
    …
}
```

稍后章节将解释，你可以安装声明不同平台和工具集类型的额外库。这尤其重要，因为 WebGPU 的类型未在 TypeScript 的任何内置库中定义。为了提醒编译器，这些库需要在 `tsconfig.json` 中使用 `types` 标志进行标识。

如果将 `alwaysStrict` 设置为 true，浏览器将以严格模式运行脚本。此模式将错误视为错误并防止创建意外的全局变量。如果 JavaScript 对象包含重复属性，它也会抛出错误。

## 示例应用程序——TypeScript 简介

在深入 TypeScript 的技术细节之前，建立一个简单项目是个好主意。`AppA_HelloTS` 项目包含构建 `hello_ts` 应用程序所需的三个文件：

* `appa_hello.ts`—要编译为 JavaScript (`appa_hello.js`) 的 TypeScript 代码
* `tsconfig.json`—配置编译过程
* `index.html`—导入编译后代码的网页

一旦你了解如何构建和运行此应用程序，你将毫不费力地处理更复杂的 TypeScript 项目。

### 编译器配置

TypeScript 编译器从 `tsconfig.json` 读取配置设置。其内容如下所示：

```
{
    "files": [ "appa_hello.ts" ],
    "compilerOptions": {
        "target": "es2021",  
        "removeComments": true,
        "alwaysStrict": true,
        "noEmitOnError": true, 
        "noUnusedLocals": true,
        "noUnusedParameters": true
    }
}
```

这告诉编译器唯一要编译的文件是 `appa_hello.ts`，它位于当前目录中。在执行编译时，编译器应根据 ECMAScript 2021 规范生成 JavaScript。由于设置了 `alwaysStrict`，生成的代码将在严格模式下执行。

`noEmitOnError` 字段告诉编译器如果发生错误则不生成 JavaScript。由于 `noUnusedLocals` 和 `noUnusedParameters` 设置为 true，编译器将检查未使用的声明。

### 源代码

`hello.ts` 文件中的代码并不特别令人印象深刻，但它展示了 TypeScript 的一个重要特性。其内容如下所示：

```
class HelloTS {
    public printMessage() {
        document.write("Hello TypeScript!");
    }
}

let hello: HelloTS = new HelloTS();
hello.printMessage();
```

这定义了一个名为 `HelloTS` 的 TypeScript 类，它有一个名为 `printMessage` 的方法。如果你不熟悉类和方法，不用担心。本附录后面的章节将详细讨论类。

要构建此代码，请进入项目的目录并在命令行中输入 `tsc`。编译器将 TypeScript 转换为 JavaScript 并将结果代码放在 `appa_hello.js` 中。如果你将 `index.html` 打开在浏览器中，网页将显示 Hello TypeScript！

## TypeScript 的基本数据类型

TypeScript 允许你在声明中设置变量的类型。这是一个可选功能，类型规范在代码编译为 JavaScript 时会消失。但它们提供了一个主要优势：*类型检查*。如果一个 TypeScript 变量的类型被设置为另一种类型的值，编译器会标记错误。

举例说明会更清楚。在以下代码中，第一行将 `x` 设置为一个数字，第二行将其设置为一个字符串：

```
var x = 5;
x = "Hello";
```

这在 JavaScript 和 TypeScript 中是可以接受的，但 TypeScript 使能够将 `x` 具体标识为数字。考虑以下代码：

```
var x: number;
x = "Hello";
```

第一行指定 `x` 为数字。在编译代码时，编译器会识别第二行将 `x` 设置为字符串，并会报告错误。

类型检查有三个主要目的：

* 早期错误发现——编译器在编译时报告错误，这样你就不必在运行时找出它们。
* 工具支持——当变量具有类型时，编辑器可以更好地分析文本。这会影响代码补全、错误检查和语法着色等功能。
* 可读性——当变量具有类型时，更容易理解其用途。

设置变量的类型涉及在变量名后跟冒号和所需类型。一般声明具有以下形式：

```
var <name>: <type>;
```

如果变量需要初始化，声明的形式可以如下所示：

```
var <name>: <type> = <value>;
```

当未类型化的变量被初始化时，编译器会自动将变量的类型设置为该值。换句话说，如果变量被初始化为一个值，就无需定义其类型。

变量的类型可以设置为自定义类型或预定义 TypeScript 类型。稍后章节讨论自定义类型，其中包括类和接口。本节重点介绍 TypeScript 的内置类型，包括 `boolean`、`number`、`string`、`array`、`tuple`、`Object`、`any`、`undefined` 和 `null`。

### 布尔类型

在 TypeScript 的预定义类型中，`boolean` 是最容易使用和理解的。布尔变量可以设置为两个值之一：true 或 false。例如，以下代码声明了一个名为 `check` 的布尔变量并将其值初始化为 true：

```
const check: boolean = true;
```

布尔变量可以设置为返回布尔值的任何操作。这些操作包括比较操作（`>`、`<`、`>=`、`<=`、`==`、`!==` 和 `===`）和逻辑操作（`&&`、`||` 和 `!`）。以下示例演示了如何声明和初始化布尔变量：

* `const x: boolean = 5 > 3;`
* `const y: boolean = "a" !== "b";`
* `const z: boolean = ((3 < 5) && ("a" != "b"));`

JavaScript 提供了两个用于测试相等性的运算符：`==` 和 `===`。区别在于 `x == y` 如果 `x` 和 `y` 具有相同的值则返回 true，而 `x === y` 如果 `x` 和 `y` 具有相同的值和相同类型则返回 true。

### 数字类型

在 TypeScript 中，整数和浮点值都属于 `number` 类型，无论其符号或大小如何。以下示例显示了这一点，这些示例声明并初始化了三个数字值：

```
let three: number = 3;
let pi: number = 3.14159;
let avogadro: number = 6.022e-23;
```

与 JavaScript 一样，TypeScript 中的每个数字都被视为浮点值。没有整数类型或特定于整数的操作。数字按照 IEEE-754 标准存储为 64 位双精度值。值可以使用定点表示法（0.01）或指数表示法（6.02e-23）给出。

TypeScript 支持不同进制的字面值。即 TypeScript 除了十进制外，还识别十六进制（`0x10`）、八进制（`0o20`）和二进制（`0b10000`）。

TypeScript 提供了可在代码中使用的特殊数字值。其中五个如下所示：

* `Number.MAX_VALUE`—最大可能的数字值（约 1.7977e+308）
* `Number.MIN_VALUE`—最小可能的数字值（等于 5.0e−324）
* `Number.POSITIVE_INFINITY`—正无穷大（当正值太大而无法存储时返回）
