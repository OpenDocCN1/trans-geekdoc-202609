
```php
if (!file_exists($path)) {
    throw new FileException("The file '$path' does not exist.");
}

// File read code...
return "Contents of file '$path";
}

// Using the function with exception handling
try {
    echo fileRead("example.txt");
} catch (FileException $e) {
    echo "Error: " . $e->getMessage() . "<br>";
    echo "Details: " . $e->fileInfo();
}
?>
```

这段代码定义了一个名为 FileException 的自定义异常，用于处理与文件操作相关的错误。以下是代码的详细解释：

**定义 FileException 类**：这个类扩展了 PHP 的基本 Exception 类，使其成为一个自定义异常。它有一个 fileInfo() 方法，返回关于异常的其他信息，例如文件路径（$this->getFile()）、引发异常的行数（$this->getLine()）以及关联的错误代码（$this->getCode()）。getFile()、getLine() 和 getCode() 方法是 Exception 类的原生方法。

**FileException 类构造函数：** 类构造函数接受一个可选的 $message 参数，表示抛出 FileException 时要显示的错误消息。默认情况下，此消息定义为 "File error"。然后构造函数调用父类 Exception 类的构造函数，传递错误消息。

**readFile() 函数：** 该函数将要读取的文件路径作为参数。它首先使用 **file_exists()** 函数检查文件是否存在。如果文件不存在，则抛出一个 FileException，并附带特定的错误消息，指示文件不存在。否则，它会模拟读取文件，并返回一条指示文件内容的消息。

使用带有异常处理的函数：代码使用 fileRead() 函数来读取名为 "example.txt" 的文件的内容。它被包裹在 **try-catch** 块中，以捕获任何 FileException。如果抛出异常，则向用户显示错误消息，并附带由异常的 **fileInfo()** 方法提供的更多详细信息。

总结来说，这段代码说明了如何创建和使用自定义异常来处理特定于文件操作的错误，同时提供其他信息以方便调试和故障排除。

此时，如果运行 fileRead.php 文件，将得到类似于以下的结果：

错误：文件 'example.txt' 不存在。
详情：文件路径有问题：/Applications/XAMPP/xamppfiles/htdocs/phppoo/readfile.php
错误行：23
错误代码：0

但是，如果在项目根目录下创建一个名为 example.txt 的文件并运行 fileRead.php 文件，将得到以下结果：

### 文件 'example.txt' 的内容

## PHP 中的 PDOException

数据库操作错误是 Web 开发中常见的情况。PHP 提供了一个特定的异常类 PDOException 来处理这些情况。

PDOException 是一个 PHP 特有的异常类，当使用 PDO（PHP 数据对象）扩展访问数据库时发生错误时会触发。

PDOException 在数据库错误处理中起着至关重要的作用，使开发人员能够高效地捕获、处理和管理 SQL 查询执行期间发生的错误。

### 使用 PDOException

捕获 PDOException：PDO 错误会自动转换为 PDOException 实例。要捕获 PDOException，可以在执行 SQL 查询的代码周围使用 try-catch 块。

**错误处理**：捕获后，PDOException 会提供有关错误的详细信息，例如错误消息、SQLSTATE 错误代码和数据库特定的错误代码。

**错误处理**：开发人员可以使用 PDOException 提供的信息来决定如何处理错误，例如显示用户友好的错误消息或记录错误以便调试。

### PDOException 示例

让我们开发一段简单的代码来连接数据库：

```php
<?php
try {
    // Attempt to connect.
    $db = new PDO('mysql:host=localhost;dbname=Users','root','');
    echo 'Connection successful!'; // If the connection is successful, this message will be displayed
}
catch (PDOException $e) // We catch PDOExceptions.
{
    echo 'Connection failed.<br />';
    echo $e->getMessage(); // The error number and message are displayed.
}
```

这段代码尝试使用 PDO（PHP 数据对象）连接到 MySQL 数据库。以下是详细解释：

try 块中的第一行尝试创建 PDO 类的新实例以建立到数据库的连接。传递的参数如下：

'mysql:host=localhost;dbname=Users'：这指定了要连接的数据库类型（MySQL）、主机（localhost）和数据库名称（Users）。

'root'：这是数据库用户名。

密码为空，但在生产环境中应确保其安全。

如果连接成功，屏幕上将显示消息“连接成功！”。

如果在连接尝试期间引发 PDOException（例如，由于配置或连接问题），将执行 catch 块。在此 catch 块中，将显示消息“连接失败”，随后是从异常中检索到的特定错误消息，即通过对 $e 异常对象调用 getMessage() 方法获得的。

简而言之，这段代码尝试连接到 MySQL 数据库，如果成功，则显示成功消息。如果不成功，它会在连接过程中出现问题时捕获并显示错误详细信息。

此时，执行此代码将产生类似于以下结果的错误：

![](img/caba2aa22f5409ba73dea47176330677_553_0.png)

此错误消息表明连接数据库的尝试已失败。以下是详细解释：

“连接失败”。这是我们在 catch 块中定义的消息，用于指示连接尝试期间发生了错误。

“SQLSTATE[HY000] [1049] Unknown database 'Users'”：这是数据库返回的特定错误消息。它由三部分组成：

“SQLSTATE[HY000]”：这是一个标准 SQL 状态代码，指示错误类型。在此例中，“[HY000]”表示一般错误。

“[1049]”：这是一个特定的错误代码，用于标识错误类型。在此例中，代码 1049 表示“未知数据库”，指示连接中指定的数据库不存在或无法访问。

“Unknown database 'Users'”：这是对错误的额外描述，指定名为“Users”的数据库未知或无法访问。

简而言之，此错误消息表明连接中指定的数据库存在问题，更具体地说，“Users”数据库不存在或无法访问。

## 结论

异常处理是编程中必不可少的实践，能够高效且优雅地处理错误。本章帮助我们理解了异常在软件设计中的重要性，强调了可能发生的不同类型的错误，并介绍了处理这些错误的方法。

我们探讨了 PHP 中异常的语法和用法，强调了使用 try-catch 块来捕获和处理异常。我们还研究了自定义异常的创建和使用，为处理特定于我们应用程序的错误提供了一种灵活且模块化的方式。

最后，我们讨论了异常在实际场景中的应用，例如使用 PDOException 进行数据库错误处理，并提供具体示例来说明其用法。

通过掌握异常处理，开发人员可以提高应用程序的健壮性、可靠性和质量，确保适当的错误处理，并便于调试和维护代码的过程。

## 第 19 章

### 命名空间

在进行 Web 开发项目时，高效的文件和资源管理对于保持代码井井有条和避免冲突至关重要。想象一下你的计算机桌面，同一位置不能有两个同名文件。项目目录也是如此。如果你参与过大型项目，你就会知道，要保证文件、类、属性或方法名称的唯一性可能很困难，尤其是在团队协作时。

虽然在小型项目中，通过清晰了解应用程序可以避免命名冲突，但在涉及数百或数千个文件及数千行代码的大型项目中，这很快就会成为一项挑战。代码模块化变得至关重要，它允许每个团队成员在不冒互相干扰风险的情况下，在项目的不同部分进行工作。

命名空间正是为此而设。在 PHP 中使用命名空间，你可以逻辑地组织代码，避免名称冲突，并使你的应用程序更易于维护和扩展。在本章中，我们将详细探讨 PHP 中命名空间的概念、其实际用途，以及它们在现代 Web 应用程序开发中提供的优势。
