
$$\\mathbf{\\theta}\_{n + 1}|\\mathbf{\\theta}\_{1},\\ldots,\\mathbf{\\theta}\_{n} \\sim \\frac{\\alpha}{\\alpha + n}G\_{0} + \\frac{n}{\\alpha + n}\\left( \\frac{1}{n}\\sum\\limits\_{i = 1}^{K\_{n}}n\_{i}\\delta\_{\\mathbf{\\theta}\_{i}^{\\ast}}(\\mathbf{\\theta}) \\right).$$

![Equation](images/B9780443292385000196/si474.png)

Observe that the above formulation leads directly to Eq. [(13.111)](#Chp013_635-716_B9780443292385000196.xhtml#deq167) (if we apply it for the *n*th instead of the *n* + 1th customer). Indeed, we either select a new color (table in the case of CPR) or the *i*th previously selected one, with probability $\\frac{n\_{i}}{\\alpha + n}$, *i* ≤ *K*[*n*]. Recall from Section [13.11.1](#Chp013_635-716_B9780443292385000196.xhtml#s0105) that according to this rule, the expected number of clusters grows as *α*ln *n*.

An alternative way to arrive at the CRP is as a limiting case (*K* → ∞) of the finite mixture modeling, by adopting a Dirichlet prior with parameter *α*/*K* (see, e.g., \[23,74\]).

**The cluster assignments are exchangeable**: An important aspect of the CRP is that the probability of a specific clustering does not depend on the order customers have arrived and it is unchanged after reshuffling the customers, up to a permutation of the table labels (see Problem [13.22](#Chp013_635-716_B9780443292385000196.xhtml#o0210)). In words, this means that in [Fig. 13.14](#Chp013_635-716_B9780443292385000196.xhtml#f0080), what is the important information is that, for example, customers #1, #4, #5 sit at the *same* table and customer, for example, #3 sits on his/her own. The table numbering is of no importance.

### 13.11.3 The stick breaking construction of a DP

We have already discussed the Pólya urn model and the related CRP. The *stick breaking representation* is an alternative representation of a DP and it was developed in \[77\]. The method builds upon Eq. [(13.113)](#Chp013_635-716_B9780443292385000196.xhtml#deq169) and proposes the steps to generate *P*[*i*], as well as the respective values of **θ**[*i*], *i* = 1, 2, ….
