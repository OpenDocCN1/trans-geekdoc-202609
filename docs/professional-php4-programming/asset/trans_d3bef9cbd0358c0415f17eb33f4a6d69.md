

我们为窗口创建的最后一个小部件是一个文本为“登录”的 GtkButton。我们将此按钮的 clicked 信号连接到 doLogin() 函数。当用户填写完用户名和密码后，会点击此按钮。这将触发 clicked 信号，并调用 doLogin() 函数：

```
$widgets['main']['login_btn'] = &new GtkButton('Log in');
$widgets['main']['login_btn']->connect('clicked', 'doLogin');
```

接下来的几个函数调用将我们刚刚创建的小部件放入在函数开头创建的 GtkTable 实例中。这一切都是通过调用 GtkTable 的 attach() 方法完成的。该方法接受五到九个参数。第一个参数是我们要放入表格中的小部件。接下来的四个参数指定小部件在表格中的位置：

```
$widgets['main']['table']->attach($widgets['main']['label_name'],
0, 1,
0, 1);

$widgets['main']['table']->attach($widgets['main']['label_pass'],
0, 1,
2, 3);

$widgets['main']['table']->attach($widgets['main']['login_name'],
1, 2,
0, 1);

$widgets['main']['table']->attach($widgets['main']['login_pass'],
1, 2,
2, 3);

$widgets['main']['table']->attach($widgets['main']['login_btn'],
0, 2,
3, 4);
```

表格中子小部件的位置是相对于构成该小部件边界框的列线和行线来指定的。因此，对于我们在函数开头创建的表格，我们有 4 行和 2 列。这意味着我们有五条行线（编号 0-4）和两条列线（编号 0-2）。因此，在我们第一次调用 attach 时，我们将小部件水平放置在网格线 0 和 1 之间，垂直放置在网格线 0 和 1 之间，如下图所示：

![](img/9cf7789dba9b16ef3f8576d5aea89186_762_0.png)

最后，我们将表格添加到窗口中，并调用 show_all() 方法将其显示：

```
$windows['main']->add($widgets['main']['table']);
$windows['main']->show_all();
}
```

函数 loadSearchPage() 与 loadMainPage() 非常相似。与 loadMainPage() 一样，我们首先声明将在函数中使用的全局变量。这再次包括 $windows 和 $widgets 数组：

```
function loadSearchPage()
{
GLOBAL $windows;
GLOBAL $widgets;
```

与之前一样，我们接着创建一个窗口，设置其标题并连接其 destroy 信号。我们还创建一个具有五行两列的 GtkTable 来布局我们的小部件：

```
$windows['search'] = &new GtkWindow(GTK_WINDOW_TOPLEVEL);
$windows['search']->set_title("Online Library Application");
$windows['search']->connect("destroy", "destroyWnd");

$widgets['search']['table'] = &new GtkTable(5, 2, false);
```

接下来的代码部分创建用户用于指定搜索条件和查看结果的小部件。GtkCombo 是一个带有不同选项列表的下拉菜单。我们使用它来列出可用的不同图书系列，以及用户可能用于搜索的数据库列。我们在这里使用 GtkCList（列式列表）小部件来显示搜索结果。还需要注意的是，我们将 GtkButton 的 clicked 信号连接到我们的 performSearch() 函数，以便用户每次点击搜索时都会执行搜索：

```
$widgets['search']['label_search'] = &new GtkLabel("Search: ");
$widgets['search']['label_series'] = &new GtkLabel("Series: ");
$widgets['search']['label_by'] = &new GtkLabel("Search by: ");

$widgets['search']['search_txt'] = &new GtkEntry();

$series_array = array("Beginners", "Professional",
"Early Adopters");

$widgets['search']['search_series'] = &new GtkCombo();
$widgets['search']['search_series']->set_popdown_strings(
$series_array);

$by = array("ISBN", "Author Name", "Title");
$widgets['search']['search_by'] = &new GtkCombo();
$widgets['search']['search_by']->set_popdown_strings($by);

$widgets['search']['search_btn'] = &new GtkButton("Search");
$widgets['search']['search_btn']->connect("clicked", "performSearch");
$titles = array("Book Title", "Author", "ISBN",
"Series", "No Available", "Price");

$temp_entry = array("Results...", "", "", "", "", "");
$widgets['search']['result_list'] = &new GtkCList(6, $titles);
$widgets['search']['result_list']->prepend($temp_entry);
```

与之前一样，我们使用在函数开头创建的 GtkTable 实例来安排小部件的布局：

```
$widgets['search']['table']->attach(
$widgets['search']['label_search'],
0, 1,
0, 1);
$widgets['search']['table']->attach(
$widgets['search']['label_series'],
0, 1,
1, 2);
$widgets['search']['table']->attach(
$widgets['search']['label_by'],
0, 1,
2, 3);
$widgets['search']['table']->attach(
$widgets['search']['search_txt'],
1, 2,
0, 1);
$widgets['search']['table']->attach(
$widgets['search']['search_series'],
1, 2,
1, 2);
$widgets['search']['table']->attach(
$widgets['search']['search_by'],
1, 2,
2, 3);
$widgets['search']['table']->attach(
$widgets['search']['search_btn'],
0, 2,
3, 4);
$widgets['search']['table']->attach(
$widgets['search']['result_list'],
0, 2,
4, 5);
```

