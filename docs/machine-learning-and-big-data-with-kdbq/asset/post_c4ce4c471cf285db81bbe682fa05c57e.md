
# TABLE 1.1 The list of all types in kdb/q+ when using type

| name | character size | format | null | infinity |
|---|---|---|---|---|---|
| boolean | b | 1 | 1 | 0b | | |
| guid | g | 16 | 2 | | 0h | 0Ng |
| byte | x | 1 | 4 | | 0x00 | | 0Nh 0W | | |
| short | h | 2 | 5 | | 0i | 0Ni 0Wwi |
| int | i | 4 | 6 | | 0r or 0j | | |
| long | j | 8 | 7 | | 0Nj or 0Nn 0Ow or 0Wj |
| real | e | 4 | 8 | | 0e | 0Nf 0We |
| float | f | 8 | 9 | | 0.0 or 0f | 0Nf or 0n 0Ww |
| char | c | 1 | 10 | | "a" | | | |
| symbol | s | | 11 | | abc | | | |
| timestamp | p | 8 | 12 | | 2010.01.0100:01.000 | 0Np | 0Wp |
| month | m | 4 | 13 | | 2010.10m | 0Nm 0Ww |
| date | d | 4 | 14 | | 2010.10.10 | 0Nd 0Ww |
| datetime | z | 8 | 15 | | dateTime | 0Nz 0Wz |
| timespan | n | 8 | 16 | | 00:00:0000000000 | 0Nn 0Ww |
| minute | u | 4 | 17 | | 00:00:00 | 0Nu 0Wwu |
| second | v | 4 | 18 | | 00:00:00 | 0Nv 0Wv |
| time | t | 4 | 19 | | 00:00:00 | 0Nt 0Wt |
| enumerations | | | 20-76 | | 00:00:00.000 | | | |
| unused | | | 77 | | | | | |
| mapped list of | | | 78-96 | | | | | |
| lists | | | | | | | | |
| nested sym | | | | 97 | | | | |
| enumeration | | | 98 | | | | | |
| table | | | 99 | | | | | |
| dictionary | | | 100 | | | | | |
| lambda | | | 101 | | | | | |
| unary primitive | | | 102 | | | | | |
| binary primitive | | | 103 | | | | | |
| ternary operator | | | 104 | | | | | |
| projection | | | 105 | | | | | |
| composition | | | 106 | | | | | |
| f' | | | 107 | | | | | |
| f/ | | | 108 | | | | | |
| \: | | | 109 | | | | | |
| f/: | | | 110 | | | | | |
| f\: | | | 111 | | | | | |
| dynamic load | | | 112 | | | | | |

# Fundamentals of the q Programming Language

elements of a vector or list. The general format of a null is 0N? where ? is the character entry from Table 1.1.

We can check whether a value is null using the null function. This function returns an atom of type boolean, one that can take on the value 0b (false) or 1b (true):

```
null 3h

0b

null 0Nh

1b
```

There are a few exceptions among the primitive types: the boolean and byte types do not have a null at all, whereas char and symbol have null values and ^, respectively, reflecting their non-numeric format. Besides, for a null float, we may use the shorter notation 0N instead of 0f, and for a null long we may use the shorter notation 0N instead of 0j.

```
type 0Nj

-7h

while

type 0Nf

-9h

as well as

type 0n

-9h
```

The code is case sensitive, which we can see from

```
type 0N

-7h
```

The result of basic operations involving a null is usually a null itself:

```
0Nj+2

0N
```

# Fundamentals

Nulls follow type promotion:

```
0Nj+2

0n
```

```
type 0Nj+2

-9h
```

similar to

```
type 1j+2

-9h
```

In terms of ordering, nulls have the smallest numerical value as can be seen using <, >, >=, =

```
0Nj<1000
```

saying it is true that 0Nj is smaller than a given number. This is an illustration. For proof that the null has the lowest numerical value, we need infinities. This is the second special that we have introduced.

The infinity is generally represented by 0?, where ? is the character from Table 1.1. Except for the guid type, which does not have infinity. A float infinity is denoted using lowercase, where 0wf is the same as 0w, while 0Nj is the same as. Since temporal variables are internally stored as some numeric value, null values and infinities are well defined for them, too.

One thing regarding infinities: they are only well-behaved as floats, where infinity behaves in a proper mathematical sense. Let us illustrate the difference as follows:

```
0w+1

0N
```

```
0w+2

-0w
```

```
0w+3

-922337203685475806j
```

Long infinity is the largest possible number. If such a number is incremented by one, we obtain the null long, which we have pointed out, is the smallest long number. Adding two to the long infinity, we obtain the negative infinity. Adding three to the long infinity, we obtain the next smallest long after the negative infinity.

On the other hand, the floating point infinities (i.e. the float and real infinities) are well-behaved infinities as we can see from an analogous exercise:

| 0w+1 f |
|---|
| 0w |
| 0w+2 f |
| 0w |
| 0w-3f |
| 1b |

Only the floating point infinities demonstrate arithmetic consistent with the notion of infinity in mathematics.

# 1.2.1 Casting Types

The casting, i.e., explicit conversion, of types in q is done through the dollar function with the infix notation "newType$variable, where newType is a character representation of the new type for the variable. The conversion works as intuition suggests:

| type 1 |
|---|
| -7h |
| while the converted version |
| type "f$1 |
| has the type of |
| -9h |

An alternative syntax `newType$variable, where newType is a name representation of the new type for the variable:

| type `float$1 |
|---|
| -9h |

The character representation is more in the spirit of q to use concise code. For illustration, let us consider type casting for temporal variables:

```
now: 2099.01.01D01:02:03.456789000;
type now
```

```
-12h
```

The conversion of the variable now can be directly seen in the output:

```
"j$now
```

```
3124227723456789000
```

```
"t$now
```

01:02:03.456
```

```
"d$now
```

2099.01.01
```

```
"m$now
```

2099.01m
```

```
"u$now
```
01:02
```

```
"v$now
```
01:02:03
```

```
"n$now
```
0D01:02:02:03.456789000
```

We encourage the reader to experiment with the casting of various data types on her or own. We will focus on a special type of conversion which is quite frequent in empirical work: converting a string (i.e. a character vector) into a particular type. The data we work with may come from various sources and may be available in text format.

In order to analyse the data, it will need to be converted into the appropriate data types. Let us illustrate this with "1.1", which is

# 14

function's result is that argument converted to a string. Let us see string's application in the following examples:

```
string 123.45
```

```
"123.45"
```

The double quotes mean the output is a string. Analogously, we can convert other types like dates, times, etc.

```
string 2017.01.01
```

```
"2017.01.01"
```

The conversion to a symbol, on the other hand, is done using the following notation:

```
$123
```

```
123
```

We can only convert a string into a symbol. Symbols play a special role in kdb+ large tables, and we will cover them in the subsequent sections. For now, they can be described as internalised strings or a string pool which efficiently stores strings internally for fast lookups.

# 1.3 BASIC LANGUAGE CONSTRUCTS

In the previous paragraphs, we have reviewed some of the basic building blocks for data. In order to build a complex program, we have to learn more operators and language syntax. The syntactic rules of q are derived from k and do not bear much similarity to standard programming languages such as C, Python, or Java. Indeed, q belongs to a different language family.

# 1.1 Assigning, Equality and Matching

The basic element of any program is variables. To assign a value to a variable, the usual = is represented by the assignment operator : . It works as follows:

```
a:1.0
```

We confirm that the variable a is now equal to 1.0 as:

```
a
```

```
1.0
```
