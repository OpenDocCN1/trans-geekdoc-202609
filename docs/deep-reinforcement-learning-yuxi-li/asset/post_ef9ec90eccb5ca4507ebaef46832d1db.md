
## ALPHAGO ZERO

AlphaGo Zero can be understood as following a generalized policy iteration scheme, incorporating MCTS inside the training loop to perform both policy improvement and policy evaluation. MCTS may be regarded as a policy improvement operator. It outputs move probabilities stronger than raw probabilities of the neural network. Self-play with search may be regarded as a policy evaluation operator. It uses MCTS to select moves, and game winners as samples of value function. Then the policy iteration procedure updates the neural network's weights to match the move probabilities and value more closely with the improved search probabilities and self-play winner, and conduct self-play with updated neural network weights in the next iteration to make the search stronger.

The features of AlphaGo Zero (Silver et al., 2017), comparing with AlphaGo (Silver et al., 2016a), are: 1) it learns from random play, with self-play RL, without human data or supervision; 2) it uses black and white stones from the board as input, without any manual feature engineering; 3) it uses a single neural network to represent both policy and value, rather than separate policy network and value network; and 4) it utilizes the neural network for position evaluation and move sampling for MCTS, and it does not perform Monte Carlo rollouts. AlphaGo Zero deploys several recent achievements in neural networks: residual convolutional neural networks (ResNets), batch normalization, and rectifier nonlinearities.

AlphaGo Zero has three main components in its self-play training pipeline executed in parallel asynchronously: 1) optimize neural network weights from recent self-play data continually; 2) evaluate players continually; 3) use the strongest player to generate new self-play data.

When AlphaGo Zero playing a game against an opponent, MCTS searches from the current state, with the trained neural network weights, to generate move probabilities, and then selects a move.

We present a brief, conceptual pseudo code in Algorithm 12 for training in AlphaGo Zero, conducive for easier understanding.

## ALPHA ZERO

Alpha Zero (Silver et al., 2017) generalizes the learning framework in AlphaGo Zero to more domains, in particular, perfect information two-player zero-sum games, with a general reinforcement learning algorithm, learning with no human knowledge except the game rules, and achieves superhuman performance for the games of chess, shogi, and Go.

## DISCUSSIONS

AlphaGo Zero is a reinforcement learning algorithm. It is neither supervised learning nor unsupervised learning. The game score is a reward signal, not a supervision label. Optimizing the loss function l is supervised learning. However, it performs policy evaluation and policy improvement, as one iteration in generalized policy iteration.

AlphaGo Zero is not only a heuristic search algorithm. AlphaGo Zero follows a generalized policy iteration procedure, in which, heuristic search, in particular, MCTS, plays a critical role, but within the scheme of reinforcement learning generalized policy iteration, as illustrated in the pseudo code in Algorithm 12. MCTS can be viewed as a policy improvement operator.

AlphaGo Zero has attained a superhuman level performance. It may confirm that human professionals have developed effective strategies. However, it does not need to mimic human professional plays. Thus it does not need to predict their moves correctly.

The inputs to AlphaGo Zero include the raw board representation of the position, its history, and the colour to play as 19 × 19 images; game rules; a game scoring function; invariance of game rules under rotation and reflection; and invariance to colour transposition except for komi.

AlphaGo Zero utilizes 64 GPU workers and 19 CPU parameter servers for training, around 2000 TPUs for data generation, and 4 TPUs for game playing. The computation cost is probably too formidable for researchers with average computation resources to replicate AlphaGo Zero. ELF OpenGo is a reimplementation of AlphaGo Zero/AlphaZero using ELF (Tian et al., 2017), at https://facebook.ai/developers/tools/elf.

```
Input: the raw board representation of the position, its history, and the colour to play as 19 × 19
images; game rules; a game scoring function; invariance of game rules under rotation and
reflection, and invariance to colour transposition except for komi
Output: policy (move probabilities) p, value v
initialize Neural network weights θ0 randomly
//AlphaGo Zero follows a generalized policy iteration procedure
for each iteration i do
    // termination conditions:
    // 1. both players pass
    // 2. the search value drops below a resignation threshold
    // 3. the game exceeds a maximum length
    initialize s0
    for each step t, until termination at step T do
        // MCTS can be viewed as a policy improvement operator
        // search algorithm: asynchronous policy and value MCTS algorithm (APV-MCTS)
        // execute an MCTS search πt = αθt-1(st) with previous neural network fθt-1
        // each edge (s, a) in the search tree stores a prior probability P(s, a), a visit count N(s, a),
        // and an action value Q(s, a)
        while computational resource remains do
            select: each simulation traverses the tree by selecting the edge with maximum upper
            confidence bound Q(s, a) + U(s, a), where U(s, a) ∝ P(s, a)/(1 + N(s, a))
            expand and evaluate: the leaf node is expanded and the associated position s is
            evaluated by the neural network, (P(s, ·), V(s)) = fθi(s); the vector of P values are
            stored in the outgoing edges from s
            backup: each edge (s, a) traversed in the simulation is updated to increment its visit
            count N(s, a), and to update its action value to the mean evaluation over these
            simulations, Q(s, a) = 1/N(s, a) ∑s'|s,a→s' V(s'), where s'|s, a → s' indicates that
            a simulation eventually reached s' after taking move a from position s
        end
        // self-play with search can be viewed as a policy evaluation operator: select each move
        // with the improved MCTS-based policy, use the game winner as a sample of the value
        play: once the search is complete, search probabilities π ∝ N1/τ are returned, where N is
        the visit count of each move from root and τ is a parameter controlling temperature; play
        a move by sampling the search probabilities πt, transition to next state st+1
    end
    score the game to give a final reward rT ∈ {-1, +1}
    for each step t in the last game do
        zt ← ±rT, the game winner from the perspective of the current player
        store data as (st, πt, zt)
    end
    sample data (s, π, z) uniformly among all time-steps of the last iteration(s) of self-play
    //train neural network weights θi
    //optimizing loss function l performs both policy evaluation, via (z − v)2, and policy
    improvement, via −πT log p, in a single step
    adjust the neural network (p, v) = fθi(s):
    to minimize the error between the predicted value v and the self-play winner z, and
    to maximize similarity of neural network move probabilities p to search probabilities π
    specifically, adjust the parameters θ by gradient descent on a loss function
    (p, v) = fθi(s) and l = (z − v)2 − πT log p + c||θi||2
    l sums over the mean-squared error and cross-entropy losses, respectively
    c is a parameter controlling the level of L2 weight regularization to prevent overfitting
    evaluate the checkpoint every 1000 training steps to decide if replacing the current best player
    (neural network weights) for generating next batch of self-play games
end
```

