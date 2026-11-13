
user_error('There was an error executing a query. Please contact the system administrator.', E_USER_ERROR);

您还可以设置“公开错误”消息，它将用于代替默认错误消息。这种策略是覆盖可能出现的常规PHP错误情况的一种方法。

接下来，您检查是否已开启调试。只需将名为 $debug 的变量设置为适当值即可——这种方法非常适合在函数内进行调试。或者，您可以使用 debug_file() 函数在文件级别设置调试（参见下一节）。您也可以定义一个名为 DEBUG 的常量，该常量在应用程序的任何位置都可见。

您会与处理程序函数联系，以查看如何响应错误。如果已开启日志记录，则会将消息写入错误日志。如果已开启调试，则会创建用于显示的详细调试消息。如果错误报告设置为显示此级别的错误，则会准备一条向用户显示的消息。

在设置调试消息时，您可以使用 PHP 中一个非常棒的新功能，即 debug_backtrace() 函数。该函数返回一个数组，包含从初始 URL 到当前位置所经历的所有函数和文件，包括相关行号。当您从五六层深的函数中收到错误时，这个函数简直是救星。

最后，您会向屏幕显示一条消息（如果有的话），然后根据情况从函数返回主程序（如果是警告或通知），或退出（如果是完全错误）。

## debug_file()

您在错误处理程序中看到了这个函数。debug_file() 函数为整个文件设置调试级别：

```
function debug_file()
{
    // store the file names for which we set up debugging levels
    static $debug_files = array();

    // some quick & dirty argument handling. we can do this
    // because we're only interested in two possible arguments,
    // $file and $level

    $args = func_get_args();
    $file = NULL;
    $level = NULL;
    foreach ($args as $arg)
    {
        switch (gettype($arg))
        {
            case 'array':
            case 'object':
                extract((array)$arg,EXTR_IF_EXISTS);
                break;
            case 'string':
                $file = $arg;
                break;
            case NULL:
                break;
            default:
                $level = (int)$arg;
        }
    }

    if (!$file)
    {
        // if no file name is given, use the current
        // file by default.

        // we want to find the path to the file that called
        // this function,
        // so we can't use __FILE__ - that'll just give
        // us the name of
        // the file where this function is defined.
        // use debug_backtrace()
        // instead.
        $backtrace = debug_backtrace();
        $last = array_shift($backtrace);
        $file = $last['file'];

        if ($level === NULL)
        {
            // if we're using a default file name, then if no level
            // is passed in, set up a default level as well
            $level = get_constant($file);
        }
    }
    else
    {
        $rfile = realpath($file);
        if ($rfile)
        {
            $file = $rfile;
        }
    }

    if ($level !== NULL)
    {
        // if we're given a level for a file (or have set one
        // as a default case), make a record of it
        $debug_files[$file] = $level;
    }

    // in any case, return the current level for this file,
    // if there is one, or FALSE if there isn't

    if (array_key_exists($file, $debug_files))
    {
        return $debug_files[$file];
    }
    // so now do more tedious file name matching
    $pat = "/".str_replace("/",".",$file)."/i";
    return current(preg_grep($pat, array_keys($debug_files)));
}
```

大多数时候，如果您想调试代码的一部分，只需将 $debug 设置为调试处理程序正在监视的值即可。不过，有时您可能希望为特定文件中的所有代码开启调试。这在简单的网页或包含的文件中很常见，为 $debug 赋值会使其处于全局作用域，并可能触发大量您不希望看到的调试代码。debug_file() 正好解决了这个问题。它存储一个错误级别或其他值，并将其与单个文件关联。当发生错误，或您的代码调用 user_error() 时，错误处理例程会使用 debug_file() 来查看您是否为发生错误的文件设置了任何内容。

## get_constant()

当您想要定义一个用于位掩码的常量，就像将 E_WARNING 与 error_reporting() 一起使用一样，该常量的实际值并不特别重要，只要它不与您为同一目的使用的其他常量冲突即可。get_constant() 正是为此而生：

