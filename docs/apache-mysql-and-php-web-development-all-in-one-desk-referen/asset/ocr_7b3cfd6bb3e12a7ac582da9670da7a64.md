By itself, a subroutine does nothing. The subroutine runs only when you have code in your program that calls the subroutine. To call the subroutine, you type the name of the subroutine (such as Bank) followed by a set of parentheses. (In the next section, “Passing data to a subroutine,” I show you how you can put variables inside those parentheses.)

Many other languages (including C++ and PHP) use the term function instead of subroutine. In fact, Perl is a little inconsistent in its terminology because some of the official documentation uses the term function. Therefore, I use the terms function and subroutine interchangeably. (Note, however, that some languages, most notably Pascal, distinguish between subroutines and functions. A function is a special kind of subroutine that returns data to the caller. I talk about returning data in the section, “Returning data to the caller,” later in this chapter.)

# Passing data to a subroutine

A subroutine is useful, but a subroutine that has data is even more useful. Here’s an example: Suppose you have a subroutine called Bank, and each time you call it, you want to deposit a different amount of money. For example, one day you want to deposit $13,527,985, and the next day you can only deposit a measly $995,219. Instead of writing two separate subroutines, you can write one that can handle different amounts.

Here’s the code to do this:

```
sub Bank {
   $amount = $_[0];
   print "Wow! Depositing $amount! I'm rich!\n";
}
Bank(13527985);
Bank(995219);
```

First, look at the two lines in the main part of the program that call the subroutine. Each line consists of the word Bank followed by a number inside parentheses, which is the amount of the deposit. The first line passes 13527985 to the Bank subroutine. The second line passes 995219 to the Bank subroutine.

Now look at the code for the subroutine. Miraculously, this code figures out what number was passed to it. That’s what the first line inside the subroutine does: $amount = $_[0];