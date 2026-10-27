number $n$ can be represented in this manner. Consider $n=ab$, where $a$ and $b$ are both greater than one and neither need be prime. Letting $x=(a+b)/2$ and $y=(a-b)/2$, we see

$$x^2-y^2=\left(\frac{a+b}{2}\right)^2-\left(\frac{a-b}{2}\right)^2=\left(\frac{a^2+2ab+b^2}{4}\right)-\left(\frac{a^2-2ab+b^2}{4}\right)=\frac{4ab}{4}=ab$$

Thus, such a representation always exists.

An example will make it clear how this observation may be applied. Consider $n=391$. We start with

$$x=\lceil\sqrt{n}\rceil=20$$

The $\lceil\ \rceil$ notation is referred to as the *ceiling function*. It indicates that the quantity within should be rounded up to the closest integer. In Section 14.7, a related function called the *floor function* will also be needed. It is notated with $\lfloor\ \rfloor$ and means that the quantity within should be rounded down to the closest integer. Most programming languages have commands built in to perform these operations.

Using $x=20$, we continue like so:

$$x^2-n=400-391=9=\text{a perfect square, namely }3^2$$

Thus, $y=3$ and we have $n=20^2-3^2=(20-3)(20+3)=(17)(23)$. The factorization is revealed! If the first value for $x$ yielded a value for $x^2-n$ that wasn’t a perfect square, we would increment $x$ by one and try again until a solution is found. In general, quicker factorization algorithms now exist, but Fermat’s method has an advantage when the prime factors are close together. Thus, when picking primes $p$ and $q$ for RSA, we need to avoid values such that $p-q<2n^{1/4}$. There’s nothing magical about this particular bound. It just roughly indicates for which primes Fermat’s method will be practical.

# 15.5 Euler’s Factorization Method

![](bbox=[0.363, 0.602, 0.637, 0.849])

**Figure 15.6**  Leonhard Euler (1707–1783). ([http://en.wikipedia.org/wiki/File:Leonhard_Euler.jpg](http://en.wikipedia.org/wiki/File:Leonhard_Euler.jpg)).

I tell math majors that Leonhard Euler ([Figure 15.6](#)) should be mentioned at least once in every mathematics course, and if he isn’t, they should go to the registrar’s office and ask for a tuition refund,