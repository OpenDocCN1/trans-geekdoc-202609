
Here, Bayes net variables `Alarm`, `Burglary`, and so on become ordinary program variables with values that comprise the current state of the Markov chain. The numerical threshold expressions evaluate to true or false and represent the precomputed Gibbs distributions for each combination of values in the Markov blanket of `Earthquake`. The code is not especially pretty—typically, it will be roughly as large as the Bayes net itself—but it is incredibly efficient. Compared to `GIBBS-ASK`, the compiled code will typically be 2-3 orders of magnitude faster. It can perform tens of millions of sampling steps per second on an ordinary laptop, and its speed is limited largely by the cost of generating random numbers.

## 13.5 Causal Networks
We have discussed several advantages of keeping node ordering in Bayes nets compatible with the direction of causation. In particular, we noted the ease with which conditional probabilities can be assessed if such ordering is maintained, as well as the compactness of the resultant network structure. We noted however that, in principle, any node ordering permits a consistent construction of the network to represent the joint distribution function. This was demonstrated in [Figure 13.3](#Chapter13-02.xhtml#fig13-3), where changing the node ordering produced networks that were bushier and a lot less natural than the original network in [Figure 13.2](#Chapter13-01.xhtml#fig13-2) but enabled us, nevertheless, to represent the same distribution on all variables.

This section describes causal networks, a restricted class of Bayesian networks that forbids all but causally compatible orderings. We will explore how to construct such networks, what is gained by such construction, and how to leverage this gain in decision-making tasks.

*Causal network*

Consider the simplest Bayesian network imaginable, a single arrow, `Fire` → `Smoke`. It tells us that variables `Fire` and `Smoke` may be dependent, so one needs to specify the prior `P(Fire)` and the conditional probability `P(Smoke | Fire)` in order to specify the joint distribution `P(Fire, Smoke)`. However, this distribution can be represented equally well by the reverse arrow `Fire` ← `Smoke`, using the appropriate `P(Smoke)` and `P(Fire | Smoke)` computed from Bayes’ rule. The idea that these two networks are equivalent, hence convey the same information, evokes discomfort and even resistance in most people. How could they convey the same information when we know that `Fire` causes `Smoke` and not the other way around?

In other words, we know from our experience and scientific understanding that clearing the smoke would not stop the fire and extinguishing the fire will stop the smoke. We expect therefore to represent this asymmetry through the directionality of the arrow between them. But if arrow reversal only makes things equivalent, how can we hope to represent this important information formally?

Causal Bayesian networks, sometimes called `Causal Diagrams`, were devised to permit us to represent causal asymmetries and to leverage the asymmetries towards reasoning with causal information. The idea is to decide on arrow directionality by considerations that go beyond probabilistic dependence and invoke a totally different type of judgment. Instead of asking an expert whether `Smoke` and `Fire` are probabilistically dependent, as we do in ordinary Bayesian networks, we now ask which responds to which, `Smoke` to `Fire` or `Fire` to `Smoke`?

This may sound a bit mystical, but it can be made precise through the notion of “assignment,” similar to the assignment operator in programming languages. If nature assigns a value to `Smoke` on the basis of what nature learns about `Fire`, we draw an arrow from `Fire` to `Smoke`. More importantly, if we judge that nature assigns `Fire` a truth value that depends on other variables, not `Smoke`, we refrain from drawing the arrow `Fire` ← `Smoke`. In other words, the value `xi` of each variable `Xi` is determined by an equation `xi = fi(OtherVariables)`, and an arrow `X[j]` → `Xi` is drawn if and only if `Xj` is one of the arguments of `fi`.

The equation `xi = fi(‧)` is called a structural equation, because it describes a stable mechanism in nature which, unlike the probabilities that quantify a Bayesian network, remains invariant to measurements and local changes in the environment.

*Structural equation*

To appreciate this stability to local changes, consider [Figure 13.23(a)](#Chapter13-05.xhtml#fig13-23), which depicts a slightly modified version of the lawn sprinkler story of [Figure 13.15](#Chapter13-03.xhtml#fig13-15). To represent a disabled sprinkler, for example, we simply delete from the network all links incident to the `Sprinkler` node. To represent a lawn covered by a tent, we simply delete the arrow `Rain` → `WetGrass`. Any local reconfiguration of the mechanisms in the environment can thus be translated, with only minor modification, into an isomorphic reconfiguration of the network topology. A much more elaborate transformation would be required had the network been constructed contrary to causal ordering. This local stability is particularly important for representing actions or interventions, our next topic of discussion.

Description

Part (“a”): Arrows from a node labeled `Cloudy` point to nodes labeled `sprinkler` and `Rain`. Arrows from these `Sprinkler` and `Rain` nodes point to a node labeled `Wet Grass`. An arrow from the `Wet Grass` node points to a node labeled `Greener Grass`. Part (b): An arrow from a node labeled `Cloudy` points to a node labeled `Rain`. An arrow each from the `Rain` node and a node labeled `Sprinkler equals True` points to a node labeled `Wet Grass`. An arrow from the `Wet Grass` node points to a node labeled `Greener Grass`.

×![](images/Fig-190.jpg)

Figure 13.23(a) A causal Bayesian network representing cause-effect relations among five variables. (b) The network after performing the action “turn `Sprinkler` on.”

### 13.5.1 Representing actions: The do-operator
Consider again the `Sprinkler` story of [Figure 13.23(a)](#Chapter13-05.xhtml#fig13-23). According to the standard semantics of Bayes nets, the joint distribution of the five variables is given by a product of five conditional distributions:

$\\begin{matrix} \\left. P(c,\\ r,\\ s,w,g)\\ = \\ P(c)\\ P(r \\middle| c)\\ P(s \\middle| c)\\ P(w \\middle| r,s)\\ P(g \\middle| w) \\right. & {(13.14)} \\\\ \\end{matrix}$

where we have abbreviated each variable name by its first letter. As a system of structural equations, the model looks like this:

$\\begin{array}{l} {\\,\\, C\\ = \\ f\_{C}(U\_{C})} \\\\ {\\,\\, R\\ = \\ f\_{R}(C,U\_{R})} \\\\ {\\,\\, S\\ = \\ f\_{S}(C,U\_{S})} \\\\ {W\\ = \\ f\_{W}(R,S,U\_{W})} \\\\ {G\\ = \\ f\_{G}(W,U\_{G})} \\\\ \\end{array}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\begin{array}{l} \\\\ \\\\ {\\text{(13}\\text{.15)}} \\\\ \\\\ \\\\ \\end{array}$

where, without loss of generality, `fC` can be the identity function. The `U`-variables in these equations represent unmodeled variables, also called error terms or disturbances, that perturb the functional relationship between each variable and its parents. For example, `UW` may represent another potential source of wetness, in addition to `Sprinkler` and `Rain`—perhaps `MorningDew` or `FirefightingHelicopter`.

*Unmodeled variable*
