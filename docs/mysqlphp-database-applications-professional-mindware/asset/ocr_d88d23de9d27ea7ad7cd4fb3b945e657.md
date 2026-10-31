![](bbox=[0.16, 0.12, 0.24, 0.2])

PHPbuider has an excellent article on software that can help document classes: http://www.phpbuilder.com/columns/stefano20000824.php3.

# Objects in theory

For instance, if we were to tell you about a class named Category, we could just tell you the following:

**Class Category:**
Inherits Base

**Properties:**

+   - products

**Methods:**

+   - `LoadCategory`: Loads all of the columns for the categories table into object properties, based on a unique category_id. Products belonging to the category will be available as sub-objects.
+   - `SaveCategory`: Writes a new or updated category to the database.
+   - `FetchCategory`: Based on a unique category_id, assigns all columns for a row to properties.
+   - `DeleteCategory`: Removes a Category from the database based on a unique category_id.
+   - `PrintCategory`: Writes out a category to the browser.

Knowing this, and really nothing else, you could write a new script that displayed a category. The script below assumes that a category_id was passed through the querystring, or via a POST.

```
<?php
$c = new Category;
$c -> LoadCategory($category_id);
$c -> PrintCategory();
```

But if we left it at this, the learning experience would only be a fraction of what it should be. Of course we will go over the code in depth. But before we do, you should see how objects are constructed.