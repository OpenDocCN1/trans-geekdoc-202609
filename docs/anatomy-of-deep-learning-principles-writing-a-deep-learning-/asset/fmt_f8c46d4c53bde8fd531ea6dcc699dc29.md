
$$
\begin{matrix}
\begin{bmatrix}
(W W_{1}x x - b_{1})x_{1} & (W W_{1}x x - b_{1})x_{2} & \cdots & (W W_{1}x x - b_{1})x_{n} \\
(W W_{2}x x - b_{2})x_{1} & (W W_{2}x x - b_{2})x_{2} & \cdots & (W W_{2}x x - b_{2})x_{n} \\
\vdots & \vdots & \ddots & \vdots \\
(W W_{m}x x - b_{m})x_{1} & (W W_{m}x x - b_{m})x_{2} & \cdots & (W W_{m}x x - b_{m})x_{n} \\
\end{bmatrix}
&
= \begin{bmatrix}
W W_{1}x x - b_{1} \\
W W_{2}x x - b_{2} \\
\vdots \\
W W_{m}x x - b_{m} \\
\end{bmatrix}
\times
\begin{bmatrix}
x_{1} & x_{2} & \cdots & x_{n} \\
\end{bmatrix} \\
&
= (Wx x - b){x x}^{T} = z zx x^{T} = f^{\prime}(z z)^{T}{x x}^{T}
\end{matrix}
$$

Generally, if a gradient `f`^′(`z``z`) of `f`(`z``z`) about z, and `z``z` = `W``W``x``x` + `b``b`, then `T``h``e``g``r``a``d``i``e``n``t``o``f``f`(`W``W``x``x` + `b``b`) about `x``x` is `f`^′(`z``z`)`z``z`^′(`x``x`) = `f`^′(`z``z`)`W``W`, the gradient of `W``W` can be written as the same matrix form `f`^′(`z``z`)^(`T`)`x``x`^(`T`) as `W``W`. This rule will be useful in the gradient calculation of neural networks in the future.

### 1.3.8 Integral

For the function `f(x)` in Figure 1-31, how to find the area of the shaded part below it?

![](EPUB/media/file229.png)

Figure 1-31 Calculate the shaded area

The area of the curve can be approximated by accumulating the small rectangular surfaces at points `x[i]` evenly distributed on the interval, that is, $\sum\limits_{i}{f(x_{i}) \ast \Delta x}$, where `Δ``x` is The length of the small interval where the interval where `x` is located is evenly divided.

According to the idea of limit, as long as `Δ``x` is sufficiently small, the error between the above cumulative sum and the real area will be smaller, that is, the real area S is the following limit value:

$S = \lim\limits_{\Delta x \rightarrow 0}\sum\limits_{i}{f(x_{i}) \ast \Delta x}$

This limit value is called the **definite integral** (integral) of the function `f(x)` on this interval. In calculus, a special symbol ∫[a]^(b)`f(x)``d``x` is used to represent this limit value, where the meaning of `d``x` is the differential of the independent variable, which can be regarded as an infinitesimal `Δ``x`. ∫[a]^(b) means to accumulate the product `f(x)``d``x` on the interval `[a,b]`.

Similarly, ∫[a]^(x)`f(x)``d``x` can be used for the area on the interval `[a,x]`. When the value of x is constantly changing, this value is also constantly changing, thus forming a function `F` : `x` → ∫[a]^(x)`f(x)``d``x`. Right now:

`F(x)` = ∫[a]^(x)`f(x)``d``x`

It is also a function that changes as `x` changes.

So what is the derivative of F(x)? According to the definition of derivative, there are:

$F^{\prime}(x) = \lim\limits_{\Delta x \rightarrow 0}\frac{(F(x + \Delta) - F(x))}{\Delta x} = \lim\limits_{\Delta x \rightarrow 0}\frac{(f(x) \ast \Delta x)}{\Delta x} = f(x)$

Of course, the second equation proved is a bit imprecise. Interested readers can check the calculus textbook.

## 1.4 Probability Basics

This section introduces the basics of probability theory such as probability, random variables, expectation, variance, etc.

### 1.4.1 Probability

