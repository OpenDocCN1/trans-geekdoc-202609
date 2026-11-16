```
1 # fig02_02.py
2 """Find the minimum of three values."""
3
4 number1 = int(input('Enter first integer: '))
5 number2 = int(input('Enter second integer: '))
6 number3 = int(input('Enter third integer: '))
7
8 minimum = number1
9
10 if number2 < minimum:
11     minimum = number2
12
13 if number3 < minimum:
14     minimum = number3
15
16 print('Minimum value is', minimum)
```

lick here to view code image

![](bbox=[0.13, 0.39, 0.945, 0.51])

lick here to view code image

![](bbox=[0.13, 0.56, 0.945, 0.68])

lick here to view code image

![](bbox=[0.13, 0.73, 0.945, 0.85])

After inputting the three values, we process one value at a time:

+   • First, we assume that number1 contains the smallest value, so line 8 assigns it to the variable minimum. Of course, it's possible that number2 or number3 contains