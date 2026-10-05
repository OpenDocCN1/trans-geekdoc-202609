
# Fundamentals of the q Programming Language

## Join

The symbol `,` is used to join two lists:

```
(@ 1 2 3 4), (5 6 7 8 9)
```

The join operator can join lists of any type:

```
(@ 1 2 3 4), `a, "hello"
```

```
((@ 1 2 3 4);;"hello")
```

## Print to console

The symbol `!` has important functionalities which will be reviewed later. The particular function involving `!` is:

```
-n
```

which prints the argument on the right-hand side to console in an unformatted form but also allows q to use the argument further down the statement for subsequent operations on the left. In particular, when using the q prompt, we can use `! ` as control prints:

```
1+!1+!1+!
```

```
+ 1
2
3
4
```

This is useful to track the evaluation of a complicated statement – such functionality, however, does not work when using IDEs.

## Separator

We saw that the symbol `;` denotes the end of a statement. However, when surrounded by brackets, it acts as a separator for elements within a list:

```
(1;2;3;4)
```

1 2 3 4

## LANGUAGE FUNDAMENTALS

or nested lists:

- (1;2;(1;2);4)

```
1
2
1 2
4
```

As we will see in the next chapter, the symbol `;` also separates arguments when defining a function. Finally – as we saw previously – it separates statements:

```
a:1;b:2;a+b
```

```
+ 3
```

We may easily write quite complicated commands within one line. If a separator is used to separate statements, the statements are evaluated one by one from the left, but within a statement, the right-to-left priority is used. q does not consider the end of a line (newline operator) as the end of a statement so one statement can also be written in multiple lines for better clarity. For reducing clutter in our code, we should also keep separate statements in separate lines. #### Quit

The symbol `\` is not a symbol per se but plays an important role. When entered in the q session, it will terminate the session.

## Index

The “at” sign, `@`, is known as “apply” and can be used to apply a monadic (one-argument) function to its argument. Since q is a functional language, indexing is a function, too, and we can use index to apply a vector to a list. The following forms are equivalent:

```
max [1 2 3]
max 2 3
x:1 2 3
x @0 1
```

## Precedence/list

`()` is primarily used to define the precedence since q evaluates expressions from right to left. When using brackets, the evaluation is commanded to start from the innermost pair and move outwards:

```
((1+2)*(3+4))
```

1+2+3+4 The usage of the brackets is very convenient as we can get some overhead and in some cases can create more “noisy” code. `()` can be used to form lists and create nested lists:

```
(((1;2);3);4)
```

```
((1;2);3);4)
```

```
(((1;2);3);4)
```

which is a nested list of lists. In the topmost layer, the list contains `(((1;2);3);4)` and atom. `enlist` is a compelling function which creates a list out of input. The opposite operation of ‘flattening’ a list (or ‘razing’ it) is achieved by `raze`:

`raze` is also used to create tables, as we will see in the next chapter. ## Block

The square brackets, `[]`, form a block of code which could be useful inside conditional expressions:

```
a:1;b:2;a+b
```

does not change precedence of statements but forms a statement, which is evaluated as a block. The brackets `[]` have two other functions in q: First, they denote the argument of the function, and second, they form special multi-valence functions. ## Assign/amend

The symbol `=` is the assignment operator as previously saw. The existing value assigned to a variable can be amended either by explicitly stating the operation or using the short notation of:

```
a:1;
a:a+1;
```

```
2
a:1;
a+=1;
```

```
a:2;
a*=2;
```

This can be applied to other arithmetic operations like `+, %`. Both functionalities will be described in Chapter 3. ## Identity

The symbol `::` stands for the identity function, which returns its argument:

```
(:) 1
```

The identity is useful whenever we need to use a function, which outputs the arguments.

```
1
```

#### 1.5 DIFFERENCE BETWEEN STRINGS AND SYMBOLS

In q, we have two types, the string and the symbol, which seemingly do the same job. Imagine we have a database, which contains a timestamp, price and also the name of the asset it belongs to, e.g. IBM, INTC, AAPL. We store the asset names as strings; however, having a large number of repeated values, will be consuming memory. We prevent wasting memory by replacing the names by short integers, for example, and keep a separate lookup table to recover the map between short integers and names, in the form of a dictionary:

```
nameToShortMap(``IBM` `INTC` `AAPL`(`1 2 3`);
```

This is not a very convenient way to work with data and in particular to share our work with others. In order to avoid such approach, q uses the concept of symbols, which are internalised. Such strings are kept in memory only, i.e each distinct value is kept in memory only, and references to the original string are used internally. Under the surface, q maintains a pool of strings as symbols and every usage of symbol points to the value in this table. The notion of symbols clearly suggests that we need to use strings repeatedly, symbols are the type of choice. As the pool of strings is maintained in memory, we should constrain the use of symbols with repeated values to avoid blowing up the memory. If we need unique and compiled names, we should stick to characters, i.e strings. Alternatively, if we need to use unique identifiers, like trade IDs, we should use the guide. Another advantage of symbols is that the comparison is much faster we do not need to check every character, but merely the reference to that string. For instance, queries like

```
where name=`IBM`
```

or

```
where in=``IBM` `INTC`
```

significantly improve the speed and simplicity of evaluation compared to using character vectors.

### 1.5.1 Enumeration

The q language allows us to go one step further when working with symbols and create enumerates. This should be a familiar concept from other languages (q does contain various features we are used in “common” programming languages). The enumerated list of symbols form a new type — enumerations have a type range of short integers — restrict the values within the existing domain. Any changes to the new type in terms of appending or changing the values are restricted to the provided list. Let us create an enumerated list out of our three names of assets used above:

```
assetNames=``IBM` `INTC` `AAPL`;
```

and a list of names within our hypothetical analysis involving multiple occurrences of the vector of assetNames:

```
name: `IBM` `INT` `IBM` `INT` `IBM` `INT` `AAPL` `INT` `IBM` `INT` `IBM` `INT` `AAPL` `INT` `IBM` `AAPL`;
```

```
name
```

```
type
```

```
28
```

```
LANGUAGE FUNDAMENTALS
```

```
32
```

```
3
```

```
4
```

```
1
2
1 2
4
```

```
3
```

```
4
```

```
3
```

```
4
```

```
3
```

```
4
```

```
3
```

```
4
```

```
30
```
