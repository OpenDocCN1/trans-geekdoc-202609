![](bbox=[0.07, 0.1, 0.92, 0.38])

FIGURE 18.4 On the left side: a CP-net that models the collective moral preferences of a society. On the right side: the induced partial order over the action space. Note that we have kept the outcomes in the same positions as Figure 18.2 and rearranged the arrows which show the ordering according to worsening flips.

Indeed, he also prefers solutions that are maximally damaging and could be even more serious, for instance, by swerving the car and also injuring his passengers.

Hence it is important to have tools which are able to understand how different or how similar two given preference orderings are. This is needed whether the preferences represent moral principles, exogenous priorities, or individual preferences. Having such metrics allows us to define value alignment procedures that enable artificial agents to both follow established guidelines and correct or prevent harm from non-compliant behaviors. When preferences and priorities are modeled as CP-nets, a straightforward metric that can be used to measure the distance between two preferences is the [16] τ (KT) distance, which counts how many swaps are required in order to change one linear order into another one. [18] proposed such a metric for CP-nets, along with tractable approximations. In the next section, we discuss these metrics and define a value alignment procedure for supporting decision making under exogenous priorities.

# NOTIONS OF DISTANCE BETWEEN CP-NETS

CP-nets do not induce total orders, but rather a partial order over the solution space, meaning that some outcomes can be incomparable as seen in the examples in the last section. The following definition is an extension of the [16] τ (KT) distance with a penalty parameter p defined for partial rankings by [14]. A more complete treatment and proofs of correctness for this definition are discussed by [18].

# Definition 1 (Kendall τ Distance (KTD)): Given two CP-nets A and B inducing partial orders P and Q over the same set of outcomes U:

KTD(A,B) = KT(P,Q) = Σ_{∀i,j∈U,i≠j} K_{i,j}^p(P,Q) (18.1)