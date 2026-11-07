
# 位权限

在包含多个列的数据库中，我们可以使用 `SELECT * FROM author WHERE id = 4 AND editCategories = 1` 来确定 `editCategories` 列是否对于特定用户被设置为 `1` —— 在本例中，`id` 为 `4` 的用户。

大多数编程语言，包括 PHP 和 MySQL，都支持一种称为 **位运算** 的功能。这些允许你查询任意整数中是否设置了特定的位。使用单个 `permissions` 列，上面的查询可以表示如下：

```
SELECT * FROM author WHERE id = 4 AND 8 & permissions
```

这里巧妙的部分是 `AND 8 & permissions`。它使用位运算符 `&` 来查询该记录的 `permissions` 列中存储的数字是否设置了 `8` 位。

位运算符 `&` 用于检查提供的两个数字中哪些位同时被设置。`&` 运算符实际上是一种像 `+` 或 `-` 这样的数学运算，它接受两个操作数并产生一个输出。位运算符 `&` 的输出是同时在两个操作数中被设置的位列表。例如：

```
0010 & 1111 = 0010
0111 & 1111 = 0111
1000 & 1111 = 1000
1100 & 1001 = 1000
0000 & 1111 = 0000
```

这些相同的表达式在 PHP 和 MySQL 中使用十进制数也适用：

```
2 & 6 // will calculate to 2
```

这表示“数字 2 和 6 中哪些位同时被设置？”，并计算结果为 2。如果你想知道为什么，让我们用二进制数做同样的检查：

```
0010 & 0110
```

同时被设置的唯一位是从右数第二个位，它代表数字 2。在 PHP 中，该表达式将被求值为 true：

```
if (2 & 6 == 2) {

}
```

我们可以利用这一点来存储权限列表。如果用户拥有权限 `011111`（十进制为 31），并且我们想知道他们是否拥有与 `010000`（十进制为 16）关联的权限，我们可以使用表达式 `if (16 & 32 == 16)`

因为 `if` 语句会对任何非零整数求值为 true，如果表达式一侧的任何位在另一侧的数字中被设置，则 if 语句将被求值为 true。因此，这两者是等价的：

```
if (2 & 6) {

}
//equivalent to 
if (2 & 6 == 2) {

}
```

使用此简写时要谨慎。它仅在其中一个数字代表单个位时才有效（因此任何只有一个 1 的二进制数，例如 `00100` 或 `10000`，但不是 `01100`）。

像这样的二进制运算在 PHP 中其实相当常见！当你在 PHP 中将 `error_reporting` 变量设置为 `E_WARNING | E_NOTICE` 时，你所做的是设置代表警告和通知的位。PHP 然后会在遇到错误时内部检查哪些位被设置。

在内部，PHP 会做类似这样的事情：

```
if (E_NOTICE & ini_get('error_reporting')) {
  display_notice($notice);
}
```

我们可以将此应用于权限。假设 `author` 表有一个名为 `permissions` 的列：如果我们将 `EDIT_CATEGORY` 与位 `8` 关联，就可以通过以下代码确定作者是否具有 `EDIT_CATEGORY` 权限：

```
if (8 & $author->permissions) {

}
```

这段代码有我之前提到过同样的问题：对查看代码的人来说，这里到底发生了什么并不清楚。再次，我们可以将位表示为常量：

```
const EDIT_JOKE = 1;
const DELETE_JOKE = 2;
const LIST_CATEGORIES = 4;
const EDIT_CATEGORY = 8;
const DELETE_CATEGORY = 16;
const EDIT_USER_ACCESS = 32;
```

我们就可以像这样编写权限检查：

```
// Does the author have the EDIT_CATEGORY permission?
if (EDIT_CATEGORY & $author->permissions) {

}

// Does the author have the DELETE_JOKE permission?
if (DELETE_JOKE & $author->permissions) {

}
```

如果您不理解上面介绍的所有二进制理论，也没关系。您不需要理解底层理论就能理解这里发生了什么，而且正如您所见，您甚至永远不需要处理单独的数字或二进制值。作为设置此功能的程序员，您只需要将常量与相应的位关联起来。

## 在数据库中存储位权限

让我们在网站上实现这一点。通过向 `author` 表添加一个名为 `permissions` 的列来修改它，并将其设置为 `INT(64)`，以便我们可以存储最多 64 种不同的权限。

更改 `Author` 实体类中的常量值，如上所示。添加新权限意味着计算下一个位；只需将前一个值加倍即可。

我们不需要对编辑权限表单页面做任何更改，但需要添加 `permissionsSubmit` 方法并让它将二进制权限存储到数据库中。

在这样做之前，让我们考虑表单提交时会发生什么。如果您勾选标记为 `EDIT_JOKE` 和 `DELETE_CATEGORY` 的复选框，变量 `$_POST['permissions']` 将是一个包含数字 `1` 和 `16` 的数组（`[1, 16]`）。

我们希望将它们转换为二进制表示，其中 `1` 位和 `16` 位被设置。听起来很困难，但正如你很快就会看到的，其实并不难！

我们需要生成的数字是 `010001`，其中 `16` 位和 `1` 位被设置。利用你新的二进制知识计算此值的十进制版本，你会发现这个二进制数代表 17。

我们需要做的就是将数字加起来！

为了证明理论，让我们假设 `EDIT_JOKE`、`DELETE_JOKE`、`LIST_CATEGORIES` 和 `EDIT_USER_ACCESS` 的复选框被勾选。提交表单时，我们会得到数组 `[1, 2, 4, 32]`。

这些权限的二进制表示是 `100111`。如果你算出它的十进制值，会得到 `39`。将数组中的值相加 `1 + 2 + 4 + 32`，你也会得到 39！

我们需要做的就是将 `$_POST['permissions']` 数组中的每个元素加起来以将数字存储到数据库中。

PHP 甚至包含一个名为 `array_sum` 的函数，可以完全做到这一点。

`Author` 控制器中的 `permissionsSubmit` 方法可以这样写：

```
public function permissionsSubmit($id = null) {
  $author = [
    'id' => $_POST['id'],
    'permissions' => array_sum($_POST['permissions'] ?? [])
  ];

  $this->authorsTable->save($author);

  header('location: /author/list');
}
```

行 `'permissions' => array_sum($_POST['permissions'] ?? [])` 用于将 `$_POST['permissions']` 数组中的所有值相加。然而，如果没有勾选任何复选框，`$_POST['permissions']` 将不会被设置。`??` 运算符用于在 `$_POST['permissions']` 变量中没有内容时为 `array_sum` 提供一个空数组。

就是这样！`permissionsSubmit` 方法将勾选的复选框转换为一个数字，而该数字的二进制表示就是我们对每个用户权限的建模方式。

## 连接表与位方法：优缺点

使用类别的 `join` 表方法时，为了处理未勾选的复选框，我们必须在每次提交表单时专门删除所有记录并重新插入它们。由于 `permissions` 列是一个单一数字，如果没有勾选任何复选框，`array_sum` 将返回 `0`，并且 `0` 将被插入数据库，避免了专门处理未勾选复选框的需求。

最后一步是 `Author` 实体类中的 `hasPermission` 方法。添加 `$permission` 类变量。然后，要检查用户是否具有权限，我们只需要一行代码。

示例：[关系-二进制权限](https://github.com/spbooks/phpmysql7/tree/Relationships-BinaryPermissions)

```
public function hasPermission(int $permission) {
  return $this->permissions & $permission;
}
```

与 `join` 表相比，这种方法有几个优势。首先是性能：我们不需要为用户的权限查询数据库。其次，这在保存表单和检查权限是否设置方面代码要少得多。
