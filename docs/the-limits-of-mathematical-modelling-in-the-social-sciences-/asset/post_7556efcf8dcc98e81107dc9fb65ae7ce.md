
# The Limits of Mathematical Modeling in the Social Sciences

population. For $x > 0, y > 0$, they interact through:

```
$\dot{x} = +\alpha x - \beta xy,$
$\dot{y} = -\gamma y + \delta xy,\quad (1)$
```

where $\alpha, \beta, \gamma, \delta$ are positive real constants. There is an immediate first integral,

```
$\exp H = y^{\alpha}x^{\gamma}\exp[-(\beta y + \delta x)] = k,\quad (2)$
```

where $k$ is a positive constant. Solutions for the LV equations to be on nonlinear cycles.

If we put $u = \log x, v = \log y$, then there is a time-independent Hamiltonian

```
$H = \alpha v + \gamma u - (\beta e^v + \delta e^u) = \log k,\quad (3)$
```

so that equation (1) becomes:

```
$\dot{u} = +\partial H/\partial v,$
$\dot{v} = -\partial H/\partial u.\quad (4)$
```

For the references, see Goel *et al.* (1971) and Nicolis and Prigogine (1977).

# Competing populations with chaotic dynamics

We use a famous result by Ruelle and Takens.

**Proposition 20.1.** If $\omega = \langle w_1, w_2, w_3, w_4\rangle$ is a constant vectorfield on the torus $T^4$, where $w_1 \leq w_2 \leq w_3 \leq w_4$, then every given $C^3$-neighborhood of $\omega$ is an open set of vectorfields with strange attractors.

**Proof.** See Ruelle and Takens (1971). $\square$

Now consider two sets of four LV predator-prey populations obey two uncoupled LV systems (equation (1)),

```
$\Xi = \langle x, y\rangle, \langle x', y'\rangle.$
```

