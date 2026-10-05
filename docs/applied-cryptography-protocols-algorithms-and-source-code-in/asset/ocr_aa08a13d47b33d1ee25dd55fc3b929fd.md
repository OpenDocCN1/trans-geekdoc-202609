# CHAPTER 11 Mathematical Background

Choose a random number, $p$, to test. Calculate $b$, where $b$ is the number of times 2 divides $p-1$. $2^b$ is the largest power of 2 that divides $p-1$. Then calculate $m$, such that $p = 1+2^bm$.

+   (1) Choose a random number $a$, such that $a$ is less than $p$.
(2) Set $j=0$ and set $z=a^j \pmod p$.
(3) If $z=0$, or $z=p-1$, then $p$ passes the test and may be prime.
(4) If $j>0$ and $z=p-1$, then $p$ is not prime.
(5) Set $j=j+1$. If $j<b$ and $z \neq p-1$, set $z=z^2 \pmod p$ and go back to step (4). If $z=p-1$, then $p$ passes the test and may be prime.
(6) If $j=b$ and $z \neq p-1$, then $p$ is not prime.

The odds of a composite passing decreases faster with this than previous ones. Three-quarters of the possible values of $a$ are guaranteed to be witnesses. This means that a composite number will slip through $t$ tests no more than $1/4$ of the time. For most random numbers, this is very pessimistic, like $99.9$ percent of the possible values $a$ are witnesses [96].

There are even better estimations [417]. For $n$-bit candidates (where $n$ is more than one), the odds of error in one test are less than 1 in $4n2^{n/251}$. And for a 256-bit $n$, the odds of error in six tests are less than 1 in $2^n$. More theory is in [418].

# Practical Considerations

In real-world implementations, prime generation goes quickly.

+   (1) Generate a random $n$-bit number, $p$.
(2) Set the high-order and low-order bit to 1 (This ensures the prime is of the required length and the low-order bit ensures it is odd).
(3) Check to make sure $p$ is not divisible by small primes:3, 5, 7, 11, and so on. Many implementations test $p$ for divisibility by all primes less than 256. The most efficient is to test for divisibility by all primes less than 2000 [949]. You can do this using a wheel [863].
(4) Perform the Rabin-Miller test for random $a$. If $p$ passes, generate another random $a$ and go through the test again. Choose a small value of $a$ to make the calculations go quicker. Do five tests [651]. (One might seem enough, but not so.) If $p$ fails on one of the tests, generate another $p$ and try again.

Another option is not to generate a random $p$ each time, but to incrementally search numbers starting at a random point until you find a prime.
Step [3] is optional, but it is a good idea. Testing a random odd $p$ to make sure it is not divisible by 3, 5, and 7 eliminates 54 percent of the odd numbers before you get