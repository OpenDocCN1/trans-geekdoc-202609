# Preventing Inheritance and Overwriting

```
final class MyFinalBaseClass ()
public final function myMethod() {
```

There are some classes you do not want to inherit from (for instance, if they contain critical functionality, and you do not want the other developers overwrite those vital methods). PHP's final keyword is suited for that task. You can either make a class final (in which case, it is not possible to inherit from it at all) or you can declare a method as final (in which case, code cannot overwrite it). Therefore, the following code causes an exception, as depicted in Figure 4.1:

```
<?php
    class MyFinalBaseClass {
        public final function getCopyrightNotice() {
            return '&copy; by Original Author';
        }
    }

    class MyFinalClass extends MyFinalBaseClass {
        function getCopyrightNotice() {
            return '&copy; by me!';
        }
    }
?>
```

*Preventing Overloading with the final Keyword (final.php)*