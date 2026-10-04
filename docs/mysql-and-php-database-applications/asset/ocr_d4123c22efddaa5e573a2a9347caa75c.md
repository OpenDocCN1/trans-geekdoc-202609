# Part II: Working with PHP

number and not use it with any other functions, use the mt functions described below—they're faster and more random

# RANDOM NUMBER GENERATOR FUNCTIONS USED IN THIS BOOK

Now we will examine important random number generator functions not used in the applications in this book.

# MT_SRAND() This function seeds your random number generator.

```
void mt_srand(int seed)
```

Using the following line and you can be sure your numbers are plenty random:

```
mt_rand((double) microtime()) * 1000000;
```

Seed the random number generator only per script.

# MT_RAND() This function returns a random number. You can specify a minimum value and/or a maximum value.

```
int mt_rand([int min [, int max])
```

To get a random number between 1 and 100, do the following:

```
mt_srand((double)microtime()) * 1000000;
$number = mt_rand(1,100);
echo $number;
```

# cURL functions

These are explained in detail in Chapter 14. cURL is a library that allows for communication between servers using a variety of protocols. For the sake of the applications in this book, cURL was most useful for its ability to communicate with HTTPS. This is a secure protocol used in the shopping cart to do credit transactions.

# Session functions

These are explained in detail in Chapter 14. Sessions are means of maintaining state between pages. Remember that HTTP, the language of the Web, does not allow servers to remember anything between requests for pages from a specific user. Sessions allow the server to keep track of activities by a single user.

# HTTP header functions

There are two vital HTTP header functions, both of which you will need to get to know.