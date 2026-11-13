+   - 42 may denote the number of pixels per clock tick that a simulation or game object moves;
+   - 42 may mean a temperature, on the Fahrenheit, Celsius, or Kelvin scale for the domain of physics;
+   - 42 may specify the size of some table if the domain of the program is a furniture catalog; or
+   - 42 could just count the number of characters in a string.

The key is to know how to go from numbers as information to numbers as data and vice versa.

Since this knowledge is so important for everyone who reads the program, we often write it down in the form of comments, which we call *data definitions*. A data definition serves two purposes. First, it names a collection of data—a *class*—using a meaningful word. Second, it informs readers how to create elements of this class and how to decide whether some arbitrary piece of data belongs to the collection.

> Computing scientists use “class” to mean something like a “mathematical set.”

Here is a data definition for one of the above examples:

```
```
; A Temperature is a Number.
; **interpretation** represents Celsius degrees
```
```

The first line introduces the name of the data collection, Temperature, and tells us that the class consists of all Numbers. So, for example, if we ask whether 102 is a temperature, you can respond with “yes” because 102 is a number and all numbers are temperatures. Similarly, if we ask whether "cold" is a Temperature, you will say “no” because no string belongs to Temperature. And, if we asked you to make up a sample Temperature, you might come up with something like –400.

If you happen to know that the lowest possible temperature is approximately –274° C, you may wonder whether it is possible to express this knowledge in a