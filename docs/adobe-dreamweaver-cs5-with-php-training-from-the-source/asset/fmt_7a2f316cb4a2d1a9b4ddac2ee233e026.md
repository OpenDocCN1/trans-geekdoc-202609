
**8** Immediately following the `<style>` block is the following code:

``` 
<script type="text/xml">  

<!--  

<oa:widgets>  

  <oa:widget wid="2127022" binding="#gallery" />  

</oa:widgets>  

\-->  

</script>  
```  

Again, the purpose is to identify the widget and its related code.

**9.** Inside the `<body>` of the page, locate the section of code that begins like this (around lines 78–86):

<div id="gallery" class="lbGallery">

This is the HTML code that contains the thumbnails. It’s an unordered list restyled by the widget’s CSS.

**10** Immediately after the gallery `<div>` is a `<script>` block (around lines 87–107) that initializes the Ajax gallery. Again, it contains comments that identify the widget number and its ID.

Even if you don’t understand the JavaScript code, it’s easy to see that it contains the paths to the widget’s loading, previous, and next buttons. You should also be able to recognize the values set for opacity (`0.6`) and background color (`#cccccc`) in the IMAGE CONTAINER BOX section of the Widget Browser.

All the changes you made in the Widget Browser have been added to the page where the widget is used but not to any of the external files.

If you mouse over the widget in Design view and select the turquoise tab at the top left of the widget, you can remove the widget and its associated files from the page by pressing Delete. For this exercise, you don’t want to delete the widget unless you inserted it in the wrong part of the page.

#### **Populating the gallery widget dynamically**

The gallery widget uses hard-coded links to the full size images and thumbnails, but since the details of the images are stored in a database, it makes more sense to query the database and use a PHP loop to generate the links dynamically. By adding a `<select>` menu, visitors can select a state and control which images are displayed. The following steps explain how:

**1** Include db\_definitions.php and library.php above the `DOCTYPE` declaration in gallery.php using `require_once()`, and open a `try` block like this:

```php
<?php
require_once('scripts/library.php');
require_once('scripts/db_definitions.php');
try {
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
```

**2.** Scroll down to the bottom of the page. Close the `try` block and add a `catch` block after the closing `</html>` tag:

</html>  

```php
<?php
} catch (Exception $e) {
    echo $e->getMessage();
}
?>
```

**3.** In Design view, move your pointer over the gallery widget, and click the turquoise tab at the top left to select it. You’ll insert a form and `<select>` menu above the widget, so the insertion point needs to be immediately before the widget’s opening `<div>` tag.

Press the left keyboard arrow once. This is the same technique you used in step 2 of the preceding section.

In Design view, the cursor looks as though it’s still inside the widget, but you can confirm the insertion point’s location in Split view. Don’t move the focus into Code view, because inserting form elements is easier in Design view.

**4.** Choose Insert > Form > Form. The red outline of the form appears above the widget and the `<h2>` heading in Design view.

**5.** The `<select>` menu will pass the selected state name through a query string, so the form needs to use the `GET` method. With the form still selected, change the value of Method in the Property inspector to **GET**.

![Image](graphics/fig12_13.jpg)

**6.** Make sure the insertion point is inside the form, and choose Insert > Form > Select (List/Menu).

In the Input Tag Accessibility Attributes dialog box, type **state** in the ID field and **Select a state:** in the Label field. Click OK.

**7.** Click to the right of the `<select>` menu you just inserted and choose Insert > Form > Button.

In the Input Tag Accessibility Attributes dialog box, type **selectState** in the ID field, and leave the Label field blank. Click OK.

**8.** With the button still selected, change the Value field in the Property inspector from Submit to **Go**. The form should look like this in Design view (don’t worry if the thumbnails still show broken image icons):

![Image](graphics/fig12_14.jpg)

If you need to check your code so far, compare it with gallery_01.php in lesson12/completed.

**9.** In [Lesson 10](#ch10.html#ch10), you created a function in db_definitions.php to populate a `<select>` menu with the names of all states. However, not all states have places and photos associated with them in the database, so you need to create a different function to select only those states that do.

Select db_definitions.php in the Related Files toolbar, and add the following function definition:

function getRegisteredStates($read) {  

    $sql = 'SELECT DISTINCT state_name FROM states  

        INNER JOIN places USING (state_id)  

        ORDER BY state_name';  

    return $read->fetchCol($sql);  

}

The `SELECT` query uses an `INNER` `JOIN` between the `states` and `places` tables. An `INNER` `JOIN` selects only records that have matches in both tables, so this query excludes states that don’t have photos or places associated with them. However, there are 11 records in the `places` table, so using `SELECT` on its own would produce duplicate results. The `DISTINCT` keyword ensures only one instance of each `state_name` is retrieved.

The final line of the function uses `fetchCol()`, a `Zend_Db` method you’ve not encountered before. It returns an indexed array of results from the first column in the `SELECT` query. Since the query selects only the `state_name` column, this makes it a lot simpler to loop through the results.

**10** You also need a function to retrieve the image filenames, captions, and associated place names to populate the gallery widget. Add the following code to db_definitions.php:

function getGalleryByState($read, $state_name) {  

    $sql = $read->quoteInto('SELECT name, filename, caption  

        FROM places  

        INNER JOIN states USING (state_id)  

        INNER JOIN place2photo USING (place_id)  

        INNER JOIN photos USING (photo_id)  

        WHERE state_name = ?  

        ORDER BY name', $state_name);  

    return $read->fetchAll($sql);  

}

This function takes two arguments: the `Zend_Db` object with read permission and the state name. Because the state name is passed through the query string, the SQL query needs to use the `quoteInto()` method to sanitize the value (see “Using a variable in a SELECT query” in [Lesson 7](#ch07.html#ch07)).

The query joins all four tables in the CMS with `INNER` `JOIN`, using the foreign keys to identify related records.

**11** Save db_definitions.php, and click Source Code in the Related Files toolbar to return to the code in gallery.php.

Add the following code in the `try` block above the `DOCTYPE` declaration:

try {  

    **$states = getRegisteredStates($dbRead);**  

    **if (isset($_GET['state']) && in_array($_GET['state'], $states)) {**  

        **$selected = $_GET['state'];**  

    } else {**  

        **$selected = 'California';**  

    }**  

    **$pix = getGalleryByState($dbRead, $selected);**  

}**

**12** Amend the page’s `<title>` by displaying the name of the selected state:

<title>Destinations West: **<?php echo $selected; ?>**</title>
