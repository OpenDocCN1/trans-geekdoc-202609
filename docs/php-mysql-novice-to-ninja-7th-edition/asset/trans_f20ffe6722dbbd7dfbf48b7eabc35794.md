
```
$jokesTable = new DatabaseTable('jokes', $pdo, 'id');
```

这实际上不会导致任何错误。运行这行代码的人不会知道它有问题。可以
使用 `if` 语句来检查每个参数的类型，但 PHP 也提供了一个名为“类型提示”的便捷特性，用更少的代码来解决这个问题。

**类型提示** 允许你指定参数的类型。类型可以是类名，也可以是基本类型之一，例如 string、array 或 integer。

要为参数提供类型提示，请用变量应有的类型作为前缀。对于我们的数据库类，它将是：

```
public function __construct(PDO $pdo, string $table, string $primaryKey) {
```

这告诉 PHP 在提供参数时检查每个参数的类型。如果现在用错误的类型构造对象——例如 `$jokesTable = new DatabaseTable('jokes', $pdo, 'id');` ——PHP 将检查每个参数的 *类型* 是否与 *提示* 匹配。如果不匹配，它将产生错误。此情况下打印的错误是：

```
Uncaught TypeError: Argument 1 passed to DatabaseTable::__construct() must be an instance of PDO, string given
```

这个错误比“在非对象上调用函数 `prepare`”更清晰地解释了问题所在，并且它会阻止脚本的其余部分继续运行。一旦检测到错误，脚本就会停止，以便你修复它。这比在尝试调用对象的方法时才得到一个模糊的错误信息要好得多！

通过像这样在构造函数上使用类型提示，你可以确保类变量被设置为你期望的类型。这样，当在类的某个方法内部运行代码 `$this->pdo->prepare` 时，`$this->pdo` *必须* 被设置为 `$pdo` 的实例并且具有 `prepare` 方法。`$this->pdo` 变量不可能被设置为字符串、数字，甚至不被设置。

这被称为 **防御性编程**，它是一种非常有用的防止错误的方式。通过阻止变量被设置为错误的类型，你可以排除许多潜在错误的可能性。

## 私有变量

`DatabaseTable` 类中的类变量和构造函数现在看起来像这样：

```
class DatabaseTable {
  public $pdo;
  public $table;
  public $primaryKey;

  public function __construct(PDO $pdo, string $table, string $primaryKey) {
    $this->pdo = $pdo;
    $this->table = $table;
    $this->primaryKey = $primaryKey;
  }

  // …
}
```

当创建类的实例时，它 *必须* 传入三个参数，并且这三个参数必须是特定类型（一个 `$pdo` 实例、一个字符串和一个字符串）。

现在如果不提供正确的参数就无法构造该类：

```
$jokesTable = new DatabaseTable($pdo, 'jokes', 'id');
```

任何其他组合——例如 `new DatabaseTable($pdo, 'jokes');`、或 `new DatabaseTable('jokes', $pdo, 'id');`、或 `new DatabaseTable();`——都会显示错误。一旦调用其中一个方法（例如 `$jokesTable->findAll();`），所有类变量都必须已设置为正确类型，这应该会阻止 `$pdo` 变量被设置为真实数据库连接、`PDO` 实例之外的任何内容。

然而，代码仍然存在一个薄弱点。仍然有一种方法可以使类中的 `$pdo` 变量不是 `PDO` 实例。

这是因为变量 `$pdo` 是 *公共* 的。就像公共函数一样，这意味着变量可以从类外部访问，并且以下代码成为可能：

// Correctly create the instance with a database connection
$jokesTable = new DatabaseTable($pdo, 'jokes', 'id');

$jokesTable->pdo = 'a string';

$jokes = $jokesTable->findAll();
```

尽管构造函数在创建对象时确保设置了有效的数据库连接，但上面的代码在构造函数执行和 `findAll` 方法被调用之间覆盖了 `$pdo` 类变量。`$jokesTable` 对象中的 `$pdo` 变量已被设置为“a string”。当 `findAll()` 方法运行时，`$this->pdo->prepare()` 将抛出错误，因为 `$this->pdo` 是一个字符串，而不是具有 `prepare` 方法的对象。

像这样的公共类变量会造成问题，因为它们允许变量从任何地方被覆盖。相反，将类变量设为 *私有* 以防止这些问题是良好的实践：

```
class DatabaseTable {
  private $pdo;
  private $table;
  private $primaryKey;

  public function __construct(PDO $pdo, string $table, string $primaryKey) {
    $this->pdo = $pdo;
    $this->table = $table;
    $this->primaryKey = $primaryKey;
  }

  // …
}
```

当变量为私有时，就像私有函数一样，它们不能从类外部访问（无论是读取还是写入）。

通过结合类型提示、构造函数和私有属性，对该类施加了几个条件：

* 使用 `DatabaseTable` 类创建实例时，如果不传入 `$pdo` 实例是不可能的
* 第一个参数必须是有效的 `PDO` 实例
* 在设置后，无法从类外部更改 `$pdo` 变量

由于这些条件，当调用任何函数时（例如 `findAll()` 或 `save()`），`$pdo`、`$table` 和 `$primaryKey` 变量必须已设置，并且必须是正确类型。当调用 `$this->pdo->prepare()` 时，它不会导致错误，因为除非变量设置正确，否则无法调用 `findAll()`。

这种防御性编程需要多一点思考（例如，什么需要公开，什么需要私有？），但在除最简单项目之外的所有项目中都是值得的！通过消除错误存在的条件，你可以节省以后大量的错误追踪时间。

## 构造函数属性提升

查看带有 `private` 属性的代码：

```
class DatabaseTable {
    private $pdo;
    private $table;
    private $primaryKey;

    public function __construct(PDO $pdo, string $table, string $primaryKey) {
        $this->pdo = $pdo;
        $this->table = $table;
        $this->primaryKey = $primaryKey;
    }
```

这段小代码中有很多重复。每个变量名重复了四次！

直到 PHP 8，此方法是在实现上述好处的唯一方式。然而，PHP 现在支持一项旨在消除所有这些重复的新特性：**构造函数属性提升**。

而不是先声明类变量，然后声明参数，然后将类变量设置为参数，现在可以一次性完成所有这些操作。

下面的代码等同于上面的代码：

```
class DatabaseTable {
    public function __construct(private PDO $pdo, private string $table, private string $primaryKey) {
    }
```

删除了大量代码。变量不再在类中声明，所有以 `$this->` 开头的行也都消失了。

使用这个新的 PHP 特性时，你通过为其加上可见性前缀来将类变量声明为参数。定义为 `private PDO $pdo` 的参数告诉 PHP 从该参数创建同名且私有可见性的类变量。

在功能上，它与手动将类变量分配给对应参数相同，但这个新特性节省了大量输入！

你可能会想知道如何创建一个既不是类变量的构造函数参数。要做到这一点，只需在不使用 `private` 或 `public` 可见性前缀的情况下创建参数，该参数仅在构造函数中可用，不会被提升为类变量。

## 使用 `DatabaseTable` 类

`DatabaseTable` 类的最终版本如下所示：
