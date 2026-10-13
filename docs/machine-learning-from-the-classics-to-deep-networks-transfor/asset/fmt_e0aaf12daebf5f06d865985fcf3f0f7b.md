
### 3. θₖ(n) = ψₖ(n−1) + μₖ ∑[m∈𝒩ₖ] cₘₖ xₘ(n) eₖ,ₘ(n)

For complex-valued data, eₖ,ₘ(n) → eₖ,ₘ*(n).

### 4. End For

* End For

The rationale of this adaptation scheme is the reverse of that illustrated in [Fig. 5.25](#Chp005_177-248_B9780443292385000111.xhtml#f0135), where the phase in [5.25](#Chp005_177-248_B9780443292385000111.xhtml#f0135)B precedes that of [5.25](#Chp005_177-248_B9780443292385000111.xhtml#f0135)A. In the case C = I, there is no input–output data information exchange and the parameter update for the k node becomes:

```
θₖ(n) = ψₖ(n−1) + μₖ xₖ(n) eₖ(n)
```

**Remarks 5.4**

* One of the early reports on the DiLMS can be found in [59]. In [80, 93], versions of the algorithm for diminishing step sizes are presented and its convergence properties are analyzed. Besides the DiLMS, a version for incremental distributed cooperation has been proposed in [58]. For a related review, see [84, 86, 87].
* So far, nothing has been said about the choice of the matrices C (A). There are a number of possibilities. Two popular choices are the following.

#### Averaging rule:

```
cₘₖ = { 1/nₖ, if k = m or if nodes k and m are neighbors,
      { 0,    otherwise
```

and the respective matrix is left stochastic.

#### Metropolis rule:
