# Dictionaries and Tables: The q Fundamentals 49

database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```
d~flip t

ib
```