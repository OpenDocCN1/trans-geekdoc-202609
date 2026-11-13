Notice that near the end, the return value is forced TRUE. This is for testing purposes. In reality, your authorization house returns a value for auth_result that determines whether the function returns TRUE or FALSE.

# Scripts

These are the pages called by URLs and the includes. You will probably notice that not much is involved here. Almost all the work is done in the classes. These scripts are concerned more with presentation of data and ways of manipulating them – as they should be, because such a design makes it more likely that you'll be able to reuse the classes somewhere else someday.

# DISPLAY.PHP

This prints out either a list of categories or a specific product:

```
<?php
require_once('header.php');

$product_id = (int)array_key_value($_REQUEST,'product_id',0);
$submit = (string)array_key_value($_POST, 'submit');
$again = (string)array_key_value($_POST, 'again');

$p = new Product(array('product_id'=>$product_id));

if (empty($p->product_id))
{
    $p->description = "Here at Bag'O'Stuff, we've got so much stuff
    we don't know what to do with it. So buy some and help us clear out
    some space.";
    $p->product = "What've We Got?";
}
else
{
    $p->fetch_from_db();
}

// begin constructing the page title with a link to the main page
// of the catalog

// add a link back to the product level to the page title,
// followed by the name of this product, and print out the
// top of the page

$page_title = anchor_tag('index.php', "Bag'O'Stuff");
foreach ($p->parents() as $t)
{
```