Probability refers to the likelihood (likelihood) of an event occurring (occurring). Probability is a real number between 0 and 1. If the probability of an event is 0, it means that the event cannot happen, such as "the sun rises from the west", "people can live forever". If the probability of an event is 1, it means that this is an inevitable event, such as "a person will always die". Therefore, events with a probability of 1 and 0 are deterministic events, that is, they must happen or they must not happen.

However, whether many events occur and how likely they are to occur are often uncertain, that is, random events. For example, the event "buying a lottery ticket and winning the jackpot" may or may not happen. Toss a coin at random, it may be "heads" or "tails". Throwing a sieve, the number that appears may be any number in 1, 2, 3, 4, 5, or 6. "Winning the jackpot by buying a lottery ticket" is a small probability event, that is, its probability should be a small real number close to 0.

If a coin is fair, the chances, or probabilities, of heads and tails are the same in a toss of the coin. A random experiment (such as a "coin toss") may have many different outcomes (random events), all of which may have different probabilities, but one of all these outcomes must occur, that is, the sum of the probabilities of all outcomes is equal to 1 . Therefore, assuming that the probability of "tossing a coin", "heads" and "heads" is p, then 2p = 1, that is, p=1/2=0.5. Similarly, if the sieve with 6 numbers is complete and uniform in density, the probability of each number appearing in the "throwing sieve" is 1/6.

The capital letter P is usually used to indicate probability, then the probability of 2 events that may occur in a coin toss is: `P`(`h``e``a``d``s`) = 1/2, `P`(`t``a``i``l``s`) = 1/2.. And the probability of a number i appearing in the throwing sieve is: `P`(`t``h``e` `n``u``m``b``e``r` `i` `a``p``p``e``a``r``s`) = 1/6, `i` ∈ 1, 2, 3, 4, 5, 6

Call "flipping a coin at random" a **random experiment**. The possible results (events) of a random experiment are called **sample points**, and all possible results of a random experiment, that is, the collection of all sample points are called **sample space**. A randomized experiment is usually denoted by a capital E, while a sample space is usually denoted by a capital letter `S`, `Ω`, or `U`.

For the coin toss experiment, its sample space = `{"comes heads", "comes tails"}`. And for throwing a sieve, its sample space = `{"Number 1 appears", "Number 2 appears", "Number 3 appears", "Number 4 appears", "Number 5 appears", "Number 6 appears"}`.

If the random trial is "randomly throwing the sieve 2 times", its sample space = {"number 1 appears for the first time, number 1 appears for the 2nd time", "number 1 appears for the first time, number 2 appears for the 2nd time", \cdots,"The number 6 appears for the first time, the number 6 appears for the second time"}. That is, there are a total of 36 possible results. Assuming that the probability of each number appearing on each sieve is the same, the probability of each result is equal, and the probability is 1/36.

Let the random experiment E be "randomly draw a card from 52 playing cards, and observe the number of words in the card", then its sample space is: {A,2,3,...,J,Q,K}, There are 13 sample points in total. If the random test E is "randomly draw a card from 52 playing cards, what is its suit", then its sample space is: {spades, hearts, clubs, diamonds}, a total of 4 sample points. If the random test E is "randomly draw a card from 52 playing cards, what is the card", at this time, the result of the random test must examine both the number and the suit, and its sample space will be the Cartesian of the above two sample spaces Child product: { (A, spades), (A, hearts), (A, clubs), (A, diamonds), (B, spades), (B, hearts), (B, clubs), (B, diamond),...(K, spade), (K, heart), (K, club), (K, diamond)}, a total of 13×4 = 52 sample points.

The sample points of the sample space are called **elementary events**. A collection of multiple sample points is also an event. For example, in the random experiment "throwing a dice", there are 6 basic events, and these basic events may be combined into other events, such as "numbers appearing no more than 3" this event = { "number 1 appears", "number 2 appears", " The number 3"} appears, which is the union of 3 basic events.

Among all random events, there are 2 special events, that is, the event corresponding to the empty set, which is marked as ⌀; the event corresponding to the full set (including all sample points), is still represented by the symbol `Ω`.
