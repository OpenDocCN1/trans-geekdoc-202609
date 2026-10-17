
```php
<?php
/*  Program name: displayForm
 *  Description:  Script displays a form that asks for the
 *                customer address.
 */
echo "<html>
        <head><title>Customer Address</title></head>
        <body>";
$labels = array( "firstName"=>"First Name:",
                "midName"=>"Middle Name:",
                "lastName"=>"Last Name:",
                "street"=>"Street Address:",
                "city"=>"City:",
                "state"=>"State:",
                "zip"=>"Zipcode:");
echo "<p align='center'>
        <b>Please enter your address below.</b><hr>";
echo "<form action='processform.php' method='POST'>
        <table width='95%' border='0' cellspacing='0'
                cellpadding='2'>\n";
foreach($labels as $field=>$label)
{
    echo "<tr>
            <td align='right'><B>{$labels[$field]} </B><br></td>
            <td><input type='text' name='$field' size='65'
                    maxlength='65' ></td>
            </tr>";
```
```php
}
echo "</table>
        <div align='center'><p><input type='submit'
             value='Submit Address'> </p></div>
        </form>";
?>
</body></html>
```

请注意 `displayForm.php` 中的以下内容，如清单 8-6 所示：

- 创建一个包含表单中使用的标签的数组。键是字段名称。
- 脚本 `processform.php` 被指定为表单提交时运行的脚本。表单中的信息发送到 `processform.php`，后者处理这些信息。
- 表单使用 HTML 表格进行格式化。表格是 HTML 的重要组成部分。如果您不熟悉 HTML 表格，请查看 *HTML 4 For Dummies*，第 4 版，作者 Ed Tittel 和 Natanya Pitts（Wiley）。
- 脚本使用 `foreach` 语句遍历 `$labels` 数组。在每次循环中输出表格行的 HTML 代码。适当的数组值在 HTML 代码中使用。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_233_0.png)

出于安全原因，请始终在 HTML 语句中包含 `maxlength` — 它定义用户允许在字段中输入的字符数。限制字符数有助于防止坏人将恶意代码输入到您的表单字段中。如果信息将存储在数据库中，请将 `maxlength` 设置为与数据库表中列的宽度相同的数字。

当 Goliath Smith 填写图 8-5 所示的表单（由清单 8-6 中的程序创建）并提交时，程序 `processform.php` 运行并产生以下输出：

```
firstName = Goliath
midName =
lastName = Smith
street = 1234 Tall St
city = Big City
state = TX
zip = 88888
```

在 `processform.php` 中，`$_POST` 内置数组的所有元素都会显示，因为本节中显示的两个表单都使用了 POST 方法，大多数表单也是如此。除了 `$_POST` 数组之外，还有其他内置数组，如表 8-2 所示。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_234_0.png)

图 8-5：用于输入客户地址的表单。

相同的 information 可在两组数组中使用。使用较新的数组（名称以 _ 开头），因为它们可以在任何地方使用，甚至在函数内部使用。（我在第 7 章中解释了函数以及函数内部变量的使用。）这些数组称为超全局变量或自动全局变量，于 PHP 4.1.0 中引入。旧的数组，其名称很长，例如 `$HTTP_POST_VARS`，在函数中使用之前必须设为全局变量，我在第 7 章中解释了这一点。旧的数组只有在您被迫使用早于 PHP 4.1.0 的 PHP 版本时才应使用。

## 使表单动态化

PHP 为 HTML 表单带来了新的功能。因为您可以在 PHP 表单中使用变量，所以您的表单现在可以是动态的。以下是 PHP 为表单带来的主要功能：

- ✓ 使用变量在输入文本字段中显示信息
- ✓ 使用变量为用户构建动态选择列表
- ✓ 使用变量为用户构建动态单选按钮列表
- ✓ 使用变量为用户构建动态复选框列表

### 在表单字段中显示动态信息

当您在网页上显示表单时，您可以将信息放入字段中，而不是仅显示空白字段。例如，如果大多数客户居住在美国，您可以在询问客户地址时自动在国家/地区字段中输入 US。如果客户确实居住在美国，您就为客户节省了输入时间。而且如果客户不住在美国，他或她只需将 **US** 替换为适当的国家即可。此外，如果程序自动将 **US** 作为字段的值输入，您就知道该信息没有任何错误。

