# Soft Computing and Machine Learning with Python

Note that the constructor method does not (and cannot) include a return statement. The value of self is implicitly returned to the statement that called the constructor.

As for the other methods of class, their definitions also start with the special argument self that contains the instance namespace. For any method that takes $N$ arguments, the caller passes only the last $N$-arguments to it.

In our example class, the def for the .show() method has one argument named self, the caller invokes it with no arguments at all:

```
>>> kyleRace3=SnailRun('Kyle', 96.6)
>>> kyleRace3.show()
```

Snail ‘Kyle’ finished in 96.6 minutes.

# Life Cycle Of An Instance

To really understand what is going inside a running Python program, let’s follow the creation of an instance of the SnailRun class from the preceding section.

Just for review, let’s assume you are using conversational mode, and you create a variable like this:

```
>>> badPi = 3.00
```

Whenever you start up Python, it creates the “global namespace” to hold the names and values you define. After the statement above, here’s how it looks.

# Global namespace

| Name Value |
|---|---|
| badPi | float 3.0 |

Next, suppose you type in the class definition as above. As it happens, a class is a namespace too—it is a container for methods. So the global namespace now has two names in it: the variable badPi and the class SnailRun. Here is a picture of the world after you define the class:

![](bbox=[0.356, 0.735, 0.643, 0.765])