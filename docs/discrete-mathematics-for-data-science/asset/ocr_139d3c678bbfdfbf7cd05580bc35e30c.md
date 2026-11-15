```
{ inner_scope } E WORD
{ E outer_scope } λx.E WORD
```

For example:

```
{ 1 + } E WORD
{ E ’ EXEC } λx.E WORD
3 λx.E ( → 4)
```

3 More about this is discussed in the chapter on Computability.

In the above example, the lambda expression λx.E is a function in which every element in E is bound to its local scope. The integer 1 is bound to a variable in the scope of the guest function E, whereas the integer 3 is not. If 3, a concrete parameter, were replaced by a variable, such as y, then y would be considered a free variable.

Some languages use a let keyword to explicitly relegate a variable's effectiveness to a local environment, or to that of a lambda expression. This may be referred to as let over lambda.4 Consider for example the use of the LET word in the following application that computes the λx.2x + 1:

```
{ 2 * y LET } λy.y WORD
{ TEL 1 + } λx WORD
{ λy.y λx } λx.λy.y WORD
3 λx.λy.y ( → 7)
```