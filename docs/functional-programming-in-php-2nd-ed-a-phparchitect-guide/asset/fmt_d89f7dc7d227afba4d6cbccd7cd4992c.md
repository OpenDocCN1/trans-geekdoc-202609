
Looking at the first `then()` block, you can see it accepts three callback functions. The first is called when the promise is successfully resolved. When a promise fails to be resolved, the second function will be called. Progress updates will trigger the third and final callback function. Returning a value from any of these functions will cause it to be supplied as the input parameter to the respective function in the next `then()` block.

As you can see in the subsequent `then()` block, the callbacks are optional. The second and third `then()` blocks are defined with only the successful callbacks supplied. The workings of these callback functions are so simplistic I am not going to go into any further detail.

To put this into action, we will need a simple event loop, and as before, `React/event-loop` fills this need admirably.

```

```

This creates a new event loop, adds a read stream to it by binding the promise to the file handle, and finally, the loop is run. When executed, the code we have laid out will print a list of updates (in real time) followed by a printout of all the results combined into one long result string.

This is a nice introduction to promises, but it would be remiss of me to skip over the more powerful combinatory functionality `React/Promise` also provides. To allow me to cover the reduce operation, we will need to define another deferred promise before the event loop.

First, though, we must open a new file resource handle and set it to be a non-blocking stream.

```

```

The second deferred is essentially the same as the first, but with references changed to include ‘2nd’.

**Listing 8.6**

```

```

To combine the two promises, we will use a reduce operation by implementing `When::reduce()`, which takes an array of the `deferred` as its first parameter. The second parameter is a callback function that performs the combination logic and returns a new deferred promise wrapping the result.

You can then apply `then()` function blocks to this deferred to gain access to the final result.

**Listing 8.7**

```

```

The first `then()` block simply `elog()`’s the result of the combination and also returns the result for use in the next `then()` block. The final `then()` block prints out an MD5 hash of the result from the reduce operation.

To execute this code, you will need to bind it to the deferred in the event loop again, like:

```

```

When this code is run, you will get a debug log for each read from both the first and second `deferred`. Each deferred will then print its result.

Finally, the `When::reduce()` will print a combination of both the first and second deferred along with an MD5 hash of the result. There are a number of other operations you can perform on lists of deferred promises, and these include: `map()`, `some()`, `any()`, `all()`, and more. Each allow you to make different decisions based upon the results from your deferred promise. Although interesting, it is beyond our scope here to go into further detail, but you can easily use the `reduce()` example as a base to explore the rest of the features of this library. For more information, please see the project’s documentation on GitHub

Promises are a very handy way to organize callback functions and prevent them from getting out of control. There are some handy pieces of code to make it easier to handle asynchronous operations in PHP code. PHP is not known for being event-driven, or for asynchronous operations for that matter. Most standard library calls do not run this way—leaving the parser to process the job until it is finished in series. With the help of some libraries, it is possible to bring this power to PHP in an elegant way.

Promises provide one way of helping to mitigate the callback hell that event-driven programming can bring with it.

## 8.6 Wrap Up the Show

Event-driven programming is not only possible in PHP, but thanks to the reactor pattern and ReactPHP, it is easy. While event-driven programming can lead to callback hell, as we have seen, there are a number of libraries and patterns you can adopt to avoid this. Much like functional programming, a lot of the event-driven programming we have reviewed here is experimental. It is fun to play with, but rarely finds itself in production.

There are at least two far more popular alternatives in Node.js (`ReactPHP` was formerly known as NodePHP) and Python’s Twisted. Both of these have seen far more time in production than PHP’s event libraries. This can be attributed to PHP’s focus on short-running processes for a web server. Sure, it can be run as a daemon with libraries like `PHPDaemon`

All of this combines to make it a really small niche in PHP programming, but as Igor Wiedler (`ReactPHP`’s creator) says: “anything they can have, we can steal!”

* * *

1.  [`ReactPHP`](http://reactphp.org)[↩](#ch011.xhtml#fnref1)

2.  [`React/Promise`](https://github.com/reactphp/promise)[↩](#ch011.xhtml#fnref2)

3.  [`React/Promise`](https://github.com/reactphp/promise)[↩](#ch011.xhtml#fnref3)

4.  [`PHPDaemon`](http://daemon.io)[↩](#ch011.xhtml#fnref4)

5.  [`PHP Simple Daemon`](http://github.com/shaneharter/PHP-Daemon)[↩](#ch011.xhtml#fnref5)

# 9 Hazards of Functional Programming in PHP

> “‘I am not going to exploit functional programming because my coworkers would complain’ is such a gross and cynical thing to believe.”

> 

> –Tony Morris (Functional programmer, @dibblego)

PHP is not a functional language, and therefore, it is more than a lack of syntactic sugar we must overcome. Or more likely in PHP’s case, work around and make do! As a language, PHP has not evolved to support the use of functions as we need, and there has been a deliberate choice to concentrate development resources on improving the language’s object-oriented capabilities. I am not criticizing this; given limited resources, it is important you focus on aspects which will have the greatest impact. Catering to a minority of PHP developers while ignoring the masses would hamper continued uptake of the language and disenfranchise current users.

Having said all this, it is of course, frustrating when a language you are using is not able to cater to the code you wish to implement with it. “Use a more appropriate language,” you might quite rightly cry! I would counter there are a great number of developers who are immensely productive in PHP and may wish to use those skills in a functional style. More practically, there are those of us who must use PHP for various reasons such as it is the only deployment platform, integration with a legacy codebase, or it is an employer’s mandate.

All of this means you will need to think about how you are going to manage your functional projects in PHP. First, how will you lay out your files and create functional “packages” for code sharing?

Unfortunately, PHP does not have a mechanism for autoloading functions at present and from following the discussions surrounding two related PHP RFCs

Which leaves you with a few choices:

1.  Require/include in all the files for all requests. 

2.  Set up the functions as static methods in a class file, which can then be autoloaded similar to `Underscore.php` 

3.  Use my simple functions which cause namespace `use` statements to perform more like an import clause. While it solves a problem, it is—at its core—a complete hack which will invariably slow down your code due to the use of the PHP Tokenizer to double parse the files 

    This is not a show stopper, but it’s annoying and does merit mentioning. If you are going to be implementing some basic functional styles, then it does not matter so much, but if you want to share or reuse a whole library of functions, then you are faced with these three horrible options.
