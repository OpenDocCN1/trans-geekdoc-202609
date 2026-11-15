

2009-03-02 16:46:50 - 警告：calcWidgetsPerDay(): 总天数不能为
零，位于 myscript.php 第 5 行

变量：
Array
(
    [totalWidgets] => 10
    [totalDays] => 0
)

paranoidHandler() 函数会设置一个数组，将最常用的错误级别常量映射为人类可读的名称（例如 E_ERROR 和 E_PARSE 等级别被排除，因为这些始终由 PHP 错误处理程序处理）。然后它会将错误详细信息记录到 paranoid_errors.log 文件中，包括错误类型、错误消息、发生错误的文件和行号，以及出错时作用域内的变量。最后，它会调用 die() 来停止执行并向浏览器发送一条通用错误消息。（这就是为什么“这永远不会被打印”消息不会出现的原因。）

## 微调错误报告

通常，PHP 错误处理程序会报告（即记录）除 E_NOTICE 错误之外的所有错误。你可以通过调用 error_reporting() 函数来更改此默认设置，传入一个表示要记录的错误级别的掩码。

例如，若只报告 E_ERROR 错误（忽略所有其他错误），请使用以下代码：

```
error_reporting( E_ERROR );
```

若要指定多个错误级别，请使用 |（按位或）运算符将它们连接起来：

```
error_reporting( E_ERROR | E_WARNING | E_PARSE );
```

若要报告所有错误，请使用特殊常量 E_ALL：

```
error_reporting( E_ALL );
```

> E_ALL 的整数值会随 PHP 版本而变化，因为会添加更多错误级别。在 PHP 5.3 中，E_ALL 的值为 30,719。

如果要指定除特定级别或某些级别之外的所有错误报告，请将级别与 E_ALL 进行异或（XOR）运算：

```
error_reporting( E_ALL ^ E_NOTICE ^ E_USER_NOTICE );
```

若要关闭所有错误类型的错误报告，请传入值 0（请注意，致命错误仍会停止脚本运行）：

```
error_reporting( 0 );
```

由于错误报告级别存储为名为 error_reporting 的配置指令，你也可以在 php.ini 或通过 ini_set() 中设置它，并使用 ini_get() 检索其当前值：

```
error_reporting( E_ERROR );
echo ini_get( "error_reporting" ); // Displays 1
```

如果你使用 set_error_handler() 指定了自定义错误处理程序，那么无论 error_reporting 设置如何，只要发生错误，你的处理程序仍会被调用。之后是否记录错误，由你的错误处理程序决定。

## 使用异常对象处理错误

虽然 trigger_error() 和 set_error_handler() 等函数在引发和处理错误方面非常灵活，但它们也有局限性。例如，如果一段代码调用类方法且该方法中发生错误，理想情况下该方法可以直接告知调用代码发生了错误，而不必使用 trigger_error() 引发错误并经过中央错误处理程序。这样，调用代码可以采取措施修复问题，从而使应用程序更加健壮。

实现这一点的一种简单常见方法是让函数或方法返回一个特殊的错误值，例如 -1 或 false。调用代码随后可以检查返回值，如果它等于错误值，则知道出现了问题。然而，当你开始处理深度嵌套的函数或方法调用时，这会变得非常繁琐，如下面的代码所示：

```
class WarpDrive {
public function setWarpFactor( $factor ) {
if ( $factor > 1 && $factor <= 9 ) {
echo "Warp factor $factor<br />";
return true;
} else {
return false;
}
}
}

class ChiefEngineer {
public function doWarp( $factor ) {
$wd = new WarpDrive();
return $wd->setWarpFactor( $factor );
}
}

class Captain {
public function newWarpOrder( $factor ) {
$ce = new ChiefEngineer;
return $ce->doWarp( $factor );
}
}

$c = new Captain;
if ( !$c->newWarpOrder( 10 ) ) echo "She cannot go any faster!<br />";
```

如果 `WarpDrive::setWarpFactor()` 函数执行成功，则返回 `true`，否则返回 `false`（如果 warp 因子小于 1 或大于 9）。然后，该返回值需要同时通过 `ChiefEngineer::doWarp()` 方法和 `Captain::newWarpOrder()` 方法传递到调用代码，以便调用代码识别并报告错误。在复杂应用程序中，出现至少这种层级的嵌套方法调用并不罕见。

