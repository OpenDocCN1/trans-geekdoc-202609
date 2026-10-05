
# 584

# MACHINE LEARNING

The power-law is mathematically given as:

$f(x) = \alpha^{-\beta}, \quad (29.1)$

$\beta$ being power of the power-law behaviour. Such a relationship is scale-invariant. When $\beta > 2$, the distribution has a finite mean, and when $\beta > 3$ it has a finite variance. A useful method to reveal the process of power-law behaviour is the log-transform, which makes the relationship linear:

$log(f(x)) = \alpha' - \beta log(x). \quad (29.2)$

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

Imagine you have the funds to make a movie about a famous novel. The novel includes – besides other plots and stories – an epic battle involving thousands of units ranging from desperate villagers to a professional armada with shiny cavalry, units riding elephants, scary ogres and dragons. To make the movie realistic and get your funds back, you need to employ state-of-the-art computer graphic to get all the animated objects into realistic scenes, but more importantly, you have to solve the problem of how you want to drive the movement of units across the battlefield.

# Econophysics: The Agent-Based Computational Models

A naive approach would be to define and model the movement of every single unit explicitly from the first appearance on the horizon until its final breath or moments of glory. This approach is traditional and would likely be possible if a few units were involved. When we talk about an epic battle with a large number of units, such an approach is impractical.

Also, realistic battles require that units are organised in groups following their leader. Each type of unit responds to other types differently – humans hate and fear of dragons, cavalry lead by heroic characters with spears could scare a dragon when horses panic when encountering elephants. These features nicely colour the storyline of a book and thus have to be seen on the battlefield. Furthermore, the units cannot be perfectly synchronous; they follow their orders but also what they see around. Such rules inevitably lead to chaotic behaviour and discordance. Enforcing straight lines on behaviour would not be realistic even in the fantasy genre.

The features revealed in the previous paragraphs naturally call for modelling the units on the battlefield explicit rules. The agent-based models are a natural framework. The battlefield is then modelled as an ensemble of agents, where each agent represents a unit. Each unit has its type and characteristics. The agent can be a scared villager simply filling others, prone to panic when seeing any inhuman creature, a strategically thinking hero who knows his enemies and saves the day through ingenuity and good luck. The agents are placed over some topology which affects their line of sight, and their movement is affected by the factors they encounter. The battle is then just a step-by-step simulation of every agent. Since there is a randomness in the actions of agents, it should contain plenty of checkpoints to keep the overall simulation in check and link with the main themes.

In the real world, epic battles in movies or may not be an essential part of our life. An example which is more important for our daily lives is emergency planning for city buildings. Especially in the case of large and complex buildings where the exit cannot be in the line of sight, proper planning of escape routes is a vital safety measure. Modelling of safe routes through an equation-based approach is not trivial, as a flow of people can be easily described by human decision. On the other hand, we can formulate rules to conduct surveys or laboratory experiments to understand the factors which drive a human decision in similar situations.

The rules include factors like frequent usage of the agent already knows a new route; even though the sign may suggest that the exit is behind the corner, the agent may prefer to return to a more familiar route. Another rule is the tendency to follow a crowd, where everyone escapees an agent's behaviour though he has seen the exit. The factor of panic and chaotic behaviour should also be considered. The model of emergency evacuation plans and exit signs can be back-tested by using an agent-based model with agents following the behavioural rules. Agents will be thus moving through the provided topological layout responding to their environment.

Simulations can be evaluated in a statistical manner and the environment and emergency signs can be modified such that the probability of survival for agents is maximized. This approach can be used to find the optimum emergency setup or the existing one can be tested. We can also stress-test the emergency setup such that some of the features may fail, or behavioural rules change. It is apparent that this approach is very versatile and an intuitive tool for architects to consider.

# 586

# MACHINE LEARNING

Now we leave the epic battles and evacuation plans and focus on finance.

# 29.1.2 Agent-Based Models in Finance

Finance and economics is another field where agent-based models have been extensively used. For interested readers, we recommend Amman et al. (1996) as a first dive into the models in the field. The handbook shows models describing the dynamics of organisations, financial interactions, and social dynamics. The particular interest across the book is dedicated to learning and its effects on evolving systems. The detailed overview of all possible models is beyond the scope of this chapter. The agent-based models are becoming more widespread across economic and financial outlets.

As an illustration of a particular agent-based model, let us mention Lavička et al. (2016), titled “Sand in the Wheels or Wheels in the Sand? Tobin Taxes and Market Crashes”, where the authors focus on modelling the financial transaction through the lenses of agent-based models. Policymakers consider the financial transaction as a measure to offset negative externalities. The academic research does not provide sufficient insights into the effects of financial transaction variances. The reason is that most of the theoretical and empirical research focuses on Gaussian variance. In this paper, the authors argue that it is crucial to understand the relationship between price jumps, Gaussian variance, and financial transaction taxes.

Namely, Gaussian variance is not necessarily a problem per se; the non-normality of return distribution caused by price jumps not only affects the performance of many risk-hedging algorithms but directly influences the frequency of catastrophic market events. To study the relationship mentioned above, the authors used an agent-based model of financial markets based on Raberto (2003) and Mannaro et al. (2008). The model mimics the behaviour of heterogeneous traders. Their interaction leads to price dynamics of financial assets satisfying the well-known facts of clustering volatility, zero skewness, and higher kurtosis, or price jumps. There are four types of agents based on their behaviour: random traders, fundamentalist traders, momentum traders, and contrarian traders.

The results show that the relationship between FTIs and price jumps is intricate. This implies that regulators may face a trade-off between overall variance and price jumps when designing optimal tax. The conclusion derived from the agent-based model cannot be described by an equation in which it illustrates the power of the computational approach.

Since ABMs allow us to provide a much more general description of system, one may ask why they have not replaced equation-driven systems. The answer is obvious: expensive numerical simulation is required to obtain a solution from an agent-based system. Thus, agent-based systems are usually thought of as “black box” and
