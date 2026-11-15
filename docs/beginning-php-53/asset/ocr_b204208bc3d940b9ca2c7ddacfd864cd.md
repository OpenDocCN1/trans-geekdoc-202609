The wonderful thing about inheritance is that, if you want to create a lot of similar classes, you have to write the code that they have in common only once, in the parent class. This saves you from duplicating code. Furthermore, any outside code that can work with the parent class automatically has the ability to work with its child classes, provided the code works only with the properties and methods contained in the parent class.

Imagine that you’re creating a program to deal with various regular shapes, such as circles, squares, equilateral triangles, and so on. You want to create a Shape class that can store information such as number of sides, side length, radius, and color, and that can calculate values such as the shape’s area and perimeter. However, not all shapes are the same. Circles don’t really have a clearly defined number of sides, and you calculate an equilateral triangle’s area using a different formula than for a square. So if you wanted to handle all types of regular shapes in a single Shape class, your class’s code would get quite complicated.

By using inheritance, however, you can break the problem down into simpler steps. First, you create a parent Shape class that contains just those properties and methods that are common to all shapes. Then, you can create child classes such as Circle, Square, and Triangle that inherit from the Shape class.

To create a child class that’s based on a parent class, you use the extends keyword, as follows:

```
class Shape {
  // (General Shape properties and methods here)
}

class Circle extends Shape {
  // (Circle-specific properties and methods here)
}
```

# # Try It Out Create a Parent Class and Child Classes

The following script shows inheritance in action. It creates a parent Shape class, holding properties and methods common to all shapes, then creates two child classes based on Shape — Circle and Square — that contain properties and methods related to circles and squares, respectively.

Save the script as inheritance.php in your document root folder, then run the script in your Web browser. You should see the page shown in Figure 8-5.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Creating Shape Classes using Inheritance</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Creating Shape Classes using Inheritance</h1>

<?php
```