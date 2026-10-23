# Keeping Track of Names

Up until now we’ve referenced values in our Monkey code by using boolean and integer literals. That’s going to change. In this chapter we’re going to implement bindings, by adding support for let statements and identifier expressions. At the end, we’ll be able to bind any value to any name and then have that name resolve to the value.

As preparation, here’s a short refresher of what let statements in Monkey look like:

```
let x = 5 * 5;
```

As you can see, a let statement in Monkey starts with the let keyword followed by an identifier. The identifier is the name to which we want to bind a value, in this case it’s x. The right side of the = is an expression. It evaluates to the value the name will be bound to. And since it’s a let statement it’s followed by a semicolon. Let name equal value of expression; that’s it.

Referencing the value to which x has been bound is easy, since identifiers, which is what the x is in the terms of our AST, are expressions and can be used interchangeably. We can use x in every place where an expression is valid:

```
x * 5 * x * 5;
if (x < 10) { x * 2 } else { x / 2 };
let y = x + 5;
```

Let statements are valid as either top-level statements or inside a block statement, like the branches of a conditional or the body of a function. In this chapter, we’re only going to add support for the top-level and non-function-body block-statement varieties. We’ll tackle local variables, which is what let statements inside functions produce, when we implement functions and closures.

Our goal for this chapter is to be able to compile the following code to bytecode and have our VM execute it:

```
let x = 5 * 5;

if (x > 10) {
let y = x * 2;
```