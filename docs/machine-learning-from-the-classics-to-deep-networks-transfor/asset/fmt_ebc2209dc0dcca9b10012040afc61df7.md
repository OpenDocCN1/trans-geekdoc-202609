
where each one of the summations is over *k* possible values, which is equivalent to 𝒪(*k*^(*l*)) summations; for large values of *k* and/or *l*, this is a formidable and sometimes impossible task. Let us consider now one extreme case, where all the involved variables are mutually independent. Then the product rule becomes

```
P(x_1, x_2, ..., x_l) = ∏_{i=1}^l P(x_i)
```

and marginalization turns out to be the trivial identity

```
P(x_1) = (∑_{x_l} P(x_l) ∑_{x_{l-1}} P(x_{l-1}) ... ∑_{x_2} P(x_2)) P(x_1)  (15.9)
```

because each summation is carried out independently, and of course results to one. In other words, exploiting the product rule and the statistical independence can bypass the obstacle of the exponential growth of the computational load. As a matter of fact, the previous full-independence assumption gives birth to the naive Bayes classifier (Chapter [7](#Chp007_293-342_B9780443292385000135.xhtml)).

In this chapter, we are going to study cases that lie between the previous two extremes. The general idea is to be able to express the joint probability distribution (probability density/mass function) in terms of *products* of factors, where each one of them depends on a *subset* of the involved variables. This can be expressed by writing the joint distribution as

![Equation](images/B9780443292385000214/fx001.jpg) (15.10)

where `Pa[i]` denotes the subset of variables associated with the random variable `x[i]`. Take the following example:
