```
<?php
require classes.php;

$c = new Category($category_id);

if(!$$c->delete_category()) {
    echo "Deletion Failed: $c->error";
} else {
    echo "Deletion Succeeded for:";
    echo "<ul>";
    <li>$c->category_name</li>
    <li>$c->category_description</li>
    <li>$c->category_id</li>
    echo "</ul>";
}

?>
```

As you can see this makes for a pretty clean page, which everyone is looking for ultimately.

# Inheritance

So far, we have worked with only one class. But one of the great advantages of object-oriented programming is that methods and properties from one class are inherited by another. We'll show a very quick example of this by writing a class called Product. Here's the shell:

```
class Product extends Category {
    var $product_id;
    var $product_name;
    var $product_price;
}
```

Notice the use of word extends. This tells PHP that all of the products and methods available in Category should be available in Product. If we wanted to call the delete_category() method from within the Product class, we could call it with $this->delete_category($category_id).