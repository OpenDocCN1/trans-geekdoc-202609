# # Chapter 6

# Functions and Language Constructs

*Functions are the easiest way to bundle frequently used functionality in programming.*

*Functions* are, simply put, collections of statements. You either write these collections yourself, or they are supplied by PHP or one of the infinite number of PHP extensions.

*A language construct* is quite similar to a function specified by PHP. However, you can omit the round brackets typical for functions in a language construct.

# ## 6.1 Functions

Functions are easy to use. Two steps are necessary:

+   - You must define the function (also known as *declaring* it). This is not necessary with a PHP function; it is already defined there.
+   - You must then call the function, as it is only executed when it is called.

To define a function, use the function keyword:

```
function Name() {
  statements;
}
```

The *function* keyword is followed by the function name. The round brackets are characteristic of functions. This is also where the parameters are placed (Section 6.1.1). The curly brackets contain the statements. You are already familiar with this type of statement block from case distinctions and loops. To call a function, use its name and the round brackets:

```
Name();
```

In the following simple example, the function outputs a record when it is called (see Figure 6.1).

```
<?php
function output() {
  echo "This is a function.";
}
```