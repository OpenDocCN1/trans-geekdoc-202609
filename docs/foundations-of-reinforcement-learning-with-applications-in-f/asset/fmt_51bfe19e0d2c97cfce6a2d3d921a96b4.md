
$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}}) \\approx {\\sum\\limits\_{s \\in \\mathcal{N}}\\rho^{\\pi}}(s) \\cdot {\\sum\\limits\_{a \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(s,a;\\mathbf{\\mathbf{\\theta}}) \\cdot Q(s,a;\\mathbf{\\mathbf{w}})} \\\\ \\end{array}$$  

Now let's implement some code to perform Policy Gradient with the Critic updated using Temporal-Difference (again, for the simple case of single-dimensional continuous action space). In the function `actor_critic_gaussian` below, the key changes (from the code in `reinforce_gaussian`) are:

*   The Q-Value function approximation parameters `w` are updated after each atomic experience as:

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{w}} = \\beta \\cdot (R\_{t + 1} + \\gamma \\cdot Q(S\_{t + 1},A\_{t + 1};\\mathbf{\\mathbf{w}}) - Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}})) \\cdot \\nabla\_{\\mathbf{\\mathbf{w}}}Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}})} \\\\ \\end{array}$$  

    where `β` is the learning rate for the Q-Value function approximation.

*   The policy mean parameters `θ` are updated after each atomic experience as:

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha \\cdot \\gamma^{t} \\cdot (\\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(S\_{t};A\_{t};\\mathbf{\\mathbf{\\theta}})) \\cdot Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}})} \\\\ \\end{array}$$  

    (instead of `α`⋅`γ`^(`t`)⋅(∇[`θ`]log`π`(`S`[`t`],`A`[`t`];`θ`))⋅`G`[`t`]).

![](images/comp14_11.jpg)

The above code is in the file `rl/policy_gradient.py`. We leave it to you as an exercise to implement the update of `Q(s,a;w)` with TD(`λ`), i.e., with eligibility traces.

We can reduce the variance of this Actor-Critic method by subtracting a Baseline Function `B(s)` from `Q(s,a;w)` in the Policy Gradient estimate. This means we update the parameters `θ` as:

$$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha \\cdot \\gamma^{t} \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(S\_{t},A\_{t};\\mathbf{\\mathbf{\\theta}}) \\cdot (Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}}) - B(S\_{t}))} \\\\ \\end{array}$$  

Note that the Baseline Function `B(s)` is only a function of state `s` (and not of action `a`). This ensures that subtracting the Baseline Function `B(s)` does not add bias. This is because:

$$\\begin{aligned} & {{\\sum\\limits\_{s \\in \\mathcal{N}}\\rho^{\\pi}}(s){\\sum\\limits\_{a \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(s,a;\\mathbf{\\mathbf{\\theta}}) \\cdot B(s)} \\\\ = & {{\\sum\\limits\_{s \\in \\mathcal{N}}\\rho^{\\pi}}(s) \\cdot B(s) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}({\\sum\\limits\_{a \\in \\mathcal{A}}\\pi}(s,a;\\mathbf{\\mathbf{\\theta}}))} \\\\ = & {{\\sum\\limits\_{s \\in \\mathcal{N}}\\rho^{\\pi}}(s) \\cdot B(s) \\cdot \\nabla\_{\\mathbf{\\mathbf{\\theta}}}1} \\\\ = & 0 \\\\ \\end{aligned}$$  

A good Baseline Function `B(s)` is a function approximation `V(s;v)` of the State-Value Function `V`^(`π`)(`s`). So then we can rewrite the Actor-Critic Policy Gradient algorithm using an estimate of the Advantage Function, as follows:

$$\\begin{array}{r} {A(s,a;\\mathbf{\\mathbf{w}},\\mathbf{\\mathbf{v}}) = Q(s,a;\\mathbf{\\mathbf{w}}) - V(s;\\mathbf{\\mathbf{v}})} \\\\ \\end{array}$$  

With this, the approximation for ∇[`θ`]*J*(`θ`) is given by:

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}}) \\approx {\\sum\\limits\_{s \\in \\mathcal{N}}\\rho^{\\pi}}(s) \\cdot {\\sum\\limits\_{a \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(s,a;\\mathbf{\\mathbf{\\theta}}) \\cdot A(s,a;\\mathbf{\\mathbf{w}},\\mathbf{\\mathbf{v}})} \\\\ \\end{array}$$  

The function `actor_critic_advantage_gaussian` in the file `rl/policy_gradient.py` implements this algorithm, i.e., Policy Gradient with two Critics `Q(s,a;w)` and `V(s;v)`, each updated using Temporal-Difference (again, for the simple case of single-dimensional continuous action space). Specifically, in the code of `actor_critic_advantage_gaussian`:

*   The Q-Value function approximation parameters `w` are updated after each atomic experience as:

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{w}} = \\beta\_{\\mathbf{\\mathbf{w}}} \\cdot (R\_{t + 1} + \\gamma \\cdot Q(S\_{t + 1},A\_{t + 1};\\mathbf{\\mathbf{w}}) - Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}})) \\cdot \\nabla\_{\\mathbf{\\mathbf{w}}}Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}})} \\\\ \\end{array}$$  

    where `β`[`w`] is the learning rate for the Q-Value function approximation.

