```
else :
    print (f "{number} is not a multiple of two")
```

The following program could also have been written:

```
number = int(input("Enter a number:"))
if number % 2 == 0 and number% 4! = 0:
    print (f "{number} is a multiple of two")
elif number % 2 == 0:
    print (f "{number} is a multiple of four and two")
else :
    print (f "{number} is not a multiple of two")
```

This program works because the multiples of four are also multiples of two and the program only evaluates the second condition (elif's) if the first one has not been met.

But we can still simplify the program further, ordering the cases differently:

```
number = int(input("Enter a number:"))
if number % 4 == 0:
    print (f "{number} is a multiple of four and two")
elif number % 2 == 0:
    print (f "{number} is a multiple of two")
else :
    print (f "{number} is not a multiple of two")
```

This program works correctly because although the second condition (elif's) does not distinguish between multiples of two and four, if number is a multiple of four, the program fails to evaluate the second condition because the first one is met (the one of if).

In general, the order that makes it easier to simplify the expressions is usually to consider the particular cases first and then the general cases.