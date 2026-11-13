
an expression. The first name is the name of the function; you need it to apply the function as often as you wish. The second name—called a parameter—represents the input of the function, which is unknown until you apply the function. The expression, dubbed body, computes the output of the function for a specific input.

- Second,

```
(FunctionName ArgumentExpression)
```

is a function application. The first part tells DrRacket which function you wish to use. The second part is the input to which you want to apply the function. If you were reading a Windows or a Mac manual, it might tell you that this expression “launches” the “application” called FunctionName and that it is going to process ArgumentExpression as the input. Like all expressions, the latter is possibly a plain piece of data or a deeply nested expression.

Functions can input more than numbers, and they can output all kinds of data, too. Our next task is to create a function that simulates the second table—the one with images of a colored dot—just like the first function simulated the numeric table. Since the creation of images from expressions isn’t something you know from high school, let’s start simply. Do you remember empty-scene? We quickly mentioned it at the end of the previous section. When you type it into the interactions area, like that:

```
> (empty-scene 100 60)
```

![](img/19fbe4068996ced0ce42cec7fb82a834_47_0.png)

DrRacket produces an empty rectangle, also called a scene. You can add images to a scene with place-image:

```
> (place-image 50 23 (empty-scene 100 60))
```

![](img/19fbe4068996ced0ce42cec7fb82a834_48_0.png)

Think of the rocket as an object that is like the dot in the above table from your mathematics class. The difference is that a rocket is interesting.

Next, you should make the rocket descend, just like the dot in the above table. From the preceding section, you know how to achieve this effect by increasing the y-coordinate that is supplied to place-image:

```
> (place-image rocket 50 20 (empty-scene 100 60))
```

![](img/19fbe4068996ced0ce42cec7fb82a834_49_0.png)

```
> (place-image rocket 50 30 (empty-scene 100 60))
```

![](img/19fbe4068996ced0ce42cec7fb82a834_49_1.png)

```
> (place-image rocket 50 40 (empty-scene 100 60))
```

![](img/19fbe4068996ced0ce42cec7fb82a834_49_2.png)

All that's needed now is to produce lots of these scenes easily and to display all of them in rapid order.

The first goal can be achieved with a function, of course; see figure 4. Yes, this is a function definition. Instead of y, it uses the name picture-of-rocket, a name that immediately tells you what the function outputs: a scene with a rocket. Instead of x, the function definition uses height for the name of its parameter, a name that suggests that it is a number and that it tells the function where to place the rocket. The body expression of the function is exactly like the series of expressions with which we just experimented, except that it uses height in place of a number. And we can easily create all of those images with this one function:

```
(picture-of-rocket 0)
(picture-of-rocket 10)
(picture-of-rocket 20)
(picture-of-rocket 30)
```

```
(define (picture-of-rocket height)
  (place-image 🚀 50 height (empty-scene 100 60)))
```

## Figure 4: Landing a rocket (version 1)

Try this out in the definitions area or the interactions area; both create the expected scenes.

In BSL, you can use all kinds of characters in names, including “-” and “.”.

The second goal requires knowledge about one additional primitive operation from the 2htdp/universe library: animate. So, click RUN and enter the following expression:

```
> (animate picture-of-rocket)
```

Stop and note that the argument expression is a function. Don’t worry for now about using functions as arguments; it works well with animate, but don’t try to define functions like animate at home just yet.

Don’t forget to add the 2htdp/universe library to your definitions area.

As soon as you hit the “return” key, DrRacket evaluates the expression; but it does not display a result, not even a prompt. It opens another window—a canvas—and starts a clock that ticks 28 times per second. Every time the clock ticks, DrRacket applies picture-of-rocket to the number of ticks passed since this function call. The results of these function calls are displayed in the canvas, and it produces the effect of an animated movie. The simulation runs until you close the window. At that point, animate returns the number of ticks that have passed.

The question is where the images on the window come from. The short explanation is that animate runs its operand on the numbers 0, 1, 2, and so on, and displays the resulting images. The long explanation is this:

- animate starts a clock and counts the number of ticks;
- the clock ticks 28 times per second;
- every time the clock ticks, animate applies the function picture-of-rocket to the current clock tick; and
- the scene that this application creates is displayed on the canvas.

This means that the rocket first appears at height 0, then 1, then 2, and so on, which explains why the rocket descends from the top of the canvas to the bottom. That is, our three-line program creates some 100 pictures in about 3.5 seconds, and displaying these pictures rapidly creates the effect of a rocket descending to the ground.

*Exercise 298 explains how to design animate.*

So here is what you learned in this section. Functions are useful because they can process lots of data in a short time. You can launch a function by hand on a few select inputs to ensure that it produces the proper outputs. This is called testing a function. Or, DrRacket can launch a function on lots of inputs with the help of some libraries; when you do that, you are running the function. Naturally, DrRacket can launch functions when you press a key on your keyboard or when you manipulate the mouse of your computer. To find out how, keep reading. Whatever triggers a function application isn’t important, but do keep in mind that (simple) programs are functions.

## Many Ways to Compute

When you evaluate `(animate picture-of-rocket)`, the rocket eventually disappears into the ground. That’s plain silly. Rockets in old science fiction movies don’t sink into the ground; they gracefully land on their bottoms, and the movie should end right there.

This idea suggests that computations should proceed differently, depending on the situation. In our example, the picture-of-rocket program should work “as is” while the rocket is in flight. When the rocket’s bottom touches the bottom of the canvas, however, it should stop the rocket from descending any farther.

In a sense, the idea shouldn’t be new to you. Even your mathematics teachers define functions that distinguish various situations:

sign(x) = 

| Condition | Result |
|-----------|--------|
| x > 0     | +1     |
| x = 0     | 0      |
| x < 0     | -1     |

This *sign* function distinguishes three kinds of inputs: those numbers that are larger than 0, those equal to 0, and those smaller than 0. Depending on the input, the result of the function is +1, 0, or -1.

You can define this function in DrRacket without much ado using a conditional expression:

```
(define (sign x)
  (cond
    [(> x 0) 1]
    [(= x 0) 0]
    [(< x 0) -1]))
```

After you click *RUN*, you can interact with *sign* like any other function:

```
> (sign 10)
1
> (sign -5)
-1
> (sign 0)
0
```

Open a new tab in DrRacket and start with a clean slate.

In general, a *conditional expression* has the shape

```
(cond
  [ConditionExpression1 ResultExpression1]
  [ConditionExpression2 ResultExpression2]
  ...
  [ConditionExpressionN ResultExpressionN])
```

This is a good time to explore what the *STEP* button does. Add *(sign -5)* to the definitions area and click STEP for the above sign program. When the new window comes up, click the right and left arrows there.

That is, a conditional expression consists of as many *conditional lines* as needed. Each line contains two expressions: the left one is often called *condition*, and the right one is called *result*; occasionally we also use *question* and *answer*. To evaluate a cond expression, DrRacket evaluates the first condition expression, *ConditionExpression1*. If this yields #true, DrRacket replaces the cond expression with *ResultExpression1*, evaluates it, and uses the value as the result of the entire cond expression. If the evaluation of *ConditionExpression1* yields #false, DrRacket drops the first line and starts over. In case all condition expressions evaluate to #false, DrRacket signals an error.

With this knowledge, you can now change the course of the simulation. The goal is to not let the rocket descend below the ground level of a 100-by-60 scene. Since the *picture-of-rocket* function consumes the height where it should place the rocket in the scene, a simple test comparing the given height to the maximum height appears to suffice.

See figure 5 for the revised function definition. The definition uses the name *picture-of-rocket.v2* to distinguish the two versions. Using distinct names also allows us to use both functions in the interactions area and to compare the results. Here is how the original version works:

```
> (picture-of-rocket 5555)
```

![](img/19fbe4068996ced0ce42cec7fb82a834_53_0.png)

```
(define (picture-of-rocket.v2 height)
  (cond
    [(<= height 60)
     (place-image
      [rocket icon]
      50 height
      (empty-scene 100 60))]
    [(> height 60)
     (place-image
      [rocket icon]
      50 60
      (empty-scene 100 60))]))
```
