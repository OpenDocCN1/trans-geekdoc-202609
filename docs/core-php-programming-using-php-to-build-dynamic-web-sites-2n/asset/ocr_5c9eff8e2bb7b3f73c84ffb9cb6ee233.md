# integer jewishtojd(integer month, integer day, integer year)

The jewishtojd function returns a Julian Day Count for the given Jewish calendar date.

```
$jdc = jewishtojd(1,1,1);
print (jdtogregorian(\$jdc));
```

# integer juliantoj(integer month, integer day, integer year)

Use the juliantoj function to get the Julian Day Count for a Julian calendar date.

```
$jdc = juliantoj(1,1,1);
print (jdtogregorian(\$jdc));
```

# Configuration

The following functions affect the operation of PHP. Some of them alter configuration variables. Others cause a script to stop executing for a period of time.

# boolean bcscale(integer scale)

The bcscale sets the default scale for the functions that perform math on arbitrary-precision numbers. The scale is the number of digits after the decimal point. See the section on arbitrary-precision numbers in Chapter 10, "Mathematical Functions."

```
//use ten digits
bscale(10);
```

# clearstatcache()

Calling's stat function may take a considerable amount of time. To increase performance, PHP caches the results of each call. When you use a function that relies on stat, if information about a file changes often, you may need to clear the stat cache.