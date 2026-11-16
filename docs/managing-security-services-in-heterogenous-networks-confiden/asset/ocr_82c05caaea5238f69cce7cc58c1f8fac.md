![](bbox=[0.22, 0.08, 0.78, 0.23])

![](bbox=[0.22, 0.26, 0.78, 0.44])

**Figure 3.12** (a) MANET Network Topology. (b) DFPN-Modeled MANET Network.

that are received from multiple paths. The DST method can identify the bias recommendations, and it can reduce the impact of biased recommendation in trust computations.

The DST function depends on three functions, i.e. mass function, plausibility function (PI), and belief function (Bel). Let an event e happen, and E = {e1, e2, e3} is the set of evidences about the event e The power set P(E) is the {Ø, {e1}, {e2}, {e3}{e1, e2}, {e2, e3}, {e1, e3}, {e1, e2, e3}}.

*Mass function*: The mass function(m) maps all the subsets in P(E) to the range [0,1], m:P(E) → [01] where m(Ø) = 0 and ΣB∈P(E) m(B) = 1.

*Belief function* _(Bel)_: If X is the subset in (E), then bel(X) = ΣC⊆X m(C).

*Plausibility function(pl)*: If X is the subset in P(E), then pl(X) = ΣC∩X≠Ø m(C).

# ### 3.4.3.1 Dempster's Rule for Combinations Let X be the element in