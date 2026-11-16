Keep in mind that stored procedures severely limit database portability — one of the key aims of the PDO project. To that end, use them sparingly and judiciously.

# Singleton Instantiation

On a typical PHP project, only one connection to one database is required. For that reason, instantiating multiple instances of the PDO class shouldn't happen in a given request — after all, one instance equals one connection.

This can be a tricky rule to stick to, though. You'll notice as you start to build increasingly sophisticated projects that your database access requirements are split across multiple classes. If each method of each class needs access to your database, how do you share access to a single connection across each of those classes?

The answer is a singleton class, a class with a single factory method that returns an instance of PDO for your application. This method is pretty smart. It figures out whether or not an instance of PDO has already been returned to your application. If one hasn't, then it creates a new instance of PDO and returns a reference to it. If it has, then it returns a reference to the existing instance:

```
<?php
class PDOFactory {
    public static function GetPDO($strDSN, $strUser, $strPass, $arParms) {
        $strKey = md5(serialize(array($strDSN, $strUser, $strPass, $arParms)));
        if (!($GLOBALS["PDOS"][$strKey] instanceof PDO)) {
            $GLOBALS["PDOS"][$strKey] = new PDO($strDSN,
                $strUser, $strPass, $arParms);
        };
        return($GLOBALS["PDOS"][$strKey]);
    }
}
?>
```

This class enables you to create new instances of PDO without ever worrying about duplicate connections. Provided that the DSN, username, password, and parameter array are identical on each occasion, you'll never get a duplicate — just the original.

Therefore, in your code, look for the following:

```
$objPDO = new PDO($strDSN, NULL, NULL, array(PDO::ATTR_PERSISTENT => true));
```

Instead of the preceding syntax, use the following:

```
$objPDO = PDOFactory::GetPDO($strDSN, NULL, NULL, array(PDO::ATTR_PERSISTENT =>
true));
```

The effect is the same — you get an instance of the PDO object — but you're guaranteed not to get more than one per script execution, regardless of the class from which you request the instance.