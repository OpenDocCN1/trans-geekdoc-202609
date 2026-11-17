As you can see, reducing the Red value and increasing the Green value of our plant by the variable `plantSize` as the user visits the site will conveniently turn the plant from brown to green!

To execute the function and create a variable whose value is a hex string representing a color that we’ll use to color our plant, we write:

```
convertColors("fillColor", (200-plantSize),
➥ (150+plantSize), 0);
```

We end up with a variable named `fillColor` that has a string value of `0xC39B00`. Then we do the same again to store the color for the outline of the plant:

```
convertColors("outlineColor", (150-
➥ plantSize), (100+plantSize), 0);
```

which gives us a variable named `outlineColor`, which
has a string value of `0x906A00`.

So now we’ve created some variables to store the value of
the outline and fill colors of the plant, and seeing as we’ve
created this neat little function already, we may as well use
it to create the colors for the pot that the plant sits in, by
dynamically creating the variables `potFill` and
`potColor`:

```
convertColors("potOutline", 0, 102, 255);
convertColors("potFill", 0, 153, 255);
```

![](bbox=[0.0, 0.56, 0.999, 0.915])