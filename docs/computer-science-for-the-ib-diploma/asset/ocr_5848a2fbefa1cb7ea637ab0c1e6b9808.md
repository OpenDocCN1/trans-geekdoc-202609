If the array is of type string, it would look like this:

```
String pilots[] = { "Bob", "John", "Elvis" };
```

An array of Boolean data type can look like this:

```
Boolean passedExam[] = { true, false, true };
```

# One-dimensional lists (Python)

Python replaces arrays with lists, but you can manipulate those lists to behave like arrays.

In Python, data structures don't need to be declared. Square brackets are still used to specify that the data structure used is a 1D list.

For example, the grades array will look look like this:

```
grades = [75, 64, 95, 50, 34]
```

If the user wants to initialize a 1D list by using a FOR loop, then the code would look like this:

```
grades = [0]*5 #creates an array of 5 zeros
for i in range(5): #repeats 5 times
#stores value entered at given index
grades[i] = int(input("enter a value: "))
```

The first line in the code above specifies the initial value each element in the list will take (in this case, 0). After the *, it is the size of the list (meaning there are five 0s in this list at first).

If you were to write this line of code as grades = [ ], when trying the FOR loop an error would be thrown (index out of range), as the size of the list would be none or zero, so there would not be a way to add any new elements to it. However, the following statement is completely valid:

```
grades = []
grades = [0 for i in range(5)]
```

And this is possible because the grades list is overwritten. But this could have been just like this:

```
grades = [0 for i in range(5)]
```

The purpose of the line above is to initialize the grades list to 0 for all its five elements.

The following two lists are examples of a 1D list of type string and a 1D list of type Boolean:

```
pilots = ["Bob", "John", "Elvis"]
passedExam = [True, False, True]
```