要显示包含信息的文本字段，您对输入字段 HTML 语句使用以下格式：

```html
<input type="text" name="country" value="US">
```

通过使用 PHP，您可以使用变量以以下任一语句显示此信息：

```php
<input type="text" name="country"
       value="<?php echo $country ?>">
echo "<input type='text' name='country' value='$country'>";
```

第一个示例在 HTML 部分中创建输入字段，仅对值使用简短的 PHP 部分。第二个示例使用 PHP 部分中的 `echo` 语句创建输入字段。如果您使用的是只有偶尔使用变量的长表单，使用第一种格式更有效。如果您的表单使用许多变量，则使用第二种格式更有效。

如果您将用户信息存储在数据库中，您可能希望在表单字段中显示来自数据库的信息。例如，您可能向用户显示信息，以便他或她进行必要的更改。或者您可能显示客户上次在线订单的送货地址，以便他或她不必重新输入地址。清单 8-7 显示了程序 `displayAddress.php`，它显示了一个包含来自数据库信息的表单。此表单与图 8-5 所示的表单非常相似，只是此表单中包含信息（从数据库检索），而图 8-5 中的表单字段为空。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_235_0.png)

### 注册长数组

PHP 5 中引入的新 `php.ini` 设置允许您防止 PHP 自动创建较旧的长数组。您不太可能需要使用它们，除非您使用包含长变量的一些旧脚本。`php.ini` 中的以下行控制此设置：

```ini
register_long_arrays = On
```

目前，此设置默认情况下为 **On**。除非您正在运行需要旧数组的旧脚本，否则应将设置更改为 **Off**，以便 PHP 不执行此额外工作。尽管设置目前默认情况下为 **On**，但情况可能会改变。默认设置将来可能会更改为 **Off**。如果您使用了一些旧脚本，并且在包含长数组的行上出现错误，例如 `$HTTP_GET_VARS`，请检查 `php.ini` 中长数组的设置。它可能为 **Off**，并且旧脚本所需的长数组根本没有被创建。

## 列表 8-7：用于显示 HTML 表单信息的程序

```php
<?php
/* Program name: displayAddress
 * Description: Script displays a form with address
 *              information obtained from the database.
 */
echo "<html>
    <head><title>Customer Address</title></head>
    <body>";
$labels = array( "firstName"=>"First Name:",
                "lastName"=>"Last Name:",
                "street"=>"Street Address:",
                "city" =>"City:",
                "state"=>"State:",
                "zip"=>"Zipcode:");
$user="admin";
$host="localhost";
$password="";
$database = "MemberDirectory";
$loginName = "gsmith";    // user login name

$connection = mysql_connect($host,$user,$password)
    or die ("Couldn't connect to server");
$db = mysql_select_db($database,$connection)
    or die ("Couldn't select database");
$query = "SELECT * FROM Member
          WHERE loginName='$loginName'";
$result = mysql_query($query)
    or die ("Couldn't execute query.");
$row = mysql_fetch_array($result);

echo "<p align='center'>
    <h1 align='center'>Address for $loginName</h1>\n";
echo "<br><p align='center'>
    <font size='+1'><b>Please check the information below
    and change any information that is incorrect.</b></font>
    <hr>";
echo "<form action='processAddress.php' method='POST'>
    <table width='95%' border='0' cellspacing='0'
    cellpadding='2'>\n";
foreach($labels as $field=>$label)
{
    echo "<tr>
        <td align='right' ><B>{$labels[$field]} </B></br></td>
        <td><input type='text' name='$field'
            value='$row[$field]' size='65' maxlength='65'>
        </td>
        </tr>";
}
echo "</table>
    <div align='center'><p><input type='submit'
        value='Submit Address' </p></div>
    </form>";
?>
</body></html>
```

请注意列表 8-7 中程序中的以下内容：

