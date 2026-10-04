

## 附录 E：PHP 函数引用

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| checkdnsrr(string host [. string type]) | int | 检查对应给定 Internet 主机名或 IP 地址的 DNS 记录 |
| getmxrr(string hostname, array mhosts [. array weight]) | int | 获取对应给定 Internet 主机名的 MX 记录 |

## 表 E-39 数学函数

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| abs(int number) | int | 返回数字的绝对值 |
| ceil(double number) | int | 返回数字的下一个整数 |
| floor(double number) | int | 返回数字的上一个整数 |
| round(double number [, int precision]) | double | 返回四舍五入指定精度的数字 |
| sin(double number) | double | 返回弧度制数字的正弦值 |
| cos(double number) | double | 返回弧度制数字的余弦值 |
| tan(double number) | double | 返回弧度制数字的正切值 |
| asin(double number) | double | 返回弧度制数字的反正正弦 |
| acos(double number) | double | 返回弧度制数字的反正余弦 |
| atan(double number) | double | 返回弧度制数字的反正正切 |

## 表 E-39 数学函数（续）

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| atan2(double y, double x) | double | 返回 y/x 的反正正切，结果象限由 y 和 x 的符号决定 |
| pi(void) | double | 返回 pi 的近似值 |
| pow(double base, exponent) | double | 返回 base 的 exponent 次方 |
| exp(double number) | double | 返回 e 的 number 次 |
| log(double number) | double | 返回数字的自然对数 |
| log10(double number) | double | 返回以 10 为底的对数 |
| sqrt(double number) | double | 返回数字的平方根 |
| deg2rad(double number) | double | 将角度数转换为弧度数 |
| rad2deg(double number) | double | 将弧度数转换为角度数 |
| bindec(string binary_number) | int | 返回二进制数的十进制值 |
| hexdec(string hexadecimal_number) | int | 返回十六进制数的十进制值 |
| octdec(string octal_number) | int | 返回八进制字符串的十进制值 |
| decbin(int decimal_number) | string | 返回包含数字二进制表示的字符串 |
| decoct(int decimal_number) | string | 返回包含给定数字八进制表示的字符串 |
| dehex(int decimal_number) | string | 返回包含给定数字十六进制表示的字符串 |

## 附录 E：PHP 函数引用

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| base_convert(string number, int frombase, int tobase) | string | 将字符串数字从任意 <= 36 的进制转换为任意 <= 36 的进制 |
| number_format(double number [, int num_decimal_places [, string dec_separator, string thousands_seperator]]) | string | 对数字进行千分位分组格式化 |

## 表 E-40 MD5

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| md5(string str) | string | 计算字符串的 md5 哈希值 |

## 表 E-41 输出缓冲

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| ob_start(void) | void | 开启输出缓冲 |
| ob_end_flush(void) | void | 刷新（发送）输出缓冲区并关闭输出缓冲 |
| ob_end_clean(void) | void | 清除（删除）输出缓冲区并关闭输出缓冲 |
| ob_get_contents(void) | string | 返回输出缓冲区的内容 |

## 第五部分：附录

## 表 E-42 PAYFLOW 函数

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| pfpro_version() | string | 返回版本 |
| pfpro_init() | void | 初始化 |
| pfpro_cleanup() | void | 关闭 |
| pfpro_process(string_list, string host, int timeout) | string | 执行原始操作 |
| pfpro_process(array list) | array | 执行 |

## 表 E-43 CURL 函数

| 函数 | 返回 | 操作 |
| :--- | :--- | :--- |
| curl_version(void) | string | 返回版本 |
| curl_setopt(int ch, string option, mixed value) | bool | 设置选项 |
| curl_exec(int ch) | bool | 执行 |
| curl_close(int ch) | void | 关闭 |

## 附录 F：正则表达式

### 概述

正则表达式提供了一种在字符串中进行模式匹配的方法。模式可以是简单的字面量，也可以变得复杂。如果你是正则表达式初学者，这看起来可能很糟糕。

Perl 兼容正则表达式 (PCRE) 在某些方面与标准 ere 不同，并提供了一些标准 ere 函数无法实现的功能。在对正则表达式有了良好的理解后，你应该访问此页面查看差异：http://www.perl.com/pub/doc/manual/html/pod/perlre.html。主要的 PCRE 函数有 `preg_match()`、`preg_match_all()` 和 `preg_replace()`。

### 字面量模式

最简单的模式匹配是匹配已知字符。例如，要在字符串中匹配 "jay"，你可以这样做：

```php
$str = "this is a string with my name: jay";
if(ereg("jay", $str)){
  echo "pattern found";
} else {
    echo "string not found";
}
```

这将测试并打印 "pattern found"。然而，对于像这样的简单字符串，你不需要正则表达式。PHP 的一个字符串函数就能工作，而且速度快得多。例如，在上面的示例中，使用 `strstr($str, "jay")` 同样有效。

### 字符

在正则表达式中，你可以使用以下字符：

- \n- 换行
- \t- 制表符
- \r- 回车
- \f- 换页
- ^ (Shift-6)— 字符串开始
- $- 字符串结束
- . (点)- 匹配任何非换行字符。

所以，如果你需要在字符串的开头匹配单词 "jay"，你可以这样做：

```php
ereg("^jay", $str);
```

如果你想确保字符串中的 "jay" 之前或之后没有其他内容，你可以这样做：

```php
ereg("jay$", $str);
```

点（.) 的含义：它代表任何非换行字符。如果你想打印字符串中紧随 "jay" 之后的四个字符，你可以这样做：

```php
ereg("jay....", $str, $arr);
echo $arr[1];
```

