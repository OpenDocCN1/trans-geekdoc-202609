```
class Dog:

    # Initializer / Instance Attributes
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

In the following example, each dog has a unique name and age, which is critical to know especially when you begin to define different dogs. Don't forget that the class is only defining the Dog, and not creating objects of individual dogs with unique names and ages.
Similarly, the self-variable also belongs to an instance of the class. Because class instance has different values you can write Dog.name = name instead of self.name.

# Class Attributes

While instance attributes are unique to every object, characteristics of a class are the same for all instances. In this case, all dogs.

# Methods

When you have attributes that belong to a class, you can proceed to define functions that will access the class attribute. These functions are referred to as methods. When you declare methods, you will want to provide the first argument to the method using a self-keyword.
For instance, you can define a class Snake, which contains the attribute name and the method change_name. The method change name will accept the argument new_name plus you can instantiate this class with a variable snake and change the name using the method change_name.

```
>>> # instantiate the class
>>> snake = Snake()

>>> # print the current object name
>>> print(snake.name)
python

>>> # change the name using the change_name method
>>> snake.change_name("anaconda")
>>> print(snake.name)
anaconda
```