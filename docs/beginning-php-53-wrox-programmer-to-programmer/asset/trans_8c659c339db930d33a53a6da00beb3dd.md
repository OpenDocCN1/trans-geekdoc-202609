

## 第 20 章：编写高质量代码

- 在函数调用中何时使用空格：本书倾向于在函数参数周围使用空格，但在函数名和左括号之间不留空格：

```
include("animal_functions.php");
```

- 如何格式化流程结构：本书在条件判断括号周围和内部都使用空格：

```
if ($queryType == "animal") {
```

- 如何命名标识符：一种常用的命名技术是使用下划线分隔标识符内的单词（variable_name 或 CONSTANT_NAME）；由于 C 语言编程中使用了这种惯例，这有时被称为“C 风格”。另一种常用技术是将标识符中的每个单词的首字母大写（可选包括第一个字母）（VariableName 和 variableName）；这些约定通常被称为大驼峰命名（upper camel case）和小驼峰命名（lower camel case）；请遵循本书的规定：

- 类名使用大写（MyClass）
- 函数、方法和变量名使用小写（myMethod() 和 $variable）
- 常量名使用大写字母加下划线（MY_CONSTANT）
- 预定义字面值使用小写（true, false, null）

你可以发明自己的编码标准（如果有帮助，可以正式写出来）或采用现有的标准。常见的标准包括：

- PEAR 编码标准：http://pear.php.net/manual/en/standards.php
- Java 代码规范：http://java.sun.com/docs/codeconv/
- GNU 编码标准：http://www.gnu.org/prep/standards/

使用现成标准还是创建自己的标准并不重要。重要的是，一旦你采纳了某种标准，就应该将其一致地应用于你所有的 PHP 代码中。

## 为代码编写文档

为代码编写良好的文档需要自律，但它是构建应用程序的一个重要方面。虽然没有文档的代码在编写时完全可以理解，但代码在六个月后你再次回看时，往往会变得难以理解。更此外，如果其他开发者需要处理你没有文档的代码，他们将很难弄清楚这些代码的意图。

## 第三部分：在中使用 PHP

记录 PHP 代码的主要方法是在代码中添加注释。到此时你可能已经知道 PHP 中可以创建两种注释：

- 单行注释：以两个斜杠（//）或井号（#）开头。
- 多行注释：以 /* 开头，以 */ 结束。

## 编写良好的注释

编写注释非常简单，但如何编写良好的注释呢？首先，注释需要解释一段代码的作用（或意图）。然而，不要陈述显而易见的事。以下是一个糟糕注释的示例：

```
for ($i=0; $i < count($users); $i++) { // 从 0 循环到 count($users) -
$users[$i]->insert(); //为用户调用 insert() 方法
}
```

这些注释所只是重复了阅读代码本身就能看出显而易见的内容；它们没有为代码增加额外的含义。下面的注释会有用得多：

```
// 将所有用户插入到数据库
for ($i=0; $i < count($users); $i++) {
$users[$i]->insert();
}
```

这让读者能够从更高层面的视角理解代码正尝试做什么。

改进注释的另一种方法是提高可读性的格式化。在注释开始之前（可能可能在注释之后）添加一个空行；在使用行内注释时，在 // 后添加一个空格；并将跨行的行内注释对齐。考虑以下格式化糟糕的注释：

```
//Retrieve all users
$users = User::getAll();
/*
Add the users to the database.
Each user's modification time is updated
before the user is added.
*/
for ($i=0; $i < count($users); $i++) {
$users[$i]->updateModDate(); //Set the modification time
$users[$i]->insert(); //Insert the user
}
```

你可以看出，很难判断脚本哪些部分是注释，哪些部分是代码。这是一个改进后的版本：

```
// 获取所有用户
$users = User::getAll();

/*
 将所有用户添加到数据库。
 在添加用户之前更新每个用户的修改时间。
*/
for ( $i=0; $i < count($ users ); $i++ ) {
$users[$i]->updateModification(); // 修改时间
$users[$i]->insert();
}
```

通过在注释之间添加水平和垂直空间并对齐两个行内注释，代码变得更具读性。

另一种良好的注释策略是在编写代码的同时编写注释，而不是事后补写。事实上，在代码还停留在脑海中的这个阶段编写注释更容易。此外，因为注释描述了代码的意图，注释会鼓励你思考如何以及为什么要编写那段代码。事实上，为了增加一倍自律性，尝试在编写代码之前先写注释！

通过添加大量有帮助的注释使代码更易于读，你可以通过使用有意义的变量、函数和方法名来改进代码。以下代码足够清晰，不需要任何注释：

```
$jim = new User();
$jim->setFirstName("Jim");
$jim->setLastName("Smith");
$jim->addToDatabase();
```

## 使用 phpDocumentor 生成外部文档

虽然代码注释很有用，但如果文档与代码文件分离，开发者可能更容易获得应用程序的更高层面的概览。

phpDocumentor 是一个 PEAR 包，用于更新外部文档文件的生成。它读取你的 PHP 脚本文件，并使用代码中的注释生成文档。通过以特殊方式格式化注释，你可以为 phpDocumentor 提供关于代码的额外信息，例如每个变量的作用范围和数据类型，以及变量、函数和类之间的关系。

你可以像安装其他 PEAR 包一样安装 phpDocument（安装 PEAR 包的更多信息请参见第 15 own 章）：

```
$ php install --aldeps phpDocument
downloading phpDocument-1.4.2.tgz
Starting to download PhpDocument-1.4.2.tgz (2,421,028 bytes)
-------------------------------------------------------
... done: 2,421,028 bytes
downloading XML_Beautifier-1.2.0.tgz
Starting to download XML_Beautifier-1.2.0.tgz (12,948 bytes)
-------------------------------------------------------
... done: 12,948 bytes
downloading XML_Parser-1.3.2.tgz
Starting to download XML_Parser-1.3.2.tgz (16,260 bytes)
-------------------------------------------------------
... done: 16,260 bytes
downloading XML_Util-1.2.1.tgz
Starting to download XML_Util-1.2.1.tgz (17,729 bytes)
-------------------------------------------------------
... done: 17,729 bytes
install ok: channel://pear.php.net/phpDocument-1.4.2
install ok: channel://pear.php.net/XML_Parser-1.3.2
install ok: channel://pear.php.net/XML_Util-1.2.1
install ok: channel://pear.php.net/XML_Beautifier-1.2.0
$
```

你通过命令行使用 `phpdoc` 命令来运行 phpDocument，如下：

```
$ phpdoc -o html:earthli -f /home/joe/htdocs/myscript.php -t /home/docs
```

此命令告诉 phpDocument 执行：

- 以 HTML 格式输出生成
- 使用 "frames" 转换器
- 使用 "earthli" 模板
- 读取 PHP 脚本 /home/joe/htdocs/myscript.php 中的注释
- 将生成的文档保存到 /home/docs

phpdoc 支持广泛的不同选项。例如，你可以使用 -d 指定要读取的目录，而不是单个文件。你还可以以 PDF 或 XML 格式输出文档。完整的选项列表请访问 http://manual.phpdoc.org/HTMLSmartConverter/PHP/phpDocument/tutorial_phpDocument.howto.pkg#command-line。

如果你愿意，可以使用 phpDocument 的 Web 界面，而不是命令行界面。有关安装和使用 Web 界面的更多信息，请参见 http://manual.phpdoc.org/HTMLSmartConverter/PHP/phpDocument/tutorial_phpDocument.howto.pkg.html。

