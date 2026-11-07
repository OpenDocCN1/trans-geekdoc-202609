
# Joke Website and Category Management

```
namespace Ijdb;
class JokeWebsite implements \Ninja\Website {
    private ?\Ninja\DatabaseTable $jokesTable;
    private ?\Ninja\DatabaseTable $authorsTable;
    private ?\Ninja\DatabaseTable $categoriesTable;
    private \Ninja\Authentication $authentication;

    public function __construct() {
        $pdo = new \PDO('mysql:host=mysql;dbname=ijdb;charset=utf8mb4', 'ijdbuser', 'mypassword');

        $this->jokesTable = new \Ninja\DatabaseTable($pdo, 'joke', 'id', '\Ijdb\Entity\Joke', [&$this->authorsTable]);

        $this->authorsTable = new \Ninja\DatabaseTable($pdo, 'author', 'id', '\Ijdb\Entity\Author', [&$this->jokesTable]);

        $this->categoriesTable = new \Ninja\DatabaseTable($pdo, 'category', 'id');

        $this->authentication = new \Ninja\Authentication($this->authorsTable, 'email', 'password');

    }

    public function getDefaultRoute(): string {
        return 'joke/home';
    }

    public function getController(string $controllerName): ?object {
        if ($controllerName === 'joke') {
            $controller = new \Ijdb\Controllers\Joke($this->jokesTable, $this->authorsTable, $this->authentication);
        }
        else if ($controllerName === 'author') {
            $controller = new \Ijdb\Controllers\Author($this->authorsTable);
        }
        else if ($controllerName === 'category') {
            $controller = new \Ijdb\Controllers\Category($this->categoriesTable);
        }
        else {
            $controller = null;
        }

        return $controller;
    }
}
```

Notice that I haven’t specified an entity class for the `category` table. Unless we need to add some functionality to it, it can use the `stdClass` class that we set as the default.

While we’re here, the `if … else` statement in the `getController` method is starting to become a little long and difficult to manage.

When faced with this kind of problem, it’s often better to remove the `if` statement entirely. You might be wondering how to do this kind of decision-making without an `if` statement, but it’s actually very straightforward and requires even less code.

To solve this without an `if`, we can move the `if … else` into an array:

```
public function getController(string $controllerName): ?object {

  $controllers = [
    'joke' => new \Ijdb\Controllers\Joke($this->jokesTable, $this->authorsTable, $this->authentication),
    'author' => new \Ijdb\Controllers\Author($this->authorsTable),
    'login' => new \Ijdb\Controllers\login($this->authentication),
    'category' => new \Ijdb\Controllers\Category($this->categoriesTable)
  ];

  return $controllers[$controllerName] ?? null;
}
```

This creates an array of all the possible controllers, then looks up the controller by its name—which is a lot simpler than a long `if … else` statement. To add new controllers, we simply add an entry to the array with the name and the corresponding controller object.

## Processing Power vs Memory

Using an array like this requires less processing, but it will use more memory. All the classes must be loaded into memory, and objects must be created up front for the array.

Loading classes has very little overhead as long as PHP’s `OPcache` is turned on. The `OPcache` stores parsed code in a single file for all classes in the project. In the old days of PHP, a `require` statement (even one triggered by an autoloader) caused PHP to look the file up on disk—a relatively slow process. This is no longer the case.

However, constructing all three controllers will use slightly more memory. Ultimately, you have to choose between additional processing power or additional memory usage. Since both are going to be negligible, I prefer the latter, as the code is cleaner.

If you’ve followed the steps above, visit `https://v.je/category/edit` and you should see the form. To get it working, add the `editSubmit` method to add a category to the database when the form is submitted.

**Example: [Relationships-AddCategory-Save](https://github.com/spbooks/phpmysql7/tree/Relationships-AddCategory-Save)**

```
public function editSubmit() {
  $category = $_POST['category'];

  $this->categoriesTable->save($category);

  header('location: /category/list');
}
```

If you test the form and press **Save**, you’ll see an error message, because we haven’t built the list page yet. However, you can check the form is working by selecting all the records from the table in `MySQL Workbench`.

Once a category has been added, you should even be able to edit it by visiting `https://v.je/category/edit/1`.

At this point, it’s worth momentarily stepping back and considering the benefit of the classes and framework we’ve built. With fairly little effort, we’ve created a form that allows inserting data into the database, loading a record into it and editing it. Think back to Chapter 4, when we were manually writing `INSERT` and `UPDATE` queries, and consider how much more code you would have needed to write with that approach!

## List Page

We can also add the list page with fairly little code. Firstly, let’s create a `categories.html.php` template that loops through a list of categories and displays an **Edit**/**Delete** option for each of them.

**Example: [Relationships-ListCategories](https://github.com/spbooks/phpmysql7/tree/Relationships-ListCategories)**

```
<h2>Categories</h2>

<a href="/category/edit">Add a new category</a>

<?php foreach ($categories as $category): ?>
<blockquote>
  <p>
  <?=htmlspecialchars($category->name, ENT_QUOTES, 'UTF-8')?>

  <a href="/category/edit?id=<?=$category->id?>">Edit</a>
  <form action="/category/delete" method="post">
    <input type="hidden" name="id" value="<?=$category->id?>">
    <input type="submit" value="Delete">
  </form>
  </p>
</blockquote>

<?php endforeach; ?>
```

Here’s the controller action in `Category.php`:

```
public function list() {
  return ['template' => 'categories.html.php',
    'title' => 'Joke Categories',
    'variables' => [
      'categories' => $this->categoriesTable->findAll()
    ]
  ];
}
```

The **Edit** link from the template already works. Add the route and controller action for the **Delete** button to finish the category management pages.

**Example: [Relationships-DeleteCategory](https://github.com/spbooks/phpmysql7/tree/Relationships-DeleteCategory)**

```
public function deleteSubmit() {
  $this->categoriesTable->delete('id', $_POST['id']);

  header('location: /category/list');
}
```

## Assigning Jokes to Categories

Now that categories can be added to the website, let’s add the ability to assign a joke to a category.

As I mentioned previously, the *simplest* approach would be to have a `<select>` box on the add joke page, which sets a `categoryId` column in the `joke` table.

However, this approach is the least flexible. It’s possible that a joke will fall into more than one category. Instead, we’re going to model this relationship using a **join table**—that is, a table with just two columns.

In our case, the columns will be `jokeId` and `categoryId`.

Let’s create the following table using either `MySQL Workbench` or by running this query:

```
CREATE TABLE `ijdb`.`joke_category` (
  `jokeId` INT NOT NULL,
  `categoryId` INT NOT NULL,
  PRIMARY KEY (`jokeId`, `categoryId`));
```

Note that both the `jokeId` and `categoryId` columns are the primary key. As I explained in Chapter 4, this is to prevent the same joke being added to a category twice.

Before continuing, let’s add some categories to the database. Using the form at `https://v.je/category/edit`, add the categories “programming jokes” and “one-liners”.

Currently, we have three jokes, each of which falls into the “programming jokes” category:

> How many programmers does it take to screw in a lightbulb? None. It’s a hardware problem.

> 

> Why did the programmer quit his job? He didn’t get arrays.

> 

> Why was the empty array stuck outside? It didn’t have any keys.

Here are some more jokes that fit in the two categories:
