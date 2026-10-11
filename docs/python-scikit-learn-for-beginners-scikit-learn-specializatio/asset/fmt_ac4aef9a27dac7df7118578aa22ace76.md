
# For Loop

The `for` loop is used to iteratively execute a piece of code a certain number of times. You should use `for` loop when you know the exact number of iterations or repetitions for which you want to run your code. A `for` loop iterates over a collection of items. In the following example, we create a collection of five integers using the `range()` method. Next, a `for` loop iterates five times and prints each integer in the collection.

**Script 12:**
```
![](Image00054.jpg)
```
**Output:**
```
0 1 2 3 4
```

# While Loop

The `while` loop keeps executing a certain piece of code unless the evaluation condition becomes false. For instance, the `while` loop in the following script keeps executing unless the variable `c` becomes greater than 10.

**Script 13:**
```
![](Image00055.jpg)
```
**Output:**
```
0 1 2 3 4 5 6 7 8 9
```

# 2.2.6 Functions

Functions in any programming language are used to implement the piece of code that is required to be executed multiple times at different locations in the code. In such cases, instead of writing long pieces of code again and again, you can simply define a function that contains the piece of code, and then you can call the function wherever you want in the code.

To create a function in Python, the `def` keyword is used, followed by the name of the function and opening and closing parenthesis. Once a function is defined, you have to call it in order to execute the code inside a function body. To call a function, you simply have to specify the name of the function followed by the opening and closing parenthesis.

In the following script, we create a function named `myfunc`, which prints a simple statement on the console using the `print()` method.

**Script 14:**
```
![](Image00056.jpg)
```
**Output:**
```
This is a simple function
```

You can also pass values to a function. The values are passed inside the parenthesis of the function call. However, you must specify the parameter name in the function definition, too.

In the following script, we define a function named `myfuncparam()`. The function accepts one parameter, i.e., `num`. The value passed in the parenthesis of the function call will be stored in this `num` variable and will be printed by the `print()` method inside the `myfuncparam()` method.

**Script 15:**
```
![](Image00057.jpg)
```
**Output:**
```
This is a function with parameter value: Parameter 1
```

Finally, a function can also return values to the function call. To do so, you simply have to use the `return` keyword followed by the value that you want to return.

In the following script, the `myreturnfunc()` function returns a string value to the calling function.

**Script 16:**
```
![](Image00058.jpg)
```
**Output:**
```
This function returns a value
```

# 2.2.7 Objects and Classes

Python supports object-oriented programming (OOP). In OOP, any entity that can perform some function and have some attributes is implemented in the form of an object. For instance, a car can be implemented as an object since a car has some attributes, such as price, color, model, and it can perform some functions, such as drive car, change gear, stop car, etc. Similarly, a fruit can also be implemented as an object since a fruit has a price, name and you can eat a fruit, grow a fruit and perform functions with a fruit.

To create an object, you have to first define a class. For instance, in the following example, a class `Fruit` has been defined. The class has two attributes, `name` and `price`, and one method `eat_fruit()`. Next, we create an object `f` of class `Fruit`, and then call the `eat_fruit()` method from the `f` object. We also access the `name` and `price` attributes of the `f` object and print them on the console.

**Script 17:**
```
![](Image00059.jpg)
```
**Output:**
```
Fruit has been eaten
apple
10
```

A class in Python can have a special method called a constructor. The name of the constructor method in Python is `__init__()`. The constructor is called whenever an object of a class is created. Look at the following example to see a constructor in action.

**Script 18:**
```
![](Image00060.jpg)
```
**Output:**
```
Fruit has been eaten
Orange
15
```

---

## Further Readings – Python [1]

To study more about Python, please check Python 3 Official Documentation. Get used to searching and reading this documentation. It is a great resource of knowledge.

---

## Hands-on Time – Exercise

Now, it is your turn. Follow the instructions in the exercises below to check your understanding of the basic Python programming language concepts. The answers to these questions are given at the end of the book.

### Exercise 2.1

**Question 1:** Which iteration should be used when you want to repeatedly execute a code specific number of times?

1. For Loop
2. While Loop
3. C.
4. D.

**Question 2:** What is the maximum number of values that a function can return in Python?

1. Single Value
2. Double Value
3. C.
4. D.

**Question 3:** Which of the following membership operators are supported by Python?

1. In
2. Out
3. C.
4. D.

### Exercise 2.2

Print the table of integer 9 using a `while` loop:
