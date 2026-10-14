
## Sampling from the MDN-RNN

We can sample from the MDN output to generate a prediction for the next z and reward at the following timestep, through the following process:

- 1. Split the 481-dimensional output vector into the 3 variables (logpi, mu, logvar) and the reward value.
- 2. Exponentiate and scale logpi so that it can be interpreted as 32 probability distributions over the 5 mixture indices.
- 3. For each of the 32 dimensions of z, sample from the distributions created from logpi (i.e., choose which of the 5 distributions should be used for each dimension of z).
- 4. Fetch the corresponding values of mu and logvar for this distribution.
- 5. Sample a value for each dimension of z from the normal distribution parameterized by the chosen parameters of mu and logvar for this dimension.

The loss function for the MDN-RNN is the sum of the z vector reconstruction loss and the reward loss. The z vector reconstruction loss is the negative log-likelihood of the distribution predicted by the MDN-RNN, given the true value of z, and the reward loss is the mean squared error between the predicted reward and the true reward.

## Training the Controller

The final step is to train the controller (the network that outputs the chosen action) using an evolutionary algorithm called the covariance matrix adaptation evolution strategy (CMA-ES).

The hyperparameters of this step of the process are as follows:

`controller_num_worker`
The number of workers that will test solutions in parallel

`controller_num_worker_trial`
The number of solutions that each worker will be given to test at each generation

`controller_num_episode`
The number of episodes that each solution will be tested against to calculate the average reward

`controller_eval_steps`
The number of generations between evaluations of the current best parameter set

## The Controller Architecture

The architecture of the controller is very simple. It is a densely connected neural network with no hidden layers. It connects the input vector directly to the action vector.

The input vector is a concatenation of the current z vector (length 32) and the current hidden state of the LSTM (length 256), giving a vector of length 288. Since we are connecting each input unit directly to the 3 output action units, the total number of weights to tune is 288 × 3 = 864, plus 3 bias weights, giving 867 in total.

How should we train this network? Notice that this is not a supervised learning problem—we are not trying to *predict* the correct action. There is no training set of correct actions, as we do not know what the optimal action is for a given state of the environment. This is what distinguishes this as a reinforcement learning problem. We need the agent to discover the optimal values for the weights itself by experimenting within the environment and updating its weights based on received feedback.

Evolutionary strategies are a popular choice for solving reinforcement learning problems, due to their simplicity, efficiency, and scalability. We shall use one particular strategy, known as CMA-ES.

## CMA-ES

Evolutionary strategies generally adhere to the following process:

- 1. Create a *population* of agents and randomly initialize the parameters to be optimized for each agent.
- 2. Loop over the following:
  - a. Evaluate each agent in the environment, returning the average reward over multiple episodes.
  - b. Breed the agents with the best scores to create new members of the population.
  - c. Add randomness to the parameters of the new members.
  - d. Update the population pool by adding the newly created agents and removing poorly performing agents.

This is similar to the process through which animals evolve in nature—hence the name *evolutionary* strategies. “Breeding” in this context simply means combining the existing best-scoring agents such that the next generation are more likely to produce high-quality results, similar to their parents. As with all reinforcement learning solutions, there is a balance to be found between greedily searching for locally optimal solutions and exploring unknown areas of the parameter space for potentially better solutions. This is why it is important to add randomness to the population, to ensure we are not too narrow in our search field.

CMA-ES is just one form of evolutionary strategy. In short, it works by maintaining a normal distribution from which it can sample the parameters of new agents. At each generation, it updates the mean of the distribution to maximize the likelihood of sampling the high-scoring agents from the previous timestep. At the same time, it updates the covariance matrix of the distribution to maximize the likelihood of sampling the high-scoring agents, given the previous mean. It can be thought of as a form of naturally arising gradient descent, but with the added benefit that it is derivative-free, meaning that we do not need to calculate or estimate costly gradients.

One generation of the algorithm demonstrated on a toy example is shown in Figure 12-13. Here we are trying to find the minimum point of a highly nonlinear function in two dimensions—the value of the function in the red/black areas of the image is greater than the value of the function in the white/yellow parts of the image.

![](img/f0f0f5d89818fdddf117bbe758ac8143_376_0.png)

Figure 12-13. One update step from the CMA-ES algorithm (source: Ha, 2017)²

The steps are as follows:

- 1. We start with a randomly generated 2D normal distribution and sample a population of candidates, shown in blue in Figure 12-13.
- 2. We then calculate the value of the function for each candidate and isolate the best 25%, shown in purple in Figure 12-13—we’ll call this set of points P.
- 3. We set the mean of the new normal distribution to be the mean of the points in P. This can be thought of as the breeding stage, wherein we only use the best candidates to generate a new mean for the distribution. We also set the covariance matrix of the new normal distribution to be the covariance matrix of the points in P, but use the existing mean in the covariance calculation rather than the current mean of the points in P. The larger the difference between the existing mean and the mean of the points in P, the wider the variance of the next normal distribution. This has the effect of naturally creating momentum in the search for the optimal parameters.
- 4. We can then sample a new population of candidates from our new normal distribution with an updated mean and covariance matrix.

Figure 12-14 shows several generations of the process. See how the covariance widens as the mean moves in large steps toward the minimum, but narrows as the mean settles into the true minimum.

![](img/f0f0f5d89818fdddf117bbe758ac8143_377_0.png)

Figure 12-14. CMA-ES (source: Wikipedia)

For the car racing task, we do not have a well-defined function to maximize, but instead an environment where the 867 parameters to be optimized determine how well the agent scores. Initially, some sets of parameters will, by random chance, generate scores that are higher than others and the algorithm will gradually move the normal distribution in the direction of those parameters that score highest in the environment.

## Parallelizing CMA-ES

One of the great benefits of CMA-ES is that it can be easily parallelized. The most time-consuming part of the algorithm is calculating the score for a given set of parameters, since it needs to simulate an agent with these parameters in the environment. However, this process can be parallelized, since there are no dependencies between individual simulations. There is a orchestrator process that sends out parameter sets to be tested to many node processes in parallel. The nodes return the results to the orchestrator, which accumulates the results and then passes the overall result of the generation to the CMA-ES object. This object updates the mean and covariance
