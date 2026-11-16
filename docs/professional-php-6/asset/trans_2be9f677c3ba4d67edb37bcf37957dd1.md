

此外，此处提供的预打包约束类型并非详尽无遗。然而，快速浏览一下代码应该能让你非常清楚，如果应用程序需要，添加自己的约束类型是多么容易。

## 常量

你确实需要定义若干常量，以便你的类能够无缝协同工作。这些常量定义了三种参数类型（GET、POST 和 Cookies），以及你可以应用的各种约束类型。如前所述，你可以随意定义可能适合你应用程序的其他约束，只要记得在 Request 类中实现它们即可。

请检查以下代码，并将其保存为名为 constants.phpm 的文件：

```
<?php // Constants

define(VERB_METHOD_COOKIE, 1);
define(VERB_METHOD_GET, 2);
define(VERB_METHOD_POST, 4);
define(CT_MINLENGTH, 1);
define(CT_MAXLENGTH, 2);
define(CT_PERMITTEDCHARACTERS, 3);
define(CT_NONPERMITTEDCHARACTERS, 4);
define(CT_LESSTHAN, 5);
define(CT_EQUALTO, 6);
define(CT_MORETHAN, 7);
define(CT_NOTEQUALTO, 8);
define(CT_MUSTMATCHREGEXP, 9);
define(CT_MUSTNOTMATCHREGEXP, 10);
?>
```

请注意定义这些常量时的两种编号方案。其中一种是 _指数序列_，用于定义 HTTP 请求中提供的三个参数动词；另一种是纯 _顺序序列_，用于定义约束类型。

采用两种不同方法的原因，简要涉及了 _位逻辑_ 的特性。由于此主题在本书其他地方未曾涉及，让我们在此简要了解一下。

请考虑以下代码片段：

```
$var3 = ($var1 && $var2);
```

这里的条件语句明确要求 $var1 为真（字面意义上，或作为某个非零或非空值），且 $var2 为真（使用 && 运算符的传统用法来表达布尔逻辑）。如果两者都为真，$var3 也将为真。这非常基础，但还有一种第二种比较逻辑，使用相同的基本运算符 AND 和 OR。

请考虑以下内容：

```
$var3 = ($var1 & $var2);
```

请注意这个单个与号。这表示你想执行位运算（而非布尔运算）来进行比较。接下来发生的情况（假设 $var1 和 $var2 是整数）是，每个值的相应二进制位将受到传统布尔比较的影响（1 表示真，0 表示假）。如果 $var1 为 34 且 $var2 为 11，则适用以下情况：

```
34       =   00100010
11       =   00001011
34 & 11  =   00000010   =   2
```

因此，34 和 11 的位运算结果为 2，因为只有在“2”这一列中，两个数字的对应位都为 1。

这与常量有什么关系？简单来说，它使你能够将常量组合成一个单一值（该值由其组成常量的算术和构成），并随后轻松确定这些组成常量是什么。

如果每个常量代表二进制数中单个位的递增十进制值（本质上是 2 的幂），那么将它们相加后，得到的二进制数将具有值为 1 的位，表示求和中包含的那些常量：

```
CONST_A =   1   =   00000001
CONST_B =   2   =   00000010
CONST_C =   4   =   00000100
CONST_D =   8   =   00001000
CONST_E =   16  =   00010000
```

例如，假设你想定义一个由常量 B、D 和 E 组合而成的参数（不管这意味着什么）。只需将 2、8 和 16 相加得到 26。请看一下 26 的二进制形式，以及其组成部分：

```
CONST_B =   2   =   00000010
CONST_D =   8   =   00001000
CONST_E =   16  =   00010000
CONST_B+D+E =   26  =   00011010
```

请注意，你可以清楚地识别出组合的组成常量是 B、D 和 E；但是如何在代码中测试这一点呢？

从命令行（而不是 Web 浏览器）输入并运行以下代码。通常，你只需在命令提示符下输入 php 即可，但如果 PHP 可执行文件不在你的路径中，你需要先找到它——在 UNIX 上可以尝试 /usr/local/php/bin：

