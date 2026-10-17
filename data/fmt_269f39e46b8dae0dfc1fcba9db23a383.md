
```php
function tour_brochure($info_array) {
  $city =
  isset($info_array['city']) ?
  $info_array['city'] : "Gotham City";
  $desc =
  isset($info_array['desc']) ?
  $info_array['desc'] : "great metropolis";
  $how_many =
  isset($info_array['how_many']) ?
  $info_array['how_many'] : "dozens";
  $of_what =
  isset($info_array['of_what']) ?
  $info_array['of_what'] : "customed villains";

  print("$city is a $desc filled with $how_many of $of_what.");
}
```

此函数检查单个传入的数组参数，查找与特定字符串相关的四个不同值。使用三元条件运算符`?`，将变量赋值为传入的值（如果它已存储在数组中）或我们的漫画书默认值。现在，让我们尝试用几个不同的数组调用此函数：

```php
tour_brochure(array()); // 空数组
$info_info = array(
  'city' => 'Cozumel',
  'desc' => 'destination getaway',
  'of_what' => 'sandy beaches');
tour_brochure($info_info);
```

在这个示例中，我们首先用空数组调用`tour_brochure`（对应没有参数），然后用一个存储了四个可能的关联值中的三个数组调用。我们得到的浏览器输出是：

```
Gotham City is a great metropolis filled with dozens of customed villains. Cozumel is a destination getaway filled with dozens of sandy beaches.
```

在这两种情况下，"dozens"（几十个）数量都是默认值，因为这两个数组在`"how_many"`关联下都没有任何内容。

# PHP 4 中的多参数

最后，PHP 4 提供了一些可以在函数体内部使用的函数来恢复参数的数量和值。它们是：

- `func_num_args()` 不接受参数，并返回调用它的函数所传递的参数个数。

- `func_get_arg()` 接收一个整数参数`n`，并返回调用它的函数的第`n`个参数。参数从 0 开始编号。

- `func_get_args()` 不接受参数，并返回一个包含调用函数中所有参数的数组，数组索引从 0 开始。

所有这些函数在函数体外调用时都会产生警告，如果调用`func_get_arg()`的索引高于传递的最后一个参数的索引，将给出警告。

如果你打算使用这些函数处理参数的解码，那么你可以利用这样一个事实：PHP 不会对比参数多于定义中形式参数的函数调用表示意见——只需定义你的函数不接受任何参数，然后使用这些函数捕获任何实际传递的参数即可。

例如，考虑以下两个函数，它们都返回所接收到的参数数组：

```php
function args_as_array_1 () {
  $arg_count = func_num_args();
  $counter = 0;
  $local_array = array();
  while ($counter < $arg_count) {
    $local_array[$counter] = func_get_arg($counter);
    $counter = $counter + 1;
  }
  return ($local_array);
}
```

```php
function args_as_array_2 () {
  return(func_get_args());
}
```

第一个复杂的函数使用`func_get_arg()`获取单个参数并使用`func_num_args()`限制循环，以免尝试获取比实际传递的更多的参数。每个参数单独存储在数组中，然后返回。这种参数打包已经通过`func_get_args()`免费完成，因此第二个版本的函数非常短。

作为另一个示例，让我们重写早期的`guide()`函数，使用多参数函数代替默认：

```php
function guide_2() {
  $num_args = func_num_args();
  $city = $num_args > 0 ? func_get_arg(0) : "Gotham City";
  $desc = $num_args > 1 ? func_get_arg(1) : "great metropolis";
  $how_many = $num_args > 2 ? func_get_arg(2) : "dozens";
  $of_what = $num_args > 3 ? func_get_arg(3) : "customed villains";
  print("$city is a $desc filled with $how_many of $of_what.");
}
```

这与默认参数版本的行为完全相同，并且受到相同的限制。参数按位置传递的，因此没有办法替换"customed villains"为其他内容，留下"Gotham"作为默认值。

## 值传递与引用传递

PHP 中定义函数的默认行为是"按值传递"。这意味着当你向函数调用传递变量时，PHP 会创建变量值的副本。因此，无论函数做什么，无法更改函数调用中的实际变量。这种行为可能是坏的，如果你只想使用函数的返回值，它是很好的；但如果目标是更改传递的变量，这就令人沮丧。

