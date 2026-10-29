
tail as well. This aspect of linked list is very important and, as you'll see, most of the operations on the list need to be implemented quite differently compared to an array. The opposite of the head, the tail, denotes the end of the list. Every node other than the tail points to the next node in the list, but tail doesn't point to anything. This is basically how we know it's the end of the list.

Nodes are what are called **self referential objects**. Figure 2.3.2.

![](img/225e78c1e15afa64fe5c5ef7710b7b57_27_0.png)

*Figure 2.3.2: Nodes in a linked list have heads and a tails*

The definition of a node includes a link to another node and self-referential here means the definition of node includes the node itself. Linked lists often come in two forms: a **singly linked list** where each node stores a reference to the next node in the list, or a **doubly linked list** where each node stores a reference to both the node before and after.

![](img/225e78c1e15afa64fe5c5ef7710b7b57_27_1.png)

*Figure 2.3.3: A singly linked list*

![](img/225e78c1e15afa64fe5c5ef7710b7b57_28_0.png)

Figure 2.3.4: A doubly linked list

If an array is a train with a bunch of cars in order, then a linked list is like a treasure hunt. When you start the hunt, you have a piece of paper with a location of the first treasure. You go to that location and you find an item along with a location to the next item of treasure. When you finally find an item that doesn't also include a location, you know that the hunt has ended. Now that we have a high-level view of what a linked list is, let's jump into code and build one together.

We'll focus on building a singly linked list for this course. There are advantages to having a doubly linked list, but we don't want to get ahead of ourselves. Let's start by creating a new file where we're going to put all our code for our linked list. We’ll name this file linked_list.py.

First, we're going to create a class to represent a node.

```python
class Node:
    data = None
    next_node = None
```

Now, node is a simple object in that it won't model much. So first, we'll add a data variable. It’s an instance variable here called data and we'll assign the value None initially. Then we'll add one more and call this next_node and to this we'll assign None as well. So, we've created two instance variables: data to hold onto the data that we're storing and next_node to point to the next node in the list.

Now we need to add a constructor to make this class easy to create. So, we'll add def __init__(self,data). Figure 2.3.5 shows the updated code from my workspace. This will be explained shortly.

![](img/225e78c1e15afa64fe5c5ef7710b7b57_29_0.png)

Figure 2.3.5: Code for a singly linked list

An init method here that takes self and some data to start off. And all we're going to do is assign data to that instance variable we created. That's all we need to model Node. Before we do anything else though, let's document our code. So, right after the class definition, let's create a docstring.

```
'''
An object for storing a single node of a linked list.
Models two attributes - data and the link to the next node in the list.
'''
```

Using the Node class is fairly straightforward so we can create a new instance of node with some data to store.

Now, just so you know, every time you run this code you start off from scratch. So, let's go ahead and create it:

```
N1 = Node(10)
print (N1)
```

When you run the code now, we have the following result.

```
<Node data: 10>
```

You can see that we have a node and it contains the data 10. We can now create another node by adding this:

```
N2 = Node(20)
N1.next_node = N2
```

So, N1 now points to N2. If we say

```
print(N1.next_node)
```

you'll see from the following result that it points to that node (the node containing 20).

```
<Node data: 20>
```

Figure 2.3.6 shows the updated code and results inside Pycharm.

![](img/225e78c1e15afa64fe5c5ef7710b7b57_30_0.png)

Figure 2.3.6: Updated code and results for examples of some nodes

Nodes are the building blocks for a list and now that we have a node object, we can use it to create a singly linked list.

```
class LinkedList:
```

```
def __init__(self):
    self.head = None
```

We have also created a constructor (def __init__(self)). This head attribute models the only node that the list will have a reference to. Since every node points to the next node, to find a particular node, we can go from one node to the next in a process called list traversal. Since the class constructor here will have set the default value of head to None so that new lists created are always empty.

Again, you'll notice in the above code that I didn't explicitly declare the head attribute at the top of the class definition. Don't worry, that's not an oversight. The self.head in the initializer means that it's still created. That's all there is to modeling a linked list.

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

Next, we're going to assign the next node in the list to current. So

```
current = current.next_node
```

This way, once we get to the tail and call next node, current will equal None and the while loop terminates. So in the end we can return count.

```
return count
```

As you can see, we need to visit every node to determine the size, meaning our algorithm runs in linear time.

Let's take a break here. We can now create lists, check if they're empty and check the size in the next section. Let's start implementing some common operations.

## 2.3.2. Adding Nodes to a Linked List

At the moment we can create an empty list but nothing else. Let's define a method to add data to our list. Technically speaking, there are three ways we can add data to a list. We can add nodes at the head of the list, which means that the most recent node we created will be the head and the first node we created will be the tail. Or we could flip that around: most recent nodes are the tail of the list and the first node to be added is the head.

I mentioned that one of the advantages of linked lists over arrays is that inserting data into the list is much more efficient than to the array. This is only true if we're inserting at the head or the tail. Technically speaking, this isn't an insert, and you'll often see this method called prepend if the data is added to the head, or append if it's added to the tail. A true insert is where you can insert the data at any point in the list, which is our third way of adding data. We're going to circle back on that.

If we wanted to insert at the tail, then the list needs a reference to the tail node, otherwise we would have to start at the head and walk down the length of the list, or traverse it to find the tail. Since our list only keeps a reference to the head, we're going to add new items at the head of the list.

## 2.3.3. Bonus Algorithm Code

Try the following bonus linked list code written in Python in your favorite Python editor. If you use a different programming language, try to translate it to your own language. If you need further help, just shoot me an email.

```
class Node:
    """
    An object for storing a single node in a linked list
```
