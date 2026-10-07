# BM becomes a system, which represents our system (our nuclear power plant).

Once BM does the learning, all of these weights are adjusted, BM understands how all parameters interact with each other and what kind of constraints should exist between them in order to be the system that we're modeling.

Once's all we can use the BM to monitor our nuclear power plant.

Because we've modeled it using good behavior, that hasn't led to any meltdown or any explosions. BM knows what is normal for the nuclear power plant.

Then the BM will understand what is abnormal behavior.

In real-life we cannot model a nuclear meltdown through supervised learning, we don't have that luxury of having all of this training data a Boltzmann machine does.

+   - You have to model it in an unsupervised mode, and that's what a Boltzmann machine does.

Learning through good examples, it understands how the system works in it's normal state, and through it helps us model what the system would look like in an abnormal state and model those scenarios and recognize those scenarios, and therefore monitor the nuclear power plant.

That explains the design of Boltzmann machines:

+   - Why do we not have an output layer because we're not putting out any value. We are creating a model that describes our system.
- Why all of these nodes are interconnected. All of the parameters are interconnected with each other. For example: the speed of turbine and the moisture in the air on that are connected.
- The directionality. The visible nodes and hidden nodes of all the nodes are equal in a BM. All of these parameters are interconnected and therefore it had to be undirected. All the connections are going both ways.

# 14.1.4 Energy based Models (EBM)

Energy-Based models help us understand the stochastic processes that describe system in BM.

Boltzmann distribution: Notice the following equation. This is the Boltzmann distribution. That why the method is called Boltzmann machines (BM). This equation comes from physics, and it is used in the sampling distribution for the Boltzmann machine.

```
p_i = rac{e^{-e_i/kT}}{\sum_{j=1}^M e^{-e_j/kT}}
```

Using this Boltzmann distribution the Boltzmann machine constantly creates different states of our system.

From the equation we see that Boltzmann distribution talks about probability. It describes the probability p_i, of a certain state of a system. Assuming we have total M states for the system.

+   - i is a state. Represents different states.
- e_i = probability of the state i.
- p_i = probability of your system being in state i.
- K is constant and
- T = the temperature of your system.

The important thing is that e^{-e_i/kT} means the energy of a certain state at fixed temperature, the lower the probability. So, probability is inversely related with energy.

![](bbox=[0.493, 0.031, 0.856, 0.246])