*   The State-Value function approximation parameters `v` are updated after each atomic experience as:

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{v}} = \\beta\_{\\mathbf{\\mathbf{v}}} \\cdot (R\_{t + 1} + \\gamma \\cdot V(S\_{t + 1};\\mathbf{\\mathbf{v}}) - V(S\_{t};\\mathbf{\\mathbf{v}})) \\cdot \\nabla\_{\\mathbf{\\mathbf{v}}}V(S\_{t};\\mathbf{\\mathbf{v}})} \\\\ \\end{array}$$  

    where `β`[`v`] is the learning rate for the State-Value function approximation.

*   The policy mean parameters `θ` are updated after each atomic experience as:

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{\\theta}} = \\alpha \\cdot \\gamma^{t} \\cdot (\\nabla\_{\\mathbf{\\mathbf{\\theta}}}\\log\\pi(S\_{t};A\_{t};\\mathbf{\\mathbf{\\theta}})) \\cdot (Q(S\_{t},A\_{t};\\mathbf{\\mathbf{w}}) - V(S\_{t};\\mathbf{\\mathbf{v}}))} \\\\ \\end{array}$$  

A simpler way is to use the TD Error of the State-Value Function as an estimate of the Advantage Function. To understand this idea, let `δ`^(`π`) denote the TD Error for the `true` State-Value Function `V`^(`π`)(`s`). Then,

$$\\begin{array}{r} {\\delta^{\\pi} = r + \\gamma \\cdot V^{\\pi}(s^{\\prime}) - V^{\\pi}(s)} \\\\ \\end{array}$$  

Note that `δ`^(`π`) is an unbiased estimate of the Advantage function `A`^(`π`)(`s`,`a`). This is because

$$\\begin{array}{r} {\\mathbb{E}\_{\\pi}\\lbrack\\delta^{\\pi}|s,a\\rbrack = \\mathbb{E}\_{\\pi}\\lbrack r + \\gamma \\cdot V^{\\pi}(s^{\\prime})|s,a\\rbrack - V^{\\pi}(s) = Q^{\\pi}(s,a) - V^{\\pi}(s) = A^{\\pi}(s,a)} \\\\ \\end{array}$$  

So we can write Policy Gradient in terms of 𝔼[`π`][`δ`^(`π`)|`s`,`a`]:

$$\\begin{array}{r} {\\nabla\_{\\mathbf{\\mathbf{\\theta}}}J(\\mathbf{\\mathbf{\\theta}}) = {\\sum\\limits\_{s \\in \\mathcal{N}}\\rho^{\\pi}}(s) \\cdot {\\sum\\limits\_{a \\in \\mathcal{A}}\\nabla\_{\\mathbf{\\mathbf{\\theta}}}}\\pi(s,a;\\mathbf{\\mathbf{\\theta}}) \\cdot \\mathbb{E}\_{\\pi}\\lbrack\\delta^{\\pi}|s,a\\rbrack} \\\\ \\end{array}$$  

In practice, we use a function approximation for the TD error, and sample:

$$\\begin{array}{r} {\\delta(s,r,s^{\\prime};\\mathbf{\\mathbf{v}}) = r + \\gamma \\cdot V(s^{\\prime};\\mathbf{\\mathbf{v}}) - V(s;\\mathbf{\\mathbf{v}})} \\\\ \\end{array}$$  

This approach requires only one set of critic parameters `v`, and we don't have to worry about the Action-Value Function `Q`.

Now let's implement some code for this TD Error-based PG Algorithm (again, for the simple case of single-dimensional continuous action space). In the function `actor_critic_td_error_gaussian` below:

*   The State-Value function approximation parameters `v` are updated after each atomic experience as:

    $$\\begin{array}{r} {\\Delta\\mathbf{\\mathbf{v}} = \\alpha\_{\\mathbf{\\mathbf{v}}} \\cdot (R\_{t + 1} + \\gamma \\cdot V(S\_{t + 1};\\mathbf{\\mathbf{v}}) - V(S\_{t};\\mathbf{\\mathbf{v}})) \\cdot \\nabla\_{\\mathbf{\\mathbf{v}}}V(S\_{t};\\mathbf{\\mathbf{v}})} \\\\ \\end{array}$$  

    where `α`[`v`] is the learning rate for the State-Value function approximation.

*   The policy mean parameters `θ` are updated after each atomic experience as:
