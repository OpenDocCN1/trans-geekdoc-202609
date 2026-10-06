and the memory location of the next item on the list. A place in memory that holds the memory location of another place in memory is called a pointer. Therefore in a linked list, each element contains a pointer to the next element. The first item of a list is called its head. The items in a list are also called nodes. The last node does not point to anywhere; we say that it points to null: nothingness on a computer.

A list is a sequence of items, but it is not necessary that the sequence is ordered using some specific criterion. For example, the following is a list containing some letters from the alphabet:

![](bbox=[0.117, 0.463, 0.922, 0.493])

If we have an unordered list, the algorithm for finding an item on it goes like this:

+   1. Go to the head of the list.
2. If the item is the one we are looking for, report that it is found and stop.
3. Go to the next item on the list.
4. If we are at null, report that the search item was not found and stop. Otherwise, return to step 2.