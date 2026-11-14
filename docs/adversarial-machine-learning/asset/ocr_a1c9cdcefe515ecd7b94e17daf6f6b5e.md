# ### 4.6.2 Attacks with Mixed Data

Here we analyze the expected net effect of applying the optimal greedy attack of Lemma 4.21 over T iterations and thus provide an analysis for the mixed data scenario described in Equation (4.24). To do so, we require an additional assumption about the benign data's distribution—namely we assume (i) that all benign data is drawn independently from P_x, (ii) that the benign data has a stationary mean, E_{x~P_x} [x] = c^(0), and (iii) that benign data is never rejected. These are strong assumptions about the benign data, but, in assuming that the benign data has a stationary mean and is always accepted, these are conservative assumptions on the attacker and yield the following theorem.³

> THEOREM 4.22 (Paraphrased from Kloft & Laskov 2012) Given a fixed mixture probability v, applying the greedy optimal attack strategy (given by Lemma 4.21) at each iteration yields an expected displacement alignment of

```
E [ρ (D_T)] = \frac{v}{1 - v} \cdot \left( 1 - \left( 1 - \frac{(1 - v)}{N} \right)^T \right) \le \frac{v}{1 - v}
```

after T iterations.

Proof. Under the optimal attack strategy of Lemma 4.21 the centroid becomes

```
c^(t) = c^(t-1) + \frac{1}{N} \left( B^{(t)} R \cdot \frac{x^4 - c^{(0)}}{\|x^4 - c^{(0)}\|} + \left( 1 - B^{(t)} \right) (x^{(t)} - c^{(t-1)}) \right)
```

```
= c^(t-1) + \frac{B^{(t)} R}{N} \frac{x^4 - c^{(0)}}{\|x^4 - c^{(0)}\|} + \frac{1}{N} \left( 1 - B^{(t)} \right) (x^{(t)} - c^{(0)})
```

```
- \frac{1}{N} \left( 1 - B^{(t)} \right) \left( c^(t-1) - c^{(0)} \right) ,
```

where the summation has been conveniently reorganized for later. Now, using the definition of D_t = \frac{c^{(t)} - c^{(0)}}{R} from Equation (4.4), we substitute this form of c^(t) and use the linearity of ρ ( · ) to obtain

```
D_t = \left( 1 - \frac{1 - B^{(t)}}{N} \right) D_{t-1} + \frac{x^4 - c^{(0)}}{\|x^4 - c^{(0)}\|} \frac{B^{(t)}}{N} + \frac{\left( 1 - B^{(t)} \right) \left( x^{(t)} - c^{(0)} \right)^\top}{N} \frac{x^4 - c^{(0)}}{R},
```

```
ρ (D_t) = \left( 1 - \frac{1 - B^{(t)}}{N} \right) ρ (D_{t-1}) + \frac{B^{(t)}}{N} + \frac{\left( 1 - B^{(t)} \right) \left( x^{(t)} - c^{(0)} \right)^\top}{N} \frac{x^4 - c^{(0)}}{R \|x^4 - c^{(0)}\|} .
```

Next we use the linearity of E [ · ] and the mutual independence of the random variables B^(t) and x^(t) to compute the expectation of ρ (D_t). Importantly, D_{t-1} is also mutually independent of B^(t) and x^(t) from the t^th iteration. Finally, using the fact that E [B^(t)] = v and E [x^(t)] = c^(0), we arrive at the following recursive formula

```
E [ρ (D_t)] = \left( 1 - \frac{(1 - v)}{N} \right) E [ρ (D_{t-1})] + \frac{1}{N} v. Unwrapping this recursion and using the
```

³ In a more realistic model, benign data would not always be accepted, particularly once the attack had significantly shifted the detector. This would motivate the attacker to concentrate its attack mass in the early iterations. Amenable models for this scenario are further explored in Kloft & Laskov (2012).