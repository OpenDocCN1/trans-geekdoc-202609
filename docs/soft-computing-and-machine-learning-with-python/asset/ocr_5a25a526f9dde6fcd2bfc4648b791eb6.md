# A Python 2.7 Programming Tutorial

```
>>> "{bat:8s}".format(bat=`fruit`)
'(fruit )'
```

```
>>> "{0:8f}".format(1.0/7.0)
'.0142857'
```

```
>>> "{n:20.11f}".format(n=1.0/7.0)
0.142857142857
```

```
>>> "{silly:50.40f}".format(silly=5.33333)
5.3333300000000012619238970993793010117'
```

Notice in the last example above that it is possible for you to produce a number of spurious digits beyond the number originally! Beware, because those digits are utter garbage.

When you specify a precision, the value is rounded to the nearest value with that precision.

```
>>> "{0:.1f}".format(0.999)
'1.0'
```

```
>>> "{0:.1f}".format(0.99)
'1.0'
```

```
>>> "{0:.1f}".format(0.9)
'0.9'
```

```
>>> "{0:.1f}".format(0.96)
'1.0'
```

```
>>> "{0:.1f}".format(0.9501)
'1.0'
```

```
>>> "{0:.1f}".format(0.9499999)
'0.9'
```

The "e" type code forces exponential notation. You may also wish to use the "g" (for general) type code, which selects either float or exponential notation depending on the value.

```
>>> avo = 6.022e23
>>> "{0:e}".format(avo)
'6.022000e+23'
>>> "{0:.3e}".format(avo)
```