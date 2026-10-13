
As we talked about the stack in previous pages, we already know that stack is a linear data structure with the LIFO principle. As a result, stacks have only one end to add a new item or remove an item. It is one of the oldest and most used data structures in computer technology. We always add or remove an item from a stack using the single point named `top`. The term `push` is used to indicate an item to be added on top of the stack and `pop` to remove an item from the top; this is shown in the following diagram. We will discuss more about stacks in [Chapter 4](#text00098.html), *Constructing Stacks and Queues*.

![](Image00011.jpg)

# Queue

A queue is another linear data structure which follows the FIFO principle. A queue allows two basic operations on the collection. The first one is `enqueue` which allows us to add an item to the back of the queue. The second one is `dequeue` which allows us to remove an item from the front of the queue. A queue is another of the most used data structures in computer technology. We will learn details about queues in [Chapter 4](#text00098.html), *Consrtucting Stacks and Queues*.

![](Image00012.jpg)

# Set

A set is an abstract data type which is used to store certain values. These values are not stored in any particular order but there should not be any repeated values in the set. Set is not used like a collection where we retrieve a specific value from it; a set is used to check the existence of a value inside it. Sometimes a set data structure can be sorted and we call it an ordered set.

# Map

A map is a collection of key and value pairs where all the keys are unique. We can consider a map as an associative array where all keys are unique. We can add and remove using key and value pairs along with update and look up from a map using a key. In fact, PHP arrays are ordered map implementations. We are going to explore that in the next chapter.

# Tree

A tree is the most widely used nonlinear data structure in the computing world. It is highly used for hierarchical data structures. A tree consists of nodes and there is a special node which is known as the `root` of the tree which starts the tree structure. Other nodes descend from the root node. Tree data structure is recursive which means a tree can contain many subtrees. Nodes are connected with each other through edges. We are going to discuss different types of trees, their operations, and purposes in [Chapter 6](#text00138.html), *Understanding and Implementing Trees*.

![](Image00013.jpg)

# Graph

A graph data structure is a special type of nonlinear data structure which consists of a finite number of vertices or nodes, and edges or arcs. A graph can be both directed and undirected. A directed graph clearly indicates the direction of the edges, while an undirected graph mentions the edges, not the direction. As a result, in an undirected graph, both directions of edge are considered as a single edge. In other words, we can say a graph is a pair of sets (`V, E`), where `V` is the set of vertices and `E` is the set of edges:

`V = {A, B, C, D, E, F}`

`E = {AB, BC, CE, ED, EF, DB}`

In a directed graph, an edge `AB` is different from an edge `BA` while in an undirected graph, both `AB` and `BA` are the same. Graphs are handy to solve lots of complex problems in the programming world. We are going to continue our discussion of graph data structures in [Chapter 9](#text00202.html), *Putting Graphs into Action*. In the following diagram, we have:

![](Image00014.gif)

# Heap

A heap is a special tree-based data structure which satisfies the heap properties. The largest key is the root and smaller keys are leaves, which is known as `max heap`. Or, the smallest key is the root and larger keys are leaves, which is known as `min heap`. Though the root of a heap structure is either the largest or smallest key of the tree, it is not necessarily a sorted structure. A heap is used for solving graph algorithms with efficiency and also in sorting. We are going to explore heap data structures in [Chapter 10](#text00229.html), *Understanding and Using Heaps*.

![](Image00015.jpg)

# 读累了记得休息一会哦~

**公众号：古德猫宁李**

*   电子书搜索下载
*   书单分享
*   书友学习交流

**网站：**[沉金书屋 https://www.chenjin5.com](https://www.chenjin5.com)

*   电子书搜索下载
*   电子书打包资源分享
*   学习资源分享

# Solving a problem - algorithmic approach

So far we have discussed different types of data structures and their usage. But, one thing we have to remember is that just putting data in a proper structure might not solve our problems. We need to find solutions to our problems using the help of data structures or, in other words, we are going to solve problems using data structures. We need algorithms to solve our problem.

An algorithm is a step by step process which defines the set of instructions to be executed in a certain order to get a desired output. In general, algorithms are not limited to any programming language or platform. They are independent of programming languages. An algorithm must have the following characteristics:

*   **Input**: An algorithm must have well-defined input. It can be 0 or more inputs.
*   **Output**: An algorithm must have well-defined output. It must match the desired output.
*   **Precision**: All steps are precisely defined.
*   **Finiteness**: An algorithm must stop after a certain number of steps. It should not run indefinitely.
*   **Unambiguous**: An algorithm should be clear and should not have any ambiguity in any of the steps.
*   **Independent**: An algorithm should be independent of any programming language or platforms.

Let us now create an algorithm. But in order to do that, we need a problem statement. So let us assume that we have a new shipment of books for our library. There are 1000 books and they are not sorted in any particular order. We need to find books as per the list and store them in their designated shelves. How do we find them from the pile of books?

Now, we can solve the problem in different ways. Each way has a different approach to find out a solution for the problem. We call these approaches algorithms. To keep the discussion short and precise, we are going to only consider two approaches to solve the problem. We know there are several other ways as well but for simplicity let us keep our discussion only for one algorithm.

We are going to store the books in a simple row so that we can see the book names. Now, we will pick a book name from the list and search from one end of the row to the other end till we find the book. So basically, we are going to follow a sequential search for each of the books. We will repeat these steps until we place all books in their designated places.

# Writing pseudocode

Computer programs are written for machine reading. We have to write them in a certain format which will be compiled for the machine to understand. But often those written codes are not easy to follow for people other than programmers. In order to show those codes in an informal way so that humans can also understand, we prepare **pseudocode**. Though it is not an actual programming language code, pseudocode has similar structural conventions of a programming language. Since pseudocode does not run as a real program, there is no standard way of writing a pseudocode. We can follow our own way of writing a pseudocode.

Here is the pseudocode for our algorithm to find a book:

```
Algorithm FindABook(L, book_name)

  Input: list of Books L & name of the search book_name

  Output: False if not found or position of the book we are looking for.

  if L.size = 0 return null

  found := false

  for each item in L, do

    if item = book_name, then

      found := position of the item

  return found
```
