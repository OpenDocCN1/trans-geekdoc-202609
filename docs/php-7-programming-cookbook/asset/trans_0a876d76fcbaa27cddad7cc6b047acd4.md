
# 3

## 使用 PHP 函数式编程

本章将涵盖以下主题：

- 开发函数
- 提示数据类型
- 使用返回值数据类型
- 使用迭代器
- 使用生成器编写自己的迭代器

### 简介

在本章中，我们将介绍利用 PHP **函数式编程** 特性的配方。函数式或**过程式**编程是 PHP 4 版本引入首个**面向对象编程 (OOP)** 实现之前，传统上编写 PHP 代码的方式。在函数式编程中，程序逻辑被封装到一系列离散的**函数**中，这些函数通常存储在单独的 PHP 文件中。然后，该文件可以被包含在任何未来的脚本中，从而允许随时调用所定义的函数。

### 开发函数

最困难的方面在于决定如何将程序逻辑拆分为函数。另一方面，在 PHP 中开发函数的机制相当简单。只需使用 `function` 关键字，给它一个名称，并在后面加上括号。

#### 实现方法...

1. 代码本身放在花括号内，如下所示：

```php
function someName ($parameter)
{
    $result = 'INIT';
    // one or more statements which do something
    // to affect $result
    $result .= ' and also ' . $parameter;
    return $result;
}
```

2. 你可以定义一个或多个**参数**。要使其中一个变为可选参数，只需为其分配一个默认值。如果你不确定要分配什么默认值，请使用 `NULL`：

```php
function someOtherName ($requiredParam, $optionalParam = NULL)
{
    $result = 0;
    $result += $requiredParam;
    $result += $optionalParam ?? 0;
    return $result;
}
```

你不能重新定义函数。唯一的例外是当重复的函数在不同的命名空间中定义时。以下定义将产生错误：

```php
function someTest ()
{
    return 'TEST';
}
function someTest ($a)
{
    return 'TEST: ' . $a;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_76_0.png)

3. 如果你不知道将为你的函数提供多少个参数，或者你想允许无限数量的参数，请使用 `...` 后跟变量名。所有提供的参数将以数组形式出现在该变量中：

```php
function someInfinite(...$params)
{
    // any params passed go into an array $params
    return var_export($params, TRUE);
}
```

4. 函数可以调用自身。这被称为**递归**。以下函数执行递归目录扫描：

```php
function someDirScan($dir)
{
    // uses "static" to retain value of $list
    static $list = array();
    // get a list of files and directories for this path
    $list = glob($dir . DIRECTORY_SEPARATOR . '*');
    // loop through
    foreach ($list as $item) {
        if (is_dir($item)) {
            $list = array_merge($list, someDirScan($item));
        }
    }
    return $list;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_77_0.png)

> 在函数内部使用 **static** 关键字的功能已在语言中存在了 12 年多。**static** 的作用是在**static** 声明时初始化变量一次，然后在同一请求中的函数调用之间保持该值的保留。

如果你需要在 HTTP 请求之间保留变量的值，请确保 PHP 会话已启动，并将值存储在 `$_SESSION` 中。

5. 在 PHP **命名空间**内部定义时，函数会受到约束。你可以利用这一特性，在函数库之间提供额外的逻辑分离。为了*锚定*命名空间，你需要添加 **use** 关键字。以下示例放置在不同的命名空间中。请注意，即使函数名称相同，由于它们彼此不可见，因此没有冲突。

6. 我们在命名空间 `Alpha` 中定义 `someFunction()`。我们将此保存到一个单独的 PHP 文件 `chap_03_developing_functions_namespace_alpha.php` 中：

```php
<?php
namespace Alpha;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

7. 然后我们在命名空间 `Beta` 中定义 `someFunction()`。我们将此保存到一个单独的 PHP 文件 `chap_03_developing_functions_namespace_beta.php` 中：

```php
<?php
namespace Beta;

function someFunction()
{
    echo __NAMESPACE__ . ':' . __FUNCTION__ . PHP_EOL;
}
```

8. 然后我们可以通过在函数名称前加上命名空间名称来调用 `someFunction()`：

```php
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_alpha.php');
include ( __DIR__ . DIRECTORY_SEPARATOR . 'chap_03_developing_functions_namespace_beta.php');
Alpha\someFunction();
Beta\someFunction();
```

> **最佳实践**
> 将函数库（以及类！）放入单独的文件中通常被认为是最佳实践：每个命名空间一个文件，每个文件一个类或函数库。
> 可以在单个命名空间中定义许多类或函数库。你开发到单独命名空间中的唯一原因是如果你希望促进功能的逻辑分离。

