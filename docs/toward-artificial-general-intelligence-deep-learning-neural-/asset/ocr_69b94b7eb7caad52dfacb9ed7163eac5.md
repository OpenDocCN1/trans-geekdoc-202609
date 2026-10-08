# ### 3.7.1 Bayes' theorem and probability basics

A crucial tool in probability and statistics is the Bayes' theorem. It is described as a formula for figuring out the conditional probability of an event using information about past conditions or circumstances. In other words, the Bayes' theorem illustrates how new information can alter the likelihood of a specific event. It bears the name Thomas Bayes (1702–1761), a Presbyterian priest and English mathematician.

The theorem is expressed in the following equation:

$$P(A|B) = P(B|A)P(A) \; / \; P(B) \qquad (3.1)$$

where $P(A|B)$ is the probability of event *A* occurring given that event *B* has already occurred. $P(B|A)$ is the probability of event *B* occurring given that event *A* has already occurred. $P(A)$ is the probability of event *A* occurring, independent of any other events. Finally, $P(B)$ is the probability of event *B* occurring, independent of any other events.

For example, let us say we want to use the Bayes' theorem to calculate the probability of someone having the flu, given that they have a fever. We could express this problem in the following equation:

$$P(\text{flu}|\text{fever}) = P(\text{fever}|\text{flu})P(\text{flu}) \; /P(\text{fever}) \qquad (3.2)$$

Here, $P(\text{flu}|\text{fever})$ is the probability of having the flu given that the person has a fever. $P(\text{fever}|\text{flu})$ is the probability of having a fever, given that the person already has the flu. Without considering any other influencing circumstances, $P(\text{flu})$ and $P(\text{fever})$ represent the likelihood of getting the flu and a fever, respectively. Given the existence of a fever, we may determine the possibility of having the flu by plugging the actual probabilities of each event into the equation. This allows us to revise our assessment of an event's likelihood when new information comes to light. As this example shows, the Bayes' theorem is a helpful resource for performing probabilistic computations. Its fundamental ideas are simple, and they may be applied to make decisions about potential outcomes in various settings.

# ### 3.7.2 Naive Bayes assumption

An ML method called the naive Bayes assumption forecasts potential outcomes based on a group of connected variables. This presumption, based on the Bayes' theorem, asserts that all of the model's linked variables are independently correlated [19]. This means that the value of a single variable will not impact the results of any other variables in the model. This supposition makes computation easier since it eliminates the need to study the intricate relationships between the variables and enables the model to generate predictions much more quickly. This assumption simplifies the calculating process, but it can be wrong if the data are not correctly analyzed; remembering is