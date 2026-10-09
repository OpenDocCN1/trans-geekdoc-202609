still satisfy the partial order relation in the learning subspace. For example, given half of a lion's image, most people still recognise this mapping, although the mapping is missing nearly half of the dimensions, because the human brain has the ability to think of the overall image from the fitting of local information. If the whole image is severely distorted, although this mapping does not seem to have lost any one-dimensional information, almost no one can identify it, because the meaningful local information has disappeared [9].

The local finite partial set in LML is defined as follows:

**Definition 2.13.** Let the sample data set *P* in the LML be a partially ordered set. If for any *x, y* \in *P* and *x < y*, the interval [*x, y*] is a finite set, then *P* is called the local finite partially ordered set. If *P* is a finite set, *P* is called a finite partially ordered set.

**Definition 2.14.** Let the sample data set *P* in LML be a local finite partially ordered set, *R* be a commutative ring with the unit element, and *\mu*(*x, y*) be a binary function defined on *P* and valued in *R*, assuming that *\mu*(*x, y*) satisfies the following three conditions:

+   (1) For any *x* \in *P*, there is always *\mu*(*x, x*) = 1;
(2) If *x* \nleq *y*, then *\mu*(*x, y*) = 0;
(3) If *x < y*, then $\sum_{x \le z \le y} \mu(x, z)$ = 0.

Let *\mu*(*x, y*) be a M\"obius function defined on *P* and valued in *R*.

The M\"obius function can be used to determine the parameters of the relationship between the states in the learning process. If the two states are equivalent, the function value is 1; otherwise, it is 0.

**Lemma 2.1.** Let the sample data set *P* in LML be a local finite partially ordered set. *x, y* \in *P*, if *x < y*, then *d*(*x, y*) < $\infty$.

**Proposition 2.1.** The local finite partially ordered set of the sample data set *P* in LML must have a M\"obius function and is unique.

*Proof.* Let the sample data set *P* in LML be a locally finite partially ordered set. First, we prove that there must be a M\"obius function on *P*. We define

```
$$
\begin{aligned}  
&\mu(x, x)=1 \text{ for any } x \in P \\ 
&\mu(x, y)=0 \text{ if } x, y \in P \text{ and } x \nleq y
\end{aligned}
$$
```

Let *x, y* \in *P* and *x* \le *y* for the induction of *d*(*x, y*) to define *\mu*(*x, y*). When *d*(*x, y*) = 0, *x = y*, and *\mu*(*x, y*) = 1 as defined above, set *d*(*x, y*) > 0. For *z* \in *P* and *x* \le *z* \le *y*, there is obviously *d*(*x, z*) < *d*(*x, y*); hence, *d*(*x, z*) is defined. Thus,

```
$$\mu(x, y)=-\sum_{x \le z \le y} \mu(x, z) \ .$$
```

According to the definition of *\mu*(*x, y*), it is suitable for (1), (2), and (3). Thus *\mu*(*x, y*) is the M\"obius function on *P*.