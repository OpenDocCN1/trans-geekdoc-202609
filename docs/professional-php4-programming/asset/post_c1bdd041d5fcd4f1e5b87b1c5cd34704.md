
The final widget we create for our window is a GtkButton with the text Log in on it. We connect the clicked signal for this button to the doLogin() function. The user will click this button when they have filled in the username and password. This causes the clicked signal to be emitted, and the doLogin() function is called:

```
$widgets['main']['login_btn'] = &new GtkButton('Log in');
$widgets['main']['login_btn']->connect('clicked', 'doLogin');
```

The next few function calls place the widgets we just created into the instance of GtkTable we created at the beginning of the function. This is all done by calling the attach() method of GtkTable. This method accepts between five and nine arguments. The first parameter is the widget we want to place into the table. The next four parameters specify where in the table the widget will be placed:

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

The position of the child widget within a table is specified in relation to column and row lines that make up the bounding box for that widget. So for the table we created at the beginning of the function we have 4 rows and 2 columns. This means we have five row lines (numbered 0-4) and two column lines (numbered 0-2). So in our first call to attach we are placing our widget between grid lines 0 and 1 horizontally, and between grid lines 0 and 1 vertically as shown in the diagram below:

![](img/9cf7789dba9b16ef3f8576d5aea89186_762_0.png)

Finally we add the table to the window and call the show_all() method to display it:

```
$windows['main']->add($widgets['main']['table']);
$windows['main']->show_all();
}
```

The function loadSearchPage() is very similar to loadMainPage(). We start, as with loadMainPage(), by declaring the globals that we will use within the function. Once again this consists of the $windows and $widgets arrays:

```
function loadSearchPage()
{
GLOBAL $windows;
GLOBAL $widgets;
```

As before, we then create a window, set its title and connect its destroy signal. We also create a GtkTable with five rows and two columns to layout our widgets:

```
$windows['search'] = &new GtkWindow(GTK_WINDOW_TOPLEVEL);
$windows['search']->set_title("Online Library Application");
$windows['search']->connect("destroy", "destroyWnd");

$widgets['search']['table'] = &new GtkTable(5, 2, false);
```

The next section of code creates the widgets that will be used by the user to specify the search criteria and view the results. GtkCombo is a drop down menu with a list of different options to choose from. We use this to list the different series of books available, and also the database columns the user might perform the search on. We use the GtkCList (columned list) widget here to display the results from the search. One other thing to note here is that we connect the GtkButton's clicked signal to our performSearch() function, so that a search is performed whenever the user clicks on search:

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

Once again we use the instance of GtkTable we created at the beginning of the function to arrange the layout of the widgets:

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

Finally, we add the table to the window and call the show_all() method to display it:

```
$windows['search']->add($widgets['search']['table']);
$windows['search']->show_all();
}
```

As with the other functions we declare $windows and $widgets as global so that we can access the windows and widgets we created before in this function:

```
function performSearch()
{
 GLOBAL $windows;
 GLOBAL $widgets;
}
```

We need to fetch various pieces of information from the form the user filled out. Firstly we get the text the user entered into the search box by calling the get_text() method on the instance of GtkEntry. We also need to know what the user selected from the two drop-down boxes we created. The entry property of GtkCombo allows us to access this; we assign this to a temporary variable, which we then also call get_text() on to retrieve the selected text from these two drop-down menus:

```
$search_txt = $widgets['search']['search_txt']->get_text();
$series_entry = $widgets['search']['search_series']->entry;
$search_series = $series_entry->get_text();
$by_entry = $widgets['search']['search_by']->entry;
$search_by = $by_entry->get_text();
```

The last 7 lines above create our SQL query. Firstly we assign to the variable $search_by a portion of the SQL that will make up our WHERE clause. We then create the rest of our SQL query using a host of LEFT JOIN constructions to select the data that we need:

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

Finally, in this function we perform the query and then check if any rows are returned. If there are no rows returned we clear the results box using the clear() method and then add the text No Results to the first column. If there are results to be shown we iterate through each result, adding it to the instance of GtkCList using the append() method which accepts an array of values for the row:

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

The doLogin() function is used to authenticate users when they click Log in on the first page. We start by setting four variables to global scope; $windows and $widgets so that we can access the widgets we have already created, the variable $conn, which is used as the MySQL link identifier, and $disconnect_id. $conn is then used to test whether a connection to MySQL has already been made. If there is no connection, we create one and select our database:

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

We then retrieve the username and password from the two GtkEntry boxes on the main window form, once again using the get_text() method:

```
$username = $widgets['main']['login_name']->get_text();
$password = $widgets['main']['login_pass']->get_text();
```

We construct our SQL query and send it to MySQL, storing the results pointer in the $result variable. We then disconnect the main window's destroy signal handler. If you remember, in loadMainWindow() we set the scope of $disconnect_id to global as we did at the beginning of this function. The reason for this is that the disconnect() method takes a single argument, which is the return value of the connect() method, and we used the $disconnect_id variable to store this. We then destroy our main window.

Finally, we need to test whether the user was authenticated or not. We check our result, and if it returned true we then load the search page. If the result returned false we exit the program, sending the message Authentication failed to the console:
