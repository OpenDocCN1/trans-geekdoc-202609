

## push_handler() 和 pop_handler()

这些函数使用 set_handler() 的栈功能，使更改错误处理级别变得更加简单。

```
function push_handler($newvalue=0, $where=NULL)
{
    return set_handler($newvalue,$where,TRUE);
}
function pop_handler($newvalue=NULL, $where=NULL)
{
    return set_handler($newvalue,$where,FALSE);
}
```

push_handler() 和 pop_handler() 函数并不复杂；它们只是省去了你为 set_handler() 编写第一个参数的麻烦。但在你的应用程序代码中，它们更容易遵循。如果你想打开用户通知（即 PHP E_USER_NOTICE 错误级别）的日志记录，可以这样写：

```
push_error_handler(E_USER_NOTICE, H_LOG);
```

而要再次关闭它：

```
pop_error_handler(E_USER_NOTICE, H_LOG);
```

或者只需这样：

```
pop_error_handler();
```

这不算地道的英语，但相对清晰。

在这里，你所做的决策与你决定如何向函数传递参数时所做的决策类似。完全可以跳过 set_handler()、push_handler() 和 pop_handler() 函数，直接使用处理程序函数：

```
error_reporting(error_reporting() | E_USER_NOTICE);
error_logging(error_logging() | E_USER_NOTICE);
```

函数调用会变得稍微晦涩一点，但也并非十分晦涩。由你来找到平衡点。你是把一段相当复杂的代码放在一个地方，还是把稍微复杂的代码分散在很多地方？这个问题没有通用的答案。

## error_handler()

说到在一个地方放置一段相当复杂的代码，现在你可以查看你的实际错误处理函数了。你使用 PHP 函数 set_error_handler() 来告诉 PHP，每当代码中发生错误时就调用你自己的函数。该函数随后负责执行 PHP 默认错误处理程序所做的所有工作。它会检查当前的错误报告级别，以查看是否应该对特定错误做出反应；它控制用户看到哪种错误消息，等等。

> 并非每个 PHP 错误都会发送到错误处理函数。例如，对未定义函数的调用不会。正如手册所说：“以下错误类型无法使用用户定义的函数来处理：E_ERROR、E_PARSE、E_CORE_ERROR、E_CORE_WARNING、E_COMPILE_ERROR 和 E_COMPILE_WARNING。” 有关更多信息，请查看手册页面：http://www.php.net/manual/en/function.set-error-handler.php。

