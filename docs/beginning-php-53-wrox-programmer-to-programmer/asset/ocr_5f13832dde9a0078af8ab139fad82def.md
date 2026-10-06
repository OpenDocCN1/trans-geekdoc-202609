# Chapter 13: Retrieving Data from MySQL PHP

```
$conn = "*";
}
?
```

So how does this class work? First of all, the script includes the config.php file so that it can access the database configuration:

```
require_once "config.php";
```

The PHP require_once() function imports another PHP script into the current script in a similar way to require(), which you've used in previous chapters. The difference is that require_once ensures that the file is imported only once. This is important if you create a large application with script files, many of which need to include the same name, such as config.php. If you used require(), the PHP engine would include config.php every time it encountered the require() function call, resulting in multiple copies of the config.php file being included in the application (with, needless to say, chaotic results).

Find out more require_once() and related functions in Chapter 20.

Next, the class declares a protected $data array to hold the record's data. The fact that it's protected means that the class derived from this will be able to use it, but it's still hidden from the outside (as most properties should be).

The first method, __construct(), is the class's constructor. It's called whenever a new object is created based on a class that is derived from this class. The constructor accepts an associative array of field names and values ($data) and stores them in the protected $data array (assuming each field name exists in $data). In this it's possible for outside code to create fully populated data objects.

The getValue() method accepts a field name, looks up that in the object's $data array and returns its value. If the field name wasn't found, the method halts execution with an error message. getValue() enables outside code to access the data stored in the object.

getValueEncoded() is a convenience method that allows outside code to retrieve a field value that has been passed through PHP htmlspecialchars(). This function encodes markup characters as &amp; &lt; and &gt;. Not only is this required when generating XHTML markup, but it's also a good security measure that can help reduce the risk of malicious markup injecting into your Web page.

The final two protected functions allow to create a PDO connection to the database, as connect() creates a new PDO object and returns it to the calling code. Along the way, it sets a collection of useful attributes:

```
$conn->setAttribute(PDO::ATTR_PERSISTENT, true);
$conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

Setting the PDO::ATTR_PERSISTENT attribute allows PHP to keep the MySQL connection open for reuse by other parts of the application (or other applications). With this set to false, the default setting, a new MySQL connection is created every time a new PDO object is created in the application. Because setting up a MySQL connection takes both time and resources, setting this attribute to true can help improve performance.

389