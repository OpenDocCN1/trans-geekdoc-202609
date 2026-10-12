
定界符可以是任何非字母、数字、反斜杠或空格的字符。最常用的定界符是正斜杠（`/`），但当您的模式包含正斜杠时，选择其他定界符（如 `#` 或 `~`）会更方便。

#### 模式

模式或搜索模式是我们用于搜索的字符序列。方括号用于查找字符范围：

![3-4-1-pattern](img/image00206.jpeg)

**注意：**

如果您的表达式需要搜索特殊字符之一，可以使用反斜杠（`\\`）进行转义。

#### 修饰符

修饰符可以更改搜索的执行方式。

![3-4-2-modifier](img/image00207.jpeg)

我们还可以在正则表达式中提及一些元字符和量词。

##### 元字符

元字符是具有特殊含义的字符。它们可以包含在搜索模式中。

![3-4-3-metacharacter](img/image00208.jpeg)

##### 量词

量词定义数量。这告诉搜索字符或搜索模式的出现次数。

![3-4-4-quantifier](img/image00209.jpeg)

##### 分组

##### 正则表达式函数

您可以使用圆括号 `()` 将量词应用于整个模式。它们也可用于选择模式的部分内容以用作匹配。

我们将在何处以及如何使用这些正则表达式？我们有相应的函数来实现这一目的。我们将在这些函数中使用这些表达式。我们将在表达式中应用修饰符、量词，并将其作为函数参数使用。

让我直接向您展示一些函数，然后我们将进入实践环节。

PHP 提供了多种函数，允许您使用正则表达式。

![3-4-5-function](img/image00210.jpeg)

##### 实践

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

##### 执行

执行代码，尝试检查模式搜索的输出是否与您猜测的相同。

![3-4](img/image00211.jpeg)

---

#### 3.5 异常

异常是一个描述 PHP 脚本错误或意外行为的对象。

许多 PHP 内置函数/类以及用户定义的函数/类都会抛出异常。当函数遇到无法处理的数据时，异常是停止函数执行的一种好方法。

代码中可能存在某些位置，我们认为错误的输入可能会导致错误。对于普通用户来说，他们可能不知道如何处理输入。因此，当他们提供错误输入时，异常可以给出关于出了什么问题的适当提示。

由于本书不涵盖面向对象编程，我们将仅讨论与函数相关的异常。

##### 异常对象

异常对象包含有关函数遇到的错误或意外行为的信息。虽然这部分使用了对象，但我们将学习它以便在函数中使用。

我们有两个与异常相关的操作：

*   **抛出异常** - 抛出信息表明发生了某些错误
*   **捕获异常** - 说明异常是什么（提示发生了哪种错误）

###### 语法

```php
new Exception(message, code, previous)
```

**参数：**

所有参数均为可选。

*   `message` - 描述抛出异常原因的字符串
*   `code` - 一个整数，可用于轻松区分此异常与其他同类型异常
*   `previous` - 如果此异常是在另一个异常的 catch 块中抛出的，建议将该异常传递给此参数

##### 抛出异常

`throw` 语句允许用户定义的函数或方法抛出异常。当抛出异常时，其后的代码将不会被执行。

如果异常未被捕获，将发生致命错误，并显示 "Uncaught Exception"（未捕获的异常）消息。

##### 实践

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

![3-5-1](img/image00212.jpeg)

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

![3-5-2](img/image00213.jpeg)

当该异常发现变量 `$divisor` 的值为 0 时，它不允许函数返回任何值，从而也阻止了相关的 `echo` 语句被打印。

对于使用您网页的普通用户来说，`INF` 可能不清楚，但错误消息将意味着他们的输入无效。这可能是一个小示例，因此不使用异常显示 `INF` 影响不大。此外，`INF` 值不会被进一步使用。但当您开发实时应用程序时，当一个输出被转发到程序的其他部分时，这就会变成大问题，有时会导致不受控制的循环。所以让我们练习使用异常。

现在，我们将看看 `catch` 语句。

##### try...catch 语句

为了避免上述示例中的错误，我们可以使用 `try...catch` 语句来捕获异常并继续执行过程。

###### 语法

```php
try {
  可能抛出异常的代码
} catch(Exception $ex) {
  捕获异常时运行的代码
}
```

`catch` 块指明应捕获哪种类型的异常以及可用于访问该异常的变量名。在上面的示例中，异常类型是 `Exception`，变量名是 `$ex`。

##### 实践

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

##### 执行

![3-5-3](img/image00214.jpeg)

##### try...catch...finally 语句

`try...catch...finally` 语句可用于捕获异常。无论是否捕获到异常，`finally` 块中的代码都将始终运行。如果存在 `finally`，则 `catch` 块是可选的。

###### 语法

```php
try {
  可能抛出异常的代码
} catch(Exception $e) {
  捕获异常时运行的代码
} finally {
  无论是否捕获异常始终运行的代码
}
```

##### 实践

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

##### 执行

现在，我们将获得包含 `finally` 块中 echo 语句的输出。

![3-5-4](img/image00215.jpeg)

##### 方法

捕获异常时，下表展示了一些可用于获取异常信息的方法：

![3-5-methods](img/image00216.jpeg)

**练习：**

我们将结合上述讨论的方法，查看相同的编码示例。

希望你会产生一个疑问：如果 `try` 块被执行会发生什么？这个问题也将得到解答。

```php
//Exception
function divide($dividend,$divisor){
 if($divisor == 0){
	throw new Exception("Division by zero");
 }
 return ($dividend / $divisor);
}

try{
  echo "<br>Division 10/5 = ".divide(10,5);
}catch(Exception $ex){
  echo "No error in input";
}

echo "<br>Division 10/0 = ";
try{
  echo divide(10,0);
}catch (Exception $ex){
  $code = $ex->getCode();
  $message = $ex->getMessage();
  $file = $ex->getFile();
  $line = $ex->getLine();
  echo "Exception thrown in $file on line $line: [Code $code] $message";
}
```

**执行：**

当 `try` 块被执行时，`catch` 块不会被执行。这类似于 `if...else` 语句的执行。两个块中只会有一个被执行！

希望你能理解：

*   `$ex->getCode()` - 返回异常代码
*   `$ex->getMessage()` - 从函数内部的 `Exception()` 对象中获取消息
*   `$ex->getFile()` - 获取抛出异常的完整文件路径
*   `$ex->getLine()` - 获取抛出异常的行号（`Exception()` 对象）

![3-5-5](img/image00217.jpeg)

如果你是新手程序员，你可能会觉得为什么要去处理这些异常。在学习和练习的语境下，你或许是对的。但在开发过程中，优秀的程序员应该定义好代码中所有可能的块，以便为最终用户避免不必要且不明确的错误。

希望当你开始从事实时应用开发时，会开始使用异常。

---

### 第 4 章：文件与表单

---

*   [](#part0025.xhtml) #### 4.1 文件处理
*   [](#part0026.xhtml) #### 4.2 超全局变量
*   [](#part0027.xhtml) #### 4.3 表单操作
*   [](#part0028.xhtml) #### 4.4 表单验证
*   [](#part0029.xhtml) #### 4.5 文件上传

---

#### 4.1 文件处理

---

文件处理是 Web 应用程序的一个重要方面。本节介绍如何在服务器上操作文件。

PHP 拥有多个用于创建、打开、读取、上传和编辑文件的函数。

**创建 / 打开文件：**

在 PHP 中，要打开文件或将文件写入服务器，我们需要创建该文件。所有这些任务均由单个函数完成。这意味着：

*   当你创建时，需要打开；一旦打开，就需要将其写入服务器
*   当你想将文件写入服务器时，显然必须打开它
*   当你想打开一个文件时，它必须是已创建的或已存在的。

**函数：`fopen()`**

如果对不存在的文件使用 `fopen()`，它将创建该文件，前提是该文件以写入 (`w`) 或追加 (`a`) 模式打开。写入意味着开始写入内容，而追加意味着向现有内容添加更多内容。

参数：

`fopen(文件名, 打开模式);`

我们来看看可用的各种模式：

![4-1-filemodes](img/image00218.jpeg)

创建新文件时，需要使用 `w`。

**练习：**

希望你的新文件 `section4.php` 已创建并打开以供编辑。我们首先创建一个文件用于写入：

```php
$testfile = fopen("test.txt", "w");
```

执行后，你将在 `section4.php` 所在的位置发现一个已创建的文本文件。

创建了一个大小为 0 字节的新文件。该文本文档将没有内容。

![4-1-1](img/image00219.jpeg)

**注意：** 如果尝试运行此代码时出现错误，请检查是否已授予 PHP 文件向硬盘写入信息的访问权限。

*   要授予访问权限，右键点击文件夹 `PracticePHP` => 属性 => 取消勾选“只读”
*   转到“安全”选项卡 => 检查相应用户所需的权限

你还记得第 2 节中的**资源数据类型**吗？

`$testfile` 属于资源数据类型——虽然不是实际类型，但它在此处持有一个资源，如文件。

**向文件写入内容：**

有一个函数 `fwrite()` 可将内容写入文件。

理解：

*   当你打开一个文件时，该文件会被写入服务器
*   但当你使用 `fwrite()` 写入时，意味着你正在向文件添加内容

希望你理解这两种“写入”的区别。当你打开文件时，你以写入模式打开，并将其指定为 `w`。而函数 `fwrite()` 则用于写入内容。

有 2 个参数：

`fwrite(文件名, 要添加的内容);`

**练习：**

我们将向文件添加几个字符串字符：继续在同一个 `section4.php` 中编码：

```php
$texttoadd = "First Line of Text followed by new line character! ";
fwrite($testfile,$texttoadd);
$texttoadd = "Second Line of Text followed by new line character! ";
fwrite($testfile,$texttoadd);
```

暂不要执行，我们将关闭文件后再执行。

**关闭文件：**

写入完成后，我们必须关闭文件。这就像打开文件后必须关闭它一样。

函数 `fclose()` 负责关闭文件。

**练习：**

在上述代码中添加以下行：

```php
fclose($testfile);
```

在完成文件操作后关闭所有文件是一个良好的编程习惯。打开的文件会占用资源。

现在，执行该 PHP 文件，然后前往 `text.txt` 所在的路径。打开 `text.txt`，你将看到以下几行：

![4-1-2](img/image00220.jpeg)

**向现有文件写入内容：**

**当你关闭文件，然后再次以写入模式打开它时会发生什么？**
