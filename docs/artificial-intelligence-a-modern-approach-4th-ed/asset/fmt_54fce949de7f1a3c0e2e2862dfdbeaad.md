
The computational complexity of planning has been analyzed by several authors (Bylander, 1994; Ghallab et al., 2004; Rintanen, 2016). There are two main tasks: `PlanSAT` is the question of whether there exists any plan that solves a planning problem. `Bounded PlanSAT` asks whether there is a solution of length k or less; this can be used to find an optimal plan. Both are decidable for classical planning (because the number of states is finite). But if we add function symbols to the language, then the number of states becomes infinite, and `PlanSAT` becomes only semidecidable. For propositionalized problems both are in the complexity class `PSPACE`, a class that is larger (and hence more difficult) than NP and refers to problems that can be solved by a deterministic Turing machine with a polynomial amount of space. These theoretical results are discouraging, but in practice, the problems we want to solve tend to be not so bad. The true advantage of the classical planning formalism is that it has facilitated the development of very accurate domain-independent heuristics; other approaches have not been as fruitful.

Readings in Planning (Allen et al., 1990) is a comprehensive anthology of early work in the field. Weld (1994, 1999) provides two excellent surveys of planning algorithms of the 1990s. It is interesting to see the change in the five years between the two surveys: the first concentrates on partial-order planning, and the second introduces Graphplan and SATPLAN. Automated Planning and Acting (Ghallab et al., 2016) is an excellent textbook on all aspects of the field. LaValle’s text Planning Algorithms (2006) covers both classical and stochastic planning, with extensive coverage of robot motion planning.

Planning research has been central to AI since its inception, and papers on planning are a staple of mainstream AI journals and conferences. There are also specialized conferences such as the International Conference on Automated Planning and Scheduling and the International Workshop on Planning and Scheduling for Space.

[1](#Chapter11-01.xhtml#sup11_1)The blocks world commonly used in planning research is much simpler than SHRDLU’S version ([page 38](#Chapter01-03.xhtml#page_38)).

[2](#Chapter11-03.xhtml#sup11_2)Many problems are written with this convention. For problems that aren’t, replace every negative literal ¬P in a goal or precondition with a new positive literal, P', and modify the initial state and the action effects accordingly.

[3](#Chapter11-05.xhtml#sup11_3)If cyclic solutions are required for a nondeterministic problem, `AND-OR` search must be generalized to a loopy version such as `LAO*` (Hansen and Zilberstein, 2001).

[4](#Chapter11-05.xhtml#sup11_4)In 1954, a Mrs. Hodges of Alabama was hit by meteorite that crashed through her roof. In 1992, a piece of the Mbale meteorite hit a small boy on the head; fortunately, its descent was slowed by banana leaves (Jenniskens et al., 1994). And in 2009, a German boy claimed to have been hit in the hand by a pea-sized meteorite. No serious injuries resulted from any of these incidents, suggesting that the need for preplanning against such contingencies is sometimes overstated.

[5](#Chapter11-05.xhtml#sup11_5)Plan monitoring means that finally, after 374 pages, we have an agent that is smarter than a dung beetle (see [page 59](#Chapter02-02.xhtml#page_59)). A plan-monitoring agent would notice that the dung ball was missing from its grasp and would replan to get another ball and plug its hole.

[6](#Chapter11-05.xhtml#sup11_6)Futile repetition of a plan repair is exactly the behavior exhibited by the sphex wasp ([page 59](#Chapter02-02.xhtml#page_59)).

# CHAPTER 12

## QUANTIFYING UNCERTAINTY

In which we see how to tame uncertainty with numeric degrees of belief.

### 12.1 Acting under Uncertainty

Agents in the real world need to handle uncertainty, whether due to partial observability, nondeterminism, or adversaries. An agent may never know for sure what state it is in now or where it will end up after a sequence of actions.

<p class="sidebar">Uncertainty</p>

We have seen problem-solving and logical agents handle uncertainty by keeping track of a belief state—a representation of the set of all possible world states that it might be in—and generating a contingency plan that handles every possible eventuality that its sensors may report during execution. This approach works on simple problems, but it has drawbacks:

• The agent must consider every possible explanation for its sensor observations, no matter how unlikely. This leads to a large belief-state full of unlikely possibilities.
• A correct contingent plan that handles every eventuality can grow arbitrarily large and must consider arbitrarily unlikely contingencies.
• Sometimes there is no plan that is guaranteed to achieve the goal—yet the agent must act. It must have some way to compare the merits of plans that are not guaranteed.

Suppose, for example, that an automated taxi has the goal of delivering a passenger to the airport on time. The taxi forms a plan, `A90`, that involves leaving home 90 minutes before the flight departs and driving at a reasonable speed. Even though the airport is only 5 miles away, a logical agent will not be able to conclude with absolute certainty that “Plan `A90` will get us to the airport in time.” Instead, it reaches the weaker conclusion “Plan `A90` will get us to the airport in time, as long as the car doesn’t break down, and I don’t get into an accident, and the road isn’t closed, and no meteorite hits the car, and ... .” None of these conditions can be deduced for sure, so we can’t infer that the plan succeeds. This is the logical qualification problem ([page 259](#Chapter07-07.xhtml#page_259)), for which we so far have seen no real solution.

Nonetheless, in some sense `A90` is in fact the right thing to do. What do we mean by this? As we discussed in [Chapter 2](#Chapter02-00.xhtml), we mean that out of all the plans that could be executed, `A90` is expected to maximize the agent’s performance measure (where the expectation is relative to the agent’s knowledge about the environment). The performance measure includes getting to the airport in time for the flight, avoiding a long, unproductive wait at the airport, and avoiding speeding tickets along the way. The agent’s knowledge cannot guarantee any of these outcomes for `A90`, but it can provide some degree of belief that they will be achieved. Other plans, such as `A180`, might increase the agent’s belief that it will get to the airport on time, but also increase the likelihood of a long, boring wait. The right thing to do—the rational decision—therefore depends on both the relative importance of various goals and the likelihood that, and degree to which, they will be achieved. The remainder of this section hones these ideas, in preparation for the development of the general theories of uncertain reasoning and rational decisions that we present in this and subsequent chapters.

#### 12.1.1 Summarizing uncertainty

Let’s consider an example of uncertain reasoning: diagnosing a dental patient’s toothache. Diagnosis—whether for medicine, automobile repair, or whatever—almost always involves uncertainty. Let us try to write rules for dental diagnosis using propositional logic, so that we can see how the logical approach breaks down. Consider the following simple rule:

`Toothache` ⇒ `Cavity`.

The problem is that this rule is wrong. Not all patients with toothaches have cavities; some of them have gum disease, an abscess, or one of several other problems:

`Toothache` ⇒ `Cavity`∨`GumProblem`∨`Abscess`…

Unfortunately, in order to make the rule true, we have to add an almost unlimited list of possible problems. We could try turning the rule into a causal rule:

`Cavity`⇒`Toothache`.
