# # Changing an item in a list

Changing an item is easy. All you do is access the item within the list, put it on the left side of an equal sign, and put something new on the right side. Suppose your list looks like this:

```
@names = ("Amy", "Bob", "Carl", "Danielle",
"Egbert", "Frank");
```

Then you use this line of code:

```
$names[2] = 'Carrie';
```

Your list now has Amy, Bob, Carrie, Danielle, Egbert, and Frank in it. (Remember, the first item has index 0, so $names[2] refers to the third item in the list, which is Carl.)

Now, suppose you use this line:

```
print $names[2];
```

The name Carrie prints out. The original data, Carl, is gone for good ... at least until you do this:

```
$names[2] = 'Carl';
```

![](bbox=[0.05, 0.56, 0.14, 0.63])

Carl is now back in the list, and Carrie is gone.

Each item in the list is a scalar. Thus, when you have this line:

```
$names[2] = 'Carrie';
```

the previous value in the element, Carl, gets replaced by the value Carrie. You don't end up with both Carl and Carrie in the array at once. You can't because the element is a scalar, not a list.

# # Embedding list elements in a string

If you want to put a list element inside a string, type it into the string as you would any other variable. Here's an example:

```
print "Hello $names[0], how are you?\n";
```

If your array @names contains a list of strings and the first one is Amy, you see the following output:

Hello Amy, how are you?