# Part III: Using PHP Practice

By the end of this chapter you'll have the know-how to create PHP applications that are robust, secure, and easy for you and other programmers to work with, no matter how large or complex your applications may be. So let's get started!

# Writing Modular Code

In Chapter 15 you already explored the concept of modular code — that is, small chunks of code that you can reuse again and again. PEAR packages are a great example. Each PEAR package is a self-contained collection of code that does a specific task. Many PEAR packages have been used thousands and thousands of times by developers all the globe.

Writing modular code gives you many advantages, including:

+   - Reuse: You only have to write the code once, and then you can use it many times throughout your various applications

+   - Ease of maintenance: Rather than having seven copies of the same code throughout your apps, you can keep the code in a single place. If you need to add any functionality to the code, or a bug, you only have to change one copy of the code

+   - Readability: By splitting your code into chunks you make your application easier to read and understand

+   - Efficiency: Rather than having your application in one huge file — which the PHP engine has to load and interpret for each page view — you can load only the code you need to carry out each request

PHP contains a number of features that help you write modular code, including:

+   - Functions: In Chapter 7 you saw how you can encapsulate a chunk of code within a function, and then reuse that code simply by calling the function from elsewhere in your application code

+   - Classes: These take the concept of code encapsulation, further letting you store both functionality and properties within a single scope. You learned all classes and objects in Chapter 8

+   - include() and require(): These two PHP functions — and their related functions, include_once() and require_once() — let you include the code from one file into another script file

+   - Namespaces: These are useful for large applications and libraries. They help to avoid clashes where the same class name, function name, or constant name is accidentally used in different libraries, or in different parts of an application

Functions and classes have been covered in detail in Chapters 7 and 8. Here you take a look at include(), require(), include_once(), and require_once(), and learn how to use them to create modular, reusable code files. You also take a brief look at namespaces, and see how they can be useful for larger projects.

620