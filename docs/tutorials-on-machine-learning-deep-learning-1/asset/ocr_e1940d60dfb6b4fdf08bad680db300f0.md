# # 3. P(X|Walks)

![](bbox=[0.165, 0.045, 0.493, 0.215])

Number of Similar Observations
Among those who Walk
Total number of Walkers

$P(X|Walks) = \frac{P(X|Walks)}{3}$

+   D. Calculate Posterior Probability:

$Posterior Probability, P(Walks|X) = \frac{P(Walks) \times P(X|Walks)}{P(X)} = \frac{Prior Probability \times Likelihood}{Marginal Likelihood} = \frac{10/30 \times 3/4}{30}$

+   [1] Prior Probability: $P(Walks)$

+   [2] Calculate the Marginal Likelihood: Select a radius around the data point. $P(X)$ is the probability of any given point to fall within selected radius.

+   [3] Likelihood: Same radius. $P(X|Walks)$: Probability of the data point would be in this circle given that datapoint walks.

+   [4] Calculate Posterior Probability:

$Posterior Probability, P(Walks|X) = \frac{P(Walks) \times P(X|Walks)}{P(X)} = \frac{Prior Probability \times Likelihood}{Marginal Likelihood} = \frac{10/30 \times 3/4}{30}$

+   Step 2: $P(Drives|X) = \frac{P(Drives) \times P(Drives)}{P(X)}$

We consider the new data-point and same circle. Then:

+   A. Prior Probability: $P(Drives)$
$P(Drives) = \frac{Number.of.Drivers}{Total \ Observations} = \frac{20}{30}$

+   B. Calculate the Marginal Likelihood: $P(X)$
$P(X) = \frac{Number \ of \ Similar \ Observations}{Total \ Observations} = \frac{4}{30}$

+   C. Likelihood: $P(X|Drives)$: Considering only the green points
$P(X|Walks) = \frac{Number \ of \ observations \ among \ those \ who \ Drives}{Total \ of \ Drivers} = \frac{1}{20}$

+   D. Calculate Posterior Probability:

$Posterior Probability, P(Drives|X) = \frac{P(Drives) \times P(X|Drives)}{P(X)} = \frac{Prior Probability \times Likelihood}{Marginal Likelihood} = \frac{20/30 \times 1/20}{4/30}$

![](bbox=[0.655, 0.695, 0.905, 0.825])