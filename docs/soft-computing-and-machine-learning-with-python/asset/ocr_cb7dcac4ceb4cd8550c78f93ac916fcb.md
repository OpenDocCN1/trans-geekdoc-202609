# List Methods

All list instances have methods for changing the values in the list. These methods work only on lists. They do not work on the other sequence types that are not mutable, that is, the values they contain may not be changed, added, or deleted.

For example, for any list instance $L$, the .append($v$) method adds a new value $v$ to that list.

```
>>> menu1 = ['kale', 'tofu']
>>> menu1
['kale', 'tofu']
>>> menu1.append ('sardines')
>>> menu1
['kale', 'tofu', 'sardines']
>>>
```

To insert a single new value $V$ into a list $L$ at an arbitrary position $P$, use this method:
$L$.insert($P, V$)

To continue the example above:

```
>>> ['kale', 'tofu', 'sardines']
>>> menu1.insert(0, 'beans')
>>> menu1
['beans', 'kale', 'tofu', 'sardines']
>>> menu1[3]
'sardines'
>>> menu1.insert(3, 'trifle')
>>> menu1
['beans', 'kale', 'tofu', 'trifle', 'sardines']
```

The method $L$.remove($V$) removes the first element of $L$ that equals $V$, if there