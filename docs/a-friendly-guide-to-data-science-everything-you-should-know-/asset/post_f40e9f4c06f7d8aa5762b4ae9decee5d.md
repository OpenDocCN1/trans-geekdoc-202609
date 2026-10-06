
## CHAPTER 11 TOOLS OF THE TRADE: PYTHON AND R

### PSEUDOCODE AND CODE STEP-THROUGH

Pseudocode is basically the steps of an algorithm, basically code, in human language. When you're first learning programming, it's often beneficial to write things out this way so you can understand what the logic and flow is.

It's also to write down what happens at every step of the pseudocode with actual values to see what happens. For example, a step-through of the code in Figure 11-4 would start off something like this:

| num | value |
| :--- | :--- |
| 0 | The square of 0 is 0. |
| 1 | The square of 1 is 1. |
| 2 | The square of 2 is 4. |
| 3 | The square of 3 is 9. |
| 4 | The square of 4 is 16. |
| 5 | The square of 5 is 25. |
| 6 | The square of 6 is 36. |
| 7 | The square of 7 is 49. |
| 8 | The square of 8 is 64. |
| 9 | The square of 9 is 81. |

This can help you see what's going on and find problems, especially in trickier code.

Python has the for loop and the while loop. The for loop uses the keywords `for` and `in` to set it up, and the while loop uses `while`. R has the same keywords but also has another loop similar to a while loop, which uses the keyword repeat. This one is just like a while loop, but it has no condition and only stops running when the keyword break is used inside the loop. So it always runs up to the first appearance of the loop break. A while loop may never run all if the initial condition isn't met. Table 11-7 for examples in R and Python for a loop running what's in Figure 11-3. In Python a way to get a list of every number from 0 to 9 is `range(10)` (not 1 to 10), so you'll see that in the code. You can get the same thing in R with the code `0:9`.

#### Table 11-7. Example for loop code in Python and R

```python
Python
for num in range(10):
    sq_num = num * num
    print("The square of " + num + " is " + sq_num)

nR
for (num in 0:9) {
    sq_num <- num * num
    print(paste("on the ", paste0(counter,
        "The square of ", num, " is ", sq_num, sep="")))
}
```

Table 11-8 shows the code for accomplishing the same thing using a while loop. Note that in Python, there's a shorthand way of adding 1 to a number: `num += 1`.

#### Table 11-8. Example while loop code in Python and R

Python
num = 0
```python
while num < 10:
    sq_num = num * num
    print("The square of " + num + " is " + sq_num)
    num += 1
```

R
num <- 1
```r
while (num < 10) {
    sq_num <- num * num
    print(paste("on the ", paste0(counter,
"The square of ", num, " is ", sq_num, sep="")))
    num <- num + 1
}
```

You can see another for and while loop in the example Python code in Figure 11-2 on lines 27–29 and 32–35.

### Functions

Everything we've talked about so far applies to procedural programming, but adding functions will take us into functional programming and can vastly improve code if we are performing tasks that are the same or similar over and over. A function is a block of code that does a specific task and may take variables as use and return a value. It can have different names in different languages and contexts, including methods, procedures, and subroutines (these aren't exactly synonymous, but are similar enough for this section). A function is considered callable, which means that you define it once and then run it later by including its name in the code.

A function has two high-level components: a function definition and the function body. These can look different in different languages, but the first line is always the function definition and contains the name of the function and input variables if they're needed. Input variables are called arguments or parameters. The function starts indented on the next line or is contained within curly braces (or something else).

Functions can be small—even just a single line—or hundreds of lines long. In general, shorter is preferred, because it's best practice for a function to do one primary thing (even if it takes many, many steps to accomplish that one thing) rather than several different things. You'll use functions extensively in your code when you call functions that are native to Python or R or are are in some of the packages you install. But you'll also create your own, which is incredibly powerful.

### Python

In Python, functions are called functions except when they are used in a certain context in object-oriented programming, but we won't worry about that. They are defined with the keyword `def`, followed by the name and opening and closing parentheses, with variables inside the parentheses if they are to be included in the function run. The function that appears in the Figure 11-2 code on lines 38–40 is just a silly function that returns the square of a number modified by 1. Line 38 is the definition, with the keyword `def`, the name of the function, and the opening parenthesis, one argument, a closing parenthesis, and the colon, which ends the definition and indicates the function body is coming next. In Python, you start on the next line. The first line calculates the new value, and the final line returns it using the `return` keyword. We can call the function later by using the function name followed by opening and closing parentheses, with any variables to be sent in the same order as the function definition. The parentheses are required whether variables are passed or not. Calling a function looks like line 42 in the sample code in Figure **11-2**, with the name and argument in parentheses. The argument can be a hard-coded value or a variable name.

Python has one additional type of function that's a little unusual. You can define what's considered an anonymous function with the keyword `lambda`. This creates a block of code that behaves like a function, but it's only called once, where it's defined, because it doesn't have a name. One of the most common nonstandard ways of this is when you want to sort something a particular list of two numbers (a row number and a height), like [[4, 60], [8, 69], [3, 62], [1, 67], [2, 65], [9, 72]]. If you just call the Python `sort()` function on the overall list, it would sort of what you might expect—sort all the two-item lists by the first number in each of them. But if we want it by the second number, we could create a simple lambda function in the call to the sort function that tells it to sort by the second number.

### R

Functions in R are similar to those in Python in how they're defined and used, but they look a little different. The same lopsided_square function seen in Python in Figure 11-2 above written in R is shown in Figure 11-5. The name comes first in the definition, followed by the assignment operator, the keyword function, opening and closing parentheses with the argument name inside, and finally an opening curly brace indicating the start of the function definition. The function definition follows on the next two lines, and it's closed with an ending curly brace. R also uses the same keyword as Python, return, to return a value.

```r
lopsided_square <- function(var) {
  var.square <- var * var + 1
  return var.square
}
```
**Figure 11-5.** An example function defined in R

If we include lopsided_square(3) in the code, what we'll get back 10.

### Libraries and Packages

One thing that's important in coding in almost any language is that they're organized by purpose through libraries and packages. In Python the word “library” is sometimes used, but “package” is generally preferred. The base installation of the language includes as many as default, but you can also install more. There are also many third-party packages that although basic mathematical operations are included in Python, there's a special package that includes more advanced math. There are also many packages that are available and used in data science code. To use these kinds of packages in both Python and R, you have to import them first.

### Python

In Python, you can import packages a few different ways. It's customary to do these at the top of your code. Packages contain classes or functions that you want to use, and how you import the packages determines how you refer to those items later. Table 11-9 shows some of the different ways to import a package called Pandas and how you would refer to a function later if you'd imported it that way.
