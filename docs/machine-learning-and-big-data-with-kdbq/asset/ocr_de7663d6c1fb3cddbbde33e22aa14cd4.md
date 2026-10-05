# 32

and a list of names within our hypothetical analysis involving multiple occurrences of the vector of assetNames:
name: `IBM` `INT` `IBM` `INT` `IBM` `INT` `AAPL` `INT` `IBM` `INT` `IBM` `INT` `AAPL` `INT` `IBM` `AAPL`;
type name

We now `cast`, i.e. enumerate the list of symbols against the domain of values:
name2:`assetNames$name2`;
type name2

20h
as expected from Table 1.1;; enumerated types take values from 20h to 76h so the actual outcome will depend on what was already enumerated within the q session.
We can see what name2 looks like:

```
name2
`assetNames$`IBM` `INT` `IBM` `INT` `AAPL` `IBM` `IBM` `INT` `AAPL` `IBM` `INT` `INT` `AAPL`_
`IBM` `AAPL`
```

Let us try to append a value into the list name2 which is within the specified type, and one is not:
name2, `IBM`

i.e. no problem, the new item was added. In contrast,
name2, `C`

`cast
 thus the specified type restricts us to the list of values within an enumerated list. We cannot add `C` into our analysis unless we specify a new item into assetNames.
If we try a slightly different version of the previous command
name2:name2, `C`

we do not obtain any error message and the command will go through without any issue. Why? Let us investigate:
type name2

11h
q has recast name2 back into a non-enumerated symbol type. This is because in the first case we amended name2 *in-place*, i.e. by reference, and the new value was missing from our enumeration. In the second example, q un-enumerated the result of name2, `C` since since `C` was not an element of the enumeration domain.