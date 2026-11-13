an expression. The first name is the name of the function; you need it to apply the function as often as you wish. The second name—called a parameter—represents the input of the function, which is unknown until you apply the function. The expression, dubbed body, computes the output of the function for a specific input.

+   • Second,

```
(FunctionName ArgumentExpression)
```

is a function application. The first part tells DrRacket which function you wish to use. The second part is the input to which you want to apply the function. If you were reading a Windows or a Mac manual, it might tell you that this expression “launches” the “application” called FunctionName and that it is going to process ArgumentExpression as the input. Like all expressions, the latter is possibly a plain piece of data or a deeply nested expression.

Functions can input more than numbers, and they can output all kinds of data, too. Our next task is to create a function that simulates the second table—the one with images of a colored dot—just like the first function simulated the numeric table. Since the creation of images from expressions isn’t something you know from high school, let’s start simply. Do you remember empty-scene? We quickly mentioned it at the end of the previous section. When you type it into the interactions area, like that:

```
> (empty-scene 100 60)
```

![](bbox=[0.14, 0.69, 0.3, 0.765])

DrRacket produces an empty rectangle, also called a scene. You can add images to a scene with place-image: