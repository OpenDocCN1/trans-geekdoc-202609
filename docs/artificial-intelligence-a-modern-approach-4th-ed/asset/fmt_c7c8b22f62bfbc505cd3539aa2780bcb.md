
In this section, we bring together what we have learned so far in order to construct wumpus world agents that use propositional logic. The first step is to enable the agent to deduce, to the extent possible, the state of the world given its percept history. This requires writing down a complete logical model of the effects of actions. We then show how logical inference can be used by an agent in the wumpus world. We also show how the agent can keep track of the world efficiently without going back into the percept history for each inference. Finally, we show how the agent can use logical inference to construct plans that are guaranteed to achieve its goals, provided its knowledge base is true in the actual world.

## 7.7.1 The current state of the world

As stated at the beginning of the chapter, a logical agent operates by deducing what to do from a knowledge base of sentences about the world. The knowledge base is composed of axioms—general knowledge about how the world works—and percept sentences obtained from the agent’s experience in a particular world. In this section, we focus on the problem of deducing the current state of the wumpus world—where am I, is that square safe, and so on.

We began collecting axioms in [Section 7.4.3](#Chapter07-04.xhtml#sec7-4-3). The agent knows that the starting square contains no pit (`¬P1,1`) and no wumpus (`¬W1,1`). Furthermore, for each square, it knows that the square is breezy if and only if a neighboring square has a pit; and a square is smelly if and only if a neighboring square has a wumpus. Thus, we include a large collection of sentences of the following form:

$\\begin{array}{l} \\left. B\_{\\text{1,1}}\\,\\Leftrightarrow\\,(P\_{\\text{1,2}}\\ \\vee \\,\\,\\, P\_{\\text{2,1}}) \\right. \\\\ \\left. S\_{1,1}\\Leftrightarrow\\,(W\_{1.2} \\vee W\_{2,1}) \\right. \\\\ \\ldots \\\\ \\end{array}$

The agent also knows that there is exactly one wumpus. This is expressed in two parts. First, we have to say that there is at least one wumpus:

`W[1,1] ∨ W[1,2] ∨ … ∨ W[4,3] ∨ W[4,4]`.

Then we have to say that there is at most one wumpus. For each pair of locations, we add a sentence saying that at least one of them must be wumpus-free:

$\\begin{array}{l} {\\neg W\_{1,1} \\vee \\neg W\_{1,2}} \\\\ {\\neg W\_{1,1} \\vee \\neg W\_{1,3}} \\\\ \\ldots \\\\ {\\neg W\_{4,3} \\vee \\neg W\_{4,4}.} \\\\ \\end{array}$

So far, so good. Now let’s consider the agent’s percepts. We are using `S1,1` to mean there is a stench in \[1,1\]; can we use a single proposition, `Stench` to mean that the agent perceives a stench? Unfortunately we can’t: if there was no stench at the previous time step, then `¬Stench` would already be asserted, and the new assertion would simply result in a contradiction. The problem is solved when we realize that a percept asserts something only about the current time. Thus, if the time step (as supplied to `MAKE-PERCEPT-SENTENCE` in [Figure 7.1](#Chapter07-01.xhtml#fig7-1)) is 4, then we add `Stench4` to the knowledge base, rather than `Stench`—neatly avoiding any contradiction with `¬Stench3`. The same goes for the `breeze`, `bump`, `glitter`, and `scream` percepts.

The idea of associating propositions with time steps extends to any aspect of the world that changes over time. For example, the initial knowledge base includes `L[1,1]^0`—the agent is in square \[1, 1\] at time 0—as well as `FacingEast0`, `HaveArrow0`, and `WumpusAlive0`. We use the noun fluent (from the Latin fluens, flowing) to refer to an aspect of the world that changes. “Fluent” is a synonym for “state variable,” in the sense described in the discussion of factored representations in [Section 2.4.7](#Chapter02-04.xhtml#sec2-4-7) on [page 76](#Chapter02-04.xhtml#page_76). Symbols associated with permanent aspects of the world do not need a time superscript and are sometimes called atemporal variables.

*Fluent* *Atemporal variable*

We can connect stench and breeze percepts directly to the properties of the squares where they are experienced as follows.[11](#Chapter07-09.xhtml#sup07-11) For any time step `t` and any square \[x, y\], we assert

$\\begin{array}{l} \\left. L\_{x,y}^{t}\\,\\Rightarrow\\text{(}Breeze^{t}\\ \\Leftrightarrow\\ B\_{x\\text{,}y}\\text{)} \\right. \\\\ \\left. L\_{x,y}^{t}\\,\\Rightarrow\\text{(}Stench^{t}\\ \\Leftrightarrow\\ S\_{x\\text{,}y}\\text{)}\\text{.} \\right. \\\\ \\end{array}$

Now, of course, we need axioms that allow the agent to keep track of fluents such as `L[x,y]^t`. These fluents change as the result of actions taken by the agent, so, in the terminology of [Chapter 3](#Chapter03-00.xhtml), we need to write down the transition model of the wumpus world as a set of logical sentences.

First we need proposition symbols for the occurrences of actions. As with percepts, these symbols are indexed by time; thus, `Forward0` means that the agent executes the `Forward` action at time 0. By convention, the percept for a given time step happens first, followed by the action for that time step, followed by a transition to the next time step.

To describe how the world changes, we can try writing effect axioms that specify the outcome of an action at the next time step. For example, if the agent is at location \[1,1\] facing east at time 0 and goes Forward, the result is that the agent is in square \[2,1\] and no longer is in \[1,1\]:

*Effect axiom*

$\\begin{matrix} \\left. L\_{1,1}^{0}\\,\\, \\land \\,\\, FacingEast^{0}\\,\\, \\land \\,\\, Forward^{0}\\Rightarrow(L\_{2,1}^{1}\\,\\, \\land \\,\\,\\neg L\_{1,1}^{1}). \\right. & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(7.1)} \\\\ \\end{matrix}$

We would need one such sentence for each possible time step, for each of the 16 squares, and each of the four orientations. We would also need similar sentences for the other actions: `Grab`, `Shoot`, `Climb`, `TurnLeft`, and `TurnRight`.

Let us suppose that the agent does decide to move `Forward` at time 0 and asserts this fact into its knowledge base. Given the effect axiom in [Equation (7.1)](#Chapter07-07.xhtml#eq7-1), combined with the initial assertions about the state at time 0, the agent can now deduce that it is in \[2,1\]. That is, `ASK(KB, L[2,1]^1) = true`. So far, so good. Unfortunately, if we `ASK(KB, HaveArrow1)`, the answer is false, that is, the agent cannot prove it still has the arrow; nor can it prove it doesn’t have it! The information has been lost because the effect axiom fails to state what remains unchanged as the result of an action. The need to do this gives rise to the frame problem.[12](#Chapter07-09.xhtml#sup07-12) One possible solution to the frame problem would be to add frame axioms explicitly asserting all the propositions that remain the same. For example, for each time `t` we would have

*Frame problem* *Frame axiom*

$\\begin{array}{l} \\left. Forward^{t}\\Rightarrow(HaveArrow^{t}\\Leftrightarrow HaveArrow^{t + 1}) \\right. \\\\ \\left. Forward^{t}\\Rightarrow(WumpusAlive^{t}\\Leftrightarrow WumpusAlive^{t + 1}) \\right. \\\\ \\ldots \\\\ \\end{array}$

where we explicitly mention every proposition that stays unchanged from time `t` to time `t + 1` under the action `Forward`. Although the agent now knows that it still has the arrow after moving forward and that the wumpus hasn’t died or come back to life, the proliferation of frame axioms seems remarkably inefficient. In a world with `m` different actions and `n` fluents, the set of frame axioms will be of size `O(mn)`. This specific manifestation of the frame problem is sometimes called the `representational frame problem`.

*Representational frame problem*
