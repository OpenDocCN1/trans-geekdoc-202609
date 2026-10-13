
This is the first of two chapters dedicated to probabilistic graphical models. This chapter focuses on the basic definitions and concepts, and most of its material is a must for a first reading on the topic. A number of basic graphical models are discussed, such as Bayesian networks (BNs) and Markov random fields (MRFs). Exact inference is presented, and the elegant message passing algorithm for inference on chains and trees is introduced.

## 15.2 The need for graphical models

Let us consider a simplified example of a learning system in the context of a medical application. Such a system comprises a set of `m` diseases that correspond to hidden variables and a set of `n` symptoms (findings). The diseases are treated as random variables, `d[1], d[2], …, d[m]`, and each of them can be absent or present and thus can be encoded by a zero or a one, that is, `d[j] ∈ {0, 1}`, `j = 1, 2, …, m`. The same applies to the symptoms `f[i]`, which can either be absent or present; hence, `f[i] ∈ {0, 1}`, `i = 1, 2, …, n`. The symptoms comprise the observed variables.^([^(110)](#fn110))

The goal of the system is to predict a disease hypothesis, that is, the presence of a number of diseases, given the presence of a set of symptoms which have been observed. During the training, which is based on experts' assessments, the system learns the prior probabilities `P(d[j])` and the conditional probabilities `P[ij] = P(f[i] = 1 | d[j] = 1)`, `i = 1, 2, …, n`, `j = 1, 2, …, m`. The latter comprise a table of `nm` entries. For a realistic system, these numbers can be very large. For example, in [41], `m` is of the order of 500–600 and `n` of the order of 4000. Let `f` be the vector that corresponds to a specific set of observations for the findings, indicating the presence or absence of the respective symptoms. Assuming that symptoms are *conditionally independent*, given any disease hypothesis, `d`, we can write

```
P(f|d) = ∏_{i=1}^{n} P(f_i|d).
```
(15.1)

Ideally, one should be able to obtain the conditional probabilities `P(f[i]|d)` for each disease hypothesis. However, for all possible `2^m` combinations of `d`, this should require a huge amount of training data, which is impossible to collect for any practical system. This is bypassed by adopting the following model:
