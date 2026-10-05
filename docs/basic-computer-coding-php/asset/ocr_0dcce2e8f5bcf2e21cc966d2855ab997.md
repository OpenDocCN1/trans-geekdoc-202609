```
}
...
}
```

# 6.3.1 Declaring Methods

A method is a function defined inside a class. Although PHP imposes no special restrictions, most methods act only on data within the object in which the method resides. Method names beginning with two underscores (_) may be used in the future by PHP (and are currently used for the object serialization methods _sleep() and _wakeup())), so it is recommended that you do not begin your method names with a sequence.

Within a method, the $this variable contains a reference to the object on which the method was called. For instance, if you call $rasmus->birthday(), inside the birthday() method, $this holds the same value as $rasmus. Methods use the $this variable to access the properties of the current object and to call other methods on that object.

Here's a simple class definition of the Person class that shows the $this variable in action:

```
class Person {
    var $name;

    function get_name () {
        return $this->name;
    }

    function set_name($new_name) {
        $this->name = $new_name;
    }
}
```