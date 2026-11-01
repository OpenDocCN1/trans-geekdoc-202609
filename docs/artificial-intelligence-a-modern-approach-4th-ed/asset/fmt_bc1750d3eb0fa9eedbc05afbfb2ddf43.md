
## 4.2 Gradient-Based Optimization

$\\nabla f = \\left( \\frac{\\partial f}{\\partial x\_{1}},\\frac{\\partial f}{\\partial y\_{1}},\\frac{\\partial f}{\\partial x\_{2}},\\frac{\\partial f}{\\partial y\_{2}},\\frac{\\partial f}{\\partial x\_{3}},\\frac{\\partial f}{\\partial y\_{3}}, \\right).$

In some cases, we can find a maximum by solving the equation `∇f = 0`. (This could be done, for example, if we were placing just one airport; the solution is the arithmetic mean of all the cities’ coordinates.) In many cases, however, this equation cannot be solved in closed form. For example, with three airports, the expression for the gradient depends on what cities are closest to each airport in the current state. This means we can compute the gradient locally (but not globally); for example,

$\\begin{matrix} {\\frac{\\partial f}{\\partial x\_{1}} = 2{\\sum\\limits\_{c \\in C\_{1}}{\\text{(}x\_{1}\\ - \\ x\_{c}\\text{)~}\\text{.}}}} & {(4.2)} \\\\ \\end{matrix}$

Given a locally correct expression for the gradient, we can perform steepest-ascent hill climbing by updating the current state according to the formula

`x`←`x`+`α`∇`f`(`x`),

where `α` (alpha) is a small constant often called the step size. There exist a huge variety of methods for adjusting `α`. The basic problem is that if `α` is too small, too many steps are needed; if `α` is too large, the search could overshoot the maximum. The technique of line search tries to overcome this dilemma by extending the current gradient direction—usually by repeatedly doubling `α`—until `f` starts to decrease again. The point at which this occurs becomes the new current state. There are several schools of thought about how the new direction should be chosen at this point.

Step size
Line search

For many problems, the most effective algorithm is the venerable `Newton–Raphson` method. This is a general technique for finding roots of functions—that is, solving equations of the form `g(x) = 0`. It works by computing a new estimate for the root `x` according to Newton’s formula

Newton–Raphson

`x`←`x` − `g`(`x`) / `g′`(`x`).

To find a maximum or minimum of `f`, we need to find `x` such that the gradient is a zero vector (i.e., `∇f(x) = 0`). Thus, `g(x)` in Newton’s formula becomes `∇f(x)`, and the update equation can be written in matrix–vector form as

`x`←`x`−`H`[`f`]^(-1)(`x`)∇`f`(`x`),

where `Hf(x)` is the Hessian matrix of second derivatives, whose elements `Hij` are given by `∂²f/∂xi∂xj`. For our airport example, we can see from [Equation (4.2)](#Chapter04-02.xhtml#eq4-2) that `Hf(x)` is particularly simple: the off-diagonal elements are zero and the diagonal elements for airport `i` are just twice the number of cities in `Ci`. A moment’s calculation shows that one step of the update moves airport `i` directly to the centroid of `Ci`, which is the minimum of the local expression for `f` from [Equation (4.1)](#Chapter04-02.xhtml#eq4-1).[3](#Chapter04-07.xhtml#sup04-3) For high-dimensional problems, however, computing the `n²` entries of the Hessian and inverting it may be expensive, so many approximate versions of the `Newton–Raphson` method have been developed.

Hessian

Local search methods suffer from local maxima, ridges, and plateaus in continuous state spaces just as much as in discrete spaces. Random restarts and simulated annealing are often helpful. High-dimensional continuous spaces are, however, big places in which it is very easy to get lost.

A final topic is constrained optimization. An optimization problem is constrained if solutions must satisfy some hard constraints on the values of the variables. For example, in our airport-siting problem, we might constrain sites to be inside Romania and on dry land (rather than in the middle of lakes). The difficulty of constrained optimization problems depends on the nature of the constraints and the objective function. The best-known category is that of linear programming problems, in which constraints must be linear inequalities forming a convex set[4](#Chapter04-07.xhtml#sup04-4) and the objective function is also linear. The time complexity of linear programming is polynomial in the number of variables.

Constrained optimization
Linear programming
Convex set

Linear programming is probably the most widely studied and broadly useful method for optimization. It is a special case of the more general problem of convex optimization, which allows the constraint region to be any convex region and the objective to be any function that is convex within the constraint region. Under certain conditions, convex optimization problems are also polynomially solvable and may be feasible in practice with thousands of variables. Several important problems in machine learning and control theory can be formulated as convex optimization problems (see [Chapter 21](#Chapter21-00.xhtml)).

Convex optimization

## 4.3 Search with Nondeterministic Actions

In [Chapter 3](#Chapter03-00.xhtml), we assumed a fully observable, deterministic, known environment. Therefore, an agent can observe the initial state, calculate a sequence of actions that reach the goal, and execute the actions with its “eyes closed,” never having to use its percepts.

When the environment is partially observable, however, the agent doesn’t know for sure what state it is in; and when the environment is nondeterministic, the agent doesn’t know what state it transitions to after taking an action. That means that rather than thinking “I’m in state `s1` and if I do action `a` I’ll end up in state `s2`,” an agent will now be thinking “I’m either in state `s1` or `s3`, and if I do action `a` I’ll end up in state `s2`, `s4` or `s5`.” We call a set of physical states that the agent believes are possible a belief state.

Belief state

In partially observable and nondeterministic environments, the solution to a problem is no longer a sequence, but rather a conditional plan (sometimes called a contingency plan or a strategy) that specifies what to do depending on what percepts agent receives while executing the plan. We examine nondeterminism in this section and partial observability in the next.

Conditional plan

## 4.3.1 The erratic vacuum world

The vacuum world from [Chapter 2](#Chapter02-00.xhtml) has eight states, as shown in [Figure 4.9](#Chapter04-03.xhtml#fig4-9). There are three actions—`Right`, `Left`, and `Suck`—and the goal is to clean up all the dirt (states 7 and 8). If the environment is fully observable, deterministic, and completely known, then the problem is easy to solve with any of the algorithms in [Chapter 3](#Chapter03-00.xhtml), and the solution is an action sequence. For example, if the initial state is 1, then the action sequence [`Suck`, `Right`, `Suck`] will reach a goal state, 8.

Description

A bold arrow labeled suck and another arrow labeled Right from the first state of the vacuum world point to the first two circular nodes. An arrow from the second node on the right with an arc points back to state 1 and another arrow points to state 2 of the vacuum world. Two bold arrows from state 2 points outward. A bold arrow from the first node points to state 5 of the vacuum world. A bold arrow labeled Right, from state 5, points to the third node with an arc. A bold arrow from the third node points back to state 5. Another bold arrow from the third node points to state 6 of the vacuum world. Two arrows from state 6 points outward.

![](images/Fig-56.jpg)

Figure 4.9 The eight possible states of the vacuum world; states 7 and 8 are goal states.

Now suppose that we introduce nondeterminism in the form of a powerful but erratic vacuum cleaner. In the erratic vacuum world, the `Suck` action works as follows:

•When applied to a dirty square the action cleans the square and sometimes cleans up dirt in an adjacent square, too.
