The answer lies in the conditional logic in the for loop: when the variable i equals 9, the iterator variable is “reset” to its initial value, thereby preventing an error. You can test this situation by “commenting out” the if statement, and when you launch the code you will see the following error message:

```
OutOfRangeError (see above for traceback): End of sequence
[[node IteratorGetNext (defined at tf-init-iterator.py:11) ]
```

Reset the code in Listing 6.5 to its original contents and you will see the following output when you launch the code in Listing 6.5 here:

+   0
1
2
3
4
5
6
7
8
9
0
1
2
3
4

# THE TENSORFLOW FILTER() OPERATOR