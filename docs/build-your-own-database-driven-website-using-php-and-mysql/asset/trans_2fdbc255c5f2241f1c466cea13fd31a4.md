

我们将提示管理员从数据库中那些作者的下拉列表中选择一位作者：

```html
<p>Author:
<select name="aid" size="1">
<option selected value="">Select One</option>
<option value="">------------------------</option>
<?php
while ($Author = mysql_fetch_array($authors)) {
    $aid = $Author["ID"];
    $aname = htmlspecialchars($Author["Name"]);
    echo("<option value='$aid'>$aname</option>\n");
}
?>
</select></p>
```

然而，下拉列表不足以用于类别的选择，因为我们希望管理员能够选择多个类别。因此，我们将使用一系列复选框——每个类别一个。由于我们无法预先知道需要多少个复选框，因此为它们命名的问题变得很有挑战性。我们实际上会做的是为所有复选框使用一个 *单个* 变量；因此，所有复选框将具有相同的名称。要能够从单个变量名接收多个值，我们必须将该变量设为 **数组**。回顾一下，数组是一个带有“隔间”的单个变量，每个隔间都可以保存一个值。要将表单元素作为数组变量的一部分提交，我们只需在变量名末尾添加一对方括号（在此情况下，将其变为 `cats[]`）。

当所有复选框都使用相同名称时，我们需要一种方法来识别选中了哪些特定复选框。为此，我们为每个复选框分配一个不同的值——数据库中相应类别的 ID。因此，表单提交的是一个数组，其中包含新笑话应添加到的所有类别 ID。

```html
<p>Place in categories:<br />
<?php
while ($cat = mysql_fetch_array($cats)) {
    $cid = $cat["ID"];
    $cname = htmlspecialchars($cat["Name"]);
    echo("<input type='checkbox' name='cats[]' ".
          "value='$cid'>$cname<br />\n");
}
?>
</p>
```

然后，我们照常完成表单：

```html
<p><input type="submit" name="submit" value="SUBMIT"></p>
</form>
<?php endif; ?>
```

由于我们第一次提交数组，处理此表单的代码并不完全直接。当我们将笑话添加到 Jokes 表时，它开始得相当简单。由于需要作者，我们确保 $aid 包含一个值。这防止管理员在作者选择列表中选择“Select One”选项，因为该选择的值为 ""（空字符串）。

```php
if ($submit): // A new joke has been entered
    // using the form.

if ($aid == "") {
    echo("<p>You must choose an author " .
    "for this joke. Click 'Back' " .
    "and try again.</p>");
    exit();
}

$dbcx = mysql_connect("localhost", "root",
    "mypasswd");
mysql_select_db("jokes");

$sql = "INSERT INTO Jokes SET
    JokeText='$joketext',
    JokeDate=CURDATE(),
    AID='$aid'";
if (@mysql_query($sql)) {
    echo("<p>New joke added</p>");
} else {
    echo("<p>Error adding new joke: " .
    mysql_error() . "</p>");
}

$jid = mysql_insert_id();
```

上述代码的最后一行使用了一个我们以前没有见过的函数：mysql_insert_id。该函数返回由 MySQL 的 AUTO_INCREMENT 功能分配给最后插入条目的编号。换句话说，它检索新插入笑话的 ID，我们稍后会用到它。

根据选中了哪些复选框向 JokeLookup 添加条目的代码并不那么简单。首先，我们以前从未见过复选框如何将其值传递给 PHP 变量。此外，我们需要处理这样一个事实：这些特定的复选框将提交到一个数组变量中。

典型的复选框在被选中时会将其值传递给 PHP 变量，而在未选中时不做任何操作。未分配值的复选框在被选中时会将 "on" 作为其相应变量的值传递。但是，我们已为复选框分配了值（类别 ID），因此这不是问题。

这些复选框提交到数组这一事实实际上为我们的代码带来了相当大的便利。本质上，我们从提交的表单中接收到的要么是 1) 一个要添加笑话的类别 ID 数组，要么是 2) 根本什么都没有（如果没有复选框被选中）。首先，让我们处理后者（特殊情况），即当发现 `$cats` 变量为空时创建一个空数组：

```php
if ($cats == "") $cats = array();
```

