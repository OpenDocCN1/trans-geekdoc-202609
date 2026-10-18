

Additional caveats include not being able to simply import one function from a namespace or alias which function in your `use` statement. You could potentially work around the former by putting each function into its own namespace. You could then use the narrower namespace to pull in just the one function.

There is a miserable trade-off, though, as it will make calling the function a more verbose procedure. If you import the parent namespace, for instance, you would need to specify the child namespace before each function call:

```

```

However, it would allow you to pull in just one function like so:

```

```

Handling immutable data is complicated by the fact PHP does not support it natively, and it is the functional developer’s responsibility to ensure they do not introduce state changes into the code themselves. There have been a few attempts to enforce immutable data in PHP, but none of them are particularly satisfactory and all of them require class-based trickery such as Mikko Koppanen’s `php-immutable` extension.

You are now in the uncharted wilds of PHP and pushing the boundaries of what is possible all the time. Things will be sub-optimal at times or just down right impossible, so you will need to use your judgement as to when these techniques are best employed—if at all—in your projects.

Another minor issue is other PHP developers may struggle to understand your code and curse your name!

* * *

1. [Autofunc RFC](https://wiki.php.net/rfc/autofunc) 和 [Function Loading RFC](https://wiki.php.net/rfc/function_autoloading)[↩](#ch012.xhtml#fnref1)

2. [Underscore.php](http://brianhaveri.github.com/Underscore.php/)[↩](#ch012.xhtml#fnref2)

3. [Namespace Importer](https://github.com/treffynnon/namespace-importer)[↩](#ch012.xhtml#fnref3)

4. [php-immutable extension](https://github.com/mkoppanen/php-immutable)[↩](#ch012.xhtml#fnref4)

# 10 Advances in PHP

> “When there’s a will to fail, obstacles can be found.”

> — John McCarthy (Computer scientist and LISP programming language, 1927–2011)

## 10.1 PHP 5.4

With the introduction of PHP 5.4, a few new features have been added which make programming in a functional style easier.

### Callables

The first of these additions is the `callable` type hint

```

```

### Short Array Syntax

Next up is a handy addition to make defining arrays a little easier on the keyboard, which has been snappily named: short array syntax, and it works like this:

```

```

### Array Dereferencing

Isn’t it annoying when you can’t skip straight to a certain array element returned from a function call? With array dereferencing now in the PHP core, a pet peeve of mine—for as long as I can remember—has now been fixed.

```

```

In a similar vein, you can now also access class members on instantiation—although unfortunately, it is not possible to call functors in this way.

```

```

This bug was fixed as an oversight in PHP 7

There is one further implementation detail supported by closures in PHP 5.4 which, while not strictly applicable to functional programming, deserves a quick mention. You can bind a class to a closure instance to make the class available as `$this` within the closure. This saves you from having to pass in the context via a `use` statement incorporating the `$this`—`$that` dance.

## 10.2 PHP 5.5

With 5.5 there is a new list of features available. Here are my picks for functional programming.

### Generators

Generators are simple constructs which allow you to bring the lazy loading style functionality to building arrays such as those returned by `range()`.

Instead of building the whole array in one hit up front, it will generate the next item just in time for the next iteration, which results in significant memory savings. Here is an example taken from the PHP manual:

```

```

### Empty() and Functional Values

The `empty()` language construct can now take function return values directly:

```

```

### Other Additions

It will now also be possible to dereference arrays and string literals directly:

```

```

As previously mentioned, PHP will also receive array pluck functionality in the form of the `array_column()` function.

## 10.3 PHP 5.6

### Variadics

Nikita proposed an RFC which defines syntax for variadic functions in PHP 5.6

```

```

This becomes the far simpler and more obvious:

```

```

The feature has now shipped with PHP 5.6 and is available to be used in production now.

### List Type Checking

With the addition of variadics to the language it is now possible to check type hint the contents of an array in a very naive way on functions. It works for a one dimensional array of PHP objects to ensure each value in the array is of a certain type and that is all. To make this work, we will use the variadic and splat operator to expand the array into function arguments and then assemble it back into an array again.

```

```

The code above can be applied to a list of objects as the example below shows.

```

```

The call to `set_dates()` using the array of objects with the `...` keyword is functionally equivalent to:

```

```

An incorrect type being passed into the function will trigger a catchable error as demonstrated here:

```

```

### Namespaces

With PHP 5.6 namespacing functions got a little easier with the ability to import a specific function instead of the entire namespace in the example above. Note the `function` keyword included in the use statement to indicate we are importing a function.

```

```

A particularly handy aspect of this development is it’s now possible to alias function identifiers when they are imported into a namespace.

```

```

You can see here the function identifier is aliased at the point it is imported into the namespace with the `as` keyword. This essentially tells PHP to treat and call to `p()` as though it is a call directly to `e()`.

For the sake of completeness it is worth pointing out here the same enhancement brought with it the ability to import namespaced constants as well:

```

```

Namespaces are a great way of keeping functions in distinct libraries to prevent naming collisions and maintain logical separations. Additionally, it is now possible to alias a function identifier as it is imported to further assist in avoiding namespace collisions. Tragically it became evident PHP still does not support autoloading of functions and it looks unlikely to do so in the near future.

## 10.4 PHP 7

Following the vote to skip the version number 6 of PHP, it was decided to call PHPNG (next generation) PHP 7. There was once a PHP 6, but it never saw the light of day and remained unmerged into the master PHP branch. It was cancelled for several reasons and some features were backported into the PHP 5.x branch. Before it got cancelled, though, a number of companies wrote books, articles, and blog posts about it. These are still accessible via your favorite search engine!

The PHP team decided it would be too confusing to call what is now being released PHP 6, All those old resources would come up and they would be inaccurate. So the version number was consigned to history.

A number of new features have been added to the language alongside some bug fixes and speed enhancements. A lot of effort has been put in by many members of the PHP language team. This has resulted in PHP’s greatest release yet. There are a few new features I will highlight here which can be useful while producing functional PHP code. It goes without saying there are plenty of other features and improvements to the language so if I have missed your favorite I apologize. Profusely.

### Scalar Type Hinting

