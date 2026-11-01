
This is, of course, merely a trivial example of a very general phenomenon. Once something is understood, it can be generalized and reused in other circumstances. It becomes an “obvious” step and can then be used as a building block in solving problems still more complex. Alfred North Whitehead (1911), co-author with Bertrand Russell of Principia Mathematica, wrote “Civilization advances by extending the number of important operations that we can do without thinking about them,” perhaps himself applying EBL to his understanding of events such as Zog’s discovery. If you have understood the basic idea of the differentiation example, then your brain is already busily trying to extract the general principles of explanation-based learning from it. Notice that you hadn’t already invented EBL before you saw the example. Like the cavemen watching Zog, you (and we) needed an example before we could generate the basic principles. This is because explaining why something is a good idea is much easier than coming up with the idea in the first place.

## 20.3.1 Extracting general rules from examples

The basic idea behind EBL is first to construct an explanation of the observation using prior knowledge, and then to establish a definition of the class of cases for which the same explanation structure can be used. This definition provides the basis for a rule covering all of the cases in the class. The “explanation” can be a logical proof, but more generally it can be any reasoning or problem-solving process whose steps are well defined. The key is to be able to identify the necessary conditions for those same steps to apply to another case.

We will use for our reasoning system the simple backward-chaining theorem prover described in [Chapter 9](#Chapter09-00.xhtml). The proof tree for `Derivative(X2, X) = 2X` is too large to use as an example, so we will use a simpler problem to illustrate the generalization method. Suppose our problem is to simplify `1 × (0 + X)`. The knowledge base includes the following rules:

$\\begin{array}{l} \\begin{array}{l} \\left. Rewrite(u,v)\\, \\land \\, Simplify(v,w)\\Rightarrow Simplify(u,w). \\right. \\\\ \\left. Primitive(u)\\ \\Rightarrow\\ Simplify(u,u)\\ . \\right. \\\\ \\left. ArithmeticUnknown(u)\\ \\Rightarrow\\ Primitive(u). \\right. \\\\ \\left. Number(u)\\ \\Rightarrow\\ Primitive(u)\\ . \\right. \\\\ {Rewrite(1 \\times u,u).} \\\\ {Rewrite(0 + u,u).} \\\\ \\end{array} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\vdots} \\\\ \\end{array}$

The proof that the answer is `X` is shown in the top half of [Figure 20.7](#Chapter20-03.xhtml#fig20-7). The EBL method actually constructs two proof trees simultaneously. The second proof tree uses a variabilized goal in which the constants from the original goal are replaced by variables. As the original proof proceeds, the variabilized proof proceeds in step, using exactly the same rule applications. This could cause some of the variables to become instantiated. For example, in order to use the rule `Rewrite(1 × u, u)`, the variable `x` in the subgoal `Rewrite(x × (y + z), v)` must be bound to `1`. Similarly, `y` must be bound to `0` in the subgoal `Rewrite(y + z, v')` in order to use the rule `Rewrite(0 + u, u)`. Once we have the generalized proof tree, we take the leaves (with the necessary bindings) and form a general rule for the goal predicate:

Description

George joins Mum has two child nodes labeled Elizabeth joins Philip and Margaret. Elizabeth joins Philip has four child nodes labeled Diana joins Charles, Anne joins Mark, Andrew joins Sarah, and Edward joins Sophie. Diana joins Charles has two child nodes labeled William and Harry. Anne joins Mark has two child nodes labeled Peter and Zara. Andrew joins Sarah has two child nodes labeled Beatrice and Eugenie. Edward joins Sophie has two child nodes labeled Louise and James. Spence joins Kydd has a child node labeled Diana.

×![](images/Fig-297.jpg)

Figure 20.7 Proof trees for the simplification problem. The first tree shows the proof for the original problem instance, from which we can derive

`ArithmeticUnknown(z) ⇒ Simplify(1×(0+z), z)`.

The second tree shows the proof for a problem instance with all constants replaced by variables, from which we can derive a variety of other rules.

$\\begin{array}{l} {Rewrite(1 \\times (0 + z);0 + z) \\land Rewrite(0 + z,z) \\land ArithmeticUnknown(z)} \\\\ \\left. \\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\Rightarrow\\,\\,\\, Simplify\\text{(1} \\times \\text{(0} + z\\text{),~}z\\text{)}\\text{.} \\right. \\\\ \\end{array}$

Notice that the first two conditions on the left-hand side are true regardless of the value of `z`. We can therefore drop them from the rule, yielding

`ArithmeticUnknown(z) ⇒ Simplify(1×(0+z), z)`.

In general, conditions can be dropped from the final rule if they impose no constraints on the variables on the right-hand side of the rule, because the resulting rule will still be true and will be more efficient. Notice that we cannot drop the condition `ArithmeticUnknown(z)`, because not all possible values of `z` are arithmetic unknowns. Values other than arithmetic unknowns might require different forms of simplification: for example, if `z` were `2 × 3`, then the correct simplification of `1 × (0 + (2 × 3))` would be `6` and not `2 × 3`.

To recap, the basic EBL process works as follows:

1. Given an example, construct a proof that the goal predicate applies to the example using the available background knowledge.
2. In parallel, construct a generalized proof tree for the variabilized goal using the same inference steps as in the original proof.
3. Construct a new rule whose left-hand side consists of the leaves of the proof tree and whose right-hand side is the variabilized goal (after applying the necessary bindings from the generalized proof).
4. Drop any conditions from the left-hand side that are true regardless of the values of the variables in the goal.

## 20.3.2 Improving efficiency

The generalized proof tree in [Figure 20.7](#Chapter20-03.xhtml#fig20-7) actually yields more than one generalized rule. For example, if we terminate, or prune, the growth of the right-hand branch in the proof tree when it reaches the `Primitive` step, we get the rule

`Primitive(z) ⇒ Simplify(1×(0+z), z)`.

This rule is as valid as, but more general than, the rule using `ArithmeticUnknown`, because it covers cases where `z` is a number. We can extract a still more general rule by pruning after the step `Simplify(y + z, w)`, yielding the rule

`Simplify(y+z,w) ⇒ Simplify(1×(y+z),w)`.

In general, a rule can be extracted from any partial subtree of the generalized proof tree. Now we have a problem: which of these rules do we choose?

The choice of which rule to generate comes down to the question of efficiency. There are three factors involved in the analysis of efficiency gains from EBL:

1. Adding large numbers of rules can slow down the reasoning process, because the inference mechanism must still check those rules even in cases where they do not yield a solution. In other words, it increases the branching factor in the search space.
2. To compensate for the slowdown in reasoning, the derived rules must offer significant increases in speed for the cases that they do cover. These increases come about mainly because the derived rules avoid dead ends that would otherwise be taken, but also because they shorten the proof itself.
3. Derived rules should be as general as possible, so that they apply to the largest possible set of cases.
