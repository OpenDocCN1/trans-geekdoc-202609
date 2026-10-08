The explode function has the following prototype:

```
array explode(string separator, string string [, int limit])
```

In the preceding chapter, we used the tab character as a delimiter when storing this data, so
here we do the following:

```
$line = explode("t", $orders[$i]);
```

This code "explodes the passed-in string into parts. Each tab character becomes a break
tween two elements. For example, the string

```
16:44,28th September 2014\t1 tires\t2 oil\t3 spark plugs\t145.2\t123 Main Street,
Sowtown 95128
```

is exploded into the parts "16:44, 28th September 2014, "1 tires", "2 oil, "3spark
plugs," "145.2" and "123 Main Street, Sowtown 95128". Note that the optional
limit parameter can be used to limit the maximum number of parts returned.

This example doesn't do much processing. Rather than output tires, oil, and spark plugs
on every line, this example displays only the number of and gives the heading row
to show what the numbers represent.

You could extract numbers from these strings in a number of ways. Here, we used the function
val(). As mentioned in Chapter 1, intval() converts a string to an integer. The cover-
sion is reasonably clever and ignores parts, as the label in this example, which cannot be
converted to an integer. We cover various ways of processing strings in the next chapter.

# Performing Other Array Manipulations

So far, we have covered only half the array processing functions. Many others will be
useful from time to time; we describe some of them.

# Navigating Within an Array: each(), current(), reset(),
(), next(), pos(), and prev ()

We mentioned previously that every array has an internal pointer that points to the current
element in the array. You indirectly use this pointer when using the each() function,
but you can use and manipulate this pointer.

If you create a new array, the current pointer is initialized to first the element in the
array. Calling current($array_name) returns the first element.

Calling either next() or each() advances the pointer forward one element. Calling
each($array_name) returns the current element before advancing the pointer. The function
next() behaves slightly differently: Calling next($array_name) advances the pointer and
then returns the new current element.