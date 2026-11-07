
```
<?php
class DatabaseTable {
    public function __construct(private PDO $pdo, private string $table, private string $primaryKey) {
    }

    public function find($field, $value) {
        $query = 'SELECT * FROM `' . $this->table . '` WHERE `' . $field . '` = :value';

        $values = [
            'value' => $value
        ];

        $stmt = $this->pdo->prepare($query);
        $stmt->execute($values);

        return $stmt->fetchAll();
    }

    public function findAll() {
        $stmt = $this->pdo->prepare('SELECT * FROM `' . $this->table . '`');
        $stmt->execute();

        return $result->fetchAll();
    }

    public function total() {
        $stmt = $this->pdo->prepare('SELECT COUNT(*) FROM `' . $this->table . '`');
        $stmt->execute();
        $row = $stmt->fetch();
        return $row[0];
    }

    public function save($record) {
        try {
           if (empty($record[$this->primaryKey]) {
             unset($record[$this->primaryKey]);
           }
           $this->insert($record);
        } catch (PDOException $e) {
           $this->update($record);
        }
    }

    private function update($values) {
        $query = ' UPDATE `' . $this->table .'` SET ';

        foreach ($values as $key => $value) {
            $query .= '`' . $key . '` = :' . $key . ',';
        }

        $query = rtrim($query, ',');

        $query .= ' WHERE `' . $this->primaryKey . '` = :primaryKey';

        // Set the :primaryKey variable
        $values['primaryKey'] = $values['id'];

        $values = $this->processDates($values);

        $stmt = $this->pdo->prepare($query);
        $stmt->execute($values);
    }

    private function insert($values) {
        $query = 'INSERT INTO `' . $this->table . '` (';

        foreach ($values as $key => $value) {
            $query .= '`' . $key . '`,';
        }

        $query = rtrim($query, ',');

        $query .= ') VALUES (';

        foreach ($values as $key => $value) {
            $query .= ':' . $key . ',';
        }

        $query = rtrim($query, ',');

        $query .= ')';

        $values = $this->processDates($values);

        $stmt = $this->pdo->prepare($query);
        $stmt->execute($values);
    }

    public function delete($field, $value) {
        $values = [':value' => $value];

        $stmt = $this->pdo->prepare('DELETE FROM `' . $this->table . '` WHERE `' . $field . '` = :value');

        $stmt->execute($values);
    }

    private function processDates($values) {
        foreach ($values as $key => $value) {
            if ($value instanceof DateTime) {
                $values[$key] = $value->format('Y-m-d');
            }
        }

        return $values;
    }

}
```

让我们将其保存到自己的文件中，`DatabaseTable.php`。请记住在文件顶部放置 `<?php` 标签。

### 从文件中省略闭合的 PHP 标签

每当你创建一个 PHP 文件时，需要记住将 PHP 代码放在 PHP 标签内。然而，闭合标签是可选的，如果文件仅包含 PHP 代码，实际上最好省略它。

这是因为，如果在文件末尾的闭合 PHP 标签 `?>` 之后存在任何空白字符（空行、制表符或空格），它们将被发送到浏览器，而这并不是你想要发生的。相反，最好通过完全省略 `?>` 标签来防止这种情况发生。通过省略闭合的 PHP 标签，空白将被 PHP 在服务器上解释并忽略，而不是作为 HTML 代码的一部分发送到浏览器。

如前所述，使用类的最有用功能之一是，一旦类被编写完成，就可以使用任意多次。每次使用它时，通过创建 *实例*，该实例可以存储类变量的不同值。例如，可以使用 `DatabaseTable` 类与 `joke` 表和 `author` 表进行交互。

因为每个 *实例* 都有自己版本的变量，所以我们可以有一个类的版本，其中 `$table` 设置为 `joke`，另一个版本其中 `$table` 设置为 `author`：

```
$jokesTable = new DatabaseTable($pdo, 'joke', 'id');
$authorsTable = new DatabaseTable($pdo, 'author', 'id');

// Find the joke with the ID 123
$joke = $jokesTable->find('id', 123)[0];

// Find the author with the ID 34
$author = $authorsTable->find('id', 34)[0];
```

因为类变量 `$table` 不同，所以每个实例都会使用不同的表。

当调用 `$authorsTable->find('id', 34)[0]` 时，`$this->table` 等于 `author`，因此运行的查询将是 `SELECT * FROM author …`，而当调用 `$joke = $jokesTable->find('id', 123)[0];` 时，`$this->table` 设置为 `joke`，因此运行的查询是 `SELET * FROM joke …`。

这意味着 `DatabaseTable` 类现在可以通过在构造函数中传入表名来构造实例，从而用于插入、更新或查找数据库中任何表的记录！

## 更新控制器以使用该类

现在我们有了完整的 `DatabaseTable` 类，让我们在控制器中使用它。

首先，删除 `includes/DatabaseFunctions.php`。我们所有的函数现在都存储在 `classes/DatabaseTable.php` 中的类里。

其次，让我们更新 `public/jokes.php` 以使用新的类：

```
<?php

try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../classes/DatabaseTable.php';

    $jokesTable = new DatabaseTable($pdo, 'joke', 'id');
    $authorsTable = new DatabaseTable($pdo, 'author', 'id');

    $result = $jokesTable->findAll();

    $jokes = [];
    foreach ($result as $joke) {
        $author = $authorsTable->find('id', $joke['authorId'])[0];

        $jokes[] = [
            'id' => $joke['id'],
            'joketext' => $joke['joketext'],
            'jokedate' => $joke['jokedate'],
            'name' => $author['name'],
            'email' => $author['email']
        ];
    }

    $title = 'Joke list';

    $totalJokes = $jokesTable->total();

    ob_start();

    include  __DIR__ . '/../templates/jokes.html.php';

    $output = ob_get_clean();
} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

这个控制器更好：它使用 `DatabaseTable` 类，并且不再使用 `INNER JOIN` 查询。现在，每个笑话及其作者都被放入名为 `$jokes` 的数组中。我们将在第 13 章整理它，但在那之前，让我们先看看我们在这里实现了什么。

好处是我们不再需要为每个函数提供表名和 `$pdo` 实例——`total`、`find` 和 `findAll`。请注意，正在创建 `DatabaseTable` 类的两个实例——一个用于 `joke` 表，一个用于 `author` 表。然后可以分别在 `$jokesTable` 变量或 `$authorsTable` 变量上调用这些函数，以在任一表上运行相关查询。

让我们对其他控制器也做同样的事情。

这是更新后的 `deletejoke.php`：

```
<?php
try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../classes/DatabaseTable.php';

    $jokesTable = new DatabaseTable($pdo, 'joke', 'id');

    $jokesTable->delete('id', $_POST['id']);

    header('location: jokes.php');
} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Unable to connect to the database server: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

以及 `editjoke.php`：