```
function error_handler($error_level,$error,$file,$line,$context)
{
    // $context is an array of all the variables defined at the
    // time of the error. so we can check it to see if the
    // variables $public_error, $private_error, or $debug were
    // defined.

    if (array_key_exists('public_error', $context))
    {
        $public_error = $context['public_error'];
    }
    else
    {
        $public_error = $error;
    }

    if (array_key_exists('private_error', $context))
    {
        $private_error = $context['private_error'];
    }
    else
    {
        $private_error = '';
    }

    // the value for $debug that we'll use is a combination of the
    // value of the $debug variable in the scope of the line where
    // the error occurred (if defined), the setting of the debugging
    // level for the file from debug_file() (if there is one), and
    // the value of the constant DEBUG (if defined).

    if (array_key_exists('debug', $context))
    {
        $debug_scope = $context['debug'];
    }
    else
    {
        $debug_scope = 0;
    }

    $debug_file = debug_file($file);
    if (defined('DEBUG'))
    {
        $debug_constant = constant('DEBUG');
    }
    else
    {
        $debug_constant = 0;
    }

    $debug = $debug_scope | $debug_file | $debug_constant;

    // get the current error handling levels
    $error_reporting = error_reporting();
    $error_logging = error_logging();
    $error_debugging = error_debugging();

    // get the name of the constant that matches the error
    // (if there is one)
    $error_name = error_levels($error_level, "_Error#$error_level");
    $public_name = substr($error_name,strrpos($error_name,'_')+1);

    // write the error to the server error log if it's of a level
    // that we're interested in

    if ($error_logging & $error_level)
    {
        $logerror = "$error_name file: $file line: $line\n"
        . " error: $error\n"
        ;
    }

    if ($public_error && $public_error != $error)
    {
        $logger .= "  public_error: $public_error\n";
    }

    if ($private_error && $private_error != $error
        && $private_error != $public_error
    )
    {
        $logger .= "  private_error: $private_error\n";
    }

    error_log($logger);
}

// if $debug is set to something that we're debugging at the
// moment, add some stuff to the error message and make sure
// it gets displayed, no matter what the error_reporting level is

if ($error_debugging && $debug)
{
    $debug_error = " <li>error: $error\n";
    if ($public_error && $public_error != $error)
    {
        $debug_error .= " <li>public_error: $public_error\n";
    }
    if ($private_error && $private_error != $error
        && $private_error != $public_error
    )
    {
        $debug_error .= " <li>private_error: $private_error\n";
    }

    $debug_error .= "<li>backtrace:<ul>\n";

    $backtrace = debug_backtrace();

    foreach ($backtrace as $skip)
    {
        $class = 'NoClass';
        $function = 'NoFunction';
        $file = 'NoFile';
        $line = 'NoLine';
        extract($skip, EXTR_IF_EXISTS);
    }

    $debug_error .= sprintf("\t<li>%s::%s [%s:%s]\n"
        . $class
        . $function
        . $file
        . $line
    );

    $debug_error .= "</ul>\n";

    $public_error .= $debug_error;

    // if E_ALL has been explicitly set in the debug mask
    // dump *everything*...
    if (($error_debugging & E_ALL) == E_ALL)
    {
        // OK, not everything. but you can uncomment this
        // if you want.

        // $context = array_merge(
        //     $context, get_defined_constants()
        // );

        $public_error .= "<li>context:".dumpvar($context)."\n";
    }

    elseif (!($error_reporting & $error_level))
    {
        // if the error is not of a level that we're reporting,
        // blank out the error message
        $public_error = '';
    }

    if (!empty($public_error))
    {
        print <<<EOO
<blockquote>
<b>$public_name:</b>
$public_error
</blockquote>
EOO;
    }

    if (error_debugging() & get_constant('fatal'))
    {
        exit;
    }
}

switch ($error_level)
{
    // the non-fatal errors
    case E_NOTICE:
    case E_USER_NOTICE:
    case E_WARNING:
    case E_USER_WARNING:
        return;

    // everything else is fatal
    default:
        exit;
}
```

首先我们应该讨论的是参数。因为是 PHP 在调用该函数，所以由 PHP 定义参数是什么。第一个参数 $error_level 是错误类型，与预定义的错误级别常量匹配。你可以在网上找到这些常量列表：http://www.php.net/manual/en/ref.errorfunc.php。

第二个参数 $error 是错误消息的文本。这可能是 PHP 自己的错误消息；如果你使用 user_error() 触发了一个错误，那么它就是传递给该函数的文本。接下来的两个参数 $file 和 $line 告诉你错误发生时的文件名及该文件中的行号。最后一个参数 $context 是错误发生时作用域内所有变量的关联数组。（要小心处理这个参数——如果错误发生在函数外部，在全局作用域中，那么它不仅包含你自己的全局变量，还包含所有 PHP 超全局变量。由于某些变量会包含其他变量——例如 $_REQUEST 包含 $_POST、$_GET 和 $_COOKIE——因此尝试转储此数组可能会导致递归问题。）

最后一个参数 $context 是你可以好好利用的东西。首先，你可以从中获取 $debug 的局部值。它还能让你查看是否设置了“私有”错误消息。例如，在 my_query() 函数中，你可以使用它来捕获 MySQL 错误消息：

```
$private_error = 'ack! query failed: '
    .'<li>errorno='.mysql_errno()
    .'<li>error='.mysql_error()
    .'<li>query='. $query
    ;
```

然后，错误处理程序可以将其写入错误日志，或将其打印为调试输出，具体取决于你的设置。同时，为用户设置了一条通用消息：

