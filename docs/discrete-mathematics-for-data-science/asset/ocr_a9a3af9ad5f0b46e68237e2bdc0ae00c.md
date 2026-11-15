Note how elements having a subscript of 0, such as $a_0$, are both an element of the host list and a first element of a constituent list.$^7$ The host list shares one element with each of its constituent lists.

Each constituent list, $a\ b\ c$ and $d$, as well as the lists of lists, $l$, has a cardinality of 4. That is the count of their respective elements. We may denote:

$|a| \equiv |b| \equiv |c| \equiv |d| \equiv |l|$

# 16.5 LISTS OF ABSTRACT DATA TYPES

The data of a list is not limited to characters and numbers. Custom or abstract data type definitions can comprise lists.$^8$ Abstract data types are sometimes called ADTs.

7 Incidentally, in computer science the address of the first element of an array is also the address of the array itself, representing the other elements of the array. ↵

8 For more details, please refer to the chapter *Atoms & Abstractions*. ↵

Given a list of ADTs, we call the elements *instances* or *objects* of the ADT.

Suppose we have an ADT named $A$. Then we should denote instances of $A$ such as $a_0\ a_1 \dots a_N$. As an abstract type, $A$ may be composed of objects of various types, including integers, characters, lists, and other abstract objects.