```
```python
def main(low = 1, high = 4):
    if len(sys.argv) == 3:
        low = int(sys.argv[1])
        high = int(sys.argv[2])
    print("The summation of", low, "and", high,
          "is", summation(low, high))
if __name__ == "__main__":
    main()
```
```

Note that the main function here includes default arguments of 1 and 4, which are passed on to the summation function when the program launches. You can then test the function by calling main in the shell with other arguments, as shown in the next session:

```
```
>>>
The summation of 1 and 4 is 10
>>> main(1, 10)
The summation of 1 and 10 is 55
>>> main(2, 10)
The summation of 2 and 10 is 54
>>>
```
```

Because the program also checks for command-line arguments, you can test the program in a terminal window as well:

```
```
Madison:~ ken$ python3 recursion1.py
The summation of 1 and 4 is 10
Madison:~ ken$ python3 recursion1.py 1 10
The summation of 1 and 10 is 55
```
```

# Recursive Function Call Tracing

To get a better understanding of how a recursive function works, it is helpful to trace its calls. You'll do that for the summation function. You add an argument for a margin of indentation and print statements to trace the two arguments and the value returned on each call. The first statement on each call computes the indentation, which is then used in printing the two arguments. The value computed is also printed with this indentation just before each call returns. Here is the code for the summation function with tracing:

```
```python
def summation(low, high, margin = 0):
    """Returns the summation of the integers
    from low to high. Prints a trace of low,
    high, and the value returned for each call,
```
```