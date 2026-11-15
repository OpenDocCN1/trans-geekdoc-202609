
a in a relation, there is exactly one b, then the relation is a function.

The domain of the function is the set of distinct a elements comprising each pair, (a, b), and the range of the function is the set of distinct b elements comprising each pair, (a, b).

Consider for example:

S = { (1, 2), (2, 5), (3, 2), (4, 1) }

S is a function because each first element is related to exactly one second element.

The domain of S is: DoS={ 1, 2, 3, 4 }
The range of S is: RaS={ 1, 2, 5 }

Conversely, consider:

R = { (1, 2), (1, 3), (2, 2), (4, 1) }

Here, R is <u>not</u> a function because 1 is related to both 2 and 3.

A function f is also called a mapping from a domain A to a range B. A mapping is symbolized as:

f : A → B

An individual element, a ∈ A is related to exactly one element, b ∈ B. Element relationships may be expressed as:

(a, b) or f(a) = b

![](img/ff796e63b14a88ab72583e78f3994e90_248_0.png)

Figure 10.1 Function versus non-function.

## 10.4 RANGE, IMAGE, & CODOMAIN

The range of a function is sometimes referred to as the image of a function. This is the set of all outputs or the set of all b elements in the ordered pairs (a, b) that make up a function. With a large (and possibly infinite) set of ordered pairs, the range may be difficult to determine. For this reason, a codomain, a set that contains the range as a subset, may be specified instead.

For example, recall from the Numbers chapter that R is the set of real numbers. Consider the function f where

```
f : R → R, with f(x) = x²
```

This function contains all ordered pairs of the form (x, x²), x ∈ R. The domain of f is all real numbers because we can find the square of any real number. The codomain is described by the initial mapping $(\rightarrow \mathbb{R})$ as the set of real numbers. However, the actual range or image is the set of non-negative real numbers, $[0, \infty)$, because $x^2$ is never negative. The range here is a subset of the codomain.

Had the initial mapping been given as

$f : \mathbb{R} \rightarrow [0, \infty)$, with $f(x) = x^2$

then the codomain and the range would be the same.

## 10.5 TYPES OF FUNCTIONS

Injective (one-to-one): A function is injective, or one-to-one, if every range element is mapped to by no more than one domain element.

$f(x) = x + 1$ is one-to-one.

$g(x) = x^2$ is not one-to-one because the function contains both $(3, 9)$ and $(-3, 9)$.

Surjective (onto): A function $f$ from set $A$ to set $B$ is onto if for every element $b \in B$, there is at least one element $a \in A$ such that $f(a) = b$.

A function having a range and codomain that are the same is surjective. Then all the elements of the codomain are mapped to by all the elements of the domain set.

For example:

$f: \mathbb{R} \rightarrow \mathbb{R}$ with $f(x) = x + 1$ is onto because the range is $\mathbb{R}$, or $(-\infty, \infty)$.

$f: \mathbb{R} \rightarrow \mathbb{R}$ with $f(x) = x^2$ is not onto because the range is not $\mathbb{R}$ ($x^2$ is never negative).

