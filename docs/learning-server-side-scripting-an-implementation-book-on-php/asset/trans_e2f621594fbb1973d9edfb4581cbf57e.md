
# 正则表达式函数

您可以使用圆括号 `()` 将量词应用于整个模式。它们也可用于选择模式的部分内容以用作匹配。

我们将在何处以及如何使用这些正则表达式？我们有相应的函数来实现这一目的。我们将在这些函数中使用这些表达式。我们将在表达式中应用修饰符、量词，并将其作为函数参数使用。

让我直接向您展示一些函数，然后我们将进入实践环节。

PHP 提供了多种函数，允许您使用正则表达式。

![3-4-5-function](Images/image00210.jpeg)

## 实践

我们将在此查看一些最常用的函数。我们将在示例中使用定界符、修饰符、量词！

```php
//正则表达式
$str_array = array("Hello World","New World","Welcome to New Course", "This is a new course","Hello is the first word tested");

//区分大小写的搜索
$pattern1 = "/New/";
echo "<br>区分大小写的搜索模式: ".$pattern1;
foreach ($str_array as $str){
  echo "<br>字符串: ".$str." | 搜索结果 - ".preg_match($pattern1,$str);
}

//不区分大小写的搜索
$pattern2 = "/New/i";
echo "<br><br>不区分大小写的搜索模式: ".$pattern2;
foreach ($str_array as $str){
  echo "<br>字符串: ".$str." | 搜索结果 - ".preg_match($pattern2,$str);
}

$pattern3 = "/is/i";
echo "<br><br>不区分大小写的搜索所有模式: ".$pattern3;
foreach ($str_array as $str){
  echo "<br>字符串: ".$str." | 搜索结果 - ".preg_match_all($pattern3,$str);
}

$pattern4 = "/world/i";
echo "<br><br>不区分大小写的替换模式: ".$pattern4;
foreach ($str_array as $str){
  echo "<br>字符串: ".$str." | 搜索结果 - ".preg_replace($pattern4,'universe',$str);
}

//使用量词
$pattern5 = "/(l){2}/";
echo "<br><br>区分大小写的搜索所有模式: ".$pattern5;
foreach ($str_array as $str){
  echo "<br>字符串: ".$str." | 搜索结果 - ".preg_match($pattern5,$str);
}
```

在此示例代码片段中，我们使用了 5 个模式：

*   `$pattern1 = "/New/";`
*   `$pattern2 = "/New/i";`
*   `$pattern3 = "/is/i";`
*   `$pattern4 = "/world/i";`
*   `$pattern5 = "/(l){2}/";`

让我们分析一下上述模式！

*   此处使用的定界符是 `/`。这意味着定界符指定了模式字符串的开始和结束。
*   在末尾定界符旁边使用修饰符 `i` 将表明模式搜索应**不区分大小写**，这与默认的区分大小写搜索相反。
*   最后一个模式使用量词指定字符 `l` 应出现两次。

### 执行

执行代码，尝试检查模式搜索的输出是否与您猜测的相同。

![3-4](Images/image00211.jpeg)

---

# 3.5 异常

异常是一个描述 PHP 脚本错误或意外行为的对象。

许多 PHP 内置函数/类以及用户定义的函数/类都会抛出异常。当函数遇到无法处理的数据时，异常是停止函数执行的一种好方法。

代码中可能存在某些位置，我们认为错误的输入可能会导致错误。对于普通用户来说，他们可能不知道如何处理输入。因此，当他们提供错误输入时，异常可以给出关于出了什么问题的适当提示。

由于本书不涵盖面向对象编程，我们将仅讨论与函数相关的异常。

## 异常对象

异常对象包含有关函数遇到的错误或意外行为的信息。虽然这部分使用了对象，但我们将学习它以便在函数中使用。

我们有两个与异常相关的操作：

*   **抛出异常** - 抛出信息表明发生了某些错误
*   **捕获异常** - 说明异常是什么（提示发生了哪种错误）

### 语法

```php
new Exception(message, code, previous)
```

**参数：**

所有参数均为可选。

*   `message` - 描述抛出异常原因的字符串
*   `code` - 一个整数，可用于轻松区分此异常与其他同类型异常
*   `previous` - 如果此异常是在另一个异常的 catch 块中抛出的，建议将该异常传递给此参数

## 抛出异常

`throw` 语句允许用户定义的函数或方法抛出异常。当抛出异常时，其后的代码将不会被执行。

如果异常未被捕获，将发生致命错误，并显示 "Uncaught Exception"（未捕获的异常）消息。

### 实践

我们现在将看一个使用异常的示例。这是一个使用异常的通用示例，以便每个人都能清楚地理解。

我们将查看不抛出异常的代码片段：

```php
//异常
function divide($dividend,$divisor){
	return ($dividend / $divisor);
}

echo "<br>除法 10/5 = ".divide(10,5);
echo "<br>除法 10/0 = ".divide(10,0);
```

![3-5-1](Images/image00212.jpeg)

您看到了吗？`10/0` 给出了 infinity（无穷大）。

现在，我们将在代码中加入异常：

```php
//异常
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

echo "<br>除法 10/5 = ".divide(10,5);
echo "<br>除法 10/0 = ".divide(10,0);
```

现在，输出将是：

![3-5-2](Images/image00213.jpeg)

当该异常发现变量 `$divisor` 的值为 0 时，它不允许函数返回任何值，从而也阻止了相关的 `echo` 语句被打印。

对于使用您网页的普通用户来说，`INF` 可能不清楚，但错误消息将意味着他们的输入无效。这可能是一个小示例，因此不使用异常显示 `INF` 影响不大。此外，`INF` 值不会被进一步使用。但当您开发实时应用程序时，当一个输出被转发到程序的其他部分时，这就会变成大问题，有时会导致不受控制的循环。所以让我们练习使用异常。

现在，我们将看看 `catch` 语句。

## try...catch 语句

为了避免上述示例中的错误，我们可以使用 `try...catch` 语句来捕获异常并继续执行过程。

### 语法

```php
try {
  可能抛出异常的代码
} catch(Exception $ex) {
  捕获异常时运行的代码
}
```

`catch` 块指明应捕获哪种类型的异常以及可用于访问该异常的变量名。在上面的示例中，异常类型是 `Exception`，变量名是 `$ex`。

### 实践

```php
//异常
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

echo "<br>除法 10/5 = ".divide(10,5);
echo "<br>除法 10/0 = ";
try{
  echo divide(10,0);
}catch (Exception $ex){
  echo "Unable to divide";
}
```

### 执行

![3-5-3](Images/image00214.jpeg)

## try...catch...finally 语句

`try...catch...finally` 语句可用于捕获异常。无论是否捕获到异常，`finally` 块中的代码都将始终运行。如果存在 `finally`，则 `catch` 块是可选的。

### 语法

```php
try {
  可能抛出异常的代码
} catch(Exception $e) {
  捕获异常时运行的代码
} finally {
  无论是否捕获异常始终运行的代码
}
```

### 实践

我们将使用 `finally` 重写相同的示例：

```php
//异常
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

echo "<br>除法 10/5 = ".divide(10,5);
echo "<br>除法 10/0 = ";
try{
  echo divide(10,0);
}catch (Exception $ex){
  echo "Unable to divide";
}finally{
echo "<br> End of Program";
}
```

### 执行

现在，我们将获得包含 `finally` 块中 echo 语句的输出。

![3-5-4](Images/image00215.jpeg)

## 方法