- 表单语句将操作转移到程序 `processAddress.php`。该程序处理表单中的信息并用用户更改的任何信息更新数据库。这是您自己编写的程序。检查表单中的数据并将信息保存到数据库将在本章后面的“检查信息”和“将信息放入数据库”部分中讨论。
- 表单中的每个输入字段都被赋予一个名称。输入字段中的信息存储在与输入字段同名的变量中。
- 程序将表单中的字段名称与数据库中的列名称设为相同。这简化了数据库和表单之间信息的移动，无需从一个变量向另一个变量传输信息。
- 数据库中的值通过输入字段语句中的 `value` 参数显示在表单字段中。`value` 参数显示来自数组 `$row` 的适当值，其中包含来自数据库的数据。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_237_0.png)

出于安全原因，始终在您的 HTML 语句中包含 `maxlength`。`maxlength` 定义用户允许在字段中输入的字符数。如果信息将被存储在数据库中，请将 `maxlength` 设置为与数据库表中列的宽度相同的数字。

图 8-6 显示了列表 8-7 中程序生成的网页。表单中的信息是存储在数据库中的信息。

## 构建选择列表

HTML 表单中可以使用的一种字段类型是选择列表。用户不是在字段中输入，而是从列表中选择。例如，在产品目录中，您可能会提供一个类别列表，用户从中选择他们想要查看的内容。或者用户地址的表单可能包含用户可以选择的州列表。或者用户可以通过从列表中选择月份、日期和年份来输入日期。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_237_1.png)

只要可行就使用选择列表。当用户从列表中选择一个项目时，您可以确保该项目是准确的，没有拼写错误、奇怪字符或用户输入错误带来的其他问题。

Pet Catalog 中类别的 HTML 选择列表的格式如下：

当用户单击 select 下拉列表框上的箭头时，整个列表会下拉，如图 8-8 所示，用户可以从列表中选择任何项目。请注意，cat 会被选中，直到用户选择不同的项目。

使用 PHP 时，您的选项可以是变量。此功能允许您构建动态选择列表。例如，您必须维护前面示例中显示的静态宠物类别列表。如果您添加一个新的宠物类别，您必须手动添加 `option` 标签。然而，使用 PHP 变量，您可以从数据库中的类别动态构建列表。当您向数据库添加新类别时，新类别会自动添加到您的选择列表中，而无需更改您的 PHP 程序。列表 8-8 中的程序 `buildSelect.php` 从数据库构建宠物类别的选择列表。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_239_0.png)

图 8-8：带有下拉列表的 Pet Catalog 选择字段。

## 列表 8-8：构建选择列表的程序

```php
<?php
/* Program name: buildSelect.php
 * Description: Program builds a selection list
 *              from the database.
 */
?>
<html>
<head><title>Pet Types</title></head>
<body>
<?php
$user="catalog";
$host="localhost";
$password="";
$database = "PetCatalog";

$connection = mysql_connect($host,$user,$password)
    or die ("couldn't connect to server");
$db = mysql_select_db($database,$connection)
or die ("Couldn't select database");
$query = "SELECT DISTINCT petType FROM Pet ORDER BY petType";
$result = mysql_query($query)
    or die ("Couldn't execute query.");

/* create form containing selection list */
echo "<form action='processform.php' method='POST'>
    <select name='petType'>\n";

while ($row = mysql_fetch_array($result))
{
    extract($row);
    echo "<option value='$petType'>$petType\n";
}
echo "</select>\n";
echo "<input type='submit' value='Select Type of Pet'>
    </form>\n";
?>
</body></html>
```

请注意列表 8-8 中程序中的以下内容：

- 在查询中使用 `DISTINCT`：`DISTINCT` 使查询仅获取每个宠物类型一次。如果没有 `DISTINCT`，查询如果在数据库中出现多次，则会多次返回每个宠物类型。
- 在查询中使用 `ORDER BY`：宠物类型按字母顺序排序。
- 循环之前的 `echo` 语句：`form` 和 `select` 标签在 `while` 循环开始之前被 `echo`，因为它们只 `echo` 一次。
- 循环中的 `echo` 语句：`option` 标签在循环中被 `echo` — 数据库中每个宠物类型一个。没有项目被标记为已选择，因此列表中的第一个项目会自动被选中。
