
This is more complex than the equivalent SQL, but it’s worth using here to avoid fetching a full database result each time a page link is clicked.

5. Scroll to the bottom of the page, and add a PHP block below the closing `</html>` tag to end the `try` block and add a `catch` block:

</html>  

**<?php**  

**} catch (Exception $e) {**  

**  echo $e->getMessage();**  

**}**  

**?>**

6. Scroll back to the top of the page, and add the code for the paginator inside the first PHP block:

```php
$paginator = Zend\Paginator::factory(@@Result@@);
if (isset($_GET['page'])) {
    $paginator->setCurrentPageNumber($_GET['page']);
}
$paginator->setItemCountPerPage(@@Items Per Page@@);
$paginator->setPageRange(@@Pages in Range@@);
```

This passes `$places` to the `Zend_Paginator` static `factory()` method and sets the paginator’s basic settings. The number of items per page is deliberately low to show how the paginator works. As long as you have at least three records in the `places` table, it will display the results across multiple pages.

7. Wrap the second table row in a `foreach` loop, assigning `$paginator` to the temporary variable `$row`, and use `echo` to display the values of the `state_name` and `name` columns in the first two table cells like this:

```php
<?php foreach($paginator as $row) { // paginator repeat region ?>
<tr>  
    <td><?php echo $row['state_name']; ?></td>  
    <td><?php echo $row['name']; ?></td>  
    <td>EDIT</td>  
    <td>DELETE</td>  
</tr>  
<?php } // end of paginator repeat region ?>
```

### ![image](graphics/tip.jpg)TIP:

When using `echo` to insert a brief snippet of code in HTML, use the echo icon ![image](graphics/echo.jpg) in the PHP category of the Insert panel/bar.

Although `$paginator` is an object that contains a database result, you can loop through it with `foreach` as if it were an ordinary array.

8. Save list_places.php, and click Live View to test your code so far. Depending on what’s in your database, your page should look similar to this:

![image](graphics/fig11_06.jpg)

You can compare your code with list_places_01.php in lesson11/completed.

9. Exit Live View, and select the EDIT text in the third cell. Create a link to update_place.php. Select the DELETE text, and create a link to delete_place.php.

10. You need to add a query string to each link. Click in Code view to position the insertion point before the closing quotation mark of the `href` attribute, and type **?place_id=**. Then use the echo icon to add **$row['place_id']**. The EDIT link should look like this:

<a href="update_place.php?place_id=<?php echo $row['place_id']; ?>"> EDIT</a>

Do the same for the DELETE link.

11. Add a paragraph between the closing `</table>` and `</body>` tags, and create the navigation links for the paginator like this:

```php
<p>  
<?php  
$pages = $paginator->getPages('Elastic');  
if (isset($pages->previous)) {  
    echo '<a href="' . $_SERVER['PHP_SELF'] . '?page=' . $pages->previous . '">Prev</a>';  
}  
foreach ($pages->pagesInRange as $page) {  
    if ($page != $pages->current) {  
        echo " <a href='". $_SERVER['PHP_SELF'] . "?page={$page}'>{$page}</a>";  
    } else {  
        echo ' ' . $page;  
    }  
}  
if (isset($pages->next)) {  
    echo ' <a href="'. $_SERVER['PHP_SELF'] . '?page=' . $pages->next . '">Next</a>';  
}  
?>  
</p>
```

The first line of code inside the PHP block uses the `getPages()` method to get an array of the pages needed to display the other database results and selects the Elastic scrolling method. The array is stored as `$pages`.

The next line checks whether `$pages` has a `previous` property (see [Table 11.1](#ch11.html#ch11tab1)). If it does, a link to the previous page is created. The link is built from `$_SERVER[‘PHP_SELF’]`, which contains the URL of the current page, followed by a query string that uses the `previous` property to insert the correct page number. For example, if the current page is the third in the navigation sequence, it creates a link to page 2. If the current page is the first in the sequence, no link is created.

The center section of links is created by a `foreach` loop that uses the array stored in the `pagesInRange` property and assigns each element temporarily to `$page`. Inside the loop, a link is created for each page in the range except the current one. The current page number is displayed as plain text.

The final section of the code checks the `next` property and creates a text link to it if necessary.

### ![image](graphics/caution.jpg)CAUTION!

When copying this code, pay careful attention to the mixture of single and double quotation marks. Also, note that the strings include a space before each link except the first one.

12. Save the page, and click Live View to test it. You should see a set of navigation links below the table. The number of links depends on how many records you inserted in the `places` table.

![image](graphics/fig11_07.jpg)

13. Hold down Ctrl/Cmd and click the Next link. You should be taken to the second set of results, and a Prev link should appear at the start of the row.

![image](graphics/fig11_08.jpg)

You can compare your code with list_places_02.php in lesson11/completed.

#### Converting the paginator into a server behavior

`Zend_Paginator` involves code in different parts of the page, but that’s not a barrier to converting it to a server behavior. This is how you do it:

1. Exit Live View, if necessary, and copy the PHP code from step 11 in the previous section to a plain text editor. You need to paste two sections of code into the Server Behavior Builder dialog box, so it’s more convenient to have the second section saved temporarily outside Dreamweaver.

2. Copy to your clipboard the code from step 6 in the previous section, click the plus button in the Server Behaviors panel, and choose New Server Behavior.

3. In the New Server Behavior dialog box, type **Zend Paginator** in the Name field, and click OK.

4. Click the plus button next to “Code blocks to insert,” and click OK to accept the suggested name.

5. Paste the code from step 6 of the previous section into the “Code block” text area, and amend it to convert some of the original values to server behavior parameters. The edited code should look like this:

```php
<?php  

$paginator = Zend\Paginator::factory(@@Result@@);  

if (isset($_GET['page'])) {  

    $paginator->setCurrentPageNumber($_GET['page']);  

}  

$paginator->setItemCountPerPage(@@Items Per Page@@);  

$paginator->setPageRange(@@Pages in Range@@);  

?>
```

6. Leave the “Insert code” and “Relative position” menus at their default settings.

7. Click the plus button next to “Code blocks to insert,” and click OK to accept the suggested name.

8. Replace the placeholder text in the “Code block” text area with the following:

```php
<?php **foreach($paginator as $row) { // paginator repeat region** ?>
```

9. Set the “Insert code” menu to Relative to the Selection and the “Relative position” menu to Before the Selection.

10. Click the plus button to insert another code block.

11. Replace the placeholder text in the “Code block” text area with a closing curly brace and inline comment:

```php
<?php **} // end of paginator repeat region** ?>
```

### ![image](graphics/note.jpg)NOTE:

The comments after the curly braces in steps 8 and 11 are essential to prevent Dreamweaver from mistaking other loops as part of this server behavior. If you omit them, Dreamweaver incorrectly lists Zend Paginator in the Server Behaviors panel on any page that uses a closing curly brace on its own.

12. Set the “Insert code” menu to Relative to the Selection and the “Relative position” menu to After the Selection.
