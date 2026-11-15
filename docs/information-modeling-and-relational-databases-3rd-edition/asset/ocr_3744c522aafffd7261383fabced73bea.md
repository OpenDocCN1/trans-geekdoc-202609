To indicate that the value of an expression does *not* belong to a bag or set, the logical **not** operator may be used with the **in** operator. As with ordinary comparison operators, SQL gives the **in** operator higher priority than logical operators (unlike most programming languages). In SQL, the condition “not (x in S)” may be rendered more briefly as **not x in S**. Even better, SQL also allows **not in** for “∉”, so this may set out more naturally as **x not in S**.

```
x not in ( a, b ... ) means x ∉ [ a, b ... ]
```

For example, to obtain the names and birth years of those not born in any of the years 1950, 1967, or 1974, the following query may be used (yielding Fred and Terry):

```
select firstname, birthyr from Person
where birthyr not in (1950,1967,1974)
```

Sometimes, we wish to determine whether an expression has a value occurring in a range of values. In mathematics, to say that some variable x has a value in the range from a to b, we usually express this as a <= x <= b. This notation is illegal in SQL. Instead, we could say a<= x and x<= b. For the sample population, the following query returns the name and birth year of all but Terry.

```
select firstname, birthyr from Person
where 1950 <= birthyr and birthyr <= 1974
```

As another way to specify range membership, SQL provides the ternary mixfix operator “...between...and...” that may be defined as shown, where x, a, and b may be scalar expressions:

```
x between a and b means a <= x and x <= b
```

For example, the previous query may be reformulated as:

```
select firstname, birthyr from Person
where birthyr between 1950 and 1974
```

Note carefully that, in contrast to ordinary English, **between** in SQL is read in an *inclusive sense*. For instance, both 1950 and 1974 are included in the given range.

Notice also that here **and** is just part of the mixfix operator; it is not a logical operator. As already noted, the <= operator may be used to order strings as well as numbers. So, strings may be used as operands. For example, the following query returns the bag (“Bob”, “Eve”, “Fred”).

```
select firstname from Person
where firstname between ‘Bob’ and ‘Fred’
```

Nonmembership in a range may be expressed with the help of the **not** operator, which has lower priority than **between**, and may be placed just before the word **between**. Thus, each of the following conditions is equivalent to x < a or x > b.

```
x not between a and b not ( x between a and b ) not x between a and b
```