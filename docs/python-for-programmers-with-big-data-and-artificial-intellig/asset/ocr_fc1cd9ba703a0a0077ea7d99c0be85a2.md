that encourage correct use. By convention, Python programmers know that any attribute name beginning with an underscore (_) is for a class’s internal use only. Client code should use the class’s methods and—as you’ll see in the next section—the class’s properties to interact with each object’s internal-use data attributes. Attributes whose identifiers do not begin with an underscore (_) are considered publicly accessible for use in client code. In the next section, we’ll define a Time class and use these naming conventions. However, even when we use these conventions, attributes are always accessible.

# 10.4 PROPERTIES FOR DATA ACCESS

Let’s develop a Time class that stores the time in 24-hour clock format with hours in the range 0–23, and minutes and seconds each in the range 0–59. For this class, we’ll provide properties, which look like data attributes to client-code programmers, but control the manner in which they get and modify an object’s data. This assumes that other programmers follow Python conventions to correctly use objects of your class.

# 10.4.1 Test-Driving Class Time

Before we look at class Time’s definition, let’s demonstrate its capabilities. First, ensure that you’re in the ch10 folder, then import class Time from timewithproperties.py:

lick here to view code image

```
In [1]: from timewithproperties import Time
```

# Creating a Time Object

Next, let’s create a Time object. Class Time’s __init__ method has hour, minute and second parameters, each with a default argument value of 0. Here, we specify the hour and minute—second defaults to 0:

lick here to view code image

```
In [2]: wake_up = Time(hour=6, minute=30)
```

# Displaying a Time Object

Class Time defines two methods that produce string representations of Time object. When you evaluate a variable in IPython as in snippet [3], IPython calls the object’s __repr__ special method to produce a string representation of the object. Our __repr__ implementation creates a string in the following format:

lick here to view code image

```
In [3]: wake_up
```