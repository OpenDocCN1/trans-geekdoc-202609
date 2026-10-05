1, 2, ..., 12.

#!/usr/local/bin/python

print "Table of powers of two"

```
print "{0:>10s} {1:>2s}".format("2***n", "n", "2**(-n)\)
for n in range(13):
    print "{0:10d} {1:27.15f}".format(2**n, n, 2**(-n))
```

Here we use the invocation of this script under the bash shell, and the output:
 ./powersof2

# Table of powers of two

**n n 2**(-n)
1 0.100000000000000
2 1.500000000000000
4 2 0.250000000000000
8 3 0.125000000000000
16 4 0.062500000000000
32 5 0.031250000000000
64 6 0.015625000000000
128 7 0.007812500000000
256 8 0.003906250000000
512 9 0.001953125000000
1024 10 0.000976562500000
2048 11 0.000488281250000
4096 12 0.000244140625000

# def: DEFINING FUNCTIONS

You can define your own functions in Python with the def statement.

+   - Python functions can act like mathematical functions such as len(s), which computes the length of s. In this example, values like s are passed to the function are called parameters to the function.

+   - However, more generally, a Python function is just a container for some Python statements that do some task. A function can take any number of parameters, even zero.