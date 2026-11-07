
# 笑话实体和类别分配

## editSubmit 方法

```
public function editSubmit() {
  $author = $this->authentication->getUser();

  if (!empty($id)) {
    $joke = $this->jokesTable->find('id', $id)[0];

    if ($joke->authorId != $author->id) {
      return;
    }
  }   

  $joke = $_POST['joke'];
  $joke['jokedate'] = new \DateTime();

  $jokeEntity = $author->addJoke($joke);

  foreach ($_POST['category'] as $categoryId) {
    $jokeEntity->addCategory($categoryId);
  }

  header('location: /joke/list');
}
```

现在 `$author->addJoke($joke)` 返回一个 `Joke` 实体对象，我们可以在代表刚插入记录的实体上调用方法。在这种情况下，可以使用 `$jokeEntity->addCategory($categoryId)` 为刚添加到数据库的笑话分配类别。

当然，要实现这一点，我们需要对 `Joke` 实体类进行一些更改。

由于 `addCategory()` 方法会向新的 `joke_category` 表写入记录，因此它需要一个对 `jokeCategoriesTable` `DatabaseTable` 实例的引用。你知道该怎么做：添加一个类变量和构造函数参数：

## Joke 实体类

```
namespace Ijdb\Entity;

class Joke {
    public int $id;
    public int $authorId;
    public string $jokedate;
    public string $joketext;
    private ?object $author;

    public function __construct(private ?\Ninja\DatabaseTable $authorsTable, private ?\Ninja\DatabaseTable $jokeCategoriesTable) {
    }

    public function getAuthor() {
      if (empty($this->author)) {
        $this->author = $this->authorsTable->find('id', $this->authorId)[0];
      }

      return $this->author;
    }
}
```

然后修改 `Ijdb\JokeWebsite` 以将实例作为参数提供给 `$jokesTable` 实例的构造函数：

```
$this->jokesTable = new \Ninja\DatabaseTable($pdo, 'joke', 'id', '\Ijdb\Entity\Joke', [&$this->authorsTable, &$this->jokeCategoriesTable]);
```

通过将 `&$this->jokeCategoriesTable` 添加到作为第五个参数传递的数组中，每次在 `$jokesTable` 实例内部创建 `\Ijdb\Entity\Joke` 的实例时，构造函数都将使用 `authorsTable` 和 `jokeCategoriesTable` 实例调用。

## addCategory 方法

接下来，将 `addCategory()` 方法添加到 `Joke` 实体类。

