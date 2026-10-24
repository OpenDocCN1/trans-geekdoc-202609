| | Day 1 | Day 2 | Day 3 | Day 4 | Day 5 |
|---|---|---|---|---|---|
| Action | camera | camera | TV | camera | camera |
| Rewards | 20 | 20 | 100 | 150 | 10 |

| | TV | Camera | Printer |
|---|---|---|---|
| Value q(a) | ? | ? | ? |
| Estimated value Q(a) | 100 | 50 | ? |

# FIGURE 7.29 An example of reinforcement learning.

use (exploitation) of the information we have collected so far regarding the true value q(a). However, what if there is a big gap between the estimated value Q(a) and the true value q(a)? In other words, it is quite possible that q(camera) > q(TV), even though Q(camera) < Q(TV), especially given that Q(camera) and Q(TV) are based on very limited data in this example (4 days for camera and 1 day for TV). Moreover, we have never tried printer advertisement at all and thus have zero knowledge about q(printer). What if the printer advertisement actually has the highest value?

Another alternative strategy is the random strategy (exploration). Each day, we choose a random product to advertise and observe the reward of that advertisement. If we keep running this for many days, the estimated value Q(a) is likely to be very close to the true value q(a). After that, we choose the advertisement with the highest (estimated) value. This strategy is optimal in the long run. However, we might spend many days before we figure out the optimal action, during which the received rewards might be low.

A better strategy is to combine the greedy strategy and the random strategy together. That is, at each day, with the probability 1 − ε (0 < ε < 1), we choose the action (advertisement) with the highest estimated value Q(a); with the probability ε, we choose a random action; and at the end of the day, we use the observed reward to update the estimated value Q(a). This strategy (called ε-greedy) is likely to obtain a better balance between the immediate (exploitation) and the long-term (exploration) return.

In reinforcement learning, the learning agent tries to figure out what to do (e.g., choose the best product to advertise in order to maximize the overall increased revenue) by interacting with the environment (e.g., trying a few different advertisements, observing their rewards, and adjusting the environment for next day accordingly). This is related to, but bears subtle difference from, classification. In classification, classifier receives the instructive feedback (i.e., the true labels for the training tuples) in order to construct the best classifier. In reinforcement learning, the learning agent receives evaluative feedback (e.g., the immediate reward of an action taken on a specific time step) in order to find the best action.

The above example is called multiarmed bandit problem, in that we can imagine a slot machine with multiple arms, and each arm corresponds to an action (an advertisement on a product) with an unknown value. Beyond the ε-greedy algorithm, many alternative methods exist. For example, upper-confidence-bound method selects the action at each time step based on both the estimated value Q(a) and the uncertainty (or confidence) of the estimation on Q(a). Multiarmed bandit problem is a classic setting in reinforcement learning, where the learning agent tries to find out the best action to act in a single situation (e.g., each advertisement has a fixed value). In more complicated setting, the learning agent needs to choose different actions in different situations. In such settings, reinforcement learning is often formulated as a (finite) Markov decision process. Reinforcement learning has been applied in many application domains, including online advertisement, robotics, chess, and many more.