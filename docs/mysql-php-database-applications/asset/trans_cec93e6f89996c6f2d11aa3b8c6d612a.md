

```
if ($result == FALSE)
{
    // if there was an error executing the query, write out the
    // details to the error log
    $private_error = 'ack! query failed: '
        .'<li>errno='.mysql_errno()
        .'<li>error='.mysql_error()
        .'<li>query='.$query
    ;

    // just in case we were in a transaction
    @mysql_query('rollback');

    // send a generic error message to the user
    user_error('There was an error executing a query. Please '
        .'contact the system administrator.', E_USER_ERROR);
}
```

你使用$private_error变量（你的错误处理函数会检查该变量）来存储失败的查询和错误消息。然后，导致错误的查询可以写入服务器错误日志，或者如果你正在调试应用程序，直接写入屏幕。同时，用户得到的错误消息不那么显露细节（也不那么令人恐惧）。

## 错误处理和调试函数

看似不可能，但有时你会在代码中犯错。或者数据库服务器未运行，因为有人忘了重新启动它。错误总会发生。当错误发生时，拥有一种统一的响应方式很有用。PHP使你能够设置一个函数，来获取应用程序中的所有错误（那些来自PHP本身的错误——至少大部分是）——以及你在自己的代码中发现某事不对劲时引发的错误。在本节中，我们介绍一组在本书余下部分中用于处理错误的函数。这些相同的函数还以多种方式为你的代码做好调试准备，而不会干扰其正常使用。

PHP有自己的错误处理函数。显然，让别人甘愿为你做的工作由你来做并不是最简单的路径。但是，设置自己的错误处理程序是值得的，原因有二。

- 首先，它使你能够对用户体验多一些控制。当出问题时，如果你选择，用户只会看到一份平静的报告，称似乎有个小问题，而MySQL仍会将可怕的原始错误消息写入日志文件，你可以使用它来修复出错的地方。
- 其次，它可以使调试应用程序容易得多，尤其是使用一些现在存在于PHP中的函数时。

可以肯定的是，你在接下来的页面中看到的绝非Hello_World()函数。这里有很多东西在进行。而且在构思错误处理代码时调试错误几乎比一个人应该被允许拥有的乐趣还要多。但一旦你设置好它，你会发现继续完成其余工作更容易，因为它就在那里。

## error_debugging() 和 error_logging()

PHP函数error_reporting()使你能够修改默认错误处理程序显示的错误级别。在这里，你使用编程中最古老的技巧之一——偷窃——为你想要写入服务器错误日志或作为调试信息的错误类型（或其他事物）设置同样的级别：

```
function error_debugging($newlevel=NULL)
{
    static $debug_error_level = 0;
    $output = $debug_error_level;
    if ($newlevel !== NULL)
    {
        $debug_error_level = $newlevel;
    }
    return $output;
}
function error_logging($newlevel=NULL)
{
    static $log_error_level = E_ALL;
    $output = $log_error_level;
    if ($newlevel !== NULL)
    {
        $log_error_level = $newlevel;
    }
    return $output;
}
```

每个函数的工作方式都与error_reporting()一样——你可以通过传入新值来更改级别，或者通过不带参数调用函数来获取当前值。另外，当设置新值时，会返回之前的值。

## set_handler()

现在你有三个函数来跟踪你希望如何响应各种类型的错误——内置的error_reporting()函数，以及我们自己的error_debugging()和error_logging()函数——管理所有这些可能会变得棘手。因此，你创建了一个接口，使设置所需条件更加简单直接。

```
// create constants to represent normal error reporting,
// error logging, and debugging
define('H_ERROR',1);
define('H_LOG',2);
define('H_DEBUG',4);
define('H_ALL', ( H_ERROR | H_LOG | H_DEBUG));

function set_handler($newvalue=NULL, $where=NULL, $direction=NULL)
{
    // store the names of the handling functions
    static $functions = array(
        H_ERROR => 'error_reporting'
        , H_LOG => 'error_logging'
        , H_DEBUG => 'error_debugging'
    );

    // this will hold the last error level that we turned on,
    // so we can easily turn it off (see below)
    static $last_args = array();

    if ($direction === FALSE && $newvalue === NULL && $where ===
NULL)
    {
        // if we just get an argument to turn something off, but
        // not what or where, use the last error level that we
        // turned on
        list($where,$newvalue) = array_pop($last_args);
    }

    if (empty($where))
    {
        // if we don't get a request for a specific kind of
        // handler, pick a default one

        if (error_levels($newvalue))
        {
            // if the error level we're dealing with
            // is one of the standard PHP values, assume that
            // we want to change error handling
            $where = H_ERROR | H_LOG;
        }
        else
        {
            // if we're dealing with some made-up error level,
            // it's probably for debugging, so use that as
            // the default
            $where = H_DEBUG;
        }
    }

    if ($direction != FALSE)
    {
        // if we're turning on handling for something, store
        // it for turning off later
        array_push($last_args, array($where,$newvalue));
    }

    $output = 0;
    foreach ($functions as $handler => $handler_function_name)
    {
        if ($where & $handler)
        {
            // if this type of handler is one of the ones we want
            // to change, get its current value
            $handler_level = call_user_func($handler_function_name);

            // either set handling directly to new level,
            // or turn it on or off
            if ($direction == FALSE)
            {
                $handler_level = $handler_level ^ $newvalue;
            }
            elseif ($direction == TRUE)
            {
                $handler_level = $handler_level | $newvalue;
            }
            else
            {
                $handler_level = $newvalue;
            }
        }
    }
// add the new level to our result
$output = $output | $handler_level;

// call the handler function to set it to the new level
call_user_func($handler_function_name,$handler_level);
}
}

// return an OR'd sum of the changed handling values
return $output;
}
```

在此代码中，你设置了三个常量，分别对应响应错误的三种方式：H_ERROR用于捕获错误并在屏幕上显示，通过error_reporting()设置；H_LOG用于将错误写入服务器错误日志文件，通过error_logging()设置；H_DEBUG用于采取额外步骤来调试错误，通过error_debugging()设置。你在代码中使用这些常量，就像使用PHP错误级别常量（E_ERROR、E_USER_NOTICE等）一样。你还定义了一个H_ALL常量，以指示你想影响所有这些常量，就像E_ALL表示“所有错误级别”一样。

set_handler()函数通常带有三个参数调用：一个用于指定你是否要打开（TRUE）或关闭（FALSE）给定错误的处理；一个用于指定你感兴趣的错误级别或其他类型的值，例如调试常量；另一个用于指定你想影响哪个处理程序：H_ERROR、H_DEBUG、H_LOG、H_ALL表示所有，或者是将其中任意两个组合的位掩码，例如(H_ERROR|H_LOG)以影响错误报告和日志记录。

如果你为给定错误级别打开处理，你会将错误处理程序规范存储在像栈一样工作的静态数组中。这使你能够不带除OFF之外的任何参数调用set_handler(); 在这种情况下，你只需关闭最近打开的内容即可。

此函数中另一个有趣的地方是使用PHP的call_user_func()函数。对于所有三个处理程序函数，你进行完全相同的调用——一次不带任何参数，以获取当前状态；一次传入新状态。由于步骤相同，你不需要在三个地方分别硬编码。请注意，在call_user_func()中，函数名之后的参数会原样传递给被调用的函数。因此，这段代码

```
call_user_func('my_function',3,'hello',$some_variable);
```

与这段代码实际上相同：

```
my_function(3,'hello',$some_variable);
```

