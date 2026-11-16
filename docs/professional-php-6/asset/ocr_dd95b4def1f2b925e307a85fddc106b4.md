# # Executing Queries

So far, you’ve learned how to connect and disconnect using the PDO driver, and you should understand how to pass connection parameters to customize your connection.

Now you can see how to execute a simple query using your instantiated PDO object. The following snippet of code should be inserted between your simple connection and disconnection code:

```
// Let's interrogate the database
$i = 0;
$strQuery = "SELECT * FROM `\\user\\`";
$objStatement = $objPDO->query($strQuery);
foreach ($objStatement as $arRow) {
    print "Row $i<br />\n";
    foreach ($arRow as $key => $value) {
        if (!is_numeric($key)) print " - Column $key, value
        $value<br />\n";
    };
    $i++;
};
```

If all goes well, then you should be able to see exactly the same output you generated earlier in the chapter using procedural database connectivity.

It’s worth taking a little time to understand what’s happening here. It will make your life considerably easier when you get into the more advanced material later in this chapter.

The query() method of the PDO class quickly and “unfussily” executes the query specified and returns an instantiated class of type PDOStatement. The beauty of the PDOStatement class is that it implements the interface known as Traversable; that means it supports direct iteration. Therefore, you can execute a foreach() statement on an instance without worrying about how the class works under the hood.

Well, that is, almost. Iterating over the class results in associative arrays, each one equaling one row of output; but each associative array entry contains both key/value and index/value data. That’s why you need the is_numeric() clause to filter out the index/value stuff — try removing it and see what happens.

The preceding illustrates two points. First, it is hoped that it shows you that interrogating a database using PDO need not necessarily be any more code-intensive than using procedural code. Second, it also demonstrates that this quick-and-dirty approach doesn’t exactly give you much flexibility.

What would happen if, rather than iterate directly over the PDOStatement object returned directly, you intercepted it, and worked with it in a little more detail?