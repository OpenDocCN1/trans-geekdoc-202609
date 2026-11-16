
![](img/dd452eef0506ea820c436fef2f776436_156_0.png)

Figure 10.2 Reinforcement learning scenario. The agent actively explores the environment by taking actions and making observations. If an action is successful, the agent receives a reward. The goal is to learn actions that maximize future rewards.

decisions, and taking actions. Reinforcement learning is based on the observation that animals solve difficult problems in uncertain conditions by exploring the various options in the environment and learning from their outcomes. As learning improves, the exploration decreases, eventually leading to pure exploitation of the best strategy found during learning.

Suppose you have to make a series of decisions to reach a goal. If you already know all the possible choices and each of their expected future rewards, you can use a search algorithm—specifically, Richard Bellman’s algorithm for dynamic programming⁴—to figure out the set of choices that maximizes future rewards, but, as the number of possible choices grows, the size of the problem grows exponentially, which has been called the “curse of dimensionality,” and was illustrated at the beginning of this chapter. But, if you don’t have all the information about the outcomes of the choices ahead of time, you have to learn to make the best choices you can as you go along. This is called “online learning.”

The online learning algorithm that Richard Sutton (figure 10.3) developed depended on differences between expected and received rewards (box 10.1). In temporal difference learning, you compare your estimated long-range reward for making a move in a current state, with a better estimator based on the actual reward you got, and the estimated long-range reward of the next state. By changing the previous estimate to be more like the improved estimate, the decisions that you make on moves will get better

![](img/dd452eef0506ea820c436fef2f776436_157_0.png)

Figure 10.3 Richard Sutton at the University of Alberta in Edmonton in 2006. He taught us how to learn the route to future rewards. Rich is a cancer survivor who has remained a leader in reinforcement learning and continues to develop innovative algorithms. He is generous with his time and insights, which everyone in the field greatly values. His book with Andrew Barto, Reinforcement Learning: An Introduction, is a classic in the field. The second edition is freely available on the Internet. Courtesy of Richard Sutton.

and better. The update is made to a value network that estimates the future expected reward for each board position and is used to decide on the next move. The temporal difference algorithm converges to the optimal rule for making decisions in a given state after you have had enough time to explore the possibilities. The curse of dimensionality is avoided because only a small fraction of all possible board positions are actually visited, but this is enough to develop good strategies for similar board positions that are likely to arise in new games.

Gerry Tesauro's program, called “TD-Gammon,” had important features of the backgammon board and rules built into it, but it had no knowledge of what was a good move to make. At the beginning of the learning, the moves were random, but eventually one side won and got the final reward.

## Box 10.1

### Temporal Difference Learning

![](img/dd452eef0506ea820c436fef2f776436_158_0.png)

In this model of the honeybee brain, actions are chosen (such as landing on a flower) that maximize all future discounted rewards:
\( R(t) = r_{t+1} + \gamma r_{t+2} + \gamma^2 r_{t+3} + ..., \)

where \( r_{t+1} \) is the reward at time t+1 and \( 0 < \gamma < 1 \) is a discount factor. The predicted future reward based on current sensory inputs \( s(t) \) is computed by neuron \( P \):
\( P_t (s) = w^y s^y + w^b s^b, \)

where the sensory input from yellow (Y) and blue (B) flowers are weighted by \( w^y \) and \( w^b \). The reward prediction error \( \delta(t) \) at time \( t \) is given by
\( \delta_t = r_t + \gamma P_t(s_t) - P_t(s_{t-1}), \)

where \( r_t \) is the current reward. The change in each weight is given by:
\( \delta w_t = \alpha \delta_t s_{t-1}, \)

where \( \alpha \) is the learning rate. If the current reward is greater than the predicted reward, and \( \delta \) is positive, the weight is increased on the sensory input that was present before the reward, but if the current reward is less than expected, and \( \delta \) is negative, the weight is decreased.

Adapted from Montague, P. R. and Sejnowski, T. J., *The Predictive Brain: Temporal Coincidence and Temporal Order in Synaptic Learning Mechanisms*, figure 6A.

The winner in backgammon is the first player to “bear off” all of the pieces from the game board.

Since the only actual reward occurs at the end of a game, you might reasonably expect that TD-Gammon would first learn the endgame, then the middle game, and finally the openings. This is in fact what happens in “tabular reinforcement learning,” or “tabular RL,” where there is a table of values for every state in the state space. But it’s completely different with neural networks—they latch quickly onto simple and reliable signals in the input features, and more complex and unreliable input signals later. The first concept that TD-Gammon learns is “Bear off pieces,” by attaching positive weight to the input feature that represents number of pieces borne off. The second concept is “Hit the opponent pieces”—a fairly good heuristic in all phases, learned by putting positive weight on the input unit encoding number of opponent pieces that were hit. The third concept, “Avoid being hit” is a natural reaction to the second concept, and is learned by putting negative weight on single pieces that can be hit. The fourth concept is “Build new points” to block the opponent’s progress by putting positive weights on made-point inputs. Getting these basic concepts requires a few thousand training games. By 10,000 games, TD-Gammon is learning intermediate concepts; by 100,000 games, it starts to learn advanced concepts, and by one million games, it has learned concepts that were either world class, or beyond the knowledge of humans in the early 1990s.

TD-Gammon surprised me and many others when Gerry Tesauro revealed it to the world in 1992⁵. The value function was a backprop network with eighty hidden units. After three hundred thousand games, the program was beating Gerry, so he contacted a famous world-champion backgammon player and author, Bill Robertie, and invited him to visit IBM at Yorktown Heights to play TD-Gammon. Robertie won most of the games but was surprised to lose several well-played ones and declared it the best backgammon program he had ever played. Some of TD-Gammon’s unusual moves he had never seen before; on closer examination, these proved to be improvements on human play overall. Robertie returned when the program had reached 1.5 million self-played games and was astonished when TD-Gammon played him to a draw. It had gotten so much better that he felt it had achieved human-championship level. One backgammon expert, Kit Woolsey, found that TD-Gammon’s positional judgment on whether to play “safe” (low risk/reward) or play “bold” (high risk/reward) was at that time better than that of any human he had seen. Although 1.5 million may seem like a lot of training games, it represented only an infinitesimal fraction of all 10^20 possible backgammon board positions; this required TD-Gammon to generalize to new board positions on almost every move.

TD-Gammon did not get as much publicity as IBM’s Deep Blue, which beat Garry Kasparov at chess in 1997. Chess is much more difficult than backgammon, and Kasparov was the world champion at the time. In some ways, though, TD-Gammon was a more impressive achievement. First, TD-Gammon taught itself how to play, using pattern recognition, a style similar to how humans play, whereas Deep Blue won by brute force, using custom hardware to look more moves into the future than any human could. And, second, TD-Gammon was creative and came up with subtle strategies and positional play never before seen by humans. In doing so, TD-Gammon raised the level of human play. This achievement was a watershed in the history of artificial intelligence because we learned something new from an AI program that taught itself how to master a complex strategy in a well-trodden domain, a strategy that is worthy of human interest and effort.

## Reward Learning in Brains

The heart of TD-Gammon is the temporal difference learning algorithm, which was inspired by learning experiments with animals. Nearly all species that have been tested, from bees to humans, can be taught associatively, just like Pavlov’s dog. In Pavlov’s experiment, a sensory stimulus such as a bell was followed by the presentation of food, which elicited salivation. After several pairings, the bell by itself would lead to salivation. Different species have different preferred unconditioned stimuli in associative learning. Bees are very good at associating the smell, color, and shape of a flower with the reward of nectar and use this learned association to find similar flowers that are in season. Something about this universal form of learning must be important, and there was a period in the 1960s when psychologists intensively studied the conditions that gave rise to associative learning and developed models to explain it. Behaviorists like B. F. Skinner trained pigeons to recognize humans in photos, which calls to mind what can be accomplished with deep learning, but there is a big difference. Backprop learning requires detailed feedback to all the units on the output layer, but associative learning provides only a single reward signal, correct or incorrect. The brain has to figure out what features of the world were responsible for a successful decision.

Only the stimulus that occurs just before the reward gets associated with the reward. This makes sense because a stimulus is more likely to have caused the reward if it comes just before it than if it comes just after the reward. Causality is an important principle in nature. The opposite occurs when the conditioned stimulus is followed by punishment, such as a shock to the foot, which teaches an animal to avoid the stimulus. In some cases,