这里出现的 array 函数用于在 PHP 中创建一个新数组。传递给它的参数将成为数组的元素。因为我们在这里没有向它传递任何参数，所以它将简单地创建一个空数组。

既然我们已保证 `$cats` 变量包含一个数组，就可以使用循环依次考虑数组中的每个类别 ID，并将适当的条目插入数据库。由于此数组不是基于数据库行的，你可能会想知道如何访问数组中的值。毕竟，我们以前是使用数据库列名（例如 `$cat["Name"]`）来检索数组值的。在这种情况下，我们的数组只是通过将一系列值馈送到同一个变量名来创建的。当这种情况发生时，PHP 会自动为数组中的值分配数字标签或 **索引**。例如，第一个被选中的复选框的值会首先提交到数组中，并可以通过 `$cats[0]` 访问。也就是说，PHP 为其分配数组索引 0。第二个被选中的复选框的值将以索引 1 存储，可以通过 `$cats[1]` 访问。因此，如果有 `n` 个复选框被选中，则最后一个复选框的值将在 `$cats[n-1]` 中。通过在代码循环中依次递增数组索引，我们可以逐个处理此数组的元素。

但是等等... `n` 是什么？我们无法预先知道会有多少个复选框被选中，那么如何知道何时停止计数呢？嗯，有两种方法。第一种是使用名为 `count` 的 PHP 函数，它以数组作为参数并计算其中的元素数量。如果使用此方法，我们的 while 循环将如下所示：

```php
$i = 0; // First index
while ($i < count($cats)) { // while we're not at the end
    // process $cats[$i]
    $i = $i + 1;
}
```

如你所见，此循环使用一个 **计数器变量** (`$i`)，也就是说，一个计算循环执行次数的变量。第一次循环时，它的值为 0，然后在循环结束时我们给它加 1。因此，第二次循环时它的值为 1，以此类推。在循环内部，我们可以将此变量作为数组索引，从 `$cats` 数组中取出一个类别 ID。当 `$i` 达到 count($cats)（即 $cats 数组中的元素数量）时，循环停止。如果 $cats 不包含任何元素（即如果没有选择任何类别），则 $i 将开始时等于 count($cats)，循环内容根本不会执行！

这一切看起来都很酷，但实际上有更好的方法。我们不使用 count 函数，只需一直进行，直到达到 $cats[$i] 为空的 $i 值为止。当我们这样做时，我们知道我们已经到达了类别 ID 列表的末尾：

```php
$i = 0; // First index
while ($cats[$i] != "") { // while we're not at the end
    // process $cats[$i]
    $i = $i + 1;
}
```

这样运行会快一点，因为我们不需要在每次循环时调用函数。而且它聪明了一点点，我们程序员得趁机乐一乐！不过，请不要难以相信，PHP 通过拥有一种完全不同的循环类型（专门用于遍历数组，称为 foreach 循环）来破坏我们的乐趣。在这种情况下，代码如下所示：

```php
foreach ($cats as $catID) {
    // Process $catID
}
```

这将对 $cats 数组中的每个项目执行一次循环内部的代码（你看到 foreach 循环名称的由来了），并将每次循环的项目赋值给变量 $catID。由于此代码无可争议地比等效的 while 循环更整洁，我们将采用此方案。剩下要做的就是确定对每个选定的类别 ID 该执行什么操作。

好了，在被所有这些不同类型的循环分散注意力之前，我们正要拿我们的类别 ID 数组，并用它将新插入的笑话放入其相应的类别中。对数据库布局的粗略检查显示，我们只需为该笑话应成为成员的每个类别向 JokeLookup 表插入一条条目。回顾一下，JokeLookup 表中的每个条目由一个笑话 ID (JID) 和一个类别 ID (CID) 组合而成，这两者共同表示特定笑话属于特定类别。以下是完成的 foreach 循环：

```php
foreach ($cats as $catID) {
    $sql = "INSERT IGNORE INTO JokeLookup
    SET JID=$jid, CID=$catID";
    $ok = @mysql_query($sql);
    if ($ok) {
        $numCats = $numCats + 1;
    } else {
        echo("<p>Error inserting joke into category ".
        " $catID: " . mysql_error() . "</p>");
    }
}
```

