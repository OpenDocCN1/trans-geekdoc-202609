
在所有这些页面上，顶部有一行文字为 `Click on any picture to see a larger version`。如果客户点击图片，则会显示该图片的较大版本。

## 将宠物添加到目录

该应用程序包含三个客户看不到的页面；这些页面用于将宠物添加到宠物目录中。这三个页面按顺序工作以添加单个宠物：

- 1. **获取宠物类型页面。** 添加宠物到目录的人员选择宠物类型的单选按钮。用户还可以输入新的宠物类型。
- 2. **获取宠物信息页面。** 用户选择要添加的宠物的单选按钮并填写宠物描述、价格和图片文件名。用户还可以输入新的宠物名称。
- 3. **反馈页面。** 显示一个页面，展示已添加到目录的宠物信息。

## 获取宠物类型页面

第一个页面获取需要添加到目录的宠物的宠物类型。图 11-6 显示了获取宠物类型页面。请注意，目录中当前所有的宠物类型都已列出，并且提供了一个区域，用户可以在需要时输入新的宠物类型。

## 获取宠物信息页面

图 11-7 显示了第二个页面。此页面允许用户输入将进入目录的宠物的信息。此页面列出了所选宠物类型在目录中的所有宠物名称，以便用户可以选择其中一个。它还提供了一个区域，用户可以在需要时输入新的宠物名称。

## 反馈页面

当用户提交宠物信息时，信息将被添加到 `PetCatalog` 数据库中。图 11-8 显示了一个验证已添加到数据库中的信息的页面。用户可以点击链接返回第一页并添加另一只宠物。

## 获取缺失信息页面

应用程序检查数据以查看用户是否输入了所需信息，并提示用户输入任何未输入的信息。例如，如果用户在第一页选择“新类别”，则用户必须输入类别名称和描述。如果用户未输入名称或描述，则会显示一个页面指出问题并请求信息。图 11-9 显示了用户忘记输入类别名称和描述时看到的页面。

图 11-6：
添加宠物到目录的第一页。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_328_0.png)

## 选择要添加的宠物的类别。

如果您要添加的宠物类别未列出，请选择“新类别”并输入该类别的名称和描述。在您完成选择现有类别或输入新类别后，按“提交类别”。

图 11-7：
第二个页面要求输入宠物名称。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_328_1.png)

## 图 11-8：

最后一页提供反馈。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_329_0.png)

以下宠物已添加到宠物目录：

- Category: Dog
- Pet Name: Golden Retriever
- Pet Description: Large, intelligent retriever. Likes people. Often wins obedience trials.
- Price: 100.00
- Picture file: gold.jpg

Add Another Pet

## 图 11-9：

此页面请求新的类别和描述。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_329_1.png)

类别名称或类别描述留空。您必须同时输入两者。

Category name:

Category description:

Enter new category

Return to category page

## 编写程序

在您知道页面将是什么样子以及它们将做什么之后，您就可以编写程序了。一般来说，您为每个页面编写一个程序，尽管有时将程序分离到多个文件或将页面上的程序合并是有意义的。（有关如何组织应用程序的详细信息，请参阅第 10 章。）

正如我在第 10 章中所讨论的，将连接数据库所需的信息保存在单独的文件中，并在所有需要访问数据库的程序中包含该文件。出于安全原因，该文件应存储在安全位置并使用误导性的名称。对于此应用程序，以下信息存储在名为 `misc.inc` 的文件中：

```php
<?php
    $user="catalog";
    $host="localhost";
    $password="";
    $database="PetCatalog";
?>
```

宠物目录应用程序有两个独立的程序集：一组向客户展示宠物目录，另一组将新宠物输入目录。

### 向客户展示宠物

向客户展示宠物目录的应用程序有三个基本任务：

- 显示店面页面。提供目录链接。
- 显示用户选择宠物类型的页面。
- 显示所选宠物类型的宠物页面。

### 显示店面

店面页面不需要任何 PHP 语句。它只显示一个带有链接的网页。HTML 语句足以完成此操作。列表 11-1 显示了描述店面页面的 HTML 文件。

## 列表 11-1：店面页面的 HTML 文件

```php
<?php
  /* Program: PetShopFront.php
   * Desc:    Displays opening page for Pet Store.
   */
?>
```
```html
<html>
<head><title>Pet Store Front Page</title></head>
<body topmargin="0" leftmargin="0" marginheight="0"
      marginwidth="0">
  <table width="100%" height="100%" border="0"
         cellspacing="0" cellpadding="0">
    <tr>
      <td align="center" valign="top" height="30">
        <img src="images/awning-top.gif" alt="awning">
      </td>
    </tr>
    <tr>
      <td align="center" valign="top">
        <img src="images/Name.gif" alt="Pet Store">
        <p style="margin-top: 40pt">
        <img src="images/lizard-front.jpg" alt="animal picture"
             height="186" width="280">
        <p><h2>Looking for a new friend?</h2>
        <p>Check out our <a href="PetCatalog.php">Pet
             Catalog.</a>
        <br> We may have just what you're looking for.
      </td>
    </tr>
  </table>
</body></html>
```

请注意，链接指向名为 `PetCatalog.php` 的 PHP 程序。当客户点击链接时，宠物目录程序（`PetCatalog.php`）开始运行。

## 显示宠物类型

宠物类型页面（参见图 11-2）向客户显示目录中当前所有宠物类型的列表。列表 11-2 显示了生成宠物类型网页的程序。

## 列表 11-2：显示宠物类型的程序

```php
<?php
  /* Program: PetCatalog.php
   * Desc:        Displays a list of pet categories from the
                 PetType table. Includes descriptions.
   *              User checks radio button.
   */
?>
<html>
<head><title>Pet Types</title></head>
<body>
<?php
  include("misc.inc");
```

## 列表 11-2（续）

```php
$connection = mysql_connect($host,$user,$password)      #13
    or die ("couldn't connect to server");
$db = mysql_select_db($database,$connection)            #15
    or die ("Couldn't select database");

/* Select all categories from PetType table */
$query = "SELECT * FROM PetType ORDER BY petType";      #19
$result = mysql_query($query)                           #21
    or die ("Couldn't execute query.");

/* Display text before form */
echo "<div style='margin-left: .1in'>"
<h1 align='center'>Pet Catalog</h1>
<h2 align='center'>The Following animal friends are
waiting for you.</h2>
<p align='center'>Find just what you want and hurry in to
the store to pick up your new friend.
<p><h3>Which pet are you interested in?</h3>\n";

/* Create form containing selection list */
echo "<form action='ShowPets.php' method='post'>\n";    #34
echo "<table cellpadding='5' border='1'>";
$counter=1;                                             #36
while ($row = mysql_fetch_array($result))               #37
{
    extract($row);                                      #39
    echo "<tr><td valign='top' width='15%'>\n";
    echo "<input type='radio' name='interest'
        value='$petType'\n";                           #42
    if ( $counter == 1 )                                #43
    {
        echo "checked";
    }
    echo "><font size='+1'><b>$petType</b></font>";    #47
    echo "</td>"
    "<td>$typeDescription</td>";                       #49
    echo "</tr>";
    $counter++;                                         #51
}
echo "</table>";
echo "<p><input type='submit' value='Select Pet Type'>
</form>\n";                                             #55
?>
</div>
</body></html>
```

列表 11-2 中的程序在某些行的末尾有行号。行号是参考，以便我可以引用程序的特定部分。以下列表中的数字对应于列表中的行号。以下是这些行在程序中作用的简要说明：
