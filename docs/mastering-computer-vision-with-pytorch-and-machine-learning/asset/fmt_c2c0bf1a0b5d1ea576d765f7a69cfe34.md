
# Humans have the ability to imagine, create and build new things that have never existed before

The ability to innovate and invent is one of the key characteristics of human intelligence and has led to significant advancements in various fields, such as science, technology, engineering and the arts. We build skyscrapers in cities to live in, make cellphones to keep in our pockets for communication and launch rockets to carry satellites to the edge of our solar system to explore our universe. All these engineering achievements are based on laws of physics and mathematics, such as Newton's law of universal gravitation, Maxwell's electromagnetic law, Einstein's theory of relativity, quantum mechanics, etc. These laws are the foundations of our civilization. They are keys for us to understand and modify our world. However, knowing these physics and mathematics laws is not enough, experts or professionals also have to do work based on their experiences. Those experiences come from life-time practices. Once, when an expert passed away, all of the experiences of that expert were lost. Now it is possible for professionals to train computers with machine learning algorithms, so that human experiences can be inherited and stored in computers forever. The goal of computer vision research is to enable computers to have humanlike perception capabilities. Machine learning is a branch of artificial intelligence (AI) that deals with the development of algorithms and statistical models. Machine learning allows computers to 'learn' from data without being explicitly programmed. In machine learning, models based on algorithms are trained on datasets to find patterns in the datasets to predict new data. There are several types of machine learning, including supervised learning, unsupervised learning, semi-supervised learning, and reinforcement learning, each having a unique set of algorithms and approaches.

## 1.1 Probability, entropy and Kullback–Leibler divergence

Images are composed of pixels, which are minuscule dots on a screen. When numerous pixels are arranged in a specific configuration (pattern), they form an image. The resolution of an image is determined by the number of pixels it contains. Higher image resolutions give us clearer and more detailed visuals. From the pattern or probability of an image's pixels distributed in a space, we can generate new images. To begin our study of computer vision, it is essential to embrace the concept of statistics, particularly probability. Utilizing the Bayesian probability theorem and Shannon's information entropy theory, we can derive loss functions for model training. These models would be so smart that they can not only tell us if there are dogs or cats in an image, but also can generate photorealistic images/videos according to our text prompts.

### 1.1.1 Probability and Shannon entropy

To a fair coin, its 'head' and 'tail' sides have the same probability (50%) to appear when you toss it. In the coin system, we have a discrete random variable `X` within a space of {'head', 'tail'}, and its probability mass function (PMD) is `P(X) = {1/2, 1/2}`. In case when a coin is not fair, its head probability is `p = 0.45`, and we toss the coin ten times (`n = 10`), what is the probability of getting four heads (`x = 4`)? This unfair coin system has a discrete random variable `X` within a space of {0, 1, …, 10} with the binomial dstribution function. Taking those parameters into equation (1.1), you will obtain the answer: 23.8%.

```
P(X = x) = n! / (x!(n - x)!) * p^x * (1 - p)^(n - x)
```

(1.1)

The height variable (`X`) of our bodies is a continuous random number with a Gaussian distribution function which is the most important probability density function (PDF) for machine learning. Although probability density functions of many image datasets are too complex to write down explicitly, we can still try to use Gaussian distribution functions to approximate them.

```
P(X = x) = N(x; μ, σ²) = 1 / √(2πσ²) * e^(-1/2 * ((x - μ)/σ)²)
```

(1.2)

In equation (1.2), `μ` is the **mean** or expected value of `X`, `σ` is the standard deviation of `X` and `σ²` is the **variance** of `X`. For any random variable `X` with a known PDF, its expected value `E[p][X]` and variance `E[p][(X-μ)²]` are:

```
μ = Σ(i=1 to n) x_i * p(x_i)  or  ∫(-∞ to ∞) x * p(x) dx
```

(1.3)

```
σ² = Σ(i=1 to n) (x_i - μ)² * p(x_i)  or  ∫(-∞ to ∞) (x - μ)² * p(x) dx
```

(1.4)

Shannon '**Entropy**' of information is the 'amount of information' contained in a random variable, or the minimum bits to encode information of a system.

```
H(p) = - Σ(i=1 to n) p_i * log₂(p_i)  or  - ∫(-∞ to ∞) p(x) * log₂(p(x)) dx
```

(1.5)

A fair coin system's entropy is `H(p) = - 2 * 1/2 * log₂(1/2) = 1` bit, and a fair dice system's entropy is `H(p) = - 6 * 1/6 * log₂(1/6) = 2.585` bits. For mathematical convenience in machine learning, we usually use natural logarithm, and the entropy unit is 'nit'. The coin's entropy and the dice's entropy are 0.69 nits and 1.79 nits respectively.

### 1.1.2 Kullback–Leibler divergence and cross entropy

In the case where there are two distribution functions `p` and `q` for a same random variable `X`, their log likelihood ratio is a function `f(x) = ln[p(x) / q(x)]`. The expected value of the log likelihood ratio is called **Kullback–Leibler divergence** (`D_KL`):

```
D_KL(p||q) = E_p[ln(p(X) / q(X))] = Σ(i=1 to n) p(x_i) * ln(p(x_i) / q(x_i))
```

(1.6)

`D_KL` is used to measure the difference between two PDFs of a system with the same random variable `X`. If `p` and `q` are the same, we have `D_KL = 0`. Cross entropy is another index to quantify the difference between two PDFs, and it is often used as a loss function in machine learning.

```
H(p,q) = - Σ(i=1 to n) p(x_i) * ln(q(x_i)) = D_KL(p||q) + H(p)
```
