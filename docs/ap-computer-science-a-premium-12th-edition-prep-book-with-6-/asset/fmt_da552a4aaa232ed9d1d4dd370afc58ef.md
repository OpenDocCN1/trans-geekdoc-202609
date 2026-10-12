
There are certain errors that are not penalized. For example, the graders will look the other way if you omit semicolons, or misspell identifiers, or use keywords as identifiers, or confuse `length` with `length()`, or use `=` instead of `==`, or use the wrong kind of brackets for an array element.

They will, however, deduct points for each of the following types of errors:

![](images/sq1.jpg)Including output statements in methods that don't require it.

![](images/sq1.jpg)Including an output statement in a method, instead of returning a value. (Are you clear on this? No `System.out.print()` or `System.out.println()` statements in methods that didn't ask for output!).

![](images/sq1.jpg)Using local variables that aren't declared.

![](images/sq1.jpg)Returning the wrong type of value in a method, or returning a value in a `void` method, or having a constructor return a value.

![](images/sq1.jpg)Using incorrect syntax for traversing and processing arrays and `ArrayList`s.

Take heart: On any given question, you won't receive a negative score!

### Writing Code

Here are important reminders for the code that you write:

![](images/sq1.jpg)It's worth repeating: You must use Java for your solutions. No pseudocode, or C++, or any other programming language.

![](images/sq1.jpg)If the statement of the question provides an algorithm, you should say "thank you" and use it. Don't waste time trying to reinvent the wheel.

![](images/sq1.jpg)Don't omit a question just because you can't come up with a complete solution. Remember, partial credit is awarded. Also, don't omit part (b) of a question just because you couldn't do part (a)—the various parts of a question are graded independently.

![](images/sq1.jpg)In writing solutions to a question, you must use the public methods of classes provided in that question wherever possible. If you write a significant chunk of code that can be replaced by a call to one of those methods, you will probably not receive full credit for the question.

![](images/sq1.jpg)If you're writing a subclass of a given superclass, don't rewrite the public methods of that class unless you are overriding them. All public methods are inherited.

![](images/sq1.jpg)It is fine to use methods from the Java library that are not in the AP Java subset. You will receive full credit if you use those methods correctly. If your usage, however, is incorrect, your solution will be penalized. Note that there is always a solution that uses the subset, and you should try to find it.

![](images/sq1.jpg)It is fine to write a helper method for your solution. But be aware that usually you can solve the question using methods that are already provided.

### Maximizing Your Score

Here are some final general tips for maximizing your free-response score:

![](images/sq1.jpg)At the start of the free-response section, clear the decks! The multiple-choice section is over, and whether you did great or not, it is past history. Take a deep breath and psych yourself up for the code-writing part of the exam. Now is the time to strut your stuff.

![](images/sq1.jpg)Don't ever erase a solution. Cross it out. You want to avoid a situation in which you erased some code, but don't have time to write the replacement code.

![](images/sq1.jpg)If you can't see a solution to a question, but have some understanding of what is required to solve it, write something down. Just showing that you understand that you must loop through all of the elements in a list, for example, may earn you a point from the rubric.

![](images/sq1.jpg)Don't provide more than one solution for a given part. The exam readers are instructed to grade the first attempt only, and to ignore all subsequent ones. Not even the most warm-hearted among us will go wading through the marshes of your various solutions, searching for the one that solves the problem correctly. This means that you must choose one solution and cross out the others with firm, legible lines.

![](images/sq1.jpg)One final reminder: Use clear, readable code from the AP Java subset. Avoid obscure, opaque brilliancies. The AP exam is not the place to show the world you're a genius.

Good luck!

# Introductory Java Language Features

*Fifty loops shalt thou make ...*

—Exodus 26:5

**Learning Objectives**

In this chapter, you will learn:

➜Packages and classes

➜Types and identifiers

➜Operators

➜Input/output

➜Control structures

➜Errors and exceptions

The AP Computer Science course includes algorithm analysis, data structures, and the techniques and methods of modern programming—specifically, object-oriented programming. A high-level programming language is used to explore these concepts. Java is the language currently in use on the AP exam.

Java was developed by James Gosling and a team at Sun Microsystems in California; it continues to evolve. The AP exam covers a clearly defined subset of Java language features that are presented throughout this book. A complete listing of this subset can be found on the College Board website.

Java provides basic control structures such as the `if-else` statement, `for` loop, enhanced `for` loop, and `while` loop, as well as fundamental built-in data types. But the power of the language lies in the manipulation of user-defined types called *objects*, many of which can interact in a single program.

### Packages and Classes

A typical Java program has user-defined classes whose objects interact with those from Java class libraries. In Java, related classes are grouped into *packages*, many of which are provided with the compiler. For example, the package `java.util` contains the collections classes. Note that you can put your own classes into a package—this facilitates their use in other programs.

The package `java.lang`, which contains many commonly used classes, is automatically provided to all Java programs. To use any other package in a program, an `import` statement must be used. To import all of the classes in a package called `packagename`, use the form

```
import packagename.*;
```

Note that the package name is all lowercase letters. To import a single class called `ClassName` from the package, use

```
import packagename.ClassName;
```

Java has a hierarchy of packages and subpackages. Subpackages are selected using multiple dots:

```
import packagename.subpackagename.ClassName;
```

For example,

```
import java.util.ArrayList;
```

The `import` statement allows the programmer to use the objects and methods defined in the designated package. You will not be expected to write any `import` statements.

A Java program must have at least one class, the one that contains the *main method*. The Java files that comprise your program are called *source files*.

A *compiler* converts source code into machine-readable form called *bytecode*.

Here is a typical source file for a Java program:

![images](images/f064-02.jpg)

### Note

**1.** All Java methods must be contained in a class.

**2.** The words `class`, `public`, `static`, and `void` are *reserved words*, also called *keywords*. (This means they have specific uses in Java and may not be used as identifiers.)

**3.** The keyword `public` signals that the class or method is usable outside of the class, whereas `private` data members or methods (see [Chapter 3](#48_Chapter40.xhtml#ch3)) are not.

**4.** The keyword `static` is used for methods that will not access any objects of a class, such as the methods in the `FirstProg` class in the example above. This is typically true for all methods in a source file that contains no *instance variables* (see [Chapter 3](#48_Chapter40.xhtml#ch3)). Most methods in Java do operate on objects and are not static. The `main` method, however, must always be static.

**5.** The program shown above is a Java *application*.
