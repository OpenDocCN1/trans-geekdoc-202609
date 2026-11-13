
## Uploading files

This is the first application that enables users to upload files; specifically, the administrators of the catalog need to be able to upload images of their products. Uploading files is easy enough in PHP, but before you understand how the upload works you need to know how PHP handles uploaded files.

In your HTML page you have a form like the following:

```
<form action="admin_product.php" method="post"
enctype="multipart/form-data" >
<input type="file" name="imagefile">
</form>
```

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_454_0.png)

When you allow file uploads, you open yourself up to denial-of-service (DoS) attacks. If you're not careful, someone could send many multi-megabyte files to your system simultaneously, which could bring your machine to a crashing halt. There are two things you can do about this. The first is to put a hidden form field before your `<INPUT TYPE="file">` tag. The hidden field should look like this:

```
<INPUT TYPE="hidden" name="MAX_FILE_SIZE" value="1000">
```

where value indicates the maximum size allowed, in bytes. This is a reasonable first step and can be of help in stopping someone who didn't know you have a size limit. However, this measure will not stop anyone with stronger malicious intent. All that person has to do is look at the source code of your page and make the needed changes.

The other security measure has to do with altering the php.ini file, which contains the upload_max_filesize item. If you have access to your php.ini, you can set the value of this item to a number that you think is reasonable. (By default php.ini will allow 2MB uploads.) By making the change in the php.ini file you prevent the attacker from altering it.

When a file is specified and this form is submitted, PHP automatically creates a few variables. They are as follows:

- $_FILES[yourfieldname][tmp_name] – The name of the file as stored in the temporary directory on the server
- $_FILES[yourfieldname][name] – The name of the file as it was on the user's machine
- $_FILES[yourfieldname][size] – The size of the file, in bytes
- $_FILES[yourfieldname][type] – The MIME type, in this case image/gif, image/png, or image/jpg (if it was provided by the browser)

The image is stored in the temp directory specified in the php.ini file; if no temp directory is specified in php.ini, the operating system's default temporary directory is used.

> The Paths and Directories category of php.ini controls many of the file-upload options.

## Code Breakdown

In OO coding, good documentation is your best friend because, as has already been stated, it almost shouldn’t matter how the classes you are using accomplish their tasks. You just need to know that they work.

> PHPBuilder has an excellent article on software that can help document classes: http://www.phpbuilder.com/columns/stefano20000824.php3.

## Objects in theory

For example, if we were to tell you about a class named Product, we could just tell you the following:

Class Product:

Inherits CatalogBase

### Properties

- product_id
- product
- description

### Methods

- fetch_from_db: Retrieve all data about this product from the database
- write_to_db: Write a new or updated product record to the database
- delete_from_db: Remove a product from the database
- print: Display a product to the browser

Knowing this information, and really nothing else, you could write a new script that displayed a product. The script that follows assumes that a product_id was passed through the querystring or via a POST.

```
$p = new Product(array('product_id'=>$product_id));
$p->fetch_from_db();
$p->print();
```

But if we left it at this, your learning experience would be only a fraction of what it should be. Of course, in the next section, we go over the code in depth. For one thing, in this application the display of an object is left to the user of the object—we use regular functions, rather than having a print method in each object.

## Classes

We designed the classes in this application so that most of them look and behave similarly. As you look at the classes, you should notice that all but the Base class have methods with similar names. Our hope is that once you understand one class, the workings of the others will be pretty clear. For this reason, we're only going to break down two classes in this chapter. Note that the each method in each class is extensively commented on the CD. If you have a specific question as to the working of a snippet of code, you will likely find the answer within the comments.

In the following pages we break down code in the following classes: Base and Product. For the other classes we describe only how to use the methods and properties. But once you understand the Product class, the other classes should be easy enough to figure out.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_456_0.png)

Please be sure that you have mastered the concepts in Chapter 7 before reading this section.

Breaking the classes into includes also enables you to selectively reuse specific classes when you need them. This becomes important in Chapter 14, when we reuse some of these classes in creating the shopping cart.

PHP 5 also has a new feature that gives objects a bit of an advantage over functions. You can create a function named `__autoload()` that PHP calls whenever you reference a class that you have not yet declared. This function can then include the file that declares that class. What this means is that you don't have to include a whole raft of class declarations just because you might use them in your script. Neither do you have to do the bug-prone work of spreading the `include` statements throughout your code. We use the `__autoload()` feature in these examples, but files that include the class definitions, like the preceding one, are included in a commented-out version as well – you can use them if you wish.

## BASE

There is usually a base class on which your other classes are built (though it's not always named `Base`). In this application `Base` contains a set of utilities that all of the other classes make use of. The class is declared with the following statement:

```
class Base
{
```

Next you declare a couple of constants used by methods of the class. They're not exactly the most original or purposeful constants you'll ever see, but are mostly here as examples:

```
const ON = TRUE;
const OFF = FALSE;
```

Now on to the properties. Most of the classes are built to handle reading, writing, and manipulating data pertaining to a single table in a database. Those common functions are what the `Base` class is built to handle, and its properties show that:

```
var $table = NULL;
var $idfield = NULL;
var $id = NULL;
var $what = NULL;
var $fields = NULL;
var $appname = 'test';

var $error = NULL;
```

The properties are all assigned values of `NULL` in `Base` because it's up to each child class to fill them in with the values specific to the table it will be handling. For example, the `Product` class sets the `$table` property to `products` and the `$idfield` property to `property_id`.

The $appname property is typically set in the base class of an application – in this example, CatalogBase – because it’s what you use to determine what database to use when connecting to MySQL.

### __construct()

In earlier versions of PHP a class’s constructor method–the method that is run every time you instantiate a new object of that class–had to be given the same name as the class itself. In PHP 5 constructor methods can all be given the same name, __construct(). Here you are taking any arguments passed into the class in a new Classname() statement and handing them off to the build() method, and then setting up the $idfield and $id properties and connecting to the database:

```
function __construct()
{
    $args = func_get_args();
    call_user_func_array(array($this,'build'), $args);
    if (!empty($this->idfield))
    {
    $f = $this->idfield;
    $this->id =& $this->$f;
    }
    if ($this->table != null)
    $this->dbh();
}
```

### dbh()

This method shows the use of static variables in methods. As with regular functions, a static variable retains its value from one call to the next. In the context of a class method, what that means is that two objects of the same class–or of classes that inherit the same class–make use of the same single static value. This makes good sense for something like a database connection, as shown in the following code. If you have four objects in your script, after all, they’re all still talking to the same database (probably), and so they need only the one connection.

```
function dbh()
{
    static $dbh = NULL;
    if ($dbh == NULL)
    {
    $dbh = db_connect($this->appname);
    if ($dbh == NULL)
    {
    user_error(
    'Received NULL db connection'
    , E_USER_ERROR
    );
}
```
