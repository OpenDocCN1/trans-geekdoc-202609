# 584

# MACHINE LEARNING

The power-law is mathematically given as:

$f(x) = \alpha^{-\beta}, \quad (29.1)

$\beta$ being power of the power-law behaviour. Such a relationship is scale-invariant. When $\beta > 2$, the distribution has a finite mean, and when $\beta > 3$ it has a finite variance. A useful method to reveal the process of power-law behaviour is the log-transform, which makes the relationship linear:

$log(f(x)) = \alpha' - \beta log(x). \quad (29.2)

For the sake of completeness, the power-law is defined as:

```
quantQ.physics.powerLaw:[alpha;beta;x]
// alpha -- the coefficient
// beta -- the power of the distribution
// x -- the independent variable
alpha*(x xexp neg beta);
```

# 29.1 AGENT-BASED MODELING

The power-law, however, is not the main focus of this chapter, even though traditionally stands as a main selling point of physics in economics and finance. Econophysics has another significant contribution to economics and finance: the Agent-Based Computational Models, or ABMs. It is not entirely fair to attribute ABMs to physics, as its exact origin is indeed the von Neumann finance, cells-on-the-grid theoretical model of a machine which is supposed to reproduce itself.

The equation-driven approach to describe a particular system is to express its properties based on the macro-dynamics. This usually requires the presence of an equilibrium in the system. On the other hand, the agent-driven approach is based describing the system as an explicit ensemble of interacting agents, or units, which follow some micro-driven rules. Such an approach may lead to a much full range of phenomena going beyond the equilibrium. For instance, the agent-based approach may rise to steady-states or phase transitions. Also, some problems are more naturally described through interacting agents rather than the system dynamics.

# 29.1.1 Agent-Based Models in Society

Imagine you have the funds to make a movie about a famous novel. The novel includes – besides other plots and stories – an epic battle involving thousands of units ranging from desperate villagers to a professional armada with shiny cavalry, units riding elephants, scary og and dragons. To make the movie realistic and get your funds back, you need to employ state-of-the-art computer graphic to get all the animated objects into realistic scenes, but more importantly, you have to solve the problem of how you want to drive the movement of units across the battlefield.