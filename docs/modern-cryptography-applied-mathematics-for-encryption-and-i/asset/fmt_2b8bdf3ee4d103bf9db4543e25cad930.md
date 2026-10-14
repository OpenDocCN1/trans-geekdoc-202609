
If two numbers are congruent modulo n, then the difference between a and b will be some multiple of n. To make this clearer, let’s return to the clock analogy, in which 14 and 2 are congruent modulo 12. It turns out that the difference between 14 and 2 is 12, a multiple of n (1 × 12). We also know that 14, or 1400 hours on the 24-hour clock, is 2 o’clock. So when we say that 14 and 2 are congruent modulo 12, we are stating that, at least in reference to modulo 12, 14 and 2 are the same. Here’s another example: 17 and 5 are congruent modulo 12. The difference between them is 12. Again using the 24-hour clock to test our conclusions, we find that 1700 hours is the same as 5 P.M.

You should be aware of some basic properties of congruence:

![image](Images/image00484.jpeg) `a ≡ b (mod n)` if n|(a – b)

![image](Images/image00484.jpeg) `a ≡ b (mod n)` implies `b ≡ a (mod n)`

![image](Images/image00484.jpeg) `a ≡ b (mod n)` and `b ≡ c (mod n)` imply `a ≡ c (mod n)`

###### Congruence Classes

A *congruence class*, or residue class, is a group of numbers that are all congruent for some given modulus.

Consider an example where the modulus is 5. What numbers are congruent modulo 5? Let’s begin with 7: `7 mod 5 ≡ 2`. Next, we ask what other numbers’ mod 5 ≡ 2, and we arrive at an infinite series of numbers: 12, 17, 22, 27, 32 …. Notice that this works the other way as well (with integers smaller than the modulus, including negatives). We know that 7 mod 5 ≡ 2, but also 2 mod 5 ≡ 2 (that is, the nearest multiple of 5 would be 0; 0 × 5, thus 2 mod 5 ≡ 2). Make sure you fully understand why 2 mod 5 ≡ 2, then we can proceed to examine negative numbers. Our next multiple of 5 after 0, going backward, is –5 (5 × –1). So –3 mod 5 ≡ 2. We can now expand the elements of our congruence class to include –3, 0, 2, 7, 12, 17, 22, 27, 32, and so on.

You should also note that for any modulus n, there are n congruence classes. If you reflect on this for just a moment you should see that the modulus itself creates a boundary on the arithmetic done with that modulus, so it is impossible to have more congruence classes than the integer value of the modulus.

Modulus operations are very important to several asymmetric cryptography algorithms that we will be examining in [Chapter 10](#part0020.xhtml#ch10). So make certain you are comfortable with these concepts before proceeding.

**Tip**

For more on modulus arithmetic, consult the Rutgers University tutorial “Modular Arithmetic” at [`www.math.rutgers.edu/~erowland/modulararithmetic.html`](http://www.math.rutgers.edu/~erowland/modulararithmetic.html), or TheMathsters YouTube video “Modular Arithmetic 1” at [`www.youtube.com/watch?v=SR3oLCYoh-I`](http://www.youtube.com/watch?v=SR3oLCYoh-I).

#### Famous Number Theorists and Their Contributions

When learning any new topic, you may often find it helpful to review a bit of its history. In some cases, this is best accomplished by examining some of the most important figures in that history. Number theory is replete with prominent names. In this section I have restricted myself to a brief biography of mathematicians whose contributions to number theory are most relevant to cryptography.

##### Fibonacci

Leonardo Bonacci (1170–1250), known as Fibonacci, was an Italian mathematician who made significant contributions to mathematics. He is most famous for the Fibonacci numbers, which represent an interesting sequence of numbers:

1, 1, 2, 3, 5, 8, 13, 21, …

The sequence is derived from adding the two previous numbers. To put it in a more mathematical format,

`Fn = Fn–1 + Fn–2`

So in our example, 2 is 1 + 1, 3 is 2 + 1, 5 is 3 + 2, 8 is 5 + 3, and so on.

The sequence continues infinitely. Fibonacci numbers were actually known earlier in India, but they were unknown in Europe until Fibonacci rediscovered them. He published this concept in his book *Liber Abaci*. Although this number series has many interesting applications, for our purposes, the most important is its use in pseudo-random number generators that we will be exploring in [Chapter 12](#part0023.xhtml#ch12).

Fibonacci was the son of a wealthy merchant and was able to travel extensively. He spent time in the Mediterranean area studying under various Arab mathematicians. In his book *Liber Abaci*, he also introduced Arabic numerals, which are still widely used today.

##### Fermat

Pierre de Fermat (1601–1665) was trained as a lawyer and was an amateur mathematician, although he made significant contributions to mathematics. He worked with analytical geometry and probability but is best known for several theorems in number theory, which we will look at briefly.

Fermat’s little theorem states that if p is a prime number, then for any integer a, the number a^p – a is an integer multiple of p. What does this mean? Let’s look at an example: Suppose a = 2 and p = 5. Then 2⁵ = 32 and 32 – 2 is 30, which is indeed a multiple of p (5). This actually turns into a primality test. If you think p is a prime number, you can test it. If it is prime, then a^(p–a) should be an integer multiple of p. If it is not, then p is not prime.

Let’s test this on some numbers we know are not prime. Use p = 9: 2⁸ – 2 = 256 – 2 = 250, and 250 is not prime. This is an example of how various aspects of number theory, that might not at first appear to have practical applications, can indeed be applied to practical problems.

**Note**

This theorem is often stated in a format using modulus arithmetic. However, we have not yet discussed modulus arithmetic so I am avoiding that notation at this time.

Fermat first articulated this theorem in 1640, which he worded as follows:

p divides a^(p–1) – 1 whenever p is prime and a is co-prime to p

Fermat is perhaps best known for Fermat’s Last Theorem, sometimes called Fermat’s conjecture (which, incidentally, is no longer a conjecture). This theorem states that no three positive integers (x, y, z) can satisfy the equation x^n + y^n = c^n for any n that is greater than 2. Put another way, if n > 2, then there is no integer to the n power that is the sum of two other integers to the n power. Fermat first proposed this in 1637, actually in handwritten notes in the margin of his copy of *Arithmetica*, an ancient Greek text written in about 250 C.E. by Diophantus of Alexandria. Fermat claimed to have a proof that would not fit in the margin, but it has never been found. However, his theorem was subsequently proven by Stanford University professor Andrew Wiles in 1994.

##### Euler

Swiss mathematician and physicist Leonhard Euler (1707–1783) is an important figure in the history of mathematics and number theory. Euler (pronounced *oy*‑ler) is considered one of the best mathematicians of all time, and he is certainly the pinnacle of 18th-century mathematics.

Euler’s father was a pastor of a church. As a child, Euler and his family were friends with the Bernoulli family, including Johann Bernoulli, a prominent mathematician of the time. Euler’s contributions to mathematics are very broad. He worked in algebra, number theory, physics, and geometry. The number e you probably encountered in elementary calculus courses (approximately 2.7182), which is the base for the natural logarithm, is named after Euler, as is the Euler-Mascheroni constant.

Euler was responsible for the development of infinitesimal calculus and provided proof for Fermat’s little theorem, as well as inventing the totient function discussed earlier in this chapter. He also made significant contributions to graph theory. Graph theory is discussed later in this chapter in reference to discrete mathematics.

##### Goldbach
