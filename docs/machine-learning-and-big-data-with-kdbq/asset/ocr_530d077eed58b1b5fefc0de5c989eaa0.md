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