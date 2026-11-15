
Because of their lack of restrictions, bags may serve as a foundational data structure for more restrictive and abstract structures. Closer to machine level instructions, bags may be constructed using the native facilities for arrays or lists. Used this way, processing a bag is similar to randomly selecting elements from a random access list, which is a topic in the Linear Structures chapter.

Because of the randomness inherent in processing unconnected data, the algorithm efficiency for processing a bag is relatively poor. We never know exactly when, or in what sequence, an element will be drawn from a bag.

A set can be represented by a list such as { a b c d }. Because order does not matter, the same set can be represented as { c b d a }.

Similarly, a bag can be represented by a list, such as { a b c d b } or { b c b d a }. Note the duplicates in these lists.

We can designate elements for a bag b₀ or set s₀ as follows:

```
{ a r g u } s₀ LIST
{ y t b b } b₀ LIST
```

No particular ordering in these list representations of bags and sets is intended here.

The values contained in bags and sets can be numbers, characters, or objects that represent some categorical classification, such as animals, automobiles, financial instruments, etc.

By definition, the data type of the values of a bag are to be the same. However, it may be argued that type consistency in bags does not matter, as bag data is unconnected and there is no comparison of the data inside the bag, such as would be the case if sorting were applicable. Once drawn from the bag, elements can be processed into more restrictive collections by data type as needed.

Therefore, we should be able to construct a bag mixed of numbers and characters, such as:

```
{ a 3 b b } bag₀ LIST
```

Typical bag and set operations include:

- Inserting or adding elements.
- Removing certain elements.
- Verifying that certain elements exist.
- Counting some or all elements.

## 15.2 RANDOM SELECTIONS OF DATA

Due to the unordered nature of bags and sets, adding, removing, and searching bag and set data entails a random function. Randomly searching a bag is less efficient than searching a list if element removal is not part of the selection operation. This is because the random aspect of bag retrieval occasionally results in selecting the same elements, while random selection from a list can still be limited to a range of indices.

In computer programs, the selection of elements at random depends on a function that generates numbers at random. To be practical, such a random number generator must be limited to a range of integers. Numbers outside of a reasonable range may be too large or too small to apply to the problem at hand.

Here is an example number generating function:

```
{ -10 10 RAND } rng WORD
rng ( → 4)
rng ( → -2)
```

Here the word RAND retrieves an integer at random from within the range of -10 to 10, including those lower and upper bounds. Each time that “rng” is invoked, a random integer in the range of -10 to 10 is generated. Given that the RAND operation retrieves any number in the range with the same likelihood as any other number in the range, an ongoing selection of many numbers should eventually display a _uniform random distribution_.

An ideal random number function will generate a uniform distribution, an important consideration for applications in statistical re-sampling and cryptography.

It can be said that nothing is actually random. There is only the complexity of cause and effect that masquerades as random in our clouded view of complexity. Therefore, we can only simulate an approximation of true randomness using clever algorithms. In computers, perfect randomness is impossible since random number functions depend on the interactions of system states that are not exactly random. The system clock is one such factor, as it is commonly used to initiate (seed) a random number. Of course, clocks exhibit a non-random sequential pattern, time, and so other system factors must be mixed for a randomizing algorithm. For these reasons, we call random number functions _pseudo-random number generators_, or _PRNGs_.

Using a pseudo-random number generator, we can fetch an element from a set as follows:

```
{ a b c d e f g h i j } x LIST
{ 1 GSC RAND PICK. CR } prng WORD
x prng → b
x prng → g
```

Or, display a random sequence of those elements:

```
{ x 1 GSC RAND PICK } prng WORD
{ prng. SPACE } GSC LREPEAT ( → e a b j h c d i f g)
```

## 15.3 UNIFORM RANDOM DISTRIBUTION

A discrete uniform random distribution exhibits an equal likelihood of discrete outcomes. In other words, there are a finite number of possible outcomes, each with an equal chance of occurring. Consider the roll of a six sided die. Each of the six numbers has a probability of 1/6. Or consider the selection of a card from a fifty-two card deck. Any card, from the 1st card to the 52nd card, has a probability of 1/52.

The function for such a probability is given as:

f(x) = 1/n

where x represents the individual outcomes 1, 2, 3, ..., n.

For the six-sided die example, if we were to graph f(x) for successive rolls, the graph would appear as a horizontal line like the one in Figure 15.1, with a height of 1/6. Such a horizontal line indicates a uniform distribution of the outcomes.

![](img/ff796e63b14a88ab72583e78f3994e90_344_0.png)

Figure 15.1 A uniform probability distribution of 6 random samples.

## 15.4 PSEUDO-RANDOM NUMBER FUNCTIONS

Generating a uniform distribution is not trivial, as there are no true random number sequences, as was mentioned above.

The computer system approach noted above entails getting a seed number, such as the system clock's current time in nano seconds. However, time alone is not random, but a linear periodic sequence, which makes it predictable. Therefore, apart from time, other data factors are needed to create the illusion of randomness. Such data might include operating system conditions, including memory, CPU usage, etc. One approach might be to divide the product of these factors by the number of desired samples, computing the modulo (taking the remainder).

Using the modulo, or mod, we can limit the range of possible outcomes from a random number generator. For example, suppose we have a batch of random numbers that range from 0 to 50, but we want to limit the numbers to a range of 0 to 9. We can achieve this desired outcome by computing f(x)mod10 for each random number f(x). For example, 50mod10 is 0, 17mod10 is 7, 10mod10 is 0, and 24mod10 is 4.

Pseudo-randomness can be enhanced by mixing in additional factors, such as the number of current processes in the operating system, as piped to the following md5sum command on a Unix command-line:

```
ps-aux|md5sum
```

On a Unix system, that command creates a 128-bit number in hexadecimal format, the length of which is 32 hexadecimal characters.

Another Unix oriented approach is to use the /dev/urandom device file, which consists of numbers created by Unix using random computer noise, doing so by waiting a sufficient amount of time between each generation for a prior state to experience entropy. These random numbers can be displayed using the following Unix command:

```
od -d /dev/urandom
```

Incidentally, the urandom file has a large quantity of random numbers pregenerated at boot time, freeing real-time applications from having to deal with time-consuming random number generation. For example, a pseudo-random algorithm to generate a single random number can be defined as follows in epop:

```
1 begin !
100 end !
{ ( ( od -vAn -N4 -tu4 < /dev/urandom)) SYSTEM } bignum WORD
{ end @ begin @ - } range WORD
{ bignum range % } prng WORD
```

This code uses a modulo operation, the % operator, and is of a class of pseudo-random number generators known as *linear congruential generators*, or *LNGs*.

LNGs have a state space S of positive whole numbers up to a limit n, such as:

{ 0 1 2 ... n } S

An LNG function can be given by:

f(i) = g(i, a, b, ...) mod n

where the symbols i, a, and b are integer constants selected from S.

## 15.5 EVALUATING PSEUDO RANDOM NUMBERS

Generally, a Pseudo Random Number Generator PRNG will depend on a finite set of states D, a seed number n, and output that is a subset of R, such that:

n = 1, 2, 3, ...
f(D, n) → R

By running a PRNG many times, the numbers generated can be analyzed for uniformity by sorting and plotting them for visualization. The more uniform the distribution, the more reliable the PRNG. For example, the following code generates a list of 2000 random probabilities.