Due to equations (1)-(4) they can be cast in Hamiltonian form and (through the Liouville-Arnol'd theorem), they can be canonically mapped onto a constant vectorfield $\omega$ on $T^4$. Then, as a corollary of the Ruelle-Takens result, when we go back to the LV systems, we have the following corollary:

# **Corollary 20.2.** Close to $\Xi$ there is an open set of perturbed LV equations with four population components and with a chaotic behavior due to strange attractors.

The attractors are Smale horseshoes; a similar result within Hamiltonian mechanics is explicitly dealt with in Holmes and Marsden (1982).

**Remark 20.3.** If $\Xi$ also denotes the LV-system for those populations, then we note its chaotic perturbation:

```
$\Xi' = \Xi + \epsilon\Upsilon, (5)$
```

where $\epsilon$ is a small positive constant and $\Upsilon$ is the perturbation.

# Structures

We consider three interacting populations where the number of individuals in each is denoted by the variables $x, y, z > 0$ (see Nicolis and Prigogine, 1977, p. 460). The dynamics of the model is given:

```
$\dot{x} = \kappa x(N_0 - y - z) - \delta x - \rho y,$
$\dot{y} = \kappa y(N_0 - y - z) - \delta y - f(x, y),$
$\dot{z} = f(x, y) - \delta z. (6)$
```

Here $f(x,y) = \alpha z(y - z)$ is a term. Greek letters represent positive constants; $N_0$ is a maximum level of resources. $y+z$ is to be understood as population split between a “working class” $y$ and a (small-sized) “warrior class” $z$; $x$ is a “middle class”, which is preyed upon by the “warriors” since it competes within the same ecological niche with “workers.”

Stability analysis shows that equilibrium state $x_0, y_0, z_0 = 0$ is unstable. One considers the equilibria $x_0, y_0 = 0; z_0 = 0$ (no warrior class) or $x_0 = 0; y_0, z_0 = 0$ (no middle class). Condition for the survival of the middle class is

```
$\kappa(N_0 - y_0 - z_0) - \delta > 0.$
```

Since $z_0$ is small, the $x$ will vanish if either the workers $y_0$ are a large-sized population or if the warriors are very aggressive ($z_0 \gg 0$) against the middle class $x$.

Recall that the Lotka-Volterra (LV) system,

```
$\dot{x} = -x + \alpha y,$
$\dot{y} = +y - \beta x,$
```

which describes two interacting populations, the predators $(x)$ and preys $(y)$, can be made equivalent through a simple variable change,

```
$u = \log x$
$v = \log y,$
```

which is derived from a Hamiltonian function $H$ (not explicit here; see Nicolis and Prigogine, 1977), so that we have:

```
$\dot{u} = -\partial H/\partial v,$
$\dot{v} = +\partial H/\partial u.$
```

Moreover, since $H$ is a first integral in that system, and since the LV system has only closed orbits, we may transform it into a harmonic oscillator system through a canonical transformation:

```
$\xi = -\eta$
$\dot{\eta} = +\xi.$
```

Those results will be our starting point.

# Two partially competing populations or two populations that will fatally disappear?

We consider here a model derived from a Lotka–Volterra model which undergoes a Hopf bifurcation:

```
$\dot{x} = -y + \alpha xy - x(\mu - x^2 - y^2), \quad (12)$
```

```
$\dot{y} = +x - \beta xy - y(\mu - x^2 - y^2). \quad (13)$
```

It is now a simple exercise to obtain an undecidable dynamical system out of the preceding equations.

# Part II. The monster in the belly of complexity theory

# Appendix A. Preliminary remarks

We may use a more transparent (but colorless) title: completeness out of fast-growing computable functions. We explore here the fast-growing nature of several counterexample functions that appear in complexity theory, as they lead to examples of undecidability and incompleteness in reasonable axiomatic theories. Whenever required, we use (again!) a formal framework $S$ that has the following properties:

We suppose that theory $S$ satisfies the following:

- Its underlying language is the first-order classical predicate calculus.
- It has a recursively enumerable set of theorems.
- It includes PA (Peano Arithmetic) in the following sense: it includes the language and proves all theorems of PA.
- It has a model with standard arithmetic.

> Think of $S$ as PA or ZFC with models that have standard arithmetic. Suppose that we want to build a function that tops all recursive functions. Let's do it formally. We will work within $S$:

**Remark A.1.** For each $n, F(n)=\max_{k\le n}(\{e\}(k))+1$, that is, it is the sup of $\{e\}(k)$ such that:

1. $k \le n$.
2. $[Pr_S([\exists z T(e,k,z)])$

$Pr_S([\xi])$ means there is a proof of $\xi$ in $S$, where $[\xi]$ means: the Gödel number of sentence $[\text{is total}]$ in $S$. Condition 2 translates as: its Gödel number is $\le n$.

**Remark A.2.** We can explicitly compute a Gödel number $e_F$ so that $\{e_F\} = F$.

**Remark A.3.** If $S$ is consistent then $S \forall m \exists n [\{e_F\}(m) = n]$.

We do not get here a Beaver function; we get a partial recursive function (the Busy Beaver is noncomputable), which can be neither proved disproved total in $S$ — it is in the standard model for arithmetic, provided that $S$ has a model with standard arithmetic.

Notice that this function is another version for Kleene’s $F$, which appears in the beginning of this chapter.

# Sources

Again we will base our exposition in three papers of ours (see da Costa and Doria, 2015, 2016; Doria, 2016), which will be freely quoted in what follows.

# Appendix B. Technicalities

We deal here with two possible formalizations for both $P = NP$ and $P < NP$. We have called the unusual formalizations “exotic formalization.” They are naively equivalent, but when we move to a formal framework like that of $S$, we have difficulties.

Let $t_m(x)$ be the primitive recursive function that gives the operation time of $\{m\}$ over an input $x$ of length $|x|$. If $\{m\}$ stops over an input $x$, then

```
t_m(x) = |x| + [number of cycles of the machine until it stops].
```

$T$ is primitive recursive and can in fact be defined out of Kleene’s $T$ predicate.

**Definition B.1 (Standard formalization for $P = NP$). $[P = NP|] \leftarrow_{\text{Def}} \exists m, a \in \omega \forall x \in \omega [(t_m(x) \leq |x|^a + a) \wedge R(x, m)].$
