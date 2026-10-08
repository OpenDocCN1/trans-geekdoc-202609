

## boolean error_log(string message, integer type, string destination, string extra_headers)

error_log 函数根据 `type` 参数将错误消息发送到四个地方之一。`type` 参数的四个值列表 8.9 所示。`error_log` 的替代方案是 `syslog` 函数。

```php
//send log message via email to root
error_log("The log is working", 1, "root", "");
```

表 8.9. error_log 消息类型
| Type | Description |
| :--- | :--- |
| 0 | 根据 `error_log` 配置指令，消息将发送到系统日志或文件。 |
| 1 | 消息发送到 `destination` 参数指定的地址。如果 `extra_headers` 参数不为空，则将其作为邮件头信息发送。 |
| 2 | 消息通过远程调试系统发送。`destination` 参数指定由冒号分隔的主机和端口。 |
| 3 | 消息附加到 `destination` 参数指定的文件。 |

## boolean extension_loaded(string extension)

使用 `extension_loaded` 测试扩展是否存在。

```php
<?php
if(extension_loaded("php_mysql.dll")) {
    print("php_mysql.dll is present");
} else {
    print("php_mysql.dll is not present");
}
?>
```

## value func_get_arg(integer argument)

`func_get_arg` 函数允许你通过数字获取传递给你编写的函数的参数。第一个参数数字为 0。这允许你编写接受任意数量参数的函数。返回值可以是任何类型，

# PHP 核心编程

与所获取参数的类型匹配。`func_num_args` 函数返回可用的参数数量。

第 4 章“函数”讨论了函数，包括编写接受无限数量参数的函数。

```php
/*
** Function concat
** Input: 任意数量的字符串
** Output: string
** Description: 输入字符串按顺序
** 组合并作为单个字符串返回。
*/
function concat() {
  //start with empty string
  $returnValue = "";

  //loop over each argument
  for($i=0; $i < func_num_args(); $i++) {
    //add current argument to return value
    $returnValue .= func_get_arg($i);
  }

  return ($returnValue);
}

//prints "OneTwoThree"
print(concat("One","Two", "Three") . "<BR\n";
?>
```

## array func_get_args()

使用 `func_get_args` 获取一个包含所有传递给函数的参数的数组。数组元素由整数索引，从 0 开始。这为替代使用 `func_get_arg` 和 `func_num_args` 提供了一种备选方案。

```php
/*
** Function gcd
** Input: 任意数量的整数
** Output: integer
** Description: 返回输入中的最大
** 公公约数。
*/
function gcd() {
  /*
  ** start a smallest value and try every value
  ** until we get to 1, which is common to all
  */
  $start = 2147483647;
  foreach(func_get_args() as $arg) {
    if(abs($arg) < $start) {
        $start = abs($arg);
    }
  }
  for($i=$start; $i > 1; $i--) {
    //as we will find a gcd
    $isCommon = TRUE;

    //try each number in the supplied arguments
    foreach(func_get_args() as $arg) {
        //if $arg 除以 $i 产生
        // 余数，则我们没有找到 gcd
        if(($arg % $i) != 0) {
            $isCommon = FALSE;
        }
    }
    //if我们通过了之前的代码
    // 并且 $isCommon 仍然为 TRUE，那么我们就找到了
    // gcd
    if($isCommon) {
        break;
    }
  }
  return($i);
}
//prints 5
print(gcd(10, 20, -35) . " "<BR>\n";
?>
```

## integer func_num_args()

`func_num_args` 函数返回传递给函数的参数数量。使用示例参见 `func_get_arg` 的描述。

## boolean function_exists(string function)

使用 `function_exists` 测试函数是否可用，无论是原生提供的还是之前由 PHP 代码定义的的。

```php
<?php
$function = "date";
if (function_exists($function)) {
    print($function . " exists");
}
?>
```

## object get_browser(string user_agent)

`get_browser` 函数结合 `browsercap.ini`（浏览器能力）文件来报告浏览器的能力。`user_agent` 参数是浏览器在 HTTP 事务中用于标识自身的文本。如果你留空此参数，PHP 将使用为你创建的变量 `HTTP_USER_AGENT`。该参数与 `browsercap.ini` 文件中的所有浏览器进行匹配。当发生匹配时，每项能力都成为返回对象中的一个属性。

