
1. `Exception in thread «main» java.lang.NullPointerException`
2. `at com.example.Item.getIngredients(Item.java:16)`
3. `at com.example.Order.getItems(Order.java:25)`
4. `at com.example.PizzaPlaceApp.main(PizzaPlaceApp.java:14)`

众所周知，当函数被执行时，它们的上下文会被放入栈中；如果 `getItems` 函数调用 `getIngredients` 函数，则 `getIngredients` 的上下文将插入到 `getItems` 上下文之上。随着执行到达更深层次的函数，这些函数的上下文将被添加到栈顶。

为了帮助我们诊断应用程序抛出异常的情况，整个执行堆栈会被转换为字符串表示，并作为异常对象的属性包含其中。

堆栈跟踪为开发者提供了应用程序通往该错误的逐步演进路径。利用这些信息，我们可以在开发期间在堆栈跟踪中列出的函数处设置断点来诊断错误原因。

# 定义异常类型

在 Java 等面向对象的语言中，所有异常都继承自基类，如 `java.lang.Exception` 或 `java.lang.Error`。更具体的错误，例如 `FileNotFoundException`（应用程序在尝试访问不存在的文件时抛出的异常），继承了这些通用错误类。

注意：在 Java 中，`java.lang.Throwable` 是 `java.lang.Exception` 和 `java.lang.Error` 共同继承的根超类。

在此背景下，所有派自 `java.lang.Exception` 的类应该表示可恢复的错误，而派自 `java.lang.Error` 的类代表严重的、不可恢复的错误。

这种异常的子类机制允许我们编写代码分别处理不同类型的错误。然而，这种类层次结构也导致了一种并不好的做法：开发者总是使用 `java.lang.Exception` 来处理所有类型的错误。始终捕获 `Exception` 类的实例虽然“有效”，但当这些错误发生时，特定的异常类型可以提供更丰富、更易调试的错误解释。处理像 `FileNotFoundException` 这样的特定异常比处理 `java.lang.Exception` 更容易发现发生了什么。

## 捕获异常

支持异常的语言还通过 `try-catch` 块来指示应用程序如何处理它们：

```java
try {
    // 常规代码执行
} catch (Exception exception) {
    // 处理异常的代码
}
```

在 `try { … }` 块内抛出或引发每个异常都会停止应用程序的常规执行，并在 `catch() { … }` 块中带有正确的异常类型继续执行，应用程序预期在此处恢复。

例如，考虑应用程序尝试访问文件系统中不存在的文件的情况。如果我们希望应用程序处理这种错误情况，可以使用如下代码：

```java
try {
    BufferedReader rd = new BufferedReader(
        new FileReader(
            new File(fileName)));
    String line = rd.readLine();
    // 继续读取文件
} catch (FileNotFoundException file) {
    // 处理异常
}
```

在此代码中，如果 `try` 块内的任何行抛出 `FileNotFoundException`，执行将跳转到 `catch` 块，我们在那里恢复。

## 编译时验证的错误

现代编译器非常擅长静态分析：搜索可能导致常见错误的模式。某些函数具有显式的失败风险。例如，在打开文件时，始终存在文件不存在或损坏的可能性。检查异常是应用程序必须处理才能使代码通过编译的错误：通过在函数签名中使用 `throws` 关键字来实现：

```java
public void writeList() throws IOException {
    // ...
}
```

然而，编译器无法找到所有异常。想想 Java 中无处不在的 `NullPointerException`。下面的代码说明了这种情况：

```java
List nullList = null;
nullList.toString(); // 因为 nullList 为 null，所以产生 NullPointerException
```

`NullPointerException` 可能是 Java 中最常见且信息最少的异常，因为异常本身无法解释变量为什么为空。在 Java 中，编译器几乎不可能在编译时知道对象的引用会导致 `NullPointerException`；大多数情况下，空值是在运行时定义或作为参数传递的，如下：

```java
boolean createOrder(Items itemsParam) {
    Order order = new Order(itemsParam);
    return order.items.size() > 0;
}
createOrder(null); // 因为 order.items 为 null，导致 NullPointerException
```

这就是我们总是对函数参数进行“空检查”的原因：为了避免对象意外变成空引用：

```java
boolean createOrder(Items itemsParam) {
    Items items = itemsParam;
    if (items == null) {
        items = new Items();
    }
    Order order = new Order(items);
    return order.items.size() > 0;
}
createOrder(null); // 返回 false
```

由于无法在编译时简单地断言这些异常，我们将它们称为 `unchecked exceptions`（未检查异常）；它们要求开发者根据经验来判断如何以及在何时正确处理它们。

注意：某些编程语言如 Rust 并没有“null”值。它们使用“Optional”对象：一种包装器，可以显式地表示一个值可能存在也可能不存在。为了访问其值，可选对象强制开发者处理值为空的情况。

