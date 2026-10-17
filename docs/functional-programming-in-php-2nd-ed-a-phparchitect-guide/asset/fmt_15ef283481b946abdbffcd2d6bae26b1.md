
The visual difference between a closure and any other PHP function is the `use` keyword which defines the variable or variables that will be pulled into and encapsulated by that closure. This is the only real difference and otherwise a closure looks just like any other lambda function.

```

```

In the previous example you will note the `use` keyword came into play and pulled in the `$name` variable. The function is then able to operate on the value of `$name` as if it were any other parameter passed to the function.

The same example with multiple variables added to the functions context via `use` would look like the following example.

```

```

Two new variables (`$title` and `$surname`) were added to the program and pulled into the functions context with the `use` keyword. This allowed all three variables to be used within the body of the closure, but of course you do not have to use all the variables pulled in. In the next example the `$name` variable has been added to the closures context, but it does not actually get consumed within the functions body.

```

```

Much like any other function a closure can also accept arguments and these are passed to it from within the first set of parentheses in the closures definition.

```

```

Closures are useful for values you need access to on every call of the function and that will not change after the closure’s definition. Commonly, it is implemented when you want to pass other closures or lambda functions into the closure you are defining.

**Listing 3.2**

```

```

Here you can see a lambda function being pulled into a closure which is then called upon each element in `$array` using `array_map()` to create an MD5 hash for each value in the array.

### Higher Order Functions

The term, higher order function, refers to functions which either accept another function as an argument or those returning a function as a value. Of course the same name applies to functions that do both as well. When a function accepts another function as a parameter like the venerable `spl_autoload_register()` it becomes a higher order function. You can create your own functions which accept other functions as parameters too.

This is most often used in PHP when you want to call a function against items in a list or to filter results as a predicate.

While this may be the norm you can pass the function for any purpose. Going back to the case of `spl_autoload_register()`, it is used as a sort of lazy loading and a simple function to define a reusable instruction set. By lazy loading I mean the code in the callback will not be executed unless it is required explicitly to answer an autoloading request. Additionally, if an earlier registered function matches, then this code will never run—a good thing!

Back to the original point and looking at an example of a function which accepts another function as an argument. We will start with a simple apply function which will accept a value and a function. Given these ingredients our apply function will execute the supplied function against the value parameter.

```

```

This could also be used against the `$add_one` lambda function we defined in the previous section.

```

```

This is just the beginning of what is possible with this aspect of higher order functions and functional programming in general.

You have probably already encountered frameworks such as Silex, Bullet, and Slim that use lambda functions to handle the route/request process. These are anonymous functions in the wild being passed into higher order functions within the framework.

The other important property exhibited by higher order functions is the ability to return a function as a value and this allows for the creation of complex expressions (even more so with the help of closures). Keeping to simple functions and lambda functions it is possible to create a function which returns another function as a value.

Imagine you have an application supplied with hashes as either CRC32

**Listing 3.3**

```

```

In the `get_hashing_function()` example (Listing 3.5), you can see there are two ways of detecting a CRC32 hash, this is because for historical reasons PHP’s `crc32()` function returns an integer instead of a hexadecimal string like `md5()`. The `dechex()` function must be used to convert the integer to a hexadecimal representation. Otherwise this function is fairly straight forward; given a hash string it determines the length and then based on that, returns the appropriate hash function.

So given the hash `ef0f94622b0381c62cfb8fc5c6435f4c` it will calculate the length to be 32 characters and therefore make the assumption that `md5()` was used to generate the hash. Based on this knowledge it will give you a hash function back in return.

```

```

While this functions serves to illustrate the concept at hand it is highly contrived and certainly not production ready. To simplify the example for higher order functions which return another function it is also possible to do the following.

```

```

It is also possible to return an array of values from a function so you could return multiple functions in this way.

Higher order functions are at their most useful when using closures instead of just named and lambda functions, and they allow you to build powerful expressions. First, to keep it simple, the following example illustrates a function which returns a closure. This is denoted by the `use` keyword after the closures arguments and in this case it draws the value of `$operator` into the functions scope/context.

```

```

When passed a mathematical operator such as (`+`, `-`, `/`, `*` or `%`) `create_maths_func()` will return a closure which accepts two arguments. The closure will apply the supplied operator to the arguments (`$a` and `$b`) using PHP’s `eval()` function.

```

```

Closures can also be used to create more complex expressions such as repeating operations and introducing limit clauses. This is much more easily explained with a code example. To repeat a function call for number of times you can use a simple recursive function like the following code sample.

```

```

I won’t go into too much detail of the recursive nature of this function, as this is addressed in depth later in the book. For now, you can take my word it will call the supplied closure three times and return an array of the results. To add in some conditional logic, the `when()` function will take a condition and two callbacks. Based on the result of the condition it will either apply the first callback or the second.

```

```

Essentially `when()` wraps an if/else statement up into a functional expression which can be applied in a sequence of function calls. In Listing 3.4 both `repeat()` and `when()` are combined to form a simple countdown.

**Listing 3.4**

```

```

This gives us a list of three items, but the same functions could easily be re-used elsewhere or applied to larger problems.

Instead of using control statements, functional programming makes use of higher order functions which form expressions. Higher order functions are those which take other functions as arguments and/or return a function.

See the following code sample for a very contrived example which exhibits some aspects of this paradigm. We are passing in a function as an argument and returning a function from `get_calculation()`. The function it returns will be executed against each item in the array by `array_map()`.

Listing 3.5 shows how functions can easily be reused and passed around to create richer algorithms. This is merely an extension of the functionality we saw earlier whilst exploring the `spl_autoload_register()` examples in the lambda functions section. It also serves as a timely reminder that if you’re not careful, it is very easy to make a near unreadable mess with higher order functions in PHP!

**Listing 3.5**

```
