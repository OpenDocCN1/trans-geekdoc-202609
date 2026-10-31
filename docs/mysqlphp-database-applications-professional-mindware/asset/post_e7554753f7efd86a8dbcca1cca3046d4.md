
(items that describe the object) are variables. And methods (actions to be taken on the object) are functions. Let’s start with a simple class called Category.

![](img/de0823012275cf4ceebdb822a56e6b71_214_0.png)

> This is NOT the same set of classes used in the catalog application in Chapter 10. For instructive purposes, the code here has been simplified.

```php
class Category
{
    //here are the properties
    var $category_name;
    var $category_desc;
    var $category_id;
}
```

Here, at the start of this class, we defined the properties. Notice the use of var to declare each of the properties. You don’t need to declare properties elsewhere in PHP, but in classes you must. Now we’re going to create the first method.

```php
class Category
{
    //here are the properties
    var $category_name;
    var $category_desc;
    var $category_id;

    //gets all the properties for a given category_id
    function Category($category_id=0)
    {
        //expecting a category id when the object is
        //instantiated
        if ($category_id == 0)
        {
            return;
        }

        $query = "select category_name, category_desc from
            categories where category_id = $category_id";
        $result = mysql_query($query) or
            die(mysql_error());

        list($category_name, $category_desc) =
        mysql_fetch_array($result);
```

```php
$this->category_name=$category_name;
$this->category_desc=$category_desc;
$this->category_id=$category_id;
}
}
```

There are a few things here that require explanation. First, notice that the method (i.e., the function) has exactly the same name as the class. That tells PHP that this is the constructor. A constructor is automatically run as soon as a class is instantiated. The other thing to note is the use of $this->. It indicates a property or method within the current class. Above, we are assigning values to the properties: category_id, category_name, and category_description. If we wanted to call a method, we would indicate that with parenthesis: $this->method_call() or $this->method_call($value)

To continue with this example, we will add a method for deleting a category. Note that the method below assumes that the database contains two tables—one named categories and one named products—and that there is a one-to-many relationship between categories and products. Therefore, you would want to make sure that a category isn't deleted if it contains products.

```php
class Category
{
//all the stuff you saw above goes here

    function delete_category($category_id=0)
    {
        //make sure a category_id was defined in the
        //constructor or is indicated explicitly
        if($category_id == 0 && empty($this->category_id))
        {
            $this->error = "Nothing to delete";
            return FALSE;
        }
        //create where clause with the category_id
        //retrieved from the proper place
        if ($category_id !=0)
        {
            $where_clause = "where category_id = 
                $category_id";
        }
        else
        {
            $where_clause = "where category_id = 
                $this->category_id";
        }
```

```
//make sure there are no products left for this
//category
$query = "select * from products  $where_clause";
$result = mysql_query($query) or
    die(mysql_error());
if (mysql_num_rows($result)>0)
{
    $this->error = "There are
still products for this category";
    return FALSE;
}
$query="delete from categories $where_clause";
$result = mysql_query($query) or
    die(mysql_error());
if(mysql_affected_rows() == 0)
{
    $this->error = "There were no rows to delete";
    return FALSE;
}
return TRUE;
}
```

We now have a class with two methods, the constructor and delete_category, and three properties. Now it is time to put this class to work.

## Instantiating an object

Instantiating basically means “creating.” Let’s say we have a PHP page that is intended to delete categories. To make this work with the above class, we need to do a few things. First, we need to include the file containing the class.

```
require "classes.php";
```

Next we have to create an instance of the object. We can do this with the keyword new:

```
$c = new Category;
```

Now, using the object $c, we can access any of the properties or methods using the same syntax seen in the previous example: $c-> property or $c->method().

Now we want to put together a page that actually removes a record from the database. For the sake of this example, assume that a single $category_id has been passed via the querystring.

```
<?

require "classes.php";

$c = new Category($category_id);

if(!$c->delete_category())
{
    echo "Deletion Failed: $c->error";
}
else
{
    echo "Deletion Succeeded for:";
    echo "<ul>
        <li>$c->category_name
        <li>$c->category_description
        <li>$c->category_id
    </ul>
    ";
}
?>
```

As you can see this makes for a pretty clean page, which everyone is looking for ultimately.

## Inheritance

So far, we have worked with only one class. But one of the great advantages of object-oriented programming is that methods and properties from one class are inherited by another. We'll show a very quick example of this by writing a class called Product. Here's the shell:

```
class Product extends Category
{
    var $product_id;
    var $product_name;
    var $product_price;
}
```

Notice the use of the word extends. This tells PHP that all of the products and methods available in Category should be available in Product. If we wanted to call the delete_category() method from within the Product class, we could call it with $this->delete_category($category_id).

![](img/de0823012275cf4ceebdb822a56e6b71_218_0.png)

In PHP, constructor methods of parent classes are not automatically run when the child class is called. For example, calling $p = new Product will not run the Category() method.

Now we'll add a quick constructor method:

```php
class Product extends Category
{
    var $product_id;
    var $product_name;
    var $product_price;

    function Product($product_id=0)
    {
        //expecting a product_id to be passed
        if ($product_id ==0)
        {
            return FALSE;
        }

        $query = "select product_name, product_desc,
product_price, category_id from
products where product_id = $product_id";

        $result = mysql_query($query);
        list($this->product_name, $this->product_desc,
$this->product_price) =
mysql_fetch_array($result)
;
        $this->Category($category_id);
    }
}
```

Notice that this method not only assigns values to the properties for this product, it also calls the constructor of the Category class, which then assigns values to those properties. Note that because of inheritance, we could write a script as follows:

```php
require 'classes.php';

$p = new Product($product_id);
echo $p->category_name;
```

You see that the properties of Category are available to the Product object.

## Object-Oriented Code versus Procedural Code

Here’s the million-dollar question: In your applications, should you use object-oriented code or procedural code? This is another topic that inspires religious debate. But really there is no need for that because there is a correct answer: It depends. If you have an extensive background in object-oriented programming, and you are more comfortable coding classes, do that. However, if you dislike the way object-oriented code works, use only functions.

![](img/de0823012275cf4ceebdb822a56e6b71_219_0.png)

There are a few large class libraries on the included CD-ROM, including some taken from Manual Lemos’ impressive site http://phpclasses.upperdesign.com. His form creation and validation class is truly epic, but it may be a bit unwieldy for some.

Object-oriented code comes with a couple of advantages and disadvantages. Weigh them and decide for yourself if you should use classes or just functions.

Advantages:

- You can save time using the object-oriented approach.
- You can make highly reusable pieces of code.
- You can make use of extensive class libraries available for free on the Web.

Disadvantages:

- It’s slower than the procedural approach.
- The syntax can be confusing at first.
- Web programming does not make use of many of the advantages of object-oriented code.
- If you’re using very large class libraries, there may be a performance hit.

## Comments

In any programming language, comments are essential—not only to you as you’re writing the code, but to those who come to the code after you. What may be crystal-clear to you may be absolutely unreadable to others. Or, if you’ve had to do something particularly complex, you might find that you don’t even understand
