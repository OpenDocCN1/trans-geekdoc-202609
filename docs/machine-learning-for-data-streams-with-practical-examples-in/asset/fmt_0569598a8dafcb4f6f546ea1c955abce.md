
# Notation and Preliminaries

We first fix some notation used throughout the rest of the book. We use `E[X]` and `Var(X)` to denote the expected value and the variance, respectively, of random variable `X`. A log without a subscript denotes a logarithm in base 2, and `ln` denotes a natural logarithm. A function `f` is `O(g)` if there is a constant `c > 0` such that for every `x` we have `f(x) ≤ c · g(x)`. The cardinality of a set `A` is denoted `|A|`. In pseudocode, `←` denotes variable assignment, and `⊳` starts a comment line.

In streaming, an *item* is simply an element of a universe of items `I` without any relevant inner structure. Set `I` is potentially very large, which means that it is unfeasible to use memory proportional to `|I|`. We will sometimes assume that storing an element of `I` takes one unit of memory; this is necessary when `I` is infinite—for instance, the set of real numbers. In other cases we will go into more detail and count the number of bits required to store an item, which is at least `log |I|`.

We define a *sketching* algorithm by giving three operations: an `Init(...)` operation that initializes the data structure, possibly with some parameters such as the desired approximation or the amount of memory to be used; an `Update(item)` operation that will be applied to every item on the stream; and a `Query(...)` operation that returns the current value of a function of interest on the stream read so far (and may or may not have parameters). In general, a sketch may implement several types of queries.

Many functions that can be computed easily on offline data are impossible to compute *exactly* on streams in sublinear memory. For example, computing the number of distinct items seen requires linear memory in the length of the stream, in the worst case and large enough item universes. On the other hand, for many functions there are algorithms that provide *approximate* solutions and obtain large gains in memory and time with only a small loss in accuracy, which is often acceptable in applications. We next introduce some formalism for discussing approximate computation.

Let `f` and `g` be two real-valued functions. We think of `g` as an approximation of `f`. For an *accuracy* value `ε`, we say that `g` is

*   an *absolute* or *additive* `ε`-approximation of `f` if `|f(x) − g(x)| ≤ ε` for every input `x`;
*   a *relative* or *multiplicative* `ε`-approximation of `f` if `|f(x) − g(x)| ≤ ε |f(x)|` for every input `x`.

Many approximate algorithms on streams are also *randomized*, meaning that they have access to a source of random bits or numbers to make their choices. Their output on a fixed input is not uniquely defined, as it may be different on different runs. It should therefore be treated as a *random variable g* that hopefully is close to the desired `f` in most places. The definition of (absolute or relative) `(ε, δ)`-approximation is like that of `ε`-approximation as above, but requiring only that the approximation above holds with probability at least `1 − δ` over the runs of the algorithm, rather than in every single run. For example, to say that the output `g` of an algorithm is an absolute `(0.1, 0.01)`-approximation of a desired function `f`, we require that, for every `x`, `g(x)` is within `±0.1` of `f(x)` at least 99% of the times we run the algorithm. The value `1 − δ` is usually called *confidence*.

This framework is similar to the PAC learning model [146] used to formalize prediction learning problems, where PAC stands for "probably approximately correct." It should be noted that, usually, the approximation guarantees only hold when the updates and queries made do not depend on the answers returned by previous queries. That is, we cannot apply these guarantees for *adaptive queries*, which are common in exploratory data analysis.

In statistics, the traditional way of approximately describing a random variable `X` is by giving its expected value `E[X]` and its variance `Var(X)`. Suppose we have a randomized algorithm `g` that approximates a desired function `f`, in the sense that `E[g(x)] = f(x)` with some variance `Var(g) = σ²`. In that case, we can design, on the basis of `g`, another algorithm `h` that approximates `f` in the seemingly stricter sense of `(ε, δ)`-approximation. The new algorithm `h` takes any `ε` and `δ` as parameters, in addition to `x`, and uses `O((σ²/ε²) ln(1/δ))` times the memory and running time of `f`. As we might expect, it uses more resources as more accuracy and more confidence are required. The details of the conversion are given in section 4.9.2, but we describe next the main ingredient, as it is ubiquitous in stream algorithmics and stream mining.

# 4.2 Concentration Inequalities

While processing a stream, algorithms often need to make decisions based on the information they have seen, such as deciding the value to output or choosing among some finite number of options. If a decision has to be made around accumulated statistics, then a useful tool would be a method to establish the likelihood of an undesired event occurring. In other words, one could ask the question: If I make a decision at this point in time about the model I am constructing, what is the chance that I will be wrong in the long run? Such decision-making leans heavily on concentration inequalities.

Inequalities stating that random variables are concentrated around the mean with high probability are known as *concentration inequalities* or *large-deviation bounds*. They can also be regarded as providing *confidence bounds* for the variables. An example is the law of large numbers of classical probability theory, or the three-sigma rule, which states that for a normal distribution nearly all (99.73%) of the probability mass lies within three standard deviations of the mean.

The most basic concentration inequality is *Markov's inequality*, which states that for any nonnegative random variable `X`, and `t > 0`,

```
![](images/pg38-1.png)
```

*Chebyshev's inequality* is an application of Markov's inequality and states that for any nonnegative random variable `X`, and `t > 0`,

```
![](images/pg38-2.png)
```

Often, we want to estimate `E[X]` by averaging several copies of `X`. Averages, a special kind of random variable, converge to their expectation much faster than stated by Chebyshev's inequality, as the number of copies grows. For any `n`, define

```
![](images/pg38-in-1.png)
```

where `X[1], …, X[n]` are independent variables taking values in `[0, 1]` with `E[X] = p`. Then:

1.  **Chernoff's bound:** For all `ε ∈ (0, 1)`,

    ```
    ![](images/pg38-3.png)
    ```

2.  **Hoeffding's bound:** For all `ε > 0`,

    ```
    ![](images/pg38-4.png)
    ```

3.  **The normal approximation:** If in a draw of `X[1], …, X[n]` we obtain

    ```
    ![](images/pg38-in-2.png)
    ```

    then

    ```
    ![](images/pg38-in-3.png)
    ```

    happens with probability about

    ```
    ![](images/pg38-in-4.png)
    ```

    where `Φ(z)` is the probability that a normally distributed variable with average 0 and standard deviation 1 is less than `z`. The function `Φ(z)` equals

    ```
    ![](images/pg38-in-5.png)
    ```

    where `erf` is the error function available in most programming languages.

We can apply the bounds in the reverse direction and derive a formula relating the deviation from the mean and its probability. For example, if `ε = ![](images/pg38-in-6.png)`, Hoeffding's bound gives `Pr[ |X − p| > ε ] ≤ δ`. This is useful for obtaining additive `(ε, δ)`-approximations. Chernoff's bound gives multiplicative approximations instead, but has the disadvantage that the bound mentions `p = E[X]`, the unknown value that we want to estimate; also, it applies only to `ε < 1`.
