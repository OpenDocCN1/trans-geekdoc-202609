
# 数据管理：更新与删除操作

## 显示作者列表并添加删除功能

在 `display_authors.php` 页面中，该页面显示所有作者，我们将引入一个名为“Delete”的新列。该列中的每个单元格将包含一个链接，允许将相应的作者 ID 传递给新的 `delete_author.php` 文件。该文件将负责处理所选作者的删除操作。

以下是更新后的 `display_authors.php` 脚本代码：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>List of Authors</title>
    <link rel="stylesheet" href="style_tab.css">
</head>
<body>
    <h2>List of Authors</h2>

    <?php
    // Database connection
    $connexion = new PDO("mysql:host=localhost;dbname=bibliotheque", "root", "");
    $connexion->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    // Prepare selection query
    $query = $connection->prepare("SELECT * FROM authors");

    // Execute query
    $requete->execute();

    // Retrieve results
    $authors = $requete->fetchAll(PDO::FETCH_ASSOC);

    // Display results in HTML table
    if (count($authors) > 0) {
        echo "<table>";
        echo "<tr>
            <th>ID</th>
            <th>Name</th>
            <th>First name</th>
            <th>Email</th>
            <th>Biography</th>
            <th>Edit</th>
            <th>Delete</th>
        </tr>";

        foreach ($authors as $author) {
            echo "<tr>";
            echo "<td>{$author['author_id']}</td>";
            echo "<td>{$author['name']}</td>";
            echo "<td>{$author['firstname']}</td>";
            echo "<td>{$author['email']}</td>";
            echo "<td>{$author['biography']}</td>";
            echo "<td>
                <a href='form_modifier_auteur.php?id_auteur={$auteur['id_auteur']}'>
                    Edit
                </a></td>";
            echo "<td>
                <a href='supprimer_auteur.php?id_auteur={$auteur['id_auteur']}'>
                    Delete
                </a></td>";
            echo "</tr>";
        }
        echo "</table>";
    } else {
        echo "No author found.";
    }
    ?>
</body>
</html>
```

在 `display_authors.php` 脚本中，已向作者表添加新的“Delete”列。该列由以下代码定义的“Delete”表头标识：

```html
<th>Delete</th>
```

该列中的每一行都包含一个指向 `delete_author.php` 文件的链接，并带有删除操作参数。

```php
echo "<td>
    <a href='delete_author.php?author_id={$author['author_id']}'>
        Delete
    </a>
</td>";
```

此修改为用户提供了额外功能，可直接从表格显示的列表中删除特定作者。访问 `display_authors.php` 脚本时，将获得类似下图所示的结果：

![Image](images/image-160.png)

随后，我们在 `library` 项目根目录下创建了一个名为 `delete_author.php` 的新空文件。如果您此时点击“Delete”列中的第一个链接，将进入一个空白页面，因为 `delete_author.php` 文件仍为空。但请注意 URL 中通过 `author_id` 参数传递的作者 ID。

![Image](images/image-161.png)

以下代码实现了删除 URL 中传递标识符对应的作者的功能：

```php
<?php
// Check if the ID of the author to be deleted is present in the URL
if (isset($_GET['author_id'])) {
    // Retrieve author ID from URL
    $author_id = $_GET['author_id'];

    // Connect to database
    $connection = new PDO("mysql:host=localhost;dbname=library", "root", "");
    $connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    // Prepare deletion request
    $request = $connection->prepare("DELETE FROM authors WHERE author_id = :author_id");

    // Bind parameters
    $request->bindParam(':author_id', $author_id);

    // Execute query
    $result = $request->execute();

    // Verify successful deletion
    if ($result) {
        echo "The author has been successfully deleted.";
    } else {
        echo "An error occurred during deletion";
    }
} else {
    echo "No author ID specified for deletion";
}
?>
```

此 PHP 代码执行以下操作：

*   使用 `isset($_GET['author_id'])` 条件检查 URL 中是否存在要删除的作者 ID。这确保在继续删除之前已正确传输作者 ID。
*   如果 URL 中存在作者 ID，则从超全局变量 `$_GET['author_id']` 中检索它。
*   使用 PDO 建立数据库连接，并使用适当的凭据。
*   准备一条删除请求，以从 `authors` 表中删除作者，其中作者 ID 对应于 URL 中传递的 ID。
*   使用 `bindParam()` 方法将查询参数绑定到作者 ID。
*   使用 `execute()` 方法执行查询。
*   根据删除结果，向用户显示相应消息，指示操作是否成功或是否发生错误。

此脚本确保仅使用有效的作者 ID 进行删除，从而避免数据库中发生任何未经授权或意外的删除。

当您点击任意“Delete”链接时，将收到消息“The author has been successfully deleted.” 如果您检查数据库，将发现相应作者确实已从 `authors` 表中删除。

点击“Delete”链接后，如果一切顺利，将显示消息“The author has been successfully deleted.” 此外，如果您检查作者表，会注意到相应作者确实已被删除。

![Image](images/image-162.png)

### 删除确认

从数据库中删除数据有时会产生重大后果。因此，在执行删除操作之前实施确认机制至关重要，以避免意外或不必要的删除。在执行最终删除前，务必请求确认。

为了在永久删除作者前增加删除确认步骤，可以使用 JavaScript 对话框请求用户确认其操作。

在 `display_authors.php` 文件中，修改删除链接以调用显示确认对话框的 JavaScript 函数：

```php
echo "<td>
    <a href='delete_author.php?author_id={$author['author_id']}' onclick='return confirmDelete()'>
        Delete
    </a></td>";
```

在显示所有作者的表格的删除链接中，我们集成了值为 `'return confirmDelete()'` 的 `onclick` 属性。当用户点击关联元素时，这会触发对 JavaScript 函数 `confirmDeletion()` 的调用。`return` 关键字用于传递该函数的返回值。在此上下文中，我们将创建一个名为 `confirmDelete()` 的新 JavaScript 函数。该函数向用户显示确认对话框，邀请他们确认是否真要执行关联操作（如删除元素）。如果用户确认，函数返回 `true`，允许点击事件正常进行并执行预期操作。反之，如果用户取消确认，函数返回 `false`，从而取消点击操作并阻止任何进一步动作。值得注意的是，本书不专注于 JavaScript，因此我们不会详细介绍这些概念。

接下来，在 `display_authors.php` 文件的 `<head>` 标签之间的 `<script>` 标签中创建名为 `confirmDelete()` 的 JavaScript 函数。

```html
<script>
function confirmDelete() {
    return confirm("Do you really want to delete this author?");
}
</script>
```

从现在起，当您点击作者删除链接之一时，将出现确认框，如下图所示：

![Image](images/image-163.png)

## 结论

在本章中，我们深入探讨了数据库内数据管理的关键方面，重点关注更新和删除流程。通过理解这些基本操作，您现在拥有了维护数据完整性和相关性的强大工具。

