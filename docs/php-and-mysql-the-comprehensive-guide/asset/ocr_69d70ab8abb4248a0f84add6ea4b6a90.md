# Chapter 7
Strings

String handling: some people yawn at this topic. Unfortunately, strings are one of a programmer's most important tools. This chapter shows you what you need to know in practice.

A large percentage of all data ends up as a string, whether as the return value of a function or as input from the user. A look at the online documentation of PHP takes your breath away at irst. The list of functions for string manipulation is endless (http://s-prs.co/v602266). But don't worry, here you will find examples and explanations for the most important string manipulations.

> Note
> If you need even more power, you should take a closer look at regular expressions. PHP takes over the functionality of Perl here; you can read more about this in Chapter 10. Some of the string functions also require knowledge of arrays, which you can find out more about in Chapter 8. We have nevertheless put strings first, as arrays are logically based on them and string handling also plays a role in arrays.

# 7.1 Connect

Joining strings is also called concatenation in programming jargon. Strings are therefore concatenated. This is done in PHP with the dot (.). You have already used this many times and/or read about it in Chapter 5. However, the details are still of interest here: What actually happens when a string is concatenated with other data types? This is not a problem at all in PHP because, as the dot is reserved specifically for string operations, PHP always converts the data types into strings beforehand. This means that the code

```
$a = 20;
$b = " euros";
echo $a . $b;
```

correctly displays 20 euros. The following code, on the other hand, shows what?

```
$a = 20;
$b = 40;
echo $a . $b;
```

That's correct: both integers are converted into a string. The result is therefore 2040.