
你将看到“Award Winning Movies”作为 `<H1>` 标题显示。在这里，我们调用了在父类中定义的 `displayHeading()` 方法。该方法是子类继承的公共方法。因此，我们可以使用 `AwardWinningMovie` 对象访问它。

接下来，让我们看看如果在子类内部编写一个 `displayHeading()` 方法的新版本会发生什么。为了实现这一点，在 `AwardWinningMovie` 类中、`recommend()` 方法之后、类结束大括号之前添加以下方法：

```php
public function displayHeading($tag){
    $baseMsg = parent::displayHeading($tag); 
    return $baseMsg.$this->award; 
}
```

在这里，我们声明了一个与父类方法相同名称（`displayHeading`）和参数列表（`$tag`）的方法。当这种情况发生时，我们说子类方法重写了父类方法。在子类内部，我们使用 `parent::displayHeading($tag)` 来调用父类方法。

最后，我们将 `$baseMsg` 与 `$this->award` 拼接。如果你再次加载 `chap10.php`，你只会看到“Award Winning Movies”作为 `<H1>` 标题显示。

`(dbname=pawszone )`。第二个参数是用户名 (`"pz_admin"`)，第三个是密码 (`"ABCD"`）。创建此对象后，我们将其赋值给名为 `$pdo` 的变量，并在下一行使用 `$pdo` 来调用 `setAttribute()` 方法。`setAttribute()` 方法允许我们设置 `PDO` 对象的属性。在这里，我们正尝试设置错误模式。默认情况下，在成功连接后，`PDO` 不会通知我们随后发生的任何错误。例如，如果我们尝试从一个不存在的表中查询数据，`PDO` 不会我们我们这样的表。相反，我们将得到一个没有结果的页面。如果我们正试图找出错误出在哪里，这会非常令人沮丧。为了让 `PDO` 通知我们任何问题，我们需要使用 `setAttribute()` 方法来配置错误模式。为了做到这一点，我们向该方法传递两个预定义的常量。第一个常量告诉 `PDO` 我们想要设置的属性，第二个常量告诉 `PDO` 我们想要设置的值。您可以在此处找到所有预定义的 `PDO` 常量的列表：

https://www.php.net/manual/en/pdo.constants.php

在我们的示例中，我们想将错误模式属性 `(PDO::ATTR_ERRMODE)` 设置为 `PDO::ERRMODE_EXCEPTION`。在这种模式下，当发生错误时，`PDO` 会抛出一个异常。我们将在下一章学习更多关于异常的知识。现在，只需可以使用此异常中的信息找出出了什么问题即可。就是！这就是连接数据库所需的所有操作。连接到数据库后，我们就可以准备好向它发送查询了。

## 11.3 SQL 注入

MySQL 主要有两种查询类型——从数据库返回数据的（例如 `SELECT`）和不返回数据的（例如 `CREATE`、`INSERT`、`UPDATE` 和 `DELETE`）。发送不返回数据查询最简单的方法是使用 `exec()` 方法，而发送返回数据查询简单的方法是使用 `query()` 方法。然而，这两种方法都让我们面临一种被称为 SQL 注入的攻击风险。还记得我们在第 8.1.6 节中讨论过跨站脚本吗？SQL 注入与其相似，黑客可以向我们的网站输入数据并利用它来黑入我们的数据库。假设我们有一个名为“ownerName”的文本字段，并且想从数据库中名为“pets”的表中选择行，可以使用下面的代码：

```php
$owner = $_POST['ownerName'];
$sql = "SELECT * FROM pets WHERE owner = '$owner'";
$stmt = $pdo->query($sql);
```

如果上面的代码目前还没有意义，请担心。我们稍后会讨论查询数据库的更好方法。现在，只需知道在上面的代码中，我们将用户输入 `$_POST['ownerName']` 用于我们的 SQL `SELECT` 语句，并使用 `query()` 方法执行该语句。如果我们的用户在“ownerName”文本字段中输入 `Jamie`，`SELECT` 语句变为 `SELECT * FROM pets WHERE owner = 'Jamie'`，一切都按预期运行。

然而，假设用户在文本字段中输入 `Jamie' OR owner != 'Jamie`，则 `SELECT` 语句变为 `SELECT * FROM pets WHERE owner = 'Jamie' OR owner != 'Jamie'`。当我们使用 `query()` 方法执行此语句时，PHP 将用户输入中的单词“OR”解释为 SQL 运算符 `OR`。因此，它返回了“pets”表中的所有行，因为 `owner = 'Jamie' OR owner != 'Jamie'` 涵盖了“owner”列的所有可能值。这绝对不是我们想要的。

与其使用 `query()` 或 `exec()` 方法执行 SQL 语句，更好的方法是使用准备语句。

## 11.4 准备语句

使用准备语句涉及几个步骤：

1. 使用占位符创建 SQL 语句

2. 准备语句

3. 将变量或值绑定到占位符

4. 执行语句

5. 如果需要获取返回的任何数据

### 步骤 1：使用占位符创建 SQL 语句

在使用准备语句时，我们需要使用占位符来替换 SQL 语句中包含用户输入的任何变量。这些占位符可以是命名的也可以是非命名的。未命占位符用问号 `?` 表示。例如，如果我们想使用用户输入的名为“owner”和“petname”的两个列从“pets”表中查询信息，可以使用下面的 SQL 语句：

```php
$sqlUnnamed = "SELECT * FROM pets WHERE owner = ? AND petname = ?";
```

在这里，我们使用问号 (`?`) 替换 SQL 语句中的用户输入，并将该语句赋值给名为 `$sqlUnnamed` 的变量。或者，我们可以像下面所示使用命名的占位符：

```php
$sqlNamed = "SELECT * FROM pets WHERE owner = :owner AND petname = :pname";
```

在这里，我们使用 `:owner` 和 `:pname` 替换用户输入，并将语句赋值给名为 `$sqlNamed` 的变量。

### 步骤 2：准备语句

创建语句后，我们需要对其进行准备。准备语句意味着提前将语句发送到数据库服务器，让服务器有机会分析、编译并优化其执行计划。实际执行并未发生在这一步。为了准备语句，我们使用 `prepare()` 方法。这是 `PDO` 类中的内置方法，返回一个 `PDOStatement` 对象。假设我们有一个名为 `$pdo` 的 `PDO` 对象，为了准备 `$sqlUnnamed` 语句，我们写：

```php
$sqlUnnamed = $pdo->prepare($sqlUnnamed);
```

在这里，我们使用 `$pdo` 调用 `prepare()` 方法并将返回的对象赋值给变量 `$sqlUnnamed`。为了准备 `$sqlNamed` 语句，我们写：

```php
$sqlNamed = $pdo->prepare($sqlNamed);
```

在这里，我们将返回的对象赋值给变量 `$sqlNamed`。准备好语句后，我们将不再使用 `$pdo` 对象。相反，我们将在后续步骤中使用 `PDOStatement` 对象（即 `$sqlUnnamed` 和 `$sqlNamed`）。

### 步骤 3：将值绑定到占位符

在步骤 3 中，我们需要将值绑定到 SQL 语句中的占位符上。这告诉数据库服务器在执行语句时用哪些值替换占位符。我们可以使用 `bindValue()` 或 `bindParam()` 方法将值绑定到占位符。两种方法都很相似，但 `bindValue()` 往往更通用。在随后的示例中使用我们将 `bindValue()` 方法。

要将值绑定到未命名占位符，我们通常向 `bindValue()` 方法提供两个信息——占位符的位置和要绑定的值。占位符的位置从 1 开始。记得我们有一个定义并准备好的名为 `$sqlUnnamed` 的 `SELECT` 语句：

```php
$sqlUnnamed = "SELECT * FROM pets WHERE owner = ? AND petname = ?";
$sqlUnnamed = $pdo->prepare($sqlUnnamed);
```

假设我们要将名为 `$myPet` 的用户输入绑定到 `$sqlUnnamed` 中的第二个问号，我们可以这样做：

```php
$sqlUnnamed->bindValue(2, $myPet);
```

在这里，我们使用 `$sqlUnnamed` 调用 `bindValue()` 方法。第一个参数 (`2`) 表示我们正将值绑定到第二个占位符（即“petname”列的占位符），而第二个参数 (`$myPet`) 表示要绑定的值。要将值绑定到命名的占位符，我们用占位符的名字替换第一个参数。例如，如果我们想将 `$myPet` 绑定到 `$sqlNamed` 中的 `:pname` 占位符，操作如下：

```php
$sqlNamed->bindValue(':pname', $myPet);
```

第一个参数 (`':pname'`) 表示我们正将值绑定到 `:pname` 占位符，而第二个参数 (`$myPet`) 表示要绑定的值。

此时，你们中的一些可能会怀疑 `$myPet`（存储用户输入）是否让我们面临 SQL 注入攻击的风险。答案是否。这是因为 `PDO` 知道我们正在发送占位符的值；因此，它不会将存储在 `$myPet` 中的字符串的任何部分解释为 SQL 代码。例如，即使 `$myPet` 存储了字符串

'Max' OR petname != 'Max the word' 这里的 “OR” 单词、引号以及 `!=` 运算符不会被解析为 SQL 代码。相反，`PDO` 会将整个字符串视为“petname”列的值，并简单地搜索具有该奇怪名字的宠物。明白了吗？

### 第 4 步：执行语句

在将值绑定到占位符之后，我们需要使用 `PDOStatement` 对象来调用 `execute()` 方法。要执行 `$preparedUnnamed`，我们这样写：

```php
$preparedUnnamed->execute();
```

要执行 `$preparedNamed`，我们这样写：

```php
$preparedNamed->execute();
```

### 第 5 步：获取返回的数据（如果有）

执行语句后，我们可以使用 `fetch()` 或 `fetchAll()` 方法来获取任何返回数据（如果该语句是 `SELECT` 语句）。`fetch()` 方法逐行获取行，而 `fetchAll()` 方法则一次性获取所有行。两种方法在失败时都会返回 `false`。

在使用其中一种方法时，我们可以指定在获取行时希望方法使用的样式。常用的样式包括 `FETCH_ASSOC` 和 `FETCH_NUM` 样式。`FETCH_ASSOC` 样式将行作为关联数组（使用表中的列名作为键），而 `FETCH_NUM` 样式将行作为索引数组获取（基于 `SELECT` 语句返回的列顺序）。

例如，为了获取 `$sqlUnnamed` 的行，我们可以使用以下 `while` 循环：

```php
while($row = $preparedUnnamed->fetch(PDO::FETCH_NUM)){  
    echo 'Pet = '.$row[1].'<BR>';  
    echo '<BR>Owner = '.$row[0].'<BR>';  
} 
```

该循环使用赋值语句 `$row = $preparedUnnamed->fetch(PDO::FETCH_NUM)` 作为循环条件。这在处理 `PDO fetch()` 方法时是允许的，也是一种常用方法。赋值语句使用 `$preparedUnnamed`（即 `$sqlUnnamed` 的预处理语句）调用 `fetch()` 方法，并指定获取样式为 `PDO::FETCH_NUM`。接下来，它将返回的结果赋值给名为 `$row` 的变量。该变量控制 `while` 循环的何时结束。只要 `$row` 不是 `false`，循环就会继续。

在 `while` 循环内部，我们使用两个 `echo` 语句来显示 `fetch()` 方法返回的数组值。`row[0]` 为我们提供了 `$sqlUnnamed` 中的第一列（即“owner”列），而 `row[1]` 提供了第二列（即“petname”列）。当我们到达结果集的末尾且 `fetch()` 方法无法再获取更多行时，它会返回 `false`。此时 `$row` 变为 `false`，`while` 循环随之停止。

除了使用 `FETCH_NUM` 样式外，我们还可以使用 `FETCH_ASSOC` 样式来获取数据。方法如下：

```php
while($row = $preparedUnnamed->fetch(PDO::FETCH_ASSOC)) { 
    echo 'Pet = '.$row['petname'].'<BR>';  
    echo '<BR>Owner = '.$row['owner'].'<BR>'; 
} 
```

这两个循环给出的输出是相同的；我们稍后会有机会运行它们并查看结果。除了使用 `fetch()` 方法外，我们还可以使用 `fetchAll()` 方法一次性从数据库中获取所有行。我们将在书末的项目中这样做。

就是这样。我们已经涵盖了预处理语句的精要。

### 1.5 整合

要做到这一点，我们首先一个数据库和用户。首先，确保你已经启动了 XAMP 和 MySQL 服务器。如果你在启动 MySQL 服务器时遇到问题，可能是由于端口冲突。我们现在准备好连接到你刚刚创建的数据库了。

在上面的代码中，我们首先在 A 部分中连接到“pawszone”数据库。接下来，在 B 部分中，我们使用 SQL `CREATE` 语句在数据库中创建一个名为“pets”的表。由于此 SQL 语句不包含任何占位符，因此我们不需要调用 `bindValue()` 方法。相反，我们只需要简单准备语句并执行它即可。在 C 部分中，我们有一个用于向“pets”表插入数据的 `INSERT` 语句。我们首先使用 `prepare()` 方法来准备该语句。虽然我们稍后将使用 `for` 循环执行四次 `INSERT` 语句，但请注意，我们只需要准备一次语句。这是使用预处理语句的另一个优势，因为它可以带来更快的执行，特别是当查询复杂或需要运行多次时。准备好语句后，我们声明了三个数组 `$owner`、`$pname` 和 `$breed`，并将要插入的数据赋值给这些数组。接下来，我们使用 `for` 循环遍历这些数组。循环每次运行时，我们都会将每个数组中的一个值绑定到相关的占位符上。绑定数据后，我们调用 `execute()` 方法执行 `INSERT` 语句。在 C 部分插入数据后，我们在 D 部分更新了一行数据（owner = “Jamie” 且 petname = “Max”），并在 E 部分删除了另一个（owner = “Ted” 且 petname = “Angel”）。这两个部分应该是显而易见的。在继续之前，请仔细阅读并完全理解上面的代码。一旦你清楚了预处理语句的工作原理，就在浏览器中加载页面 `sql_select.php` 来运行该代码。接下来，访问 `http://localhost/phpmyadmin/` 并选择左侧的“pawszone”数据库。你应该能在右侧看到“pets”表。点击“浏览”，你会得到下面的表格：![](img/image_rsrc1J7.jpg)如你所见，“pets”表已成功创建并已添加数据。明白了吗？接下来，让我们学习如何使用 PHP 从此表中选取数据并显示在我们的网页上。为此，请创建一个名为 `sql_select.php` 的新文件并添加以下代码。

```php
<?php  

//Section A - 连接到数据库
$pdo = new PDO("mysql:host=localhost;dbname=pawszone", "pz_admin", "ABCD");  

$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION); //Section B - 从 pets 中选择所有行  

$sql = "SELECT petname, owner FROM pets";  

$stmt = $pdo->prepare($sql);  

$stmt->execute();  

while ($row = $stmt->fetch(PDO::FETCH_ASSOC)){  

echo '<BR>Owner = '.$row['owner'].'<BR>';  

echo 'Pet Name = '.$row['petname'].'<BR>';  

}  

$stmt->execute(); while ($row = $stmt->fetch(PDO::FETCH_NUM)){  

echo '<BR>Owner = '.$row[1].'<BR>';  

echo 'Pet Name = '.$row[0].'<BR>'; } 
```