```
function get_constant($constname='')
{
    // start at one above E_USER_NOTICE to avoid conflicts
    // (we can't initialize a static variable to an expression,
    // so we have to start it off as NULL and then fix that.)
    static $last_constant = NULL;
    if ($last_constant == NULL)
    {
        $last_constant = E_USER_NOTICE << 1;
    }
    static $defined_constants = array();
    static $defined_or = 0;

    $output = 0;
    if (!empty($constname))
    {
        if (!defined($constname))
        {
            define($constname, $last_constant);
            $defined_constants[$constname] = $last_constant;
            $defined_or = $defined_or | $last_constant;
            $last_constant = $last_constant << 1;
        }
        $output = constant($constname);
    }
    else
    {
        // if no constant name is given, hand back the equivalent
        // of E_ALL for the constants defined so far
        $output = $defined_or;
    }
    return $output;
}
```

此函数的另一个目的是让您获取在其他位置定义的常量的值——或者您将要定义的常量的值，这听起来有点像时空旅行功能，只是因为该定义并不真正准确。其工作原理如下：假设在名为 foo() 的函数中，您调用了 get_constant()：

```
function foo()
{
    get_constant('MY_CONSTANT');
    print "<h4>my constant is ".MY_CONSTANT."</h4>\n";
}
```

在应用程序的正常运行过程中，这可能是对 get_constant() 的第五次调用，因此 MY_CONSTANT 最终将被定义为 32768。但是，假设您想在其他地方监视 MY_CONSTANT，例如在调试函数中。您可以在应用程序的头文件中放置相同的 get_constant() 调用：

```
$global_variable = get_constant('MY_CONSTANT');
```

这是执行的第一次 get_constant() 调用，因此 MY_CONSTANT 将被定义为 2048。关键是，这无关紧要。当 foo() 函数进行其 get_constant() 调用时，将返回相同的值。只要 MY_CONSTANT 在应用程序的任何位置都表示相同的值，那才是重要的。

## Summary

如果您想了解其余代码如何组合在一起，请查看随附的光盘。其他文件都有很好的注释，应该相对容易理解。

本章结束时，您应该理解两个概念：

- 首先，递归。递归是一个很棒的工具，有时非常有用。
- 第二，我们组织数据的方式。我们没有遵循严格的规范化程序，就像在第 1 章中描述的那样。在这里，我们更关注的是什么能完成工作。归根结底，所有应用程序开发人员不都是这样做的吗，对吧？

最后，我们介绍了如何设置自己的错误处理程序，以及一些可能的用途。与 HTML 函数一样，您可能会决定采用不同的方法。如果是这样，请随意忽略我们的示例。

## Content-Management System

### 本章内容

- 创建一个经济实惠的内容管理系统
- 维护数据库安全性
- 预期 MySQL 权限方案的不足之处

欢迎来到本书中我们最喜欢的应用程序。请不要误会，我们喜欢留言簿，喜欢购物车，也钟爱问题跟踪器。但是，由于我们早年一直在处理产生大量文本内容的网站，我们深知建立某种内容管理系统的重要性。

内容管理系统种类繁多，形状、大小和成本各不相同。根据您的需求（或贵公司的需求），您可能倾向于在类似 Vignette 的东西上进行五位数投资，或在类似 Broadvision 的东西上进行六位数至七位数投资。但您的选择不止这些。Zope (http://www.zope.org)、Midgard (http://www.midgard-project.org/) 和 FileNet（曾名为 eGrail，http://www.filenet.com/）只是内容管理的三种开源选项。

鉴于所有这些选项，您可能会想，为什么要考虑使用这里介绍的应用程序——为什么不直接使用上述应用程序之一呢？事实上，有一个绝佳的理由。内容管理是一个需要高度定制的领域。您公司的关注点将与其他公司不同，无论您最终使用哪种系统，您都需要编写大量代码才能使系统完全按照您的意愿运行。例如，如果您决定使用 Vignette，您需要学习一种名为 Tcl（发音为“tickle”）的讨厌的小语言，或者使用 Java 编写。如果您想使用 Zope，则必须将 Python 加入您的技能集。Midgard 是一个基于 PHP 的应用程序，毫无疑问其中有很多优秀的代码。它是开源的，并为参与开发日益复杂的软件提供了绝佳机会。但您可能只想要一个属于自己的东西，一个您了如指掌的应用程序，一个专为解决贵组织特定问题而构建的东西。所以，请查看可用的内容，
