# How to generate random numbers

Figure 9-11 shows how to use functions to generate random numbers.
To start, this figure shows three standard functions for working with random
numbers. Then, it shows the Mersenne Twister equivalents of these functions.
Unless you have a compelling reason for doing otherwise, you should use the
Mersenne Twister functions because these functions generate better random
numbers than the standard functions.

The first example shows how to use the mt_rand function to simulate a dice
roll. This code returns an integer from 1 to 6.

The second example shows how to generate a random floating-point value
between 0 and 1 with 5 digits of precision. To start, the first statement initializes
the number to zero. Within the for loop, the first statement generates a random
number between 0 and 9 and adds it to the number. Then, the second statement
shifts the decimal point to the left by dividing the number by 10. So, let’s say
the first three random numbers are 8, 3, and 6. In that case, the number is 0.8
after the first loop, 0.38 after the second loop, and 0.638 after the third loop. This
process is repeated until the value is 5 digits long.

The third example shows how to generate a random password that includes
one symbol, one number, one uppercase letter, and five lowercase letters. To
start, the first statement defines a string of possible symbols to pick from. Then,
it picks a position in this string at random using the strlen and mt_rand functions.
Next, it uses the substr function to add the symbol to the password.

After adding a symbol, this code picks a random number and a random
uppercase letter and adds them to the password. To understand this code, you
need to know that numbers 0 through 9 have the values 48 to 57 in the ASCII
character set. Similarly, the uppercase letters range from 65 to 90 in the ASCII
character set.

After adding the number and uppercase letter, this code adds random
lowercase letters until the password is the specified length. This time, the ASCII
values range from 97 through 122. Then, the str_shuffle function is used to
randomly shuffle the characters in the password.