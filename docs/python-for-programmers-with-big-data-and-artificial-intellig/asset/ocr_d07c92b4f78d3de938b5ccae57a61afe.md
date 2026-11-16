```
Out [3]: Time(hour=6, minute=30, second=0)
```

We'll also provide the `__str__` special method, which is called when an object is converted to a string, such as when you output the object with print. 1 Our `__str__` implementation creates a string in 12-hour clock format:

1 If a class does not provide `__str__` and an object of the class is converted to a string, the classs `__repr__` method is called instead.

```
In [4]: print(wake_up)
6:30:00 AM
```

# Getting an Attribute Via a Property

Class time provides hour, minute and second properties, which provide the convenience of data attributes for getting and modifying an object's data. However, as you'll see, properties are implemented as methods, so they may contain additional logic, such as specifying the format in which to return a data attribute's value or validating a new value before using it to modify a data attribute. Here, we get the wake_up object's hour value:

```
In [5]: wake_up.hour
Out [5]: 6
```

Though this snippet appears to simply get an hour data attribute's value, it's actually a call to an hour method that returns the value of a data attribute (which we named _hour, as you'll see in the next section).

# Setting the Time

You can set a new time with the Time object's set_time method. Like method __init__, method set_time provides hour, minute and second parameters, each with a default of 0:

lick here to view code image

```
In [6]: wake_up.set_time(hour=7, minute=45)
In [7]: wake_up
Out [7]: Time(hour=7, minute=45, second=0)
```

# Setting an Attribute via a Property

Class Time also supports setting the hour, minute and second values individually via its properties. Let's change the hour value to 6:

lick here to view code image