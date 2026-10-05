# Parse Trees 167

The parse tree is a mixed list:

```
type parseTree1
Ø
```

The first element of the list is :, the assignment operator. The other elements of the list are arguments to the assignment operator. We can guess at this point that parseTree1 represents qs internal representation of assigning 1 j to the variable x. We can verify it by using eval:

```
eval parseTree1
1
```

To verify there is a value assigned to the variable x, we can just run:

```
x
1
```

Evaluating parseTree1 indeed assigned a value to variable x. The variable is called by reference, which makes the construction of the parse tree with assignment more flexible since the reference itself can be a variable which is dynamically assigned in our code. We can consider the situation where we want to create the following list of variables: x1=1, x2=2, x3=3... We may construct the k-th term as follows:

```
k:4;
name:"$x", string k;
eval (;name;k);
x4
4
```

We can embed this within a function which creates the variable:

```
parseTreeFunc1::[k]
eval (;"$x", string k);
};
```

The function has a more concise notation than the previous example. We can test it

```
as
parseTreeFunc1[10];nx10
10
```

As proof of our understanding of essential parse trees, let us try to construct a parse tree analogous to the one before for the statement:

```
1 + 2 * 3
7
```