
目前，大多数计算机语言都提供了自己的“try/catch/throw”版本（即一种处理异常的流行范式）。名为“try/catch”的结构保护其所属的代码，并告知计算机语言其安全任务。在此，程序会在检测到错误和异常时立即“throw”（抛出）它们。然后，语言（例如 `PHP`）将扫描其执行栈，以了解是否有“try/catch”结构能够处理该问题。

这种方法提供了许多优势。例如，它允许你编写健壮的程序，而无需在每个代码块中编写“if”语句。这意味着你可以最小化所需编写的代码量。借助“try/catch/throw”范式，你只需用“try/catch”结构包裹代码块，并在错误发生时进行管理。此外，通过“throw”结构检测到异常后，你可以返回到能够处理并继续程序执行的代码部分。

“try/catch”结构需要以下语法：

```
try {

  … // 可能遇到异常的代码块。

} catch (ExceptionClass1 $sample_exception) {

  … // 你想要用来处理异常的代码。

} catch (ExceptionClass2 $sample_exception) {

}
```

你需要将 `PHP` 代码放在“try{}”内部。正如你所见，该结构前面跟随一系列“catch”子句，每个子句定义将处理哪种异常以及用什么名称来标识错误。

当程序抛出异常时，初始的 `catch()` 语句将运行，且 `PHP` 将比较代码的“instanceof”（实例类型）与指定的类。如果此比较结果为 true，`PHP` 将进入“catch”代码块，并在指定的变量标识符下使异常可用。然而，如果比较结果为 false，`PHP` 将检查后续的 catch 语句。如果当前结构中没有相关的 catch 语句，语言引擎将检查其他“try/catch”块。

以下是“throw”语句的语法：

```
throw <name_of_object>;
```

该语言不允许你抛出基本数据类型（例如整数）。实际上，`PHP` 提供了一个名为“Exception”的内置异常类。所有的异常类都应继承自此预定义类。如果你尝试抛出未链接到“Exception”类的对象，你的程序将获得运行时错误。

下面给出的代码片段将提供关于 `Exception` 类的更多信息：

```
class Exception {

  function construct ([$theMessage [,theCode]]);

  final public getInfo();

  final public getCodes();

  final public getFiles();

  final public getLines();

  final public getTraces();

  final public getTracesAsStrings();

  protected $messages;

  protected $codes;

  protected $files;

  protected $lines;

}
```

以下代码展示了如何编写一个完整的“try/catch/throw”块：

```
class NullHandle extends Exception {

  function __construct ($sample_message)

  {

    parent::construct ($sample_message);

  }

}

function printObjects ($object)

{

  if ($object == NULL) {

    throw new NullHandle (“The program received a NULL object.”);

  }

  print $object . “\n”;

}

class YourName {

  function __construct ($sampleName)

  {

    $this->sampleName = $sampleName;

  }

  function __toThisString()

  {

    return $this->sampleName;

  }

  private $sampleName;

}

try {

  printTheObject (new YourName (“John”));

  printTheObject (NULL);

  printTheObject (new YourName (“Mary”));

} catch (NullHandle $sample_exception) {

  print $sample_exception->getMessages();

  print “ in the file ” . $sample_exception->getFiles();

  print “ on the line ” . $sample_exception->getLines() . “\t”;

} catch (Exception $sample_exception) {

  // 程序不会到达此部分。

}
```

**重要提示：** 使用异常时请遵循以下规则：

1.  请记住异常就是异常。你必须仅将其用于管理问题。
2.  不要使用异常来控制程序的流程。这样做会使源代码过于复杂。
3.  异常内的数据应仅限于与错误相关的内容。这不得涉及任何参数（或额外信息）。

# 第 6 章：面向对象编程的高级概念

本章将教授你面向对象编程的高级概念和能力。如果你想在 24 小时内学会 `PHP`，请仔细阅读本材料。

## OOP 的重载能力

在 `PHP` 语言中，基于 C 的编程扩展可以重载对象定义的整个语法。另一方面，`PHP` 代码只能重载对象语法的特定子集。在本书的这一部分，你将了解可以在 `PHP` 中使用的重载特性：

### 如何重载方法和属性

该语言允许你重载方法调用和属性访问。你可以通过特殊方法来实现这些功能，这些方法将在相关方法或属性不存在时运行。这意味着你在声明自己的功能和阻止这些操作方面拥有很大的灵活性。

以下是你可以在 `PHP` 中实现的方法原型：

```
function __get ($propertyName)

function __set ($propertyName, $sampleValue)

function __call ($sampleMethod, $arguments)
```

让我们详细讨论每个原型：

*   `__get` - 此方法接受一个属性的名称。使用此原型来返回值。
*   `__set` - 你可以将属性的值和名称传递给此方法原型。
*   `__call` - 使用此原型，你可以传递一个方法的名称和一个索引数组。

下面给出的代码将展示如何使用 `__get` 和 `__set` 函数：

```
class CoordinateClass {

  private $array = array ('a' => NULL, 'b' => NULL);

  function __get ($sampleProperty)

  {

    if (array_key_exists ($sampleProperty, $this->array)) {

      return $this->array [$sampleProperty];

    } else {

      print “The system can't read properties aside from a and b\n”;

    }

  }

  function __set ($sampleProperty, $sampleValue)

  {

    if (array_key_exists ($property, $this->array)) {

      $this->array[$sampleProperty] = $sampleValue;

    } else {

      print “The system can't write properties aside from a and b\n”;

    }

  }

}

$object->a = 10;

print $object->a;

print “\n”;

$object->e = 20;

print $object->e;
```

如果你运行此脚本，你将获得以下输出：

```
10

The system can't read properties aside from a and b

The system can't write properties aside from a and b
```

由于“a”存在于对象的数组中，get 和 set 方法处理程序可以读/写正确的值。然而，在访问“e”时，无论是写入还是读取，`array_key_exists()` 都将返回 false。因此，程序将执行指定的错误消息。

你可以将 `__call()` 原型用于广泛的目的。在下面的示例中，你将了解如何生成一个委托方案：

```
class HiClass {

  function show($sampleCount)

  {

    for ($a = 0; $a < $sampleCount; $a++) {

      print “Hi, how are you?\n”;

    }

    return $sampleCount;

  }

}

class HiDelegator {

  function __construct()

  {

    $this->object = new HiClass();

  }

  function __call ($sampleMethod, $sampleArguments)      

  {

    return call_user_func_array(array ($this->object , $sampleMethod) ,

    $sampleArguments;

  }

  private $sampleObject;

}

$sampleObject = new HiDelegator();

print $sampleObject->show(5);
```

如果你运行此脚本，你的屏幕将显示：

```
Hi, how are you?

Hi, how are you?

Hi, how are you?

Hi, how are you?

Hi, how are you?

5
```

名为 `call_user_func_array()` 的函数允许 `__call()` 原型将调用和参数传递给 `HiClass::show()`。除了将调用中继给另一个对象外，你还可以从 `__call()` 方法原型返回值。

## 如何重载数组访问语法
