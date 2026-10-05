
| sym | name2 |
|---|---|
| a | a |
| b | b |
| c | c |

The delete function can be used to selectively delete some observations based on a conditional clause:

```q
delete from ks where name=`alpha`
```

| sym | name | name2 |
|---|---|---|
| b | beta | b |
| c | gamma | c |

If we wanted to directly extract a column as a list instead of creating a subtable? We can replace select with exec:

```q
exec name from ks
```

```
`alpha`beta`gamma
```

If we extract more than one column using exec, the outcome will be a dictionary indexed by the column names:

```q
exec name, name2 from ks
```

| | alpha beta gamma |
|name2 | a | b | c |

Finally, the type of a table is wh as can be seen from:

```q
type t
```

Another function for working with tables is meta. The argument of the function is a table and the function returns another table, where every row of the table corresponds to a column of the original table with information about its type (t), foreign key (f), and attribute (a) corresponding to being sorted (s), unique (u), partitioned (p) or true index (g).

The following is an example of a table without any foreign keys or attributes assigned to any of its string columns:

| | t | f | a |
|---|---|---|---|
| sym | s | | |
| name | s | | |
| name2 | s | | |

## 2.3 THE TRUTH ABOUT TABLES

Dictionaries and Tables in q are related. We saw that they have different data types (wh and kh), but how different are they?

The answer is not that much. A dictionary maps a vector of symbol keys to a list of vectors appears similar to a collection of columns, which is what a table is:

```q
d:sym`price!(`a`b`c;0D00:00 0D00:01 0D00:02;10 20 30f)
```

| sym | a | b | c |
|---|---|---|---|
| time | 0D00:00.000000000 | 0D00:01.000000000 | 0D00:02.000000000 |
| price | 10 | | 30 |

A reminder of the table we defined earlier looks like in the q console:

```q
t:[] sym`a`b`c; time:0D00:00 0D00:01 0D00:02; price:10 20 30f
t
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

If we could flip (transpose) by 90 degrees, the two would look exactly the same! In Chapter 1 we saw that flip is used to transpose matrices, which were defined n lists of vectors with count n. Let's try to flip to a dictionary:

```q
flip d
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

d and t now do look exactly the same. Are they? We find out by using the function ~:

```q
~flip d
```

So tables are simply the flip or apart from providing a different syntax for table creation - it gives us convenient way to create a table out of a dictionary and vice versa, on the fly.

Let us take a moment to reflect. d - being a q dictionary - is a map of symbol names to vectors and q is a vector language, famous for being the language of a columnar database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```q
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```q
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```q
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```q
d~flip t
```

Also, applying flip twice results in identity operation:

```q
d~flip flip d
```

```q
b

```q
t~flip flip t
```

## 2.4 KEYED TABLES ARE DICTIONARIES

We just saw that tables and dictionaries are in essence the same thing under the hood, which is very efficient as well as plain handy. They appear to be different to allow us to work with both tables and maps as separate entities and have different data types.

We will now attempt to create a new construct, using both tables and dictionaries. One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? One may ask: What would happen if we created a map to another table? No.

# Dictionaries and Tables: The q Fundamentals 49

Dictionaries and Tables in q are related. We saw that they have different data types (wh and kh), but how different are they?

The answer is not that much. A dictionary maps a vector of symbol keys to a list of vectors appears similar to a collection of columns, which is what a table is:

