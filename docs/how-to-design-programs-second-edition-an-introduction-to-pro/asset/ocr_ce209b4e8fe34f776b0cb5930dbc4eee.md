Click RUN and watch nothing happen. Nothing shows up in the interactions area. Nothing seems to change anywhere else in DrRacket. It is as if you hadn’t accomplished anything. But you did. You actually defined a function and informed DrRacket about its existence. As a matter of fact, the latter is now ready for you to use the function. Enter

```
(y 1)
```

at the prompt in the interactions area and watch a 1 appear in response. The (y 1) is called a function application in DrRacket. Try

```
(y 2)
```

and see a 4 pop out. Of course, you can also enter all these expressions in the definitions area and click RUN:

```
(define (y x) (* x x))
(y 1)
(y 2)
(y 3)
(y 4)
(y 5)
```

In response, DrRacket displays: 1 4 9 16 25, which are the numbers from the table. Now determine the missing entry.

What all this means for you is that functions provide a rather economic way of computing lots of interesting values with a single expression. Indeed, programs are functions; and once you understand functions well, you know almost everything there is to know about programming. Given their importance, let’s recap what we know about functions so far:

+   First,

```
(define (FunctionName InputName) BodyExpression)
```

is a function definition. You recognize it as such because it starts with the “define” keyword. It essentially consists of three pieces: two names and