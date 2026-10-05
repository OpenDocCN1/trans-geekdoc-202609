# 10.1.2 Parse Tree Creation

We can get the parse tree of a statement using parse:

```
parse str

(cos;(acos(-1j)))
```

```
eval parse str

-1f
```

This can be handy as a helper in creating functional select statements as we will illustrate later on.

# 10.1.3 Read-Only Evaluation

Read-only evaluation is performed with the function revel which has the same signature as eval. The verb revel simulates the effect of launching q with option -b, when accessing the instance remotely and running eval. By evaluating a parse tree using revel, the instance will block any incoming messages which attempt to amend global variables.

For instance, let us assume that we have a process with port number 5000. We open a handle to the port:

```
z: hopen 5000
```

We then define a variable on the opened process:

```
z "a:1"
```

We have seen this is equivalent to

```
z "eval(;;aa;1)"
```

```
1
```

If we use revel instead, the command will fail:

```
z "revel(;;aa;1)"
```

```
'noupdate: `aa
[[] z "revel(;;aa;1)"
AA
```

The same error is obtained when we use an IDE such as qPad, since it will connect to the q instance. Running the same in qPad:

```
revel(;;aa;1)
```

```
ERROR: 'noupdate: `a
```