另一个问题是，仅返回 `false` 无法向调用代码说明具体出了什么问题。此外，当方法必须返回错误值时，它就无法轻松返回其他内容（因为方法和函数一次只能返回一个东西）。

幸运的是，PHP 提供了 `exceptions`，这是一种更优雅的触发和处理错误条件的方式。与返回单个错误值不同，你的方法或函数可以创建一个丰富的 `Exception` 对象，其中包含关于问题的详细信息，然后将该对象 `throw` 抛给调用代码进行处理或 `catch` 捕获。

异常的另一个优点是，如果调用代码不想捕获异常，则不必捕获；如果它忽略异常，异常会沿调用链重新抛出，直到被捕获为止。如果没有代码捕获异常，脚本会因致命错误而停止，并且异常会被记录或显示给用户（具体取决于你的 `log_errors` 和 `display_errors` 设置）。因此，通过使用异常，任何问题都可以由应用程序的另一部分自动处理，或者如果一切都失败，则报告给开发人员或用户。这使得应用程序在处理错误场景时更加灵活和健壮。

> 如果你不希望未捕获的异常引发致命错误，可以创建自己的异常处理程序来处理异常（类似于创建自己的错误处理程序）。有关详细信息，请参见 `http://www.php.net/manual/en/function.set-exception-handler.php`。

### 抛出异常

以下是在代码中发生错误时创建并抛出异常的方法：

```
throw new Exception;
```

你还可以在创建 `Exception` 对象时传递一个可选的错误消息（这通常是个好主意）：

```
throw new Exception( "Oops, something went wrong" );
```

如果你的应用程序中有许多不同的错误消息，为每个异常赋予一个数字错误代码以将其区分开来会很有帮助。要向抛出的异常添加错误代码，请在创建 `Exception` 对象时将其作为第二个参数传递：

```
throw new Exception( "Oops, something went wrong", 123 );
```

如果你没有在代码的其他位置捕获抛出的异常，最终它会冒泡到脚本的顶层，并显示类似下面的错误消息：

```
PHP Fatal error:  Uncaught exception 'Exception' with message 'Oops, something went wrong' in script.php:4 Stack trace: #0 {main} thrown in script.php on line 4
```

这表明发生了脚本自身未处理的异常，提供了错误消息，并告知你异常是在脚本的主（顶层）部分抛出的。

### 捕获异常

那么，如何在脚本中捕获异常呢？你可以使用 try ... catch 块，如下所示：

```
try {
        // Call the function or method
    } catch ( Exception $e ) {
        // Handle the exception
    }
```

try 和 catch 之间的代码会被执行。这通常包括对函数或对象方法的调用。如果这段代码导致抛出异常，则会执行 catch 之后的代码。catch 结构期望一个参数，即被抛出的 Exception 对象（本示例中的 $e）。随后如何处理异常由你决定。你可以简单地带上一条错误消息退出脚本：

```
die( "There was a problem." );
```

或者，你可以查询 Exception 对象以了解更多关于问题的信息。所有 Exception 对象都包含以下可用于获取更多信息的方法：

| 异常方法 | 方法描述 |
|---|---|
| getMessage() | 返回异常中包含的错误消息 |
| getCode() | 返回异常中包含的错误代码 |
| getFile() | 返回发生异常的脚本文件名 |
| getLine() | 返回发生异常的脚本文件中的行号 |
| getTrace() | 返回一个数组，显示导致异常的函数和/或方法调用的嵌套情况 |
| getTraceAsString() | 返回一个格式化的字符串，显示导致异常的函数和/或方法调用的嵌套情况 |

因此，例如，如果异常不太严重，你可以简单地显示异常的错误消息并照常继续：

```
try {
        // Call the function or method
    } catch ( Exception $e ) {
        echo $e->getMessage();
    }
```

如果在 try ... catch 块中没有发生异常，PHP 引擎将继续执行你的脚本，从 try ... catch 块之后的那一行开始。

