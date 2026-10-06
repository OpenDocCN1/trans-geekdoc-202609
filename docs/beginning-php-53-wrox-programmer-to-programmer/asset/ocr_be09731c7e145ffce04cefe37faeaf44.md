# Chapter 3: PHP Language Basics

Many programming languages prevent you from using a variable without explicitly declaring (creating). But PHP lets you use variables at any point just by naming them. This is not always the blessing you might think; if you have to use a nonexistent variable by mistake, no error message is generated, and you may end up with a hard-to-find bug. In most cases, it works fine and is a helpful feature.

When you declare a variable in PHP, it's good practice to assign a value to it at the same time. This is known as initializing a variable. By doing this, anyone reading your code knows exactly what the variable holds at the time it's created. (If you don't initialize a variable in PHP, it's given the default value of null.)

Here's an example of declaring and initializing a variable:

```
$my_first_variable = 3;
```

This creates the variable called my_first_variable, and uses the = operator to assign it a value of 3. (You look at it and other operators later in this chapter).

Looking back at the addition earlier, the following script creates two variables, initializes them with values 5 and 6, and outputs their sum (11):

```
$x = 5;
$y = 6;
echo $x + $y;
```

# Understanding Data Types

All data stored in PHP fall into one of eight basic categories, known as data types. A variable's data type determines what operations can be carried out on the variable's data, as well as the amount of memory needed to hold the data.

PHP supports four scalar data types. Scalar data means data that contains only a single value. Here's a list of them, including examples:

| Scalar Data Type | Description | Example |
|---|---|--|
| Integer | A whole number | 15 |
| Float | A floating-point number | 8.23 |
| String | A series of characters | "Hello, world!" |
| Boolean | Represents either true or false | true |