另一个例子是 Kotlin，它的变量默认不允许 null 值。如果我们要允许异常，就必须显式地将变量声明为“nullable”（可空）。

通过这些模式，编译器和开发者可以假设在默认情况下所有值始终是已定义的，并且在我们没有正确处理可能为 null 的引用时，在编译时显示错误。

# 将错误作为返回值

并不是所有的编程语言都遵循 `try-catch-exception` 模式。像 `Golang` 这样的语言将错误视为应用程序正常流程的一部分的值；因此，处理这些错误的代码也属于主程序的流程。

例如，在 `Golang` 中，我们打开文件的相同用例需要如下处理错误：

```go
content, err := ioutil.ReadFile(filename)
if err != nil { // 如果错误不是 null，说明发生了错误
    return nil, err
}
return content, nil
```

可能失败的函数会返回两个参数：一个是操作的实际结果，另一个是可能包含指向错误对象的引用。如果错误变量为 `nil`——即 null——我们可以假设操作是成功的。

通过将错误成为主执行流程的一部分，语言规范强制开发者去处理它们。与异常不同（在异常中我们可以将所有代码封装在 `try` 块中并使用全捕获 `Exception` 类来处理所有错误），而返回错误的语言要求开发者捕获并处理函数返回的每个错误。虽然这可能很繁琐，但它让错误处理更加显式且更难被忽略。

与异常相比，返回错误的另一个显著优势是，它增加了应用程序中可能失败的函数调用的可见性。错误在代码中被显式显示。相反，当使用异常时，函数中的每一行都可能抛出异常。

事实上，使用检查异常是某些编程语言尝试解决代码中可能错误可见性不足的方法，但效果差不齐。然而，检查异常仍然缺乏返回错误的清晰度。

所以，最后，哪种更好？是抛出异常还是返回错误？我们将发现这两种方法的支持者，并且最终，我们在项目中使用的代码语言将限制我们的决定。每种方法都有其优势，只有当你都用过它们时，你才知道自己更倾向于哪一种。

我们可以讨论每种方法的优缺点，但对任何开发者来说，至关重要的是如何有效地处理错误，无论它们是被捕获还是被返回。

# 实现良好的异常处理

良好的异常处理在原则上是直接的，但在实践中很困难。其一个重要原因是开发者不喜欢认为自己的代码会产生错误，因为我们将错误与完成糟糕的工作联系在一起。

事实是，虽然我们必须尽一切避免在应用程序中引入错误状态，但没有任何应用程序是 100% 无 Bug 的。只有没有任何代码的程序才是永远没有缺陷的。

一旦我们接受软件开发者是易错的人类，我们就必须创建一个多级计划，帮助我们防止错误对应用程序和用户产生负面影响：

* 防止所有可能发生的错误。
* 处理并缓解到达生产环境的错误。
* 记录所有错误。

## 尽可能防止所有错误

在我们开始处理错误之前，我们需要尽可能地防止它们。正如前面提到的，我们无法防止所有错误。但我们可以做的是建立足够的验证和流程，帮助防止最常见的错误从源上被引入应用程序：

* **测试**：我们在本书中专门用了一整章来介绍了软件测试以及它如何帮助我们在错误到达生产环境之前捕获它们。
* **Linting/静态代码分析器**：就像 `Rust` 或 `Golang` 等语言的现代编译器会在编译时报告可能的错误一样，代码分析器允许开发者搜索通常会导致 Bug 的代码模式或“异味”。

记住 `帕托法则`（也称为 `80/20` 原则）：80% 的结果（在这种情况下是缺陷）是由仅 20% 的原因引起的。关注这 20% 的错误来源可以使你的努力结果最大化。

## 注意搜索词：六西格玛

在制造领域存在一种共识：我们永远无法实现零缺陷。某些流程改进方法旨在尽可能减少这些缺陷。例如，`Six Sigma` 是一组旨在理解缺陷发生的原因，以及如何标准化和改进流程以减少波动和缺陷的技术。

遵循 `Six Sigma` 等方法的世界级公司专注于可实现和可衡量的目标。这些流程是迭代的，团队不断寻找改进流程的方法以产生更少的缺陷。

在可以防止的错误中，包括与质量问题相关的错误：缺乏验证、糟糕的代码模式等。我们无法控制的错误是诸如网络、第三方依赖、冲突的浏览器版本等其他只能处理而无法防止的变幻莫测的不利条件。

## 在生产环境中处理和缓解错误

一旦我们在开发期间尽尽努力发现并修复了所有可能的缺陷，我们该如何处理那些隐藏和潜伏在应用程序深处的其余潜在错误呢？我们应用本章节一直在讨论的 `try-catch` 和空值检查-错误功能：捕获错误、记录它并恢复。

### 定义良好的错误消息

我们处理错误的主要目标是让它们对用户尽可能不可见。如果我们可以在用户感知到错误发生之前就从中恢复，我们就实现了这个目标。

然而，大多数错误在没有用户干预的情况下无法完全处理。错误消息向用户（和开发者）说明如何从他们所处的错误状态中恢复。良好的错误消息可以帮助用户在极少或没有干预的情况下自行恢复。

什么是良好的错误消息？错误消息应该使用简单清晰的语言。它们应该帮助用户回答以下问题：

* 错误是由用户的操作引起的吗？如果不是，告诉他们这不是他们的错。
* 他们需要做什么来恢复？如果不需要，告诉他们。

记住，详细的错误对开发者很有用，但对用户则不然。错误消息应该对普通用户友好，同时为尝试调试它们的软件开发者提供足够的信息。消息中包含的数据越少，用户就越容易采取。

### 冒泡！

错误就像水或泡沫一样：它们跨越执行栈向上冒泡，从产生错误的函数一直向上到主应用程序进程，如图 7.1 所示：

![](img/Figure-7.1.jpg)

**图 7.1:** 栈跟踪的可视化表示。未处理的错误将向上冒泡

开发者可以在执行栈中的任何函数内部捕获并处理错误。如果错误没有被处理，它将一直冒泡到主进程。

为了更好地说明这一观点，让我们将其转换为以下 `JavaScript` 代码。我们可以简化一个用例，来观察在栈末尾抛出的异常是如何冒泡到顶部的：

```javascript
class FileNotFoundError extends Error {
  constructor(message) {
    super(message);
    this.name = "FileNotFoundError";
  }
}

function main() {
  findProduct()
}

function findProduct() {
  // do more stuff
  findCatalog()
}

function findCatalog() {
  // do more stuff
  return openCatalogFile()
}

function openCatalogFile() {
  // simulate an error while opening a file
  throw new FileNotFoundError("catalog.xml")
}

main()
```

如图 7.1 所示，我们将看到 `findProduct` 函数调用了 `findCatalog` 函数，而该函数又尝试使用 `openCatalogFile` 函数从文件中获取目录数据。注意，我们还没有使用 try-catch 块。

如果 `openCatalogFile` 抛出异常，你将看到如下错误消息：

```
FileNotFoundError: catalog.xml
  at openCatalogFile (…/chapter7/exception/handling-errors.js:23:11)
  at findCatalog (…/chapter7/exception/handling-errors.js:19:5)
  at findProduct (…/chapter7/exception/handling-errors.js:14:5)
  at main (…/chapter7/exception/handling-errors.js:10:5)
  at Object.<anonymous> (…/chapter7/exception/handling-errors.js:26:1)
```

虽然这个错误提供了提示信息，但我们还需要从中恢复出来。我们有几种恢复方案：

* 重试操作。例如，导致网络请求的错误可能因为超时或其他任何瞬时网络问题而失败。
* 执行备用方案：当原始函数失败时执行“计划 B”，例如我们最初想要执行的操作的精简版本。
* 跳过当前操作并返回错误消息。只要错误在到达主进程之前被处理，应用程序就可以继续运行。

## 提供备用方案

在存在错误的情况下，用户期望应用程序能够运行，即使其功能有所降级或减少。执行备用方案总是比直接返回错误消息要好。

我们将为上一个示例提供一个备用方案：如果访问目录文件失败，我们将选择提供存储在内存中的简单目录。此示例的目录只有一个产品：

```javascript
var fallbackCatalog = {
  product1321: {
    name: "Deodorant"
  }
}
```

我们处理错误的好坏取决于选择在何处处理。随着错误的冒泡，栈中的每个函数处理它的错误的灵活性就越小。

我们可以在 `findProduct` 函数内部处理错误：

```javascript
function findProduct() {
  try {
    findCatalog()
  } catch (error) {
    // 错误停止冒泡。它不会到达“main”
  }
}
```

或者我们可以通过跳过 catch 块或重新抛出错误来手动继续传播错误：

```javascript
function findProduct() {
  try {
    findCatalog()
  } catch (error) {
    // 执行一些事情，然后将错误冒泡到“main”：
    throw error;
  }
}
```

我们必须尽可能靠近抛出错误的函数来处理错误，因为这为我们提供了更多替代方案的选择。

例如，如果我们尝试将错误冒泡到主函数，我们能做的就是重试整个 `findProduct` 函数：

```javascript
function main() {
  try {
    findProduct()
  } catch(err) {
    // 在此处处理
  }
}
```

如果错误是瞬时的（只发生在短时间内），我们需要处理一个备选操作。这样应用程序就能正常工作并提供备用方案：

```javascript
fallbackCatalog = {
  product1321: {
    name: "Deodorant"
  }
}

findCatalog() {
  try {
    // do more stuff
    return openCatalogFile()
  } catch (error) {
    // 记录错误并返回备用方案
    return fallbackCatalog
  }
}

openCatalogFile() {
  // simulate an error while opening a file
  throw new FileNotFoundError("catalog.xml")
}

findProduct() {
  try {
```
