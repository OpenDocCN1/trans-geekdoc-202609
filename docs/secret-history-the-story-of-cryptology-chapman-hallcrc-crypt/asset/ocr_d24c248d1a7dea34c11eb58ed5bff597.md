In physics, this mysterious quantity is denoted by S. Although the formula is the same, Shannon used H for his entropy. The name entropy stuck, but it is sometimes referred to as “information entropy” or “Shannon entropy” to distinguish it from the concept in physics. Another reason that Shannon’s original names were problematic is that the results we get from his formula don’t always correspond to how we’re used to thinking about information or uncertainty.

If you are trying to evaluate Shannon entropy on a calculator or with a computer program, you’ll quickly bump into the problem of evaluating a base 2 logarithm. Let’s take a quick look at how to get around this difficulty.

$y = \log_2 x \leftrightarrow 2^y = x \text{ (by definition)}$

Now take $\log_b$ of both sides. You may use $b = 10$ (common logarithm) or $b = e$ (natural logarithm) or any other base $b > 0$. Bases 10 and $e$ are the ones that commonly have keys devoted to them (log and ln, respectively) on calculators. I’ll use base $b = e$, with the notation ln.

$\ln(2^y) = \ln(x)$

Making use of one of the properties of logarithms, we may bring the exponent of the argument down in front.

$y \ln(2) = \ln(x)$

Dividing through by $\ln(2)$ now gives

$y = \frac{\ln(x)}{\ln(2)}$

Thus, we have rewritten our base 2 logarithm in terms of logarithms with base $e$. We have, by the way, just derived the change of base formula for logarithms.

Also, because we can rewrite this last equation to express $y = \log_2 x$ as $y = \frac{1}{\ln(2)} \ln(x)$ we see logarithmic functions with different bases only differ by a constant multiplier. Recalling that Shannon’s formulation for entropy was only unique up to a constant multiple, we see that this flexibility is equivalent to being able to use any base for the logarithm. Base 2 is especially convenient when considering digital data; thus, 2 was the base chosen. Regardless of what form the data takes, using the base 2 logarithm results in the units of entropy being “bits per message” or “bits per character,” if we want an average rate of information transmission. The average entropy, $H$, of English may be calculated by using the probability of each of the 26 letters in the following formula: $H = -\sum p_i \log_2(p_i)$