```
In [8]: wake_up.hour = 6

In [9]: wake_up
Out[9]: Time(hour=6, minute=45, second=0)
```

Though snippet [8] appears to simply assign a value to a data attribute, it’s actually a call to an hour method that takes 6 as an argument. The method validates the value, then assigns it to a corresponding data attribute (which we named __hour, as you’ll see in the next section).

# Attempting to Set an Invalid Value

To prove that class Time’s properties validate the values you assign to them, let’s try to assign an invalid value to the hour property, which results in a ValueError:

lick here to view code image

```
In [10]: wake_up.hour = 100
--------------------------------------------
ValueError                                 Traceback (most recent call last)
<ipython-input-10-1fce0716ef14> in <module>()
----> 1 wake_up.hour = 100

~/Documents/examples/ch10/timewithproperties.py in hour(self, hour)
     20     """Set the hour."""
     21     if not (0 <= hour < 24):
---> 22         raise ValueError(f'Hour ({hour}) must be 0-23')
     23
     24     self._hour = hour

ValueError: Hour (100) must be 0-23
```

# 10.4.2 Class Time Definition

Now that we’ve seen class Time in action, let’s look at its definition.

# Class Time: __init__ Method with Default Parameter Values

Class Time’s __init__ method specifies hour, minute and second parameters, each with a default argument of 0. Similar to class Account’s __init__ method, recall that the self parameter is a reference to the Time object being initialized. The statements containing self.hour, self.minute and self.second appear to create hour, minute and second attributes for the new Time object (self). However, these statements actually call methods that implement the class’s hour, minute and second properties (lines 13–50). Those methods then create attributes named _hour, _minute and _second that are meant for use only inside the class:

lick here to view code image

```
1 # timewithproperties.py
2 """Class Time with read-write properties."""
```