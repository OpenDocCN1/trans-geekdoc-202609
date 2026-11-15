A colon ":" begins the definition in a prefix manner and a semi-colon ";" ends the definition. For example, define a word called *double* as:

```
: double DUP +;
```

Here the definition of the word double consists of:

```
DUP +
```

That is the sequence of a duplication operation followed by an addition operation. For example:

```
7 double
```

The result is 14.

# A.5 DATA

The word. S is used to display data that is readily available in a location called the *data stack*.

Data is processed on a stack, in a First In Last Out (FILO) manner. Consider the postfix expression:

```
2 45 +
```

The result of 9 is put back onto the stack. Thus, the available data is now:

```
29
```