# Chapter 2 Introduction to Array

+   4. found = 1
5. location = i
6. else
7. i = i + 1
8. end if
9. end while
10. if found = 0 then
11. print "search is unsuccessful"
12. else
13. print "Search is successful"
14. end if
15. Return
16. stop

# Insertion

This operation is used to insert an element into an array into a particular location. A simple algorithm is given below.

# Algorithm

Steps:

+   1. if A[U] ≠ NULL then
2. print "array is full"
3. exit
4. else
5. i = U
6. while i > location
7. A[i] = A[i - 1]
8. i = i - 1
9. End while
10. A[location] = Key
11. End if
12. Stop

# Deletion

This operation is used to delete a particular element from an array. The element will be deleted by overwriting it with its subsequent element. A simple algorithm is as shown.