```
<?php
define('CONST_A', 1);
define('CONST_B', 2);
define('CONST_C', 4);
define('CONST_D', 8);
define('CONST_E', 16);

$myCombinedConstant = CONST_B + CONST_D + CONST_E;

if ($myCombinedConstant & CONST_A) {
    print "Combined constant contains A\n";
};
if ($myCombinedConstant & CONST_B) {
    print "Combined constant contains B\n";
};
if ($myCombinedConstant & CONST_C) {
    print "Combined constant contains C\n";
};
if ($myCombinedConstant & CONST_D) {
    print "Combined constant contains D\n";
};
if ($myCombinedConstant & CONST_E) {
    print "Combined constant contains E\n";
};
?>
```

按 Ctrl+D（UNIX）或 Ctrl+Z（Windows）结束脚本的输入。你将看到类似于以下内容的输出：

```
Combined constant contains B
Combined constant contains D
Combined constant contains E
```

你可能已经推断出，确定组合常量是否包含特定原始常量的测试方法，就是对该原始常量执行位运算 `AND`。只有当相关位在原始常量和正在测试的组合常量中都被设置时，这才会产生非零（即 `true`）值。

请注意，这种策略已被采用于表示请求方法的常量中，但未用于表示约束类型的常量。这是因为代码未来某个阶段可能允许将请求方法作为参数的组合传递给方法。然而，约束类型的性质意味着一个约束对象只有一个约束类型。因此，要组合约束，必须组合它们的对象（而非其背后的常量）。同样，请注意，这些常量已采用线性（1、2、3、4、5）编号系统，因为它们永远不会像本节描述的那样相互相加。

## Request 类

`request` 对象本身表示用户为生成页面而发出的请求。那些曾在 .NET 中工作过的人可能熟悉使用预实例化对象来访问参数，但这个 `Request` 类更为复杂一些。

与 .NET 不同，你必须自己实例化 `request` 对象，但你会发现编写的构造函数不需要参数。它会自行相当成功地检查现有的（且全局可访问的）`$_REQUEST`、`$_COOKIE`、`$_POST` 和 `$_GET` 散列，以填充其各种成员变量。

你可以立即开始使用 `request` 对象。通过使用提供的各种方法来检索参数，你可以构建应用程序。不过，这样做忽略了由 `Constraint` 类及其孪生类 `ConstraintFailure` 提供的非常有用的语法验证方法。

请详细检查以下名为 request.phpm 的源代码：

```
<?
require_once("constants.phpm");
require_once("constraint.phpm");
require_once("constraintfailure.phpm");
class request {
    private $_arGetVars;
    private $_arPostVars;
    private $_arCookieVars;
    private $_arRequestVars;
    private $_objOriginalRequestObject;

    private $_blIsRedirectFollowingConstraintFailure;

    private $_blRedirectOnConstraintFailure;
    private $_strConstraintFailureRedirectTargetURL;
    private $_strConstraintFailureDefaultRedirectTargetURL;

    private $_arObjParameterMethodConstraintHash;
    private $_arObjConstraintFailure;
    private $_hasRunConstraintTests;

    function __construct($check_for_cookie = true) {
    // Import variables
    global $_REQUEST;
    global $_GET;
    global $_POST;
    global $_COOKIE;
    $this->_arGetVars = $_GET;
    $this->_arPostVars = $_POST;
    $this->_arCookieVars = $_COOKIE;
    $this->_arRequestVars = $_REQUEST;
    if ($check_for_cookie) {
    if ($this->_arCookieVars["phprqcOriginalRequestObject"]) {
    $cookieVal = $this->_arRequestVars["phprqcOriginalRequestObject"];
    $this->_blIsRedirectFollowingConstraintFailure = true;
    if (strlen($cookieVal) > 0) {
    $strResult = setcookie ("phprqcOriginalRequestObject", "",
    time() - 3600, "/", "");
    $origObj = unserialize(stripslashes($cookieVal));
    $this->_objOriginalRequestObject = &$origObj;
    $this->_arRequestVars["phprqcOriginalRequestObject"] = "";
    $this->_arGetVars["phprqcOriginalRequestObject"] = "";
    $this->_arPostVars["phprqcOriginalRequestObject"] = "";
    };
    $this->_blIsRedirectOnConstraintFailure = true;
    } else {
    $this->_blIsRedirectOnConstraintFailure = false;
    };
    } else {
```

