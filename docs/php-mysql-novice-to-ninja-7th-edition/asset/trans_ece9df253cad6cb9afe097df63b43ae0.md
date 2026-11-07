
# PHP 面向对象重构示例
```
$author = $this->authorsTable->find('id', $joke['authorId'])[0];

$jokes[] = [
  'id' => $joke['id'],
  'joketext' => $joke['joketext'],
  'jokedate' => $joke['jokedate'],
  'name' => $author['name'],
  'email' => $author['email']
];
```

错误发生的原因是 `$author` 和 `$joke` 不再是数组。这是一个简单的修复。让我们将从数组中读取的语法改为使用对象语法：

```
$author = $this->authorsTable->find('id', $joke->>authorId])[0];

$jokes[] = [
  'id' => $joke->id,
  'joketext' => $joke->joketext,
  'jokedate' => $joke->jokedate,
  'name' => $author->name,
  'email' => $author->email,
  'id' => $author->id,
];
```

我们还需要更改方法的 `return` 语句，以对 `$author` 变量使用对象语法：

```
$totalJokes = $this->jokesTable->total();

$user = $this->authentication->getUser();

return ['template' => 'jokes.html.php',
  'title' => $title,
  'variables' => [
    'totalJokes' => $totalJokes,
    'jokes' => $jokes,
    'userId' => $user->id ?? null
  ]
];
```

现在让我们也修改 `delete` 方法，从新的对象中读取笑话的 `authorId`。

**示例：[关系-对象](https://github.com/spbooks/phpmysql7/tree/Relationships-Objects)**

```
if ($joke->authorId != $author->id) {
  return;
}
```

让我们回到列表页面并重新审视这里的逻辑。使用对象的更新后方法如下所示：

```
public function list() {
  $result = $this->jokesTable->findAll();

  $jokes = [];
  foreach ($result as $joke) {
    $author = $this->authorsTable->find('id', $joke->authorId);

    $jokes[] = [
      'id' => $joke->id,
      'joketext' => $joke->joketext,
      'jokedate' => $joke->jokedate,
      'name' => $author->name,
      'email' => $author->email,
      'authorId' => $author->id
    ];

  }
```

虽然这个解决方案可行，但现在我们使用面向对象的方法，可以用更优雅的方式解决。目前，每个值从 `author` 或 `joke` 表中存储在 `$jokes` 数组的等效键下。

`$jokes` 数组用于为模板提供访问每个笑话及其作者的功能。

当前流程如下：
* 查询数据库并选择所有笑话
* 遍历每个笑话并：
  * 选择相关的作者
  * 创建一个包含笑话和对应作者所有信息的新数组
* 将此构造的数组传递给模板以显示

对于我们可以使用 OOP 使其变得更简单的事情来说，这是一个非常冗长的过程。

目前，我们可以使用 `$author->getJokes()` 按特定作者获取所有笑话。然而，我们也可以建模反向关系并执行类似以下操作：

```
echo $joke->getAuthor()->name;
```

这将使我们能够获取给定笑话的作者，并且此代码甚至可以从模板中运行。

如果 `$this->jokesTable->findAll();` 调用返回一个笑话 *对象* 数组，每个对象都有自己的 `getAuthor` 方法，那么创建包含两组数据的数组的过程就不再必要了！

首先，让我们在 `Ijdb/Entity/Joke.php` 中创建 `Joke` 实体类：

```
<?php
namespace Ijdb\Entity;

class Joke {
    public int $id;
    public int $authorId;
    public string $jokedate;
    public string $joketext;

    public function __construct(private \Ninja\DatabaseTable $authorsTable) {
    }

    public function getAuthor() {
        return $this->authorsTable->find('id', $this->authorId)[0];
    }
}
```

`Joke` 类的工作方式与 `Author` 类相同：它有一个构造函数，要求提供一个代表相关数据的 `DatabaseTable` 类的实例。在这种情况下，它将接收 `DatabaseTable` 实例，该实例可用于与 `author` 数据库表交互。

`getAuthor` 方法返回当前笑话的作者。如果 `$this->authorId` 为 `5`，它将返回代表 ID 为 `5` 的作者的 `Author` 对象。

## 使用 Joke 类

要使用新的 `Joke` 类，我们需要更新 `Website` 类，以将 `authorsTable` 实例作为构造函数参数提供。构造函数创建两个 `DatabaseTable` 实例，如下所示：

```
public function __construct() {
    $pdo = new \PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

    $this->jokesTable = new \Ninja\DatabaseTable($pdo, 'joke', 'id');
    $this->authorsTable = new \Ninja\DatabaseTable($pdo, 'author', 'id', '\Ijdb\Entity\Author', [$this->jokesTable]);
    $this->authentication = new \Ninja\Authentication($this->authorsTable, 'email', 'password');
}
```

创建 `authorsTable` 实例时，第四个和第五个参数提供了应创建的类的名称（`\Ijdb\Entity\Author`），以及该类的构造函数参数数组（`[$this->jokesTable]`）。

要对 `jokesTable` 实例应用相同的逻辑，我们需要在创建实例时提供类名和构造函数参数：

```
$this->jokesTable = new \Ninja\DatabaseTable($pdo, 'joke', 'id', '\Ijdb\Entity\Joke', [$this->authorsTable]);
$this->authorsTable = new \Ninja\DatabaseTable($pdo, 'author', 'id', '\Ijdb\Entity\Author', [$this->jokesTable]);
```

这将在实例化 `jokesTable` 时将 `authorsTable` 实例传递给 `jokesTable` 实例。

花点时间思考一下这里发生了什么。它提出了一个并不立刻明显的问题。

如果 `authorsTable` 实例的构造函数需要一个 `jokesTable` 实例，而 `jokesTable` 构造函数需要一个 `authorsTable` 实例，我们就遇到了两难的局面：要创建 `jokesTable` 实例，我们需要一个已存在的 `authorsTable` 实例。要创建 `authorsTable` 实例，我们需要一个已存在的 `jokesTable` 实例。两个实例都需要另一个实例先存在！

如果你尝试上面的代码，`PDO` 库会抛出异常：“Cannot call constructor”。虽然这个消息不是很清楚，但这是我刚才指出的问题的缘故。

这种两难局面有时会在面向对象编程中出现。幸运的是，在这种情况下（但并不总是），它可以使用一种称为“引用”的东西相当容易地解决。

## 引用

一种 **引用** 是一种特殊的变量类型——有点像 Windows 中的快捷方式，或 macOS 或 Linux 中的符号链接。计算机上的 **快捷方式** 是一种特殊类型的文件本身不包含任何数据。相反，它指向另一个文件。当你打开快捷方式时，它实际上打开了快捷方式指向的文件。

引用以类似的方式工作。变量不是包含特定值，而是可以包含对另一个变量的 *引用*。当你读取存储引用的变量的值时，它将读取被引用变量的值。

要创建引用，请在要创建引用的变量前加上与号 (`&`)：

```
$originalVariable = 1;
$reference = &$originalVariable;
$originalVariable = 2;
echo $reference;
```

上面的代码将打印 `2`。如果没有 `&`，它将打印 `1`！这是因为变量 `$reference` 包含对 `$originalVariable` 变量的引用。每当读取 `$reference` 的值时，它实际上会去读取变量 `$originalVariable` 在那一刻的值。

这很重要，因为它使我们能够解决前面遇到的两难局面。通过为 `Joke` 和 `Author` 类的构造函数参数提供引用，到 `authorsTable` 和 `jokesTable` 实例需要时，它们将已被创建：
