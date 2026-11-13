doesn't know the exact number, it warns you with this special prefix. Later, we will show you really strange facts about “computer numbers,” and you will then truly appreciate that DrRacket issues such warnings.

By now you might be wondering whether DrRacket can add more than two numbers at once, and yes, it can! As a matter of fact, it can do it in two different ways:

```
> (+ 2 (+ 3 4))
9
> (+ 2 3 4)
9
```

The first one is _nested arithmetic_, as you know it from school. The second one is _BSL arithmetic_; and the latter is natural, because in this notation you always use parentheses to group operations and numbers together.

> This book does not teach you Racket, even if the editor is called DrRacket. See the Preface, especially the section on DrRacket and the Teaching Languages for details on the choice to develop our own language.

In BSL, every time you want to use a “calculator operation,” you write down an opening parenthesis, the operation you wish to perform, say +, the numbers on which the operation should work (separated by spaces or even line breaks), and, finally, a closing parenthesis. The items following the operation are called the _operands_. Nested arithmetic means that you can use an expression for an operand, which is why

```
> (+ 2 (+ 3 4))
9
```

is a fine program. You can do this as often as you wish:

```
> (+ 2 (+ (* 3 3) 4))
15
> (+ 2 (+ (* 3 (/ 12 4)) 4))
15
> (+ (* 5 5) (+ (* 3 (/ 12 4)) 4))
38
```