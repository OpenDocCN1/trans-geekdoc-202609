+   1. The algorithm will spend approximately $2^{1000}$ iterations in the for-loop!

+   2. The algorithm computes $x^e$ as an *integer* first, and then reduces that integer mod $N$. Observe that $x^2$ is roughly 2000 bits long, $x^3$ is roughly 3000 bits long, etc. So it would take about $2^{1000} \cdot 1000$ bits just to write down the integer $x^e$.

As you can see, there is neither enough time nor storage capacity in the universe to use this algorithm. So how can we actually compute values like $x^e \% N$ on huge numbers?

+   1. Suppose you were given an integer $x$ and were asked to compute $x^{17}$. You can compute it as:

$x^{17} = \underbrace{x \cdot x \cdot x \cdot \cdots \cdot x}_{16 \text{ multiplications}}$ .

But a more clever way is to observe that:

$x^{17} = x^{16} \cdot x = (((x^2)^2)^2)^2 \cdot x$ .

This expression can be evaluated with only 5 multiplications (squaring is just multiplying a number by itself).

More generally, you can compute an expression like $x^e$ by following the recurrence below. The method is called **exponentiation by repeated squaring**, for reasons that are hopefully clear:

$x^e = \begin{cases} 1 & \text{if } e = 0 \\ (x^{\frac{e}{2}})^2 & \text{if } e \text{ even} \\ (x^{\frac{e-1}{2}})^2 \cdot x & \text{if } e \text{ odd} \end{cases}$

```
BETTEREXP(x, e):
if e = 0: return 1
if e even:
    return BETTEREXP(x, e/2)^2
if e odd:
    return BETTEREXP(x, (e-1)/2)^2 * x
```

BETTEREXP divides the $e$ argument by two (more or less) each time it recurses, until reaching the base case. Hence, the number of recursive calls is $O(\log e)$. In each recursive call there are only a constant number of multiplications (including squarings). So overall this algorithm requires only $O(\log e)$ multiplications (compared to $e - 1$ multiplications by just multiplying $m$ by itself $e$ times). In the case where $e \sim 2^{1000}$, this means only a few thousand multiplications.

+   2. We care about only $x^e \% N$, not the intermediate integer value $x^e$. One of the most fundamental features of modular arithmetic is that you can **reduce any intermediate values mod $N$** if you care about the final result only mod $N$.

Revisiting our previous example:

$x^{17} \% N = x^{16} \cdot x \% N = (((x^2 \% N)^2 \% N)^2 \% N)^2 \cdot x \% N$ .

More generally, we can reduce all intermediate value mod $N$: