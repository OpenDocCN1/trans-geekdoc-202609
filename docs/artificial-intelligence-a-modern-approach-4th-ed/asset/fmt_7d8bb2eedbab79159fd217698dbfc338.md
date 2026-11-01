
The third, which we pursue next, is to focus on learnable subsets of the entire hypothesis space of Boolean functions. This approach relies on the assumption that the restricted hypothesis space contains a hypothesis `h` that is close enough to the true function `f`; the benefits are that the restricted hypothesis space allows for effective generalization and is typically easier to search. We now examine one such restricted hypothesis space in more detail.

## 19.5.1 PAC learning example: Learning decision lists

We now show how to apply PAC learning to a new hypothesis space: decision lists. A decision list consists of a series of tests, each of which is a conjunction of literals. If a test succeeds when applied to an example description, the decision list specifies the value to be returned. If the test fails, processing continues with the next test in the list. Decision lists resemble decision trees, but their overall structure is simpler: they branch only in one direction. In contrast, the individual tests are more complex. [Figure 19.10](#Chapter19-05.xhtml#fig19-10) shows a decision list that represents the following hypothesis:

Description

A node labeled Patrons (x, Some) has two branches labeled Yes and No. Branch Yes is connected to a node labeled Yes. Branch No is connected to a node labeled Patrons (x, Full) and Friday slash Saturday (x). Node Patrons (x, Full) and Friday slash Saturday (x) has two branches labeled Yes and No. Branch Yes is connected to a node labeled Yes. Branch No is connected to a node labeled No.

×![](images/Fig-272.jpg)

Figure 19.10 A decision list for the restaurant problem.

<p class="sidebar">Decision lists</p>

`WillWait` ⇔ (`Patrons` = `Some`) ∨ (`Patrons` = `Full` ∧ `Fri/Sat`).

If we allow tests of arbitrary size, then decision lists can represent any Boolean function (Exercise 19.DLEX). On the other hand, if we restrict the size of each test to at most `k` literals, then it is possible for the learning algorithm to generalize successfully from a small number of examples. We use the notation `k-DL` for a decision list with up to `k` conjunctions. The example in [Figure 19.10](#Chapter19-05.xhtml#fig19-10) is in `2-DL`. It is easy to show (Exercise 19.DLEX) that `k-DL` includes as a subset `k-DT`, the set of all decision trees of depth at most `k`. We will use the notation `k-DL(n)` to denote a `k-DL` using `n` Boolean attributes.

<p class="sidebar"><span class="italic">K</span>-DT</p>

The first task is to show that `k-DL` is learnable—that is, that any function in `k-DL` can be approximated accurately after training on a reasonable number of examples. To do this, we need to calculate the number of possible hypotheses. Let the set of conjunctions of at most `k` literals using `n` attributes be `Conj(n, k)`. Because a decision list is constructed from tests, and because each test can be attached to either a Yes or a No outcome or can be absent from the decision list, there are at most `3|Conj(n, k)|` distinct sets of component tests. Each of these sets of tests can be in any order, so

|*k*−DL(*n*)|≤3^(*c*) *c*!   where *c* = |*C**o**n**j*(*n*,*k*)| .

The number of conjunctions of at most `k` literals from `n` attributes is given by

$\\text{|}Conj\\text{(}n,k\\text{)|~=}{\\sum\\limits\_{i = 0}^{k}{\\begin{pmatrix} {2n} \\\\ i \\\\ \\end{pmatrix} = O\\text{(}n^{k}\\text{)}\\text{.}}}$

Hence, after some work, we obtain

|*k*\-DL(*n*)| = 2^(*O*(*n*^(*k*) log[2](*n*^(*k*)))).

We can plug this into [Equation (19.1)](#Chapter19-05.xhtml#eq19-1) to show that the number of examples needed for PAC-learning a `k-DL(n)` function is polynomial in `n`:

$N \\geq \\frac{1}{\\epsilon}\\,\\left( \\text{ln}\\frac{1}{\\delta} + O(n^{k}\\text{log}\_{\\text{2}}\\text{(}n^{k})) \\right).$

Therefore, any algorithm that returns a consistent decision list will PAC-learn a `k-DL` function in a reasonable number of examples, for small `k`.

The next task is to find an efficient algorithm that returns a consistent decision list. We will use a greedy algorithm called `DECISION-LIST-LEARNING` that repeatedly finds a test that agrees exactly with some subset of the training set. Once it finds such a test, it adds it to the decision list under construction and removes the corresponding examples. It then constructs the remainder of the decision list, using just the remaining examples. This is repeated until there are no examples left. The algorithm is shown in [Figure 19.11](#Chapter19-05.xhtml#fig19-11).

×![](images/Fig-273.jpg)

Figure 19.11 An algorithm for learning decision lists.

This algorithm does not specify the method for selecting the next test to add to the decision list. Although the formal results given earlier do not depend on the selection method, it would seem reasonable to prefer small tests that match large sets of uniformly classified examples, so that the overall decision list will be as compact as possible. The simplest strategy is to find the smallest test `t` that matches any uniformly classified subset, regardless of the size of the subset. Even this approach works quite well, as [Figure 19.12](#Chapter19-05.xhtml#fig19-12) suggests. For this problem, the decision tree learns a bit faster than the decision list, but has more variation. Both methods are over 90% accurate after 100 trials.

Description

The horizontal axis is labeled training set size and ranges from 0 to 100 in increments of 20. The vertical axis is labeled proportion correct on test set and ranges from 0.4 to 1 in increments of 0.1. A curve labeled decision tree starts at approximately (1, 0.5), rises steeply to (20, 0.9), and then rises gradually to (100, 0.95). The decision tree curve is vertically zig-zag throughout. A curve labeled decision list starts at approximately (1, 0.5), rises steeply to (30, 0.85), and then rises gradually to (100, 0.9). The decision list curve crosses the decision tree curve at approximately (5, 0.55) and stays below the decision tree curve for the most part.

×![](images/Fig-274.jpg)

Figure 19.12 Learning curve for `DECISION-LIST-LEARNING` algorithm on the restaurant data. The curve for `LEARN-DECISION-TREE` is shown for comparison; decision trees do slightly better on this particular problem.

## 19.6 Linear Regression and Classification

Now it is time to move on from decision trees and lists to a different hypothesis space, one that has been used for hundreds of years: the class of linear functions of continuous-valued inputs. We’ll start with the simplest case: regression with a univariate linear function, otherwise known as “fitting a straight line.” [Section 19.6.3](#Chapter19-06.xhtml#sec19-6-3) covers the multivariable case. [Sections 19.6.4](#Chapter19-06.xhtml#sec19-6-4) and [19.6.5](#Chapter19-06.xhtml#sec19-6-5) show how to turn linear functions into classifiers by applying hard and soft thresholds.

<p class="sidebar">Linear function</p>

### 19.6.1 Univariate linear regression

A univariate linear function (a straight line) with input `x` and output `y` has the form `y = w1 x + w0`, where `w0` and `w1` are real-valued coefficients to be learned. We use the letter `w` because we think of the coefficients as weights; the value of `y` is changed by changing the relative weight of one term or another. We’ll define `w` to be the vector `⟨w0, w1⟩`, and define the linear function with those weights as

<p class="sidebar">Weight</p>

`h[w](x) = w[1] x + w[0]`.
