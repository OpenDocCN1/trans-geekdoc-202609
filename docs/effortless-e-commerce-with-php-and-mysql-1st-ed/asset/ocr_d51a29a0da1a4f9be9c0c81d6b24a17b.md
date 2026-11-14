As long as some rows were returned, the view file (which will display the results) will be included. There are two different view files: one for non-coffee products and one for coffee products.

+   9. If no records were returned, include the “no products” view:

```
} else {
include ('./views/noproducts.html');
}
```

This will be a new view file, which neither indicates an error nor attempts to list any products, because there aren’t any.

+   10. Complete the PHP page:

```
include ('./includes/footer.html');
?>
```

+   11. Save the file.

# Creating the View Files

The browse.php script uses three new files: list_products.html, list_coffees.html, and noproducts.html. There are two different products-listing files because the customer will buy a category of coffee in a specific format (based upon the size, caffeine, and bean type, see Figure 8.4) but will purchase other products individually (Figure 8.6). For each product type, the page should display general information about the category as a whole; hence, each view uses a trick to show that information only once.

# CREATING THE PRODUCTS LIST

This view file should first show the general category information, then each specific product. It will create two HTML boxes (from the original template) to do so (again, see Figure 8.6).

+   1. Create a new HTML file in your text editor or IDE to be named list_products.html and stored in the views folder.

+   2. Begin by creating a flag variable:

```
<?php
$sheader = false;
?>
```

This variable will be used to know whether or not the initial information has been printed (so that it’s only printed once). By default, the value is false.