让我们用一个极其低效的实现演示值传递：

```php
function lame_subtract($num1, $num2) {
  if ($num1 < $num2)
    die("Negative numbers are imaginary");
  $return_result = 0;
  while($num1 > $num2) {
    $num1 = $num1 - 1;
    $return_result = $return_result + 1;
  }
  return($return_result);
}

$first_op = 492;
$second_op = 355;
$result1 = lame_subtract($first_op, $second_op);
print("result1 is $result1<BR>");
$result2 = lame_subtract($first_op, $second_op);
print("result2 is $result2<BR>");
```

令人放心的是，我们发现两次执行相同的减法时结果是相同的：

- result1 is 138

- result2 is 138

尽管`lame_subtract`改变了形式参数`$num1`，因为它只持有实际参数`$first_op`值的副本，因此`$first_op`不受影响。

## 引用传递

PHP 提供了两种让函数实际修改其参数的方法：在函数定义和函数调用中。

如果你想定义一个直接操作传递变量的函数，只需在定义中的形式参数前加上取引用符号`&`，所示：

```php
function lame_subtract_ref(&$num1, &$num2) {
  if ($num1 < $num2)
    die("Negative numbers are imaginary");
  $return_result = 0;
  while($num1 > $num2) {
      $num1 = $num1 - 1;
      $return_result = $return_result + 1;
  }
  return($return_result);
}

$first_op = 493;
$second_op = 355;
$result1 = lame_subtract_ref($first_op, $second_op);
print("result1 is $result1<BR>");
$result2 = lame_subtract_ref($first_op, $second_op);
print("result2 is $result2<BR>");
```

现在，如果我们执行与第一次完全相同的减法调用，我们得到了输出：

```
result1 = 138
result1 is 0
```

这是因为形式参数`$num1`指的是与实际参数`$first_op`相同的东西——改变一个意味着改变另一个。

你也可以通过在实际参数前加上引用符号来强制函数按引用接收参数。也就是说，我们可以使用原始的引用传递函数并获得引用引用的行为，所示：

```php
$first_op = 493;
$second_op = 355;
$result1 = lame_subtract(&first_op, &$second_op);
print("result1 is $result1<BR>");
$result2 = lame_subtract(&first_op, &$second_op);
print("result2 is $result2<BR>");
```

再次产生了

```
result1 is 138
result1 is 0
```

从 PHP 4 开始，变量引用现在也可以在函数调用之外使用。通常情况下，将变量引用`&variable`赋值给变量将使这两个变量成为彼此的别名，而不是具有相同值的不同变量。例如：

```php
$name_1 = "Manfred von Richtofen";
$name_2 = "Percy Blakeney";
$alias_1 = &$name_1; // 变量具有相同值
$alias_2 = &$name_2; // 变量是同一个
```

```php
$alias_1 = "The Red Baron"; // 不改变真名
$alias_2 = "The Scarlet Pimpernel"; // 永远匿名
```

```php
print("alias_1 is $name_1<BR>");
print("alias_2 is $name_2<BR>");
```

将给出输出：

```
The Red Baron is Manfred von Richtofen
The Scarlet Pimpernel is the Scarlet Pimpernel
```

## 变量函数名

在 PHP 中可以操作的一个非常整洁的技巧是使用变量来代替用户定义函数的名称。也就是说，你不需要在代码中输入字面量函数名，而是输入一个美元符号变量——运行时实际调用的函数将取决于该变量所赋值的字符串。在某种意义上，这允许我们把函数当作数据使用。这种技巧对于高级 C 程序员来说非常熟悉，甚至对于任何 Lisp 语言（例如 Scheme 或 Common Lisp）的初学者来说也是如此。

例如，这两个函数调用是完全等价的：

```php
function customized_greeting() {
    print("You are being greeted in a customized way!<BR>");
}
customized_greeting();
$my_greeting = 'customized_greeting';
$my_greeting();
```

并且产生相同的输出：

```
You are being greeted in a customized way!
You are being greeted in a customized way!
```

