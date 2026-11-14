occurrences of the $j^\text{th}$ token in spam should increase the posterior probability that a message with the $j^\text{th}$ token is spam, we show that including the $j^\text{th}$ token in an attack message generally increases the corresponding score $q_j$ more than not including that token (except in unusual situations which we identify below). Similarly, we show that increasing $q_j$ generally increases the overall spam score $I( \cdot )$ of a message containing the $j^\text{th}$ token. Based on these results, we motivate the attack strategies presented in Section 5.3.1.

# C.2.1 Effect of poisoning on token scores

In this section, we establish how token spam scores change as the result of attack messages in the training set. Intuitively, one might expect that the $j^\text{th}$ score $q_j$ should increase when the $j^\text{th}$ token is added to the attack email. This would be the case, in fact, if the token score in Equation (5.1) were computed according to Bayes' Rule. However, as noted Section 5.1, the score in Equation (5.1) is derived by applying Bayes' Rule with an additional assumption that the prior distribution of spam and ham is equal. As a result, there are circumstances in which the spam score $q_j$ can decrease when the $j^\text{th}$ token is included in the attack email—specifically when the assumption is violated. We show that this occurs when there is an extraordinary imbalance between the number of ham and spam in the training set.

As in Section 5.3, we consider an attacker whose attack messages are composed a single set of attack tokens; i.e., each token is either included in _all_ attack messages or _none_. In this fashion, the attacker creates a set of _k_ attack messages used in the retraining of the filter, after which the counts become

```
\( N^{(s)} \mapsto N^{(s)} + k \\)
\( N^{(h)} \mapsto N^{(h)} \\)
\( n_j^{(s)} \mapsto \begin{cases} n_j^{(s)} + k, & \text{if } a_j = 1 \\ n_j^{(s)}, & \text{otherwise} \end{cases} \\)
\( n_j^{(h)} \mapsto n_j^{(h)}. \)
```

Using these count transformations, we compute the difference in the smoothed SpamBayes score _q<sub>j</sub>_ between training on an attack spam message **a** that contains the _j_<sup>th</sup> token and an attack spam that does not contain it. If the _j_<sup>th</sup> token is included in the attack (i.e., _a<sub>j</sub>_ = 1), then the new score for the _j_<sup>th</sup> token (from Equation 5.1) is

```
\( P_j^{(s, k)} \triangleq \frac{N^{(h)} \left( n_j^{(s)} + k \right)}{N^{(h)} \left( n_j^{(s)} + k \right) + \left( N^{(s)} + k \right) n_j^{(h)}}. \)
```

If the token is not included in the attack (i.e., _a<sub>j</sub>_ = 0), then the new token score is

```
\( P_j^{(s, 0)} \triangleq \frac{N^{(h)} n_j^{(s)}}{N^{(h)} n_j^{(s)} + \left( N^{(s)} + k \right) n_j^{(h)}}. \)
```