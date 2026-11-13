PHP 5 also has a new feature that gives objects a bit of an advantage over functions. You can create a function named `__autoload ()` that PHP calls whenever you reference a class that you have not yet declared. This function can then include the file that declares that class. What this means is that you don't have to include a whole raft of class declarations just because you might use them in your script. Neither do you have to do the bug-prone work of spreading the `include` statements throughout your code. We use the `__autoload()` feature in these examples, but files that include the class definitions, like the preceding one, are included in a commented-out version as well – you can use them if you wish.

# BASE

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