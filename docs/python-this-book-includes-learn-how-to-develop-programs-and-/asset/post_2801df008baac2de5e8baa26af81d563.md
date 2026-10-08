
A quadrilateral class having four sides as instance variables and a perimeter() method is defined below:

```python
class quadrilateral:
    def __init__(self, a, b, c, d):
        self.side1=a
        self.side2=b
        self.side3=c
        self.side4=d

    def perimeter(self):
        p=self.side1 + self.side2 + self.side3 + self.side4
        print("perimeter=",p)
```

The constructor (the __init__()) method) receives four parameters and assigns them to four instance variables. To test the above class, declare its object and invoke the perimeter() method.

```
>>>q1=quadrilateral(7,5,6,4)
>>>q1.perimeter()
perimeter=22
```

We design a rectangle class based upon the quadrilateral class (rectangle IS A quadrilateral!). The instance variables and the perimeter() method from the base class should be automatically available to it without redefining it.
Since opposite sides of the rectangle are the same, we only need two adjacent sides to construct its object. Hence, the other two parameters of the __init__() method are set to none. The __init__ method forwards the parameters to the constructor of its base (quadrilateral) class using the super() function. The object is initialized with side3 and side4 set to none. Opposite sides are equal by the constructor of the rectangle class. Remember that it has automatically inherited the perimeter() method. Hence there is no need to redefine it.

Example: Inheritance
```python
class rectangle(quadrilateral):
    def __init__(self, a, b):
        super().__init__(a, b, a, b)
```

We can now declare the object of the rectangle class and call the perimeter() method.
```
>>> r1=rectangle(10, 20)
>>> r1.perimeter()
perimeter=60
```

# Overriding in Python

In the above example, we see how resources of the base class are reused while constructing the inherited class. However, the inherited class can have its own instance attributes and methods.
Methods of the parent class are available for use in the inherited class. However, if needed, we can modify the functionality of any base class. For that purpose, the inherited class contains a new definition of a method (with the same name and the signature already present in the base class). Naturally, the object of a new class will have access to both methods, but the one from its own class will have precedence when invoked. This is called method overriding.

First, we define a new method area() in the rectangle class and use it as a base for the square class. The area of the rectangle is the product of its adjacent sides.

Example:
```python
class rectangle(Quadrilateral):
    def __init__(self, a, b):
        super().__init__(a, b, a)

    def area(self):
        a = self.side1 * self.side2
        print("area of rectangle=", a)
```

Let us define the square class which inherits the rectangle class. The area() method is overridden to implement the formula for the area of the square as the square of its sides.

Example:
```python
class square(rectangle):
    def __init__(self, a):
        super().__init__(a, a)
    def area(self):
        a=pow(self.side1, 2)
        print('Area of Square: ', a)
```

```
>>>s=Square(10)
>>>s.area()
Area of Square: 100
```

# Chapter 11: Introduction to Django Framework

Django is one of the most advanced Python web frameworks that allows rapid development and maintenance of websites. The Django framework handles most of the pros and cons of web development, so you can concentrate on building your app without the need to build something afresh. Django is free and open-source and has an active community and excellent documentation. Django will help you to build software that is:

- Complete
Django uses the “Batteries included” principle and has about everything that developers want to do. Since everything you require is part of the onestop-shop, it works seamlessly together, follows a regular design principle, and has up-to-date documentation.

- Scalable
Django features a component-based “shared-nothing” format and can thus be substituted or changed when necessary. Having a clear distinction between the different parts implies that it can scale for increased traffic by including hardware at any level. Some of the busiest websites have successfully scaled Django to achieve their demands.

- Versatile
You can use Django to create any website that you want-right from content management systems to social networks and news sites. This framework can work with any client-side framework and can support content in any format.

- Easy to maintain
The Django framework is built according to the principles of design that support code reusability. It also allows the grouping of similar functions into reusable “applications”.

- Portability
Django is developed in Python which runs on multiple platforms. In other words, you’re not forced to use a specific server platform alone, but you can run applications on any platform of your choice.

- It’s secure
Developers have nothing to fear that hackers will steal vital information from their websites or gain entry into their website applications. Django has an excellent security system that automatically protects the website.

## Where Did Django Come From?
Django was developed between 2003-2005 by a team of web experts who were responsible for building and managing newspaper websites. After making several websites, the team started to reuse most of the standard code and design patterns. This common code resulted in a general web development framework.
Since 2005 when it was open-sourced, Django continued to expand with new releases. Each release brought new functionality and fixed several bugs.
Today, Django is driving the development environment with thousands of users going for Django. Although it still has some properties that reflect its origin, Django has evolved into powerful framework that can build any website.

## What is the Level of Popularity of Django?
There’s no readily-available scale of measurement of server-side frameworks' popularity. An excellent question will be if Django is good enough to handle problems of unpopular platforms. Is it still developing? Can you get assistance if you need it? Is there a chance for you to get a job if you learn Django?

Depending on the number of high-profile websites that use Django, the number of people who contribute to the codebase, and the number of people providing free and paid help, Django is a popular framework.

### Is it Opinionated?
Web frameworks are said to be “opinionated”, and “unopinionated”. An opinionated framework is one that has opinions about the “correct way” to do a task. These frameworks support rapid development in a specific domain because the proper way to do anything is well-understood. Despite that, they can be less flexible at finding solutions and provide fewer choices for what methods they use. On the other hand, unopinionioned frameworks have fewer limitations on the right way to integrate components to accomplish a given goal. They simplify everything for developers to employ the most suitable tools.

In one way, Django is a bit opinionated, and therefore offers the “best of worlds”. It provides a set of components to take care of web development tasks and one preferred style to use them. Despite that, Django’s decoupled architecture implies that you can select and choose from different options, or include support for new ones if necessary.
