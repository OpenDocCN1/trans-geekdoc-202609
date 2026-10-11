
捕获异常时，下表展示了一些可用于获取异常信息的方法：

![3-5-methods](Images/image00216.jpeg)

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

![3-5-5](Images/image00217.jpeg)

如果你是新手程序员，你可能会觉得为什么要去处理这些异常。在学习和练习的语境下，你或许是对的。但在开发过程中，优秀的程序员应该定义好代码中所有可能的块，以便为最终用户避免不必要且不明确的错误。

希望当你开始从事实时应用开发时，会开始使用异常。

---

# 第 4 章：文件与表单

---

*   [](#part0025.xhtml)
    #### 4.1 文件处理
*   [](#part0026.xhtml)
    #### 4.2 超全局变量
*   [](#part0027.xhtml)
    #### 4.3 表单操作
*   [](#part0028.xhtml)
    #### 4.4 表单验证
*   [](#part0029.xhtml)
    #### 4.5 文件上传

---

### 4.1 文件处理

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

![4-1-filemodes](Images/image00218.jpeg)

创建新文件时，需要使用 `w`。

**练习：**

希望你的新文件 `section4.php` 已创建并打开以供编辑。我们首先创建一个文件用于写入：

```php
$testfile = fopen("test.txt", "w");
```

执行后，你将在 `section4.php` 所在的位置发现一个已创建的文本文件。

创建了一个大小为 0 字节的新文件。该文本文档将没有内容。

![4-1-1](Images/image00219.jpeg)

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

![4-1-2](Images/image00220.jpeg)

**向现有文件写入内容：**

**当你关闭文件，然后再次以写入模式打开它时会发生什么？**

文件 `testfile.txt` 已经包含一些数据，对吧？现在，如果你以写入模式打开一个现有文件，所有现有数据将被清除，我们必须像从头创建一样，从空文件重新开始。

现在，让我们在 `section4.php` 中编写以下代码：

```php
$testfile = fopen("test.txt", "w");
$texttoadd = "New first Line! ";
fwrite($testfile,$texttoadd);
$texttoadd = "New Second Line! ";
fwrite($testfile,$texttoadd);
fclose($testfile);
```

现在执行文件时，内容不会被追加，而是从头覆盖原有内容。

![4-1-3](Images/image00221.jpeg)

那么，要继续写入内容，即在不擦除现有内容的情况下追加内容，该怎么办？使用追加模式：注释掉所有之前的代码，仅保留这 4 行。

```php
$testfile = fopen("test.txt", "a");
$texttoadd = "Third Line to existing 2 lines! ";
fwrite($testfile,$texttoadd);
fclose($testfile);
```

执行 PHP 文件，现在打开 `test.txt`，你将看到以下内容：

![4-1-4](Images/image00222.jpeg)

**你无法刷新一个打开的文本文档！请关闭后重新打开以查看！**

现在我们完成了向文件写入内容。下一个任务是从文件读取内容。为此我们有许多函数。

**读取文件：**

我们可以通过以下方式打开文件以进行读取：

*   使用 `readfile()` 函数
*   使用 `fread()` 函数

我们将逐一介绍：

要执行读取文件的代码，请尝试注释掉所有写入相关的代码，仅使用读取相关的代码，以检查它们如何从现有文本文档中检索内容！

**使用 `readfile()` 函数：**

它读取文件并将其写入输出缓冲区。成功时返回读取的字节数。如果你只想打开一个文件并读取其内容，`readfile()` 函数非常有用。

我们已经创建了一个名为 `test.txt` 的文件。让我们尝试读取同一个文件。

```php
echo readfile("test.txt");
```

![4-1-5](Images/image00223.jpeg)

注释掉 echo 语句，尝试下一个函数。

**使用 `fread()` 函数：**

`fread()` 函数从打开的文件中读取。

参数：

`fread(打开的文件名, 要读取的最大字节数);`