For another example, using our definition of the natural numbers (not Peano's definition), $f: \mathbb{N} \rightarrow \mathbb{N}$ with $f(x) = x + 1$ is not surjective (onto). This function maps elements from the set of natural numbers to a subset that contains only numbers greater than 1 (not the entire set of natural numbers).

$f: \mathbb{N} \rightarrow \mathbb{N}, f(x) = 2x$ is also not surjective. This function maps the set of natural numbers to a set of non-negative even numbers. The range excludes odd natural numbers.

*Bijective function*: A function is bijective if it is both injective (one-to-one) and surjective (onto).

For a bijective function $f: A \rightarrow B$, sets $A$ and $B$ must have the same cardinality and have a perfect pairing of elements. That is, each element in the domain maps to exactly one element in the range, and each element in the range is mapped to by exactly one element in the domain. Due to this condition, sometimes a bijective function is said to have a *one-to-one correspondence*.

You may see functions that are:

- Onto but not one-to-one.
- One-to-one but not onto.
- Both one-to-one and onto.

Note that altering the domain and/or the codomain of a function may change the type of function.

![](img/ff796e63b14a88ab72583e78f3994e90_251_0.png)

Figure 10.2 Types of functions.

## 10.6 INVERSE FUNCTIONS

An inverse function “undoes” or reverses the operations performed by a function. A function may or may not have an inverse. If a function f has an inverse, then the inverse of function can be denoted by f⁻¹, or by another symbol, such as g.

A function f : A → B is invertible if its inverse g : B → A exists. That is, for every a ∈ A and b ∈ B:

```
f(a) = b ↔ g(b) = a
```

For example, recall from the Numbers chapter that Z is the set of integers and consider:

```
f : Z → Z, f(a) = a + 5
```

$f$ is invertible and the inverse is $g(a) = a - 5$.

For a function to be invertible, the function must have a one-to-one correspondence. When two elements in the domain map to the same one element in the range, the function is not invertible. For example, the function

$f : \mathbb{R} \rightarrow \mathbb{R}, f(a) = a^2$

is not invertible because it is not one-to-one. Note that both $f(2) = 4$ and $f(-2) = 4$. When two elements in the domain map to one element in the range, the function is not invertible. The existence of an inverse function requires a function with a one-to-one correspondence.

Suppose we have a function relating domain $X$ to codomain $Y, f : X \rightarrow Y$, that is not a one-to-one correspondence. It may be possible to find subsets of $X$ and $Y$ whose elements do form a one-to-one correspondence under function $f$. Then $f$ would be invertible for a smaller domain and range, the aforementioned subsets. The following definitions involve subsets of a given domain $X$ and codomain $Y.$

For function $f : X \rightarrow Y$, if $A \subseteq X$, then the image of $A$ is the set $\{ f(a) \mid a \in A \}$. The image of $A$ is a subset of $Y.$

For function $f : X \rightarrow Y$, if $B \subseteq Y$, then the inverse image, or pre-image, of $B$ is the subset of elements in $X$ that map to all elements in $B$. The pre-image is $\{ x \in X \mid f(x) \in B \}$.

For example, given function $f : \mathbb{Z} \rightarrow \mathbb{Z}, f(x) = x^2$

Suppose $A$ is a subset of the domain, $\mathbb{Z}$, such that \(A = \{ 1, 3, 5 \}\). The image of \(A\) in the codomain is the set \(\{ 1, 9, 25 \}\). The image is a subset of the original codomain.

Suppose $B$ is a subset of the codomain, $\mathbb{Z}$, such that \(B = \{ 4, 16, 49 \}\). The pre-image (or inverse image) of \(B\) is the set \(\{ 2, -2, 4, -4, 7, -7 \}\). The pre-image is a subset of the original domain.

Note that, unlike an inverse function, an inverse image of a function is a subset of the domain as applied to a subset of the codomain.

## 10.7 FUNCTION COMPOSITION

Two functions \(f : A \rightarrow B\) and \(g : B \rightarrow C\) can be composed to give a function directly from \(A\) to \(C\). This function composition may be denoted \(g \circ f\) and is defined as:

```
\((g \circ f)(a) = g(f(a))\)
```

In that manner, a function can map two sets via an intermediary set. Consider the output of function \(f\) becomes the input for function \(g\).

### Composition properties:

- If \(f\) and \(g\) are one-to-one then the function \(g \circ f\) is also one-to-one.

- If \(f\) and \(g\) are onto then the function \(g \circ f\) is also onto.

- Composition is associative, as when composing three functions.

- Composition is not commutative.

For example:

Given \( f(a) = a + 2 \) and \( g(a) = 2a + 1 \), then \( (f \circ g)(a) \) and \( (g \circ f)(a) \) are:

```
\( (f \circ g)(a) = f(g(a)) = f(2a + 1) = 2a + 1 + 2 = 2a + 3 \)
\( (g \circ f)(a) = g(f(a)) = g(a + 2) = 2(a + 2) + 1 = 2a + 5 \)
```

Therefore, \( (f \circ g)(a) \neq (g \circ f)(a) \). We have just used a counter example to prove the composition of functions is not commutative.

A function can also be composed with itself. For example, for \( f(x) = 2x + 3 \),

```
\( (f \circ f)(x) \quad = f(f(x)) \)
\( \phantom{(f \circ f)(x)} \quad = f(2x + 3) \)
\( \phantom{(f \circ f)(x)} \quad = 2(2x + 3) + 3 \)
\( \phantom{(f \circ f)(x)} \quad = 4x + 6 + 3 \)
\( \phantom{(f \circ f)(x)} \quad = 4x + 9 \)
```

## 10.8 FUNCTION ABSTRACTION

As you probably know by now, functions may invoke other functions, be composed of other functions, and may take other functions as arguments.
