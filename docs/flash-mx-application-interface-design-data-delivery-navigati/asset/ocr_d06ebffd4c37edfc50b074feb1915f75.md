Hopefully now you can see how the combination of storing all the data about each leaf in an array and passing that same information into a custom class allows us to easily make new instances of a leaf each with its own unique properties simply by adding more information to the leafMap array. Adding new properties for each leaf also requires changes to just a few lines of code inside the class constructor function.

To finish up this part of the code, we now go back and look inside the Leaf class constructor to see what makes it tick. It's pretty straightforward. Looking at the first argument, name, that we passed into the constructor function, when we create our instance of the Leaf object we give it a property called name, with a unique value, by saying something like:

```
this.name = name;
```

What the above line of code does is say to the Leaf object instance create a property for me (this – meaning this instance) called name, and give it a value equal to the name argument that was passed into the Leaf class constructor function when the instance is created. Based on this principle, the rest of the code inside the Leaf class constructor should be quite easy to understand and follow.

Notice how we can also create properties that are defined by mathematical calculations based on the various arguments that we pass in, such as:

```
this.stopX = stopX - plantSize;
```

As you'll see later on, we'll use the stopX property to help determine the size of each leaf. We'll also increment the value of the variable plantSize so that when we repeatedly call the function named drawLeaf, the plant will grow in size and so appear to animate.

The last piece of code that.I'd like to talk about in the Leaf class constructor is the one that looks like:

```
this.ID = setInterval(drawLeaf, 10,
this.name, this.dir, this.levelNum,
this.originX, this.originY, this.stopX,
this.stopY, this.controlX,
this.controlY, this.thickness);
```

You can get away without specifying this before all the arguments in this setInterval function, but it might help you to remember that those properties now actually belong to the Leaf object instance we created, and also to show that the set of arguments inside the setInterval function are slightly different in order and value from the arguments we originally passed into the Leaf class constructor function.

What does the above line of code do? It creates a setInterval action, which in turn executes a function we define in the parameters of the setInterval, and it will do this every x amount of milliseconds.

Remember that each instance of a leaf on our plant is an object that we created when we called the Leaf class constructor. We can see that for each leaf instance, we create a property called ID, and the value of this property is a setInterval action that executes a function named drawLeaf every 10 milliseconds and passes a whole bunch of arguments into that function. Too easy! The reason for using the setInterval in this way is that by giving it a name, or identifier, we can destroy or stop it when we no longer need it.

I use setInterval here rather than onEnterFrame because with an onEnterFrame method you can't accurately control when you want a function to be called each time, and you can't always easily delete the onEnterFrame action once it's no longer needed. For these reasons using setInterval saves on processor usage, ensuring that the code runs as smoothly as possible.