
嵌套在另一个类内部的匿名类无法访问该外部类的 `private` 或 `protected` 方法或属性。可以通过让匿名类继承外部类来获得对外部类 `protected` 方法和属性的访问权限。可以通过构造函数将外部类的 `private` 属性传递给匿名类来获得访问权限。

例如：

![](Image00706.jpg)

![](Image00707.jpg)

# 第 27 章：命名空间

## 27.1 节：声明命名空间

命名空间声明如下所示：

| `namespace MyProject` |
| --- |

| `namespace MyProject\Security\Cryptography` |
| --- |

| `namespace MyProject` | `{` | `...` |
| --- | --- | --- |

![](Image00708.jpg)；`- 声明命名空间 MyProject`
`;` `- 声明嵌套命名空间`
`}` `- 使用大括号声明命名空间。`

建议每个文件只声明一个命名空间，尽管你可以在单个文件中声明任意数量：

![](Image00709.jpg)

每次声明命名空间后，随后定义的类都将属于该命名空间：

![](Image00710.jpg)

| `namespace MyProject\Shapes` |
| --- |

命名空间声明可以在不同文件中多次使用。上例在单个文件中于 `MyProject\Shapes` 命名空间下定义了三个类。最好将其拆分为三个文件，每个文件均以 `namespace MyProject\Shapes;` 开头。详见 PSR-4 标准示例。

## 27.2 节：引用命名空间中的类或函数

如“声明命名空间”所示，可按如下方式在命名空间中定义类：

![](Image00711.jpg)

引用该类需使用完整路径（含命名空间）：

![](Image00712.jpg)

可通过 `use` 语句导入类以简化引用：

![](Image00713.jpg)

PHP 7.0 起，可使用大括号在一条语句中分组多个 `use` 语句：

![](Image00714.jpg)

有时两个类同名。若处于不同命名空间则无问题，但若尝试用 `use` 语句导入则会冲突：

![](Image00715.jpg)

可用 `as` 关键字自定义别名解决：

![](Image00716.jpg)

引用当前命名空间外的类需用 `\` 转义，否则会假定为相对于当前命名空间的相对路径：

![](Image00717.jpg)

## 27.3 节：声明子命名空间

声明具有层级的单个命名空间示例：

![](Image00718.jpg)

![](Image00719.jpg)

上例创建了：

常量 `MyProject\Sub\Level\CONNECT_OK`、类 `MyProject\Sub\Level\Connection` 和函数 `MyProject\Sub\Level\connect`。

## 27.4 节：什么是命名空间？

PHP 社区开发者众多，代码量巨大。这意味着某库的 PHP 代码可能与另一库使用相同的类名。当两个库在同一命名空间下使用时，会发生冲突并导致问题。

命名空间解决了此问题。正如 PHP 参考手册所述，命名空间可类比为操作系统目录对文件的命名空间划分；同名文件可共存于不同目录。同理，同名 PHP 类可共存于不同 PHP 命名空间。

为代码添加命名空间至关重要，这样其他开发者使用时无需担心与其他库冲突。

# 第 28 章：会话

## 28.1 节：`session_start()` 选项

| [ph](http://php.net/manual/en/ini.list.php) [p](http://php.net/manual/en/ini.list.php) | [.](http://php.net/manual/en/ini.list.php) | [in](http://php.net/manual/en/ini.list.php) [i](http://php.net/manual/en/ini.list.php) |
| --- | --- | --- |

PHP 7 起，可向 `session_start` 函数传递包含[基于会话的](http://php.net/manual/en/ini.list.php)[选项](http://php.net/manual/en/ini.list.php)的数组。

示例

![](Image00720.jpg)

| `php` | `.` | `ini` | `setting named` | `session` | `.` | `lazy_write` |
| --- | --- | --- | --- | --- | --- | --- |

此特性还引入了 `session.lazy_write`，默认为 `true`，表示仅在会话数据变更时才重写。

参考：[https://wiki.php.net/rfc/session-lock-ini](https://wiki.php.net/rfc/session-lock-ini)

## 28.2 节：会话锁定

| `session_start` |
| --- |

| `session_start` |
| --- |

众所周知，PHP 将会话数据写入服务端文件。当请求调用 `session_start()` 的 PHP 脚本时，PHP 会锁定该会话文件，导致相同 `session_id` 的其他传入请求阻塞/等待，直到会话文件锁释放。

会话文件保持锁定直到脚本结束或手动关闭会话。为避免多请求阻塞，可启动会话后关闭会话，释放文件锁，允许后续请求继续。

![](Image00721.jpg)

即使会话关闭，仍可读取会话值，因会话数据仍可用。

![](Image00722.jpg)

PHP >= 7.0 支持 `read_only`、`read_write` 和 `lazy_write` 会话，可能无需使用 `session_write_close()`。

## 28.3 节：操作会话数据

`$_SESSION` 变量是数组，可像普通数组一样检索或操作。

![](Image00723.jpg)

更多数组操作参考“操作数组”。

注意：若在会话中存储对象，仅当有类自动加载器或类已加载时才能优雅恢复。否则对象会作为 `__PHP_Incomplete_Class` 类型返回，可能导致[崩溃](http://stackoverflow.com/q/1055728/3990767)。自动加载详见“命名空间与自动加载”。

警告：

会话数据可能被劫持。详见：《Pro PHP Security: From Application Security Principles to the Implementation of XSS Defense - Chapter 7: Preventing Session Hijacking》（https://books.google.com.au/books?id=EUc6NlZRDqcC&pg=PA97#v=onepage&q&f=false）

强烈建议切勿在 `$_SESSION` 中存储任何个人信息。最关键的是信用卡号、政府颁发的 ID、密码；也包括姓名、邮箱、电话等不太敏感但可让黑客冒充/攻破合法用户的数据。通用原则：会话数据仅使用无价值/非个人值，如数字标识符。

## 28.4 节：销毁整个会话

| [`session_destroy`](http://php.net/session_destroy) |
| --- |

若需销毁会话，可用 `session_destroy()`：

![](Image00724.jpg)

![](Image00725.jpg)

| `session_destroy()` | 与 `$_SESSION = array();` 不同 |
| --- | --- |

`session_destroy()` 会移除 SESSION 超全局变量中所有存储的值，但不会销毁实际存储的会话版本。

| `$_SESSION = array();` | 代替 `session_unset()` |
| --- | --- |

注意：用 `$_SESSION = array();` 是因[手册](http://php.net/session_destroy)规定：

![](Image00726.jpg) 仅在不使用 `$_SESSION` 的旧弃用代码中使用 `session_unset()`。

## 28.5 节：无错误的安全会话启动
