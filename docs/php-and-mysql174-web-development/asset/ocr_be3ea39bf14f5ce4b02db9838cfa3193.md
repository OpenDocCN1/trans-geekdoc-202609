The output in the browser should be similar to that shown in Figure 2.5.

![](bbox=[0.143, 0.155, 0.751, 0.463])

Figure 2.5 After reading the orders, the file pointer points to the end of the file, an offset of 198 bytes. The call to rewind sets it back to position 0, the start of the file

You can use the function fseek() to set the file pointer to some point within the file. Its prototype is

```
int fseek( resource fp, int offset, int whence );
```

A call to fseek() sets the file pointer to a point starting from whence and moving offset into the file. The optional whence parameter defaults to the value SEEK_SET, which is effectively the start of the file. The other possible values are SEEK_CUR (the current location of the file pointer) and SEEK_END (the end of the file).

The rewind() function is equivalent to calling the fseek() function with an offset of zero. For example, you can use fseek() to find the middle record in a file or to perform a binary search. If reach the level of complexity in a data file where you need to do these kinds of things, your life will be much easier if you use a build-purpose database.

# # Locking Files

Imagine a situation in which two customers are trying to order a product at the same time. (This situation is not uncommon, especially when your website starts to get any kind of traffic volume) If one customer calls fopen() and begins writing, and then the other customer calls fopen() and begins writing. What will be the final contents of the file? Will it be the first order followed by the second order, or vice versa? Will it be one order or the other?