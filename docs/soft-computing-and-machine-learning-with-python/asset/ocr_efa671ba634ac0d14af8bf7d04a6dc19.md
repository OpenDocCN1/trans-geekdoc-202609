# A Python 2.7 Programming Tutorial 165

Mathematically, $\cos(\pi/2)$ should be zero. However, like pretty all other modern programming languages, transcendental functions like this use approximations. $6.12 \times 10^{-17}$ is, after all, pretty close to zero.

Two math functions that you might find useful in certain situations:

+   * floor(x) returns the largest whole number that is less than or equal to x.
* ceil(x) returns the smallest whole number that is greater than or equal to x.

```
>>> floor(4.9)
4.0
>>> floor(4.1)
4.0
>>> floor(-4.1)
-5.0
>>> floor(-4.9)
-5.0
>>> ceil(4.9)
5.0
>>> ceil(4.1)
5.0
>>> ceil(-4.1)
-4.0
>>> ceil(-4.9)
-4.0
```

Note that the floor function always moves toward $-\infty$ (minus infinity), and ceil always moves toward $+\infty$.

# CHARACTER STRING BASICS

Python has extensive features for handling strings of characters. There are two types:

+   * A str value is a string of zero or more 8-bit characters. The common characters you see on North American keyboards all use 8-bit characters. The official name for this character set is ASCII, for American Standard Code for Information Interchange.