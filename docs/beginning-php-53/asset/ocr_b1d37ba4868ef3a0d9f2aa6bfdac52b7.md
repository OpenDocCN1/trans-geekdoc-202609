# # 7

# # Functions

If you’ve been following the book up to now, you’re already familiar with the concept of functions. You’ve used built-in functions such as `gettype()` for determining the type of a variable, and `count()` that returns the number of elements in an array.

This chapter takes a formal look at functions, and shows why they’re so useful. You learn:

+   - More about how to call functions

+   - How to create your own functions to make your code easier to read and work with

+   - All about parameters and arguments — you use these to pass values into your functions — and how to return values from functions. (With these techniques, your functions can communicate with the code that calls them)

+   - Variable scope and how to use local, global, and static variables to your advantage

+   - How to create anonymous functions, which are useful when you need to create simple, disposable functions

Finally, toward the end of the chapter, you get to explore more advanced concepts, such as references — which let you function modify variables that were created in the code that calls it — and recursion, which you can use as an alternative to looping. First, though, it's a good idea to start at the beginning, and look at exactly what a function does.

# ## What Is a Function?

Generally speaking, a _function_ — also called a _subroutine_ in some other languages — is a self-contained block of code that performs a specific task. You define a function using a special syntax — which you learn about later in this chapter — and you can then call that function from elsewhere in your script.

A function often accepts one or more _arguments_, which are values passed to the function by the code that calls it. The function can then read and work on those arguments. A function may also