```q
d:sym`price!(`a`b`c;0D00:00 0D00:01 0D00:02;10 20 30f)
```

| sym | a | b | c |
|---|---|---|---|
| time | 0D00:00.000000000 | 0D00:01.000000000 | 0D00:02.000000000 |
| price | 10 | | 30 |

A reminder of the table we defined earlier looks like in the q console:

```q
t:[] sym`a`b`c; time:0D00:00 0D00:01 0D00:02; price:10 20 30f
t
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

If we could flip (transpose) by 90 degrees, the two would look exactly the same! In Chapter 1 we saw that flip is used to transpose matrices, which were defined n lists of vectors with count n. Let's try to flip to a dictionary:

```q
flip d
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

d and t now do look exactly the same. Are they? We find out by using the function ~:

```q
~flip d
```

So tables are simply the flip or apart from providing a different syntax for table creation - it gives us convenient way to create a table out of a dictionary and vice versa, on the fly.

Let us take a moment to reflect. d - being a q dictionary - is a map of symbol names to vectors and q is a vector language, famous for being the language of a columnar database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```q
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```q
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```q
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```q
d~flip t
```

Also, applying flip twice results in identity operation:

```q
d~flip flip d
```

```q
b

```

```q
t~flip flip t
```

```q
b
```

## 2.4 KEYED TABLES ARE DICTIONARIES

We just saw that tables and dictionaries are in essence the same thing under the hood, which is very efficient as well as plain handy. They appear to be different to allow us to work with both tables and maps as separate entities and have different data types.

We will now attempt to create a new construct, using both tables and dictionaries. One may ask: What would happen if we created a map to another table?

## 2.5 FROM A VECTOR LANGUAGE TO ANGEBRAIC

Dictionaries and Tables in q are related. We saw that they have different data types (wh and kh), but how different are they?

The answer is not that much. A dictionary maps a vector of symbol keys to a list of vectors appears similar to a collection of columns, which is what a table is:

```q
d:sym`price!(`a`b`c;0D00:00 0D00:01 0D00:02;10 20 30f)
```

| sym | a | b | c |
|---|---|---|---|
| time | 0D00:00.000000000 | 0D00:01.000000000 | 0D00:02.000000000 |
| price | 10 | | 30 |

A reminder of the table we defined earlier looks like in the q console:

```q
t:[] sym`a`b`c; time:0D00:00 0D00:01 0D00:02; price:10 20 30f
t
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

If we could flip (transpose) by 90 degrees, the two would look exactly the same! In Chapter 1 we saw that flip is used to transpose matrices, which were defined n lists of vectors with count n. Let's try to flip to a dictionary:

```q
flip d
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

d and t now do look exactly the same. Are they? We find out by using the function ~:

```q
~flip d
```

So tables are simply the flip or apart from providing a different syntax for table creation - it gives us convenient way to create a table out of a dictionary and vice versa, on the fly.

Let us take a moment to reflect. d - being a q dictionary - is a map of symbol names to vectors and q is a vector language, famous for being the language of a columnar database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```q
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```q
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```q
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```q
d~flip t
```

Also, applying flip twice results in identity operation:

```q
d~flip flip d
```

```q
b

```

```q
t~flip flip t
```

```q
b
```

## 2.4 KEYED TABLES ARE DICTIONARIES

We just saw that tables and dictionaries are in essence the same thing under the hood, which is very efficient as well as plain handy. They appear to be different to allow us to work with both tables and maps as separate entities and have different data types.

We will now attempt to create a new construct, using both tables and dictionaries. One may ask: What would happen if we created a map to another table?

## 2.5 FROM A VECTOR LANGUAGE TO ANGEBRAIC

Dictionaries and Tables in q are related. We saw that they have different data types (wh and kh), but how different are they?

The answer is not that much. A dictionary maps a vector of symbol keys to a list of vectors appears similar to a collection of columns, which is what a table is:

```q
d:sym`price!(`a`b`c;0D00:00 0D00:01 0D00:02;10 20 30f)
```

| sym | a | b | c |
|---|---|---|---|
| time | 0D00:00.000000000 | 0D00:01.000000000 | 0D00:02.000000000 |
| price | 10 | | 30 |

A reminder of the table we defined earlier looks like in the q console:

```q
t:[] sym`a`b`c; time:0D00:00 0D00:01 0D00:02; price:10 20 30f
t
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

If we could flip (transpose) by 90 degrees, the two would look exactly the same! In Chapter 1 we saw that flip is used to transpose matrices, which were defined n lists of vectors with count n. Let's try to flip to a dictionary:

```q
flip d
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

d and t now do look exactly the same. Are they? We find out by using the function ~:

```q
~flip d
```

So tables are simply the flip or apart from providing a different syntax for table creation - it gives us convenient way to create a table out of a dictionary and vice versa, on the fly.

Let us take a moment to reflect. d - being a q dictionary - is a map of symbol names to vectors and q is a vector language, famous for being the language of a columnar database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```q
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```q
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```q
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```q
d~flip t
```

Also, applying flip twice results in identity operation:

```q
d~flip flip d
```

```q
b

```

```q
t~flip flip t
```

```q
b
```

## 2.4 KEYED TABLES ARE DICTIONARIES

We just saw that tables and dictionaries are in essence the same thing under the hood, which is very efficient as well as plain handy. They appear to be different to allow us to work with both tables and maps as separate entities and have different data types.

We will now attempt to create a new construct, using both tables and dictionaries. One may ask: What would happen if we created a map to another table?

## 2.5 FROM A VECTOR LANGUAGE TO ANGEBRAIC

Dictionaries and Tables in q are related. We saw that they have different data types (wh and kh), but how different are they?

The answer is not that much. A dictionary maps a vector of symbol keys to a list of vectors appears similar to a collection of columns, which is what a table is:

```q
d:sym`price!(`a`b`c;0D00:00 0D00:01 0D00:02;10 20 30f)
```

| sym | a | b | c |
|---|---|---|---|
| time | 0D00:00.000000000 | 0D00:01.000000000 | 0D00:02.000000000 |
| price | 10 | | 30 |

A reminder of the table we defined earlier looks like in the q console:

```q
t:[] sym`a`b`c; time:0D00:00 0D00:01 0D00:02; price:10 20 30f
t
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

If we could flip (transpose) by 90 degrees, the two would look exactly the same! In Chapter 1 we saw that flip is used to transpose matrices, which were defined n lists of vectors with count n. Let's try to flip to a dictionary:

```q
flip d
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

d and t now do look exactly the same. Are they? We find out by using the function ~:

```q
~flip d
```

So tables are simply the flip or apart from providing a different syntax for table creation - it gives us convenient way to create a table out of a dictionary and vice versa, on the fly.

Let us take a moment to reflect. d - being a q dictionary - is a map of symbol names to vectors and q is a vector language, famous for being the language of a columnar database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```q
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```q
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```q
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```q
d~flip t
```

Also, applying flip twice results in identity operation:

```q
d~flip flip d
```

```q
b

```

```q
t~flip flip t
```

```q
b
```

## 2.4 KEYED TABLES ARE DICTIONARIES

We just saw that tables and dictionaries are in essence the same thing under the hood, which is very efficient as well as plain handy. They appear to be different to allow us to work with both tables and maps as separate entities and have different data types.

We will now attempt to create a new construct, using both tables and dictionaries. One may ask: What would happen if we created a map to another table?

## 2.5 FROM A VECTOR LANGUAGE TO ANGEBRAIC

Dictionaries and Tables in q are related. We saw that they have different data types (wh and kh), but how different are they?

The answer is not that much. A dictionary maps a vector of symbol keys to a list of vectors appears similar to a collection of columns, which is what a table is:

```q
d:sym`price!(`a`b`c;0D00:00 0D00:01 0D00:02;10 20 30f)
```

| sym | a | b | c |
|---|---|---|---|
| time | 0D00:00.000000000 | 0D00:01.000000000 | 0D00:02.000000000 |
| price | 10 | | 30 |

A reminder of the table we defined earlier looks like in the q console:

```q
t:[] sym`a`b`c; time:0D00:00 0D00:01 0D00:02; price:10 20 30f
t
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

If we could flip (transpose) by 90 degrees, the two would look exactly the same! In Chapter 1 we saw that flip is used to transpose matrices, which were defined n lists of vectors with count n. Let's try to flip to a dictionary:

```q
flip d
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

d and t now do look exactly the same. Are they? We find out by using the function ~:

```q
~flip d
```

So tables are simply the flip or apart from providing a different syntax for table creation - it gives us convenient way to create a table out of a dictionary and vice versa, on the fly.

Let us take a moment to reflect. d - being a q dictionary - is a map of symbol names to vectors and q is a vector language, famous for being the language of a columnar database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```q
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```q
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```q
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```q
d~flip t
```

Also, applying flip twice results in identity operation:

```q
d~flip flip d
```

```q
b

```

```q
t~flip flip t
```

```q
b
```

## 2.4 KEYED TABLES ARE DICTIONARIES

We just saw that tables and dictionaries are in essence the same thing under the hood, which is very efficient as well as plain handy. They appear to be different to allow us to work with both tables and maps as separate entities and have different data types.

We will now attempt to create a new construct, using both tables and dictionaries. One may ask: What would happen if we created a map to another table?

## 2.5 FROM A VECTOR LANGUAGE TO ANGEBRAIC

Dictionaries and Tables in q are related. We saw that they have different data types (wh and kh), but how different are they?

The answer is not that much. A dictionary maps a vector of symbol keys to a list of vectors appears similar to a collection of columns, which is what a table is:

```q
d:sym`price!(`a`b`c;0D00:00 0D00:01 0D00:02;10 20 30f)
```

| sym | a | b | c |
|---|---|---|---|
| time | 0D00:00.000000000 | 0D00:01.000000000 | 0D00:02.000000000 |
| price | 10 | | 30 |

A reminder of the table we defined earlier looks like in the q console:

```q
t:[] sym`a`b`c; time:0D00:00 0D00:01 0D00:02; price:10 20 30f
t
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

If we could flip (transpose) by 90 degrees, the two would look exactly the same! In Chapter 1 we saw that flip is used to transpose matrices, which were defined n lists of vectors with count n. Let's try to flip to a dictionary:

```q
flip d
```

| sym time | price |
|---|---|---|
| a | 0D00:00.000000000 10 |
| b | 0D00:01.000000000 20 |
| c | 0D00:02.000000000 30 |

d and t now do look exactly the same. Are they? We find out by using the function ~:

```q
~flip d
```

So tables are simply the flip or apart from providing a different syntax for table creation - it gives us convenient way to create a table out of a dictionary and vice versa, on the fly.

Let us take a moment to reflect. d - being a q dictionary - is a map of symbol names to vectors and q is a vector language, famous for being the language of a columnar database. Surely tables cannot be the transposition of columnar maps into plain old collections of records? Rest assured they are not. A q table is still a dictionary at heart. Internally t and d are the same and "all" that happens is indexing is allowed in a transposed way, to enable us to index a table more familiarly, i.e. indexing on records first.

Let's look at indexing and basic operations on a dictionary and a table side by side:

```q
d=`sym

`a`b`c

t[@ 0 1]`
```

| sym | price |
|---|---|
| a | 0000:00.000000000 10 |
| b | 0000:01.000000000 20 |

```q
d[`sym; 0 1]`

`a`b

t[@ 0;`sym]`
```

q is just tricking us into believing they are the transposition of each other. In fact, a table and a q dictionary both have the efficiency and speed that comes from mapping names to vectors stored in contiguous memory.

Upon further investigation, q convinces us that this is indeed the case, allowing us to do the following as well on t, as if it was a dictionary:

```q
t[`sym]

`a`b`c

t`sym`price

a b c
10 20 30`
```

Transposing a table also gives us a dictionary:

```q
d~flip t
```

Also, applying flip twice results in identity operation:

```q
d~flip flip d
```

```q
b

```

```q
t~flip flip t
```

```q
b
```

## 2.4 KEYED TABLES ARE DICTIONARIES

We just saw that tables and dictionaries are in essence the same thing under the hood, which is very efficient as well as plain handy. They appear to be different to allow us to work with both tables and maps as separate entities and have different data types.

We will now attempt to create a new construct, using both tables and dictionaries. One may ask: What would happen if we created a map to another table?
