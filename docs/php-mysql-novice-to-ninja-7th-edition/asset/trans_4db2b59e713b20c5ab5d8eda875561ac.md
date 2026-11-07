
The `$author->id = 123;` 行设置了我们所表示的作者的 ID。通常，这将来自数据库中的 `id` 列，但在这个简化示例中我手动设置了它。

设置 ID 后，当 `$jokes = $author->getJokes();` 行运行时，它会在 `Author` 实体类中执行 `getJokes()` 方法，获取与实例上指定的 ID 关联的所有笑话。

除了读取笑话列表之外，让我们使用面向对象的方法添加添加笑话的功能。关系将在幕后创建。使用该类的程序员将添加笑话，但无需手动指定作者的 ID。

实现后，添加笑话将像这样进行：

```
$joke = [
  'jokeText' => 'Why did the programmer quit his job? He didn\'t get arrays',
  'jokeDate' => '2021-11-05'
];

$author->addJoke($joke);
```

请注意，`$joke` 数组不包含谁发布了该笑话的任何信息。笑话是通过在 `Author` 实例上调用名为 `addJoke` 的方法来关联的。然后该方法将创建笑话与作者之间的关联，然后将笑话添加到数据库中。

让我们将此新方法添加到 `Author` 实体类中。它将接受笑话作为参数，然后设置 `authorId` 属性，最后将笑话插入数据库：

```
public function addJoke(array $joke) {
  // set the `authorId` in the new joke to the id stored in this instance
  $joke['authorId'] = $this->id;

  $this->jokesTable->save($joke);
}
```

让我们在 `Joke` 控制器的 `editSubmit()` 方法中使用新类，通过 `$author->addJoke($joke)` 保存笑话。

示例：[关系-作者](https://github.com/spbooks/phpmysql7/tree/Relationships-Author)

```
public function editSubmit() {
  // Get the currently logged in user as the $author to associate the joke with
  $author = $this->authentication->getUser();

  // Create an `Author` entity instance
  $authorObject = new \Ijdb\Entity\Author($this->jokesTable);

  // Copy the values from the `$author` array into the corresponding properties in the entity object
  $authorObject->id = $author['id'];
  $authorObject->name = $author['name'];
  $authorObject->email = $author['email'];
  $authorObject->password = $author['password'];

  // Read the form submission and set the date
  $joke = $_POST['joke'];
  $joke['jokedate'] = new \DateTime();

  // Save the joke using the new addJoke method
  $authorObject->addJoke($joke);

  header('location: /joke/list');
}
```

由于数据库以数组形式返回数据，我已将 `getUser()` 返回的 `$author` 数组中的数据复制到新创建的 `Author` 类的实例中。

`$author` 数组和 `$authorObject` 对象都将表示同一位作者。唯一的区别是一个是对象，另一个是数组。

该方法中的大部分代码行只是简单地将数据从数组复制到对象。这显然效率低下，如果我们可以在 `editSubmit()` 方法之外构造 `Author` 对象，并让 `getUser()` 返回构造好的对象，则可以避免此问题，如下所示：

```
public function editSubmit() {
  $authorObject = $this->authentication->getUser();

  $joke = $_POST['joke'];
  $joke['jokedate'] = new \DateTime();

  $authorObject->addJoke($joke);

  header('location: /joke/list');
}
```

### 从 DatabaseTable 类使用实体类

你可能考虑将复制数组到对象的逻辑移到 `getUser()` 方法中，但我们可以更进一步。任何创建的作者或笑话作为对象都很有用，因此我们可以修改 `DatabaseTable` 类中的 `find()` 方法，使其始终返回对象。

当前 `find()` 方法如下所示：

```
public function find($column, $value) {
    $query = 'SELECT * FROM `' . $this->table . '` WHERE `' . $column . '` = :value';

    $values = [
        'value' => $value
    ];

    $stmt = $this->pdo->prepare($query);
    $stmt->execute($values);

    return $stmt->fetchAll();
}
```

这里，`$stmt->fetchAll()` 返回查询返回的记录数组。数组中的每个条目本身就是一个数组，表示表中的一行。例如，获取作者时，此数组包含键 `id`、`email`、`name` 和 `password`。

我们可以在这里添加一些代码来创建相关的 `Author` 实例，然后将数组中的所有值复制到对象中（如上所述）。然而，PDO 库的开发者已经领先一步，`fetchAll()` 方法可以接受一些参数来配置它返回一个数组，其中每个记录由对象而不是数组表示。

要告诉 `fetchAll()` 方法返回 `Author` 实例，我们可以使用以下参数：

```
return $stmt->fetchAll(\PDO::FETCH_CLASS | \PDO::FETCH_PROPS_LATE, '\Ijdb\Entity\Author', [$jokesTable]);
```

第一个参数 `\PDO::FETCH_CLASS | \PDO::FETCH_PROPS_LATE` 告诉 PDO 创建类的实例而不是数组。第二个参数，在本例中为 `'\Ijdb\Entity\Author'`，是它应创建实例的类的名称（带命名空间且用引号括起来）。最后一个参数是创建第二个参数中命名类的实例所需的构造函数参数列表。

最后一个参数看起来有点奇怪，因为它是一个变量——`$jokesTable`——在方括号内。这段代码创建了一个数组，其中索引零为 `$jokesTable`，等同于以下内容：

```
$array = [
  0 => $jokesTable
];

return $stmt->fetchAll(\PDO::FETCH_CLASS | \PDO::FETCH_PROPS_LATE, '\Ijdb\Entity\Author', $array);
```

第三个参数必须是数组，因为第二个参数中列出的类在其构造函数中可能需要多个参数。

由于 `Author` 类需要 `$jokesTable` 作为构造函数参数，因此在调用 `fetchAll()` 时也必须提供它。然而，我们不能修改 `DatabaseTable` 类以使用上面的 `return` 行——首先，因为它无法访问 `$jokesTable` 变量，其次，因为我们使用 `DatabaseTable` 类与不同的数据库表交互。当调用 `find()` 方法时，它可能在 `authorsTable` 实例、`jokesTable` 实例上，或者代表其他数据库表的 `DatabaseTable` 类实例上。

我们希望为每个表使用不同的实体类，而且它们几乎肯定不会有相同的构造函数参数。

而不是硬编码类名和构造函数参数，我们可以修改 `DatabaseTable` 类的构造函数，使其接受两个可选参数——要创建的类名以及要提供给它的任何参数：

```
class DatabaseTable {

  public function __construct(private \PDO $pdo, private string $table, private string $primaryKey, private string $className = '\stdClass', private array $constructorArgs = []) {

  }
```

每次创建 `DatabaseTable` 的实例时，都可以可选地提供对应实体类的类名和该实体的构造函数参数数组。然后这些值将在 `find()` 和 `findAll()` 方法中使用，以返回对象而不是数组。

请注意，我为每个新参数都提供了默认值。`stdClass` 类是 PHP 内置的空类，可用于简单的数据存储。

通过将其指定为默认值，如果未指定类名，它将使用此通用内置类。这带来的好处是我们不需要为每个数据库表创建唯一的实体类，而只需要为我们想要添加方法的表创建！

现在可以更改 `find()` 方法，使其读取新的类变量，并在 `fetchAll()` 方法调用中使用它们代替硬编码的值：
