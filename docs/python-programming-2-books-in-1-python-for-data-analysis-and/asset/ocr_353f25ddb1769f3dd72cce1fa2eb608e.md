```
X = ["string1", "string2", "string3"]
print (X [-2])
```

OUTUTPUT - [string2]

You will also be able to specify a **range of indexes** by indicating the start and end of a range. The result in values of such command on a Python List would be a new List containing only the indicated items. Here is an example for your reference.

```
X = ["string1", "string2", "string3", "string4", "string5", "string6"]
print (X [3 : 5])
```

OUTUTPUT - ["string4", "string5"]

* Remember the first item is at position 0, and the final position of the range (4) is not included.

Now, if you do not indicate the start of this range, it will default to the position 0 as shown in the example below:

```
X = ["string1", "string2", "string3", "string4", "string5", "string6"]
print (X [ : 4])
```

OUTUTPUT - ["string1", "string2", "string3" , "string4"]

Similarly, if you do not indicate the end of this range it will display all the items of the List from the indicated start range to the end of the List, as