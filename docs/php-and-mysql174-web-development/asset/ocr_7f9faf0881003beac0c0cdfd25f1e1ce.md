204 Chapter 7 Error and Exception Handling

```
catch (myException $m)
{
    echo $m;
}
?
```

In this code, you declare a new exception class, myException, that extends the basic Exception class. The difference between this class and the Exception class is that you override the __toString() method to provide a "pretty" printing of the exception. The output from executing this code is shown in Figure 7.2. As you can see, it's similar to the previous example.

![](bbox=[0.119, 0.353, 0.616, 0.616])

Figure 7.2 The Exception class provides exceptions with "pretty printing"

This example is fairly simple. In the next section, we look at how to create different exceptions to deal with different categories of error.

# Exceptions in Bob’s Auto Parts

Chapter 2, "Storing and Retrieving Data," described how you could store Bob's order data in a flat file. You know that I/O (in fact, any kind of I/O) is one area in programs where errors often occur. This is a good place to apply exception handling.

Looking back at the original code, you can see that three things are likely to go wrong with writing to the file: the file cannot be opened, or a lock cannot be obtained, or the file cannot be written to. We created an exception class for each of these possibilities. The code for each is shown in Listing 7.4.