## Algorithm 12: AlphaGo Zero training pseudo code, based on Silver et al. (2017)

AlphaGo Zero requires huge amount of data for training, so it is still a big data issue. However, the data can be generated by self play, with a perfect model or precise game rules.

Due to the perfect model or precise game rules for computer Go, AlphaGo algorithms have their limitations. For example, in healthcare, robotics and self driving problems, it is usually hard to collect a large amount of data, and it is hard or impossible to have a close enough or even perfect model. As such, it is nontrivial to directly apply AlphaGo Zero algorithms to such applications.

On the other hand, AlphaGo algorithms, especially, the underlying techniques, namely, deep learning, reinforcement learning, Monte Carlo tree search, and self-play, have many applications. Silver et al. (2016a) and Silver et al. (2017) recommend the following applications: general game-playing (in particular, video games), classical planning, partially observed planning, scheduling, constraint satisfaction, robotics, industrial control, and online recommendation systems. AlphaGo Zero blog at `https://deepmind.com/blog/alphago-zero-learning-scratch/` mentions the following structured problems: protein folding, reducing energy consumption, and searching for revolutionary new materials. 7 Several of these, like planning, scheduling, constraint satisfaction, are constraint programming problems (Rossi et al., 2006).

AlphaGo has made tremendous progress, and sets a landmark in AI. However, we are still far away from attaining artificial general intelligence (AGI).

It is interesting to see how strong a deep neural network in AlphaGo can become, i.e., to approximate optimal value function and policy, and how soon a very strong computer Go program would be available on a mobile phone.

## 15.2 CARD GAMES

Variants of card games, including Texas Hold’em Poker, majian/mahjong, Skat, etc., are imperfect information games, which, as one type of game theory problems, have many applications, e.g., security and medical decision support (Chen and Bowling, 2012). It is interesting to see more progress of deep RL in such applications, and the full version of Texas Hold’em.

Heads-up Limit Hold’em Poker is essentially solved (Bowling et al., 2015) with counterfactual regret minimization (CFR), which is an iterative method to approximate a Nash equilibrium of an extensive-form game with repeated self-play between two regret-minimizing algorithms.

## DEEPSTACK

Recently, significant progress has been made for Heads-up No-Limit Hold’em Poker (Moravčík et al., 2017), the DeepStack computer program defeated professional poker players for the first time. DeepStack utilizes the recursive reasoning of CFR to handle information asymmetry, focusing computation on specific situations arising when making decisions and use of value functions trained automatically, with little domain knowledge or human expert games, without abstraction and offline computation of complete strategies as before. DeepStack follows generalized policy iteration. Watch a talk by Michael Bowling at `https://vimeo.com/212288252`.

It is desirable to see extension of DeepStack to multi-player settings. The current study of Poker limits to a single hand, while there are usually many hands in Poker. It is thus desirable to investigate

7 There is a blog titled "AlphaGo, in context" in May 2017 by Andrej Karpathy, after AlphaGo defeated Ke Jie, at `https://medium.com/@karpathy/alphago-in-context-c47718cb95a5`. The author characterizes properties of Computer Go as: fully deterministic, fully observable, discrete action space, accessible perfect simulator, relatively short episode:game, clear and fast evaluation conducive for many trial-and-errors, and huge datasets of human play games, to illustrate the narrowness of AlphaGo. (AlphaGo Zero invalidates the last property, “huge datasets of human play games”.) It is true that computer Go has limitations in the problem setting and thus for potential applications, and is far from artificial general intelligence. However, we see the success of AlphaGo, in particular, AlphaGo Zero, as the triumph of AI, in particular, the underlying techniques, i.e., deep learning, reinforcement learning, Monte Carlo tree search, and self-play; these techniques are present in many recent achievements in AI. AlphaGo techniques will shed light on classical AI areas, like planning, scheduling, and constraint satisfaction (Silver et al., 2016a), and new areas for AI, like retrosynthesis (Segler et al., 2018). Reportedly, the success of AlphaGo’s conquering titanic search space inspired quantum physicists to solve the quantum many-body problem (Carleo and Troyer, 2017).
