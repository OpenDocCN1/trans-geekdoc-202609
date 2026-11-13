Memory utilization: Linked lists can be more efficient with memory usage, as they do not create a reserved space in memory like an array does when it is declared.

Efficient insertion and deletion: Linked lists generally outperform arrays when inserting or deleting data due to their dynamic nature.

Heap space: a region of dynamically allocated memory managed by the operating system where programs store variables and data structures that require memory allocation during runtime, allowing for flexible memory usage that can grow and shrink as needed by the application.

# Disadvantages

Sequential access: As linked lists cannot be accessed via an index like arrays, searching a linked list requires a linear search algorithm, where you start at the head node and continue traversing until you find what you are looking for. This means that using a binary search algorithm, for example, is not possible on a linked list. For large data structures, this restriction when searching can be very time consuming when compared to accessing an array.

Memory utilization: Each node requires a reference to the next (and possibly the previous) node, as well as storing the data within it. This takes up system resources in the primary memory. As linked lists can grow, they potentially can go beyond the system resources that are available, causing a heap exhaustion as the system will run out of heap space.

# Types of linked lists

# Singly linked lists

![](bbox=[0.285, 0.405, 0.89, 0.475])

**Singly linked list**
This is the simplest of the three types. Each node contains a single pointer pointing to the next node in the list. The tail nodes contain a pointer that points to null (or none). This can be used to recognize the end of the list when traversing it.

# Doubly linked lists

![](bbox=[0.285, 0.585, 0.89, 0.655])

**Doubly linked list**
These differ from singly linked lists because the nodes have two pointers – one reference to the next node in the list and one to the previous. This allows for easier traversing of the list, as you can move forward and backward with ease.

# Circular linked lists

![](bbox=[0.285, 0.76, 0.88, 0.805])

**Circular linked list**