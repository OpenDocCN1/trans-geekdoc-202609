other features of python, is that you cannot use class to name a class because it is a designated python keyword. Spare it for good. You can use different attributes that belong to classes. Each instance in a python class represents an object. You can say that a class is original while an instance is its copy but has real values.

A class object may have its unique identity. It may show some behavioral traits. When you create an object, the process is dubbed as instantiation. You can add as many instances to a Python class as you like.

You will find in the code a parameter namely self. It is an extra parameter which doesn’t need a value. Python has already defined its value, which makes it similar to other programming languages such as Java and C++.

In the next code example, you will see a class namely Peacock. The peacock is a model of a real life object. I will assign it a name and an age. You can change the name and the figure to develop a unique object of your own choice. You can even change the name of the class. For example, you can name it as a Beaver or an Eagle. Just like I will do in the instance, you can define what kind of behavior you want the Peacock class to possess and display. My peacock will show you how to stand and fly away when fed with certain instructions. The behaviors can be anything like rolling on the ground, running in the wild or feeding itself. In short, you will have to assign it behaviors that a real-life object has. The rules are not defined. So, if you are creating a program for an animated series, you can assign the peacock the behavior of changing colors.

```
class Peacock():

    """This is a simple try to build a model of a peacock."""

    def __init__(self, namep, agep):

        """This will initialize the name and age attributes."""

    self.namep = namep
```