因为函数名只是字符串，所以它们也可以作为函数的参数，或者作为函数的返回结果。

## 扩展示例

为了好玩，让我们看看通过使用一些高级的特性（包括将函数名作为函数参数）会带来什么样的麻烦。

列表 8-1 显示了一个实现替换密码的函数扩展示例——这是一种原始的加密方法，通过将字母表中的一个字母替换另一个字母来打乱消息。

> 注意 这代码比书中为止的任何内容都长且更复杂。对于那些不想研究细节的人来说，它是可以跳过和快速浏览的。

## 列表 8-1: 替换密码

```php
/* Part 1 - 密码算法和工具函数 */
function add_1 ($num)
{
    return(($num + 1) % 26);
}

function sub_1 ($num)
{
    return(($num + 25) % 26);
}

function swap_2 ($num)
{
    if ($num % 2 == 0)
        return($num + 1);
    else
        return($num - 1);
}

function swap_26 ($num)
{
    return(25 - $num);
}

function lower_letter($char_string)
{
    return (ord($char_string) >= ord('a')) &&
           (ord($char_string) <= ord('z'));
}

function upper_letter($char_string)
{
    return (ord($char_string) >= ord('A')) &&
           (ord($char_string) <= ord('Z'));
}

/* Part 2 - letter_cipher 函数 */
function letter_cipher($char_string, $code_func)
{
    if (!upper_letter($char_string) ||
        lower_letter($char_string))
        return($char_string);
    if (upper_letter($char_string))
        $base_num = ord('A');
    else
        $base_num = ord('a');
    $char_num = ord($char_string) - $base_num;

return(chr($base_num +
    ($code_func($char_num) % 26)));
}
```

```php
/* Part 3 - 主 string_cipher 函数 */
function string_cipher($message, $cipher_func)
{
    $coded_message = "";
    $message_length = strlen($message);
    for ($index = 0;
         $index < $message_length;
         $index++) {
        $coded_message .=
        letter_cipher($message[$index], $cipher_func);
    }
    return($coded_message);
}
```

列表 8-1 分三个部分。在第一部分，我们定义了对 0 到 25 的数字进行简单数学运算的函数，这些数字将代表我们密码中的字母 A–Z。函数`add_1`将其数字加 1，并对 26 取模（这意味着数字 26 和更大的数字会"回绕"从零重新开始）。0 变成 1，1 变成 2，……以及 25 变成 0。`sub_1`向另一个方向移动数字，加上 25（这在模运算中等同于减去 1）——25 变成 24，24 变成 23，……以及 0 变成……`swap_2`交换数字对的位置——0 到 1，1 到 0，2 到 3，3 到 2……。`swap_26`将高数字与低数字交换（25 到 0，0 到 25，24 到 1，1 到 24……）。这些每一个函数将成为测试字符是大写字母还是小写字母的简单密码的基础。

第二部分是`letter_cipher()`，它的工作是创建一个像第一部分那样的数学函数，并将其应用于单个字母。它测试所接收到的字符串（本应该是单个字符）是否为字母；如果不是，则原样返回。如果是，它会被转换为一个数字`ord()`，并从中减去适当的字母（'a' 或 'A'）以将数字带入 0-25 的范围。如果在范围内，我们应用名称以字符串形式传递的密码函数，然后将数字转换回字母并返回它。

最后，第三部分是`string_cipher`函数，它接收一条消息和一个密码函数`cipher_func`，然后遍历消息，对每个字符应用密码函数并构建加密后的消息。

你也可以编写自己的函数，其使用方法与内置函数完全相同。函数使用简单的 C 风格语法编写，例如：

```c
function my_function ($arg1, $arg2, ..)
{
    statement1;
    statement2;
}

return($value);
```

用户定义的函数可以使用任何 PHP 类型的参数，也可以返回任何类型的返回值。不需要声明参数和返回值的类型。

在 PHP 4 中，函数定义和函数调用的顺序没有区别，只要每个被调用的函数都恰恰定义一次即可。不需要单独的函数声明或原型。在函数内部赋值的变量是该函数的局部变量，除非通过`global`声明另有指定。局部变量可以声明为`static`（静态），这意味着它们在函数调用之间会保留其值。