示例：[关系-分配类别](https://github.com/spbooks/phpmysql7/tree/Relationships-AssignCategory)

```
public function addCategory($categoryId) {
  $jokeCat = ['jokeId' => $this->id, 'categoryId' => $categoryId];

  $this->jokeCategoriesTable->save($jokeCat);
}
```

这段代码相当简单。第一行创建了一个表示要添加记录的数组。`jokeId` 是我们要添加类别的笑话的 `id`（来自 `$pdo->lastInsertId()`），而 `categoryId` 来自参数。

有了这段代码，每当笑话被添加到网站时，它就会被分配到已选中的类别。

继续添加我之前提供的笑话，或你自己的，并通过在 MySQL Workbench 中从表中选择记录来验证记录是否已添加到 `joke_category` `join` 表中。

## 按类别显示笑话

现在数据库中已有分配了类别的笑话，让我们添加一个页面，允许按类别选择笑话。

在笑话列表页面上，让我们添加一个类别列表以允许筛选笑话。

第一部分相当简单：我们需要在笑话列表页面上以链接的形式列出类别。这涉及两个相当简单的步骤。

首先，修改 `list()` 动作以向模板传递类别列表：

```
public function list() {
  $jokes = $this->jokesTable->findAll();

  $title = 'Joke list';

  $totalJokes = $this->jokesTable->total();

  $author = $this->authentication->getUser();

  return ['template' => 'jokes.html.php',
    'title' => $title,
    'variables' => [
      'totalJokes' => $totalJokes,
      'jokes' => $jokes,
      'userId' => $author->id ?? null,
      'categories' => $this->categoriesTable->findAll()
    ]
  ];
}
```

其次，在 `jokes.html.php` 模板中遍历类别并为每个类别创建带链接的列表：

```
<ul class="categories">
  <?php foreach ($categories as $category): ?>
    <li><a href="/joke/list/<?=$category->id?>"><?=$category->name?></a><li>
  <?php endforeach; ?>
</ul>
```

为了让它看起来更漂亮一些，你还可以添加一个包含的 `<div>` 和围绕笑话列表的 `<div>`：

```
<div class="jokelist">

<ul class="categories">
  <?php foreach ($categories as $category): ?>
    <li><a href="/joke/list?/<?=$category->id?>"><?=$category->name?></a><li>
  <?php endforeach; ?>
</ul>

<div class="jokes">

<p><?=$totalJokes?> jokes have been submitted to the Internet Joke Database.</p>

<?php foreach ($jokes as $joke): ?>
    // …
<?php endforeach; ?>

</div>
```

然后应用以下 CSS：

```
.jokelist {display: table;}
.categories {display: table-cell; width: 20%; background-color: #333; padding: 1em; list-style-type: none;}
.categories a {color: white; text-decoration: none;}
.categories li {margin-bottom: 1em;}
.jokelist .jokes {display: table-cell; padding: 1em;}
```

这个示例可以在 关系-类别列表 中找到。

列表就这样完成了，但链接目前什么都不做。每个链接都会向 URL 传递第三级。如果你点击其中一个新类别链接，你会看到访问的页面是 `/jokes/list/1` 或类似。

你可能已经想出我们现在需要做什么了。我们需要使用第三个 URL 参数来筛选与所选类别关联的笑话。

例如，如果 ID 为 `1` 的类别是 *编程笑话*，并且用户访问 `/jokes/list/1`，它应该只显示 *编程笑话* 类别的笑话。如果用户访问 `/jokes/list/2` 并且 ID 为 `2` 的类别是 *一句话笑话*，则只应显示 *一句话笑话* 类别的笑话。

在第 9 章中，我们修改了 `edit()` 方法以使用可以提供被编辑笑话 ID 的参数。我们已经设置了 `EntryPoint` 类将任何 URL 转换为 `/[controller]/[method]/[argument1]/[argument2]./...`，因此要访问方法中的类别，我们只需向 `list()` 方法添加参数，记住我们也希望能够获取所有笑话的列表，因此我们需要为其提供默认值：

```
public function list($categoryId = null) {
```

当访问 `/joke/list/2` 时，`$categoryId` 参数将被设置为 `2`。

如果我们将关系建模为使用 `joke` 表中 `categoryId` 列的 *一对一* 关系，这将相对简单。在 `list()` 控制器操作中，我们只需修改 `$jokes` 变量的设置方式：

```
if (!empty($categoryId)) {
  $jokes = $this->jokesTable->find('categoryId', $categoryId);
}
else {
  $jokes = $this->jokesTable->findAll();
}
```

然而，由于我们有一个 *多对多* 关系，情况就不那么简单了。一个选择是将 `jokeCategoriesTable` 传递给控制器，从中查询所有对应的笑话：

```
if (!empty($categoryId)) {
  $jokeCategories = $this->jokeCategoriesTable->find('categoryId', $categoryId);

  $jokes = [];

  foreach ($jokeCategories as $jokeCategory) {
    $jokes[] = $this->jokesTable->find('id', $jokeCategory->jokeId)[0] ?? null;
  }
}
else {
  $jokes = $this->jokesTable->findAll();
}
```

在此示例中，我们通过其 `id`（例如 `4`）获取所选类别的 `joke_cagegory` 表中的所有记录。这给我们一个记录集，每个记录都有一个 `categoryId` 和一个 `jokeId`。

在我们的示例中，`categoryId` 将始终为 `4`，因为我们只选择了该类别的记录，但每个记录都有唯一的 `jokeId`。然后我们遍历所有记录并从 `joke` 表中找到相关记录，将每个 `joke` 记录添加到 `$jokes` 数组中。
