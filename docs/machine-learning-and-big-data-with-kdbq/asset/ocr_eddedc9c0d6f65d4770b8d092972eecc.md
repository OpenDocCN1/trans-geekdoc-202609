# 98

# LANGUAGE FUNDAMENTALS

Note in the example above, how we have used the single quote ' within our type-checking if statement to produce this exception. Thus we can use ' followed by a string of text to return an error of our choice which replaces the generic 'type' error. Alternatively, we could have returned the function or taken some corrective action, such as an attempt to cast the data or ignore the new data.

The same function, when making use of the log4q library, could be written as

```
.quantQ.myspace.func:[prices;newprices]
// prices -- vector of prices
// newprices -- vector of new prices
if[ prices ] to type newprices {
  ERROR("Price type incompatible; prices is type %1 vs
  newprices is %2"; prices;type newprices));
  INFO("Ignoring new prices")
  prices; / return original prices
newprices: newprices where newprices > 0;
  prices;newprices;
```

```
};\quantQ.myspace.func [1 2 3f;10 20]
```

ERROR [2019.01.28D11:07:41.572440000] Price types are incompatible! prices
is of type 9h newprices is 7h
INFO [2019.01.28D11:07:41.572614000] Ignoring new prices
1 2 3f

# 5.1.2 Other Errors

'length – Another “popular” one. This error appears when we perform an operation
on two objects which have incompatible lengths:

```
'length
[0] 1 2 2 3
^
```

```
t1:([a]:a 1 3);
t2:([a]:a 10 20);
t1+t2
```

```
'length
[0] t1+t2
^
```

whereas

```
t2:([a]:a 10 20 30)
nt1+t2
```