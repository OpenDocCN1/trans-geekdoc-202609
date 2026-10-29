Now we can add methods that make it easier to use this data structure. Also, let’s add a really simple docstring below the class definition to provide some information.

```
"""
Singly linked list
"""
```

A common operation carried out on data structures is checking whether it contains any data or whether it's empty. At the moment, to check if a list is empty, we would need to query these instance variables head and so on every time. Ideally, we would like to not expose the inner workings of our data structure to code that uses it. Instead, let's make this operation more explicit by defining a method.

```
def is_empty(self):
    return self.head == None
```

All we're doing in the second line is checking to see if head is None. If it is, this condition evaluates to true which indicates the list is empty. Now before we end this section, let's add one more convenience method to calculate the size of our list.

The name convenience method indicates that what this method is doing is not providing any additional functionality that our data structure can't handle right now, but instead making existing functionality easier to use. We could calculate the size of our linked list by traversing it every time using a loop until we hit a tail node, but doing that every time is a hassle.

```
def size(self):
```

Unlike calling len on a Python list, not to be confused with a linked list, which is a constant time operation, our size operation is going to run in linear time. The only way we can count how many items we have is to visit each node and call next until we hit the tail node. So, we'll start by getting a reference to the head. We'll say

```
current = self.head
count = 0
```

Let's also define a local variable named count with an initial value of 0 that will increment every time we visit a node. Once we hit the tail count will reflect the size of that list.

Next, we'll define a while loop that will keep going until there are no more nodes. So, we say

```
while current:
```

Now inside this loop, we will increment the count value. So,

```
count+=1
```