最后，我们将表格添加到窗口中，并调用 show_all() 方法将其显示：

```
$windows['search']->add($widgets['search']['table']);
$windows['search']->show_all();
}
```

与其他函数一样，我们将 $windows 和 $widgets 声明为全局变量，以便在该函数中访问之前创建的窗口和小部件：

```
function performSearch()
{
 GLOBAL $windows;
 GLOBAL $widgets;
}
```

我们需要从用户填写的表单中获取各种信息。首先，我们通过对 GtkEntry 实例调用 get_text() 方法来获取用户在搜索框中输入的文本。我们还需要知道用户从我们创建的两个下拉框中选择了什么。GtkCombo 的 entry 属性允许我们访问此内容；我们将此分配给一个临时变量，然后对其再次调用 get_text() 以从这两个下拉菜单中检索选定的文本：

```
$search_txt = $widgets['search']['search_txt']->get_text();
$series_entry = $widgets['search']['search_series']->entry;
$search_series = $series_entry->get_text();
$by_entry = $widgets['search']['search_by']->entry;
$search_by = $by_entry->get_text();
```

上面的最后 7 行创建了我们的 SQL 查询。首先，我们将构成 WHERE 子句的一部分 SQL 分配给变量 $search_by。然后，我们使用大量 LEFT JOIN 构造来创建其余的 SQL 查询，以选择我们需要的数据：

```
switch ($search_by) {
 case "ISBN":
 $search_field = 'title.ISBN = "' . $search_txt . "'";
 break;

 case "Author Name":
 $search_field = 'Author.auth_name LIKE "%" . $search_txt . "%"';
 break;

 case "Title":
 default:
 $search_field = 'title.book_title LIKE "%" . $search_txt . "%"';
 }

 $sql = 'SELECT title.book_title, details.ISBN, price, num_of_books, 
 'book_series, Author.auth_name FROM details LEFT JOIN title '
 'ON title.ISBN = details.ISBN LEFT JOIN series ON '
 'details.series_ID = series.series_ID LEFT JOIN AuthorTitle '
 'ON title.ISBN = AuthorTitle.ISBN LEFT JOIN Author ON '
 'AuthorTitle.auth_ID = Author.auth_ID WHERE ' . $search_field .
 " AND series.book_series LIKE "%" . $search_series . "%";
```

最后，在该函数中，我们执行查询，然后检查是否返回任何行。如果没有返回任何行，我们使用 clear() 方法清空结果框，然后在第一列添加文本“无结果”。如果有结果要显示，我们遍历每个结果，使用 append() 方法将其添加到 GtkCList 实例中，该方法接受一行的值数组：

```
$result = mysql_query($sql) or die(mysql_error());

if (!mysql_num_rows($result)) {
	$no_results = array("No Results.", "", "", "", "", "");
	$widgets['search']['result_list']->clear();
	$widgets['search']['result_list']->prepend($no_results);
} else {
	$widgets['search']['result_list']->clear();
	while ($row = mysql_fetch_array($result)) {
		$insert_array = array($row['book_title'],
			$row['auth_name'],
			$row['ISBN'], $row['book_series'],
			$row['num_of_books'],
			number_format($row['price'], 2));
		$widgets['search']['result_list']->append($insert_array);
	}
}
}
```

doLogin() 函数用于在用户在第一页点击“登录”时对用户进行身份验证。我们首先将四个变量设置为全局作用域：$windows 和 $widgets，以便我们可以访问已经创建的小部件；变量 $conn，用作 MySQL 链接标识符；以及 $disconnect_id。然后使用 $conn 来测试是否已经建立了到 MySQL 的连接。如果没有连接，我们创建一个连接并选择我们的数据库：

```
function doLogin()
{
	GLOBAL $windows;
	GLOBAL $widgets;
	GLOBAL $conn;
	GLOBAL $disconnect_id;

	if (!$conn) {
		$conn = mysql_connect('localhost', 'user', 'pass');
		mysql_select_db('library');
	}
}
```

然后我们再次使用 get_text() 方法从主窗口表单的两个 GtkEntry 框中检索用户名和密码：

```
$username = $widgets['main']['login_name']->get_text();
$password = $widgets['main']['login_pass']->get_text();
```

我们构建 SQL 查询并将其发送到 MySQL，将结果指针存储在 $result 变量中。然后我们断开主窗口的 destroy 信号处理程序。如果您记得，在 loadMainWindow() 中，我们将 $disconnect_id 的作用域设置为全局，就像在本函数开头所做的那样。这样做的原因是 disconnect() 方法接受一个参数，即 connect() 方法的返回值，我们使用 $disconnect_id 变量来存储此值。然后我们销毁主窗口。

最后，我们需要测试用户是否通过身份验证。我们检查结果，如果返回 true，我们则加载搜索页面。如果结果返回 false，我们退出程序，并将消息“身份验证失败”发送到控制台：

