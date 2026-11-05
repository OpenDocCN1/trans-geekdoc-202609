
-s 标志使关联名称与值成为可能。在 WebAssembly 构建中，这对于将 `EXPORTED_FUNCTIONS` 名称与前面带有下划线的函数名称数组关联是必需的。例如，以下构建命令使 `foo` 函数成为导出的函数：

```
em++ -DNDEBUG example.cpp -o example.wasm --no-entry -s "EXPORTED_FUNCTIONS=['_foo']"
```

以下讨论展示了此类构建命令在实践中的使用方式。

## 在 JavaScript 中访问 WebAssembly

截至本文撰写时，所有主要浏览器都支持 WebAssembly。因此，JavaScript 代码可以访问一个 `WebAssembly` 对象，其方法使加载和执行 WebAssembly 模块成为可能。最重要的是要了解的方法是 `instantiateStreaming`，它接受两个对象：

1. 包含 WebAssembly 模块 (`*.wasm`) 内容的 `Response`。

2. 一个可选的导入对象，其中包含模块所需的数据。

`instantiateStreaming` 方法返回一个 `Promise`，它解析为包含两个属性的 `ResultSet`：

* `module`—包含已编译代码的 `WebAssembly.Module`

* `instance`—提供导出函数的 `WebAssembly.Instance` 对象

为了获取输入 `Response`，许多应用程序调用 `fetch`，该内容在 [第 6 章](#chapter6.xhtml) 中进行了讨论。这提供了一个解析为 `Response` 的 `Promise`，以下代码展示了如何使用它：

// Obtain Response containing file content
let resp = await fetch("example.wasm");
```

一旦 `Response` 可用并且导入对象已创建，应用程序就可以通过调用 `instantiateStreaming` 来访问 WebAssembly 结果：

// Obtain the ResultSet containing the module and instance
let wasm = await WebAssembly.instantiateStreaming(resp);
```

此 `wasm` 对象有两个名为 `module` 和 `instance` 的属性。`instance` 属性很重要，因为它通过其 `exports` 属性提供对导出函数的访问。例如，如果 `*.wasm` 文件导出一个名为 `func` 的函数，以下代码展示了如何在 JavaScript 中调用它：

// Invoke the exported function
wasm.instance.exports.func();
```

现在让我们看一个简单的示例。假设 `source.cpp` 包含以下函数定义：

```
extern "C" {
    int foo() {
        return 123;
    }
}
```

在文件开头，`extern "C"` 阻止编译器破坏函数名称。以下命令使用完全优化、无入口点并禁用断言来编译 `source.cpp`。结果是一个名为 `source.wasm` 的模块，其导出函数列表包含 `foo`：

```
em++ -DNDEBUG -O3 source.cpp -o source.wasm --no-entry -s "EXPORTED_FUNCTIONS=['_foo']"
```

如果构建成功完成，`foo` 函数可以从 JavaScript 调用。这需要三个步骤：

1. 为 `source.wasm` 文件创建 `Response`。

2. 从 `Response` 实例化模块。

3. 通过 resulting `instance` 的 `exports` 属性调用函数。

以下代码展示了如何完成这些步骤：

// Obtain Response containing file content
let resp = await fetch("source.wasm");

// Obtain the ResultSet containing the module and instance
let wasm = await WebAssembly.instantiateStreaming(resp);

// Print the return value of the exported function
console.log(wasm.instance.exports.foo());
```

如果这些操作成功完成，控制台将显示 `123`，这是 `source.cpp` 中 `foo` 函数的返回值。

## Makefiles

与其每次运行构建时都输入冗长的命令，使用 `emmake` 工具更高效。它调用 `make` 工具，该工具必须安装在开发系统上。在 Linux 和 macOS 上，这默认已安装。Windows 用户可以通过安装 Cygwin 或 Minimalist GNU for Windows (`MinGW`) 来安装 `make`。

当 `emmake` 运行 时，它会在当前目录中查找 makefile（通常命名为 `Makefile`）。如果存在，`emmake` 会读取其命令并执行它们。与在命令行输入命令相比，Makefile 提供了许多优势：

* 命令只需在 makefile 中输入一次。

* 构建命令可以在 makefile 中修改和扩展，而无需重新输入整个命令。

* Makefile 可以在不同的语言和环境中构建不同类型的应用程序，并且可以执行非构建操作，如安装和归档。

* Makefile 可以按层次组织，其中主 makefile 包含所有构建命令，而依赖的 makefile 指定应运行哪些命令。

Makefile 因作者和目的而大不相同，但大多数由四种类型的语句组成：

1. 依赖行——标识要创建的文件（`target`）及其创建所需的文件（`dependencies`）的行。

2. Shell 行——包含从其依赖项构建目标的命令。

3. 变量声明——文本替换语句，其功能类似于 C/C++ 中的 `#define` 指令。

4. 注释——以 `#` 开头并提供额外信息的行。

本小节描述了这些语句中的每一个。然后我将介绍 `App0B_SimpleWASM` 项目，该项目展示了如何使用 makefile 构建 WebAssembly 模块。

### 依赖行

在执行构建之前，`emmake` 会查找两条信息：要构建的文件的名称以及构建它所需的文件的名称。要构建的文件称为 `target`，构建目标所需的文件称为 `dependencies`。

makefile 使用依赖行提供此信息。依赖行包含目标名称、冒号以及由空格分隔的依赖项名称。其基本语法如下

```
target: dependency1 dependency2 …
```

例如，如果你希望 `emmake` 使用源文件 `src1.c`、`src2.c` 和 `src3.c` 构建名为 `app.wasm` 的应用程序，则依赖行是

```
app.wasm: src1.c src2.c src3.c
```

如果目标文件已存在，`emmake` 会检查目标文件和依赖文件上次修改的时间。如果任何依赖项比目标更新，`emmake` 会重建目标。否则，它不采取任何操作。

当 `emmake` 不带参数调用时，它会处理 makefile 中的第一个依赖行。但如果它带有一个目标名称调用，例如命令 `emmake target_name` 中，`emmake` 将搜索目标为 `target_name` 的依赖行。

目标文件和依赖文件可以是任何类型：源代码或目标代码，文本或二进制。唯一重要的是 `make` 知道要构建什么以及构建它需要哪些文件。但依赖行不指定应如何构建目标。为此，你需要添加 shell 行。

### Shell 行

Shell 行告诉 `emmake` 在构建前一个依赖行中标识的目标时执行哪些步骤。Shell 行包含与你在命令行输入的相同类型的命令。在 makefile 中，shell 行跟随依赖行，并且每个 shell 行 *必须以制表符开头*。其通用语法如下：

```
target: dependency1 dependency2 ...
     command1
     command2
     ...
```

依赖行及其 shell 行的组合称为 `rule`。完整的规则告诉 `emmake` 要构建什么目标，需要哪些文件，以及构建目标必须处理哪些命令。

例如，前一节解释了如何使用 `em++` 将 `source.cpp` 编译为 `source.wasm`。此操作可以用以下规则表示：

```
source.wasm: source.cpp
     em++ -DNDEBUG -O3 source.cpp -o
source.wasm --no-entry -s "EXPORTED_FUNCTIONS=['_foo']"
```

此规则在语法上是正确的，但可以使用变量简化。我将在下一部分讨论这一点。

### 变量和注释
